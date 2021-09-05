# ipseweep
script in bash to seweep your network

#!/bin/bash																								< mostra o local do bash

if [ "$1" == "" ]																							< se o argumento 1 for igual a nada					
then																											< então
echo "voce esqueceu de colocar o IP"																< mostre “voce esqueceu de colocar o ip”
echo "Syntaxe: ./findip.sh 192.168.4"																< mostre “Syntaxe: ./findip.sh 192.168.4”

else																											< caso contrario
for ip in `seq 1 254`; do																				< para ip em `sequencia de 1 a 254`; faça
ping -c 1 $1.$ip | grep "64 bytes" | cut -d " " -f 4 | tr -d "():" &							< pinga os ips e limpa o resultado
done																											< saia
fi																												< fim de se

UM USO INTERESSANTE

./findip.sh 192.168.4 > ips.txt

for ip in $(cat ips.txt) ; do nmap $ip; done < cria um looping no nmap com os ips colhidos pelo script
