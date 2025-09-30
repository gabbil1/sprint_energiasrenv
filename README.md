Sistema Integrado com Inversor GoodWe (Protótipo Simulado em Python)
Equipe Envolvida

Vinicius Mello Siqueira 565257
Arthur de Souza Matos Dias 566068 
Guilherme Carreri 565676
gabriel ramos moreira 564074


Esquema de Integração dos Componentes

O protótipo simula a operação de um sistema fotovoltaico com inversor GoodWe, bateria de 10 kWh, cargas residenciais (perfil base + picos manhã/noite), automação de carga inteligente (boiler 1,2 kW) e comando de voz (simulado).

Diagrama de Blocos
[ Painel FV ] -> (DC) -> [ Inversor GoodWe (simulado) ] -> (AC) -> [ Cargas ]
                                           |-> [ Bateria (10 kWh) ]
                                           |-> [ Automação (Smart Load) ]
                                           |-> [ Comando por Voz (simulado) ]
                                           |-> [ CSV + Visualizações ]

Fluxograma da Lógica de Automação

Leitura: PV, Carga, SOC da Bateria.

Se excedente + SOC > 80% → liga Smart Load.

Se SOC < 60% ou não houver excedente → desliga Smart Load.

Comando de voz → força ON por 60 min (simulação de Alexa/Google).

Registra dados em CSV + gráficos.

Justificativa Técnica

GoodWe (simulado): marca amplamente usada em prosumers reais, com limites AC típicos (4,6 kW).

Bateria: flexibiliza operação, reduz importação da rede e aumenta autoconsumo.

Automação inteligente: aproveita excedentes solares em tempo real, elevando eficiência.

TOU (Time of Use): tarifação simulada reforça a relevância da bateria no horário de pico.

Python: linguagem leve, com bibliotecas robustas (numpy, pandas, matplotlib) e fácil visualização.

Resultados e Dados Funcionais
1. PV Generation vs Load

📊 Arquivo: plot_pv_load.png
Mostra picos diurnos de até 4,6 kW e vales noturnos atendidos pela bateria/rede.

2. Estado de Carga da Bateria

📊 Arquivo: plot_battery.png
SOC cresce durante o dia (excedentes) e cai no pico tarifário noturno.

3. Importação e Exportação de Rede

📊 Arquivo: plot_grid.png
Exportação elevada em horários de sol, importação apenas em períodos noturnos/pico.

4. Estados de Automação

📊 Arquivo: plot_automation.png
Smart Load liga com SOC alto + excedentes; Voice Override força ON por 1h.

5. CSV de Saída

📂 Arquivo: goodwe_sim_results.csv
Inclui timestamp, PV, carga, SOC, potência bateria, import/export, preço TOU, flags de automação.

Conexão com os Conteúdos da Disciplina

Estruturas de Dados: vetores e DataFrames organizam séries temporais de medição.

Algoritmos: cálculo de SOC, controle com histerese (liga/desliga smart load), fluxo de energia.

Automação & IA: integração de regras condicionais e simulação de comandos por voz.

Visualização: gráficos temporais para análise de comportamento do sistema.

Sustentabilidade, Automação e Eficiência Energética

Redução de importação da rede → menor emissão de CO₂.

Uso inteligente da bateria e smart load → aumento de autoconsumo.

Integração com voz (Alexa/Google) → mais conforto e adesão do usuário.

Potencial de expansão → previsão solar, otimização tarifária, integração com IoT (ESP32/relés).

Repositório GitHub – Organização Recomendada

prototype_goodwe_sim.py → código principal (simulação).

goodwe_sim_results.csv → resultados tabulares.

plot_pv_load.png, plot_battery.png, plot_grid.png, plot_automation.png → visualizações.

README.md ou PDF → relatório técnico/documentação.

/diagrams/ → fluxogramas, diagramas de blocos.

/hardware/ → esquemas futuros (quando integrar com medidores/relés reais).

Conclusão

O protótipo simulado confirma a viabilidade da integração solar + bateria + automação inteligente + voz, mostrando ganhos em eficiência energética e autonomia. O trabalho reforça o domínio de estruturas de dados, algoritmos e modelagem computacional aplicados a um problema real de energia renovável.

Próximos passos: integração com APIs reais da GoodWe SEMS, controle físico via IoT e uso de previsões meteorológicas para otimização.# sprint_energiasrenv
