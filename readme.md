# ���°�װһ��Ubuntu��ϵͳ
lxrun /uninstall /full
lxrun /install

# Register the trusted Microsoft signature key:
curl https://packages.microsoft.com/keys/microsoft.asc | gpg --dearmor > microsoft.gpg
sudo mv microsoft.gpg /etc/apt/trusted.gpg.d/microsoft.gpg

# Register the Microsoft Product feed
sudo sh -c 'echo "deb [arch=amd64] https://packages.microsoft.com/repos/microsoft-ubuntu-xenial-prod xenial main" > /etc/apt/sources.list.d/dotnetdev.list'

# Install .NET SDK
sudo apt-get install apt-transport-https
sudo apt-get update
sudo apt-get install dotnet-sdk-2.1.4

# ��Ҫ�������� vsdbg ���ص���ϵͳ������bash
sudo apt-get install unzip
curl -sSL https://aka.ms/getvsdbgsh | bash /dev/stdin -v latest -l ~/vsdbg

# ��װSSH,��ϵͳ���ͨ��,��Ϊϵͳ��ͬ������Ҫ��װSSH������, unzip �� curl �� wget �����
sudo apt-get install openssh-server unzip curl

# ��װSSH��,ϵͳ�����ܷ��ʱ�����ϵͳ�Ķ˿���ͨ��,����Ҫ����һ��SSH�������������ļ�
sudo nano /etc/ssh/sshd_config

# �ֱ��ҵ��������������޸�,�޸ĺ����������:
UsePAM no
UsePrivilegeSeparation no
PasswordAuthentication yes
#PermitRootLogin prohibit-password
PermitRootLogin yes
Port 2222

# generate SSH keys for the SSH instance:
sudo ssh-keygen -A

# ���������SSH����
sudo service ssh --full-restart

# ÿ������Bash����ʱ����Ҫ��������SSH Service
sudo service ssh start