
# TASK7.1 #

A. 
I Created a script that uses with keys
- /home/ubuntu
- touch 711.sh
- chmod +x 711.sh
- ./711.sh

```
#!/bin/bash
function myfuncall {
ip a
}
function myfunctarget {
netstat -tulpn
}
function myfuncwithoutparam {
 echo "The --all key displays the IP addresses and symbolic names of all hosts in the current subnet"
 echo "The --target key displays a list of open system TCP ports"
}

if [ -n "$1" ]; then
  if [ "$1" = "--all" ];
then
  myfuncall
  fi
if [ "$1" = "--target" ];
then
  myfunctarget
fi
else
  myfuncwithoutparam
fi

```




B1.
- From which ip were the most requests? 
- /mnt/d/task7$
- touch out_script1
- chmod 777 out_script1
- 71b.sh
```
#!/bin/bash
file_out=out_script1
grep -E -o "([0-9]{1,3}[\.]){3}[0-9]{1,3}" $1 | sort | uniq -c | sort -gr > $file_out
{
read line1
} < $file_out
echo $line1
```
- ./71b.sh apache_logs.txt
-  (71b.jpg) - ![71b.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m7/task7.1/71b.jpg)


B2.
- What is the most requested page? 
- touch out_script2
- chmod 777 out_script2 
-72b.sh
```
#!/bin/bash
file_out=out_script2
awk '{print $7}' $1 | sort | uniq -c | sort -gr > $file_out
{
read line1
} < $file_out
echo $line1
```
- ./72b.sh apache_logs.txt
-  (72b.jpg) - ![72b.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m7/task7.1/72b.jpg)

B3.
- How many requests were there from each ip?
- /mnt/d/task7$
- 73b.sh
```
#!/bin/bash

grep -E -o "([0-9]{1,3}[\.]){3}[0-9]{1,3}" $1 | sort | uniq -c | sort -gr

```
- ./73b.sh apache_logs.txt
-  (73b.jpg) - ![73b.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m7/task7.1/73b.jpg)

B4.
-What non-existent pages were clients referred to? 
-74b.sh
```
#!/bin/bash
patern=error404
awk '/'$patern'/{print $7,$15}' $1 | sort | uniq -c
```
- ./74b.sh apache_logs.txt
- (74b.jpg)
- (74b.jpg) - ![74b.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m7/task7.1/74b.jpg)

B5.
- What time did site get the most requests?
- touch output7
- chmod 777 output7
- touch output8
- chmod 777 output8
- touch out_output9
- chmod 777 out_output9
- 75bb.sh

```
#!/bin/bash

file_out=output7

awk '{print $4}' $1 > $file_out

awk '{split($1, a, ":"); print a[2]}' output7 > output8

file_out1=out_output9
awk '{print $1}' output8 | sort | uniq -c | sort -gr > $file_out1
{
read line1
} <$file_out1
echo Kol_hour
echo $line1
```
- out_output9
- (75bb1.1.jpg) - ![75bb1.1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m7/task7.1/75bb1.1.jpg)
- ./75bb.sh apache_logs.txt
- (75bb1.2.jpg) - ![75bb1.2.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m7/task7.1/75bb1.2.jpg)


B52.
- What time did site get the most requests?
- I found in apache_logs.txt the ip, were the most requests. I asigned thi IP to variable $file_out3 and outputed from apache_logs.txt this IP and date, time.

-touch out_script4
- chmod 777 out_script4
-touch out_script5
- chmod 777 out_script5
- 75b.sh
```
#!/bin/bash
file_out=out_script4
awk '{print $1}' $1 | sort | uniq -c | sort -gr > $file_out
{
read line1
} < $file_out
echo $line1

file_out2=output5
awk 'NR==1 {print $2; exit}' out_script4 > $file_out2

file_out3=`awk 'NR==1 {print $2; exit}' out_script4`
echo $file_out3


awk -v c=$file_out3 '($1 == c) {print $1,$4}' apache_logs.txt
```

- ./75b.sh apache_logs.txt
- (75b.jpg) - ![75b.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m7/task7.1/75b.jpg)



                                                              
B6.
- What search bots have accessed the site? 

-76b.sh
``` 
#!/bin/bash
file_out=out_script3
awk '/(bot|Bot)/{print $14}' $1 | sort | uniq -c | sort -gr | egrep -i bot

```
- ./76b1.sh apache_logs.txt
-(76b1.jpg)
- (76b1.jpg) - ![76b1.jpg](https://github.com/karachko/DevOps_online_Chernivtsi_2021Q2/blob/main/m7/task7.1/76b1.jpg)
