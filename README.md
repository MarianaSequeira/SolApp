# SolApp_ICM2018

Lab-Project ICM 2018, Universidade de Aveiro.

#### Funcionalidades Implementadas:

1) Aceder à meteorologia de um qualquer distrito de Portugal, bastando para tal selecionar um de entre a lista de Distritos disponibilizada.
2) Visualizar a localização do distrito a selecionar, podendo, de seguida, consultar a meteorologia desse mesmo distrito.

3) Relativamente aos dados de meteorologia apresentados: são apresentados os dados do dia atual ("tipo de tempo", temperatura mínima e máxima, direção e força do vento e humidade), os dados dos próximos quatro dias ("tipo de tempo") e, por fim, um gráfico que têm como propósito consultar a variação da temperatura ao longo dos cinco dias em questão (nesse gráfico é possível ver a temperatura máxima e mínima de todos os dias).

#### Descrição do Fluxo de Interação com a Aplicação: 

Inicialmente, o utilizador, é direcionado para uma página na qual poderá consultar a informação relativa à meteorologia de um distrito. Caso o utilizador pretenda consultar a meteorologia num outro distrito poderá fazê-lo clicando no icon presente no canto superior direito. É então apresentada uma lista de distritos, sendo que o utilizador poderá optar por visualizar diretamente a informação de meteorologia desse distrito (clicando do "cardview" que lhe está associado), ou pode optar por visualizar primeiro a localização desse distrito (clicando no icon presente no "cardview" que lhe está associado).  Neste último caso, o utilizador é direcionado para um Mapa, que lhe apresenta não só a localização do distrito como também o tipo de tempo que se encontra neste. Apartir deste ponto, o utilizador poderá retroceder para a página anterior (listagem de distritos) ou poderá clicar na localização, sendo posteriormente direcionado para uma págima onde é apresentada toda a informação. 

<p align="center">
  <img width="550" alt="fluxo" src="https://user-images.githubusercontent.com/44784150/50700635-fb35be00-1042-11e9-9cb1-15727c91072e.png">
</p>

#### Arquitetura Implementada:

Para implementar as funcionalidades anteriormente enumeradas, foi necessário recorrer à API disponibilicaza pelo IPMA, usando os seguintes serviços:
1) "Previsão Meteorológica Diária até 5 dias agregada por Local"
2) "Lista de identificadores para as capitais distrito e ilhas"
3) "Lista de identificadores do tempo significativo"
4) "Lista de classes relativa à intensidade vento"

Os dados obtidos são mapeados para diferentes entidades, para assim poderem ser corretamente armazenados na base de dados, de modo a preencher os requesitos necessários à implementação de uma aplicação com base no ROOM. 

As entidades criadas foram as seguintes: 
* "WeatherForecast"     (entidade responsável por guardar os dados recebidos do pedido ao serviço 1)
* "WeatherForecastData" (entidade auxiliar para armazenar a lista "data" recebida pelo pedido ao serviço 1)
* "DistrictID"          (entidade responsável por guardar os dados recebidos do pedido ao serviço 2)
* "DistrictIDData"      (entidade auxiliar para armazenar a lista "data" recebida pelo pedido ao serviço 2)
* "WeatherID"           (entidade responsável por guardar os dados recebidos do pedido ao serviço 3)
* "WeatherIDData"       (entidade auxiliar para armazenar a lista "data" recebida pelo pedido ao serviço 3)
* "WindSpeed"           (entidade responsável por guardar os dados recebidos do pedido ao serviço 4)
* "WindSpeedData"       (entidade auxiliar para armazenar a lista "data" recebida pelo pedido ao serviço 4)

Os dados recebidos foram guardados nos respetivos repositórios: "WeatherForecastRepository", "DistrictIDRepository", "WeatherIDRepository", "WindSpeedRepository".
Como seria de esperar, tendo em conta a arquitetura do projeto, cada uma das entidades principais tem associado um view model, sendo que as mesmas são criadas pelo "FactoryViewModel". 

#### Limitações: 
Deveria haver a possibilidade de apresentar no mapa a meteorologia de todos os distritos, mesmo sendo essa uma funcionalidade não implementada na maior parte das aplicações do género. 
