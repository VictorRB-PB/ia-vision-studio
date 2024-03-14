
# Reconhecimento Facial e transformação de imagens em Dados no Azure ML  

Será realizado um passo a passo de como foi utilizado o Vision Studio da Microsoft Azure. Todas as informações foram retiradas de documentações da Microsoft Learn.




## Analisando imagens no Visual Studio

    O Azure AI Vision inclui inúmeras capacidades para compreender o conteúdo e o contexto da imagem e extrair informações das imagens.  
    O Azure AI Vision Studio permite-lhe experimentar muitas das capacidades de análise de imagens.  
   
    Neste exercício, você usará o Vision Studio para analisar imagens usando as experiências de teste integradas.  
    Suponhamos que o retalhista fictício Northwind Traders tenha decidido implementar uma “loja inteligente”, na qual os serviços de IA   
    monitorizam  a loja para identificar os clientes que necessitam de assistência e direcionam os funcionários para os ajudar.   
    Ao utilizar o Azure AI Vision, as imagens captadas por câmaras em toda a loja podem ser analisadas para fornecer descrições significativas do que representam.

1. ```Crie um recurso de serviços de IA do Azure```
      
      Você pode usar os recursos de análise de imagem do Azure AI Vision com um recurso multisserviço de serviços de IA do Azure.  
      Se ainda não o fez, crie um recurso de serviços de IA do Azure na sua assinatura do Azure

      `` 1.1 Em outra guia do navegador, abra o portal do Azure em https://portal.azure.com, entrando com a conta da Microsoft associada à sua assinatura do Azure.``
       
     `` 1.2 Clique no botão ＋Criar um recurso e pesquise os serviços de IA do Azure. Selecione criar um plano de serviços de IA do Azure. Você será levado a uma página para criar um recurso de serviços de IA do Azure. Configure-o com as seguintes configurações:``
    ![Criar recurso](https://r2.easyimg.io/5sevtae6q/criarrecurso.png)
    ![Criar serviço cognitivo](https://r2.easyimg.io/iyluhrh5e/servicocognitivo.png)

        Assinatura: sua assinatura do Azure.
        Grupo de recursos: selecione ou crie um grupo de recursos com um nome exclusivo.
        Região: Leste dos EUA.
        Nome: Insira um nome exclusivo.
        Nível de preços: Padrão S0.
        Ao marcar esta caixa, confirmo que li e compreendi todos os termos abaixo: Selecionado.
      
     `` 1.3 Selecione Revisar + criar e depois Criar e aguarde a conclusão da implantação.``


2. ```Conecte seu recurso de serviço de IA do Azure ao Vision Studio```  

    ```2.1. Em outra guia do navegador, navegue até Vision Studio(https://portal.vision.cognitive.azure.com/gallery/featured).```  
    ```2.2 Entre com sua conta e certifique-se de usar o mesmo diretório onde você criou seu recurso de serviços de IA do Azure.```  
    ```2.3 Na página inicial do Vision Studio, selecione Visualizar todos os recursos no título Introdução ao Vision.```  

     ![Vision resourcer](https://r2.easyimg.io/3t1nuv4ai/vision-resources.png)
       
    ```2.4 Na página Selecione um recurso para trabalhar, passe o cursor do mouse sobre o recurso que você criou acima na lista e marque a caixa à esquerda do nome do recurso e selecione Selecionar como recurso padrão.```  

     ![Default Resoucer](https://r2.easyimg.io/sghy3wgp6/default-resource.png)  
    ```2.5 Feche a página de configurações selecionando o “x” no canto superior direito da tela.``` 
3. ```Gerar legendas para uma imagem```
    
Agora você está pronto para usar o Vision Studio para analisar imagens tiradas por uma câmera na loja Northwind Traders.  
Vejamos a funcionalidade de legenda de imagens do Azure AI Vision.   
As legendas das imagens estão disponíveis por meio dos recursos Legenda e Legendas densas.

 ```3.1 Em um navegador da web, navegue até Vision Studio.```  
 ```3.2 Na página inicial Introdução ao Vision, selecione a guia Análise de imagem e, em seguida, selecione o bloco Adicionar legendas às imagens.```

 ![Add-caption](https://r2.easyimg.io/blg3f0ggq/add-captions.png)  
 ```3.3 No subtítulo "try it ou", reconheça a política de uso de recursos lendo e marcando a caixa.```  
 ```3.4 Selecione https://aka.ms/mslearn-images-for-análise para baixar image-análise.zip. Abra a pasta no seu computador e localize o arquivo chamado store-camera-1.jpg; que contém a seguinte imagem:```  

 ![imagem 1](https://r2.easyimg.io/vrfvzj548/store-camera-1.jpg)  
 ```3.5 Carregue a imagem store-camera-1.jpg arrastando-a para a caixa Arrastar e soltar arquivos aqui ou navegando até ela em seu sistema de arquivos.```  
 ```3.6 Observe o texto da legenda gerado, visível no painel Atributos detectados à direita da imagem.```  

    A funcionalidade Caption fornece uma frase em inglês única e legível que descreve o conteúdo da imagem.  

```3.7 Em seguida, use a mesma imagem para realizar legendas densas. Retorne à página inicial do Vision Studio e, como fez antes, selecione a guia Análise de imagem e, em seguida, selecione o bloco Legenda densa.```  
```3.8 Passe o mouse sobre uma das legendas na lista de atributos detectados e observe o que acontece na imagem.```

![dense-screenshot](https://r2.easyimg.io/ad9o8mwfg/dense-captioning.png)
Move your mouse cursor over the other captions in the list, and notice how the bounding box shifts in the image to highlight the portion of the image used to generate the caption.

## Marcando imagens
    O próximo recurso que você experimentará é a funcionalidade Extrair Tags. Extrair tags é baseado em milhares de objetos reconhecíveis, incluindo seres vivos, cenários e ações.  

 ```4.1 Retorne à página inicial do Vision Studio e selecione o bloco Extrair tags comuns de imagens na guia Análise de imagem. ```  
 ```4.2 Em Escolha o modelo que deseja experimentar, deixe selecionado Produto pré-construído vs. modelo de lacuna. Em Escolha seu idioma, selecione Inglês ou um idioma de sua preferência.```  
```4.3 Abra a pasta que contém as imagens que você baixou e localize o arquivo chamado store-image-2.jpg, que se parece com isto:```
![store camera](https://r2.easyimg.io/ioeq79w5d/store-camera-2.jpg)  

```4.4 Carregue o arquivo store-camera-2.jpg.```  
```4.5 Revise a lista de tags extraídas da imagem e a pontuação de confiança de cada uma no painel de atributos detectados. Aqui, a pontuação de confiança é a probabilidade de o texto do atributo detectado descrever o que realmente está na imagem. Observe na lista de tags que ela inclui não apenas objetos, mas ações, como comprar, vender e ficar em pé.```

## Detecção de objetos

    Nesta tarefa, você usa o recurso de detecção de objetos da Análise de imagem. A detecção de objetos detecta e extrai caixas delimitadoras com base em milhares de objetos e seres vivos reconhecíveis.

 ```5.1 Retorne à página inicial do Vision Studio e selecione o bloco Detectar objetos comuns em imagens na guia Análise de imagem.```  
 ```5.2 Em Escolha o modelo que deseja experimentar, deixe selecionado Produto pré-construído vs. modelo de lacuna.```  
 ```5.3 Abra a pasta que contém as imagens que você baixou e localize o arquivo chamado store-camera-3.jpg, que se parece com isto:```  

 ![store-image-3](https://r2.easyimg.io/2qw51hgex/store-camera-3.jpg)  
```5.4 Carregue o arquivo store-camera-3.jpg.```  
```5.5 Na caixa Atributos detectados, observe a lista de objetos detectados e suas pontuações de confiança.```  
```5.6 Passe o cursor do mouse sobre os objetos na lista de atributos detectados para destacar a caixa delimitadora do objeto na imagem.```  
```5.7 Mova o controle deslizante Valor limite até que um valor de 70 seja exibido à direita do controle deslizante. Observe o que acontece com os objetos da lista. O controle deslizante de limite especifica que somente objetos identificados com uma pontuação de confiança ou probabilidade maior que o limite devem ser exibidos. Ícone "Verificada pela comunidade"```

## Ler texto no Vision Studio
Neste exercício, você usará o serviço Azure AI para explorar os recursos de reconhecimento óptico de caracteres do Azure AI Vision. Você usará o Vision Studio para experimentar extrair texto de imagens, sem precisar escrever nenhum código.
Um desafio comum da visão computacional é detectar e interpretar texto incorporado em uma imagem. Isso é conhecido como reconhecimento óptico de caracteres (OCR). Neste exercício, você usará um recurso de serviços de IA do Azure, que inclui serviços do Azure AI Vision. Em seguida, você usará o Vision Studio para testar o OCR com diferentes tipos de imagens.

## Extraia texto de imagens no Vision Studio  
```6.1 Em um navegador da Web, navegue até Vision Studio em https://portal.vision.cognitive.azure.com.```  
```6.2 Na página inicial Introdução ao Vision, selecione Reconhecimento óptico de caracteres e, em seguida, o bloco Extrair texto de imagens.```   
```6.3 No subtítulo Experimente, reconheça a política de uso de recursos lendo e marcando a caixa.```  
```6.4 Selecione https://aka.ms/mslearn-ocr-images para baixar ocr-images.zip. Em seguida, abra a pasta.```
```6.5 No portal, selecione Procurar um arquivo e navegue até a pasta em seu computador onde você baixou ocr-images.zip. Selecione advert.jpg e selecione Abrir.```  
```6.6 Agora revise o que é retornado:```
 
⁎ Nos atributos detectados, qualquer texto encontrado na imagem é organizado em uma estrutura hierárquica de regiões, linhas e palavras.  
⁎ Na imagem, a localização do texto é indicada por uma caixa delimitadora, conforme mostrado aqui:  
![box](https://r2.easyimg.io/od2r1l262/advert-bounding-boxes.jpg)  

```6.7 Agora você pode tentar outra imagem. Selecione Procurar um arquivo e navegue até a pasta onde você salvou os arquivos do GitHub. Selecione carta.jpg.```  
![carta](https://r2.easyimg.io/fztbm48qi/letter.jpg)  
```6.8 Veja os resultados da segunda imagem. Deve retornar o texto e as caixas delimitadoras do texto. Se você tiver tempo, tente note.jpg e recibo.jpg.```

## Detecte rostos no Vision Studio  
```7.1 Num navegador web, navegue até Vision Studio em https://portal.vision.cognitive.azure.com.```  
```7.2 Na página inicial Introdução ao Vision, selecione a guia Face e, em seguida, selecione o bloco Detectar rostos em uma imagem.```  
```7.3 No subtítulo Experimente, reconheça a política de uso de recursos lendo e marcando a caixa.```  
```7.4 Selecione cada uma das imagens de amostra e observe os dados de detecção facial retornados.```  
```7.5 Agora vamos tentar com algumas de nossas próprias imagens. Selecione https://aka.ms/mslearn-detect-faces para baixar detect-faces.zip. Em seguida, abra a pasta no seu computador.```  
```7.6 Localize o arquivo chamado store-camera-1.jpg; que contém a seguinte imagem:```  

![store-camera](https://r2.easyimg.io/44hl4wwk2/store-camera-1.jpg)  

```7.7 Faça upload de store-camera-1.jpg e revise os detalhes de detecção de rosto retornados.```  
```7.8 Localize o arquivo chamado store-camera-2.jpg; que contém a seguinte imagem:```  
![store-camera-2](https://r2.easyimg.io/qkozt8y9u/store-camera-2.jpg)  
```7.9 Faça upload de store-camera-2.jpg e revise os detalhes de detecção de rosto retornados.```  
```7.10 Localize o arquivo chamado store-camera-3.jpg; que contém a seguinte imagem:```  

![store-camera-3](https://r2.easyimg.io/nuga8eltm/store-camera-3.jpg)  

```7.11 Faça upload de store-camera-3.jpg e revise os detalhes de detecção de rosto retornados. Observe como o Azure AI Face não detectou o rosto que está obscurecido.```

Neste exercício você explorou como os serviços de IA do Azure podem detectar rostos em imagens. Se você tiver tempo, sinta-se à vontade para experimentar as imagens de exemplo ou algumas de suas próprias imagens.


## Para deletar o workspace

1. No [Azure Machine Learning Studio](https://ml.azure.com/?azure-portal=true), na página Grupos de recursos, abra o grupo de recursos especificado ao criar o seu espaço de trabalho Azure Machine Learning.

![Grupo de Recursos](https://r2.easyimg.io/2o5s4m34r/gruporecursos.png)
![Lista de grupos](https://r2.easyimg.io/ln4zmp7ai/listadegrupos.png)  

2. Clique em Excluir grupo de recursos, digite o nome do grupo de recursos para confirmar que deseja excluí-lo e selecione Excluir, a exclusão pode demorar alguns minutos.
![Excluir grupo](https://r2.easyimg.io/0emlhhnaw/excluirgrupo.png)
![Confirma exclusão](https://r2.easyimg.io/7a9u590oj/confirmaexcluir.png)



## Referências
 - [Analise de imagem visual studio](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/03-image-analysis.html)
 - [Ler texto no Vision Studio](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/05-ocr.html)
 - [Detectar rostos no Vision Studio](https://microsoftlearning.github.io/mslearn-ai-fundamentals/Instructions/Labs/04-face.html)

