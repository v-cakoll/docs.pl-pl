---
title: Hosting w Usłudze aktywacji procesów systemu Windows
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: eeac535eac95b19889d0d8d74115bcddc3a15224
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402353"
---
# <a name="hosting-in-windows-process-activation-service"></a>Hosting w Usłudze aktywacji procesów systemu Windows
Windows Process Activation Service (WAS) zarządza aktywacji i okresem istnienia procesów roboczych, które zawierają aplikacji zawierających usługi Windows Communication Foundation (WCF). Model procesów WAS stanowi uogólnienie modelu procesów usług IIS 6.0 serwera HTTP przez usunięcie zależności od protokołu HTTP. Dzięki temu usługi WCF do użycia protokołów HTTP i protokołów innych niż HTTP, np. Net.TCP, w środowisku macierzystym, który obsługuje aktywację w oparciu o wiadomości i oferuje możliwość hostowania wielu aplikacji na danym komputerze.  
  
 Aby uzyskać więcej informacji na temat tworzenia usługi WCF, który jest uruchamiany w środowisku hostingu WAS, zobacz [jak: Hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md).  
  
 Model procesów WAS udostępnia kilka funkcji, które umożliwiają aplikacjom hostowane w sposób, to bardziej niezawodne, łatwiejsze w obsłudze i efektywnie, używa zasobów:  
  
- Aktywacja oparta na komunikat, aplikacji i proces roboczy procesu aplikacji uruchamiają i zatrzymują dynamicznie, w odpowiedzi na przychodzące elementów roboczych, pojawiające się przy użyciu protokołu HTTP i protokołów sieciowych protokołu HTTP.  
  
- Niezawodna aplikacja i odtwarzanie procesów roboczych do utrzymania kondycji uruchomionych aplikacji.  
  
- Konfiguracja aplikacji scentralizowane i zarządzanie.  
  
- Umożliwia aplikacjom móc korzystać z modelu procesów usług IIS bez konieczności wdrażania śladu pełnej instalacji usług IIS.  
  
 Aby uzyskać więcej informacji na temat funkcji WAS zobacz [IIS 7.0 Beta: Usługi IIS 7.0 w sieci Web administracji](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).  
  
 [Windows Server AppFabric](https://go.microsoft.com/fwlink/?LinkId=196496) współpracuje z [!INCLUDE[iisver](../../../../includes/iisver-md.md)] i Windows Process Activation Service (WAS) zapewnienie rozbudowanych aplikacji, środowisko dla usług NET4 WCF i WF hostingu. Te korzyści to m.in. Zarządzanie cyklem życia procesu, odtwarzanie procesów, dostawców usług hostingu, ochrona przed seriami błędów, oddzielanie procesu, aktywacji na żądanie i monitorowania kondycji. Aby uzyskać szczegółowe informacje, zobacz [funkcje hostingu programu AppFabric](https://go.microsoft.com/fwlink/?LinkId=196494) i [pojęcia hostingu AppFabric](https://go.microsoft.com/fwlink/?LinkId=196495).  
  
## <a name="elements-of-the-was-addressing-model"></a>Elementy WAS adresowania modelu  
 Aplikacje mają adresy identyfikator (URI), które są jednostkami kod, którego okres istnienia i wykonywania środowisko są zarządzane przez serwer. Pojedyncze wystąpienie serwera WAS może być macierzystego do wielu różnych aplikacji. Serwery Organizuj aplikacje w grupy o nazwie *witryn*. W ramach lokacji aplikacje są rozmieszczone w hierarchiczny sposób, który odzwierciedla strukturę identyfikatory URI, które służą jako ich zewnętrzne adresy.  
  
 Adresy aplikacji mają dwie części: podstawowy prefiks identyfikatora URI oraz adres specyficzne dla aplikacji, względna (ścieżka), które zawierają zewnętrzny adres dla aplikacji i połączone. Podstawowy prefiks identyfikatora URI jest tworzony z powiązania witryny i jest używany dla wszystkich aplikacji w witrynie. Adresy aplikacji następnie są tworzone, wykonując fragmenty ścieżki specyficzne dla aplikacji (takich jak "/ applicationOne") i dołączanie ich do podstawowej prefiks identyfikatora URI (na przykład, "NET.TCP://localhost") na pełny identyfikator URI aplikacji.  
  
 W poniższej tabeli przedstawiono kilka możliwych scenariuszy adresowania dla WAS lokacji przy użyciu protokołów HTTP i powiązania witryny protokołu HTTP.  
  
|Scenariusz|Powiązania witryny|Ścieżka aplikacji|Podstawowa aplikacja identyfikatory URI|  
|--------------|-------------------|----------------------|---------------------------|  
|Tylko HTTP|http: *:80:\*|/appTwo|http://localhost/appTwo/|  
|HTTP i innych niż HTTP|http: *:80:\*<br /><br /> net.tcp: 808:\*|/appTwo|http://localhost/appTwo/<br />net.tcp://localhost/appTwo/|  
|Innych niż HTTP tylko|NET.pipe: *|/appThree|net.pipe://appThree/|  
  
 Maszyny wirtualne i zasoby w ramach aplikacji również może zostać zlikwidowane. W ramach aplikacji zasobów aplikacji są adresowane względem ścieżki podstawowej aplikacji. Na przykład załóżmy, że witryna w contoso.com Nazwa maszyny zawiera powiązania witryny dla protokołów HTTP i Net.TCP. Również założono, że witryna zawiera jedną aplikację znajdujący się w /Billing, która udostępnia usługę GetOrders.svc. Następnie, jeśli usługa GetOrders.svc uwidaczniany punkt końcowy z adresem względnym SecureEndpoint, punkt końcowy usługi będą widoczne w następujących dwóch identyfikatorów URI:  
  
- `http://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
- `net.tcp://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
  
## <a name="the-was-runtime"></a>WAS środowiska uruchomieniowego  
 Aplikacje są zorganizowane w witrynach na potrzeby adresowania i zarządzania. W czasie wykonywania aplikacje są również grupowane w pulach aplikacji. Pula aplikacji mogą znajdować się wiele różnych aplikacji pochodzących od wielu witryn. Wszystkie aplikacje w puli aplikacji korzystają ze wspólnego zestawu, właściwości środowiska wykonawczego. Na przykład wszystkie działają w ramach tej samej wersji środowiska uruchomieniowego języka wspólnego (CLR), a wszystkie mają wspólną tożsamość procesu. Każda pula aplikacji odnosi się do wystąpienia procesu roboczego (w3wp.exe). Każdej zarządzanej aplikacji, które działają w ramach puli aplikacji udostępnionej jest odizolowana od innych aplikacji za pomocą CLR AppDomain.  
  
## <a name="see-also"></a>Zobacz także

- [Architektura aktywacji WAS](../../../../docs/framework/wcf/feature-details/was-activation-architecture.md)
- [Konfigurowanie usługi WAS do użycia z programem WCF](../../../../docs/framework/wcf/feature-details/configuring-the-wpa--service-for-use-with-wcf.md)
- [Instrukcje: Instalowanie i konfigurowanie składników aktywacji programu WCF](../../../../docs/framework/wcf/feature-details/how-to-install-and-configure-wcf-activation-components.md)
- [Instrukcje: Hostowanie usługi WCF w WAS](../../../../docs/framework/wcf/feature-details/how-to-host-a-wcf-service-in-was.md)
- [Windows Server AppFabric funkcje hostingu](https://go.microsoft.com/fwlink/?LinkId=201276)
