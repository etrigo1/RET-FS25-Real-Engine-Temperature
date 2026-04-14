[🇺🇸 Read in English](README.md) | 🇵🇹 Português

# 🚜 Realistic Engine Temperature (RET)

| | Versão | Estado |
|:---:|:---|:---:|
| 🟢 | **7.3.0** — Versão Estável | ![Stable](https://img.shields.io/badge/Estavel-7.3.0-brightgreen) |
| 🧪 | **8.0.0** — Beta Público | ![Beta](https://img.shields.io/badge/Beta-8.0.0-orange) |

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

### 2. Três Perfis Distintos de Motorização
O Farming Simulator não faz distinção dos motores, mas o RET faz! O mod deteta o consumo do teu trator (Diesel, Metano ou Elétrico) e aplica físicas completamente diferentes:
*   🟢 **Arrefecimento a Água (Padrão):** O clássico bloco com anticongelante e termostato. Mantém o motor nos 80ºC a 90ºC. Usa válvula de temperatura dinâmica.
*   💨 **Arrefecimento a Ar (Air-Cooled):** Ideal para clássicos (Ex: Porsches antigos). Sem Inércia térmica! A refrigeração depende puramente do rodar da ventoinha acoplada ao motor (RPMs). Se estiveres a fazer trabalho de TDF muito pesado com o trator estacionário, ele vai aquecer perigosamente rápido!
*   ⚡ **Veículos Elétricos (EV / Baterias):** Ignoram ferveduras de 100ºC. Funcionam num perfil apertado de proteção térmica (20ºC - 65ºC). Parados não geram calor, funcionam puramente pelo esforço extremo de descarga da corrente. Têm um BTMS com aquecimento próprio se estiverem ao frio e ventilação eletrificada.

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

## 🖥️ A Interface (HUD Dinâmico)
O Mod injeta texto suave e útil no canto do ecrã para monitorização a olho (apenas quando o motor está ligado):
- **RPM Max Seguras:** Mostra se já podes puxar pelo acelerador. Fica a Vermelho se o estiveres a prejudicar!
- **HP e Ajustamentos:** A cavalagem nativa reconhecida a debitar calor (com leituras ativas caso faças reprogramação (Chiptuning) na Oficina!).
- **Load / Carga Média:** A balança constante do teu esforço (% atual e a Média do último minuto de trabalho).
- **Válvula:** Observa a percentagem exata com que a água transita para os painéis refrigeradores.
- **Sujidade %:** Nível total de sujidade do radiador e a penalização de arrefecimento ativa.

Além disto, o RET apropria-se do sistema de Avisos Nativos (Banner intermitente do ecrã do Farming Simulator) alertando-o de quando forçar trabalho a frio ou no limite do Sobreaquecimento. Os avisos de sobreaquecimento de baterias (EV) são também traduzidos na tua língua de jogo.

---

## 🛠️ Comandos de Consola (Para Utilizadores Avançados)
O sistema tem memória por Trator e sincroniza tudo do lado do Servidor com Multijogador! Podes abrir a consola do jogo com a tecla `~` / `'` e utilizar os atalhos abaixo escrevendo `ret <comando>`:

| Comando | Ação |
| :--- | :--- |
| `ret help` | Mostra o painel de ajuda e todos os atalhos. |
| `ret on` / `ret off` | Liga ou desliga o mod totalmente no save game atual. |
| `ret water` | Força o trator atual em que te sentas a usar motor Arrefecido a Água (Padrão). |
| `ret air` | Força o trator atual a ignorar termostatos e a ser Arrefecido a Ar. |
| `ret electric` | Força o trator atual a usar curva térmica apertada de Lítio (Baterias EV). |
| `ret debug true` | Ativa o modo desenvolvedor cospindo na matemática crua das equações visuais de perda e absorção (+ e -) sob o menu. |
| `ret load` / `ret save` | Lê ou Força gravação dos dados no ficheiro XML de modo instantâneo. |

---

## ⚙️ Personalização Descomprometida e Guia do Config.xml

És criador de servidores de Hard-Roleplay ou um Mestre da Física? O Mod vai criar o ficheiro `modSettings/RealisticEngineTemp/Config.xml` nos teus documentos de jogo mal entres na primeira gravação. Dentro dele tu és literalmente dono das Leis da Física.

*(Sempre que a versão do mod for atualizada o sistema retém os teus números do XML e só introduz limpidamente as chaves das versões novas - Nunca mais perderás uma calibração tua)*.

### 📚 Dicionário das Principais Variáveis de Configuração:
*   **`Group00_Meta`**:
    *   `enableMultiplayerSync`: (true/false) Sincroniza as temperaturas com os restantes jogadores no servidor.
    *   `enableDataLogging`: (true/false) Exporta telemetria do motor em tempo real para um ficheiro Excel (`.csv`).
*   **`Group02_Debug_Master & Group04_HUD_Elements`**: Ativam a interface (HUD) e controlam que métricas são visíveis (Válvula, Dados Técnicos, Limites). O `uiRefreshRateBaseMs` dita a rapidez de atualização do texto.
*   **`Group05_General_Physics`**:
    *   `globalSpeed`: O multiplicador da velocidade das leis da física.
    *   `refAmbientTemp`: O clima ambiente de referência (ex: 20.0ºC) onde o aquecimento começa a agir.
    *   `warmupFastMultiplier`: Multiplicador durante arranques a frio (<60ºC) simulando injeção rica de combustível.
*   **`Group06_Thermostat_Settings` (Água / Ar / Elétricos)**:
    *   `timeToWarmupIdle` & `timeToOverheatLoad`: Cálculo automático da força gerada indicando o tempo (em minutos) exigidos de 20ºC até 85ºC.
    *   `ambientHeatingModifier` & `ambientCoolingModifier`: Influência passiva do clima exterior nas peças de metal do motor.
    *   `windCoolingMultiplier`: Ajuda aerodinâmica ao radiador ganhada pela deslocação do veículo (vento de arrasto).
*   **`Group07 ao 10` (Danos e Avarias)**:
    *   `enableColdRpmDamage` & `enableColdLoadDamage`: Punições e desgastes massivos por forçar os limites com óleo frio.
    *   `thermostatFailChance`: A probabilidade (0.0 até 1.0) do termostato falhar fisicamente se a barra de vida nativa cruzar o limite.
    *   `enableOverheatStall`: (true/false) Permite que o motor pare por sobreaquecimento crítico (acima de damageStart + overheatStallStartDelta).
    *   `enableDamageStall`: (true/false) Permite que o motor pare ou falhe o arranque por desgaste excessivo.
    *   `damageStallThreshold`: Nível de dano (0.0-1.0) a partir do qual começa o risco de paragem (padrão: 0.80 = 80%).
    *   `damageNoStartThreshold`: Nível de dano a partir do qual o motor recusa arrancar (padrão: 0.95 = 95%).
*   **`Group 11 & 12` (Escalonamento Dinâmico)**: Equilibra o calor com base nos Cavalos do motor (tratores enormes dissipam melhor).
*   **`Group 13` (Integrações Cruzadas)**: Lógica de compatibilidade com mods de Reprogramação como o *Adjustable Engine Power* (Chiptuning gera mais calor).

---

## 🌍 Suporte de Idiomas
O RET está totalmente traduzido nos seguintes idiomas:
🇬🇧 Inglês | 🇵🇹 Português | 🇩🇪 Alemão | 🇫🇷 Francês | 🇪🇸 Espanhol | 🇺🇦 Ucraniano

---

## 🤝 Integração Total
Totalmente compatível não apenas com o Farming Simulator nativo 25 mas também testado para interligação orgânica com outros Mods Famosos de Modding, como o módulo de **Adjustable Engine Power**. Onde aumentos de 10% a 20% do Chip Tuning irão multiplicar permanentemente o calor desferido dentro do bloco do motor, sendo necessário ventoinhas maiores!

Feito a pensar nos Roleplayers mais exigentes de agricultura. Desfruta!
