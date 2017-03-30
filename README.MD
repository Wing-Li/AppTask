# Android在近期任务列表显示同一个APP的多个Activity

有两种方式可以实现效果

### 第一种：代码实现

    Intent intent = new Intent(this, Main2Activity.class);
    intent.addFlags(Intent.FLAG_ACTIVITY_NEW_DOCUMENT);
    intent.addFlags(Intent.FLAG_ACTIVITY_MULTIPLE_TASK);
    startActivity(intent);

添加两个 Flag 即可，注意关闭的时候要使用:

    finishAndRemoveTask();

> **注意：使用这种方式，必须具有在清单文件中设置的 android:launchMode="standard" 属性值（默认就是这个属性）**

### 第二种：配置 AndroidManifest.xml

在要跳转的 Activit 做如下配置：

    <activity
        android:name=".Main3Activity"
        android:documentLaunchMode="intoExisting"
        android:excludeFromRecents="true"
        android:maxRecents="3"/>