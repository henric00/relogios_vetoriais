# Projeto — Relógios Vetoriais com MPI

Implementação, em C com MPI, do exemplo de Relógios Vetoriais
apresentado na atividade da disciplina PPC.

O programa utiliza três processos (`P0`, `P1` e `P2`) e reproduz a sequência de eventos internos, envios e recebimentos mostrada na figura fornecida pelo professor.

## Integrantes

- Augusto Henrique da Silva Santana
- Carlos Henrico Fontes Cabral


## Arquivo principal

- `rvet.c` — implementação dos relógios vetoriais utilizando MPI.

## Compilação

Em um ambiente com MPI instalado:

```bash
mpicc -o rvet rvet.c
```

## Execução

O programa deve ser executado com exatamente três processos:

```bash
mpiexec -n 3 ./rvet
```

## Estados esperados

Ao final da sequência da figura, os relógios vetoriais são:

- `P0`: `(7,1,2)`
- `P1`: `(6,3,2)`
- `P2`: `(4,1,3)`

A ordem das linhas impressas no terminal pode variar, pois os processos MPI executam concorrentemente. O importante é que os estados associados aos eventos correspondam à sequência representada na figura.

## Regras implementadas

- Evento interno: o processo incrementa sua própria posição no vetor.
- Envio: o processo incrementa sua posição e envia o vetor completo.
- Recebimento: o processo recebe o vetor remoto, incrementa sua posição e realiza a fusão utilizando o maior valor em cada posição.
