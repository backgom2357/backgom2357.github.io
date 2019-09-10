---
layout: post
title:  "python - Auto-clicker ver 1.0"
date:   2019-09-05
categories: programming
---
# Auto clicker
와우 클래식 대기열이 너무 길어서 접속 미리하려고 정해진 시간되면 자동으로 클릭해주는 프로그램을 만듬
<br>
하지만 구글 원격이라는 것이 있었음.
<br>

![AutoClicker](/images/AutoClicker.png){: width="60%" height="auto" .image-center}
<br>

```python
import sys
from PyQt5.QtWidgets import QApplication, QWidget, QLabel, QGroupBox, QSpinBox, QCheckBox, QPushButton, QGridLayout, QDialog, QFileDialog
import pyautogui
from PyQt5.QtCore import *
import time
import os

class MyApp(QWidget):

    def __init__(self):
        super().__init__()
        self.initUI()

        self.delayedTime = 0
        self.x = 0
        self.y = 0
        self.is_doubleClick = False
        self.filePath = ""


    def initUI(self):

        # reservation group1
        self.firstReservation = QGroupBox('Reservation')

        self.getfilePathLb = QLabel('File directory : ', self)
        self.getFilePathButton = QPushButton('Find', self)
        self.getFilePathButton.clicked.connect(self.pushFilePathButtonClicked)

        self.filePathLb = QLabel("", self)

        self.timeLb = QLabel('time(sec) :', self)
        self.delayTime = QSpinBox()
        self.delayTime.setMinimum(0)
        self.delayTime.setMaximum(99999999)

        self.mouseLocation = QLabel('Mouse Location : ', self)
        self.mouseCoordinates = QLabel("(0000 , 0000)", self)

        self.instruction = QPushButton('Find Location', self)
        self.instruction.clicked.connect(self.pushFindButtonClicked)

        self.doubleClick = QCheckBox('Double Click', self)
        self.setButton = QPushButton('Set', self)
        self.setButton.clicked.connect(self.pushSetButtonClicked)

        # group1 layout
        self.group1_layout = QGridLayout()
        self.group1_layout.addWidget(self.getfilePathLb, 0, 0)
        self.group1_layout.addWidget(self.getFilePathButton, 0, 2)
        self.group1_layout.addWidget(self.filePathLb, 1, 0)
        self.group1_layout.addWidget(self.timeLb, 2, 0)
        self.group1_layout.addWidget(self.delayTime, 2, 2)
        self.group1_layout.addWidget(self.mouseLocation, 3, 0)
        self.group1_layout.addWidget(self.mouseCoordinates, 3, 1)
        self.group1_layout.addWidget(self.instruction, 3, 2)
        self.group1_layout.addWidget(self.doubleClick, 5, 0)
        self.group1_layout.addWidget(self.setButton, 5, 2)
        self.firstReservation.setLayout(self.group1_layout)

        # layout
        self.layout = QGridLayout()
        self.layout.addWidget(self.firstReservation, 0, 0)

        self.setLayout(self.layout)

        self.setWindowTitle('Click Reservation')
        self.show()

    def pushFindButtonClicked(self):
        dlg = GetMouseLocation()
        dlg.exec_()
        self.x = dlg.x
        self.y = dlg.y
        self.mouseCoordinates.setText("({0}, {1})".format(self.x,self.y))

    def pushFilePathButtonClicked(self):
        fname = QFileDialog.getOpenFileName(self)
        self.filePath = fname[0]
        self.filePathLb.setText(self.filePath)

    def pushSetButtonClicked(self):
        self.delayedTime = self.delayTime.value()
        run = AutoClicker(self.delayedTime, self.x, self.y, self.filePath, self.is_doubleClick)
        if self.filePath != "":
            run.runFile()
        run.clickAtTheTime()
        self.close()

class GetMouseLocation(QDialog):
    def __init__(self):
        super().__init__()
        self.setupUI()

        self.x = None
        self.y = None

    def setupUI(self):
        self.setWindowTitle("Get Location")

        label1 = QLabel("Press 's' to get location")
        label1.setAlignment(Qt.AlignVCenter)
        label1.setAlignment(Qt.AlignHCenter)

        layout = QGridLayout()
        layout.addWidget(label1,0,0)
        self.setLayout(layout)

    def keyPressEvent(self, e):

        if e.key() == Qt.Key_S:
            self.x = pyautogui.position()[0]
            self.y = pyautogui.position()[1]
            self.close()

class AutoClicker:

    def __init__(self, delay, x, y, filepath, doubleclick=False):
        self.delay = delay
        self.x = x
        self.y = y
        self.filePath = filepath
        self.doubleClick = doubleclick

    def runFile(self):
        try:
            os.startfile(self.filePath)
        except:
            print("Wrong filepath")

    def clickAtTheTime(self):

        time.sleep(self.delay)
        if self.doubleClick:
            print("click!")
            pyautogui.click(self.x, self.y, clicks=2, interval=0.1)
        else:
            print("click!")
            pyautogui.click(self.x, self.y)

if __name__ == '__main__':

    app = QApplication(sys.argv)
    ex = MyApp()
    sys.exit(app.exec_())
```
