<!DOCTYPE html>
<html lang="pt-BR">
<head>
<meta charset="UTF-8">
<meta name="viewport" content="width=device-width, initial-scale=1.0">
<title>Mesmo com pouco, pode ajudar muito</title>
<style>
    body {
        font-family: Arial, sans-serif;
        text-align: center;
        background: linear-gradient(135deg, #4b0082, #000000); /* Roxo e preto */
        color: white;
        height: 100vh;
        margin: 0;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        transition: background 1s ease; /* Mais lento */
    }

    /* Flash verde */
    body.flash-green {
        background: linear-gradient(135deg, #006400, #00ff00);
        transform: scale(1.02);
    }

    h1 {
        font-size: 28px;
        margin-bottom: 30px;
    }

    /* Quadrado externo transparente */
    .outer-box {
        padding: 15px;
        border: 2px solid rgba(255, 255, 255, 0.4);
        border-radius: 20px;
        transition: transform 0.3s ease;
        display: inline-block;
    }
    .outer-box.active {
        transform: scale(1.05);
    }

    /* Quadrado interno */
    .inner-box {
        background-color: rgba(255, 255, 255, 0.1);
        padding: 20px;
        border-radius: 15px;
        transition: transform 0.3s ease;
    }
    .inner-box.active {
        transform: scale(1.05);
    }

    /* Botão */
    button {
        background-color: #8000ff;
        color: white;
        border: none;
        padding: 15px 40px;
        font-size: 18px;
        border-radius: 8px;
        cursor: pointer;
        transition: 0.3s;
    }
    button:hover {
        background-color: #a64dff;
    }

    /* Mensagem */
    #mensagem {
        margin-top: 15px;
        font-size: 16px;
        color: #00ffae;
        font-weight: bold;
        opacity: 0;
        transition: opacity 0.5s ease;
    }
    #mensagem.show {
        opacity: 1;
    }
</style>
</head>
<body id="body">

    <h1>Mesmo com pouco, pode ajudar muito</h1>

    <div class="outer-box" id="outer">
        <div class="inner-box" id="inner">
            <button onclick="copiarPix()">Copiar Pix!!</button>
            <p id="mensagem">Pix Copiado :)</p>
        </div>
    </div>

<script>
function copiarPix() {
    const chavePix = "agiotacrente200x@gmail.com";
    navigator.clipboard.writeText(chavePix).then(() => {
        const mensagem = document.getElementById("mensagem");
        const inner = document.getElementById("inner");
        const outer = document.getElementById("outer");
        const body = document.getElementById("body");

        // Anima quadrados
        inner.classList.add("active");
        outer.classList.add("active");

        // Flash verde
        body.classList.add("flash-green");
        body.style.transition = "background 1s ease, transform 0.3s ease";
        setTimeout(() => {
            inner.classList.remove("active");
            outer.classList.remove("active");
            body.classList.remove("flash-green");
        }, 1000);

        // Mostra mensagem Fade In
        mensagem.classList.add("show");
        setTimeout(() => mensagem.classList.remove("show"), 1500);
    });
}
</script>

</body>
</html>
