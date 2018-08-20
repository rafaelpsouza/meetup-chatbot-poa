# Exemplo para o Meetup Chatbot POA

## Instalação

* spaCy + sklearn
* Tensorflow

## Configuração com Tensorflow

* word vectors extraídos do próprio dataset
* suporte a múltiplas intenções por sentença

## Treino

* Markdown e Json
* Ferramentas gráficas para auxiliar
* Sinônimos

``` python -m rasa_nlu.train --config configs/tensorflow.yml --data treino.md --path projects --project restaurantes ```

## Servidor HTTP

``` python -m rasa_nlu.server --path projects ```

## Exemplos

``` curl 'localhost:5000/parse?q=oi&project=restaurantes' | jq ```

``` curl -G "localhost:5000/parse?project=restaurantes" --data-urlencode "q=quero fazer uma reserva" | jq ```

``` curl -G "localhost:5000/parse?project=restaurantes" --data-urlencode "q=estou procurando um restaurante de comida arabe na cidade baixa" | jq ```

## Exemplos com sinônimos

``` curl -G "localhost:5000/parse?project=restaurantes" --data-urlencode "q=estou procurando um restaurante de comida arabe no centro da cidade" | jq ```

``` python -m rasa_nlu.train --config configs/tensorflow_synonyms.yml --data treino.md --path projects --project restaurantes ```

``` curl -G "localhost:5000/parse?project=restaurantes" --data-urlencode "q=estou procurando um restaurante de comida arabe no centro da cidade" | jq ```

## Duckling 

``` docker run -p 8000:8000 rasa/duckling ```

``` curl -G "localhost:5000/parse?project=restaurantes" --data-urlencode "q=gostaria de fazer uma reserva para duas pessoas hoje" | jq ```