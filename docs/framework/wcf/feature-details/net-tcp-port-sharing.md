---
title: Współużytkowanie portów w składniku Net.TCP
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: 37c3d7580b48552b841823933958267cea815fab
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33497155"
---
# <a name="nettcp-port-sharing"></a>Współużytkowanie portów w składniku Net.TCP
Windows Communication Foundation (WCF) zapewnia nowy protokół sieciach opartych na protokole TCP (net.tcp://) do komunikacji wysokiej wydajności. Usługi WCF wprowadza również nowy składnik systemu usługi udostępniania portów Net.TCP, który umożliwia porty net.tcp, które mają być udostępniane wielu procesom użytkownika.  
  
## <a name="background-and-motivation"></a>Tło i Motywacją  
 Protokół TCP/IP została wprowadzona, tylko niewielka liczba protokołów aplikacji wprowadzane z niego korzystać. Numery portów jest używany przez protokół TCP/IP do rozróżniania między aplikacjami, przypisując unikatowy 16-bitowy numer portu dla każdego protokołu aplikacji. Na przykład ruch HTTP jest obecnie standardowym by używał portu TCP 80 SMTP używa portu TCP 25 i FTP używa portów TCP 20 i 21. Inne aplikacje korzystające z protokołu TCP jako transportu wybrać inny numer portu dostępne przez Konwencję lub za pośrednictwem posiadanie normalizacji.  
  
 Używanie numerów portów do rozróżniania między aplikacjami wystąpiły problemy zabezpieczeń. Zapory zwykle są skonfigurowane do blokowania ruch TCP na wszystkich portach, z wyjątkiem kilku punktów wejścia dobrze znany, więc wdrożenie aplikacji korzystającej z portem niestandardowym jest często skomplikowany lub nawet niemożliwe z powodu obecności zapór firmowymi i prywatnymi. Aplikacje, które mogą komunikować się za pośrednictwem standardowych, dobrze znanych portów, które są już dozwolone zmniejszyć obszar ataków zewnętrznych. Wiele aplikacji w sieci wykorzystuje HTTP protokołu, ponieważ większość zapór są domyślnie skonfigurowane, aby zezwolić na ruch na porcie TCP 80.  
  
 HTTP. SYS modelu, w którym ruch na wiele aplikacji HTTP jest multipleksowany na pojedynczym portem TCP stał się standardowa na platformie systemu Windows. Zapewnia to wspólny punkt kontroli zapory Administratorzy, umożliwiając deweloperom aplikacji minimalizuje to koszt wdrożenia tworzenie nowych aplikacji, które mogą ułatwić za pomocą sieci.  
  
 Możliwość udostępniania portów dla wielu aplikacji HTTP dawna funkcji programu Internetowe usługi informacyjne (IIS). Jednak było tylko wraz z wprowadzeniem HTTP. SYS (odbiornika protokołu HTTP trybu jądra) z [!INCLUDE[iis601](../../../../includes/iis601-md.md)] który pełni został uogólniony tej infrastruktury. W rezultacie HTTP. SYS umożliwia udostępnianie portów TCP dedykowana dla ruchu HTTP procesów dowolnego użytkownika. Ta funkcja umożliwia współistnieć na tym samym komputerze fizycznych w oddzielnych, izolowane procesy podczas udostępniania infrastruktury sieciowej wymaganej do wysyłać i odbierać ruch przez TCP port 80 wiele aplikacji HTTP. Usługa udostępniania portów Net.TCP umożliwia portów net.tcp aplikacji do udostępniania tego samego typu.  
  
## <a name="port-sharing-architecture"></a>Architektura Udostępnianie portów  
 Architektura Udostępnianie portów w programie WCF ma trzy główne składniki:  
  
-   Proces roboczy: Żaden proces, komunikować się za pośrednictwem net.tcp:// przy użyciu udostępnionych portów.  
  
-   Transportu TCP usługi WCF: implementuje ten protokół net.tcp://.  
  
-   Usługa udostępniania portów Net.TCP: Umożliwia wielu procesów roboczych na współużytkowanie tego samego portu TCP.  
  
 Usługa udostępniania portów Net.TCP jest usługą systemu Windows trybu użytkownika, która akceptuje połączenia net.tcp:// imieniu procesów roboczych łączących się za jego pośrednictwem. Po odebraniu połączenia gniazda usługi współużytkowania portów przeprowadzający przychodzący strumień komunikatu do uzyskiwania adresów docelowego. Oparte na ten adres, usługi współużytkowania portów może kierować strumienia danych aplikacji, w której ostatecznie przetwarza je.  
  
 Gdy usługa WCF, która wykorzystuje net.tcp:// udostępniania portów, infrastruktura transportu TCP usługi WCF nie bezpośrednio otworzyć gniazda TCP w procesie aplikacji. Zamiast tego infrastruktura transportu rejestruje usługi adres podstawowy identyfikator URI (Uniform Resource) z usługi udostępniania portów Net.TCP i czeka na port udostępnianej usługi do nasłuchiwania wiadomości w jego imieniu.  Usługi współużytkowania portów wysyła komunikaty adresowane do usługi aplikacji podczas ich dostarczania.  
  
## <a name="installing-port-sharing"></a>Instalowanie współużytkowania portów  
 Usługa udostępniania portów Net.TCP jest dostępna we wszystkich systemach operacyjnych, które obsługują [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], ale usługa nie jest domyślnie włączona. Ze względów bezpieczeństwa administrator musi ręcznie włączyć usługi udostępniania portów Net.TCP przed pierwszym użyciem. Usługa udostępniania portów Net.TCP udostępnia opcje konfiguracji, dzięki którym można manipulować pewne cechy gniazda sieci właścicielem usługi współużytkowania portów. Aby uzyskać więcej informacji, zobacz [porady: Włączanie usługi udostępniania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Za pomocą aplikacji do udostępniania portów Net.tcp  
 Najprostszym sposobem na korzystanie z portu net.tcp:// udostępnianie aplikacji WCF jest ujawnia usługi za pomocą <xref:System.ServiceModel.NetTcpBinding> , a następnie włączyć usługi udostępniania portów Net.TCP przy użyciu <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwości.  
  
 Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [porady: Konfigurowanie usługi WCF na potrzeby współużytkowania portów użyj](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Ryzyko związane z współużytkowania portów  
 Chociaż usługi udostępniania portów Net.TCP zapewnia warstwę przetwarzania między aplikacjami i siecią, aplikacje używające Udostępnianie portów nadal powinien być zabezpieczony, tak, jakby były one bezpośrednio nasłuchiwanie w sieci. W szczególności aplikacje korzystające z Udostępnianie portów należy ocenić uprawnień procesów, w których są uruchamiane. Należy rozważyć uruchomienie aplikacji przy użyciu wbudowane konto Usługa sieciowa, która działa z minimalnym zestawem uprawnień procesów wymagane do komunikacji sieciowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Konfigurowanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/configuring-the-net-tcp-port-sharing-service.md)  
 [Hosting](../../../../docs/framework/wcf/feature-details/hosting.md)  
 [Instrukcje: konfigurowanie usługi WCF na potrzeby współużytkowania portów](../../../../docs/framework/wcf/feature-details/how-to-configure-a-wcf-service-to-use-port-sharing.md)  
 [Instrukcje: włączanie usługi współużytkowania portów Net.TCP](../../../../docs/framework/wcf/feature-details/how-to-enable-the-net-tcp-port-sharing-service.md)
