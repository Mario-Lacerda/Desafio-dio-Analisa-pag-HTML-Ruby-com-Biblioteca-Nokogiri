# Desafio-dio-Analisa-pag-HTML-Ruby-com-Biblioteca-Nokogiri
# Desafio Dio - Analisando Páginas HTML em Ruby com a Biblioteca Nokogiri



Neste guia, vamos explorar como usar a biblioteca **Nokogiri** para analisar páginas HTML em Ruby. O Nokogiri é uma ferramenta poderosa que facilita a manipulação e extração de dados de documentos HTML e XML.

   

## Objetivos do Projeto

- **Fazer uma requisição HTTP** para obter o conteúdo de uma página HTML.
- **Analisar** o conteúdo HTML usando Nokogiri.
- **Extrair informações** específicas, como títulos, links e outros elementos.



## Pré-requisitos

Antes de começar, você precisa ter o Ruby instalado e a biblioteca Nokogiri. Para instalar o Nokogiri, execute o seguinte comando no seu terminal:

bash



```bash
gem install nokogiri
```

## Estrutura do Código

### Exemplo de Código

Aqui está um exemplo básico de como usar o Nokogiri para analisar uma página HTML:

ruby



```ruby
require 'nokogiri'
require 'open-uri'

def analisar_pagina(url)
  # Faz uma requisição HTTP para a URL
  begin
    conteudo = URI.open(url)
    documento = Nokogiri::HTML(conteudo)

    # Extrai e exibe o título da página
    titulo = documento.at('title').text
    puts "Título da Página: #{titulo}"

    # Extrai e exibe todos os links da página
    puts "\nLinks encontrados na página:"
    documento.css('a').each do |link|
      href = link['href']
      texto = link.text.strip
      puts "#{texto}: #{href}"
    end
  rescue StandardError => e
    puts "Ocorreu um erro ao acessar a página: #{e.message}"
  end
end

# URL da página que você deseja analisar
url = 'https://www.exemplo.com'

# Executar a análise da página
analisar_pagina(url)
```

## Explicação do Código

### Funções Principais

- analisar_pagina(url)

  :

  - Faz uma requisição para a URL fornecida e obtém o conteúdo HTML.
  - Cria um objeto Nokogiri a partir do conteúdo HTML.
  - Extrai e exibe o título da página.
  - Extrai todos os links (`<a>`) da página e exibe o texto do link junto com o seu URL.

### Tratamento de Erros

- O programa usa um bloco `begin-rescue` para capturar e exibir erros que podem ocorrer, como problemas de rede ou URLs inválidas.

## Como Executar o Programa

1. **Crie um novo arquivo Ruby** chamado `analisador_html.rb`:

   bash

   ```bash
   touch analisador_html.rb
   ```

2. **Abra o arquivo** em um editor de texto e cole o código acima.

3. **Altere a variável `url`** para a página que você deseja analisar.

4. **Execute o programa** no terminal:

   bash

   

   ```bash
   ruby analisador_html.rb
   ```

## Exemplo de Saída

Quando você executar o programa, a saída será semelhante a:

plaintext



```plaintext
Título da Página: Exemplo de Página

Links encontrados na página:
Home: /
Sobre: /sobre
Contato: /contato
```

### Mensagem de Erro

Se o programa encontrar um erro ao acessar a página, a saída será:

plaintext



```plaintext
Ocorreu um erro ao acessar a página: [mensagem de erro]
```

## Conclusão

Este projeto fornece uma introdução ao uso da biblioteca Nokogiri para analisar páginas HTML em Ruby. Você pode expandir este exemplo para incluir extrações mais complexas ou trabalhar com dados de diferentes elementos HTML.
