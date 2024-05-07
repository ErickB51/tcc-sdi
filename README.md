<h1 align="center">                            Sistema de Detecção de Incêndios Florestais (SDIF)                                                 </h1>
<p align="center">
  <img width="300px" heigth="300px" src="https://github.com/ErickB51/tcc-sdi/blob/main/Imagens/logo-editada-transparente_auto_4x.png">
</p>
<h3 align="center">                            Sumário                                                                                            </h3>

<ol>
               <li>                            Notas de atualização                                                                               </li>
               <li>                            Descrição do projeto                                                                               </li>
               <li>                            Introdução, motivação e objetivos                                                                  </li>
               <li>                            Contextualização                                                                                   </li>
                   <ol>
                       <li>                    Detecção de incêndios florestais                                                                   </li>
                       <li>                    Redes neurais convolucionais                                                                       </li>
                       <li>                    Sistemas Embarcados                                                                                </li>
                       <li>                    Transmissão de dados sem fio                                                                       </li>
                       <li>                    Computação em nuvem                                                                                </li>
                   </ol>
               <li>                            Metodologias e ferramentas                                                                         </li>
                   <ol>
                       <li>                    Metodologia para pesquisa                                                                          </li>
		       <ol>
		           <li>                Abordagem científica e estrutura da pesquisa                                                       </li>
		       </ol>
                       <li>                    Critérios para seleção de componentes                                                              </li>
		       <ol>
		           <li>                Protocolo de seleção de componentes                                                                </li>
		       </ol>
                       <li>                    Metodologia para testagem dos compontentes                                                         </li>
		       <ol>
		           <li>                Metodologia de testes do SDIF                                                                      </li>
		           <li>                Protocolos de teste                                                                                </li>
		       </ol>
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
                       <li>                        Estudo sobre alternativas para alimentação do sistema                                          </li>
                   </ol>
	       <li>                            Referências                                                                                         </li>
</ol>

<h2 align="center" style="font-style: italic">                            Notas de atualização              </h2>

<ol>
               <li>                            Introdução da câmera Arducam 3MP                                                                    </li>
               <ul>
		       <li><b>Detalhes:</b> Substituição da câmera anterior por uma Arducam 3MP para melhorar a resolução das imagens capturadas. Esta câmera oferece uma qualidade de imagem superior, o que é crucial para a análise de visão computacional e a detecção precisa de incêndios.</li>
		       <li><b>Impacto:</b> Aumento significativo na clareza e detalhes visuais das imagens, permitindo uma identificação mais precisa de sinais de fogo e fumaça através dos algoritmos de IA.</li>
	       </ul>
               <li>                            Adoção de módulos de comunicação WiFi                                                               </li>
               <ul>
		       <li><b>Detalhes:</b>  Implementação de módulos WiFi para substituir os anteriores módulos de transmissão de dados de menor capacidade. Os módulos WiFi foram escolhidos para garantir uma transmissão de dados mais rápida e confiável, especialmente importantes para o envio de imagens de maior resolução para análise em nuvem.</li>
		       <li><b>Impacto:</b> Melhoria na velocidade e confiabilidade da transmissão de dados, reduzindo significativamente a latência na comunicação entre os dispositivos de campo e o servidor de nuvem.</li>
	       </ul>
               <li>                            Observações                                                                                         </li>
               <p>As modificações realizadas foram fortemente induzidas pelas dificuldades de transmissão de dados via LoRa, mesmo com a devida implementação dos protocolos de transmissão de imagens (MPLR). O processo de compressão de imagens além de oferecer desgaste, em termos de recursos computacionais, principalmente considerando o contexto de implementação, reduz a qualidade das imagens substancialmente. </p>
</ol>

<h2 align="center">                            Descrição do projeto                                         </h2>

<p  align="justify" style="margin-top: 5px; ">Este projeto refere-se a um sistema de detecção de incêndios florestais que abrange diferentes conceitos de diferentes áreas da ciência da computação, sendo estas áreas: inteligência artificial, visão computacional, sistemas embarcados e computação em nuvem. O projeto pode ser dividido em três etapas fundamentais, sendo elas: etapa de coleta de dados, etapa de tranmissão de dados e etapa de processamento de dados. A primeira etapa envolve o uso de sistemas embarcados e sensores para coletar dados do ambiente, os dispositivos que fazem parte desta etapa são chamados de nós sensores ou dispositivos finais. A segunda etapa é caracterizada pela utilização de módulos tranmissores-receptores acoplados nos dispositivos finais e nos <i> gateways </i> (dispositivos que interceptam os dados e retransmistem estes para o provedor de serviços de computação em nuvem). A terceira etapa engloba o uso de um serviço de banco de dados em nuvem, um serviço de armazenamento de dados em nuvem, modelos de inteligência artificial pré-treinados e um software para exibição dos dados. Neste documento serão exibidos todos os aspectos introdutórios, de contextualização, metodólogicos, bem como as ferramentas e os resultados do projeto.</p>

<h2 align="center">                            Introdução, motivação e objetivos                                        </h2>

<p  align="justify" style="margin-top: 5px; ">O planeta está cada vez mais quente, seco e marcado pelos impactos ambientais negativos do aquecimento global. Tais impactos são, progressivamente, intesificados pela destruição ocasionada pelos incêndios florestais (DENNISON et al., 2014). Estes incêndios, além dos impactos ambientais negativos, promovem problemas de ordem socioeconômica e oferecem grande risco a vida das regiões afetadas e circudantes ao incêndio. Um incêndio florestal de larga escala pode avançar por dias ou até mesmo semanas, destruindo tudo que encontra no seu caminho. Para evitar que focos de incêndios se tornem catastróficos, a velocidade de detecção e reação na fase inicial é crucial. Ao se detectar precocemente um incêndio, é possível evitar a destruição parcial ou total do ecossistema local e, inclusive, a eliminação de exemplares da fauna, o que poderia vir a trazer grandes prejuízos de modo geral para a biodiversidade (MATIAS, 2020).</p>
<p align="justify">&emsp;Um dos grandes motivos que serviram de base para o desenvolvimento do projeto foi o crescente aumento do número de incêndios nos diversos biomas do Brasil. O objetivo deste projeto é desenvolver um sistema de detecção de incêndios florestais. O sistema, que é composto por sensores de temperatura, sensores de gás, câmeras e módulos de comunicação por radiofrequência, irá realizar a predição da existência de fogo em uma determinada área, isto é, através de técnicas de <i> Internet of Things </i> (IoT) e de Inteligência Artificial (IA). A idéia principal é gerar, a partir dos dados coletados, saídas que evidenciam a existência do incêndio, isto é, por meio de algoritmos de <i> machine learning </i> e <i> deep learning </i> pré-treinados á partir de bases de imagens de incêndios em florestas.</p>

<h2 align="center">                            Contextualização                                         </h2>

<h3 align="center">                            Detecção de incêndios florestais                                         </h3>
<p  align="justify" style="margin-top: 5px; ">Um grande problema a ser encarado atualmente é o aumento considerável do número de incêndios florestais, bem como da extensão das respectivas áreas queimadas. Este problema, como já exposto anteriormente na seção de introdução, motivação e objetivo, impacta, direta e indiretamente, de forma negativa, em diferentes esferas – socioambiental, por exemplo (BATISTA, 2004). Para que o processo de combate aos incêndios florestais seja realizado de maneira eficiente e para que, consequentemente, os custos operacionais sejam reduzidos, é de vital importância que existam meios de obtenção de informações, identificação e detecção precípite dos incêndios florestais. Para o desenvolvimento de métodos e estratégias de obtenção de informações acerca de incêndios florestais devem ser considerados diversos fatores como, por exemplo: a extensão da área que será monitorada, as características do ambiente, as limitações que impeçam certos tipos de métodos de vigilância e que favoreçam outros tipos.</p>
<p align="justify">&emsp;Atualmente, no contexto brasileiro de tecnologias voltadas a prevenção e combate de incêndios florestais, existem diversos desafios. Os principais métodos de percepção destes eventos, isto é, voltados a grandes áreas, são, geralmente, métodos que envolvem técnicas de sensoriamento remoto por satélite. Assim posto, um dos principais desafios que podem ser observados é a dificuldade de detecção quando existem interferências, sejam elas de caráter eletromagnético ou de caráter geoespacial – como no caso da presença de copas de árvores muito volumosas, o que dificulta na visualização de pequenos focos de incêndio.</p>
<p align="justify">&emsp;Segundo o site do órgão de Redução de Emissões por Desmatamento e Degradação florestal (REDD+), os sistemas de monitoramento florestal desenvolvidos pelo governo federal são, em sua maioria, como dito anteriormente, baseados em sensoriamento remoto por satélite. Ainda, de acordo com os artigos consultados, o principal desenvolvedor de sistemas de monitoramento utilizados é o Instituto Nacional de Pesquisas Espaciais (INPE) que, através de parcerias mantidas com o Ministério do Meio Ambiente (MMA), com o Instituto Brasileiro do Meio Ambiente e dos Recursos Naturais Renováveis (IBAMA), com a Empresa Brasileira de Pequisa Agropecuária (EMBRAPA) – vinculada ao Ministério da Agricultura, Pecuária e Abastecimento (MAPA) – e com as Universidades Públicas, desenvolve tais projetos.</p>
<p align="justify">&emsp;Um dos principais projetos citados voltado ao monitoramento e detecção de incêndios florestais é o Programa de Monitoramento de Queimadas e Incêndios. Tal programa é mantido pelo INPE e desempenha função vital na obtenção e disponibilização de dados diários sobre focos de incêndio. Segundo informações obtidas pelo site do IBAMA e do programa, há diversos desafios que impedem que determinadas queimadas sejam detectadas, sendo eles: frentes de fogo com menos de trinta metros, fogo apenas no chão de uma floresta densa (sem afetar a copa das árvores), nuvens (exceto as de fumaça) cobrindo a região, queimadas encobertas por montanhas e imprecisão na localização do foco (podendo chegar a seis quilômetros).</p>
<p align="justify">&emsp;É importante dizer que são diversos os programas desenvolvidos com o intuito de mitigar o problema mas que os desafios, principalmente dos projetos que utilizam monitoramento por satélite, são os mesmos.</p>
<p align="center"><img src="https://upload.wikimedia.org/wikipedia/commons/thumb/6/6a/JPSS-1.jpg/1024px-JPSS-1.jpg"></p>
<p align="center"> Figura 1. Representação ilustrativa do satélite NOAA-20.</p>
  
<h3 align="center">                            Redes neurais convolucionais                                         </h3>
<p  align="justify" style="margin-top: 5px; ">Uma rede neural convolucional pode ser definida como um tipo específico de rede neural artificial composta por múltiplas estruturas que desempenham diferentes funções. Nesse sentido, tais estruturas costumam ser chamadas de camadas de convolução (conjuntos de neurônios cujo objetivo é realizar o processamento da imagem, isto é, através da aplicação de técnicas de filtragem para linhas, curvas e bordas). Esta classe de rede neural é fortemente baseada em um estudo proposto em 1962 por Hubel e Wiesel. O estudo realizado forneceu base para a compreensão biológica do funcionamento do processo de reconhecimento visual – o experimento relatado nesse estudo envolveu a observação de alguns neurônios durante o ato de exposição de um indivíduo a algumas linhas e curvas (VARGAS et al., 2016).</p>
<p align="justify">&emsp;A partir da primeira aplicação efetiva de uma rede neural convolucional, que foi realizada em 1998 por Yann LeCun, ocorreram avanços significativos na profundidade, e consequentemente, na complexidade destas (ALVES, 2018). Em geral, uma rede neural convolucional possui quatro tipos de estruturas, sendo elas: entradas, camadas de convolução, camadas de agrupamento e funções de ativação.</p>
<p align="center"><img src="https://www.researchgate.net/profile/Maurice-Velte/publication/281289234/figure/fig5/AS:648202571223049@1531554944948/Architecture-of-LeCun-et-al-1998s-LeNet-5-convolutional-neural-network-for-digits.png"></p>
<p align="center"> Figura 2. Arquitetura de uma rede neural convolucional voltada ao reconhecimento de dígitos projetada por LeCun, Bottou, Bengio e Haffner (LeNet-5).</p>
<p align="justify">&emsp;As entradas podem ser descritas como estruturas de dados primitivas, geralmente matrizes, que são utilizadas para armazenar as características da imagem (alturas, largura e profundidade – variando de imagem para imagem por consequência da quantidade de canais de cores).</p>
<p align="justify">&emsp;As convoluções, outro nome para as camadas de convolução, são estruturas que agem como filtros, ressaltando detalhes ou traços marcantes – é importante ressaltar que a profundidade de saída deste tipo de camada é dado pela quantidade de filtros aplicados.</p>
<p align="justify">&emsp;As funções de ativação são estruturas responsáveis pela aplicação de transformações nos dados passados como entrada, nesse caso, o objetivo é trazer a não-linearidade ao sistema, para que dessa forma, a rede possa desempenhar qualquer tipo de funcionalidade (dentro do escopo proposto).</p>
<p align="justify">&emsp;As camadas de agrupamento são estruturas responsáveis pela redução da dimensionalidade dos dados da rede – essa redução, além de trazer agilidade para o treinamento da rede, é capaz de simplificar a informação de saída da camada anterior.</p>
<p align="justify">&emsp;Em virtude dos fatos apresentados acima, as redes neurais convolucionais são e se tornaram mecanismos de grande eficiência quando o assunto é classificação de imagens. Elas são capazes de considerar detalhes de grande importância para o processo de reconhecimento visual como, por exemplo, a coerência espacial da imagem (fator de proximidade dos pixeis e sua relação com o significado da imagem).</p>

<h3 align="center">                            Sistemas embarcados                                         </h3>
<p  align="justify" style="margin-top: 5px; ">Os sistemas embarcados podem ser definidos como dispositivos de propósito único que, ao contrário dos sistemas convencionais (de propósito geral), possuem estruturas de hardware suficientes para a função desempenhada e, consequentemente, para o software executado. Em geral, estes sistemas possuem um microprocessador ou microcontrolador e fazem parte de um sistema maior desempenhando funções como, por exemplo, controle de eventos – nesse sentido, é comum observar dentro deste contexto a utilização de sensores, atuadores ou interfaces de acesso. Este tipo de sistema é frequentemente encontrado em diversas áreas como, por exemplo: área automobilística, área aeronáutica, área robótica, área doméstica, área agrícola e entre outras áreas.</p>
  
<h3 align="center">                            Transmissão de dados sem fio                                         </h3>
<p  align="justify" style="margin-top: 5px; ">No desenvolvimento de um projeto de Internet das Coisas, a transmissão de dados e informações é um processo recorrente e, considerando que, na maior parte do tempo os sistemas envolvidos são embarcados, os aspectos de gerenciamento de energia devem ser observados e estudados a fim de amplificar o tempo de funcionamento dos sistemas sem que haja manutenção ou troca de baterias. É importante ressaltar que, dentro deste contexto, a transmissão de dados muitas vezes ocorre a distância, isto é, sem cabeamento. Nesse sentido, atualmente existem diversas tecnologias de transmissão de dados sem fio que dispensam alimentação em grande escala. Algumas destas tecnologias, que emergiram e atingiram seu ápice ou que estão em processo de emergência, são conhecidas por fazerem parte de um conjunto de tecnologias que possibilitam redes de grande cobertura e baixo consumo, também conhecidas como <i> Low Power Wide Area Network </i> (LPWAN).</p>

<h3 align="center">                            Computação em nuvem                                         </h3>
<p  align="justify" style="margin-top: 5px; ">Computação em nuvem é um termo utilizado para definir serviços e recursos computacionais hospedados e providos de maneira distribuída e sob demanda. A computação em nuvem pode ser dividida em três principais categorias baseadas em sua disponibilidade, no entanto, é importante ressaltar que ao todo existem dez tipos de modelos de serviços. Dentre estas três categorias,  estão:</p>
	<ul>
		<li>Infraestrutura como Serviço, do inglês <i> “Infrastructure as a Service” </i>, (IaaS): Trata-se de um termo utilizado para se referir a um tipo de modalidade de computação em nuvem que engloba serviços essenciais para estruturação de uma infraestrutura, tais como, por exemplo: redes, armazenamento e segurança. Nesse modelo, o gerenciamento de alguns recursos, como por exemplo, das aplicações, do sistema operacional, dos dados, dos certificados e dos sistemas operacionais, é responsabilidade do usuário/cliente.</li> 
		<li>Plataforma como Serviço, do inglês <i> “Plataform as a Service” </i>, (PaaS): Nessa modalidade, o provedor de serviços de computação em nuvem oferece e gerencia a plataforma e infraestrutura necessária para que o usuário/cliente hospede e/ou desenvolva suas aplicações. Neste tipo de modalidade, o usuário/cliente gerencia a aplicação, algumas configurações do ambiente e, em alguns casos, os dados.</li>
		<li>Software como Serviço, do inglês <i> “Software as a Service” </i>, (SaaS): É a modalidade com menos preocupações para o usuário/cliente acerca do produto. Toda infraestrutura, plataforma e aspectos relacionados a estes tópicos que estão posicionados de maneira subjacente são fornecidos e gerenciados pelo provedor.</li>
	</ul>
<p  align="justify" style="margin-top: 5px; ">&emsp;Nesse sentido, como é possível observar na imagem abaixo, ainda é viável desenvolver uma relação entre os diferentes tipos de cenários, expressos nesse artigo na forma de categorias, para a construção de uma arquitetura diferente.</p>
<p align="center"><img src="https://www.gta.ufrj.br/ensino/eel879/trabalhos_vf_2009_2/seabra/images/cenarios.png"></p>
<p align="center"> Figura 3. Exemplo relação entre os diferentes tipos de cenários, expressos nesse artigo na forma de categorias, para a construção de uma arquitetura diferente (Dois IaaS utilizados para construção de um).</p>
<p  align="justify" style="margin-top: 5px; ">&emsp;Enfim, em resumo, os serviços computacionais são os mais diversos possíveis, podendo ir de um simples serviço de armazenamento até um conjunto de serviços que fazem parte da infraestrutura de um produto. </p>

<h2 align="center">                            Metodologias e Ferramentas                                          </h2>

  <h3 align="center">                            Metodologia para pesquisa                                         </h3>
  <p  align="justify" style="margin-top: 5px; ">O desenvolvimento do Sistema de Detecção de Incêndios Florestais (SDIF) adotou uma abordagem cuidadosa e sistemática para a seleção de tecnologias e componentes, fundamentada em metodologias de pesquisa científica. O método científico foi aplicado de maneira qualitativa, descritiva, aplicada e experimental, para garantir a eficácia e adequação de cada componente e tecnologia incorporada no sistema. </p>
    <h4 align="center">                            Abordagem científica e estrutura da pesquisa                     </h4>
    <p  align="justify" style="margin-top: 5px; ">A pesquisa foi estruturada em várias fases sequenciais e ciclícas, sendo elas: de revisão bibliográfica, análise e filtragem e integração dos resultados obtidos ao final destas etapas no conjunto de pesquisa. Esse processo foi repetido iterativamente até que os produtos selecionados satisfizessem completamente os requisitos e expectativas do projeto. </p>
    <ul>
	    <li><b>Revisão Bibliográfica:</b> Inicialmente, foi realizada uma extensa revisão da literatura existente relacionada à detecção de incêndios florestais e às tecnologias envolvidas no projeto. Isso incluiu estudos acadêmicos, artigos técnicos, e publicações sobre os avanços mais recentes em sensores, comunicação de dados e análise de imagens por inteligência artificial. Essa revisão ajudou a definir as bases teóricas e práticas para o desenvolvimento do projeto. </li>
            <li><b>Análise e Filtragem:</b> Após a compilação de fontes relevantes, seguiu-se uma fase meticulosa de análise e filtragem onde cada fonte foi examinada para validar sua relevância e precisão. Datasheets de componentes, estudos de caso e benchmarks foram particularmente enfatizados. Essa etapa também incluiu análises técnicas detalhadas dos componentes potenciais para garantir que atendiam às especificações necessárias do projeto. Avaliações de desempenho, compatibilidade de sistema e análises de custo-benefício foram alguns dos pontos levados em conta durante essa fase. </li>
            <li><b>Integração dos Resultados Obtidos:</b>  Os insights e dados coletados nas fases anteriores foram sintetizados e integrados em um plano de desenvolvimento. Essa etapa envolveu a seleção final de componentes e tecnologias que seriam implementadas no protótipo do SDIF. Decisões sobre arquitetura de sistema, interconexões de hardware e software, e estratégias de implementação foram solidificadas. A integração destes elementos de forma adequada constituiu-se essencial para a construção do protótipo. </li>
    </ul>
  <h3 align="center">                            Critérios para seleção de componentes                                               </h3>
  <ol>
	  <li><b>Capacidade de mensuração de temperatura:</b></li>
	  <ul>
		  <li><b>Ambiente:</b> Os sensores de temperatura devem ser capazes de monitorar eficientemente a temperatura ambiente, crucial para detectar alterações que possam indicar o início de um incêndio. O foco principal nessa etapa foi selecionar sensores que possuem resposta rápida às mudanças ambientais locais. </li>
		  <li><b>Método de medição:</b> Os sensores escolhidos devem basear-se em tecnologias adequadas para medições ambientais, como termistores para sensibilidade a temperaturas, ou circuitos integrados (CIs) que oferecem facilidade de integração e leituras precisas. Tecnologias como termopares são menos relevantes para este aplicativo, dado o foco em medições de temperatura ambiente e não pontuais. </li>
	  </ul>
	  <li><b>Capacidade de transmissão de dados:</b></li>
	  <ul>
		  <li><b>Tamanho máximo de pacote:</b> O tamanho do pacote define o volume de dados que pode ser enviado em uma única transmissão. Para o SDIF, que envolve a transmissão de dados de sensor e, potencialmente, imagens capturadas pelas câmeras Arducam, a capacidade de enviar pacotes maiores é crucial para a integridade e a rapidez da comunicação. Nesse sentido, foram escolhidas tecnologias que permitissem o envio de pacotes de dados suficientemente grandes para cobrir as necessidades de transmissão de uma única imagem ou de múltiplos dados sensoriais simultaneamente. Isso reduz a complexidade do sistema de controle de transmissão e minimiza o risco de perda de dados. </li>
		  <li><b>Alcance e resistência às interferências:</b> Os componentes devem suportar uma transmissão de dados robusta e confiável a distâncias consideráveis, isto é, afim de diminuir a quantidade de gateways intermediários e de nós finais. A seleção considera a capacidade de operar em frequências adequadas para comunicação à longa distância e em condições potencialmente interferentes, como áreas densamente arborizadas. </li>
	  </ul>
	  <li><b>Condições suportadas:</b></li>
	  <p  align="justify" style="margin-top: 5px; ">Os componentes devem ser resistentes a condições extremas, incluindo altas temperaturas, umidade, chuva e exposição prolongada ao sol. A durabilidade em diversas condições climáticas é avaliada para garantir a longevidade e a confiabilidade do sistema. </p>
	  <li><b>Consumo energético:</b></li>
	  <p  align="justify" style="margin-top: 5px; ">O consumo de energia é um fator crítico, especialmente para sistemas que requerem operação contínua e autônoma em áreas remotas. Componentes de baixo consumo são preferidos para maximizar a vida útil das baterias e a eficiência energética do sistema. </p>
  </ol>
    <h4 align="center">                            Protocolo de seleção de componentes                                               </h4>
    <p  align="justify" style="margin-top: 5px; ">Cada componente potencial passa por um processo de seleção rigoroso que inclui: </p>
    <ol>
	    <li><b>Documentação detalhada:</b> Criação de um documento para cada modelo de componente analisado, incluindo título, descrição detalhada do tipo, subtipo, características principais e fontes de consulta. </li>
	    <li><b>Análise de datasheets:</b> Revisão minuciosa de datasheets para validar as especificações técnicas de cada componente, com atenção especial para os parâmetros operacionais e limitações. </li>
    </ol>
  <h3 align="center">                            Metodologia para testagem dos componentes                                           </h3>
  <p  align="justify" style="margin-top: 5px; ">Para garantir que os resultados dessa pesquisa coincidam com as expectativas definidas no levantamento de requisitos, uma metodologia de testes rigorosa foi estabelecida. Essa metodologia segue um conjunto de protocolos projetados para validar cada componente e sistema integrado, desde a precisão dos sensores até a confiabilidade da transmissão de dados. </p>
    <h4 align="center">                            Metodologia de testes do SDIF                                                     </h4>
    <p  align="justify" style="margin-top: 5px; ">A metodologia de testes adotada para o SDIF é composta de várias etapas chave, cada uma com seus próprios critérios e procedimentos específicos: </p>
    <ol>
	    <li><b>Testes de componentes isolados (Unitário):</b></li>
	    <ul>
		    <li><b>Objetivo:</b> Avaliar o desempenho e a confiabilidade de cada componente individualmente. </li>
		    <li><b>Procedimento:</b> Cada componente (sensores, módulos de comunicação, câmeras, etc.) é testado isoladamente para verificar suas especificações técnicas contra os valores e desempenhos descritos nos datasheets. Isso inclui testes de durabilidade, precisão de medição e consumo de energia. </li>
	    </ul>
	    <li><b>Testes de integração de sistema (Integração):</b></li>
	    <ul>
		    <li><b>Objetivo:</b> Garantir que todos os componentes funcionem harmoniosamente como um sistema integrado. </li>
		    <li><b>Procedimento:</b> Após os testes individuais, os componentes são integrados e testados juntos para identificar qualquer incompatibilidade ou falha de integração. Testes incluem a verificação da comunicação entre os módulos, a eficácia da coleta de dados e o processamento em tempo real. </li>
	    </ul>
	    <li><b>Testes de desempenho em ambiente controlado:</b></li>
	    <ul>
		    <li><b>Objetivo:</b> Avaliar o desempenho do sistema em condições controladas que simulam ambientes reais. </li>
		    <li><b>Procedimento:</b> O sistema é exposto a variadas condições ambientais em laboratório ou em ambientes controlados externos. Isso inclui a simulação de condições de incêndio, variáveis meteorológicas e outras condições ambientais adversas para testar a robustez e a resposta do sistema. </li>
	    </ul>
	    <li><b>Observações</b></li>
	    <p  align="justify" style="margin-top: 5px; "> É importante notar que, uma das etapas fundamentais para um projeto desse tipo são os testes de campo. No entanto, dado as limitações e possibilidades de realização desse tipo de teste, ele foi excluído da metodologia atual e será tratado como um objetivo futuro. </p>
    </ol>
    <h4 align="center">                            Protocolos de teste                                                               </h4>
    <p  align="justify" style="margin-top: 5px; ">Para cada fase de teste, foram estabelecidos protocolos detalhados: </p>
    <ol>
	    <li><b>Documentação de Testes:</b> Cada teste é meticulosamente documentado, incluindo a configuração do teste, os resultados obtidos, e as análises realizadas. Isso assegura uma referência clara para futuras melhorias e validação de dados. </li>
	    <li><b>Revisão de Resultados: </b> Os resultados são revisados por uma equipe de engenheiros e especialistas para validar a integridade e a aplicabilidade dos resultados. Decisões sobre a necessidade de revisões de design ou ajustes de componente são tomadas com base nessa análise. </li>
    </ol>
  <h3 align="center">                            Metodologia para seleção do provedor de serviçoes em nuvem                          </h3>
  <p  align="justify" style="margin-top: 5px; ">  </p>
  <h3 align="center">                            Métricas de Avaliação para Modelos de <i> Machine Learning </i> e <i> Deep Learning </i>  </h3>
  <p  align="justify" style="margin-top: 5px; "> Para a avaliação do desempenho dos classificadores de detecção de incêndios florestais, foram utilizadas as métricas de Acurácia (AC) proporção dos classificados corretamente para todas as classes, Recall (RC) proporção dos incêndios encontrados no algoritmo, Precisão (PR) observações classificadas como fogo que eram na verdade fogo, F1-score (F1) média harmônica do recall e da precisão (RODRIGUES, 2019). As equações são representadas na figura a seguir: </p>
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

<p  align="justify" style="margin-top: 5px; ">Dennison et al. (2014), "Wildfires and Climate Change", https://www.c2es.org/content/wildfires-and-climate-change/, Abril.</p>

<p align="justify" style="margin-top: 5px; ">A. Matias (2020), "Queimadas na Amazônia", https://mundoeducacao.uol.com.br/geografia/queimadas-na-amazonia.htm, Abril.</p>

<p align="justify" style="margin-top: 5px; ">“Monitoramento de queimadas em imagens de satélites”, http://www.ibama.gov.br/consultas/incendios-florestais/consultas-monitoramento-de-queimadas/monitoramento-de-focos-de-queimadas-em-imagens-de-satelites, Abril.</p>

<p align="justify" style="margin-top: 5px; ">“Sistemas de monitoramento”, http://queimadas.dgi.inpe.br/queimadas/portal, Abril.</p>

<p align="justify" style="margin-top: 5px; ">“Perguntas frequentes”, http://queimadas.dgi.inpe.br/queimadas/portal/informacoes/perguntas-frequentes#p2, Abril.</p>

<p align="justify" style="margin-top: 5px; ">“Monitoramento”, http://redd.mma.gov.br/pt/monitoramento, Abril.</p>

<p align="justify" style="margin-top: 5px; ">“Centro Nacional de Prevenção e Combate aos Incêndios Florestais (Prevfogo)”, http://www.ibama.gov.br/prevfogo#programas-e-projetos, Abril.</p>

<p align="justify" style="margin-top: 5px; ">LeCun, Y., Bottou, L., Bengio, Y., and Haffner, P., (1998), “Gradient Based Learning Applied to Document Recognition”, In Proceedings of the IEEE Conference. Publishing Press.</p>

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
