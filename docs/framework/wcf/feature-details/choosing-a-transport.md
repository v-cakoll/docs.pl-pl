---
title: Wybieranie transportu
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
caps.latest.revision: 25
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 7b051cdeebf83b34b6e503d8d9cb54a38a46a2a6
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="choosing-a-transport"></a>Wybieranie transportu
W tym temacie omówiono kryteriów wyboru spośród trzech głównych transportów uwzględnionych w [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)]: HTTP, TCP i nazwane potoki. [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] zawiera również transportu MSMQ (MSMQ), ale ten dokument nie obejmuje usługi kolejkowania komunikatów.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Model programowania oddziela operacji punktu końcowego (jak wyrażony w kontrakcie usługi) od mechanizm transportu, który łączy dwa punkty końcowe. Zapewnia to elastyczność, aby określić sposób ujawniać usług do sieci.  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], określ sposób transferu danych za pośrednictwem sieci między punktami końcowymi za pomocą *powiązania*, która składa się z sekwencji *elementów wiązania*. Transport jest reprezentowany przez element powiązania transportu, który należy do powiązania. Powiązanie zawiera elementów powiązania protokołu opcjonalnych, takich jak zabezpieczeń, element powiązania kodera wiadomości wymagane i element powiązania transportu wymagane. Transport wysłania lub odebrania serializacji formularza wiadomości do lub z innej aplikacji.  
  
 Jeśli musisz nawiązać istniejącego klienta lub serwera, nie masz wybór o przy użyciu danego transportu. Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] usług można udostępnić za pośrednictwem wiele punktów końcowych, każda z innego transportu. W przypadku pojedynczego transportu nie obejmuje określonej grupy odbiorców dla usługi, należy rozważyć, udostępnianie przez wiele punktów końcowych usługi. Aplikacje klienckie można użyć punktu końcowego, który jest najlepsze dla nich.  
  
 Po wybraniu transportu, musisz wybrać powiązania, które korzysta z niego. Możesz wybrać powiązania dostarczane przez system (zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md)), lub można utworzyć wiązania niestandardowego (zobacz [niestandardowego powiązania](../../../../docs/framework/wcf/extending/custom-bindings.md)). Można też utworzyć własne powiązania. Aby uzyskać więcej informacji, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Zalety każdego transportu  
 W tej sekcji opisano główne powody wyboru jednego z trzech transportów głównego, w tym wybór między nimi wykres decyzji szczegółowe.  
  
### <a name="when-to-use-http-transport"></a>Kiedy należy używać transportu HTTP  
 HTTP jest protokołem żądanie/odpowiedź między klientami a serwerami. Najbardziej typowe aplikacja składa się z klientów w przeglądarkach sieci Web, które komunikują się z serwerem sieci Web. Klient wysyła żądanie do serwera, który oczekuje na komunikaty żądania klienta. Kiedy serwer odbiera żądanie, zwraca odpowiedź, który zawiera stan żądania. W przypadku powodzenia jest zwracana opcjonalna danych, takich jak strony sieci Web, komunikat o błędzie lub innych informacji. [!INCLUDE[crabout](../../../../includes/crabout-md.md)] Protokół HTTP, zobacz [HTTP - Hypertext Transfer Protocol](http://go.microsoft.com/fwlink/?LinkId=94858).  
  
 Protokół HTTP nie jest opartego na połączeniach — po wysłaniu odpowiedzi Państwa nie jest obsługiwany. Do obsługi transakcji wielu stron, aplikacji, muszą zostać zachowane wszystkie niezbędne stanu.  
  
 W [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], HTTP transport powiązania jest zoptymalizowana pod kątem współdziałania z starsze niż[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] systemów. Jeśli używasz wszystkich uczestników komunikacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)], TCP lub nazwanym powiązania na podstawie potoków są szybsze. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetTcpBinding> i <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>Kiedy należy używać transportu TCP  
 TCP jest usługą dostarczania opartego na połączeniach, zorientowanych strumieniowo z detekcji i korekcji błędów na trasie. *Opartego na połączeniach* oznacza, że komunikacji między hostami ustanowiono przed rozpoczęciem wymiany danych. Host jest dowolnego urządzenia w sieci TCP/IP identyfikowana na podstawie logicznego adresu IP.  
  
 TCP zapewnia dostarczania danych niezawodnych i łatwość użycia. W szczególności TCP powiadamia nadawca dostarczania pakietów gwarantuje, że pakiety są dostarczane w takiej samej kolejności, w jakiej są wysyłane, ponownie wysyła pakiety utracone i zapewnia, że pakiety danych nie są duplikowane. Zauważ, że to niezawodne dostarczanie stosuje się między dwoma węzłami TCP/IP i nie jest odpowiednikiem *WS-ReliableMessaging*, którego dotyczy między punktami końcowymi, bez względu na liczbę węzłów pośredniej mogą obejmować.  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Transportu TCP jest zoptymalizowana pod kątem scenariusza, w którym korzystają z obu końców komunikacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]. To powiązanie jest najszybszym [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] powiązania dla scenariuszy dotyczących komunikacji między kilka różnych maszyn. Użyj wymiany wiadomości <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> dla transferu komunikatów zoptymalizowane. TCP zapewnia komunikację dupleksową i dlatego może służyć do zaimplementowania kontrakty dwukierunkowe, nawet jeśli klient znajduje się za translatora adresów sieciowych (NAT).  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Kiedy należy używać transportu nazwanego potoku  
 Nazwany potok jest obiekt jądra systemu operacyjnego Windows, takich jak sekcji pamięci współdzielonej procesy mogą używać do komunikacji. Nazwany potok zawiera nazwę i może służyć do jednokierunkowe lub dupleks komunikacji między procesami na jednym komputerze.  
  
 Kiedy komunikacja jest wymagany między różnymi [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] aplikacji na jednym komputerze i chcesz zapobiec cała komunikacja z innego komputera, a następnie użyj transportu nazwanych potoków. Dodatkowe ograniczenie jest, że procesów uruchomionych z pulpitu zdalnego systemu Windows mogą być ograniczone do tej samej sesji pulpitu zdalnego systemu Windows, chyba że mają podwyższony poziom uprawnień.  
  
> [!WARNING]
>  Jeśli używasz transportu nazwanego potoku z rezerwację adresu URL słabe symbolu wieloznacznego w wielu lokacjach hostowanych w usługach IIS, może wystąpić następujący błąd: Wystąpił błąd w usłudze aktywacji "NetPipeActivator" protokołu "net.pipe" podczas próby nasłuchiwania dla witryny "2", w związku z tym protokołem jest witryny tymczasowo wyłączone. Zawiera komunikat wyjątku, aby uzyskać więcej informacji. Adres URL: WeakWildcard:net.pipe:/\<nazwa komputera > / stanu: wyjątek ConflictingRegistration: Nazwa procesu: SMSvcHost identyfikator procesu: 1076\  
  
## <a name="decision-points-for-choosing-a-transport"></a>Punkty decyzyjne dotyczące wybierania transportu  
 W poniższej tabeli opisano typowe punkty decyzyjne używane do wybierania transportu. Należy rozważyć wszelkie dodatkowe atrybuty i transportów, które mają zastosowanie do aplikacji. Zidentyfikuj atrybutów, które są ważne w przypadku aplikacji, zidentyfikować transporty favorably skojarzenia z każdym z atrybutów, a następnie wybierz transportów, które najlepiej pracować z zestawu atrybutów.  
  
|Atrybut|Opis|Transporty ich drużyna jest faworytem|  
|---------------|-----------------|------------------------|  
|Diagnostyka|Diagnostyka umożliwiają automatycznie Wykryj problemy z łącznością z transportu. Wszystkich transportów obsługi wysłać informacje o błędzie Wstecz, który opisuje łączności. Jednak [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] nie zawiera narzędzia diagnostyczne do badania problemów dotyczących sieci.|Brak|  
|Hosting|Wszystkie [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] punkty końcowe muszą znajdować się wewnątrz aplikacji. [!INCLUDE[iis601](../../../../includes/iis601-md.md)] i wcześniejsze wersje obsługują tylko hostingu aplikacji, które używają protokołu HTTP. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], dodano obsługę wszystkich hosting [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transportu, w tym TCP i nazwane potoki. Aby uzyskać więcej informacji, zobacz [hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) i [Hosting w usłudze aktywacji procesów systemu Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|Inspekcji|Kontroli jest możliwość wyodrębnić i przetworzyć informacji z komunikatów podczas przesyłania. Protokół HTTP oddziela routingu i kontroli informacji ze źródła danych, ułatwiając narzędzi, które kontrolują i analizować wiadomości do kompilacji. Transporty łatwych do zbadania może również wymagać mniejszej mocy przetwarzania w urządzeniach sieciowych. Poziom zabezpieczeń używane wpływ czy mogą być kontrolowane wiadomości.|HTTP|  
|Czas oczekiwania|Opóźnienie to minimalny czas wymagany do ukończenia wymiany wiadomości. Wszystkie operacje sieciowe mają więcej lub mniej opóźnienie w zależności od wyboru transportu. Za pomocą transportu, którego natywnego wymiany komunikatów jest żądanie odpowiedź, takich jak HTTP, może spowodować dodatkowe opóźnienia z powodu wymuszonego korelacji wiadomości przy użyciu komunikacji dupleksowej lub jednokierunkowe. W takiej sytuacji należy wziąć pod uwagę przy użyciu transportu, w których natywnego wymiany komunikatów jest dupleksowy, takie jak protokół TCP.|TCP, o nazwie<br /><br /> potoku|  
|Reach|Zasięg transportu odzwierciedla, jak stanie transport jest na łączenie się z innymi systemami. Transportu nazwanego potoku osiągnął bardzo mało; można połączyć tylko z usługami uruchomionymi na tym samym komputerze. Transportu TCP i HTTP ma znakomity reach i koloru niektóre konfiguracje translatora adresów Sieciowych i zapory. Aby uzyskać więcej informacji, zobacz [Praca z translatorami adresów sieciowych i zaporami](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Zabezpieczenia|Bezpieczeństwo jest możliwość ochrony wiadomości podczas transferu podając poufność, integralność lub uwierzytelniania. Poufność chroni wiadomość z badane, integralność chroni komunikat przed modyfikacją i uwierzytelniania daje gwarancje o nadawcy i adresata wiadomości.<br /><br /> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] obsługuje transfer zabezpieczeń zarówno na poziomie komunikatu i transportu. Zabezpieczenia komunikatów Redaguj za pomocą transportu, jeśli transport obsługuje tryb buforowany transferu. Obsługa zabezpieczeń transportu różni się w zależności od wybranego transportu. HTTP, TCP i transportu nazwanego potoku ma uzasadnione parzystości w ich obsługę zabezpieczeń transportu.|Wszystkie|  
|Przepływność|Przepływność mierzy ilość danych, które mogą być przesyłane i przetwarzane w danym okresie czasu. Takie jak czas oczekiwania wybranego transportu może mieć wpływ na przepustowość dla operacji usługi. DSI oznacza optymalne wykorzystanie przepustowości transportu wymaga zminimalizować koszty przesyłania zawartości, jak również zminimalizować czas oczekiwania na wymiany komunikatów zakończyć. TCP i transportu nazwanego potoku Dodaj małego obciążenia do treści wiadomości i obsługuje natywnego kształtu dupleksowy, skraca czas oczekiwania w odpowiedzi na wiadomość.|TCP, nazwany potok|  
|Narzędzia|Narzędzia reprezentuje aplikacji innych firm obsługę protokołu dla rozwoju, Diagnostyka hosting i innych działań. Narzędzia i oprogramowania, aby pracować przy użyciu protokołu HTTP oznacza szczególnie duże inwestycji.|HTTP|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.ServiceModel.BasicHttpBinding>  
 <<!--zz xref:System.ServiceModel.WsHttpBinding --> `xref:System.ServiceModel.WsHttpBinding`>  
  <<!--zz <xref:System.ServiceModel.WsDualHttpBinding> --> `System.ServiceModel.WsDualHttpBinding`
 <<!--zz <xref:System.ServiceModel.WsFederationHttpBinding>  --> `System.ServiceModel.WsFederationHttpBinding` <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
 <xref:System.ServiceModel.NetTcpBinding>  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
 <xref:System.ServiceModel.NetNamedPipeBinding>  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
 [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)  
 [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [Tworzenie powiązań zdefiniowanych przez użytkownika](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
