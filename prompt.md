## prompt 1

quero criar um jogo da memória na raiz do meu projeto, tem uma pasta img com as cartas, os nomes delas são assim: "carta1.jpg", "carta2.jpg" (vamos seguir esse padrão apenas incrementando o numero da carta)
criar uma variável para controlar quantas cartas devem ser lidas

o fluxo é o seguinte:
- ao clica em uma carta, ela vira pra cima
- ao clicar em outra, ela também vira pra cima
- se a pessoa errou o par: aguarda 1 segundo e vira ambas para baixo
- se a pessoa acertou o par: mantém as cartas viradas e ela pode ir pra proxima tentativa

existe uma segunda página (semelhante a um caderno ou album de figurinhas), onde as cartas que a pessoa já achou o par, são exibidas.
ao clicar na carta, abre um modal com mais informações.


tecnologias:
- html vanilla static (vou usar live server para hostear)
- tailwindcss: <script src="https://cdn.jsdelivr.net/npm/@tailwindcss/browser@4"></script>
- js vanilla

## prompt2

na verdade, crie um vetor, onde eu vou editar apenas esse vetor, para colocar o nome das cartas

[ "carta1.jpg", "seila.png" ]

nem todas cartas vao ter o mesmo nome, e nem sempre o mesmo formato.

// Informações dos animais
        const animaisInfo = {
            1: { nome: "Arara-azul-de-lear", desc: "Ave endêmica da Bahia, conhecida por sua plumagem azul vibrante e bico forte." },
            2: { nome: "Peixe-boi-da-amazônia", desc: "Mamífero aquático herbívoro que habita rios e lagos da Amazônia." },
            3: { nome: "Tartaruga-verde", desc: "Réptil marinho que pode ser encontrado no litoral brasileiro, se alimenta principalmente de algas." },
            4: { nome: "Sagui-de-duas-cores", desc: "Pequeno primata encontrado na Mata Atlântica, conhecido por sua agilidade." },
            5: { nome: "Onça-pintada", desc: "O maior felino das Américas, símbolo da fauna brasileira e excelente nadador." },
            6: { nome: "Tamanduá-bandeira", desc: "Mamífero com língua longa e pegajosa, se alimenta principalmente de formigas e cupins." }
        };

pensando bem , talvez seria melhor, adicionar uma nova chave, qeu guarda o nome da foto ...



## prompt3 

function atualizarAlbum() {
            albumGrid.innerHTML = '';
            
            if (paresEncontrados.size === 0) {
                mensagemAlbumVazio.classList.remove('hidden');
                return;
            }
            
            mensagemAlbumVazio.classList.add('hidden');
            
            paresEncontrados.forEach(numero => {
                const cartaAlbum = document.createElement('div');
                cartaAlbum.className = 'bg-white rounded-xl shadow-lg overflow-hidden cursor-pointer transform hover:scale-105 transition';
                cartaAlbum.innerHTML = `
                    <img src="img/carta${numero}.jpg" alt="${animaisInfo[numero].nome}" class="w-full h-48 object-cover">
                    <div class="p-3">
                        <h4 class="font-bold text-teal-700 text-sm">${animaisInfo[numero].nome}</h4>
                    </div>
                `;
                cartaAlbum.addEventListener('click', () => abrirModal(numero));
                albumGrid.appendChild(cartaAlbum);
            });
        }
        function abrirModal(numero) {
            const info = animaisInfo[numero];
            document.getElementById('modalImg').src = `img/carta${numero}.jpg`;
            document.getElementById('modalTitle').textContent = info.nome;
            document.getElementById('modalDesc').textContent = info.desc;
            modal.classList.remove('hidden');
            modal.classList.add('flex');
        }

veja que tem lugares usando o formato antigo, onde é fixo o nome da carta, revise todo o codigo para ler do array.

index.html:245 Uncaught ReferenceError: animaisInfo is not defined
    at index.html:245:62
    at Set.forEach (<anonymous>)
    at atualizarAlbum (index.html:241:30)
    at atualizarScore (index.html:228:13)
    at index.html:188:21