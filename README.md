# Comentarios-twitter
<!DOCTYPE html>
<html lang="pt-BR">
<head>
  <meta charset="UTF-8" />
  <meta name="viewport" content="width=device-width, initial-scale=1.0"/>
  <title>Sistema de Comentários</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      background-color: #f4f4f4;
      padding: 30px;
    }

    .container {
      max-width: 600px;
      margin: auto;
      background: #fff;
      padding: 20px;
      border-radius: 8px;
    }

    input[type="text"] {
      width: 80%;
      padding: 10px;
      margin-bottom: 10px;
    }

    button {
      padding: 10px;
      margin: 5px;
      cursor: pointer;
    }

    .comentario {
      background-color: #eaeaea;
      padding: 10px;
      margin-top: 10px;
      border-radius: 4px;
      position: relative;
    }

    .botoes {
      margin-top: 5px;
    }
  </style>
</head>
<body>
  <div class="container">
    <h1>Twittwer 2</h1>
    <input type="text" id="comentarioInput" placeholder="Digite seu tweet..." />
    <button onclick="adicionarComentario()">Adicionar tweet</button>

    <div id="listaComentarios"></div>
  </div>

  <script>
    function adicionarComentario() {
      const input = document.getElementById("comentarioInput");
      const texto = input.value.trim();

      if (texto === "") {
        alert("Digite um comentário!");
        return;
      }

      const comentarioDiv = document.createElement("div");
      comentarioDiv.className = "comentario";

      const textoComentario = document.createElement("p");
      textoComentario.textContent = texto;

      const botoesDiv = document.createElement("div");
      botoesDiv.className = "botoes";

      const botaoEditar = document.createElement("button");
      botaoEditar.textContent = "Editar";
      botaoEditar.onclick = function () {
        const novoTexto = prompt("Editar comentário:", textoComentario.textContent);
        if (novoTexto !== null && novoTexto.trim() !== "") {
          textoComentario.textContent = novoTexto.trim();
        }
      };

      const botaoRemover = document.createElement("button");
      botaoRemover.textContent = "Remover";
      botaoRemover.onclick = function () {
        comentarioDiv.remove();
      };

      botoesDiv.appendChild(botaoEditar);
      botoesDiv.appendChild(botaoRemover);

      comentarioDiv.appendChild(textoComentario);
      comentarioDiv.appendChild(botoesDiv);

      document.getElementById("listaComentarios").appendChild(comentarioDiv);

      input.value = "";
    }
  </script>
</body>
</html>
