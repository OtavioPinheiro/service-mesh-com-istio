# Service Mesh com Istio

# Sumário
1. [O que é Service Mesh?](#o-que-é-service-mesh)
2. [O que é Istio?](#o-que-é-istio)

# O que é Service Mesh?
**Service Mesh** é uma arquitetura de rede que visa resolver desafios complexos associados à comunicação entre os serviços em uma infraestrutura de microsserviços. Ele fornece uma camada de abstração sobre a comunicação entre os serviços, permitindo a descoberta dinâmica, a roteamento inteligente, a segurança e o monitoramento avançados.

Conceitos e componentes-chave de um **Service Mesh**:

**Proxy Sidecar**: Cada instância de serviço é acompanhada por um ***proxy sidecar***, como o ***Envoy Proxy***, que é injetado no mesmo `pod`. O *proxy sidecar* intercepta todo o tráfego de entrada e saída do serviço, fornecendo funcionalidades avançadas, como roteamento, balanceamento de carga, segurança e monitoramento.

**Balanceamento de carga**: A **Service Mesh** distribui uniformemente o tráfego entre as instâncias de um serviço, garantindo alta disponibilidade e desempenho.

**Descoberta de Serviços**: O **Service Mesh** oferece descoberta de serviços dinamicamente, permitindo que os serviços se encontrem e se comuniquem de forma eficiente, sem a necessidade de configuração estática, ou seja, sem precisar saber os endereços IP ou portas. Isso é geralmente realizado por meio de um registro de serviço, como o *Consul* ou o *Kubernetes Service Discovery*.

**Roteamento de Tráfego**: O **Service Mesh** permite o roteamento avançado de tráfego com base em regras configuráveis, direcionando as solicitações para o serviço correto. Isso inclui roteamento com base em características como cabeçalhos HTTP, metadados do serviço, políticas de segurança e condições de tráfego.

**Segurança**: A segurança é uma preocupação central em um ambiente de microsserviços distribuído. O **Service Mesh** oferece recursos avançados de segurança, como autenticação mútua, autorização baseada em políticas, criptografia de comunicação e gerenciamento de chaves.

**Monitoramento e Observabilidade**: Com o **Service Mesh**, você pode obter *insights* detalhados sobre o tráfego de rede e o comportamento dos serviços. Isso inclui métricas de desempenho, rastreamento de solicitações, registros e alertas para ajudar na solução de problemas e no diagnóstico de problemas de maneira rápida e eficaz, permitindo que os desenvolvedores e operadores acompanhem o desempenho e a saúde dos serviços em tempo real.

**Resiliência**: O **Service Mesh** oferece recursos para aumentar a resiliência de aplicativos distribuídos, como ***retries***, ***circuit breakers***, ***rate limiting*** e ***failover*** automático.

Em resumo, o **Service Mesh** é uma abordagem poderosa para simplificar e fortalecer a comunicação entre os serviços em uma arquitetura de microsserviços. Ele fornece uma série de recursos essenciais, desde a descoberta de serviços até a segurança e o monitoramento avançados, ajudando as organizações a construir e operar aplicativos escaláveis e altamente disponíveis em ambientes de microsserviços complexos.

[Voltar para o sumário](#sumário)

# O que é Istio?
O Istio é uma plataforma de [***service mesh***](#o-que-é-service-mesh) de código aberto que fornece uma camada de abstração inteligente para gerenciar e conectar microsserviços em ambientes distribuídos. Ele foi projetado para resolver os desafios complexos associados à comunicação entre microsserviços distribuídos em uma arquitetura de contêineres.

A conectividade segura e resiliente é garantida através do balanceamento de carga inteligente, que distribui o tráfego entre as instâncias de forma eficiente e automatizada, assegurando alta disponibilidade e desempenho. A segurança integrada implementa autenticação, autorização e criptografia de tráfego para proteger seus microsserviços contra acessos não autorizados e ataques cibernéticos. Além disso, o monitoramento detalhado oferece visibilidade profunda do tráfego de rede, métricas de desempenho e logs, permitindo identificar e resolver problemas rapidamente.

A observação e controle granulares são possíveis através do gerenciamento de tráfego granular, que permite definir políticas de roteamento avançadas, controlar o fluxo de dados e implementar medidas de segurança personalizadas por microsserviço. O monitoramento em tempo real fornece dashboards e alertas para acompanhar o desempenho e a saúde dos microsserviços, permitindo identificar e solucionar problemas proativamente. O rastreamento de solicitações permite acompanhar o fluxo de solicitações entre os microsserviços, facilitando a depuração e a otimização do desempenho.

A integração com ferramentas existentes é facilitada pelo suporte a diversas plataformas, incluindo **Kubernetes**, **OpenShift** e **AWS Elastic Kubernetes Service (EKS)**. A integração com ferramentas de DevOps, como **Prometheus**, **Grafana** e **Jaeger**, facilita a adoção e o gerenciamento em workflows existentes. A extensibilidade permite a criação de plugins e extensões personalizados para atender às necessidades específicas da sua organização.

Os benefícios do **Istio** incluem a simplificação da gestão de microsserviços, reduzindo a complexidade da operação e do gerenciamento de microsserviços em ambientes distribuídos. A melhoria da segurança e confiabilidade garante a segurança robusta dos microsserviços e a confiabilidade das aplicações. A visibilidade e observação aprimoradas oferecem _insights_ profundos sobre o comportamento dos microsserviços, facilitando a identificação e resolução de problemas. O aumento da agilidade e da escalabilidade permite o desenvolvimento e a implantação de aplicações escaláveis e resilientes de forma mais rápida e eficiente.

Em resumo, o **Istio** oferece uma solução abrangente para os desafios de gerenciamento de microsserviços em ambientes de nuvem modernos. Ele fornece uma maneira eficaz de lidar com a complexidade associada à comunicação entre serviços distribuídos, oferecendo controle, segurança e observabilidade em toda a malha de serviços. Como uma plataforma de código aberto, o **Istio** continua a evoluir e inovar, fornecendo uma base sólida para a construção e operação de sistemas distribuídos escaláveis e confiáveis.

[Voltar para o sumário](#sumário)

# Arquitetura do **Istio**
A arquitetura do **Istio** é composta por vários componentes que trabalham juntos para fornecer funcionalidades avançadas de gerenciamento, segurança e observabilidade para microsserviços distribuídos. Os principais componentes da arquitetura do **Istio** são:

1. **Envoy Proxy**: O `Envoy` é o componente central da arquitetura do **Istio**. <u>Ele é um proxy de serviço de alto desempenho</u> e extensível que é <u>implantado ao lado de cada microsserviço (`pod`) para gerenciar o tráfego de rede</u>. O `Envoy` lida com tarefas como roteamento de tráfego, balanceamento de carga, descoberta de serviços, autenticação e autorização.

2. **Data Plane e Control Plane**: O **Istio** segue uma arquitetura de duas camadas, composta pelo `Data Plane` e pelo `Control Plane`. O `Data Plane` é composto por _proxies_ `Envoy` implantados ao lado de cada serviço, que gerenciam o tráfego de rede em tempo real, ou seja, <u>é um conjunto de `Envoy Proxy`</u>. O `Control Plane` é <u>responsável por configurar e controlar o comportamento do `Data Plane`</u>. Ele inclui componentes como o **Istio Pilot**, **Istio Mixer** e **Istio Citadel**.

3. **Pilot**: O **Istio Pilot** é <u>responsável por gerenciar as configurações de roteamento de tráfego e descoberta de serviços</u>. Ele converte as configurações de alto nível definidas pelos operadores em configurações específicas de _proxy_ que são distribuídas para os _proxies_ `Envoy` em tempo real.

4. **Mixer**: O **Istio Mixer** é <u>responsável pela coleta de telemetria, aplicação de políticas e autorização</u>. Ele fornece um ponto centralizado para aplicar políticas de segurança, monitorar o tráfego de rede e coletar métricas e registros de telemetria.

5. **Citadel**: O **Istio Citadel** é <u>responsável por gerenciar a identidade e a segurança dos microsserviços</u>. Ele emite certificados TLS e chaves de autenticação para os _proxies_ `Envoy` e fornece um mecanismo de autenticação mútua entre os serviços.

6. **Galley**: O **Istio Galley** é <u>responsável pela validação e distribuição de configurações de serviço</u>. Ele valida as configurações de alto nível definidas pelos operadores e as converte em configurações específicas de _proxy_ que são distribuídas para os _proxies_ `Envoy`.

7. **Telemetria e Ferramentas de Observabilidade**: O **Istio** integra-se a várias ferramentas de observabilidade, como ***Prometheus***, ***Grafana***, ***Jaeger*** e ***Zipkin***, para fornecer monitoramento e rastreamento distribuído do tráfego de rede entre os microsserviços.

No geral, a arquitetura do **Istio** é altamente distribuída e escalável, projetada para lidar com a complexidade associada à comunicação entre microsserviços em ambientes de nuvem modernos. Ao fornecer uma camada de abstração entre os microsserviços e a infraestrutura subjacente, o **Istio** simplifica o gerenciamento e a operação de sistemas distribuídos, oferecendo controle, segurança e observabilidade em toda a malha de serviços.

![Arquitetura do Istio](./imgs/istio-arquitetura.png)

**Fontes:**
- [Istio](https://istio.io/latest/about/service-mesh/)