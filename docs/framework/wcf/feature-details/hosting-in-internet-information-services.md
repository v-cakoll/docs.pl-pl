---
title: Hostowanie przez Internetowe usługi informacyjne
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 3940d8436ba5441d4e884879213a7a782214cb05
ms.sourcegitcommit: 2d42b7ae4252cfe1232777f501ea9ac97df31b63
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2019
ms.locfileid: "67486750"
---
# <a name="hosting-in-internet-information-services"></a>Hostowanie przez Internetowe usługi informacyjne
Jedną z opcji hostingu usług Windows Communication Foundation (WCF) jest wewnątrz aplikacji usług Internet Information Services (IIS). Ten model hostingu jest podobny do modelu, używane przez program ASP.NET i usług sieci Web (ASMX) usługi sieci Web platformy ASP.NET.  
  
## <a name="versions-of-iis"></a>Wersje usług IIS  
 Usługi WCF, może być hostowana na następujących wersjach usług IIS w następujących systemach operacyjnych:  
  
- Usługi IIS 5.1 w [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. To środowisko jest przydatne w przypadku projektowania i opracowywania aplikacji hostowanych przez usługi IIS, wdrożone później w systemie operacyjnym serwera takich jak [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
- Usługi IIS 6.0 na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. Usługi IIS 6.0 zapewnia model zaawansowany proces, który oferuje zwiększona skalowalność, niezawodność i izolacji aplikacji. To środowisko jest odpowiednia do wdrożenia produkcyjnego usług WCF, które używają wyłącznie protokołu HTTP do komunikacji.  
  
- Usługi IIS 7.0 na [!INCLUDE[wv](../../../../includes/wv-md.md)] i [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. Usługi IIS 7.0 zawiera ten sam model zaawansowany proces jako usług IIS 6.0, ale używa Windows Process Activation Service (WAS), aby umożliwić aktywacji i komunikację sieciową za pośrednictwem protokołów innych niż HTTP. To środowisko jest odpowiednie do tworzenia usług WCF, które komunikują się przez dowolny protokół sieciowy obsługiwany przez architekturę WCF (w tym HTTP, net.tcp, net.pipe i net.msmq). Aby uzyskać więcej informacji o WAS, zobacz [Hosting w usłudze aktywacji procesów Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
- [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) współpracuje z usług IIS 7.0 i usługa Windows Process Activation Service (WAS) w celu zapewnienia zaawansowanych aplikacji, środowisko dla usług NET4 WCF i WF hostingu. Te korzyści to m.in. Zarządzanie cyklem życia procesu, odtwarzanie procesów, dostawców usług hostingu, ochrona przed seriami błędów, oddzielanie procesu, aktywacji na żądanie i monitorowania kondycji. Aby uzyskać szczegółowe informacje, zobacz [funkcje hostingu programu AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) i [pojęcia hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Zalety hostowanie usług IIS  
 Hostowanie usługi WCF w usługach IIS ma kilka zalet:  
  
- Usług WCF hostowanych w usługach IIS są wdrożone i zarządzane podobnie jak każdy inny rodzaj aplikacji usług IIS, w tym aplikacji ASP.NET i ASMX.  
  
- IIS oferuje proces aktywacji, zarządzanie stanem zdrowia i odtwarzanie możliwości w celu zwiększenia niezawodności obsługiwanych aplikacji.  
  
- Takimi jak ASP.NET usługi WCF hostowane na platformie ASP.NET można korzystać z modelu hostingu współdzielonego ASP.NET gdy wiele aplikacji znajdują się w typowych procesu roboczego dla serwera ulepszoną gęstość i skalowalności.  
  
- Usługi WCF hostowane w usługach IIS przy użyciu tego samego modelu kompilacji dynamicznej jako programu ASP.NET 2.0, który upraszcza opracowywanie i wdrażanie usług hostowanych.  
  
 Przy wyborze rozwiązania do obsługi usług WCF w usługach IIS, jest pamiętać, że usługi IIS 5.1 i IIS 6.0 jest ograniczone do tylko komunikacji HTTP. Aby uzyskać więcej informacji o wybieraniu Środowisko hostingu, zobacz [usług obsługującego](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Wdrażanie usługi WCF hostowanej przez usługi IIS  
 Tworzenie i wdrażanie usługi WCF hostowanej przez usługi IIS składa się z następujących zadań:  
  
- Upewnij się, że usługi IIS, ASP.NET, usługi WCF i składnika Aktywacja HTTP programu WCF jest poprawnie zainstalowany i zarejestrowany.  
  
- Tworzenie nowej aplikacji usług IIS lub ponownego użycia istniejącej aplikacji ASP.NET.  
  
- Utwórz plik .svc dla usługi WCF.  
  
- Wdrażanie implementacji usługi do aplikacji usług IIS.  
  
- Konfigurowanie usługi WCF.  
  
 Aby uzyskać omówienie każdego z tych zadań, zobacz [wdrażanie usługi WCF Internet Information Services-Hosted](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Usługi WCF i platforma ASP.NET  
 Usługi WCF, mogą być hostowane albo side-by-side przy użyciu platformy ASP.NET lub w trybie zgodności platformy ASP.NET, w którym usługi mogą w pełni korzystać z funkcji oferowanych przez platformę aplikacji sieci Web platformy ASP.NET. Omówienie tych funkcji, zobacz [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Zobacz także

- [Rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)
- [Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)
- [Usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)
- [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)
- [Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)
- [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
