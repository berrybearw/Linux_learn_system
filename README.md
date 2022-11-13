# Linux_learn_system
內核資訊查看

sysctl -a 全部查看

threads 查看 : sysctl -a | grep threads

![image](https://user-images.githubusercontent.com/96226780/201522577-2210c728-9d32-4f4e-9741-5b5c8b1a41ca.png)

解說 : To get the sum of all threads running in the system

參考 : 
* https://stackoverflow.com/posts/37713259/revisions

ps -eo nlwp | tail -n +2 | awk '{ num_threads += $1 } END { print num_threads }'

* [https://iter01.com/395377.html](https://iter01.com/395377.html)
* [https://www.ibm.com/docs/en/db2/11.5?topic=linux-troubleshooting-tasksmax-set-too-low](https://www.ibm.com/docs/en/db2/11.5?topic=linux-troubleshooting-tasksmax-set-too-low)

計算 systemctl Task , Mem 使用量 : watch 'systemctl status gas-topprd | grep -C 2 Tasks'

![image](https://user-images.githubusercontent.com/96226780/201522633-91480df5-970e-496e-8e67-f4b4660044d9.png)

立即讀取系統資訊 : systemctl daemon-reload

pid_max ( 最大上限基準 ) 大於 kernel.threads_max ( 整體設定基準 )

Task ( 個別設定數值 ， 沒設定會用整體設定 80 % 來當標準數值 )
