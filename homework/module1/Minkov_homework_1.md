Завдання 1 (Перероблено):

ddminkov@ddminkov-virtual-machine:~/Desktop$ ls ~
Desktop  Documents  Downloads  Music  Pictures  Public  Templates  Videos
ddminkov@ddminkov-virtual-machine:~/Desktop$ cd ~/Downloads
ddminkov@ddminkov-virtual-machine:~/Downloads$ ls
ddminkov@ddminkov-virtual-machine:~/Downloads$ > newfile.txt
ddminkov@ddminkov-virtual-machine:~/Downloads$ cat newfile.txt
ddminkov@ddminkov-virtual-machine:~/Downloads$ cd /home/ddminkov
ddminkov@ddminkov-virtual-machine:~$ cd ~
ddminkov@ddminkov-virtual-machine:~$ cd ~/Downloads
ddminkov@ddminkov-virtual-machine:~/Downloads$ ls
newfile.txt

Завдання 2:

1. Який ключ ls показує приховані файли?
Відповідь: Ключ -a (all). Наприклад: ls -a.

2. Який ключ у cat нумерує рядки?
Відповідь: Ключ -n (number). Наприклад: cat -n file.txt.

3. Чим відрізняються man і -help?
Відповідь: man (manual): Це повноцінна системна документація, яка відкривається в окремому інтерфейсі (пейджері). Вона містить детальний опис, приклади, імена авторів та технічні подробиці.
--help: Це короткий прапорець самої команди, який виводить стислу довідку щодо синтаксису та доступних ключів прямо в термінал. Це швидше, але менш детально.

Завдання 3:

Міні беш-сценарій:

cd ~/Documents
echo "Створюємо новий файлик" > homework_file.txt
ls -l
cd /tmp
cd -
man ls
