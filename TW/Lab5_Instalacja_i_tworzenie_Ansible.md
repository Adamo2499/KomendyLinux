## Instalowanie Ansible (wymagany jest Python)
```bash
sudo apt update
sudo apt install ansible #
```
## Konfiguracja hostów w Ansible

```bash
sudo nano /etc/ansible/hosts # edycja plików z hostami
ansible-inventory --list -y # wyświetlenie listy hostów
ansible all -m ping -u root # testowanie połączenia poprzez wysłanie wiadomości ping do grupy all jako użytkownik root
```

```
[group_name]
hostname ansible_host=host_ip ansible_user=username
```



