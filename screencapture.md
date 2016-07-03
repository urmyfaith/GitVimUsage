## screencapture   截图保存到桌面

-i 交互式截图
-o 截图没有阴影
-W 交互式 window 截图
-x 截图不播放声音


```
alias zxshot="screencapture -i -o -W -x $(date '+~/Desktop/%Y_%m_%d_%H_%M_%S.png')"
```

```
man screencapture -t | open -fa Preview
```

