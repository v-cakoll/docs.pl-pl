---
title: Współużytkowanie portów w składniku Net.TCP
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: e191dc62368fc9c16bd58efd30dd1a3769d2bb88
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54540315"
---
# <a name="nettcp-port-sharing"></a>Współużytkowanie portów w składniku Net.TCP
Windows Communication Foundation (WCF) zapewnia nowy Protokół sieci oparte na protokole TCP (net.tcp://) komunikację o wysokiej wydajności. Usługi WCF wprowadza również nowy składnik systemu, usługi udostępniania portów Net.TCP, która umożliwia użycie portów net.tcp być współużytkowane przez wiele procesów użytkownika.  
  
## <a name="background-and-motivation"></a>Tło i motywację  
 Protokół TCP/IP została wprowadzona, tylko niewielka liczba protokołów aplikacji tworzone z niego korzystać. TCP/IP używany numery portów do rozróżnienia między aplikacjami, przypisując unikatowy 16-bitowy numer portu dla każdego protokołu aplikacji. Na przykład ruch HTTP jest obecnie standardowym by używał portu TCP 80 SMTP używa portu TCP 25 i protokół FTP używa portów TCP 20 i 21. Inne aplikacje korzystające z protokołu TCP jako transportu wybrać inny numer portu dostępne, zgodnie z Konwencją lub za pośrednictwem formalne normalizacji.  
  
 Za pomocą numerów portów do rozróżniania między aplikacjami wystąpiły problemy z zabezpieczeniami. Ogólnie zapór zablokować ruch TCP na wszystkich portach, z wyjątkiem kilku punktów wejścia dobrze znanego, dzięki czemu wdrożenie aplikacji korzystającej z niestandardowego portu jest często skomplikowany lub nawet niemożliwe z powodu obecności zapory firmowymi i prywatnymi. Aplikacje, które mogą komunikować się za pośrednictwem standardowych, dobrze znanych portów, które są już dozwolone, ale zmniejszyć obszar ataków zewnętrznych. Wiele aplikacji sieciowych, korzystaj z HTTP protokołu, ponieważ większość zapór są domyślnie skonfigurowane, aby zezwolić na ruch na porcie 80 protokołu TCP.  
  
 HTTP. SYS modelu, w którym ruch dla wielu różnych aplikacji protokołu HTTP jest multipleksowany do jednego portu TCP stał się standardowego dla Windows platform. Dzięki temu można wspólnego punktu kontroli zapory Administratorzy, zapewniając deweloperom aplikacji w celu zminimalizowania kosztów wdrożenia, tworzenia nowych aplikacji, które mogą ułatwić korzystanie z sieci.  
  
 Możliwość udostępniania portów dla wielu aplikacji HTTP dawna funkcji programu Internetowe usługi informacyjne (IIS). Jednakże było tylko w przypadku wprowadzenia protokołu HTTP. SYS (tryb jądra odbiornika protokołu HTTP) przy użyciu [!INCLUDE[iis601](../../../../includes/iis601-md.md)] pełni uogólniony tej infrastruktury. W efekcie HTTP. SYS umożliwia użytkownika jest swobodny procesom współużytkowanie portów TCP dedykowany dla ruchu HTTP. Ta funkcja umożliwia wielu aplikacji HTTP, które będą mogły nadal współistnieć na tym samym komputerze fizycznych w oddzielnych, izolowane procesów podczas udostępniania infrastruktury sieciowej, wymagane do wysyłania i odbierania ruchu za pośrednictwem portu TCP 80. Usługi udostępniania portów Net.TCP umożliwia ten sam typ udostępniania dla aplikacji net.tcp portów.  
  
## <a name="port-sharing-architecture"></a>Architektura współużytkowania portów  
 Architektura współużytkowanie portów w programie WCF ma trzy główne składniki:  
  
-   Proces roboczy: Żaden proces, komunikacji za pośrednictwem net.tcp:// przy użyciu udostępnionych portów.  
  
-   Transportu TCP usługi WCF: Implementuje protokół net.tcp://.  
  
-   Usługa udostępniania portów Net.TCP: Umożliwia wielu procesów roboczych na udostępnianie tego samego portu TCP.  
  
 Usługi udostępniania portów Net.TCP jest usługa Windows trybu użytkownika, która akceptuje połączenia net.tcp:// imieniu procesów roboczych, łączących się za jego pośrednictwem. Po odebraniu połączenia z gniazdem współużytkowania portów bada strumienia komunikatów przychodzących w celu uzyskania adresu docelowego. Oparte na ten adres, port udostępnianej usługi może kierować strumień danych do aplikacji, które ostatecznie przetwarza je.  
  
 Gdy usługa WCF, która używa net.tcp:// udostępniania portów, infrastruktura transportu TCP usługi WCF nie bezpośrednio otworzyć gniazda TCP w procesie aplikacji. Zamiast tego infrastruktura transportu rejestruje usługi adres podstawowy identyfikator URI (Uniform Resource) za pomocą usługi udostępniania portów Net.TCP i czeka na port udostępnianej usługi, aby nasłuchiwać komunikatów w jej imieniu.  Port udostępnianej usługi wysyła komunikaty adresowane do usługi aplikacji, podczas ich dostarczania.  
  
## <a name="installing-port-sharing"></a>Instalowanie współużytkowania portów  
 Usługi udostępniania portów Net.TCP jest dostępna we wszystkich systemach operacyjnych, które obsługują [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], ale usługa nie jest domyślnie włączona. Ze względów bezpieczeństwa administrator musi ręcznie włączyć usługi udostępniania portów Net.TCP przed pierwszym użyciu. Usługi udostępniania portów Net.TCP udostępnia opcje konfiguracji, które umożliwiają manipulowanie pewne cechy gniazd sieciowych należących do współużytkowania portów. Aby uzyskać więcej informacji, zobacz [jak: Włączanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Przy użyciu portów Net.tcp, udostępnianie w aplikacji  
 Najprostszym sposobem na korzystanie z portu net.tcp:// udostępnianie w aplikację WCF jest do udostępnienia usługi za pomocą <xref:System.ServiceModel.NetTcpBinding> a następnie włączyć usługi udostępniania portów Net.TCP przy użyciu <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwości.  
  
 Aby uzyskać więcej informacji na temat jak to zrobić, zobacz [jak: Konfigurowanie usługi WCF na potrzeby współużytkowania portów](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Ryzyko związane z współużytkowania portów  
 Chociaż usługi udostępniania portów Net.TCP warstwy przetwarzania między aplikacjami i sieci, aplikacje, które używają współużytkowania portów nadal powinien być zabezpieczony, tak, jakby były one bezpośrednio nasłuchiwanie w sieci. Ściślej mówiąc aplikacje, które używają współużytkowania portów należy ocenić uprawnień procesów, na których działają. Rozważ uruchomienie aplikacji przy użyciu wbudowanego konta Usługa sieciowa działa z minimalnym zestawem uprawnień procesów wymaganych do komunikacji sieciowej.  
  
## <a name="see-also"></a>Zobacz także
- [Konfigurowanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)
- [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md)
- [Instrukcje: Konfigurowanie usługi WCF na potrzeby współużytkowania portów](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)
- [Instrukcje: Włączanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
