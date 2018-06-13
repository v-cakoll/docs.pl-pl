---
title: Hostowanie przez Internetowe usługi informacyjne
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], IIS
ms.assetid: ddae14e8-143c-442d-b660-2046809b2d43
ms.openlocfilehash: 588e069280afc369256fdbee0132f732348ffc37
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33494117"
---
# <a name="hosting-in-internet-information-services"></a>Hostowanie przez Internetowe usługi informacyjne
Jedną z opcji hosting usług Windows Communication Foundation (WCF) jest wewnątrz aplikacji usług Internet Information Services (IIS). Ten model obsługi jest podobny do modelu używanego przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] i usług sieci Web (ASMX) usług sieci Web ASP.NET.  
  
## <a name="versions-of-iis"></a>Wersje programu IIS  
 Usługi WCF może znajdować się na następujących wersjach usług IIS w następujących systemach operacyjnych:  
  
-   Usługi IIS 5.1 w [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]. To środowisko jest przydatne w przypadku projektowania i opracowywania aplikacji hostowanych przez usługi IIS, wdrożonych później w systemie operacyjnym serwera takich jak [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)].  
  
-   [!INCLUDE[iis601](../../../../includes/iis601-md.md)] na [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)]. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] udostępnia model procesu zaawansowane, który zapewnia lepszą skalowalność i niezawodność izolacji aplikacji. To środowisko jest odpowiednia w przypadku wdrożenia produkcyjnego usług WCF, które używają wyłącznie protokołu HTTP do komunikacji.  
  
-   Usługi IIS 7.0 na [!INCLUDE[wv](../../../../includes/wv-md.md)] i [!INCLUDE[lserver](../../../../includes/lserver-md.md)]. Usługi IIS 7.0 zawiera ten sam model procesu zaawansowane jako [!INCLUDE[iis601](../../../../includes/iis601-md.md)], ale używa usługi aktywacji procesów systemu Windows (WAS), aby umożliwić aktywacji i komunikację sieciową za pośrednictwem protokołów innych niż HTTP. To środowisko jest odpowiednie do tworzenia usług WCF, które komunikują się za pośrednictwem każdy protokół sieciowy obsługiwany przez usługi WCF (w tym HTTP, net.tcp net.pipe i net.msmq). Aby uzyskać więcej informacji na temat WAS, zobacz [Hosting w usłudze aktywacji procesów systemu Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
-   [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) współpracuje z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] i Windows Process Activation Service (WAS) zapewnienie rozbudowanych aplikacji, środowisko NET4 WCF i WF usług hostingu. Te korzyści obejmują zarządzanie cyklem życia procesu, odtwarzanie procesów, udostępniona Usługa hostingu, natychmiastową ochronę przed błędami, oddzielanie procesu, na żądanie aktywacji i monitorowanie kondycji. Aby uzyskać szczegółowe informacje, zobacz [funkcje hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494) i [pojęcia Hosting AppFabric](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="benefits-of-iis-hosting"></a>Zalety hostowanie usług IIS  
 Hosting usług WCF w usługach IIS ma wiele zalet:  
  
-   Usług WCF hostowanych w usługach IIS są wdrażane i zarządzane podobnie jak każdy inny rodzaj aplikacji usług IIS, w tym [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji i ASMX.  
  
-   Usługi IIS oferują aktywacji procesów, zarządzania kondycji oraz odzyskiwanie funkcji w celu zwiększenia niezawodności obsługiwanych aplikacji.  
  
-   Podobnie jak [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)], usługi WCF hostowanej w [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] mogą wykorzystać [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] modelu hostingu współdzielonego, gdy wiele aplikacji znajdują się w typowych procesu roboczego dla serwera ulepszone gęstości i skalowalności.  
  
-   Usługi WCF hostowanej w programie IIS korzystania z tego samego modelu kompilacji dynamicznej jako [!INCLUDE[vstecasplong](../../../../includes/vstecasplong-md.md)], który upraszcza tworzenie i wdrażanie usług hostowanych.  
  
 Podczas podejmowania decyzji o do obsługi usług WCF w usługach IIS, ważne jest, aby należy pamiętać, że usługi IIS 5.1 i [!INCLUDE[iis601](../../../../includes/iis601-md.md)] są ograniczone do komunikacji HTTP tylko. Aby uzyskać więcej informacji o wybieraniu środowiska macierzystego, zobacz [Hosting usług](../../../../docs/framework/wcf/hosting-services.md).  
  
## <a name="deploying-an-iis-hosted-wcf-service"></a>Wdrażanie usługi WCF hostowanych przez usługi IIS  
 Tworzenie i wdrażanie usługi WCF hostowanych przez usługi IIS składa się z następujących zadań:  
  
-   Upewnij się, że usługi IIS, platformy ASP.NET i WCF składnika Aktywacja HTTP programu WCF jest prawidłowo zainstalowany i zarejestrowany.  
  
-   Tworzenie nowej aplikacji usług IIS lub ponowne użycie istniejących [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] aplikacji.  
  
-   Utwórz plik .svc dla usługi WCF.  
  
-   Wdrażanie implementacji usługi do aplikacji usług IIS.  
  
-   Konfigurowanie usługi WCF.  
  
 Aby uzyskać informacje dotyczące każdego z tych zadań, zobacz [wdrażanie usługi WCF Internet Information Services-Hosted](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md).  
  
## <a name="wcf-services-and-aspnet"></a>Usługi WCF i platforma ASP.NET  
 Usługi WCF może być hostowana albo side-by-side z [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] lub [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] tryb zgodności, w którym usług mogą w pełni korzystać z funkcji udostępnianych przez [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] platforma aplikacji sieci Web. Aby uzyskać informacje dotyczące tych funkcji, zobacz [usługi WCF i platformy ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Rozszerzanie hostingu za pomocą elementu ServiceHostFactory](../../../../docs/framework/wcf/extending/extending-hosting-using-servicehostfactory.md)  
 [Wdrażanie usługi WCF hostowanej przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/deploying-an-internet-information-services-hosted-wcf-service.md)  
 [Usługi WCF i platforma ASP.NET](../../../../docs/framework/wcf/feature-details/wcf-services-and-aspnet.md)  
 [Najlepsze rozwiązania dotyczące hostowania Internetowych usług informacyjnych](../../../../docs/framework/wcf/feature-details/internet-information-services-hosting-best-practices.md)  
 [Konfigurowanie Internetowych usług informacyjnych 7.0 na potrzeby programu Windows Communication Foundation](../../../../docs/framework/wcf/feature-details/configuring-iis-for-wcf.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
