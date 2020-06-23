---
title: Współużytkowanie portów w składniku Net.TCP
description: Dowiedz się więcej na temat protokołu opartego na protokole TCP na potrzeby komunikacji o wysokiej wydajności i usługi umożliwiającej współużytkowanie portów przez wiele procesów użytkownika w programie WCF.
ms.date: 03/30/2017
helpviewer_keywords:
- port activation [WCF]
- port sharing [WCF]
ms.assetid: f13692ee-a179-4439-ae72-50db9534eded
ms.openlocfilehash: a9579c588906f509dd835d3c9b25571495d147e0
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245248"
---
# <a name="nettcp-port-sharing"></a>Współużytkowanie portów w składniku Net.TCP
Windows Communication Foundation (WCF) udostępnia nowy protokół sieciowy oparty na protokole TCP (NET. TCP://) na potrzeby komunikacji o wysokiej wydajności. W programie WCF wprowadzono również nowy składnik systemu, usługę udostępniania portów Net. TCP, która umożliwia współużytkowanie portów Net. TCP między wieloma procesami użytkownika.  
  
## <a name="background-and-motivation"></a>Tło i motywacja  
 Po pierwszym wprowadzeniu protokołu TCP/IP jest używana tylko niewielka liczba protokołów aplikacji. Protokół TCP/IP używa numerów portów do rozróżniania między aplikacjami przez przypisanie unikatowego numeru portu 16-bitowego do każdego protokołu aplikacji. Na przykład obecnie ruch HTTP jest standardem używanym do korzystania z portu TCP 80, SMTP używa portu 25 TCP, a FTP używa portów TCP 20 i 21. Inne aplikacje korzystające z protokołu TCP jako transportu mogą wybrać inny dostępny numer portu (według Konwencji lub do formalnej normalizacji).  
  
 Używanie numerów portów do rozróżniania między aplikacjami ma problemy z zabezpieczeniami. Zapory są zwykle skonfigurowane do blokowania ruchu TCP na wszystkich portach z wyjątkiem kilku dobrze znanych punktów wejścia, dlatego wdrożenie aplikacji używającej niestandardowego portu jest często skomplikowane lub nawet niemożliwe ze względu na obecność firmowych i osobistych zapór. Aplikacje, które mogą komunikować się za pośrednictwem standardowych, dobrze znanych portów, które są już dozwolone, zmniejszają powierzchnię zewnętrznego ataku. Wiele aplikacji sieciowych korzysta z protokołu HTTP, ponieważ większość zapór jest domyślnie skonfigurowanych do zezwalania na ruch na porcie TCP 80.  
  
 Model HTTP.SYS, w którym ruch dla wielu różnych aplikacji HTTP jest przybierany na jeden port TCP, stał się standardem na platformie systemu Windows. Zapewnia to typowy punkt kontroli administratorów zapory, a jednocześnie pozwala deweloperom aplikacji zminimalizować koszty wdrożenia nowych aplikacji, które mogą korzystać z sieci.  
  
 Możliwość udostępniania portów w wielu aplikacjach HTTP była funkcją Internet Information Services (IIS). Jednak było to tylko wprowadzenie HTTP.SYS (odbiornik protokołu HTTP trybu jądra) z usługami IIS 6,0, że ta infrastruktura była w pełni uogólniona. W efekcie HTTP.SYS zezwala dowolnym procesom użytkownika na współużytkowanie portów TCP dedykowanych dla ruchu HTTP. Ta funkcja pozwala wielu aplikacjom HTTP współistnieć na tym samym komputerze fizycznym w oddzielnych, izolowanych procesach, udostępniając infrastrukturę sieci wymaganą do wysyłania i odbierania ruchu przez port TCP 80. Usługa udostępniania portów Net. TCP włącza ten sam typ udostępniania portów dla aplikacji net. TCP.  
  
## <a name="port-sharing-architecture"></a>Architektura udostępniania portów  
 Architektura udostępniania portów w programie WCF ma trzy główne składniki:  
  
- Proces roboczy: każdy proces komunikuje się za pośrednictwem net. TCP://przy użyciu portów udostępnionych.  
  
- Transport TCP WCF: implementuje protokół net. TCP://Protocol.  
  
- Usługa udostępniania portów Net. TCP: umożliwia wielu procesom roboczym współużytkowanie tego samego portu TCP.  
  
 Usługa udostępniania portów Net. TCP to usługa systemu Windows w trybie użytkownika akceptująca net. TCP://Connections w imieniu procesów roboczych, które nawiązują połączenie. Po nadejściu połączenia gniazda usługa udostępniania portów sprawdza strumień komunikatów przychodzących, aby uzyskać swój adres docelowy. Na podstawie tego adresu usługa udostępniania portów może kierować strumień danych do aplikacji, która ostatecznie ją przetwarza.  
  
 W przypadku otwarcia usługi WCF korzystającej z programu net. TCP://przydzielania portów Infrastruktura transportu TCP programu WCF nie otwiera bezpośrednio gniazda TCP w procesie aplikacji. Zamiast tego infrastruktura transportowa rejestruje adres podstawowy usługi Uniform Resource Identifier (URI) za pomocą usługi udostępniania portów Net. TCP i czeka na nasłuchiwanie przez usługę udostępniania portów komunikatów w jej imieniu.  Usługa udostępniania portów wysyła komunikaty do usługi aplikacji podczas ich odbierania.  
  
## <a name="installing-port-sharing"></a>Instalowanie udostępniania portów  
 Usługa udostępniania portów Net. TCP jest dostępna we wszystkich systemach operacyjnych, które obsługują model WinFX, ale usługa nie jest domyślnie włączona. Ze względów bezpieczeństwa administrator musi ręcznie włączyć usługę udostępniania portów Net. TCP przed pierwszym użyciem. Usługa udostępniania portów Net. TCP udostępnia opcje konfiguracji, które umożliwiają manipulowanie wieloma charakterystykami gniazd sieciowych należących do usługi udostępniania portów. Aby uzyskać więcej informacji, zobacz [jak: Włączanie usługi udostępniania portów Net. TCP](how-to-enable-the-net-tcp-port-sharing-service.md).  
  
## <a name="using-nettcp-port-sharing-in-an-application"></a>Używanie udostępniania portów Net. TCP w aplikacji  
 Najprostszym sposobem korzystania z usługi net. TCP://udostępniania portów w aplikacji WCF jest udostępnienie usługi przy użyciu, <xref:System.ServiceModel.NetTcpBinding> a następnie umożliwienie usłudze udostępniania portów Net. TCP przy użyciu <xref:System.ServiceModel.NetTcpBinding.PortSharingEnabled%2A> właściwości.  
  
 Aby uzyskać więcej informacji o tym, jak to zrobić, zobacz [jak: Konfigurowanie usługi WCF do korzystania z udostępniania portów](how-to-configure-a-wcf-service-to-use-port-sharing.md).  
  
## <a name="security-implications-of-port-sharing"></a>Implikacje zabezpieczeń dotyczące udostępniania portów  
 Mimo że usługa udostępniania portów Net. TCP zapewnia warstwę przetwarzania między aplikacjami i siecią, aplikacje korzystające z udostępniania portów powinny nadal być zabezpieczone tak, jakby były bezpośrednio nasłuchiwani w sieci. W przypadku aplikacji korzystających z udostępniania portów należy oszacować uprawnienia procesu, w których są uruchamiane. Rozważ uruchomienie aplikacji przy użyciu wbudowanego konta usługi sieciowej, które działa z minimalnym zestawem uprawnień procesu wymaganych do komunikacji sieciowej.  
  
## <a name="see-also"></a>Zobacz też

- [Konfigurowanie usługi współużytkowania portów Net.TCP](configuring-the-net-tcp-port-sharing-service.md)
- [Hosting](hosting.md)
- [Instrukcje: konfigurowanie usługi WCF na potrzeby współużytkowania portów](how-to-configure-a-wcf-service-to-use-port-sharing.md)
- [Instrukcje: włączanie usługi współużytkowania portów Net.TCP](how-to-enable-the-net-tcp-port-sharing-service.md)
