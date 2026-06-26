import { useState } from "react";

const FASES = [
  {
    id: 1, nome: "Fase 1 — Readaptação", periodo: "Jul · Ago 2026", semanas: "Semanas 1–8",
    cor: "#E65100", corBg: "#FFF3E0",
    descricao: "Reacostumar o corpo ao estresse do treino. Volume baixo, foco em técnica e ativação muscular.",
    objetivo: "−3 a 4 kg · Recuperar o condicionamento",
    regras: [
      "Cargas leves a moderadas — nunca até a falha",
      "Descanso de 90s entre séries",
      "Joelho: ZERO agachamento livre nas 4 primeiras semanas",
      "Prioridade absoluta: técnica > carga",
    ]
  },
  {
    id: 2, nome: "Fase 2 — Aceleração", periodo: "Set · Out 2026", semanas: "Semanas 9–16",
    cor: "#1565C0", corBg: "#E3F2FD",
    descricao: "Aumentar volume e intensidade progressivamente. Introduzir variações compostas.",
    objetivo: "−4 a 5 kg · Ganhar força base",
    regras: [
      "Progressão de carga a cada 2 semanas (+2,5kg nos compostos)",
      "Introduzir agachamento guiado (Smith) com observação do joelho",
      "Descanso 60–75s entre séries isoladas",
      "Cardio HIIT 2× por semana",
    ]
  },
  {
    id: 3, nome: "Fase 3 — Finalização", periodo: "Nov · Dez 2026", semanas: "Semanas 17–26",
    cor: "#1B5E20", corBg: "#E8F5E9",
    descricao: "Alta intensidade, déficit calórico mais agressivo, definição e manutenção da massa.",
    objetivo: "−4 a 5 kg · Chegar em 90kg",
    regras: [
      "Treino pesado 4× semana + cardio 3×",
      "Calorias reduzidas ~400 kcal abaixo do gasto",
      "Hidratação ≥3L por dia",
      "Dormir 22h–7h como regra inegociável",
    ]
  },
];

const TREINOS = {
  Segunda: {
    label: "Segunda", emoji: "🔵", tag: "LEVE", tagCor: "#1565C0",
    aviso: "Chegou de madrugada de Ourinhos. Treino de ativação — sem esforço máximo.",
    blocos: [
      {
        nome: "Aquecimento", duracao: "10 min", cor: "#78909C",
        exercicios: [
          { nome: "Esteira caminhada inclinada 3%", series: "1×10min", obs: "Ativa sem impacto no joelho" },
          { nome: "Mobilidade quadril (círculos)", series: "2×10 cada", obs: "" },
          { nome: "Elevação pélvica (ativação glúteo)", series: "2×15", obs: "Estabiliza o joelho indiretamente" },
        ]
      },
      {
        nome: "Peito + Tríceps", duracao: "35 min", cor: "#1565C0",
        exercicios: [
          { nome: "Supino reto halteres", series: "4×12", obs: "Fase 1: carga leve · Fase 2+: progressão" },
          { nome: "Supino inclinado halteres", series: "3×12", obs: "" },
          { nome: "Crucifixo polia baixa", series: "3×15", obs: "Contração no pico" },
          { nome: "Tríceps polia alta (corda)", series: "4×12", obs: "Cotovelo fixo" },
          { nome: "Tríceps testa haltere", series: "3×12", obs: "" },
        ]
      },
      {
        nome: "Core", duracao: "10 min", cor: "#546E7A",
        exercicios: [
          { nome: "Prancha frontal", series: "3×40s", obs: "" },
          { nome: "Abdominal bicicleta", series: "3×20", obs: "" },
          { nome: "Elevação de pernas deitado", series: "3×15", obs: "" },
        ]
      },
    ]
  },
  Terça: {
    label: "Terça", emoji: "⚽", tag: "MODERADO", tagCor: "#F57F17",
    aviso: "Futebol às 20h. Treino focado em superior — preserve as pernas para o campo.",
    blocos: [
      {
        nome: "Aquecimento", duracao: "8 min", cor: "#78909C",
        exercicios: [
          { nome: "Remada máquina leve", series: "2×15", obs: "Aquecimento de escápula" },
          { nome: "Rotação ombro com elástico", series: "2×15", obs: "Previne lesão" },
        ]
      },
      {
        nome: "Costas + Bíceps", duracao: "40 min", cor: "#F57F17",
        exercicios: [
          { nome: "Puxada frontal aberta", series: "4×10", obs: "Fase 1: assistida se necessário" },
          { nome: "Remada curvada barra", series: "4×10", obs: "Costas retas, quadril neutro" },
          { nome: "Remada unilateral haltere", series: "3×12 cada", obs: "Apoio no banco" },
          { nome: "Pull-down polia reto", series: "3×12", obs: "Amplitude total" },
          { nome: "Rosca direta barra W", series: "4×12", obs: "Sem balanço do tronco" },
          { nome: "Rosca martelo haltere", series: "3×12", obs: "" },
        ]
      },
      {
        nome: "Cardio pré-futebol", duracao: "10 min", cor: "#43A047",
        exercicios: [
          { nome: "Esteira 8 km/h ou caminhada rápida", series: "1×10min", obs: "Aquece para o futebol" },
        ]
      },
    ]
  },
  Quarta: {
    label: "Quarta", emoji: "🔴", tag: "PESADO", tagCor: "#B71C1C",
    aviso: "Melhor dia para treinar pesado. Inglês às 20h — saia do treino até 19h45.",
    blocos: [
      {
        nome: "Aquecimento Joelho", duracao: "12 min", cor: "#78909C",
        exercicios: [
          { nome: "Bicicleta ergométrica leve", series: "1×8min", obs: "Lubrifica a articulação sem impacto" },
          { nome: "Cadeira extensora leve (30%)", series: "2×20", obs: "Ativa o quadríceps" },
          { nome: "Mesa flexora leve", series: "2×15", obs: "Ativa posterior de coxa" },
        ]
      },
      {
        nome: "Inferior — Protocolo Joelho", duracao: "40 min", cor: "#B71C1C",
        exercicios: [
          { nome: "Leg press 45°", series: "5×10", obs: "⚠️ Pé alto, desça só até 90° — não além" },
          { nome: "Cadeira extensora", series: "4×12", obs: "Fase 1: 50–60% da carga máx" },
          { nome: "Mesa flexora", series: "4×12", obs: "" },
          { nome: "Abdução de quadril máquina", series: "3×15", obs: "Fortalece glúteo médio → estabiliza joelho" },
          { nome: "Stiff com halteres", series: "3×12", obs: "Posterior e glúteo · costas retas" },
          { nome: "Panturrilha em pé", series: "4×20", obs: "" },
        ]
      },
      {
        nome: "HIIT (Fase 2 em diante)", duracao: "15 min", cor: "#E65100",
        exercicios: [
          { nome: "Bicicleta: 30s intenso / 30s leve", series: "10 ciclos", obs: "Fase 1: substituir por 15min esteira" },
        ]
      },
    ]
  },
  Quinta: {
    label: "Quinta", emoji: "🔴", tag: "PESADO", tagCor: "#B71C1C",
    aviso: "Dia livre à noite. Treino mais completo — dorme cedo após (22h).",
    blocos: [
      {
        nome: "Aquecimento", duracao: "8 min", cor: "#78909C",
        exercicios: [
          { nome: "Elíptico leve", series: "1×8min", obs: "Baixo impacto, aquece o corpo todo" },
        ]
      },
      {
        nome: "Ombro + Trapézio", duracao: "35 min", cor: "#6A1B9A",
        exercicios: [
          { nome: "Desenvolvimento com halteres", series: "4×10", obs: "Amplitude controlada" },
          { nome: "Elevação lateral", series: "4×15", obs: "Carga leve, contração no pico" },
          { nome: "Elevação frontal alternada", series: "3×12", obs: "" },
          { nome: "Encolhimento com halteres", series: "4×12", obs: "Segura 1s no topo" },
          { nome: "Face pull polia", series: "3×15", obs: "Saúde do manguito rotador" },
        ]
      },
      {
        nome: "Core Avançado", duracao: "12 min", cor: "#546E7A",
        exercicios: [
          { nome: "Prancha lateral", series: "3×30s cada lado", obs: "" },
          { nome: "Dead bug", series: "3×10 cada lado", obs: "Controla lombar" },
          { nome: "Ab wheel (roda)", series: "3×8–12", obs: "Fase 1: ajoelhado" },
        ]
      },
    ]
  },
  Sexta: {
    label: "Sexta", emoji: "🟡", tag: "LEVE", tagCor: "#F9A825",
    aviso: "Saída às 17h para Ourinhos. Treino opcional e curto antes das 16h30.",
    blocos: [
      {
        nome: "Full body expresso (opcional)", duracao: "25 min", cor: "#F9A825",
        exercicios: [
          { nome: "Supino halteres", series: "3×12", obs: "Carga moderada" },
          { nome: "Puxada polia", series: "3×12", obs: "" },
          { nome: "Desenvolvimento halteres", series: "3×12", obs: "" },
          { nome: "Leg press leve", series: "3×15", obs: "50% da carga de quarta" },
        ]
      },
    ]
  },
  Sábado: {
    label: "Sábado", emoji: "🟢", tag: "ATIVO", tagCor: "#2E7D32",
    aviso: "Ourinhos — qualidade com a namorada. Atividade ao ar livre vale muito.",
    blocos: [
      {
        nome: "Lazer ativo", duracao: "30–60 min", cor: "#2E7D32",
        exercicios: [
          { nome: "Caminhada ao ar livre", series: "30–60 min", obs: "Ritmo confortável" },
          { nome: "Passeio de bike (se disponível)", series: "—", obs: "" },
          { nome: "Natação", series: "—", obs: "Excelente para o joelho — sem impacto" },
        ]
      },
    ]
  },
  Dom: {
    label: "Dom", emoji: "⚪", tag: "DESCANSO", tagCor: "#90A4AE",
    aviso: "Meal prep + descanso total. Músculo cresce no repouso, não na academia.",
    blocos: [
      {
        nome: "Recuperação ativa", duracao: "20 min", cor: "#90A4AE",
        exercicios: [
          { nome: "Alongamento global", series: "15 min", obs: "Foco em posterior de coxa e panturrilha" },
          { nome: "Foam roller perna", series: "5 min", obs: "Libera tensão muscular acumulada" },
        ]
      },
    ]
  },
};

const NUTRICAO_REFEICOES = [
  { hora: "07:00", nome: "Café da Manhã", emoji: "🌅", kcal: "~480 kcal",
    itens: ["3 ovos mexidos no azeite", "2 fatias pão integral", "1 banana média", "Café preto sem açúcar"],
    macro: "P: 28g · C: 55g · G: 16g", dica: "Nunca pule. Evita comer besteira às 10h." },
  { hora: "10:00", nome: "Lanche Manhã", emoji: "🍎", kcal: "~200 kcal",
    itens: ["Iogurte grego natural 170g", "30g granola sem açúcar", "1 col pasta amendoim"],
    macro: "P: 17g · C: 22g · G: 8g", dica: "Deixa na geladeira do trabalho." },
  { hora: "12:30", nome: "Almoço (Marmita)", emoji: "🍱", kcal: "~650 kcal",
    itens: ["160g frango grelhado ou carne magra", "5 col arroz integral", "2 col feijão ou lentilha", "Vegetais refogados à vontade", "Salada crua sem limite"],
    macro: "P: 45g · C: 70g · G: 12g", dica: "Monte 4 marmitas no domingo. É o alicerce do plano." },
  { hora: "15:30", nome: "Pré-treino", emoji: "⚡", kcal: "~250 kcal",
    itens: ["1 banana", "30g whey protein ou 3 claras", "Água 500ml"],
    macro: "P: 25g · C: 28g · G: 2g", dica: "Coma 40–60 min antes. Energia sem peso no estômago." },
  { hora: "19:30", nome: "Jantar Pós-treino", emoji: "🍽️", kcal: "~580 kcal",
    itens: ["160g frango, tilápia ou 4 ovos", "3 col batata-doce ou arroz integral", "Legumes no vapor", "Fio de azeite"],
    macro: "P: 42g · C: 45g · G: 14g", dica: "Priorize proteína. Reduza carb na Fase 3." },
  { hora: "22:00", nome: "Ceia (opcional)", emoji: "🌙", kcal: "~150 kcal",
    itens: ["200g iogurte grego natural", "OU 2 ovos cozidos"],
    macro: "P: 20g · C: 6g · G: 5g", dica: "Só se sentir fome real." },
];

const SUPLEMENTOS = [
  { nome: "Whey Protein", prioridade: "Alta", quando: "Pós-treino ou café da manhã", dose: "1 scoop (~25g proteína)", motivo: "Fecha a meta proteica sem aumentar muito a caloria", essencial: true },
  { nome: "Creatina", prioridade: "Alta", quando: "Todo dia (mesmo sem treino)", dose: "5g em água ou suco", motivo: "Aumenta força, recuperação e preserva massa no déficit", essencial: true },
  { nome: "Vitamina D3 + K2", prioridade: "Alta", quando: "Com refeição gordurosa", dose: "2.000–4.000 UI (confirme no exame)", motivo: "Impacta diretamente a disposição e imunidade", essencial: true },
  { nome: "Ômega 3", prioridade: "Média", quando: "Com almoço ou jantar", dose: "2–3g de EPA+DHA", motivo: "Anti-inflamatório natural — importante para o joelho", essencial: false },
  { nome: "Magnésio Bisglicinato", prioridade: "Média", quando: "30 min antes de dormir", dose: "300–400mg", motivo: "Melhora qualidade do sono e recuperação muscular", essencial: false },
];

const JOELHO = [
  { titulo: "✅ Sempre permitido", cor: "#1B5E20", items: ["Bicicleta ergométrica no aquecimento", "Leg press com pé alto (até 90°)", "Cadeira extensora com progressão controlada", "Abdução de quadril (fortalece glúteo médio)", "Stiff e mesa flexora"] },
  { titulo: "🚫 Fase 1 — PROIBIDO", cor: "#B71C1C", items: ["Agachamento livre com carga", "Avanço (lunge) com carga", "Step-up com carga", "Corrida e impacto direto"] },
  { titulo: "⚠️ Fase 2 — Introduzir com cuidado", cor: "#E65100", items: ["Smith machine (agachamento guiado)", "Agachamento sumo (alivia o joelho)", "Lunge estático leve"] },
  { titulo: "🛑 Pare imediatamente se...", cor: "#880E4F", items: ["Dor durante o exercício (não só desconforto)", "Inchaço após o treino", "Crepitação com dor ao dobrar", "→ Consulte ortopedista se qualquer um aparecer"] },
];

const META_MESES = [
  { mes: "Jun", meta: 112, label: "Início" },
  { mes: "Jul", meta: 110, label: "−2" },
  { mes: "Ago", meta: 108, label: "−4" },
  { mes: "Set", meta: 106, label: "−6" },
  { mes: "Out", meta: 104, label: "−8" },
  { mes: "Nov", meta: 101, label: "−11" },
  { mes: "Dez", meta: 90, label: "🏆 90" },
];

function Badge({ text, cor }) {
  return (
    <span style={{ background: cor, color: "white", fontSize: 9, fontWeight: 800, padding: "3px 8px", borderRadius: 10, letterSpacing: "0.6px" }}>
      {text}
    </span>
  );
}

export default function App() {
  const [aba, setAba] = useState("visao");
  const [diaAtivo, setDiaAtivo] = useState("Segunda");
  const [faseAtiva, setFaseAtiva] = useState(1);
  const [pesoAtual, setPesoAtual] = useState(112);

  const dias = Object.keys(TREINOS);
  const treino = TREINOS[diaAtivo];
  const fase = FASES[faseAtiva - 1];
  const progresso = Math.min(100, Math.max(0, Math.round(((112 - pesoAtual) / 22) * 100)));

  const tabs = [
    { id: "visao", label: "📊 Geral" },
    { id: "treino", label: "🏋️ Treino" },
    { id: "nutricao", label: "🍽️ Nutrição" },
    { id: "joelho", label: "🦵 Joelho" },
    { id: "suplementos", label: "💊 Suplementos" },
  ];

  return (
    <div style={{ fontFamily: "'Inter','Segoe UI',system-ui,sans-serif", background: "#F0F4F8", minHeight: "100vh", paddingBottom: 80 }}>

      {/* HEADER */}
      <div style={{ background: "linear-gradient(160deg,#0D1B2A 0%,#1B3A5C 60%,#1B5E20 100%)", padding: "env(safe-area-inset-top,20px) 18px 0", color: "white" }}>
        <div style={{ paddingTop: 16 }}>
          <div style={{ fontSize: 10, fontWeight: 700, letterSpacing: "2px", opacity: 0.55, marginBottom: 4 }}>PLANO DE TRANSFORMAÇÃO</div>
          <div style={{ fontSize: 22, fontWeight: 800 }}>Felipe Bonini</div>
          <div style={{ fontSize: 12, opacity: 0.7, marginTop: 2 }}>112 kg → <strong style={{ color: "#69F0AE" }}>90 kg</strong> · Jun–Dez 2026</div>

          {/* Progresso */}
          <div style={{ marginTop: 14 }}>
            <div style={{ display: "flex", justifyContent: "space-between", fontSize: 10, opacity: 0.65, marginBottom: 5 }}>
              <span>Progresso</span><span>{progresso}% da meta</span>
            </div>
            <div style={{ background: "rgba(255,255,255,0.15)", borderRadius: 8, height: 9, overflow: "hidden" }}>
              <div style={{ background: "linear-gradient(90deg,#69F0AE,#00C853)", width: `${Math.max(progresso, 2)}%`, height: "100%", borderRadius: 8, transition: "width 0.4s" }} />
            </div>
            <div style={{ display: "flex", alignItems: "center", gap: 8, marginTop: 10 }}>
              <span style={{ fontSize: 11, opacity: 0.65 }}>Peso atual:</span>
              <input type="number" value={pesoAtual} onChange={e => setPesoAtual(Number(e.target.value))}
                style={{ width: 65, padding: "4px 8px", borderRadius: 8, border: "none", background: "rgba(255,255,255,0.15)", color: "white", fontSize: 14, fontWeight: 700, textAlign: "center", outline: "none" }} />
              <span style={{ fontSize: 11, opacity: 0.65 }}>kg</span>
            </div>
          </div>

          {/* Tabs */}
          <div style={{ display: "flex", gap: 4, marginTop: 16, overflowX: "auto", paddingBottom: 0 }}>
            {tabs.map(t => (
              <button key={t.id} onClick={() => setAba(t.id)}
                style={{ padding: "8px 12px", borderRadius: "10px 10px 0 0", border: "none", cursor: "pointer", fontSize: 11, fontWeight: 700, whiteSpace: "nowrap", flexShrink: 0,
                  background: aba === t.id ? "#F0F4F8" : "rgba(255,255,255,0.12)",
                  color: aba === t.id ? "#0D1B2A" : "rgba(255,255,255,0.8)",
                  transition: "all 0.15s" }}>
                {t.label}
              </button>
            ))}
          </div>
        </div>
      </div>

      {/* CONTEÚDO */}
      <div style={{ padding: "16px", maxWidth: 600, margin: "0 auto" }}>

        {/* ── VISÃO GERAL ── */}
        {aba === "visao" && (
          <div style={{ display: "flex", flexDirection: "column", gap: 12 }}>
            {/* Seletor Fase */}
            <div style={{ display: "flex", gap: 6 }}>
              {FASES.map(f => (
                <button key={f.id} onClick={() => setFaseAtiva(f.id)}
                  style={{ flex: 1, padding: "10px 4px", borderRadius: 12, border: `2px solid ${faseAtiva === f.id ? f.cor : "#DDD"}`,
                    background: faseAtiva === f.id ? f.cor : "white", color: faseAtiva === f.id ? "white" : "#666",
                    cursor: "pointer", fontWeight: 700, fontSize: 11, lineHeight: 1.4, transition: "all 0.18s" }}>
                  Fase {f.id}<br /><span style={{ fontWeight: 400, fontSize: 10 }}>{f.periodo}</span>
                </button>
              ))}
            </div>

            <div style={{ background: "white", borderRadius: 14, overflow: "hidden", boxShadow: "0 2px 12px rgba(0,0,0,0.07)" }}>
              <div style={{ background: fase.cor, padding: "14px 18px", color: "white" }}>
                <div style={{ fontWeight: 800, fontSize: 15 }}>{fase.nome}</div>
                <div style={{ fontSize: 11, opacity: 0.9, marginTop: 2 }}>{fase.semanas} · {fase.periodo}</div>
              </div>
              <div style={{ padding: "14px 18px" }}>
                <div style={{ background: fase.corBg, borderRadius: 10, padding: "10px 14px", marginBottom: 12, fontSize: 13 }}>
                  🎯 <strong>Meta:</strong> {fase.objetivo}
                </div>
                <p style={{ fontSize: 13, color: "#555", marginBottom: 12, lineHeight: 1.6 }}>{fase.descricao}</p>
                {fase.regras.map((r, i) => (
                  <div key={i} style={{ display: "flex", gap: 8, marginBottom: 7, fontSize: 13, color: "#444" }}>
                    <span style={{ color: fase.cor, fontWeight: 800 }}>→</span>{r}
                  </div>
                ))}
              </div>
            </div>

            {/* Progressão */}
            <div style={{ background: "white", borderRadius: 14, padding: "16px 18px", boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
              <div style={{ fontWeight: 800, fontSize: 15, marginBottom: 14, color: "#0D1B2A" }}>📈 Progressão Esperada</div>
              {META_MESES.map((m, i) => {
                const pct = ((112 - m.meta) / 22) * 100;
                const isMeta = m.mes === "Dez";
                return (
                  <div key={i} style={{ display: "flex", alignItems: "center", gap: 8, marginBottom: 7 }}>
                    <div style={{ width: 28, fontSize: 11, color: "#888", flexShrink: 0 }}>{m.mes}</div>
                    <div style={{ flex: 1, background: "#F0F4F8", borderRadius: 6, height: 24, overflow: "hidden", position: "relative" }}>
                      <div style={{ width: `${pct}%`, height: "100%", background: isMeta ? "linear-gradient(90deg,#1B5E20,#43A047)" : "linear-gradient(90deg,#1565C0,#42A5F5)", borderRadius: 6 }} />
                    </div>
                    <div style={{ width: 52, fontSize: 12, fontWeight: 700, color: isMeta ? "#1B5E20" : "#1565C0", textAlign: "right" }}>{m.meta} kg</div>
                    <div style={{ width: 32, fontSize: 10, color: "#999" }}>{m.label}</div>
                  </div>
                );
              })}
            </div>

            {/* Semana tipo */}
            <div style={{ background: "white", borderRadius: 14, padding: "16px 18px", boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
              <div style={{ fontWeight: 800, fontSize: 15, marginBottom: 12, color: "#0D1B2A" }}>🗓️ Semana Tipo</div>
              {dias.map((d, i) => {
                const t = TREINOS[d];
                return (
                  <div key={d} style={{ display: "flex", alignItems: "center", gap: 8, padding: "7px 0", borderBottom: i < dias.length - 1 ? "1px solid #F0F4F8" : "none" }}>
                    <div style={{ width: 60, fontSize: 12, fontWeight: 700, color: "#333" }}>{t.emoji} {d}</div>
                    <Badge text={t.tag} cor={t.tagCor} />
                    <div style={{ fontSize: 11, color: "#666", flex: 1, overflow: "hidden", textOverflow: "ellipsis", whiteSpace: "nowrap" }}>
                      {t.blocos.filter(b => !b.nome.includes("Aquecimento") && !b.nome.includes("Recuperação")).map(b => b.nome).join(" + ")}
                    </div>
                  </div>
                );
              })}
            </div>
          </div>
        )}

        {/* ── TREINO ── */}
        {aba === "treino" && (
          <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
            <div style={{ display: "flex", gap: 5, flexWrap: "wrap" }}>
              {dias.map(d => (
                <button key={d} onClick={() => setDiaAtivo(d)}
                  style={{ padding: "6px 10px", borderRadius: 8, border: `2px solid ${diaAtivo === d ? TREINOS[d].tagCor : "#DDD"}`,
                    background: diaAtivo === d ? TREINOS[d].tagCor : "white", color: diaAtivo === d ? "white" : "#555",
                    cursor: "pointer", fontWeight: 700, fontSize: 11, transition: "all 0.15s" }}>
                  {TREINOS[d].emoji} {d}
                </button>
              ))}
            </div>

            <div style={{ background: "#FFF8E1", border: "1px solid #FFD54F", borderRadius: 10, padding: "10px 14px", fontSize: 12, color: "#5D4037" }}>
              ⚠️ {treino.aviso}
            </div>

            {treino.blocos.map((bloco, bi) => (
              <div key={bi} style={{ background: "white", borderRadius: 14, overflow: "hidden", boxShadow: "0 2px 10px rgba(0,0,0,0.07)" }}>
                <div style={{ background: bloco.cor, padding: "10px 14px", display: "flex", justifyContent: "space-between", alignItems: "center" }}>
                  <div style={{ color: "white", fontWeight: 700, fontSize: 13 }}>{bloco.nome}</div>
                  <div style={{ background: "rgba(255,255,255,0.2)", color: "white", borderRadius: 6, padding: "2px 8px", fontSize: 11 }}>{bloco.duracao}</div>
                </div>
                <div style={{ padding: "10px 12px", display: "flex", flexDirection: "column", gap: 6 }}>
                  {bloco.exercicios.map((ex, ei) => (
                    <div key={ei} style={{ background: "#F8FAFC", borderRadius: 10, padding: "9px 12px", display: "flex", gap: 8, alignItems: "flex-start" }}>
                      <div style={{ width: 20, height: 20, borderRadius: "50%", background: bloco.cor, color: "white", display: "flex", alignItems: "center", justifyContent: "center", fontSize: 9, fontWeight: 800, flexShrink: 0 }}>{ei + 1}</div>
                      <div style={{ flex: 1 }}>
                        <div style={{ fontSize: 12, fontWeight: 600, color: "#1A1A2E" }}>{ex.nome}</div>
                        {ex.obs && <div style={{ fontSize: 10, color: "#888", marginTop: 2 }}>💡 {ex.obs}</div>}
                      </div>
                      <div style={{ background: bloco.cor + "22", color: bloco.cor, borderRadius: 6, padding: "2px 7px", fontSize: 10, fontWeight: 700, flexShrink: 0 }}>{ex.series}</div>
                    </div>
                  ))}
                </div>
              </div>
            ))}
          </div>
        )}

        {/* ── NUTRIÇÃO ── */}
        {aba === "nutricao" && (
          <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
            <div style={{ background: "white", borderRadius: 14, padding: "14px 16px", boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
              <div style={{ fontWeight: 800, fontSize: 14, marginBottom: 10, color: "#0D1B2A" }}>🔥 Calorias por Fase</div>
              {[
                { label: "Sem controle (atual)", kcal: 2800, cor: "#EF5350" },
                { label: "Fase 1 · Jul–Ago", kcal: 2400, cor: "#E65100" },
                { label: "Fase 2 · Set–Out", kcal: 2250, cor: "#1565C0" },
                { label: "Fase 3 · Nov–Dez", kcal: 2100, cor: "#1B5E20" },
              ].map((item, i) => (
                <div key={i} style={{ marginBottom: 8 }}>
                  <div style={{ display: "flex", justifyContent: "space-between", fontSize: 11, marginBottom: 3 }}>
                    <span style={{ color: "#555" }}>{item.label}</span>
                    <strong style={{ color: item.cor }}>{item.kcal} kcal</strong>
                  </div>
                  <div style={{ background: "#F0F4F8", borderRadius: 5, height: 7 }}>
                    <div style={{ width: `${(item.kcal / 2800) * 100}%`, height: "100%", background: item.cor, borderRadius: 5 }} />
                  </div>
                </div>
              ))}
            </div>

            {NUTRICAO_REFEICOES.map((ref, i) => (
              <div key={i} style={{ background: "white", borderRadius: 14, overflow: "hidden", boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
                <div style={{ background: i % 2 === 0 ? "#0D1B2A" : "#1B5E20", padding: "10px 14px", display: "flex", justifyContent: "space-between", alignItems: "center" }}>
                  <div style={{ color: "white", fontWeight: 700, fontSize: 13 }}>{ref.emoji} {ref.nome}</div>
                  <div style={{ display: "flex", gap: 6, alignItems: "center" }}>
                    <span style={{ color: "#69F0AE", fontSize: 11, fontWeight: 700 }}>{ref.kcal}</span>
                    <span style={{ background: "rgba(255,255,255,0.2)", color: "white", borderRadius: 5, padding: "2px 7px", fontSize: 10 }}>{ref.hora}</span>
                  </div>
                </div>
                <div style={{ padding: "10px 14px" }}>
                  {ref.itens.map((item, j) => (
                    <div key={j} style={{ display: "flex", gap: 7, fontSize: 12, color: "#333", marginBottom: 4 }}>
                      <span style={{ color: "#43A047", fontWeight: 700 }}>✓</span>{item}
                    </div>
                  ))}
                  <div style={{ marginTop: 8, display: "flex", justifyContent: "space-between", flexWrap: "wrap", gap: 6 }}>
                    <div style={{ background: "#E8F5E9", borderRadius: 6, padding: "3px 9px", fontSize: 10, color: "#2E7D32", fontWeight: 600 }}>{ref.macro}</div>
                    <div style={{ fontSize: 10, color: "#888", fontStyle: "italic" }}>💡 {ref.dica}</div>
                  </div>
                </div>
              </div>
            ))}
          </div>
        )}

        {/* ── JOELHO ── */}
        {aba === "joelho" && (
          <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
            <div style={{ background: "#B71C1C", borderRadius: 14, padding: "14px 16px", color: "white" }}>
              <div style={{ fontWeight: 800, fontSize: 15, marginBottom: 6 }}>🦵 Protocolo Joelho</div>
              <div style={{ fontSize: 12, opacity: 0.9, lineHeight: 1.6 }}>
                Dor no joelho com sobrepeso é comum — geralmente condromalacia ou tendinite patelar. Este protocolo protege a articulação enquanto você emagrece e fortalece os músculos ao redor.
              </div>
            </div>
            {JOELHO.map((p, i) => (
              <div key={i} style={{ background: "white", borderRadius: 14, overflow: "hidden", boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
                <div style={{ background: p.cor, padding: "10px 14px", color: "white", fontWeight: 700, fontSize: 13 }}>{p.titulo}</div>
                <div style={{ padding: "10px 14px", display: "flex", flexDirection: "column", gap: 6 }}>
                  {p.items.map((item, j) => (
                    <div key={j} style={{ background: "#F8FAFC", borderRadius: 8, padding: "8px 12px", fontSize: 12, color: "#333", display: "flex", gap: 7 }}>
                      <span style={{ color: p.cor, fontWeight: 700, flexShrink: 0 }}>•</span>{item}
                    </div>
                  ))}
                </div>
              </div>
            ))}
            <div style={{ background: "#E3F2FD", borderRadius: 12, padding: "12px 14px", fontSize: 12, color: "#1565C0" }}>
              💊 <strong>Apoio extra:</strong> Ômega 3 (3g/dia) · Colágeno Tipo 2 (40mg) · Gelo pós-treino 15min · Joelheira de compressão no treino
            </div>
          </div>
        )}

        {/* ── SUPLEMENTOS ── */}
        {aba === "suplementos" && (
          <div style={{ display: "flex", flexDirection: "column", gap: 10 }}>
            <div style={{ background: "#1B3A5C", borderRadius: 14, padding: "14px 16px", color: "white" }}>
              <div style={{ fontWeight: 800, fontSize: 15, marginBottom: 4 }}>💊 Stack de Suplementos</div>
              <div style={{ fontSize: 12, opacity: 0.8 }}>Comece pelos essenciais — o resto é otimização.</div>
            </div>
            {SUPLEMENTOS.map((s, i) => (
              <div key={i} style={{ background: "white", borderRadius: 14, padding: "14px 16px", boxShadow: "0 2px 8px rgba(0,0,0,0.06)" }}>
                <div style={{ display: "flex", justifyContent: "space-between", alignItems: "flex-start", marginBottom: 8 }}>
                  <div style={{ fontWeight: 800, fontSize: 14, color: "#0D1B2A" }}>{s.nome}</div>
                  <div style={{ display: "flex", gap: 5 }}>
                    {s.essencial && <Badge text="ESSENCIAL" cor="#1B5E20" />}
                    <Badge text={s.prioridade.toUpperCase()} cor={s.prioridade === "Alta" ? "#E65100" : "#1565C0"} />
                  </div>
                </div>
                <div style={{ fontSize: 12, color: "#555", marginBottom: 4 }}>⏰ {s.quando}</div>
                <div style={{ fontSize: 12, color: "#555", marginBottom: 8 }}>📏 {s.dose}</div>
                <div style={{ background: "#F0F4F8", borderRadius: 8, padding: "8px 10px", fontSize: 11, color: "#444" }}>💡 {s.motivo}</div>
              </div>
            ))}
            <div style={{ background: "#E8F5E9", borderRadius: 12, padding: "12px 14px", fontSize: 12, color: "#2E7D32" }}>
              💰 <strong>Custo estimado essenciais:</strong> Whey ~R$90 + Creatina ~R$40 + Vit. D ~R$25 = <strong>~R$155/mês</strong>
            </div>
          </div>
        )}
      </div>
    </div>
  );
}
