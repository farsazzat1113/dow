@echo off
echo ====== بدء التنظيف الشامل ======
echo.

:: 1. تنظيف ملفات النظام المؤقتة
echo [1/6] تنظيف ملفات Temp...
del /q/f/s %TEMP%\*
del /q/f/s C:\Windows\Temp\*

:: 2. تنظيف ذاكرة DNS
echo [2/6] تنظيف ذاكرة DNS...
ipconfig /flushdns

:: 3. إصلاح ملفات النظام التالفة
echo [3/6] فحص وإصلاح ملفات النظام...
sfc /scannow

:: 4. تنظيف ملفات Roblox القديمة
echo [4/6] تنظيف ملفات Robكس القديمة...
rmdir /q/s "%LOCALAPPDATA%\Roblox" 2>nul
rmdir /q/s "%LOCALAPPDATA%\Temp\Roblox" 2>nul

:: 5. إصلاح صورة النظام
echo [5/6] إصلاح صورة النظام (DISM)...
DISM /Online /Cleanup-Image /RestoreHealth

:: 6. تنظيف القرص
echo [6/6] تنظيف القرص...
cleanmgr /sagerun:1

echo.
echo ====== التنظيف انتهى! ======
echo يرجى إعادة تشغيل الجهاز.
pause
