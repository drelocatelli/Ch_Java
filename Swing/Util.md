## Util

# Set Icon
```
SetIcon(new ImageIcon(getClass().getClassLoader().getResource("file.png")));
```

# Get Current Frame
```
JFrame currentFrame = (JFrame) SwingUtilities.getWindowAncestor(contentPane);
```

# Set Current Frame Maximized
```
currentFrame.setExtendedState(JFrame.MAXIMIZED_BOTH);
```

# Robot
```
import java.awt.Robot;
import java.awt.AWTException;
```

```
try {

  Robot robot = new Robot();
  robot.keyPress(KeyEvent.VK_TAB);

}catch(AWTException e1) {

  e1.printStackTrace();

}
```

