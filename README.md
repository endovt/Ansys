Universidade Federal de Santa Catarina

Centro Tecnológico de Joinville

EMB5764 - Estruturas Navais II

Prof. Vitor Takashi Endo, Dr.Eng.

---

# Resumo

<!-- Contexto -->
Neste projeto são descritos os modelos em elementos finitos de estruturas navais (primária, secundária e terciária).
Os conceitos teóricos são apresentados na disciplina EMB5764 - Estruturas Navais II, do curso de Engenharia Naval da Universidade Federal de Santa Catarina.

<!-- Objetivo -->
O objetivo é complementar o material didático por meio da apresentação de resultados numéricos.
Espera-se um melhor entendimento acerca dos fenômenos, como a visualização da configuração deformada da estrutura e a distribuição de tensões.

<!-- Script em APDL: parametrização do modelo -->
O script foi elaborado em APDL, uma linguagem de programação do Ansys, permitindo a construção automática do modelo em elementos finitos a partir de parâmetros inseridos pelo usuário.

# Instruções gerais

Link para download da versão estudantil do Ansys: 
https://www.ansys.com/academic/students/ansys-student

Após a instalação do programa, seguir os seguintes passos:
1. Abrir o Ansys Mechanical APDL Product Launcher.
- Definir a pasta de trabalho (working directory)
- Definir o nome dos arquivos do projeto (job name)
- Inicializar a interface gráfica: Run
2. Ler o arquivo de entrada da simulação
- Menu: File, Read Input From...
- Alternativamente, é possível ler o arquivo de entrada com o comando /INPUT, por exemplo:

```
/INPUT,secundaria,apdl  
```

## Estrutura Primária 

Este script requer um arquivo com extensão .txt com a curva de cargas (q) ao longo do comprimento da embarcação (x-pos), sendo esperado que a embarcação esteja devidamente em equilíbrio.
A primeira linha do arquivo é o cabeçalho, que será desconsiderada durante a importação.
Os dados se iniciam efetivamente a partir da segunda linha; é esperado que a tabela siga o formato "separado por tabulações".
Editores de planilhas, como o Excel, normalmente permitem exportar arquivos de texto com este formato.
O arquivo gerado não deve conter linhas em branco.
Salienta-se que o ponto é utilizado como separador decimal.
A seguir, temos um exemplo:
```
x-pos (m) q (N/m)
0 -492.752376
1 -492.752376
2 -471.209033
3 -449.477859
4 -427.596169
```
<!-- apresentação da tabela -->
<!-- | x-pos (m) | q (N/m)     |
| ------ | ---------- |
| 0	     |-492.752376 |
| 1	     |-492.752376 |
| 2	     |-471.209033 |
| 3	     |-449.477859 |
| 4	     |-427.596169 | -->

Ademais, é importante frisar que o arquivo .txt deve ser incluído na pasta de trabalho (Working directory, definido no Ansys Product Launcher).
Com a execução do script, o programa perguntará qual o nome do arquivo de texto.

## Estrutura Secundária e Terciária

Com a leitura do arquivo de entrada, o script solicitá os parâmetros da simulação.

Obs.: A versão corrente do script emprega o comando MULTIPRO, permitindo a inclusão de todos os parâmetros numa única janela.
O referido comando não funciona adequadamente se o script for executado diretamente do UIDL (por exemplo, se as instruções forem coladas no Command Prompt do Ansys); portanto, para o devido funcionamento do script, é necessário seguir as instruções indicadas neste documento.

# Code description, according to ChatGPT

## primaria.apdl

"This code performs finite element analysis on a beam structure loaded by a line load.
The external load data is read from a text file, and the beam is modeled using beam element loops. 
The main objectives of this analysis are to obtain the bending moment diagram and the shear force diagram of the beam. 
The code also defines some variables, creates arrays and tables, and includes macros for viewing results. 
Additionally, the code sets material properties, applies boundary conditions, and applies weak springs to improve convergence."

## secundaria.apdl

"This code is an APDL script for creating a finite element analysis model of a rectangular plate (shell) with reinforcement (beam).
It starts with defining design variables such as plate dimensions (shell), reinforcement dimensions (beam), loading condition, and mesh parameter. 
Then it creates the geometry using keypoints, lines, and areas.
The material properties and section properties are defined next. 
The script generates the mesh by defining the element types, mesh size, and selecting elements for meshing.
Boundary conditions such as displacement and symmetry constraints are applied to certain nodes.
The script creates a component manager and a toolbar with shortcuts for element and plot selections. 
Finally, it solves the model and produces output results for stress and deformation."

## terciaria.apdl

"The code is performing a finite element analysis for a shell plate under uniform pressure loading using ANSYS software. 
It starts by defining the design variables such as the plate dimensions, pressure, and mesh size. 
Then it creates the geometry using the rectangular command and defines the material, section, and mesh. 
Afterwards, it applies the boundary conditions and the pressure load, runs the solution, and plots the results. 
Finally, it prints the stress results at two points of interest. 
The code also includes macros and shortcuts for ease of use."