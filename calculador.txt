#!/bin/bash

while true; do
	echo "Calculadora"
	echo "Escolha a operação:"
	echo "1 - Adição"
	echo "2 - Subtração"
	echo "3 - Multiplicação"
	echo "4 - Divisão"
	echo "5 - Sair"

read -p "Opção: " opcao
if [ "$opcao" -eq 5 ]; then
	echo "Saindo..."
	break
fi

read -p "Digite o primeiro número: " num1
read -p "Digite o segundo número: " num2

case $opcao in
	1) resultado=$(echo "$num1 + $num2" | bc);;
	2) resultado=$(echo "$num1 - $num2" | bc);;
	3) resultado=$(echo "$num1 * $num2" | bc);;
	4)
	   if [ "$num2" -eq 0 ]; then
		echo "Erro: Divisão por zero!"
		continue
	   fi
	   resultado=$(echo "scale=2; $num1 / $num2" | bc);;
	*) echo "Opção Invalida!"; continue;;
esac
	echo "Resultado: $resultado"
done
