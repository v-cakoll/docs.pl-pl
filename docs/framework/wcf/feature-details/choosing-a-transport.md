---
title: Wybieranie transportu
ms.date: 03/30/2017
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
ms.openlocfilehash: 611e8df29b37efd880ee1d19515697d899e4fa7e
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402157"
---
# <a name="choosing-a-transport"></a>Wybieranie transportu
W tym temacie omówiono kryteria wyboru spośród trzech głównych transportu, zawartych w Windows Communication Foundation (WCF): HTTP, TCP i nazwane potoki. Zawiera również WCF transportu MSMQ (MSMQ), ale ten dokument nie obejmuje usługi kolejkowania komunikatów.  
  
 Model programowania WCF oddziela operacje punktu końcowego (jak wyrażone w kontrakcie usługi) od mechanizm transportu, który łączy dwa punkty końcowe. Zapewnia to elastyczność, aby określić, jak udostępnić swoje usługi w sieci.  
  
 W programie WCF, możesz określić sposób transferu danych za pośrednictwem sieci między punktami końcowymi za pomocą *powiązania*, która składa się z sekwencji *elementów wiązania*. Transport jest reprezentowany przez element powiązania transportu, który jest częścią powiązania. Powiązanie zawiera elementy powiązania protokołu opcjonalne, takie jak zabezpieczenia, element powiązania kodera komunikatów wymagane i element powiązania transportu wymagane. Transport wysyłane lub odbierane z postaci serializowanej wiadomości do lub z innej aplikacji.  
  
 Jeśli musisz nawiązać istniejącego klienta lub serwera, możesz nie mieć wyboru o korzystaniu z danego transportu. Jednak usług WCF mogą być dostępne za pośrednictwem wielu punktów końcowych, każdy z innego transportu. W przypadku pojedynczego transportu nie obejmuje odbiorców dla Twojej usługi, należy rozważyć, udostępnianie usługi za pośrednictwem wielu punktów końcowych. Aplikacje klienckie mogą następnie używać punktu końcowego, który jest najlepsze dla nich.  
  
 Po wybraniu transportu, musisz wybrać powiązania, które go używa. Możesz wybrać powiązania dostarczane przez system (zobacz [powiązania System-Provided](../../../../docs/framework/wcf/system-provided-bindings.md)), możesz też skompilować własne powiązania niestandardowego (zobacz [powiązań niestandardowych](../../../../docs/framework/wcf/extending/custom-bindings.md)). Można również utworzyć własne powiązania. Aby uzyskać więcej informacji, zobacz [powiązania Creating User-Defined](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Korzyści wynikające z każdego transportu  
 W tej sekcji opisano główne powody wyboru jednej z trzech transportów głównego, łącznie z wykresu decyzji szczegółowe, dotyczące wybierania między nimi.  
  
### <a name="when-to-use-http-transport"></a>Kiedy należy używać transportu HTTP  
 HTTP jest protokół żądania/odpowiedzi między klientami a serwerami. Najczęściej aplikacja składa się z klientów w przeglądarkach sieci Web, które komunikują się z serwerem sieci Web. Klient wysyła żądanie do serwera, która nasłuchuje komunikatów żądań klientów. Gdy serwer otrzymuje żądania, zwraca odpowiedź, który zawiera stan żądania. Jeśli to się powiedzie, jest zwracany opcjonalnymi danymi, takich jak strony sieci Web, komunikat o błędzie lub inne informacje. Aby uzyskać więcej informacji na temat protokołu HTTP, zobacz [HTTP - Hypertext Transfer Protocol](https://go.microsoft.com/fwlink/?LinkId=94858).  
  
 Protokół HTTP nie jest opartego na połączeniach — po wysłaniu odpowiedzi nie jest zachowywana. Do obsługi transakcji wielu stron, aplikacja musi utrwalić wszystkie niezbędne stanu.  
  
 W programie WCF, transportu HTTP powiązania zoptymalizowana pod kątem współdziałania z systemów starszych niż WCF. Jeśli wszystkie strony komunikujące się z usługi WCF, TCP lub nazwane powiązania na podstawie potoków są realizowane szybciej. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetTcpBinding> i <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>Kiedy należy używać transportu TCP  
 Protokół TCP jest usługa dostarczania opartego na połączeniach, zorientowane na strumień o wykrywanie błędów end-to-end i korekty. *Opartego na połączeniach* oznacza, że komunikacja między hostami ustanowiono przed rozpoczęciem wymiany danych. Host jest dowolne urządzenie w sieci TCP/IP identyfikowane za pomocą adresu IP w logiczne.  
  
 Protokół TCP zapewnia dostarczanie danych niezawodne i łatwość użycia. W szczególności TCP powiadamia nadawcy dostarczania pakietów gwarantuje, że pakiety są dostarczane w tej samej kolejności, w której są wysyłane ponownie wysyła utraty pakietów i gwarantuje, że pakiety danych nie są duplikowane. Pamiętaj, że to niezawodne dostarczanie stosuje się między dwoma węzłami TCP/IP nie jest tak samo jak *WS-ReliableMessaging*, którego dotyczy między punktami końcowymi, niezależnie od tego, ile węzły pośrednie mogą obejmować.  
  
 Warstwy transportowej WCF TCP jest zoptymalizowany pod kątem scenariusza, w którym obu końcach komunikacji są przy użyciu usługi WCF. To powiązanie jest najszybszy powiązania WCF dla scenariuszy dotyczących komunikacji między różnych komputerach. Komunikat wymienia użyj <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> do transferu wiadomości zoptymalizowane. Protokół TCP zapewnia komunikację dupleksową, a tym samym może być używana do zaimplementowania kontrakty dwukierunkowe, nawet jeśli klient znajduje się za zaporą translatora adresów sieciowych (NAT).  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Kiedy należy używać transportu nazwanego potoku  
 Nazwany potok jest obiekt jądra systemu operacyjnego Windows, takich jak części pamięci współużytkowanej, używanego przez procesy do komunikacji. Nazwany potok o nazwie i może służyć do komunikacji jednokierunkowej lub dwukierunkowego między procesami na jednym komputerze.  
  
 Gdy komunikacja jest wymagany między różnymi aplikacjami usługi WCF na jednym komputerze, a chcesz uniemożliwić cała komunikacja z innego komputera, następnie używać transportu do potoków nazwanych. Dodatkowych ograniczeń jest, czy procesów uruchomionych z pulpitu zdalnego Windows może być ograniczony do tej samej sesji usług pulpitu zdalnego Windows, chyba że mają podwyższony poziom uprawnień.  
  
> [!WARNING]
>  Korzystając z transportu nazwanego potoku przy użyciu symboli wieloznacznych słabe rezerwację adresu URL, na wiele witryn hostowanych w usługach IIS, może wystąpić następujący błąd: Wystąpił błąd w usłudze aktywacji NetPipeActivator, protokołu "net.pipe" podczas próby nasłuchiwania dla witryny "2", dlatego protokół jest wyłączona dla witryny tymczasowo. Wyświetlony komunikat o wyjątku, aby uzyskać więcej informacji. ADRES URL: WeakWildcard:net.pipe:/\<nazwa komputera > / Status: ConflictingRegistration wyjątek:  Nazwa procesu: Identyfikator procesu SMSvcHost: 1076\  
  
## <a name="decision-points-for-choosing-a-transport"></a>Decyzje dotyczące wybierania transportu  
 W poniższej tabeli opisano typowe punkty decyzyjne używane do wybierania transportu. Należy rozważyć wszelkie dodatkowe atrybuty i transportu, które są stosowane do aplikacji. Identyfikować atrybuty, które są istotne dla twojej aplikacji, zidentyfikować transportów, które kojarzą favorably z każdego z atrybutów, a następnie wybierz transportu, które najlepiej przy użyciu zestawu atrybutów.  
  
|Atrybut|Opis|Faworytem transportu|  
|---------------|-----------------|------------------------|  
|Diagnostyka|Diagnostyka pozwalają wykryć problemy z łącznością transportu. Wszystkich transportów obsługuje możliwość wysyłania informacji wstecz błędów łączności. Usługi WCF nie zawiera jednak narzędzia diagnostyczne badania problemów z siecią.|Brak|  
|Hosting|Wszystkie punkty końcowe WCF musi być hostowany w aplikacji. Usługi IIS 6.0 i starsze wersje obsługują tylko hostowanie aplikacji, które używają protokołu HTTP. Na [!INCLUDE[wv](../../../../includes/wv-md.md)], pomocy technicznej zostaną dodane do obsługi wszystkich transportów WCF, w tym TCP i nazwane potoki. Aby uzyskać więcej informacji, zobacz [hostowanie przez Internetowe usługi informacyjne](../../../../docs/framework/wcf/feature-details/hosting-in-internet-information-services.md) i [Hosting w usłudze aktywacji procesów Windows](../../../../docs/framework/wcf/feature-details/hosting-in-windows-process-activation-service.md).|HTTP|  
|Inspekcja|Inspekcja jest możliwość wyodrębniania i przetwarzania informacji z komunikatów podczas transmisji. Protokół HTTP oddziela routingu i kontrola informacji na podstawie danych, ułatwiając tworzenie narzędzi, które sprawdzanie i analizowania komunikatów. Transporty, które można łatwo sprawdzić może również wymagać mniejszej mocy obliczeniowej w urządzeniach sieciowych. Poziom zabezpieczeń używane na środowisko, czy komunikaty mogą być kontrolowane.|HTTP|  
|Czas oczekiwania|Opóźnienie jest minimalna ilość czasu wymaganego do ukończenia wymiany wiadomości. Wszystkie operacje sieci mają więcej lub mniej opóźnienia w zależności od wybranego transportu. Przy użyciu komunikacji dupleksu lub jednokierunkowe za pomocą transportu, w których wymiany natywny komunikat jest żądanie odpowiedź, takich jak HTTP, może spowodować, że dodatkowe opóźnienie z powodu wymuszonego korelacji wiadomości. W takiej sytuacji należy rozważyć użycie transportu, w których wymiany natywny komunikat jest dupleksowy, takich jak protokół TCP.|TCP, o nazwie<br /><br /> Potoku|  
|Zasięg|Zasięg transportu odzwierciedla sposób stanie transport jest na łączenie z innymi systemami. Transportu nazwanego potoku ma bardzo mało zasięg; można połączyć tylko do usług uruchomionych na tym samym komputerze. Transportu TCP i HTTP ma doskonałą zasięgu i może przechodzić przez różne konfiguracje translatora adresów Sieciowych i zapory. Aby uzyskać więcej informacji, zobacz [Praca z translatorami adresów sieciowych i zaporami](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Zabezpieczenia|Bezpieczeństwo jest możliwość ochrony podczas transferu wiadomości, podając poufność, integralność lub uwierzytelniania. Poufność ochronę komunikat sprawdzane, integralność chroni komunikatu przed modyfikacją i uwierzytelniania daje gwarancje dotyczące nadawcy i adresata wiadomości.<br /><br /> Usługi WCF obsługuje transfer zabezpieczeń zarówno na poziomie transportu i poziom komunikatu. Zabezpieczenia komunikatów komponuje się za pomocą transportu, czy transport obsługuje sygnał trybu buforowanego transferu. Obsługa zabezpieczeń transportu różni się zależnie od wybranej transportu. HTTP, TCP i transport nazwany potok ma uzasadnione parzystości ich obsługę zabezpieczeń transportu.|Wszystkie|  
|Przepływność|Przepływność mierzy ilość danych, które mogą być przesyłane i przetwarzane w danym czasie. Np. czas oczekiwania wybranym transportu mogą mieć wpływ na przepływność dla operacji usługi. DSI oznacza optymalne wykorzystanie przepustowości dla transportu wymaga dodatkowe obciążenie przesyłanie zawartości, a także zminimalizować czas oczekiwania na wymianę komunikatów zakończyć. Zarówno TCP, jak i transportu nazwanego potoku Dodaj niewielkim zapasem do treści wiadomości i obsługuje natywnych kształtu dwukierunkowego, który zmniejsza czas oczekiwania, aby uzyskać odpowiedzi na wiadomości.|TCP, nazwany potok|  
|Narzędzia|Narzędzia reprezentuje pomocy technicznej dla protokołu dla rozwoju, Diagnostyka, hostowania go i inne działania aplikacji innych firm. Tworzenia, narzędzia i oprogramowanie do pracy z protokołem HTTP oznacza, szczególnie dużych inwestycji.|HTTP|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- [Powiązania](../../../../docs/framework/wcf/feature-details/bindings.md)
- [Powiązania dostarczane przez system](../../../../docs/framework/wcf/system-provided-bindings.md)
- [Tworzenie powiązań zdefiniowanych przez użytkownika](../../../../docs/framework/wcf/extending/creating-user-defined-bindings.md)
