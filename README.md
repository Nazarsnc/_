from PyQt5.QtCore import Qt
from PyQt5.QtWidgets import (QApplication, QWidget, QHBoxLayout, QVBoxLayout, QRadioButton,
                            QLabel, QButtonGroup, QGroupBox, QPushButton, QSpinBox, QMessageBox)

class CasinoGame(QWidget):
    def init(self):
        super().init()

        self.setWindowTitle("Казино")
        self.resize(400, 400)

        self.qtext = QLabel()
        self.v_line = QVBoxLayout()

        self.rbtn_1 = QRadioButton('1991')
        self.rbtn_2 = QRadioButton('1989')
        self.rbtn_3 = QRadioButton('1998')
        self.rbtn_4 = QRadioButton('1992')

        self.RadioGroupBox = QGroupBox('Baрiaнти відповідей')
        self.RadioGroup = QButtonGroup()
        self.RadioGroup.addButton(self.rbtn_1)
        self.RadioGroup.addButton(self.rbtn_2)
        self.RadioGroup.addButton(self.rbtn_3)
        self.RadioGroup.addButton(self.rbtn_4)

        self.Layout_ans1 = QHBoxLayout()
        self.Layout_ans2 = QVBoxLayout()
        self.Layout_ans3 = QVBoxLayout()

        self.Layout_ans2.addWidget(self.rbtn_1)
        self.Layout_ans2.addWidget(self.rbtn_2)
        self.Layout_ans3.addWidget(self.rbtn_3)
        self.Layout_ans3.addWidget(self.rbtn_4)

        self.btn_Menu = QPushButton("Меню")
        self.btn_Sleep = QPushButton("Відпочити")
        self.box_Minutes = QSpinBox()
        self.box_Minutes.setValue(30)
        self.btn_Ok = QPushButton("Відповісти")

        self.Layout_line1 = QHBoxLayout()
        self.Layout_line2 = QHBoxLayout()
        self.Layout_line3 = QHBoxLayout()
        self.Layout_line4 = QHBoxLayout()

        self.Layout_line1.addWidget(self.btn_Menu)
        self.Layout_line1.addWidget(self.btn_Sleep)
        self.Layout_line1.addWidget(self.box_Minutes)

        self.Layout_line2.addWidget(self.qtext, alignment=Qt.AlignVCenter)
        self.Layout_line3.addWidget(self.RadioGroupBox)
        self.Layout_line4.addWidget(self.btn_Ok, alignment=Qt.AlignVCenter)

        self.Layout_card = QVBoxLayout()
        self.Layout_card.addLayout(self.Layout_line1)
        self.Layout_card.addLayout(self.Layout_line2)
        self.Layout_card.addLayout(self.Layout_line3)
        self.Layout_card.addLayout(self.Layout_line4)

        self.Layout_ans1.addLayout(self.Layout_ans2)
        self.Layout_ans1.addLayout(self.Layout_ans3)
        self.RadioGroupBox.setLayout(self.Layout_ans1)

        self.btn_Menu.clicked.connect(self.open_menu_window)

        self.setLayout(self.Layout_card)

    def open_menu_window(self):
        self.menu_window = MenuWindow(self)
        self.menu_window.show()

class MenuWindow(QWidget):
    def init(self, parent):
        super().init()
        self.parent = parent  # Посилання на головне вікно
        self.setWindowTitle("Меню")
        self.setGeometry(100, 100, 400, 300)

        # Додайте решту коду для створення вікна "Меню" з полями, кнопками та обробниками подій, як в попередньому коді.

        # Приклад:
        self.add_question_button = QPushButton("Додати запитання")
        self.add_question_button.clicked.connect(self.add_question)

        # Вам потрібно також додати логіку для збереження запитань та відповідей, а також для відображення статистики.

if name == "main":
    app = QApplication([])
    main_win = CasinoGame()
    main_win.show()
    app.exec_()
