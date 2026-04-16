[🇺🇸 Read in English](README.md) | 🇵🇹 Português

# 🚜 Realistic Engine Temperature (RET)

| | Versão | Estado |
|:---:|:---|:---:|
| 🟢 | **7.3.0** — Versão Estável | ![Stable](https://img.shields.io/badge/Estavel-7.3.0-brightgreen) |
| 🧪 | **8.1.0** — Beta Público | ![Beta](https://img.shields.io/badge/Beta-8.1.0-orange) |

**Farming Simulator 25**

O **Realistic Engine Temperature (RET)** é um mod de física avançada concebido para o Farming Simulator 25. Ele desativa a temperatura mecânica nativa e utópica do jogo base, substituíndo-a por um modelo termodinâmico hiper-realista.

Quer tenhas um velho trator a gasóleo, uma ceifeira antiga arrefecida a ar ou um modelo elétrico topo de gama, o RET simulará exatamente como o calor é gerado, dissipado e as potenciais avarias no meio do processo!

---

## 🌟 Principais Funcionalidades

### 1. Sistema Termodinâmico Ativo
O calor não sobe de forma linear. Ele é calculado a cada milissegundo baseado em:
- **Carga do Motor (Load):** Puxar um arado pesado numa subida a 100% de Esforço vai gerar um calor extremo que leva a mecânica ao seu limite.
- **RPMs / Ralenti:** Motores deixados ao ralenti geram apenas calor base. Levá-los ao Redline em ponto morto gera fricção e calor.
- **Clima e Vento:** Trabalhar num dia chuvoso e frio diminui o calor. Conduzir a 50 km/h gera um fluxo de arrasto natural (Wind Cooling) que ajuda a arrefecer independentemente da ventoinha.
- **DFCO (Corte de Injeção por Desaceleração):** Quando o trator desce engatado sem acelerar, o motor corta a injeção de combustível e deixa de gerar calor — exatamente como um motor real.

### 2. Cinco Perfis de Veículo
O Farming Simulator não faz distinção dos motores, mas o RET faz! O mod deteta o consumo do teu veículo (Diesel, Metano ou Elétrico) e aplica físicas completamente diferentes. Podes também forçar um perfil manualmente a qualquer momento via consola:
*   🟢 **Arrefecimento a Água (Padrão):** O clássico bloco com anticongelante e termostato. Mantém o motor nos 80ºC a 90ºC. Usa válvula de temperatura dinâmica.
*   💨 **Arrefecimento a Ar (Air-Cooled):** Ideal para clássicos (Ex: Porsches antigos). Sem Inércia térmica! A refrigeração depende puramente do rodar da ventoinha acoplada ao motor (RPMs). Se estiveres a fazer trabalho de TDF muito pesado com o trator estacionário, ele vai aquecer perigosamente rápido!
*   ⚡ **Veículos Elétricos (EV / Baterias):** Ignoram ferveduras de 100ºC. Funcionam num perfil apertado de proteção térmica (20ºC - 65ºC). Parados não geram calor, funcionam puramente pelo esforço extremo de descarga da corrente. Têm um BTMS com aquecimento próprio se estiverem ao frio e ventilação eletrificada.
*   🚗 **Carro (Veículo Ligeiro) *(NOVO na v8.1!)***:  Os carros modernos aquecem muito mais rápido (~2 min até 80ºC). A válvula do termostato abre entre 80ºC e 87ºC. O arrefecimento é passivo por vento enquanto o carro anda (sem ventoinha), e uma **ventoinha elétrica independente** só ativa quando a temperatura atinge os 95ºC. Todas as regras de dano a frio e sobreaquecimento aplicam-se igualmente.
*   🚫 **Sem RET (NoRET) *(NOVO na v8.1!)***:  Remove completamente um veículo específico da simulação do RET. O controlo de temperatura nativo do jogo toma conta. Apenas a barra de título do RET é mostrada a cinzento quando o modo debug está ativo.

### 3. Válvulas e Termostatos Inteligentes
No trator padrão (Água), a física é controlada por um **Termostato**. Durante os primeiros minutos da manhã ele está fechado (0%) a reter calor usando injeção rica de combustível (fast warmup). Ao pisar os 85ºC a válvula abre dinamicamente em percentagem para invocar as ventoinhas do Radiador Central e travar a subida!

### 4. Sistema de Danos Avançado e Avarias Físicas Reais *(NOVO na v8!)*
O RET introduz três camadas independentes de consequências mecânicas:

**Camada 1 — Avaria da Válvula do Termostato (Estocástica):**
Quando o teu trator acumula desgaste suficiente (configurável, padrão 70%), um sorteio determina se a **válvula do termostato encrava fisicamente**:
*   **Encravar Aberta:** O trator não consegue reter calor e trabalha cronicamente a frio, danificando os cilindros sob carga.
*   **Encravar Fechada:** O fluxo para o radiador fica completamente bloqueado. A água ferve rapidamente, o alarme da cabine soa e o motor sofre dano imediato até parar!

Reparar o trator na oficina repõe o estado da válvula e dá-lhe uma nova hipótese.

**Camada 2 — Paragem por Sobreaquecimento Crítico:**
Se a temperatura do motor subir **5ºC acima do limiar de dano** (padrão: acima de 115ºC), existe uma probabilidade aleatória crescente de o motor **se parar a si próprio** para evitar uma falha catastrófica. Quanto mais quente estiver, maior a probabilidade por segundo.

**Camada 3 — Paragem e Bloqueio de Arranque por Dano *(NOVO na v8!)***:
O estado geral do trator afeta agora diretamente a capacidade do motor de funcionar:
*   **Entre 80% e 95% de dano:** O motor tem uma probabilidade aleatória crescente de **parar no meio do trabalho**. Quanto mais próximo de 95%, maior a probabilidade por segundo.
*   **Acima de 95% de dano:** O motor **não consegue arrancar de todo**. Leva o trator à oficina antes que seja tarde demais!

*(Todos os limiares e probabilidades são totalmente configuráveis no Config.xml).*

### 5. Dano por Esforço a Frio
Não pegues no trator às 6h da manhã e comeces a lavrar a direito!
O mod pune severamente tratores levados ao limite de RPMs ou a altos níveis de Carga quando o medidor da temperatura ainda está a frio. Aquece o teu trator primeiro!

### 6. Penalização por Sujidade (Lodo no Radiador)
Trabalhar na lama o dia todo cobre os favos do maquinário. À medida que o medidor de Sujidade aumenta no FS25, a força máxima de refrigeração do seu radiador cai a pique, tornando os trabalhos de verão impossíveis sem parar ao sol.

---

## 🖥️ A Interface (HUD Adaptativo)
O Mod injeta texto suave e útil no canto do ecrã para monitorização a olho (apenas quando o motor está ligado). O HUD adapta-se automaticamente ao perfil do veículo:
- **RPM Max Seguras:** Mostra se já podes puxar pelo acelerador. Fica a Vermelho se o estiveres a prejudicar!
- **HP e Ajustamentos:** A cavalagem nativa reconhecida a debitar calor (com leituras ativas caso faças reprogramação (Chiptuning) na Oficina!).
- **Load / Carga Média:** A balança constante do teu esforço (% atual e a Média do último minuto de trabalho).
- **Válvula:** Observa a percentagem exata com que a água transita para os painéis refrigeradores.
- **Ventoinha *(só no perfil Carro)*:** Mostra o estado da ventoinha elétrica — `Fan: OFF` (azul) quando a temperatura está abaixo de 95ºC, `Fan: ON (70%)` (verde) quando está a refrigerar ativamente.
- **Sujidade %:** Nível total de sujidade do radiador e a penalização de arrefecimento ativa.
- **Veículos NoRET:** Apenas a barra de título é mostrada a cinzento, indicando que o veículo está excluído da simulação.

Além disto, o RET apropria-se do sistema de Avisos Nativos (Banner intermitente do ecrã do Farming Simulator) alertando-o de quando forçar trabalho a frio ou no limite do Sobreaquecimento. Os avisos de sobreaquecimento de baterias (EV) são também traduzidos na tua língua de jogo.

---

## 🛠️ Comandos de Consola (Para Utilizadores Avançados)
O sistema tem memória por Trator e sincroniza tudo do lado do Servidor com Multijogador! Podes abrir a consola do jogo com a tecla `~` / `'` e utilizar os atalhos abaixo escrevendo `ret <comando>`:

| Comando | Ação |
| :--- | :--- |
| `ret help` | Mostra o painel de ajuda e todos os atalhos. |
| `ret on` / `ret off` | Liga ou desliga o mod totalmente no save game atual. |
| `ret water` | Força o veículo atual a usar motor Arrefecido a Água (Padrão). |
| `ret air` | Força o veículo atual a ignorar termostatos e a ser Arrefecido a Ar. |
| `ret electric` | Força o veículo atual a usar curva térmica apertada de Lítio (Baterias EV). |
| `ret car` | Força o veículo atual a usar o **perfil Carro** (termostato + ventoinha elétrica). *(Novo na v8.1)* |
| `ret noret` | **Exclui** o veículo atual do RET. O controlo de temperatura nativo toma conta. *(Novo na v8.1)* |
| `ret debug true` | Ativa o modo desenvolvedor cospindo na matemática crua das equações visuais de perda e absorção (+ e -) sob o menu. |
| `ret load` / `ret save` | Lê ou Força gravação dos dados no ficheiro XML de modo instantâneo. |

---

## ⚙️ Personalização Descomprometida e Guia do Config.xml

És criador de servidores de Hard-Roleplay ou um Mestre da Física? O Mod vai criar o ficheiro `modSettings/RealisticEngineTemp/Config.xml` nos teus documentos de jogo mal entres na primeira gravação. Dentro dele tu és literalmente dono das Leis da Física.

> **Sistema de Atualização Inteligente:** Sempre que a versão do mod for atualizada, o sistema retém os teus números do XML e só introduz limpidamente as chaves das versões novas. Nunca mais perderás uma calibração tua.

### 📚 Referência de Variáveis do Config.xml

---

#### 🌐 Geral & Multijogador

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `enableMultiplayerSync` | bool | `true` | Sincroniza as temperaturas do motor entre todos os jogadores no servidor. |
| `enableDataLogging` | bool | `false` | Exporta telemetria do motor em tempo real para um ficheiro `.csv` (para análise em Excel). |
| `logIntervalMs` | number | `1000` | Com que frequência (em ms) é guardada uma linha de telemetria no CSV. |

---

#### 🖥️ HUD & Debug

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `debugMode` | bool | `false` | Ativa o HUD de debug no ecrã com todos os valores de física em tempo real. |
| `hud_ShowTitle` | bool | `true` | Mostra a barra de título do RET e o modo de multijogador. |
| `hud_ShowTempRPM` | bool | `true` | Mostra a temperatura atual e as RPMs. |
| `hud_ShowValve` | bool | `true` | Mostra a percentagem de abertura da válvula do termostato. |
| `hud_ShowFlow` | bool | `true` | Mostra as taxas de geração e dissipação de calor (Gen/Pas/Rad). |
| `hud_ShowEff` | bool | `true` | Mostra a carga do motor e a penalização por sujidade. |
| `hud_ShowLimits` | bool | `true` | Mostra as RPM máximas seguras e os HP (com chiptuning se ativo). |
| `hud_ShowFan` | bool | `true` | Mostra a linha de estado da ventoinha elétrica (apenas perfil Carro). |
| `uiRefreshRateBaseMs` | number | `500` | Intervalo de atualização do HUD em milissegundos (valor base/mestre). |

---

#### 🔥 Física Geral

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `globalSpeed` | number | `1.0` | Multiplicador global da velocidade de toda a física (1.0 = tempo real). |
| `refAmbientTemp` | number | `20.0` | Temperatura ambiente de referência (ºC) usada em todos os cálculos. |
| `minRpmForHeat` | number | `250` | RPM mínimas para o motor ser considerado "em funcionamento" e a gerar calor. |
| `warmupFastMultiplier` | number | `2.0` | Multiplicador de calor no arranque a frio abaixo dos 60ºC (simula injeção rica). |
| `autoCompensateWarmup` | bool | `true` | Ajusta automaticamente o calor base para que o tempo total de aquecimento seja respeitado mesmo com o multiplicador a frio ativo. |

---

#### 🌡️ Termostato (Motor Arrefecido a Água)

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `thermoStart` | number | `85.0` | Temperatura (ºC) a partir da qual a válvula começa a abrir. |
| `thermoFull` | number | `90.0` | Temperatura (ºC) a partir da qual a válvula está completamente aberta. |
| `timeToWarmupIdle` | number | `8.0` | Minutos para o motor aquecer do ambiente (20ºC) até `thermoStart` em ralenti. |
| `timeToOverheatLoad` | number | `12.0` | Minutos para ir de `thermoFull` até `damageStart` a 100% de carga. |
| `timeToCoolDown` | number | `120.0` | Minutos para o motor arrefecer de `thermoStart` até à temperatura ambiente. |
| `damageStart` | number | `110.0` | Temperatura (ºC) a partir da qual o motor começa a sofrer dano. |
| `ambientHeatingModifier` | number | `0.0` | Influência extra do clima no aquecimento por cada ºC acima da referência (0.0 = desligado). |
| `ambientCoolingModifier` | number | `0.05` | Redução do arrefecimento por cada ºC acima da referência (0.05 = 5% por grau). |
| `windCoolingMultiplier` | number | `0.02` | Eficiência extra do radiador por cada km/h de velocidade de deslocação (2% por km/h). |

---

#### ⚡ Veículos Elétricos (EV/Baterias)

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `ev_thermoStart` | number | `25.0` | Temperatura (ºC) a partir da qual o BTMS começa a arrefecer o pack de baterias. |
| `ev_thermoFull` | number | `35.0` | Temperatura (ºC) em que o arrefecimento do BTMS está no máximo. |
| `ev_optimalTemp` | number | `20.0` | Temperatura ideal das baterias. O BTMS aquece até este valor quando a frio. |
| `ev_damageStart` | number | `65.0` | Temperatura (ºC) a partir da qual as baterias começam a sofrer dano. |

---

#### 💨 Motor Arrefecido a Ar

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `air_fanCoolingMultiplier` | number | `1.0` | Multiplicador da potência de arrefecimento pela ventoinha (escala com RPM + vento). |

---

#### 🚗 Perfil Carro *(Novo na v8.1)*

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `car_thermoStart` | number | `80.0` | Temperatura (ºC) a partir da qual o termostato do carro começa a abrir. |
| `car_thermoFull` | number | `87.0` | Temperatura (ºC) a partir da qual o termostato do carro está completamente aberto. |
| `car_warmupTime` | number | `2.0` | Minutos para aquecer do ambiente até `car_thermoStart`. |
| `car_windCoolingMultiplier` | number | `0.05` | Ganho de arrefecimento por km/h em andamento (efeito de vento no radiador). |
| `car_fanOnTemp` | number | `95.0` | Temperatura (ºC) a partir da qual a ventoinha elétrica ativa (independente da válvula). |
| `car_fanPower` | number | `0.70` | Potência da ventoinha elétrica como fração do `cooling_power_max` (70%). |

---

#### 🔧 Dano por Motor Frio

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `enableColdRpmDamage` | bool | `true` | O motor sofre dano se as RPMs excederem o limite seguro com o motor frio. |
| `enableColdLoadDamage` | bool | `true` | O motor sofre dano se a carga exceder o limite seguro com o motor frio. |
| `coldDamageTempThreshold` | number | `60.0` | Temperatura (ºC) abaixo da qual as regras de dano a frio se aplicam. |
| `maxColdDamagePerSec` | number | `0.01` | Dano máximo aplicado por segundo ao forçar com óleo frio. |
| `limitRpmAtRef` | number | `0.60` | RPM máximas seguras como fração das RPM máximas à temperatura ambiente (60%). |
| `limitLoadAtRef` | number | `0.50` | Fração de carga máxima segura com o motor frio (50%). |

---

#### 💥 Avaria do Termostato & Paragem por Sobreaquecimento

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `enableDamageEffects` | bool | `true` | Ativa o sistema de avaria física da válvula do termostato. |
| `damageStartThreshold` | number | `0.70` | Nível de dano do trator (0–1) que despoleta o sorteio de avaria do termostato. |
| `thermostatFailChance` | number | `0.50` | Probabilidade (0–1) de o termostato falhar fisicamente quando o dano cruza o limiar. |
| `damageFullFailure` | number | `0.90` | Nível de dano em que a severidade da avaria atinge 100%. |
| `enableOverheatStall` | bool | `true` | O motor pode parar se a temperatura exceder `damageStart` + delta. |
| `overheatStallStartDelta` | number | `5.0` | Graus acima de `damageStart` antes de começar o risco de paragem (padrão: 115ºC). |
| `overheatStallChancePerSec` | number | `0.015` | Probabilidade base de paragem por segundo em sobreaquecimento crítico (1.5%/s). |

---

#### 🚨 Paragem e Bloqueio de Arranque por Dano *(Novo na v8)*

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `enableDamageStall` | bool | `true` | O motor pode parar ou recusar arrancar com base no desgaste do trator. |
| `damageStallThreshold` | number | `0.80` | Nível de dano (0–1) a partir do qual começa o risco de paragem aleatória (80%). |
| `damageStallChancePerSec` | number | `0.010` | Probabilidade base de paragem por segundo entre 80% e 95% de dano (1%/s). |
| `damageNoStartThreshold` | number | `0.95` | Nível de dano a partir do qual o motor **não consegue arrancar de todo** (95%). |

---

#### 🔗 Integrações com outros Mods

| Variável | Tipo | Padrão | Descrição |
| :--- | :---: | :---: | :--- |
| `integ_AEP_Enabled` | bool | `true` | Ativa a integração com o mod *Adjustable Engine Power* (AEP). |
| `integ_AEP_heatStage1` | number | `1.10` | Multiplicador de calor para o Stage 1 do AEP (chiptuning +10%). |
| `integ_AEP_heatStage2` | number | `1.15` | Multiplicador de calor para o Stage 2 do AEP (chiptuning +15%). |
| `integ_AEP_heatStage3` | number | `1.20` | Multiplicador de calor para o Stage 3 do AEP (chiptuning +20%). |

---

## 🌍 Suporte de Idiomas
O RET está totalmente traduzido nos seguintes idiomas:
🇬🇧 Inglês | 🇵🇹 Português | 🇩🇪 Alemão | 🇫🇷 Francês | 🇪🇸 Espanhol | 🇺🇦 Ucraniano

---

## 🤝 Integração Total
Totalmente compatível não apenas com o Farming Simulator nativo 25 mas também testado para interligação orgânica com outros Mods Famosos de Modding, como o módulo de **Adjustable Engine Power**. Onde aumentos de 10% a 20% do Chip Tuning irão multiplicar permanentemente o calor desferido dentro do bloco do motor, sendo necessário ventoinhas maiores!

Feito a pensar nos Roleplayers mais exigentes de agricultura. Desfruta!

