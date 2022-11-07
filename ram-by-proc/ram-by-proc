#!/bin/bash
if [[ -z $1 ]]; then
    return
fi
sum=0
for pid in $(pidof $1); do
    ram=$(ps aux | grep $pid | tail -n 1 | awk '{ print $6 }')
    sum=$(( $sum + $ram ))
done
f=$(numfmt --to iec --format "%8.1f" $(( sum*1024 )))
f=$(echo $f | sed "s/\s//g")
printf "$f\n"
