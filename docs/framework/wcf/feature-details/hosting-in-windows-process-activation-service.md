---
title: "Hosting w Usłudze aktywacji procesów systemu Windows"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
caps.latest.revision: "16"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d7e8d8446f9cf4f95fecba6bfc18a5432f996f9f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="hosting-in-windows-process-activation-service"></a>Hosting w Usłudze aktywacji procesów systemu Windows
Usługa aktywacji procesów systemu Windows (WAS) zarządza aktywacji i okresem istnienia procesów roboczych, które zawierają aplikacji obsługujących [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] usług. Stanowi uogólnienie modelu procesów WAS [!INCLUDE[iis601](../../../../includes/iis601-md.md)] model procesu dla serwera HTTP przez usunięcie zależności od protokołu HTTP. Dzięki temu [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług jednoczesne używanie protokołów HTTP i protokołów innych niż HTTP, np. Net.TCP, w środowisku macierzystym, który obsługuje aktywację opartą na wiadomości i oferuje możliwość obsługi dużej liczby aplikacji na danym komputerze.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Tworzenie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usługi, która działa w usługi WAS hosting środowiska, zobacz [porady: hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
 Model procesu WAS zawiera kilka funkcji, które umożliwiają aplikacjom, które ma być obsługiwana w sposób jest bardziej niezawodne, łatwiejsze w obsłudze i efektywnie używającej zasobów:  
  
-   Aktywacji opartej na komunikat, aplikacje i aplikacje proces roboczy, uruchamianie i zatrzymywanie dynamicznie, w odpowiedzi na przychodzące elementów roboczych, pojawiające się przy użyciu protokołu HTTP i protokołów sieciowych z systemem innym niż HTTP.  
  
-   Niezawodnych aplikacji i odtwarzania procesu roboczego do dobrej kondycji uruchomionych aplikacji.  
  
-   Konfiguracja aplikacji scentralizowane i zarządzania.  
  
-   Pozwala aplikacjom korzystać z modelu procesów usług IIS bez konieczności wdrażania rozmiaru pełnej instalacji usług IIS.  
  
 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]Funkcje WAS, zobacz [usług IIS 7.0 Beta: Administrowanie sieci Web usług IIS 7.0](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
 [Windows Server AppFabric](http://go.microsoft.com/fwlink/?LinkId=196496) współpracuje z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] i Windows Process Activation Service (WAS) zapewnienie rozbudowanych aplikacji, środowisko NET4 WCF i WF usług hostingu. Te korzyści obejmują zarządzanie cyklem życia procesu, odtwarzanie procesów, udostępniona Usługa hostingu, natychmiastową ochronę przed błędami, oddzielanie procesu, na żądanie aktywacji i monitorowanie kondycji. Aby uzyskać szczegółowe informacje, zobacz [funkcje hostingu AppFabric](http://go.microsoft.com/fwlink/?LinkId=196494) i [pojęcia Hosting AppFabric](http://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="elements-of-the-was-addressing-model"></a>Elementy WAS adresowania modelu  
 Aplikacje mają adresy jednolity identyfikator zasobów (URI), które są jednostkami kod, którego okres istnienia i wykonywania środowisko są zarządzane przez serwer. Pojedyncze wystąpienie serwera WAS może być macierzystego do wielu różnych aplikacji. Serwery organizowania aplikacji do grupy o nazwie *witryny*. W ramach lokacji aplikacje są rozmieszczone w hierarchiczny sposób, który odzwierciedla strukturę identyfikatory URI, które służą jako zewnętrzne adresy.  
  
 Adresy aplikacji ma dwie części: podstawowej Prefiks URI oraz specyficzne dla aplikacji, względny adres (ścieżka), które zawierają zewnętrzny adres dla aplikacji, gdy są połączone. Podstawowy Prefiks URI jest tworzony z powiązania witryny i jest używany dla wszystkich aplikacji w witrynie. Następnie zbudowanych aplikacji adresów wykonując fragmenty ścieżki specyficzne dla aplikacji (takich jak "/ applicationOne") i dołączyć je do podstawowej Prefiks URI (na przykład "NET.TCP://localhost") na pełny identyfikator URI aplikacji.  
  
 W poniższej tabeli przedstawiono kilka możliwych scenariuszy adresowania witryn WAS z protokołów HTTP i powiązania witryny innych niż HTTP.  
  
|Scenariusz|Powiązania witryny|Ścieżka aplikacji|Podstawowy identyfikator URI aplikacji|  
|--------------|-------------------|----------------------|---------------------------|  
|Tylko HTTP|http: *: 80:\*|/appTwo|http://localhost/appTwo/|  
|Protokół HTTP ani innych niż HTTP|http: *: 80:\*<br /><br /> NET.TCP: 808:\*|/appTwo|http://localhost/appTwo/<br />NET.TCP://localhost/appTwo/|  
|Innych niż HTTP tylko|NET.pipe: *|/appThree|NET.pipe://appThree/|  
  
 Można również uwzględnione usług i zasobów w aplikacji. W aplikacji zasoby aplikacji są opisane względem ścieżki podstawowej aplikacji. Załóżmy na przykład, że lokacja na contoso.com nazwa komputera ma powiązania witryny dla protokołów HTTP i Net.TCP. Również założono, że lokacji zawiera jedną aplikację znajdujący się w /Billing, który udostępnia usługi po GetOrders.svc. Następnie usługa GetOrders.svc ujawniany punkt końcowy z adresem względnym SecureEndpoint, czy można ujawnić w następujących dwóch identyfikatorów URI punktu końcowego usługi:  
  
 http://contoso.com/billing/GetOrders.svc/SecureEndpoint  
NET.TCP://contoso.com/billing/GetOrders.svc/SecureEndpoint  
  
## <a name="the-was-runtime"></a>Usługi WAS środowiska wykonawczego  
 Aplikacje są zorganizowane w lokacji na potrzeby adresowania i zarządzania. W czasie wykonywania aplikacje są również grupowane w pulach aplikacji. Wiele aplikacji z wielu różnych lokacji mogą znajdować się w puli aplikacji. Wszystkie aplikacje w puli aplikacji korzystają ze wspólnego zestawu właściwości czasu wykonywania. Na przykład wszystkie one działać w ramach tej samej wersji środowisko uruchomieniowe języka wspólnego (CLR) i wszystkie mają wspólną tożsamość procesu. Każda pula aplikacji odpowiada wystąpienia procesu roboczego (w3wp.exe). Każdej zarządzanej aplikacji, które działają w ramach puli aplikacji udostępnionych jest odizolowana od innych aplikacji za pomocą CLR AppDomain.  
  
## <a name="see-also"></a>Zobacz też  
 [Architektura aktywacji WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)  
 [Konfigurowanie usługi WAS do użycia z programem WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)  
 [Porady: Instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)  
 [Porady: hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)  
 [Windows Server AppFabric funkcje hostingu](http://go.microsoft.com/fwlink/?LinkId=201276)
