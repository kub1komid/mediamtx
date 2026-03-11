````
git clone https://github.com/kub1komid/mediamtx.git
````


````
tar -xzf mediamtx_v1.15.0_linux_amd64.tar.gz
````
````
chmod +x mediamtx
````
./mediamtx

````
cp mediamtx /usr/local/bin
````
````
cp mediamtx.yml /usr/local/etc
````


paths:
  # example:
  # my_camera:
  #   source: rtsp://my_camera
  cam1:
      source: 'rtsp://admin1:admin123@192.168.137.252:554/cam1/h264'
  # Settings under path "all_others" are applied to all paths that
  # do not match another entry.
  all_others:

sudo nano /etc/systemd/system/mediamtx.service

[Unit]
Description=MediaMTX Media Server
After=network.target

[Service]
Type=simple
ExecStart=/usr/local/bin/mediamtx /usr/local/etc/mediamtx.yml
Restart=always
RestartSec=3

[Install]
WantedBy=multi-user.target


# Muat ulang konfigurasi
sudo systemctl daemon-reload

# Jalankan MediaMTX sekarang
sudo systemctl start mediamtx

# Aktifkan agar otomatis jalan saat booting
sudo systemctl enable mediamtx
