---
title: Hosting w Usłudze aktywacji procesów systemu Windows
description: Dowiedz się, jak zarządzać aktywacją i okresem istnienia procesów roboczych zawierających aplikacje obsługujące usługi WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- hosting services [WCF], WAS
ms.assetid: d2b9d226-15b7-41fc-8c9a-cb651ac20ecd
ms.openlocfilehash: 6b0b23c21762009341fd62c029431824dd26d6c3
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85247263"
---
# <a name="hosting-in-windows-process-activation-service"></a>Hosting w Usłudze aktywacji procesów systemu Windows
Usługa aktywacji procesów systemu Windows (WAS) zarządza aktywacją i okresem istnienia procesów roboczych, które zawierają aplikacje obsługujące usługi Windows Communication Foundation (WCF). Proces WAS przetwarza model procesów usług IIS 6,0 dla serwera HTTP, usuwając zależność od protokołu HTTP. Dzięki temu usługi WCF mogą korzystać zarówno z protokołu HTTP, jak i protokołów innych niż HTTP, takich jak net. TCP, w środowisku hostingu obsługującym aktywację opartą na komunikatach i oferują możliwość hostowania dużej liczby aplikacji na danym komputerze.  
  
 Aby uzyskać więcej informacji na temat tworzenia usługi WCF działającej w środowisku hostingu, zobacz [How to: hosting a usługi WCF w usłudze was](how-to-host-a-wcf-service-in-was.md).  
  
 Model WAS ma wiele funkcji, które umożliwiają hostowanie aplikacji w sposób bardziej niezawodny, bardziej zarządzany i wykorzystujący zasoby efektywnie:  
  
- Oparta na komunikatach aktywacja aplikacji i aplikacji procesów roboczych uruchamia i zatrzymuje się dynamicznie w odpowiedzi na przychodzące elementy robocze, które docierają przy użyciu protokołów sieciowych HTTP i innych niż HTTP.  
  
- Niezawodne odtwarzanie aplikacji i procesów roboczych, aby zachować kondycję uruchomionych aplikacji.  
  
- Scentralizowana konfiguracja aplikacji i zarządzanie nimi.  
  
- Zezwala aplikacjom na korzystanie z modelu procesów usług IIS bez konieczności wdrażania pełnej instalacji usług IIS.  
[System Windows Server AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)) współpracuje z usługami IIS 7,0 i usługą aktywacji procesów systemu Windows (was), aby zapewnić rozbudowane środowisko hostingu aplikacji dla usług NET4 WCF i WF. Te korzyści obejmują proces zarządzania cyklem życia procesów, odtwarzania procesów, hostingu udostępnionego, szybkiej ochrony przed awariami, oddzielania procesów, aktywacji na żądanie i monitorowania kondycji. Aby uzyskać szczegółowe informacje, zobacz temat [funkcje hostingu platformy AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10)) i [pojęcia hostingu platformy AppFabric](https://docs.microsoft.com/previous-versions/appfabric/ee677371(v=azure.10)).  
  
## <a name="elements-of-the-was-addressing-model"></a>Elementy modelu adresu  
 Aplikacje mają adresy Uniform Resource Identifier (URI), które są jednostkami kodu, których okres istnienia i środowisko wykonawcze są zarządzane przez serwer. Pojedyncze wystąpienie serwera może być w domu z wieloma różnymi aplikacjami. Serwery organizują aplikacje w grupy o nazwie *Lokacje*. W obrębie lokacji aplikacje są uporządkowane w sposób hierarchiczny, który odzwierciedla strukturę identyfikatorów URI, które pełnią rolę adresów zewnętrznych.  
  
 Adresy aplikacji mają dwie części: podstawowy prefiks identyfikatora URI i specyficzny dla aplikacji adres względny (Path), który udostępnia adres zewnętrzny dla aplikacji po połączeniu ze sobą. Podstawowy prefiks identyfikatora URI jest konstruowany z powiązania witryny i jest używany dla wszystkich aplikacji w lokacji. Następnie adresy aplikacji są tworzone przez pobranie fragmentów ścieżek specyficznych dla aplikacji (takich jak "/applicationOne") i dołączenie ich do podstawowego prefiksu URI (na przykład "net. TCP://localhost"), aby dotrzeć do pełnego identyfikatora URI aplikacji.  
  
 W poniższej tabeli przedstawiono kilka możliwych scenariuszy dotyczących adresów dla lokacji z powiązaniami witryn HTTP i innych niż HTTP.  
  
|Scenariusz|Powiązania witryny|Ścieżka aplikacji|Podstawowe identyfikatory URI aplikacji|  
|--------------|-------------------|----------------------|---------------------------|  
|Tylko HTTP|http: *: 80:\*|/appTwo|`http://localhost/appTwo/`|  
|HTTP i inne niż HTTP|http: *: 80:\*<br /><br /> NET. TCP: 808:\*|/appTwo|`http://localhost/appTwo/`<br />`net.tcp://localhost/appTwo/`|  
|Tylko inne niż HTTP|NET. pipe: *|/appThree|`net.pipe://appThree/`|  
  
 Można również rozwiązać usługi i zasoby w aplikacji. W aplikacji zasoby aplikacji są rozkierowane względem podstawowej ścieżki aplikacji. Załóżmy na przykład, że lokacja w nazwie komputera contoso.com ma powiązania lokacji dla protokołów HTTP i net. TCP. Załóżmy również, że lokacja zawiera jedną aplikację znajdującą się w/Billing, która uwidacznia usługę w usłudze GetOrders. svc. Następnie, jeśli usługa GetOrders. svc uwidocznia punkt końcowy z względnym adresem SecureEndpoint, punkt końcowy usługi zostałby ujawniony przy użyciu następujących dwóch identyfikatorów URI:  
  
- `http://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
- `net.tcp://contoso.com/Billing/GetOrders.svc/SecureEndpoint`
  
## <a name="the-was-runtime"></a>Środowisko uruchomieniowe zostało uruchomione  
 Aplikacje są zorganizowane w lokacjach na potrzeby adresowania i zarządzania. W czasie wykonywania aplikacje są również pogrupowane w pule aplikacji. Pula aplikacji może mieć wiele różnych aplikacji z wielu różnych lokacji programu. Wszystkie aplikacje wewnątrz puli aplikacji korzystają ze wspólnego zestawu właściwości czasu wykonywania. Na przykład wszystkie są uruchamiane w tej samej wersji środowiska uruchomieniowego języka wspólnego (CLR) i wszystkie mają wspólną tożsamość procesu. Każda pula aplikacji odpowiada wystąpieniu procesu roboczego (w3wp.exe). Każda aplikacja zarządzana działająca w ramach udostępnionej puli aplikacji jest odizolowana od innych aplikacji za pomocą elementu AppDomain środowiska CLR.  
  
## <a name="see-also"></a>Zobacz też

- [Architektura aktywacji WAS](was-activation-architecture.md)
- [Konfigurowanie usługi WAS do użycia z programem WCF](configuring-the-wpa--service-for-use-with-wcf.md)
- [Instrukcje: instalowanie i konfigurowanie składników aktywacji programu WCF](how-to-install-and-configure-wcf-activation-components.md)
- [Instrukcje: hostowanie usługi WCF w usłudze WAS](how-to-host-a-wcf-service-in-was.md)
- [Funkcje hostingu sieci szkieletowej aplikacji systemu Windows Server](https://docs.microsoft.com/previous-versions/appfabric/ee677189(v=azure.10))
