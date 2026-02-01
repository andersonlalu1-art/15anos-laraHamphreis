<!DOCTYPE html>
<html lang="pt-br">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>15 Anos Lara Hamphreis | Lista de Presentes</title>
    
    <!-- Bibliotecas React e Tailwind -->
    <script src="https://unpkg.com/react@18/umd/react.production.min.js" crossorigin></script>
    <script src="https://unpkg.com/react-dom@18/umd/react-dom.production.min.js" crossorigin></script>
    <script src="https://unpkg.com/@babel/standalone/babel.min.js"></script>
    <script src="https://cdn.tailwindcss.com"></script>

    <style>
        @import url('https://fonts.googleapis.com/css2?family=Cinzel:wght@400;600;700&family=Montserrat:wght@300;400;500;600&family=Pinyon+Script&display=swap');
        
        body { 
            font-family: 'Montserrat', sans-serif; 
            background-color: #006994;
            margin: 0;
            overflow-x: hidden;
            color: #115e59;
        }
        h1, h2, h3, h4 { font-family: 'Cinzel', serif; }
        .script-font { font-family: 'Pinyon Script', cursive; }
        
        /* Ocean Gradients */
        .ocean-depths {
            background: linear-gradient(180deg, #80deea 0%, #26c6da 40%, #006064 100%);
            position: fixed; top: 0; left: 0; width: 100%; height: 100%; z-index: -20;
        }
        .sun-rays {
            position: absolute; top: -100px; left: 50%; transform: translateX(-50%);
            width: 150%; height: 600px;
            background: radial-gradient(ellipse at top, rgba(255, 255, 255, 0.4) 0%, transparent 70%);
            pointer-events: none; z-index: -15; mix-blend-mode: overlay;
        }
        
        /* Cards */
        .pearl-card {
            background: rgba(255, 255, 255, 0.95);
            backdrop-filter: blur(10px);
            border: 1px solid rgba(255, 255, 255, 0.8);
            box-shadow: 0 10px 20px rgba(0,0,0,0.1);
            transition: all 0.3s ease;
            display: flex;
            flex-direction: column;
        }
        .pearl-card:hover { 
            transform: translateY(-8px); 
            box-shadow: 0 20px 30px rgba(0,0,0,0.15);
        }

        /* Container da Imagem */
        .card-image-container {
            width: 100%;
            height: 250px; 
            overflow: hidden;
            border-bottom: 1px solid #e0f2f1;
            position: relative;
            background-color: #f0fdfa;
            cursor: pointer;
        }
        .card-image {
            width: 100%;
            height: 100%;
            object-fit: cover; 
            object-position: top;
            transition: transform 0.5s ease;
        }
        .pearl-card:hover .card-image {
            object-fit: contain; /* Mostra imagem inteira ao passar o mouse */
            background-color: rgba(0,0,0,0.05);
        }

        .glass-panel {
            background: rgba(255, 255, 255, 0.2);
            backdrop-filter: blur(12px);
            border: 1px solid rgba(255, 255, 255, 0.3);
            box-shadow: 0 8px 32px 0 rgba(31, 38, 135, 0.15);
        }

        /* Animações */
        .bubble {
            position: absolute; bottom: -50px;
            background: radial-gradient(circle at 30% 30%, rgba(255, 255, 255, 0.8), rgba(255, 255, 255, 0.1));
            border-radius: 50%;
            animation: rise linear infinite; z-index: -10;
        }
        @keyframes rise {
            0% { transform: translateY(0) scale(1); opacity: 0; }
            100% { transform: translateY(-120vh) scale(1.2); opacity: 0; }
        }
        
        ::-webkit-scrollbar { width: 6px; }
        ::-webkit-scrollbar-track { background: #f1f1f1; }
        ::-webkit-scrollbar-thumb { background: #2dd4bf; border-radius: 10px; }
    </style>
</head>
<body>
    <div id="root"></div>

    <script type="text/babel">
        // Se tiver chave Gemini, coloque aqui
        const GOOGLE_API_KEY = ""; 

        const { useState, useEffect } = React;

        // --- ÍCONES SVG ---
        const Icons = {
            Gift: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><rect x="3" y="8" width="18" height="4" rx="1"/><path d="M12 8v13"/><path d="M19 12v7a2 2 0 0 1-2 2H7a2 2 0 0 1-2-2v-7"/><path d="M7.5 8a2.5 2.5 0 0 1 0-5A4.8 8 0 0 1 12 8a4.8 8 0 0 1 4.5-5 2.5 2.5 0 0 1 0 5"/></svg>,
            Shell: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M14 2c-3.87 0-7 3.13-7 7 0 5.25 7 13 7 13s7-7.75 7-13c0-3.87-3.13-7-7-7z"/><path d="M11 21c0-3 2-5 2-9"/><path d="M7.5 9a6.5 6.5 0 0 1 13 0"/></svg>,
            Star: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><polygon points="12 2 15.09 8.26 22 9.27 17 14.14 18.18 21.02 12 17.77 5.82 21.02 7 14.14 2 9.27 8.91 8.26 12 2"/></svg>,
            Copy: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><rect x="9" y="9" width="13" height="13" rx="2" ry="2"/><path d="M5 15H4a2 2 0 0 1-2-2V4a2 2 0 0 1 2-2h9a2 2 0 0 1 2 2v1"/></svg>,
            Check: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><polyline points="20 6 9 17 4 12"/></svg>,
            X: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><line x1="18" y1="6" x2="6" y2="18"/><line x1="6" y1="6" x2="18" y2="18"/></svg>,
            Sparkles: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="m12 3-1.912 5.813a2 2 0 0 1-1.275 1.275L3 12l5.813 1.912a2 2 0 0 1 1.275 1.275L12 21l1.912-5.813a2 2 0 0 1 1.275-1.275L21 12l-5.813-1.912a2 2 0 0 1-1.275-1.275L12 3Z"/></svg>,
            MessageCircle: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="m3 21 1.9-5.7a8.5 8.5 0 1 1 3.8 3.8z"/></svg>,
            Heart: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M20.84 4.61a5.5 5.5 0 0 0-7.78 0L12 5.67l-1.06-1.06a5.5 5.5 0 0 0-7.78 7.78l1.06 1.06L12 21.23l7.78-7.78 1.06-1.06a5.5 5.5 0 0 0 0-7.78z"></path></svg>,
            RefreshCw: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M3 12a9 9 0 0 1 9-9 9.75 9.75 0 0 1 6.74 2.74L21 8"/><path d="M21 3v5h-5"/><path d="M21 12a9 9 0 0 1-9 9 9.75 9.75 0 0 1-6.74-2.74L3 16"/><path d="M8 16H3v5"/></svg>,
            Wand2: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="m21.64 3.64-1.28-1.28a1.21 1.21 0 0 0-1.72 0L2.36 18.64a1.21 1.21 0 0 0 0 1.72l1.28 1.28a1.2 1.2 0 0 0 1.72 0L21.64 5.36a1.2 1.2 0 0 0 0-1.72Z"/><path d="m14 7 3 3"/><path d="M5 6v4"/><path d="M19 14v4"/><path d="M10 2v2"/><path d="M7 8H3"/><path d="M21 16h-4"/><path d="M11 3H9"/></svg>,
            Calendar: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><rect width="18" height="18" x="3" y="4" rx="2" ry="2"/><line x1="16" x2="16" y1="2" y2="6"/><line x1="8" x2="8" y1="2" y2="6"/><line x1="3" x2="21" y1="10" y2="10"/></svg>,
            Clock: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><circle cx="12" cy="12" r="10"/><polyline points="12 6 12 12 16 14"/></svg>,
            MapPin: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><path d="M20 10c0 6-8 12-8 12s-8-6-8-12a8 8 0 0 1 16 0Z"/><circle cx="12" cy="10" r="3"/></svg>,
            ImageIcon: ({size=24, className=""}) => <svg width={size} height={size} viewBox="0 0 24 24" fill="none" stroke="currentColor" strokeWidth="2" strokeLinecap="round" strokeLinejoin="round" className={className}><rect width="18" height="18" x="3" y="3" rx="2" ry="2"/><circle cx="9" cy="9" r="2"/><path d="m21 15-3.086-3.086a2 2 0 0 0-2.828 0L6 21"/></svg>
        };

        function App() {
            const [isModalOpen, setIsModalOpen] = useState(false);
            const [selectedGift, setSelectedGift] = useState(null);
            const [guestName, setGuestName] = useState("");
            const [pixCopied, setPixCopied] = useState(false);
            
            // Estados de IA
            const [generatedMessage, setGeneratedMessage] = useState("");
            const [oracleResult, setOracleResult] = useState(null);
            const [isProcessing, setIsProcessing] = useState(false);
            const [bubbles, setBubbles] = useState([]);
            const [showAiOptions, setShowAiOptions] = useState(false);
            const [messageStyle, setMessageStyle] = useState("carinhosa");

            useEffect(() => {
                setBubbles(Array.from({length: 20}, (_, i) => ({
                    id: i, left: `${Math.random()*100}%`, size: `${Math.random()*15+5}px`, 
                    duration: `${Math.random()*15+10}s`, delay: `${Math.random()*5}s`
                })));
            }, []);

            // --- LISTA DE PRESENTES VINCULADA AOS NOMES DE ARQUIVO ---
            const giftList = [
                // Grupo 1: Imagem ...223658
                { id: 1, name: "Calça Jeans Pantalona", detail: "Azul Claro (38/16/M)", category: "Moda", image: "Screenshot_20260131_223658_WhatsApp.jpg" },
                { id: 2, name: "Wide Leg Cargo", detail: "Off-White (38/16/M)", category: "Moda", image: "Screenshot_20260131_223658_WhatsApp.jpg" },
                { id: 3, name: "Pijama Listrado", detail: "Rosa e Branco (38/16/M)", category: "Moda", image: "Screenshot_20260131_223658_WhatsApp.jpg" },
                { id: 4, name: "Copo Stanley", detail: "Rosa Quartz Térmico", category: "Acessório", image: "Screenshot_20260131_223658_WhatsApp.jpg" },
                { id: 25, name: "Jaqueta Puffer Preta", detail: "Verniz com Capuz Pelúcia (38/M)", category: "Moda", image: "Screenshot_20260131_223658_WhatsApp.jpg" },
                { id: 26, name: "Casaco Esportivo Off-White", detail: "Estilo Lululemon (38/M)", category: "Moda", image: "Screenshot_20260131_223658_WhatsApp.jpg" },
                { id: 27, name: "Moletom Bege Flor Azul", detail: "'Perfect is Boring' (38/M)", category: "Moda", image: "Screenshot_20260131_223658_WhatsApp.jpg" },
                
                // Grupo 2: Imagem ...223641
                { id: 5, name: "Chinelo Farm Tucano", detail: "Tamanho 37", category: "Calçados", image: "Screenshot_20260131_223641_WhatsApp.jpg" },
                { id: 6, name: "Garrafa Farm", detail: "Xilo Tropical (Azul)", category: "Acessório", image: "Screenshot_20260131_223641_WhatsApp.jpg" },
                { id: 7, name: "Pelúcia Marie Big Feet", detail: "Disney", category: "Diversos", image: "Screenshot_20260131_223641_WhatsApp.jpg" },
                
                // Grupo 3: Imagem ...223636
                { id: 8, name: "Adidas Campus Cinza", detail: "Tamanho 37", category: "Calçados", image: "Screenshot_20260131_223636_WhatsApp.jpg" },
                { id: 9, name: "Adidas Campus Preto", detail: "Tamanho 37", category: "Calçados", image: "Screenshot_20260131_223636_WhatsApp.jpg" },
                { id: 10, name: "Nike Dunk Low Twist", detail: "Cinza/Branco (Tam 37)", category: "Calçados", image: "Screenshot_20260131_223636_WhatsApp.jpg" },
                { id: 11, name: "Slide Fila Drifter", detail: "Bege (Tam 37)", category: "Calçados", image: "Screenshot_20260131_223636_WhatsApp.jpg" },
                
                // Grupo 4: Imagem ...223631
                { id: 12, name: "Escova Secadora", detail: "Foxybae Blush / Elétrica", category: "Beleza", image: "Screenshot_20260131_223631_WhatsApp.jpg" },
                { id: 13, name: "Baby Liss", detail: "Modelador de Cachos", category: "Beleza", image: "Screenshot_20260131_223631_WhatsApp.jpg" },
                { id: 14, name: "Kit de Maquiagem", detail: "Paleta Sombras/Face", category: "Beleza", image: "Screenshot_20260131_223631_WhatsApp.jpg" },
                { id: 15, name: "Kit de Pincéis", detail: "Profissional (Rosa)", category: "Beleza", image: "Screenshot_20260131_223631_WhatsApp.jpg" },
                
                // Grupo 5: Imagem ...223627
                { id: 16, name: "Pulseira Vivara Life", detail: "Prata", category: "Joias", image: "Screenshot_20260131_223627_WhatsApp.jpg" },
                { id: 17, name: "Kit de Joias", detail: "Prata 925", category: "Joias", image: "Screenshot_20260131_223627_WhatsApp.jpg" },
                { id: 18, name: "Relógio Casio", detail: "Vintage Prata (Prova d'água)", category: "Acessório", image: "Screenshot_20260131_223627_WhatsApp.jpg" },
                { id: 19, name: "Smart Watch", detail: "Prova d'água", category: "Tech", image: "Screenshot_20260131_223627_WhatsApp.jpg" },
                
                // Grupo 6: Imagem ...223621
                { id: 20, name: "Kit Lily", detail: "O Boticário", category: "Cosméticos", image: "Screenshot_20260131_223621_WhatsApp.jpg" },
                { id: 21, name: "Kit Glosslicious", detail: "Fran by Franciny Ehlke", category: "Maquiagem", image: "Screenshot_20260131_223621_WhatsApp.jpg" },
                { id: 22, name: "Perfume Hello Hello!", detail: "Nah Cardoso", category: "Perfume", image: "Screenshot_20260131_223621_WhatsApp.jpg" },
                
                // Grupo 7: Imagem ...223615
                { id: 23, name: "Egeo Choc", detail: "O Boticário", category: "Perfume", image: "Screenshot_20260131_223615_WhatsApp.jpg" },
                { id: 24, name: "Kit Deleite", detail: "Cuide-se Bem", category: "Cosméticos", image: "Screenshot_20260131_223615_WhatsApp.jpg" }
            ];

            const handleGiftClick = (item) => {
                setSelectedGift(item);
                setGeneratedMessage("");
                setOracleResult(null);
                setShowAiOptions(false);
                setIsModalOpen(true);
            };

            const handleConfirm = () => {
                if (!guestName.trim()) return alert("Por favor, digite seu nome!");
                const phone = "5521980683275";
                const text = generatedMessage || `Olá! Eu sou ${guestName} e escolhi presentear a Lara com: ${selectedGift.name}.`;
                window.open(`https://wa.me/${phone}?text=${encodeURIComponent(text)}`, '_blank');
                setIsModalOpen(false);
            };

            const copyPix = () => {
                navigator.clipboard.writeText("(21) 98392-6637");
                setPixCopied(true);
                setTimeout(() => setPixCopied(false), 2000);
            };

            const callAI = async (type) => {
                if (!guestName.trim()) return alert("Digite seu nome primeiro!");
                if (!GOOGLE_API_KEY) {
                    if (type === 'message') setGeneratedMessage(`Oie Lara! Aqui é ${guestName}. Escolhi o ${selectedGift.name} com muito carinho pra você! 🌊💙`);
                    else setOracleResult({title: "Estrela do Mar", desc: "Você brilha por onde passa!"});
                    return;
                }
                setIsProcessing(true);
                try {
                    const prompt = type === 'message' 
                        ? `Escreva uma mensagem curta de WhatsApp de um convidado chamado ${guestName} para a aniversariante Lara (15 anos) sobre o presente ${selectedGift.name}. Estilo divertido e carinhoso. OBRIGATÓRIO: Incluir o nome ${guestName} no texto.`
                        : `Aja como um oráculo do mar. Defina a 'Personalidade Marinha' de alguém que escolheu ${selectedGift.name}. Retorne APENAS: Título Místico | Uma frase curta divertida.`;
                    
                    const res = await fetch(`https://generativelanguage.googleapis.com/v1beta/models/gemini-2.5-flash-preview-09-2025:generateContent?key=${GOOGLE_API_KEY}`, {
                        method: 'POST', headers: {'Content-Type': 'application/json'},
                        body: JSON.stringify({ contents: [{ parts: [{ text: prompt }] }] })
                    });
                    const data = await res.json();
                    const text = data.candidates?.[0]?.content?.parts?.[0]?.text;
                    if (type === 'message') setGeneratedMessage(text);
                    else {
                        const [t, d] = text.split('|');
                        setOracleResult({ title: t, desc: d || t });
                    }
                } catch (e) { console.error(e); }
                setIsProcessing(false);
            };

            return (
                <div className="min-h-screen text-gray-800 relative overflow-hidden pb-20">
                    <div className="ocean-depths"></div>
                    <div className="sun-rays"></div>
                    <div className="fixed inset-0 pointer-events-none">
                        {bubbles.map(b => <div key={b.id} className="bubble" style={{left: b.left, width: b.size, height: b.size, animationDuration: b.duration, animationDelay: b.delay}}/>)}
                    </div>

                    <div className="container mx-auto px-4 pt-12 relative z-10 max-w-6xl">
                        {/* Header */}
                        <header className="text-center text-white mb-16">
                            <div className="inline-block relative">
                                <Icons.Sparkles className="absolute -top-6 -left-8 text-teal-200 animate-pulse" />
                                <h2 className="text-lg tracking-[0.3em] font-light uppercase text-teal-100">Convite Especial</h2>
                                <Icons.Sparkles className="absolute -bottom-4 -right-8 text-teal-200 animate-pulse" />
                            </div>
                            <h1 className="text-5xl md:text-7xl font-bold mt-4 mb-2 drop-shadow-lg text-transparent bg-clip-text bg-gradient-to-b from-white to-teal-100">Lara Hamphreis</h1>
                            
                            {/* Data e Local */}
                            <div className="mt-6 bg-white/10 backdrop-blur-md rounded-xl p-4 inline-block border border-white/20 shadow-lg">
                                <div className="flex flex-col md:flex-row gap-4 md:gap-8 text-teal-50 text-sm font-medium tracking-wide justify-center items-center">
                                    <span className="flex items-center gap-2"><Icons.Calendar size={18} /> 28/03/2026</span>
                                    <span className="hidden md:block text-white/30">|</span>
                                    <span className="flex items-center gap-2"><Icons.Clock size={18} /> 12:50</span>
                                    <span className="hidden md:block text-white/30">|</span>
                                    <span className="flex items-center gap-2"><Icons.MapPin size={18} /> Sítio Green Garden</span>
                                </div>
                            </div>

                            <div className="flex justify-center items-center gap-4 text-teal-50 opacity-80 mt-8">
                                <div className="h-px w-12 bg-white"></div>
                                <span className="text-2xl script-font">15 Anos</span>
                                <div className="h-px w-12 bg-white"></div>
                            </div>
                        </header>

                        {/* PIX Area */}
                        <div className="max-w-xl mx-auto glass-panel rounded-3xl p-8 mb-16 text-center text-white relative overflow-hidden bg-white/10">
                            <div className="absolute top-0 left-0 w-full h-1 bg-gradient-to-r from-transparent via-white to-transparent opacity-50"></div>
                            <Icons.Heart className="mx-auto text-teal-200 mb-6 fill-current animate-pulse" size={36} />
                            <p className="text-white text-lg mb-6 font-light italic">"Sua presença é o melhor presente! Mas se quiser me mimar, aqui estão algumas sugestões ou a opção do PIX."</p>
                            <div className="bg-white/20 rounded-xl p-4 backdrop-blur-sm border border-white/30 inline-block w-full">
                                <p className="text-xs uppercase tracking-widest font-bold mb-2 text-teal-100">Chave PIX (Celular)</p>
                                <p className="text-2xl font-mono mb-4 text-white drop-shadow-md">(21) 98392-6637</p>
                                <button onClick={copyPix} className={`w-full py-2 rounded-lg font-bold transition-all flex items-center justify-center gap-2 ${pixCopied ? 'bg-teal-600 text-white' : 'bg-white text-teal-900 hover:bg-teal-50'}`}>
                                    {pixCopied ? <Icons.Check size={18}/> : <Icons.Copy size={18}/>} {pixCopied ? "Copiado!" : "Copiar Chave"}
                                </button>
                            </div>
                        </div>

                        {/* Gift Grid */}
                        <div className="grid grid-cols-1 sm:grid-cols-2 lg:grid-cols-3 xl:grid-cols-4 gap-6">
                            {giftList.map(item => (
                                <div key={item.id} onClick={() => handleGiftClick(item)} className="pearl-card rounded-2xl overflow-hidden cursor-pointer group flex flex-col min-h-[300px]">
                                    {/* IMAGEM DO ARQUIVO LOCAL */}
                                    <div className="card-image-container relative">
                                        <img 
                                            src={item.image} 
                                            alt={item.name} 
                                            className="card-image"
                                            onError={(e) => { 
                                                e.target.onerror = null; 
                                                e.target.style.display = 'none'; 
                                                e.target.nextSibling.style.display = 'flex';
                                            }}
                                        />
                                        {/* Fallback caso a imagem não carregue */}
                                        <div className="hidden absolute inset-0 flex-col items-center justify-center text-teal-400 p-4 text-center">
                                            <Icons.ImageIcon size={32} />
                                            <span className="text-[10px] mt-2 text-teal-600 font-medium break-all">Foto: {item.image}</span>
                                        </div>
                                        <div className="absolute top-2 right-2 bg-white/90 backdrop-blur px-2 py-1 rounded text-[10px] font-bold text-teal-600 uppercase tracking-widest shadow-sm">
                                            {item.category}
                                        </div>
                                    </div>
                                    
                                    <div className="p-5 flex flex-col flex-1 text-center justify-between bg-gradient-to-b from-white to-teal-50/30">
                                        <div>
                                            <h3 className="text-gray-800 font-serif text-lg font-bold leading-tight mb-2 group-hover:text-teal-700 transition-colors">{item.name}</h3>
                                            <p className="text-xs text-gray-500 italic mb-4">{item.detail}</p>
                                        </div>
                                        <div className="mt-2 text-teal-600 text-xs font-bold uppercase tracking-wider flex items-center justify-center gap-2 opacity-60 group-hover:opacity-100 transition-opacity">
                                            <Icons.Gift size={14} /> Escolher
                                        </div>
                                    </div>
                                </div>
                            ))}
                        </div>

                        <footer className="text-center text-white/60 mt-20 pb-8 text-xs tracking-widest uppercase">
                            <p className="flex justify-center items-center gap-2">Feito com <Icons.Heart size={12} className="text-teal-300"/> para os 15 anos da Lara</p>
                        </footer>
                    </div>

                    {/* Modal */}
                    {isModalOpen && (
                        <div className="fixed inset-0 z-50 flex items-center justify-center p-4">
                            <div className="absolute inset-0 bg-teal-900/80 backdrop-blur-sm" onClick={() => setIsModalOpen(false)}></div>
                            <div className="bg-white rounded-3xl shadow-2xl w-full max-w-md relative z-10 overflow-hidden border border-teal-100 max-h-[90vh] overflow-y-auto">
                                <div className="h-40 bg-gray-100 relative">
                                    <img 
                                        src={selectedGift?.image} 
                                        className="w-full h-full object-cover object-top"
                                        onError={(e) => { e.target.style.display = 'none'; }}
                                    />
                                    <div className="absolute inset-0 bg-gradient-to-t from-white via-transparent to-transparent"></div>
                                    <button onClick={() => setIsModalOpen(false)} className="absolute top-4 right-4 bg-white/80 p-2 rounded-full text-gray-600 hover:text-red-500 hover:bg-white transition-all shadow-md"><Icons.X /></button>
                                </div>
                                
                                <div className="p-8 pt-2 text-center relative">
                                    <div className="inline-flex items-center justify-center w-14 h-14 rounded-full bg-teal-100 text-teal-600 mb-4 shadow-lg -mt-9 relative z-10 border-4 border-white">
                                        <Icons.Gift size={28} />
                                    </div>

                                    <h3 className="text-2xl font-serif font-bold text-teal-900 mb-1">Ótima Escolha!</h3>
                                    <p className="text-gray-600 text-sm mb-6">Você escolheu: <span className="font-bold text-teal-600 block text-lg mt-1">{selectedGift?.name}</span></p>

                                    {/* Oráculo */}
                                    {!oracleResult && (
                                        <button onClick={() => callAI('oracle')} disabled={isProcessing} className="w-full mb-6 py-2 border border-teal-200 text-teal-600 rounded-xl text-xs font-bold hover:bg-teal-50 transition-colors flex items-center justify-center gap-2">
                                            {isProcessing ? "..." : <><Icons.Star size={14}/> Revelar Vibe do Mar (IA)</>}
                                        </button>
                                    )}
                                    {oracleResult && (
                                        <div className="mb-6 bg-teal-50 p-4 rounded-xl border border-teal-100 animate-pulse">
                                            <p className="text-xs uppercase font-bold text-teal-400 mb-1">O Oráculo Diz:</p>
                                            <p className="font-bold text-teal-800">{oracleResult.title}</p>
                                            <p className="text-xs text-teal-600 italic">"{oracleResult.desc}"</p>
                                        </div>
                                    )}

                                    <div className="space-y-4 text-left">
                                        <div>
                                            <label className="text-xs font-bold text-gray-400 uppercase ml-1">Seu Nome</label>
                                            <input type="text" value={guestName} onChange={e => setGuestName(e.target.value)} className="w-full mt-1 px-4 py-3 bg-gray-50 border border-gray-200 rounded-xl focus:ring-2 focus:ring-teal-400 outline-none" placeholder="Digite seu nome..." />
                                        </div>

                                        {/* Gerador Mensagem */}
                                        <div className="bg-gray-50 p-3 rounded-xl border border-gray-100">
                                            <div className="flex justify-between items-center mb-2">
                                                <span className="text-xs font-bold text-gray-400 uppercase flex gap-1 items-center"><Icons.Sparkles size={12}/> Mensagem Automática</span>
                                                <button onClick={() => {setShowAiOptions(true); callAI('message');}} disabled={isProcessing} className="text-[10px] bg-teal-100 text-teal-700 px-2 py-1 rounded font-bold hover:bg-teal-200">Gerar com IA</button>
                                            </div>
                                            {generatedMessage ? (
                                                <textarea value={generatedMessage} onChange={e => setGeneratedMessage(e.target.value)} className="w-full p-2 text-sm bg-white rounded-lg border border-gray-200 h-20 resize-none outline-none focus:border-teal-300" />
                                            ) : (
                                                <p className="text-xs text-gray-400 italic text-center py-2">Clique em gerar ou escreva a sua...</p>
                                            )}
                                        </div>

                                        <button onClick={handleConfirm} className="w-full py-4 bg-gradient-to-r from-teal-500 to-cyan-600 text-white rounded-xl font-bold shadow-lg hover:shadow-xl hover:-translate-y-1 transition-all flex items-center justify-center gap-2">
                                            <Icons.MessageCircle size={18} /> Confirmar e Enviar
                                        </button>
                                    </div>
                                </div>
                            </div>
                        </div>
                    )}
                </div>
            );
        }

        const root = ReactDOM.createRoot(document.getElementById('root'));
        root.render(<App />);
    </script>
</body>
</html>
