# Git Workflow Patterns - ASCII Diagrams

## 1. GitFlow - Factory Assembly Line

```
time →   0----1----2----3----4----5----6----7----8----9----10---11---12
         |    |    |    |    |    |    |    |    |    |    |    |    |

master   *----*----*---------*-----------------*----*---------*----*     ← Releases only
         |    |    |         ↑                 ↑    ↑         ↑    ↑
         |    |    |         │(4)              │(9) │(11)     │    │(12)
         |    |    |       merge            merge merge    merge  merge
                             
hotfix   |    |    |    *----*                 |    |         |    |     ← Emergency fixes
         |    |    |    ↑    │(3)              |    |         |    |
         |    |    |  branch │fix              |    |         |    |
         |    |    |    │    ↓                 |    |         |    |
         
release  |    |    |----*----*----*----*----*  |    *----*----*    |     ← Release preparation
         |    |    ↑    │(2) │    │    │    │  |    ↑    │    │    |
         |    |  branch │test│bug │test│ ok │  |  branch│test│ ok │
         |    |    │    ↓    ↓    ↓    ↓    ↓  |    │    ↓    ↓    |
         
develop  *----*----*----*----*----*----*----*--*----*----*----*----*     ← Main development
         │(1) │    ↑    │    │    │    │    │  │    │    │    │    │
         │    │  merge  │    │    │    │    │  │    │    │    │    │
         ↓    ↓    │    ↓    ↓    ↓    ↓    ↓  ↓    ↓    ↓    ↓    ↓
         
feature1 *----*----*    |    |    |    |    |  |    |    |    |    |     ← Features developed in parallel
feature2 |    *----*----*    |    |    |    |  |    |    |    |    |
feature3 |    |    |    *----*----*    |    |  |    |    |    |    |
feature4 |    |    |    |    |    *----*----*  |    |    |    |    |
feature5 |    |    |    |    |    |    |    |  *----*----*    |    |
feature6 |    |    |    |    |    |    |    |  |    |    *----*----*

Change Flow:
(1) Create feature branches from develop
(2) Feature → merge into develop after completion  
(3) Hotfix → created from master, merged into master AND develop
(4) Release → created from develop, merged into master after testing
(5) Master → stable releases only, never direct commits
```

## 2. GitHub Flow - Simple Pipeline

```
time →   0----1----2----3----4----5----6----7----8----9----10---11---12
         |    |    |    |    |    |    |    |    |    |    |    |    |

main     *----*----*----*----*----*----*----*----*----*----*----*----*    ← Main branch (always deployable)
         │(1) ↑(2) ↑(3) ↑(4) ↑(5) ↑(6) ↑(7) ↑(8) ↑(9) ↑(10)↑(11)↑(12)
         │   merge│   merge│   merge│   merge│   merge│   merge│   merge
         │    │    │    │    │    │    │    │    │    │    │    │    │
         │    │    │    │    │    │    │    │    │    │    │    │    │
         ↓    │    │    │    │    │    │    │    │    │    │    │    │
         
feature1 *----*PR  |    |    |    |    |    |    |    |    |    |    |    ← Short-lived feature branches
feature2 |    *----*PR  |    |    |    |    |    |    |    |    |    |
feature3 |    |    *----*PR  |    |    |    |    |    |    |    |    |
bugfix1  |    |    |    *----*PR  |    |    |    |    |    |    |    |
feature4 |    |    |    |    *----*----*PR  |    |    |    |    |    |    ← Sometimes slightly longer
hotfix1  |    |    |    |    |    *PR  |    |    |    |    |    |    |    ← Quick fixes
feature5 |    |    |    |    |    |    *----*PR  |    |    |    |    |
feature6 |    |    |    |    |    |    |    *----*----*PR  |    |    |
feature7 |    |    |    |    |    |    |    |    *----*PR  |    |    |
feature8 |    |    |    |    |    |    |    |    |    *----*----*PR  |

Change Flow:
(1) Create feature branch from main
(2) Pull Request → Code Review → Merge into main
(3) Every merge into main = potential release
(4) Deploy directly from main (often automatic)
(5) Hotfix = regular feature branch but with priority

PR = Pull Request (Code Review mandatory)
```

## 3. Trunk-Based Development - Racing Track

```
time →   0----1----2----3----4----5----6----7----8----9----10---11---12
         |    |    |    |    |    |    |    |    |    |    |    |    |

main     *----*----*----*----*----*----*----*----*----*----*----*----*    ← Single long-lived branch
         │A1  │B1  │A2  │C1  │B2  │A3  │D1  │C2  │B3  │A4  │E1  │D2  │F1
         ↓    ↓    ↓    ↓    ↓    ↓    ↓    ↓    ↓    ↓    ↓    ↓    ↓
      [CI][CI][CI][CI][CI][CI][CI][CI][CI][CI][CI][CI][CI] ← Every commit = CI run
         
feat-A   *----*----*----*----*----*----*    |    |    *----*    |    |    ← Short-lived branches (max 1-2 days)
feat-B   |    *----*----*----*----*----*----*----*    |    |    |    |
feat-C   |    |    |    *----*----*----*----*    |    |    |    |    |
feat-D   |    |    |    |    |    |    *----*----*----*----*    |    |
feat-E   |    |    |    |    |    |    |    |    |    |    *----*    |
feat-F   |    |    |    |    |    |    |    |    |    |    |    |    *----*

Feature Flags state:
Time 0-2:  Feature A = OFF, B = OFF, C = OFF, D = OFF
Time 3-5:  Feature A = OFF, B = OFF, C = OFF, D = OFF  
Time 6-8:  Feature A = ON,  B = OFF, C = OFF, D = OFF   ← A enabled
Time 9-11: Feature A = ON,  B = ON,  C = ON,  D = OFF   ← B,C enabled  
Time 12+:  Feature A = ON,  B = ON,  C = ON,  D = ON    ← D enabled

Change Flow:
(1) Developers create short branches (hours/days, not weeks)
(2) Code constantly merged into main BUT features disabled by flags
(3) CI runs on every commit (thousands of tests in minutes)
(4) Feature Flag enabled when feature is ready
(5) Rollback = disable flag (seconds, not hours)
(6) No long-lived branches except main

CI = Continuous Integration (automated tests)
FF = Feature Flag (enable/disable feature in production)
```

## Deployment Speed Comparison

```
GitFlow:     Feature → Develop → Release → Master → Production
             [1-2 weeks] [1-2 weeks] [testing] [release]
             TOTAL: 2-6 weeks per feature

GitHub Flow: Feature → PR → Main → Production  
             [1-5 days] [review] [deploy]
             TOTAL: 2-7 days per feature

Trunk-Based: Feature → Main → Production (disabled) → Enable flag
             [hours-days] [instant] [seconds]
             TOTAL: hours-days per feature
```