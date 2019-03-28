# To Do

# Excel Pages

## snowball

### Each debt
| | | | | |
| - | - | - | - | - |
| | {name} | {apr} | {default} | {dueDate}
| Date     | Balance | Interest | Payment | Paid |
| {mmm-yy} | {remaining} | {interest} | {pmt} | {date} |

* **`remaining`**:  
```
if (prior{remaining} - prior{pmt} > 0)
  round(
    prior{remaining} * (1 + {apr}/12) - prior{pmt}
    , 2)
else
  0
```
* **`accrued`**: `{remaining} * ( {apr} / 12 )`
* **`pmt`**: `{default} < {remaining} ? {default} : {remaining}`

### Collective
| Snowball | Starting | Remaining |
| - | - | - |
| sum{pmt} | {snowball} | {remaining} |

* **`snowball`**: total monthly amount allocated to debt (minimum plus additional "snowball" amount)
* **`remainint`**: `{snowball} - sum{pmt}`

### Notes
* Debts are ordered left to right from highest to lowest interest.
* `{remaining}` is applied to leftmost debt, after all other `{defaults}` are applied.

## Cards (debts)

|  |  |  |  |  |  |  |  |  |  |
| - | - | - | - | - | - | - | - | - | - |
| {name} | {annual} | {apr} | {limit} | {actualBalance} | {statementBalance} | {updated} | {available} | {minimum} | {interest} | {due} | {url}

* **`annual`**: annual fee
* **`interest`**: `{statementBalance} * {apr} / 12

## Bills

| Item | Statement | URL | Due | Due | Paid | Last | Acct # |
| - | - | - | - | - | - | - | - |
| {name} | {statement} | {url} | {dueDate} | {dueAmt} | {pmtAmt} | {pmtDate} | {acctNo}

### paycheck

| {payDate} | {checkingBalance} | {remaining} |
| - | - | - |

* list of all items w/ due date prior to pay date, plus amount pd
* bottom: list of auto pmts with estimated auto pmt amt and date

#### paycheck notes

* some items may require paying prior to due date if too many items due at same time (e.g., rent)
* some items may require splitting reserve for payment over multiple paychecks to allow both paying bills on time and having pocket money

---
## Consider

* redux
* [`create-react-app`](https://github.com/facebook/create-react-app) scaffolding
* [`next.js`](https://github.com/zeit/next.js) ([`on zeit.co`](https://zeit.co/blog/next))
  * [`sass`](https://github.com/zeit/next-plugins/tree/master/packages/next-sass)
  * [`preact`](https://github.com/zeit/next-plugins/tree/master/packages/next-preact)
  * [`react-hyperscript`](https://github.com/mlmorg/react-hyperscript) (instead of `preact`?)
  * [`integrating redux`](https://github.com/zeit/next.js/tree/canary/examples/with-redux)
  * [`now`](https://zeit.co/now)
* [`hapi`](https://hapijs.com/tutorials) - Node.js web server
* [`hapi-pino`](https://github.com/pinojs/hapi-pino) - Hapi plugin for the [Pino logger](https://github.com/pinojs/pino)
