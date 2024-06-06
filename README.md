# ROM_realme_17
MOD ROM realme C17 

Device: Realme C17 
Codename: RMX2101
Region: TH
Version: RMX2101export_11_C.13
System: realme UI 2.0
Size: 3.84 GB
Type: EDL Mode
Release Date: 25/05/2022
Package Name: RMX2101export_11_C.13_2022042711500000
Download[Click link realme.net](https://rms01.realme.net/SW/realme%20service/realme%20C17/20676/RMX2101export_11_C.13_2022042711500000.7z)
# Vendor Source Code
1. การสร้าง Custom ROM

ขั้นตอนที่ 1: ตั้งค่าเครื่องมือสำหรับการพัฒนา ROM

    ติดตั้ง Linux Environment:
        การพัฒนาระบบปฏิบัติการ Android มักจะทำในระบบ Linux เช่น Ubuntu

    ติดตั้งเครื่องมือที่จำเป็น:
        ติดตั้งเครื่องมือที่จำเป็นทั้งหมดสำหรับการพัฒนาระบบปฏิบัติการ Android

        bash

        sudo apt-get update
        sudo apt-get install openjdk-8-jdk
        sudo apt-get install git
        sudo apt-get install repo

ขั้นตอนที่ 2: การตั้งค่า Android Source Code

    ดาวน์โหลด Android Source Code:
        ใช้คำสั่ง repo เพื่อดาวน์โหลด Android Source Code

        bash

        mkdir ~/android
        cd ~/android
        repo init -u https://android.googlesource.com/platform/manifest -b android-11.0.0_r17
        repo sync

ขั้นตอนที่ 3: การเพิ่ม Vendor Source Code

    แตกไฟล์ Vendor Source Code:
        แตกไฟล์ realme_C15_C17_7i-AndroidR-vendor-source-master.zip และคัดลอกไปยังโฟลเดอร์ที่เหมาะสมใน source tree ของ Android

        bash

    unzip realme_C15_C17_7i-AndroidR-vendor-source-master.zip -d ~/android/vendor/realme/C15_C17_7i

ตั้งค่า environment:

    ตั้งค่า environment สำหรับการสร้าง ROM

    bash

        source build/envsetup.sh
        lunch <device_codename>-userdebug

ขั้นตอนที่ 4: การสร้าง Custom ROM

    เริ่มการสร้าง ROM:
        ใช้คำสั่ง make เพื่อเริ่มการสร้าง ROM

        bash

        make -j$(nproc)

    ไฟล์ที่สร้างขึ้น:
        เมื่อการสร้าง ROM เสร็จสมบูรณ์ ไฟล์ที่สร้างขึ้นจะอยู่ในโฟลเดอร์ out/target/product/<device_codename>/

2. การใช้ Vendor Source Code ในการพัฒนา Custom Kernel

ขั้นตอนที่ 1: การตั้งค่า Kernel Source Code

    ดาวน์โหลด Kernel Source Code:
        ดาวน์โหลด Kernel Source Code สำหรับ Realme C17

        bash

        git clone https://github.com/realme-kernel-opensource/realmeC17-kernel.git
        cd realmeC17-kernel

    เพิ่ม Vendor Source Code:
        คัดลอกไฟล์จาก realme_C15_C17_7i-AndroidR-vendor-source-master.zip ไปยังโฟลเดอร์ vendor/

ขั้นตอนที่ 2: การปรับแต่ง Kernel

    แก้ไขและปรับแต่ง Kernel:
        ทำการแก้ไขและปรับแต่ง Kernel ตามความต้องการ

ขั้นตอนที่ 3: การสร้าง Kernel

    ตั้งค่า environment:
        ตั้งค่า environment สำหรับการสร้าง Kernel

        bash

    export ARCH=arm64
    export SUBARCH=arm64
    export CROSS_COMPILE=aarch64-linux-android-

สร้าง Kernel:

    ใช้คำสั่ง make เพื่อสร้าง Kernel

    bash

        make O=out <device_defconfig>
        make O=out -j$(nproc)

คำแนะนำเพิ่มเติม

    ศึกษาและทดสอบ: การพัฒนาและปรับแต่ง ROM และ Kernel ต้องมีการศึกษาและทดสอบอย่างละเอียด
    ความปลอดภัย: ตรวจสอบความปลอดภัยของการปรับแต่งและพัฒนาเพื่อป้องกันปัญหาที่อาจเกิดขึ้น
