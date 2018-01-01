## Install
``` bash
npm install cmd-rainbow --save-dev 
```
## Usage
``` javascript
// require('cmd-rainbow')
const { llog, log, c, slog, wlog, ilog, elog, clearLine, colors } = require('cmd-rainbow')

// llog(...arg): without '\n'
llog('llog(...arg): Without "\\n", ')
llog('Hello %s', 'world')

// log(...arg): with '\n'
log('')
log('--------------------')
log('log(...arg): With "\\n", ')
log('Hello %s', 'world')

// ilog(...arg): Green log()
ilog('--------------------')
ilog('ilog(...arg): Green log(), ')
ilog('Log %s', 'info')

// wlog(...arg): Yello log()
wlog('--------------------')
wlog('wlog(...arg): Yello log(), ')
wlog('Log %s', 'warnings')

// elog(...arg): Red log()
elog('--------------------')
elog('elog(...arg): Red log(), ')
elog('Log %s', 'errors')

/*
** c(obj, frontColor, backgroundColor): Set color
** frontColor and backgroundColor need Array like [R, G, B] or String like '#9ab' '#fab9c0'
*/
log('--------------------')
log('c(obj, frontColor, backgroundColor): Set color')
log('frontColor and backgroundColor need Array like [R, G, B] or String like "#9ab" "#fab9c0"')
log(c('Set color %s', '#f7982a'), '#f7982a')
log(c('Set color %s', [68, 123, 146]), '[68, 123, 146]')
log(c('Set color %s', [255, 123, 146], '#456'), '[255, 123, 146], #456')
log(c(['I', 'm', 'an Array'], '#456', '#f7982a'))

// custom log function
function mylog (...arg) {
  log(c(arg[0], '#f7982a'), ...arg.slice(1))
}
mylog('%s', 'custom log function mylog(...arg)')
log('--------------------')
log('slog(...arg): Single line log, without "\\n", use log("") to clear single line mode')

// slog(...arg): Single line log, without '\n', use log('') can clear single line mode
let n = 0
let t = setInterval(() => {
  slog(c('slog(...arg): Count: %d/5', '#91f822'), ++n)
  if (n >= 5) {
    clearInterval(t)
    log('')
    log('clear single line mode')
    log('--------------------')
    setTimeout(() => {
      clearLine(2)
      log('--------------------')
      llog('colors = ')
      log(colors)
    }, 2000)
  }
}, 1000)
```
## License
* MIT