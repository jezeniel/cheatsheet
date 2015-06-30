Profiling
=========

Check what function/packages slows vim down.

```viml
:profile start ~/profile.log
:profile func *
:profile file *
" Do slow actions
:profile pause
:noautocmd qall!
```
