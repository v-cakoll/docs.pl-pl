---
title: Wybieranie transportu
ms.date: 03/30/2017
helpviewer_keywords:
- choosing transports [WCF]
ms.assetid: b169462b-f7b6-4cf4-9fca-d306909ee8bf
ms.openlocfilehash: 7e1f6b2e1905fb92ebfe78be351feeaebb374c11
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84587069"
---
# <a name="choosing-a-transport"></a>Wybieranie transportu
W tym temacie omówiono kryteria wyboru trzech głównych transportów, które znajdują się w Windows Communication Foundation (WCF): HTTP, TCP i nazwanych potoków. Funkcja WCF obejmuje również transport usługi kolejkowania komunikatów (MSMQ), ale ten dokument nie obejmuje usługi kolejkowania komunikatów.  
  
 Model programowania WCF oddziela operacje punktów końcowych (zgodnie z umową usługi) od mechanizmu transportu, który łączy dwa punkty końcowe. Zapewnia to elastyczność w wyborze sposobu uwidaczniania usług w sieci.  
  
 W programie WCF należy określić sposób transferu danych między punktami końcowymi przy użyciu *powiązania*, które składa się z sekwencji *elementów powiązania*. Transport jest reprezentowany przez element powiązania transportu, który jest częścią powiązania. Powiązanie obejmuje opcjonalne elementy powiązania protokołów, takie jak zabezpieczenia, wymagany element powiązania kodera komunikatów i wymagany element powiązania transportu. Transport wysyła lub odbiera serializowaną postać wiadomości do lub z innej aplikacji.  
  
 Jeśli musisz nawiązać połączenie z istniejącym klientem lub serwerem, możesz nie mieć możliwości korzystania z określonego transportu. Jednak usługi WCF można udostępnić za pomocą wielu punktów końcowych, z których każdy ma inny transport. Jeśli pojedynczy transport nie obejmuje odpowiednich odbiorców usługi, należy rozważyć udostępnienie usługi za pośrednictwem wielu punktów końcowych. Aplikacje klienckie mogą następnie używać punktu końcowego, który jest dla nich najlepszy.  
  
 Po wybraniu transportu musisz wybrać powiązanie, które go używa. Można wybrać powiązanie dostarczone z systemem (patrz [powiązania dostarczone z systemem](../system-provided-bindings.md)) lub utworzyć własne niestandardowe powiązanie (zobacz [powiązania niestandardowe](../extending/custom-bindings.md)). Możesz również utworzyć własne powiązanie. Aby uzyskać więcej informacji, zobacz [Tworzenie powiązań zdefiniowanych przez użytkownika](../extending/creating-user-defined-bindings.md).  
  
## <a name="advantages-of-each-transport"></a>Zalety poszczególnych transportów  
 W tej sekcji opisano główne przyczyny wyboru jednego z trzech głównych transportów, łącznie z szczegółowym wykresem decyzyjnym do wyboru między nimi.  
  
### <a name="when-to-use-http-transport"></a>Kiedy używać transportu HTTP  
 HTTP to protokół żądania/odpowiedzi między klientami a serwerami. Najbardziej Typowa aplikacja składa się z klientów przeglądarek sieci Web komunikujących się z serwerem sieci Web. Klient wysyła żądanie do serwera, który nasłuchuje komunikatów żądań klientów. Gdy serwer odbiera żądanie, zwraca odpowiedź, która zawiera stan żądania. Jeśli zakończono pomyślnie, opcjonalne dane, takie jak strona sieci Web, komunikat o błędzie lub inne informacje są zwracane. Aby uzyskać więcej informacji na temat protokołu HTTP, zobacz [http-Hypertext Transfer Protocol](https://www.w3.org/Protocols/).  
  
 Protokół HTTP nie jest oparty na połączeniu — po wysłaniu odpowiedzi żaden stan nie jest obsługiwany. Aby obsłużyć transakcje wielostronicowe, aplikacja musi utrzymywać wszelkie niezbędne Stany.  
  
 W programie WCF powiązanie transportu HTTP jest zoptymalizowane pod kątem współdziałania ze starszymi systemami nieobsługującymi WCF. Jeśli wszystkie strony komunikują się z użyciem usługi WCF, powiązania oparte na protokole TCP lub nazwanych potoków są szybsze. Aby uzyskać więcej informacji, zobacz <xref:System.ServiceModel.NetTcpBinding> i <xref:System.ServiceModel.NetNamedPipeBinding>.  
  
### <a name="when-to-use-the-tcp-transport"></a>Kiedy używać transportu TCP  
 TCP to oparta na połączeniach usługa dostarczania strumieniowego z kompleksowym wykrywaniem błędów i korekcją. *Oparte na połączeniach* oznacza, że sesja komunikacji między hostami została ustanowiona przed wymianą danych. Host to dowolne urządzenie w sieci TCP/IP identyfikowane za pomocą logicznego adresu IP.  
  
 Protokół TCP zapewnia niezawodne dostarczanie danych i łatwość użycia. W odniesieniu do protokołu TCP powiadamia nadawcę o dostarczeniu pakietu, gwarantuje, że pakiety są dostarczane w takiej samej kolejności, w jakiej są wysyłane, ponownie przesyła utracone pakiety i gwarantuje, że pakiety danych nie są duplikowane. Należy zauważyć, że to niezawodne dostarczanie ma zastosowanie między dwoma węzłami TCP/IP i nie jest tym samym, co Metoda *WS-ReliableMessaging*, która stosuje się między punktami końcowymi, niezależnie od tego, ile węzłów pośrednich może obejmować.  
  
 Transport TCP WCF jest zoptymalizowany pod kątem scenariusza, w którym oba punkty końcowe komunikacji korzystają z programu WCF. To powiązanie jest najszybszym powiązaniem WCF dla scenariuszy, które obejmują komunikację między różnymi komputerami. W wymianie komunikatów jest używany <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement> zoptymalizowany transfer komunikatów. Protokół TCP zapewnia komunikację dupleksową i może służyć do implementowania umów dupleksowych, nawet jeśli klient znajduje się za translatorem adresów sieciowych (NAT).  
  
### <a name="when-to-use-the-named-pipe-transport"></a>Kiedy używać transportu nazwanego potoku  
 Nazwany potok jest obiektem w jądrze systemu operacyjnego Windows, takim jak sekcja pamięci współdzielonej, która może być używana przez procesy do komunikacji. Nazwany potok ma nazwę i może być używany do komunikacji jednokierunkowej między procesami na pojedynczym komputerze.  
  
 Gdy komunikacja jest wymagana między różnymi aplikacjami programu WCF na pojedynczym komputerze i chcesz uniemożliwić wszelką komunikację z innej maszyny, użyj transportu nazwanych potoków. Dodatkowe ograniczenie polega na tym, że procesy działające z systemu Windows Pulpit zdalny mogą być ograniczone do tej samej sesji systemu Windows Pulpit zdalny, chyba że mają podwyższone uprawnienia.  
  
> [!WARNING]
> W przypadku korzystania z transportu nazwanego potoku z nieprawidłowym zarezerwowanym adresem URL w wielu witrynach hostowanych w usługach IIS może wystąpić następujący błąd: Wystąpił błąd w usłudze aktywacji "NetPipeActivator" protokołu "net. Pipe" podczas próby nasłuchiwania lokacji "2", więc protokół jest tymczasowo wyłączony dla lokacji. Aby uzyskać więcej informacji, zobacz komunikat o wyjątku. URL: WeakWildcard: net. pipe:/ \<machine name> /status: ConflictingRegistration Exception: Process Name: SMSvcHost proces ID: 1076 \  
  
## <a name="decision-points-for-choosing-a-transport"></a>Punkty decyzyjne do wyboru transportu  
 W poniższej tabeli opisano typowe punkty decyzyjne używane do wybierania transportu. Należy wziąć pod uwagę wszelkie dodatkowe atrybuty i transporty, które mają zastosowanie do Twojej aplikacji. Zidentyfikuj atrybuty, które są ważne dla aplikacji, zidentyfikuj transporty, które kojarzą favorably z każdym z atrybutów, a następnie wybierz transporty, które najlepiej współpracują z ustawionym atrybutem.  
  
|Atrybut|Opis|Preferowane transporty|  
|---------------|-----------------|------------------------|  
|Diagnostyka|Diagnostyka pozwala na automatyczne wykrywanie problemów z łącznością transportową. Wszystkie transporty obsługują możliwość wysyłania informacji o błędach, które opisują łączność. Jednak funkcja WCF nie obejmuje narzędzi diagnostycznych do badania problemów z siecią.|Brak|  
|Hosting|Wszystkie punkty końcowe WCF muszą być hostowane wewnątrz aplikacji. Usługi IIS 6,0 i wcześniejsze wersje obsługują tylko aplikacje obsługujące transport HTTP. W systemie Windows Vista dodano obsługę obsługi wszystkich transportów WCF, w tym protokołów TCP i nazwanych potoków. Aby uzyskać więcej informacji, zobacz [hosting w Internet Information Services](hosting-in-internet-information-services.md) i [hosting w usłudze aktywacji procesów systemu Windows](hosting-in-windows-process-activation-service.md).|HTTP|  
|Przedubojowego|Inspekcja to możliwość wyodrębniania i przetwarzania informacji z komunikatów podczas przesyłania. Protokół HTTP oddziela informacje o routingu i kontroli danych, ułatwiając tworzenie narzędzi, które sprawdzają i analizują komunikaty. Transporty, które są łatwe do sprawdzenia, mogą również wymagać mniejszej mocy obliczeniowej w urządzeniach sieciowych. Poziom zabezpieczeń, który ma wpływ na to, czy można sprawdzić komunikaty.|HTTP|  
|Opóźnienie|Opóźnienie to minimalny czas wymagany do ukończenia wymiany komunikatów. Wszystkie operacje sieciowe mają więcej lub mniej opóźnień w zależności od wyboru transportu. Używanie dupleksu lub komunikacji jednokierunkowej z transportem, którego natywny wzorzec wymiany komunikatów to żądanie-odpowiedź, takie jak HTTP, może spowodować dodatkowe opóźnienie wynikające z wymuszonej korelacji komunikatów. W tej sytuacji Rozważ użycie transportu, którego natywny wzorzec wymiany komunikatów jest dwukierunkowy, na przykład TCP.|TCP, nazwane<br /><br /> Wodzie|  
|Usługa Reach|Zasięg transportu odzwierciedla sposób, w jaki transport jest połączony z innymi systemami. Transport nazwanych potoków ma bardzo mały zasięg; może łączyć się tylko z usługami uruchomionymi na tym samym komputerze. Transporty TCP i HTTP mają doskonały zasięg i mogą przeniknąć pewne konfiguracje NAT i zapór. Aby uzyskać więcej informacji, zobacz [Praca z translatorami adresów sieciowych i zaporami](working-with-nats-and-firewalls.md).|HTTP, TCP|  
|Zabezpieczenia|Zabezpieczenia to możliwość ochrony komunikatów podczas transferu przez dostarczanie poufności, integralności lub uwierzytelniania. Poufność chroni komunikat przed badaniem, integralność chroni komunikat przed jego modyfikacją, a uwierzytelnianie daje gwarancje dotyczące nadawcy lub odbiorcy wiadomości.<br /><br /> Usługa WCF obsługuje transfer zabezpieczeń zarówno na poziomie wiadomości, jak i na poziomie transportu. Zabezpieczenia komunikatów tworzą transport, jeśli transport obsługuje tryb transferu buforowanego. Obsługa zabezpieczeń transportu różni się w zależności od wybranego transportu. Transporty protokołu HTTP, TCP i nazwanego potoku mają odpowiednią zgodność z obsługą zabezpieczeń transportu.|Wszystko|  
|Przepływność|Przepływność mierzy ilość danych, które mogą być przesyłane i przetwarzane w określonym przedziale czasu. Podobnie jak opóźnienie, wybrany transport może wpływać na przepływność dla operacji usługi. Maksymalizacja przepływności dla transportu wymaga zminimalizowania obciążenia przesyłania zawartości oraz zminimalizowania czasu poświęcanego na ukończenie wymiany komunikatów. Transporty protokołu TCP i nazwanego potoku dodają niewielkie obciążenie do treści wiadomości i obsługują natywny kształt dupleksu, który zmniejsza czas oczekiwania na odpowiedzi na komunikaty.|TCP, nazwany potok|  
|Narzędzia|Narzędzia przedstawiają obsługę aplikacji innych firm dla protokołu na potrzeby tworzenia, diagnozowania, hostingu i innych działań. Projektowanie narzędzi i oprogramowania do pracy z protokołem HTTP oznacza szczególnie duże inwestycje.|HTTP|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.ServiceModel.BasicHttpBinding>
- <xref:System.ServiceModel.WSHttpBinding>
- <xref:System.ServiceModel.WSDualHttpBinding>
- <xref:System.ServiceModel.WSFederationHttpBinding>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement>
- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement>
- <xref:System.ServiceModel.NetNamedPipeBinding>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>
- [Powiązania](bindings.md)
- [Powiązania dostarczane przez system](../system-provided-bindings.md)
- [Tworzenie powiązań zdefiniowanych przez użytkownika](../extending/creating-user-defined-bindings.md)
