# Hướng dẫn buid Vlc-qt lib:

### 1. Clone code:
https://github.com/anhtuanbkfet/vlc-qt.git

### 2. Download libVLC (Thường dùng luôn bản pre-built trên trang chủ)
https://get.videolan.org/vlc/3.0.18/win64/ 	---> chọn bản vlc-3.0.18-win64.7z

### 3. Mở CmakeGUI, add thêm Cach Entry:
VLC_PLUGIN_PATH 		---> "đường dẫn tới thư mục 'plugins' của VLC"
CMAKE_DEBUG_POSTFIX 	---> "D"

### 4. Sửa Config CMAKE_INSTALL_PREFIX (Optional)
(Optional) Dùng thư mục này để không cần copy vào thư mục QT nữa ----> C:\Qt\5.15.2\msvc2019_64

### 5. Config các PATH: Qt5Core_DIR, Qt5Mql_DIR,...
Qt5Core_DIR 		---> C:\Qt\5.15.2\msvc2019_64\lib\cmake\Qt5Core
Qt5Mql_DIR			---> C:\Qt\5.15.2\msvc2019_64\lib\cmake\Qt5Qml

Tương tự với các Dir lỗi (Not found) khác.

### 6. Sửa lại các Lib path nếu cần:
LIBVLCCORE_LIBRARY 	
LIBVLC_LIBRARY 		
LIBVL_INCLUDE_DIR	

### 7. Gen project and build.
Mowe solution với VS2019, buid project ALL_BUILD, sau đó build project INSTALL
- Nếu gặp lỗi MSB3073 (The command "setlocal ...):
- Vào thư mục build, file cmake_install.cmake sửa đường dẫn ở line 45,46 thành
```
"C:/Qt/5.15.2/msvc2019_64/bin/libvlc.dll"
"C:/Qt/5.15.2/msvc2019_64/bin/libvlccore.dll"
```

- Nếu ở bước 4, CMAKE_INSTALL_PREFIX không được set thành C:\Qt\5.15.2\msvc2019_64:
---> Copy toàn bộ folder INSTALL vào C:\Qt\5.15.2\msvc2019_64
 
