<!DOCTYPE html>
<html lang="pt-BR">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <meta name="description" content="Cuidado é Estilo - Moda, Lifestyle e Bem-estar">
    <meta name="keywords" content="moda, lifestyle, bem-estar, cuidados pessoais">
    <meta name="author" content="Lucas">
    <title>Cuidado é Estilo</title>
    <style>
        /* Estilos Gerais */
        body {
            font-family: Arial, sans-serif;
            margin: 0;
            padding: 0;
            background-color: #f4f4f4;
            color: #333;
        }
        header {
            background-color: #28a745;
            color: white;
            padding: 10px;
            display: flex;
            justify-content: space-between;
            align-items: center;
        }
        header h1 {
            margin: 0;
        }
        header .search-container {
            display: flex;
            align-items: center;
        }
        header input[type="text"] {
            padding: 5px;
            border: none;
            border-radius: 3px;
        }
        header button {
            margin-left: 5px;
            padding: 5px 10px;
            background-color: white;
            color: #28a745;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }
        main {
            padding: 20px;
        }
        .posts {
            display: grid;
            grid-template-columns: repeat(auto-fit, minmax(300px, 1fr));
            gap: 20px;
            margin-bottom: 20px;
        }
        .post {
            padding: 15px;
            background: white;
            border-radius: 5px;
            box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
            text-align: center;
        }
        .post h3 {
            margin: 10px 0;
            color: #28a745;
        }
        .post img {
            width: 100%;
            height: auto;
            border-radius: 5px;
        }
        .post a {
            text-decoration: none;
            color: #28a745;
        }
        .pagination {
            text-align: center;
            margin-top: 20px;
        }
        .pagination button {
            padding: 10px 15px;
            margin: 5px;
            background-color: #28a745;
            color: white;
            border: none;
            border-radius: 3px;
            cursor: pointer;
        }
        footer {
            text-align: center;
            background-color: #28a745;
            color: white;
            padding: 20px;
        }
        footer a {
            margin: 0 10px;
            text-decoration: none;
            color: white;
        }
        footer a:hover {
            text-decoration: underline;
        }
    </style>
</head>
<body>
    <header>
        <h1>Cuidado é Estilo</h1>
        <div class="search-container">
            <input type="text" placeholder="Buscar...">
            <button>Home</button>
        </div>
    </header>
    <main id="home">
        <h2>Bem-vindo ao Cuidado é Estilo!</h2>
        <p>Explore nossos posts de moda, cuidados pessoais e muito mais.</p>

        <!-- Lista de Posts -->
        <div class="posts" id="posts"></div>

        <!-- Paginação -->
        <div class="pagination">
            <button id="prevPage" onclick="changePage(-1)">⟵ Anterior</button>
            <button id="nextPage" onclick="changePage(1)">Próximo ⟶</button>
        </div>
    </main>
    <footer>
        <p>&copy; 2025 Cuidado é Estilo. Todos os direitos reservados.</p>
        <nav>
            <a href="#sobre">Sobre</a>
            <a href="#contato">Contato</a>
            <a href="#politica">Política de Privacidade</a>
            <a href="#termos">Termos de Uso</a>
        </nav>
    </footer>
    <script>
        const posts = [
            {
                title: "Cuidados com a Pele no Verão",
                image: "https://source.unsplash.com/600x400/?skincare",
                link: "post1.html"
            },
            {
                title: "Benefícios de Hidratação",
                image: "https://source.unsplash.com/600x400/?water",
                link: "post2.html"
            },
            {
                title: "Estilo Minimalista",
                image: "https://source.unsplash.com/600x400/?minimalist",
                link: "post3.html"
            },
            // Adicione mais posts no mesmo formato
        ];

        let currentPage = 1;
        const postsPerPage = 10;

        function renderPosts() {
            const postsContainer = document.getElementById("posts");
            postsContainer.innerHTML = "";
            const start = (currentPage - 1) * postsPerPage;
            const end = start + postsPerPage;

            posts.slice(start, end).forEach(post => {
                const postDiv = document.createElement("div");
                postDiv.classList.add("post");
                postDiv.innerHTML = `
                    <a href="${post.link}">
                        <h3>${post.title}</h3>
                        <img src="${post.image}" alt="${post.title}" loading="lazy">
                    </a>
                `;
                postsContainer.appendChild(postDiv);
            });
        }

        function changePage(direction) {
            const totalPages = Math.ceil(posts.length / postsPerPage);
            currentPage = Math.max(1, Math.min(currentPage + direction, totalPages));
            renderPosts();
        }

        // Renderiza os posts iniciais
        renderPosts();
    </script>
</body>
</html>
