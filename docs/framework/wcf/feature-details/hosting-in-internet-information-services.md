---
title: Hostowanie przez Internetowe usługi informacyjne
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: e9d0e5a165eb2eabae95da9fd1e744a9bd1c201b
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44085111"
---
# <a name="hosting-in-internet-information-services"></a>Hostowanie przez Internetowe usługi informacyjne
Jedną z opcji hostingu usług Windows Communication Foundation (WCF) jest wewnątrz aplikacji usług Internet Information Services (IIS). Ten model obsługi jest podobny do modelu posługują się [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] i usługami sieci Web (ASMX) usług sieci Web platformy ASP.NET.  
  
## <a name="versions-of-iis"></a>Wersje usług IIS  
 Usługi WCF, może być hostowana na następujących wersjach usług IIS w następujących systemach operacyjnych:  
  
-   Usługi IIS 5.1 w [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. To środowisko jest przydatne w przypadku projektowania i opracowywania aplikacji hostowanych przez usługi IIS, wdrożone później w systemie operacyjnym serwera takich jak [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] udostępnia model zaawansowany proces, który oferuje zwiększona skalowalność, niezawodność i izolacji aplikacji. To środowisko jest odpowiednia do wdrożenia produkcyjnego usług WCF, które używają wyłącznie protokołu HTTP do komunikacji.  
  
-   Usługi IIS 7.0 na [!INCLUDE[wv](../../../../includes/wv-md.md)] i [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. Usługi IIS 7.0 zawiera ten sam model zaawansowany proces jako [!INCLUDE[iis601](../../../../includes/iis601-md.md)], ale używa Windows Process Activation Service (WAS), aby umożliwić aktywacji i komunikację sieciową za pośrednictwem protokołów innych niż HTTP. To środowisko jest odpowiednie do tworzenia usług WCF, które komunikują się przez dowolny protokół sieciowy obsługiwany przez architekturę WCF (w tym HTTP, net.tcp, net.pipe i net.msmq). Aby uzyskać więcej informacji o WAS, zobacz [Hosting w usłudze aktywacji procesów Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) współpracuje z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] i Windows Process Activation Service (WAS) zapewnienie rozbudowanych aplikacji, środowisko dla usług NET4 WCF i WF hostingu. Te korzyści to m.in. Zarządzanie cyklem życia procesu, odtwarzanie procesów, dostawców usług hostingu, ochrona przed seriami błędów, oddzielanie procesu, aktywacji na żądanie i monitorowania kondycji. Aby uzyskać szczegółowe informacje, zobacz [funkcje hostingu programu AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) i [pojęcia hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Zalety hostowanie usług IIS  
 Hostowanie usługi WCF w usługach IIS ma kilka zalet:  
  
-   Usługi WCF hostowane w usługach IIS są wdrażania i zarządzania nimi, podobnie jak każdy inny rodzaj aplikacji usług IIS, w tym [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji i ASMX.  
  
-   IIS oferuje proces aktywacji, zarządzanie stanem zdrowia i odtwarzanie możliwości w celu zwiększenia niezawodności obsługiwanych aplikacji.  
  
-   Podobnie jak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], usługi WCF hostowanej w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] korzystać z zalet [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modelu hostingu współdzielonego, gdy wiele aplikacji znajdują się w typowych procesu roboczego dla serwera ulepszoną gęstość i skalowalności.  
  
-   Usługi WCF hostowane w usługach IIS, użyj tego samego modelu kompilacji dynamicznej w postaci [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], która upraszcza tworzenie i wdrażanie hostowanej usługi.  
  
 Podczas podejmowania decyzji o do hostowania usług WCF w usługach IIS, ważne jest, aby należy pamiętać, że usługi IIS 5.1 i [!INCLUDE[iis601](../../../../includes/iis601-md.md)] są ograniczone do komunikacji HTTP tylko. Aby uzyskać więcej informacji o wybieraniu Środowisko hostingu, zobacz [usług obsługującego](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Wdrażanie usługi WCF hostowanej przez usługi IIS  
 Tworzenie i wdrażanie usługi WCF hostowanej przez usługi IIS składa się z następujących zadań:  
  
-   Upewnij się, że usługi IIS, ASP.NET, usługi WCF i składnika Aktywacja HTTP programu WCF jest poprawnie zainstalowany i zarejestrowany.  
  
-   Tworzenie nowej aplikacji usług IIS lub ponownego użycia istniejącej [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.  
  
-   Utwórz plik .svc dla usługi WCF.  
  
-   Wdrażanie implementacji usługi do aplikacji usług IIS.  
  
-   Konfigurowanie usługi WCF.  
  
 Aby uzyskać omówienie każdego z tych zadań, zobacz [wdrażanie usługi WCF Internet Information Services-Hosted](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Usługi WCF i platforma ASP.NET  
 Usługi WCF, mogą być hostowane albo side-by-side przy użyciu [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] lub [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności, w którym usługi mogą w pełni korzystać z funkcji oferowanych przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] platforma aplikacji sieci Web. Omówienie tych funkcji, zobacz [usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [Usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
