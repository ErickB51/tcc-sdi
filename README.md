<h1 align="center">                            Sistema de Detecção de Incêndios Florestais (SDIF)                                                 </h1>
<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/logo-editada.png">
</p>
<h3 align="center">                            Sumário                                                                                            </h3>

<ol>
               <li>                            Descrição do projeto                                                                               </li>
               <li>                            Introdução, Motivação e Objetivo                                                                   </li>
               <li>                            Contextualização                                                                                   </li>
                   <ol>
                       <li>                    Detecção de incêndios florestais                                                                   </li>
                       <li>                    Redes neurais convolucionais                                                                       </li>
                       <li>                    Sistemas Embarcados                                                                                </li>
                       <li>                    Transmissão de dados sem fio                                                                       </li>
                       <li>                    Computação em nuvem                                                                                </li>
                   </ol>
               <li>                            Metodologias e Ferramentas                                                                         </li>
                   <ol>
                       <li>                    Metodologia para pesquisa                                                                          </li>
                       <li>                    Metodologia para seleção de componentes                                                            </li>
                       <li>                    Metodologia para testagem dos compontentes                                                         </li>
                       <li>                    Metodologia para seleção do provedor de serviçoes em nuvem                                         </li>
                       <li>                    Métricas de Avaliação para Modelos de <i> Machine Learning </i> e <i> Deep Leaning </i>            </li>
                       <li>                    Métricas de Avaliação para o Projeto                                                               </li>
                   </ol>
               <li>                            Design dos Experimentos                                                                            </li>
               <li>                            Resultados                                                                                         </li>
                   <ol>
                       <li>                    Modelos selecionados                                                                               </li>
                       <li>                    Resultado dos modelos                                                                              </li>
                       <li>                    Componentes selecionados                                                                           </li>
                       <li>                    Resultado dos testes dos componentes                                                               </li>
                       <li>                    Provedor de serviços em nuvem selecionado                                                          </li>
                       <li>                    Arquitetura do sistema e aspectos da rede                                                          </li>
                       <li>                    Protocolo selecionado                                                                              </li>
                       <li>                    Resultados da aplicação da arquitetura do sistema, rede e protocolo                                </li>                                  </ol>
               <li>                            Conclusões                                                                                         </li>
               <li>                            Em andamento e trabalhos futuros                                                                   </li>
                   <ol>
                       <li>                        <i> Deployment </i> e testes em ambientes reais                                                </li>
                       <li>                        Estudo sobre alterntaivas para alimentação do sistema                                          </li>
                   </ol>
	       <li>                            Referências                                                                                         </li>
</ol>

<h2 align="center">                            Descrição do projeto                                         </h2>
<p  align="justify" style="margin-top: 5px; "> <i>Neste projeto é apresentado o resultado da implementação de um sistema de detecção de incêndios florestais. Que apresenta o resultado dos testes de sensores e a simulação em determinados cenários dos mesmos. O sistema é composto por nós sensores, que medem a temperatura, a concentração de gases no ambiente, a localização e capturam imagem do local. Para a transmissão dos dados é utilizado um dispositivo LoRa. No experimento apresentado neste projeto, foi realizado a detecção de fogo utilizando 5 arquiteturas de rede neural diferentes: ConvNet, InceptionV3, Xception, VGG16 e MobileNet. Todas as arquiteturas utilizadas obtiveram as mesmas imagens de treinamento e validação, contendo 1216 e 304 imagens respectivamente. Para o testes dos modelos foram utilizadas dois conjuntos de dados, um contendo 380 imagens e o outro 998 imagens. Os resultados obtidos comparando as métricas utilizadas foram que o algoritmo MobileNet obteve melhores resultados em relação aos demais.</p>
<h2 align="center">                            Introdução, Motivação e Objetivo                                         </h2>
<p  align="justify" style="margin-top: 5px; "> <i> O planeta está cada vez mais quente e seco marcado pelos impactos do aquecimento global. Tais impactos são, cada vez mais, intesificados pela destruição ocasionada pelos incêndios florestais (DENNISON et al., 2014). Estes eventos causam diversos problemas, não só ambientais, mas também econômicos e representam um grande perigo para a vida. Um incêndio florestal de larga escala pode avançar por dias ou até mesmo semanas, destruindo tudo que encontra no seu caminho. Para evitar que focos de incêndios se tornem catastróficos, a velocidade de detecção e reação na fase inicial é crucial. Ao se detectar precocemente um incêndio, é possível evitar a destruição parcial ou total do ecossistema local e, inclusive, a eliminação de exemplares da fauna, o que poderia vir a trazer grandes prejuízos de modo geral para a biodiversidade. Isto sem mencionar os outros problemas ambientais como, por exemplo, a emissão de grandes níveis de dióxido de carbono (MATIAS, 2020).
  
  O objetivo deste trabalho é desenvolver um sistema de monitoramento de incêndios florestais. O sistema, que é composto por sensores de temperatura, sensores de gás,  câmeras e dispositivos de comunicação, irá realizar a predição de se há fogo ou não na área, isto é, através de técnicas de Internet of Things (IoT) e de Inteligência Artificial. Por meio destas técnicas é realizado uma análise por meio de algoritmos de machine learning e deep learning, e, para isso, utilizamos bases de imagens de incêndios em ambientes florestais para o treinamento e teste dos modelos. Diante disto, foram realizados testes de acurácia e  comparações entre estes algoritmos e análise de artigos cientificos relacionados.</p>
  
<h2 align="center">                            Contextualização                                         </h2>

<h3 align="center">                            Detecção de incêndios florestais                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i>Um dos grandes problemas encarado hoje é o considerável aumento do número de incêndios e a extensão das áreas queimadas, além de causar um grande dano aos ecossistemas florestais, causando grandes impactos diretos e indiretos ao meio ambiente (BATISTA, 2004).
	Para se tornar eficaz a detecção de incêndios precisa ser rápida e eficiente para viabilizar o combate ao fogo, como reduzir os custos nas operações, é importante ter a informação precisa sobre a localização e extensão da área queimada. Os métodos de detecção de incêndios florestais são peças fundamentais para o planejamento do controle, como para dimensionar os efeitos do fogo sobre o ambiente.
	Existem muitas formas de detecção que podem ser utilizadas, o que vai influenciar na escolha da estratégia será a extensão da área a ser monitorada e as características do ambiente, existem estratégias de detecção como vigilância terrestre com postos e torres de observação, patrulhamento aéreo, monitoramento com imagens de satélites e soluções com visão computacional.</p>
  
  <h3 align="center">                            Redes neurais convolucionais                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i>Uma rede neural convolucional possui múltiplas partes com funções diferentes, uma camada de convolução é composta por diversos neurônios, sendo que cada um é responsável por aplicar um filtro em um pedaço específico da imagem. As Redes Neurais Convolucionais possuem um alto índice de acurácia para o reconhecimento de imagem. A primeira aplicação efetiva de uma convolutional neural network (CNN) foi desenvolvida em 1998 por Yann LeCun. As CNNs ficaram cada vez mais profundas e complexas com o passar dos anos (Alves, 2018).
	Para entender como uma Rede Convolucional funciona é importante compreender sua inspiração biológica. Em 1962 Hubel e Wiesel fizeram um experimento mostrando que alguns neurônios são ativados juntos quando expostos a algumas linhas ou curvas, produzindo assim o reconhecimento visual (VARGAS at al, 2016).
	Esse estudo é a base da ideia principal de uma rede convolucional, filtrar linhas, curvas e bordas e em cada camada acrescida transformar essa filtragem em uma imagem mais complexa. Para melhor entendimento vamos explicar o processo e suas etapas:

•	Entradas: As entradas são usualmente matrizes tridimensionais com altura, largura e profundidade, determinada pela quantidade de canais de cores.
  
•	Convoluções: As convoluções funcionam como filtros que enxergam pequenos quadrados e percorrem toda a imagem captando traços marcantes, a profundidade da saída de uma convolução é igual a quantidade de filtros aplicados. Quanto mais profundas são as camadas das convoluções, mais detalhados são os traços identificados.
  
•	Função de ativação: As funções de ativação são responsáveis por aplicar transformações nos dados recebidos, o objetivo é trazer a não-linearidade ao sistema, a rede assim é capaz de aprender qualquer tipo de funcionalidade.
  
•	Pooling (Camada de Agrupamento): A função dessa camada é reduzir a dimensionalidade dos dados na rede, essa redução é importante por questão de agilidade no treinamento, o objetivo é simplificar a informação da saída da camada anterior.
  
De maneira geral podemos dizer que as CNNs são um tipo específico de rede neural artificial bastante eficaz para classificação de imagens pois são capazes de levar em consideração a coerência espacial da imagem, ou seja, que pixels próximos uns dos outros estão frequentemente relacionados.</p>
<h3 align="center">                            Sistemas Embarcados                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i>Um sistema embarcado pode ser definido como um dispositivo com um único propósito de aplicação, diferente de um computador convencional, que pode ser chamado de sistema computacional de propósito generalizado. São sistemas microprocessados e normalmente fazem parte de outro sistema maior, agindo como controlador de eventos com sensores, atuadores e interfaces para o acesso de seus usuários. Exemplos de equipamentos onde se utilizam sistemas embarcados: veículos, robótica, casas inteligentes, sistemas de aeronaves, equipamentos agrícolas entre outros.</p>
  
<h3 align="center">                            Transmissão de dados sem fio                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i>No desenvolvimento de um projeto IoT, a transmissão de dados e informações é recorrente, devemos considerar que na maior parte das vezes os sistemas estão embarcados e o racionamento de energia é crucial para o funcionamento do dispositivo por semanas e até anos sem a necessidade recarga ou manutenção de baterias.   Considerando isso a utilização das low-power wide-area network (LPWAN) ganhou uma grande popularidade na área, devido a permissão de comunicação sem fio de longas distâncias por um baixo custo de energia. O objetivo deste trabalho é implementar um sistema de monitoramento em real em áreas de florestas para a prevenção de incêndios, utilizaremos uma adaptação do sistema long range (LoRa) para o envio de informações de sensores para um gateway. Nosso gateway, irá alimentar um banco de dados que será consumido por um aplicativo para exibição em tempo real de nossas áreas de monitoramento.</p>

<h3 align="center">                            Computação em nuvem                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
  
<h2 align="center">                            Metodologias e Ferramentas                                         </h2>

  <h3 align="center">                            Metodologia para pesquisa                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
    <h3 align="center">                            Metodologia para seleção de componentes                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
      <h3 align="center">                            Metodologia para testagem dos compontentes                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
      <h3 align="center">                            Metodologia para seleção do provedor de serviçoes em nuvem                                          </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
      <h3 align="center">                            Métricas de Avaliação para Modelos de <i> Machine Learning </i> e <i> Deep Leaning                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i>Para a avaliação do desempenho dos classificadores de detecção de incêndios florestais, foram utilizadas as métricas de Acurácia (AC) proporção dos classificados corretamente para todas as classes, Recall (RC) proporção dos incêndios encontrados no algoritmo, Precisão (PR) observações classificadas como fogo que eram na verdade fogo, F1-score (F1) média harmônica do recall e da precisão (RODRIGUES, 2019). As equações são representadas na figura a seguir:</p>
	
<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/metricas.png">
</p>	
	
<p  align="justify" style="margin-top: 5px; "> <i>Os valores de TP e FP referem-se se a casos verdadeiros-positivos (o classificador detectou corretamente o incêndio) e casos falsos-positivos (o classificador detectou um incêndio quando não estava ocorrendo), respectivamente. Os valores TN e FN referem-se a casos verdadeiros-negativos (o classificador detectou corretamente a ausência de incêndio) e casos falsos-negativos (o classificador não detectou um incêndio quando na verdade ocorria um incêndio) respectivamente. Na figura abaixo é mostrado a matriz de confusão.</p>

<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/matrizconfusao.png">
</p>	
	
<p  align="justify" style="margin-top: 5px; "> <i>Também foi utilizado a curva de Receiver Operating Characteristic (ROC). esta curva é uma das formas de analisar classificadores em problemas binários, o algoritmo é considerado perfeito quando ele possui maior protuberância em direção ao canto superior esquerdo que é mostrado na figura abaixo.</p>

<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/roc.png">
</p>

<h3 align="center">                            Métricas de Avaliação para o Projeto                                          </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
 
<h2 align="center">                            Design dos Experimentos                                         </h2>
        
<h2 align="center">                            Resultados                                         </h2>

<h3 align="center">                            Modelos selecionados                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i>• ConvNet. Proposto por Yann LeCun et al. (1998), são um tipo específico de rede neural artificial bastante eficaz para classificação de imagens pois são capazes de levar em consideração a coerência espacial da imagem, ou seja, que pixels próximos uns dos outros estão frequentemente relacionados</p>
	
<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/convnet.png"></p>

<p  align="justify" style="margin-top: 5px; "> <i>• InceptionV3. Proposto por Szegedy et al. (2015), é uma arquitetura de CNN que busca a resolução de diversos problemas de reconhecimento de imagens em grande escala e também podem ser utilizados em problemas de transfer learning (descrito anteriormente). O seu diferencial é a presença de módulos extratores de características convolucionais. Estes módulos tem como funcionalidade aprender com  menos parâmetros que contém uma maior gama de informação.</p>
	
<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/Inceptionv3.png"></p>

<p  align="justify" style="margin-top: 5px; "> <i>• Xception. Proposto por Chollet et al.(2016), é uma arquitetura de CNN similar ao Inception descrito anteriormente e, tem como diferencial que os módulos de iniciação foram substituidos por convoluções separáveis em profundidade. A Xception possui a mesma quantidade de parâmetros que o InceptionV3 com o total de 36 camadas convolucionais. Assim, tendo um uso mais eficiente dos parâmetros.</p>
	
<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/Xception.png"></p>

	
<p  align="justify" style="margin-top: 5px; "> <i>• VGG16. Proposto por K. Simonyan et al. (2014), é uma arquitetura de CNN que apresenta uma menor quantidade de camadas e uma distribuição de pesos que é capaz de extrair diversas características. Também são utilizadas com técnicas de transfer learning.</p>
	
<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/VGG16.png"></p>

	
<p  align="justify" style="margin-top: 5px; "> <i>• MobileNet. Proposto por Howard et al. (2017), é uma arquitetura de CNN que foram criados para a executação de tarefas de visão computacional em dispositivos móveis e sistemas embarcados. Eles são baseados em operações de convolução separáveis em profundidade, que diminui o ônus das operações nas primeiras camadas.</p>
	
<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/MobileNet.png"></p>
   
<h3 align="center">                            Resultado dos modelos                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i>- Performance no treinamento e validação: 
O conjunto de dados de treinamento está balanceado e consiste de 1520 imagens no total, onde 760 imagens pertecem a cada classe com resolução espacial de 250 x 250. Este conjunto de dados foi dividido em 80:20:20 (1216 imagens ficaram para o treinamento, 304 para validação e 380 para o teste do modelo). Os resultados da avaliação se encontram na tabela abaixo.</p>

<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/results_train.PNG"></p>

<p  align="justify" style="margin-top: 5px; "> <i>- Performance no Testset1: 
O conjunto de dados Testset1 está balanceado e consiste de 380 imagens no total, onde 190 imagens pertecem a cada classe com resolução espacial de 250 x 250. Este conjunto de dados foi dividido em 80:20 como descrito anteriormente e, por esta razão possuí menos imagens para teste. Os resultados da avaliação se encontram na tabela abaixo.</p>


<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/results_test1.PNG"></p>

<p  align="justify" style="margin-top: 5px; "> <i>- Performance no Testset2: 
O conjunto de dados Testset2 está desbalanceado e consiste de 998 imagens no total, onde 755 imagens pertecem a classe fogo e 243 a classe não fogo e as imagens possuem diferentes resoluções. Portanto, este conjunto de dados é mais adequado para realizar a avaliação do desempenho do modelo do que para treinâ-lo por estar desbalanceado. Os resultados da avaliação se encontram na tabela abaixo.</p>

<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/results_test2.PNG"></p>
</p>
      <h3 align="center">                            Componentes selecionados                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
      <h3 align="center">                            Resultado dos testes dos componentes                                          </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
      <h3 align="center">                            Provedor de serviços em nuvem selecionado                                         </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
      <h3 align="center">                            Arquitetura do sistema e aspectos da rede                                          </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
      <h3 align="center">                            Protocolo selecionado                                          </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
      <h3 align="center">                            Resultados da aplicação da arquitetura do sistema, rede e protocolo                                          </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>

<h2 align="center">                            Conclusões                                         </h2>
<h2 align="center">                            Em andamento e trabalhos futuros                                         </h2>
      <h3 align="center">                            <i> Deployment </i> e testes em ambientes reais                                          </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>
      <h3 align="center">                            Estudo sobre alterntaivas para alimentação do sistema                                          </h3>
<p  align="justify" style="margin-top: 5px; "> <i> </p>

<h2 align="center">                            Referências                                         </h2>

<p  align="justify" style="margin-top: 5px; "> <i>Dennison et al. (2014), "Wildfires and Climate Change", https://www.c2es.org/content/wildfires-and-climate-change/, Abril

A. Matias (2020), "Queimadas na Amazônia", https://mundoeducacao.uol.com.br/geografia/queimadas-na-amazonia.htm, Abril

C. Altman, (2020) "Inteligência Artificial está em alta em 2020", https://www.em.com.br/app/noticia/ciencia/2020/02/06/interna_ciencia,1119794/inteligencia-artificial-esta-em-alta-em-2020.shtml, Abril

Lin, Cheng-Jian, and Shiou-Yun Jeng (2020). “Optimization of Deep Learning Network Parameters Using Uniform Experimental Design for Breast Cancer Histopathological Image Classification.” In Diagnostics (Basel, Switzerland).

Stefanini (2019), "Inteligência Artificial nos setores da economia: entenda as funcionalidades", https://stefanini.com/pt-br/trends/artigos/inteligencia-artificial-nos-setores-da-economia, Abril

Cavanagh, (2019), "Artificial Intelligence Is Attracting Investors, Inventors, and Academic Researchers Worldwide", https://marketbrief.edweek.org/marketplace-k-12/artificial-intelligence-attracting-investors-inventors-academic-researchers-worldwide/, Abril

Korolov, (2018), "O maior fator de risco da Inteligência Artificial? Dados errados", https://cio.com.br/tendencias/o-maior-fator-de-risco-da-inteligencia-artificial-dados-errados/, Abril

R.Metz, (2020), "How AI is helping spot wildfires faster", https://edition.cnn.com/2019/12/05/tech/ai-wildfires/index.html, Abril

Khan, Ali; Hassan, Bilal (2020), “Dataset for Forest Fire Detection”, https://data.mendeley.com/datasets/gjmr63rz2r/1, Maio
Rodrigues, (2019), "Métricas de Avaliação: acurácia, precisão, recall… quais as diferenças?" https://vitorborbarodrigues.medium.com/m%C3%A9tricas-de-avalia%C3%A7%C3%A3o-acur%C3%A1cia-precis%C3%A3o-recall-quais-as-diferen%C3%A7as-c8f05e0a513c, Maio
Szegedy, C., Vanhoucke, V., Ioffe,S., Shlens,J.,&Wojna,Z.(2016) “Rethinking the inception architecture for computer vision” In Proceedings of the IEEE conference on computer vision and pattern recognition.
François  Chollet (2016), “Xception:  Deep  learning  with  depthwise  separable convolutions”, In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR) pages 1251-1258. Publishing Press.
Simonyan, K. and Zisserman, A. (2014). “Very deep convolutional networks for large-scale image recognition”, In Proceedings of the IEEE Conference on Computer Vision and Pattern Recognition (CVPR) pages 1409-1556. Publishing Press.
N. S. Sanjay and A. Ahmadinia (2019), “MobileNet-Tiny: A Deep Neural Network-Based Real-Time Object Detection for Rasberry Pi”, In 18th IEEE International Conference On Machine Learning And Applications (ICMLA) pages 647-652. Publishing Press.

Brandizzi,  (2020), “Visão computacional: O que é? Como funciona?”, https://www.serpro.gov.br/menu/noticias/noticias-2020/o-que-eh-visao-computacional, Junho

Alves, (2018), “Entendendo Redes Convolucionais (CNNs)”, https://medium.com/neuronio-br/entendendo-redes-convolucionais-cnns-d10359f21184, Junho

Aliger, (2019), “As Redes Neurais Convolucionais no Deep Learning”, https://www.aliger.com.br/blog/as-redes-neuronais-convolutivas-no-deep-learning/, Abril

Noleto, (2020), “Sistemas embarcados: o que são, características e exemplos de aplicação!”, https://blog.betrybe.com/tecnologia/sistemas-embarcados/, Abril

Backes, Ricardo (2019). “Introdução a Visão Computacional usando MATLAB” In google scholar.

Vargas, Carvalho, Vasconcelos. “Um estudo sobre Redes Neurais Convolucionais e sua aplicacão em detecção de pedestres”In gibis unifesp.

Batista, (2004), “Detecção de Incêndios Florestais por Satélites” In queimadas Dgi.

Devecchi, (2015). “Um Sistema de Ponto Eletrônico Digital: projeto e implementação de hardware e software (Atividade Prática de Desenvolvimento de Software)” In researchgate.

Tonghao Chen, (2019). “Implementing Efficient and Multi-Hop Image Acquisition In Remote Monitoring IoT systems using LoRa Technology” In harvest.

Ramos, (2019). “Uso de uma rede LoRaWAN em um sistema de gerenciamento de lixo”In Cin-UFPE.


Therriault, (2020), “Wildfire Smoke A guide for public health Officials”, https://depts.washington.edu/wildfire/resources/pubhealthguide.pdf, Junho
</p>
