# android-utils

### 权限模块

如何使用：

```
public static final int PERMISSION_CALL_PHONE = 0x0001;

private void permissionStart() {
    PermissionHelper.with(this)
            .requestCode(PERMISSION_CALL_PHONE)
            .permissions(Manifest.permission.WRITE_EXTERNAL_STORAGE, Manifest.permission.CAMERA)
            .request();
}

@Override
public void onRequestPermissionsResult(int requestCode, @NonNull String[] permissions, @NonNull int[] grantResults) {
    super.onRequestPermissionsResult(requestCode, permissions, grantResults);
    PermissionHelper.onRequestPermissionsResult(this, requestCode, permissions);
}

@PermissionSuccess(requestCode = PERMISSION_CALL_PHONE)
private void callSuccess() {

}

@PermissionFailure(requestCode = PERMISSION_CALL_PHONE)
private void callFailure() {
    Toast.makeText(this, "您已拒绝相机权限,请到设置中打开相关权限!", Toast.LENGTH_SHORT).show();
}
```

### 各种工具

1. StatusBarUtil : 沉浸式状态栏工具类（设置状态栏颜色、设置状态栏透明）
2. DensityUtil : 文字转换工具（dp2px、px2dp、sp2px、px2sp、屏幕宽高）
3. DeviceIdUtil : 获取手机唯一标示