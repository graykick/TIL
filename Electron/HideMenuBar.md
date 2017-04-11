# HideMunuBar
Electron프로젝트를 시작하면 위에 메뉴바가 생긴다. 이를 제거하는 방법이다.
BrowserWindow.setMenu(null);

```
win = new BrowserWindow({
width: 600,
height: 600
})
win.setMenu(null);
``
