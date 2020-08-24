[TOC]


# QAction Class

`QAction` 类提供了可以插入到控件中的抽象用户界面动作。[更多]()...

| 属性 | 方法 |
| ----- | -------------------------------- |
| 头文件 | \#include \<QAction\> |
| qmake  | QT += widgets |
| 父类   | [QObject]() |
| 子类   | [QWdigetAction]() |

[>所有成员列表，包括继承的成员]()

## 公共成员类型

| 类型 | 方法 |
| :--: | :---- |
| enum | [ActionEvent]() { Trigger, Hover } |
| enum | [MenuRole]() { NoRole, TextHeuristicRole, ApplicationSpecificRole, AboutQtRole, AboutRole, …, QuitRole } |
| enum | [Priority]() { LowPriority, NormalPriority, HighPriority } |


## 属性

| 属性     | 类型    | 属性    | 类型    |
| :------ | ------- | ------- | ------- |
| [autoRepeat]() | bool | [prority]() | Priority |
| [checkable]() | bool | [shortcut]() | QKeySequence |
| [checked]() | bool | [shortcutContext]() | Qt::ShortcutContext |
| [enabled]() | bool | [shortcutVisibleInContextMenu]() | bool |
| [font]() | QFont | [statusTip]() | QString |
| [icon]() | QIcon | [text]() | QString |
| [iconText]() | QString | [toolTip]() | QString |
| [iconVisibleInMenu]() | bool | [visible]() | bool |
| [menuRole]() | MenuRole | [whatsThis]() | QString |


## 公共成员函数

| 返回类型 | 函数名  |
| ------: | :------ |
| | [QAction]()(const QIcon &*icon*, const QString &*text*, QObject \**parent* = nullptr) |
| | [QAction]()(const QString &*text*, QObject \**parent* = nullptr) |
| | [QAction]()(QObject \**parent* = nullptr) |
|virtual| [~QAction]()() |
|QActionGroup *| [actionGroup]()() const |
|void| [activate]()(QAction::ActionEvent *event*) |
|QList<QGraphicsWidget *>| associatedGraphicsWidgets() const |
|QList<QWidget *>| associatedWidgets() const |
|bool| autoRepeat() const |
|QVariant| data() const |
|QFont| font() const |
|QIcon| icon() const |
|QString| iconText() const |
|bool| isCheckable() const |
|bool| isChecked() const |
|bool| isEnabled() const |
|bool| isIconVisibleInMenu() const |
|bool| isSeparator() const |
|bool| isShortcutVisibleInContextMenu() const |
|bool| isVisible() const |
|QMenu *| menu() const |
|QAction::MenuRole| menuRole() const |
|QWidget *| parentWidget() const |
|QAction::Priority| priority() const |
|void| setActionGroup(QActionGroup \**group*) |
|void| setAutoRepeat(bool) |
|void| setCheckable(bool) |
|void| setData(const QVariant &*userData*) |
|void| setFont(const QFont &*font*) |
|void| setIcon(const QIcon &*icon*) |
|void| setIconText(const QString &*text*) |
|void| setIconVisibleInMenu(bool *visible*) |
|void| setMenu(QMenu \**menu*) |
|void| setMenuRole(QAction::MenuRole menuRole) |
|void| setPriority(QAction::Priority *priority*) |
|void| setSeparator(bool *b*) |
|void| setShortcut(const QKeySequence &*shortcut*) |
|void| setShortcutContext(Qt::ShortcutContext *context*) |
|void| setShortcutVisibleInContextMenu(bool *show*) |
|void| setShortcuts(const QList<QKeySequence> &*shortcuts*) |
|void| setShortcuts(QKeySequence::StandardKey *key*) |
|void| setStatusTip(const QString &*statusTip*) |
|void| setText(const QString &*text*) |
|void| setToolTip(const QString &*tip*) |
|void| setWhatsThis(const QString &*what*) |
|QKeySequence| shortcut() const |
|Qt::ShortcutContext| shortcutContext() const |
|QList<QKeySequence>| shortcuts() const |
|bool| showStatusText(QWidget \**widget* = nullptr) |
|QString| statusTip() const |
|QString| text() const |
|QString| toolTip() const |
|QString| whatsThis() const |


## 公共槽
| 返回类型  | 函数名  |
| :------: | :------ |
| void | [hover]()() |
| void | [setChecked]()(bool) |
| void | [setDisabled]()(bool *b*) |
| void | [setEnabled]()(bool) |
| void | [setVisible]()(bool) |
| void | [toggle]()() |
| void | [trigger]()() |


## 信号
| 返回类型  | 函数名 |
| :------: | :------ |
| void | [changed]()() |
| void | [hovered]()() |
| void | [toggled]()(bool *checked*) |
| void | [triggered]()(bool *checked = false*) |

## 重写保护成员函数

| 返回类型 | 函数名|
| :------: |:------|
| virtual bool | [event]()(QEvent \**e*) override |


## 详细介绍
在应用程序中，可以通过菜单、工具栏按钮和键盘快捷键来调用许多常用命令。因为用户期望以相同的方式执行每个命令，而不用关心所使用的用户界面，所以，将每个命令表示为一个*动作*是非常有用的做法。

动作可以被添加到菜单和工具栏中，并且自动使其保持同步。例如，在文字处理器中，如果用户按下“加粗”工具栏按钮，那么“加粗”菜单将被自动勾选上。

动作可以创建为独立的对象，也可以在构造菜单时创建。[QMenu]() 类包含方便创建适合用作菜单项动作的函数。

QAction 类可能包含图标、菜单文本、快捷键、状态文本、“这是什么？”文字和工具提示，其中大多数可以在构造函数中设置，也可以分别使用 `setIcon()`, `setText()`, `setIconText()`, `setShortcut()`, `setStatusTip()`, `setWhatsThis()`, `setToolTip()` 进行设置。对于菜单项，可以使用setFont() 设置单个字体。

使用 `QWidget::addAction()` 或者 `QGraphicsWidget::addAction()` 将动作添加到空间中。请注意，使用一个动作之前，必须先将其添加到控件中。全局快捷键也是如此（即 `Qt::ApplicationShortcut` 为 `Qt::ShortcutContext`）。

一旦 `QAction` 类被创建，应将其添加到相关的菜单和工具栏，然后连接到将执行动作的槽。例如：

```cpp
const QIcon openIcon = QIcon::fromTheme("document-open", QIcon(":/images/pen.png"));
QAction *openAct = new QAction(openIcon, tr("&Open..."), this);
openAct->setShortcuts(QKeySequence::Open);
openAct->setStatusTip(tr("Open an existing file"));
connect(openAct, &QAction::triggered, this, &MainWindow::open);
fileMenu->addAction(openAct);
fileToolBar->addAction(openAct);
```

我们推荐将动作创建为使用它们的窗口的子级。在大多数情况下，动作将是应用程序主窗口的子级。

另请参见 [QMenu](), [QToolBar]() 和 [应用程序实例]()。

## 成员类型文档
### enum QAction::ActionEvent
----
当调用 [QAction::activate()]() 时使用该枚举类型。

|  常量  |   值   |  描述  |
| :----  | :----: | :---- |
| QAction::Trigger | 0 | 这将导致发出 [QAction::triggered()]() 信号 |
| QAction::Hover   | 1 | 这将导致发出 [QAction::hovered()]() 信号 |


### enum QAction::MenuRole
----
该枚举描述了如何将动作移至macOS上的应用程序菜单。

|  常量  |   值   |  描述  |
| :----  | :----: | :---- |
| QAction::NoRole | 0 | 此动作不应放在应用程序菜单中 |
| QAction::TextHeuristicRole | 1 | 正如 [QMenuBar]() 文档所述，应根据动作的文本将此动作放入应用程序菜单中 |
| QAction::ApplicationSpecificRole | 2 | 此动作应以特定于应用程序的角色放在应用程序菜单中 |
| QAction::AboutQtRole | 3 | 此动作处理“关于Qt”菜单项。 |
| QAction::AboutRole | 4 | 此动作应放在应用程序菜单中“关于”菜单项的位置。菜单项的文本将设置为“关于<应用程序名称>”。应用程序的名称将从应用程序捆绑包中的Info.plist文件中获取（参见[有关MacOS的Qt部署]()） |
| QAction::PreferencesRole | 5 | 此动作应放在应用程序菜单中“首选项...”菜单项的位置 |
| QAction::QuitRole | 6 | 此动作应放在应用程序菜单中“退出”菜单项的位置 |

设置此值仅对菜单栏的快捷菜单中的项目有效，而对那些菜单的子菜单无效。例如，如果菜单栏中有“文件”菜单，并且“文件”菜单有一个子菜单，为子菜单中的动作设置 `MenuRole` 无效。它们永远不会发生动作。


### enum QAction::Priority
----
该枚举定义了用户界面中动作优先级。

|  常量  |   值   |  描述  |
| :----  | :----: | :---- |
| QAction::LowPriority | 0 | 此动作不应该在用户界面中被置为优先 |
| QAction::NormalPriority | 128 | |
| QAction::HighPriority | 256 | 此动作应该在用户界面中被置为优先 |

该枚举是在 `Qt 4.6` 中被引入或修改的。

另请参见[priority]()。


## 属性文档
### autoRepeat : bool
----
该属性保存动作能否自动重复。

如果为 `true`，则在系统上启用了键盘自动重复功能的情况下，按住键盘组合快捷键时，该动作将自动重复。默认值是 `true`。

该属性是在 `Qt 4.6` 中被引入的。

**存取函数:**
|       |       |
| ----: | :---- |
| bool  | autoRepeat() const |
| void  | setAutoRepeat(*bool*) |

**通知信号：**
|       |       |
| ----: | :---- |
| void  | [changed]()() |

