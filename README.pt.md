[🇺🇸 Read in English](README.md) | 🇵🇹 Português

# 🚜 Realistic Engine Temperature (RET)
**Versão Atual:** 7.0.x  |  **Farming Simulator 25**

O **Realistic Engine Temperature (RET)** é um mod de física avançada concebido para o Farming Simulator 25. Ele desativa a temperatura mecânica nativa e utópica do jogo base, substituíndo-a por um modelo termodinâmico hiper-realista.

Quer tenhas um velho trator a gasóleo, uma ceifeira antiga arrefecida a ar ou um modelo elétrico topo de gama, o RET simulará exatamente como o calor é gerado, dissipado e as potenciais avarias no meio do processo!

---

## 🌟 Principais Funcionalidades

### 1. Sistema Termodinâmico Ativo
O calor não sobe de forma linear. Ele é calculado a cada milissegundo baseado em:
- **Carga do Motor (Load):** Puxar um arado pesado numa subida a 100% de Esforço vai gerar um calor extremo que leva a mecânica ao seu limite.
- **RPMs / Ralenti:** Motores deixados ao ralenti geram apenas calor base. Levá-los ao Redline em ponto morto gera fricção e calor.
- **Clima e Vento:** Trabalhar num dia chuvoso e frio diminui o calor. Conduzir a 50 km/h gera um fluxo de arrasto natural (Wind Cooling) que ajuda a arrefecer independentemente da ventoinha.

### 2. Três Perfis Distintos de Motorização (NOVO na V7!)
O Farming Simulator não faz distinção dos motores, mas o RET faz! O mod deteta o consumo do teu trator (Diesel, Metano ou Elétrico) e aplica físicas completamente diferentes:
*   🟢 **Arrefecimento a Água (Padrão):** O clássico bloco com anticongelante e termostato. Mantém o motor nos 80ºC a 90ºC. Usa válvula de temperatura dinâmica.
*   💨 **Arrefecimento a Ar (Air-Cooled):** Ideal para clássicos (Ex: Porsches antigos). Sem Inércia térmica! A refrigeração depende puramente do rodar da ventoinha acoplada ao motor (RPMs). Se estiveres a fazer trabalho de TDF muito pesado com o trator estacionário, ele vai aquecer perigosamente rápido!
*   ⚡ **Veículos Elétricos (EV / Baterias):** Ignoram ferveduras de 100ºC. Funcionam num perfil apertado de proteção térmica (20ºC - 65ºC). Parados não geram calor, funcionam puramente pelo esforço extremo de descarga da corrente. Têm um BTMS com aquecimento próprio se estiverem ao frio e ventilação eletrificada.

### 3. Válvulas e Termostatos Inteligentes
No trator padrão (Água), a física é controlada por um **Termostato**. Durante os primeiros minutos da manhã ele está fechado (0%) a reter calor na cabine usando injeção rica de combustível (fast warmup). Ao pisar os 85ºC a válvula abre dinamicamente em percentagem para invocar as ventoinhas do Radiador Central e travar a subida!

### 4. Dano Mecânico e Falhas Estocásticas (Avarias de Sobreaquecimento)
O seu trator já está bastante desgastado no ecrã de reparação? Prepare-se para a lotaria mecânica!
A **Válvula do Termostato pode avariar em movimento** perante um trator envelhecido:
*   **Encravar Aberta:** O trator não consegue manter temperatura e trabalha cronicamente a frio (danificando os cilindros em esforço).
*   **Encravar Fechada:** O fluxo para o radiador é cortado. A água ferve, o alarme da cabine soa e o motor sofrerá dano imediato até encostar!

*(A gravidade e a fecho das válvulas flutua percentualmente com cada percentagem de estrago do veículo).*

### 5. Dano por Esforço a Frio
Não pegues no trator às 6h da manhã e comeces a lavrar a direito!
O mod pune severamente a mecânica de tratores (e a carteira da reparação) que sejam levados ao limite de RPMs ou a altos níveis de Carga quando o medidor da temperatura ainda está em níveis frios! Aqueça o seu trator primeiro!

### 6. Penalização por Sujidade (Lodo no Radiador)
Trabalhar na lama o dia todo cobre os favos do maquinário. À medida que o medidor de Sujidade aumenta no FS25, a força máxima de refrigeração do seu radiador cai a pique, tornando os trabalhos de verão impossíveis sem parar ao sol.

---

## 🖥️ A Interface (HUD Dinâmico)
O Mod injeta texto suave e útil no canto do ecrã para monitorização a olho (apenas quando o motor está ligado):
- **RPM Max Seguras:** Mostra se já podes puxar pelo acelerador. Fica a Vermelho se o estiveres a prejudicar!
- **HP e Ajustamentos:** A cavalagem nativa reconhecida a debitar calor (com leituras ativas caso faças reprogramação (Chiptuning) na Oficina!).
- **Load / Carga Média:** A balança constante do teu esforço (% atual e a Média do último minuto de trabalho).
- **Válvula:** Observa a percentagem exata com que a água transita para os paineis refrigeradores.

Além disto, o RET apropria-se do sistema de Avisos Nativos (Banner intermitente do ecrã do Farming Simulator) alertando-o de quando forçar trabalho a frio ou no limite do Sobreaquecimento.

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

## ⚙️ Personalização Descomprometida
És criador de servidores de Hard-Roleplay ou um Mestre da Física? O Mod vai criar a pasta física `modSettings/RealisticEngineTemp/` nos teus documentos de jogo mal entres na primeira gravação.
Dentro do ficheiro **`Config.xml`** és literalmente dono das Leis da Física. Podes:
- Alterar as taxas de aquecimento passivas em Graus por Milissegundo.
- Mudar a que Grau a válvula entra em alerta e abre (ex: de 85ºC para 95ºC).
- Mudar o Quociente de aquecimento de todas as baterias elétricas no mapa!
*(Sempre que a versão do mod for atualizada o sistema retém os teus números do XML e só introduz limpidamente as chaves das versões novas - Nunca mais perderás uma calibração tua)*.

## 🤝 Integração Total
Totalmente compatível não apenas com o Farming Simulator nativo 25 mas também testado para interligação orgânica com outros Mods Famosos de Modding, como o módulo de **Adjustable Engine Power**. Onde aumentos de 10% a 20% do Chip Tuning irão multiplicar permanentemente o calor desferido dentro do bloco do motor, sendo necessário ventoinhas maiores!

Feito a pensar nos Roleplayers mais exigentes de agricultura. Desfruta!
