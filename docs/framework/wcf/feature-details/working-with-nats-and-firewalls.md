---
title: Praca z translatorami adresów sieciowych i zaporami
ms.date: 03/30/2017
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
ms.openlocfilehash: b8be10740c8e92d3dac7094f07b3372e8d78a3d9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743872"
---
# <a name="working-with-nats-and-firewalls"></a>Praca z translatorami adresów sieciowych i zaporami
Klient i serwer połączenia sieciowego często nie mają bezpośredniego i otwartej ścieżki do komunikacji. Pakiety są filtrowane, kierowane, analizowane i przekształcane zarówno na maszynach końcowych, jak i na maszynach pośrednich w sieci. Translacji adresów sieciowych (NAT) i zapory są typowymi przykładami aplikacji pośrednich, które mogą uczestniczyć w komunikacji sieciowej.  
  
 Transporty usługi Windows Communication Foundation (WCF) i wzorce wymiany komunikatów (MEPs) reagują inaczej w zależności od obecności translatorów adresów sieciowych i zapór. W tym temacie opisano sposób, w jaki translatory adresów sieciowych i zapory funkcjonują w ramach wspólnych topologii sieci. Zalecenia dotyczące konkretnych kombinacji transportów WCF i MEPs mają na celu zwiększenie niezawodności aplikacji do translatorów adresów sieciowych i zapór w sieci.  
  
## <a name="how-nats-affect-communication"></a>Wpływ komunikacji między translatorami adresów sieciowych  
 Utworzono translator adresów sieciowych w celu umożliwienia kilku komputerom współdzielenia jednego zewnętrznego adresu IP. Mapowanie NAT dla ponownego mapowania portów mapuje wewnętrzny adres IP i port dla połączenia z zewnętrznym adresem IP z nowym numerem portu. Nowy numer portu umożliwia translacji adresów sieciowych w celu skorelowania ruchu zwrotnego z oryginalną komunikacją. Wielu użytkowników domowych ma teraz adres IP, który jest tylko prywatnie rutowany i polega na translatorze adresów sieciowych w celu zapewnienia globalnego routingu pakietów.  
  
 Translator adresów sieciowych nie zapewnia granicy zabezpieczeń. Jednak typowe konfiguracje NAT uniemożliwiają bezpośrednią Readresowanie maszyn wewnętrznych. Obejmuje to ochronę maszyn wewnętrznych przed niektórymi niechcianymi połączeniami i utrudnia zapisywanie aplikacji serwera, które muszą asynchronicznie wysyłać dane z powrotem do klienta. Translator adresów sieciowych ponownie zapisuje adresy w pakietach, aby się upewnić, że połączenia są pochodziły z maszyn translatora adresów sieciowych. Powoduje to, że serwer kończy się niepowodzeniem podczas próby otwarcia połączenia z powrotem do klienta programu. Jeśli serwer używa znanego adresu klienta, nie powiedzie się, ponieważ adres klienta nie może być kierowany publicznie. Jeśli serwer używa adresu NAT, połączenie nie powiedzie się, ponieważ żadna aplikacja nie nasłuchuje na tym komputerze.  
  
 Niektóre NAT obsługują konfigurację reguł przekazywania, aby umożliwić maszynom zewnętrznym łączenie się z konkretną maszyną wewnętrzną. Instrukcje dotyczące konfigurowania reguł przekazywania różnią się między różnymi translatorami adresów sieciowych i zaproszenie użytkowników końcowych o zmianę konfiguracji NAT nie są zalecane w przypadku większości aplikacji. Wielu użytkowników końcowych nie może lub nie chce zmieniać konfiguracji NAT dla określonej aplikacji.  
  
## <a name="how-firewalls-affect-communication"></a>Jak zapory wpływają na komunikację  
 *Zapora* to oprogramowanie lub sprzęt, które stosuje reguły do ruchu przechodzącego przez, aby zdecydować, czy zezwalać na przesyłanie lub odmawiać. Zapory można skonfigurować do badania strumieni ruchu przychodzącego i/lub wychodzącego. Zapora zapewnia granicę zabezpieczeń sieci na granicy sieci lub na hoście punktu końcowego. Użytkownicy biznesowi tradycyjnie zachowały swoje serwery za zaporą, aby zapobiec złośliwym atakom. Od momentu wprowadzenia zapory osobistej w [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)]liczba użytkowników domowych za zaporą została znacznie zwiększona. Dzięki temu jedno lub oba punkty końcowe połączenia mają zaporę sprawdzającą pakiety.  
  
 Zapory różnią się znacznie pod względem ich złożoności i możliwości testowania pakietów. Proste zapory stosują reguły oparte na adresach źródłowych i docelowych oraz portach w pakietach. Inteligentne zapory mogą również sprawdzić zawartość pakietów, aby podejmować decyzje. Te zapory są dostępne w wielu różnych konfiguracjach i często są używane w przypadku wyspecjalizowanych aplikacji.  
  
 Typową konfiguracją zapory użytkownika domowego jest Zabroń połączeń przychodzących, chyba że połączenie wychodzące nie zostało wcześniej nawiązane z tą maszyną. Typowa konfiguracja zapory użytkownika dla firm polega na tym, że połączenia przychodzące na wszystkich portach z wyjątkiem określonej przez grupę. Przykładem jest Zapora, która zabrania połączeń na wszystkich portach z wyjątkiem portów 80 i 443 w celu zapewnienia usługi HTTP i HTTPS. Zapory zarządzane istnieją zarówno dla użytkowników domowych, jak i firmowych, co pozwala na zmianę konfiguracji zapory przez zaufanego użytkownika lub proces na komputerze. Zarządzane zapory są bardziej popularne dla użytkowników domowych, w których nie ma kontroli nad użyciem zasad firmowych.  
  
## <a name="using-teredo"></a>Korzystanie z protokołu Teredo  

 Teredo to technologia przejściowa IPv6, która umożliwia bezpośrednie adresowanie maszyn za translatorem adresów sieciowych. Teredo korzysta z serwera, który może być publicznie i globalnie kierowany do anonsowania potencjalnych połączeń. Serwer Teredo zapewnia klientowi aplikacji i serwerowi wspólny punkt spotkania, w którym mogą wymieniać informacje o połączeniu. Komputery następnie żądają tymczasowego adresu Teredo, a pakiety są tunelowane za pomocą istniejącej sieci. Obsługa protokołu Teredo w programie WCF wymaga włączenia obsługi protokołów IPv6 i Teredo w systemie operacyjnym. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i nowsze systemy operacyjne obsługują protokół Teredo. System Windows Vista i nowsze systemy operacyjne obsługują protokół IPv6 domyślnie i wymagają, aby użytkownik mógł włączyć protokół Teredo. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] i Windows Server 2003 wymagają, aby użytkownik włączył zarówno protokół IPv6, jak i Teredo. Aby uzyskać więcej informacji, zobacz [Omówienie protokołu Teredo](https://docs.microsoft.com/previous-versions/windows/it-pro/windows-xp/bb457011(v%3dtechnet.10)).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Wybór wzorca transportu i wymiany komunikatów  
 Wybór transportu i unikatowy MEP jest procesem trzech etapów:  
  
1. Analizuj adresowanie maszyn punktu końcowego. Serwery korporacyjne często mają bezpośredni adres, podczas gdy użytkownicy końcowi często mają adres blokowany przez NAT. Jeśli oba punkty końcowe znajdują się za translatorem adresów sieciowych, takich jak scenariusze komunikacji równorzędnej między użytkownikami końcowymi, może być potrzebna technologia, taka jak Teredo, aby zapewnić adresowanie.  
  
2. Analizuj ograniczenia protokołu i portu dla maszyn punktu końcowego. Serwery przedsiębiorstwa są zwykle za silnymi zaporami, które blokują wiele portów. Jednak port 80 jest często otwarty, aby zezwalać na ruch HTTP, a port 443 jest otwarty, aby zezwalać na ruch HTTPS. Użytkownicy końcowi mogą mieć ograniczenia dotyczące portów, ale mogą znajdować się za zaporą, która zezwala tylko na połączenia wychodzące. Niektóre zapory umożliwiają zarządzanie przez aplikacje w punkcie końcowym w celu selektywnego otwierania połączeń.  
  
3. Oblicz transporty i MEPs, że zezwalanie na adresy i ograniczenia portów w sieci.  
  
 Wspólna Topologia aplikacji klient-serwer polega na tym, że klienci znajdują się za translatorem adresów sieciowych bez protokołu Teredo z zaporą obsługującą tylko ruch wychodzący i serwer, który jest bezpośrednio adresowany przy użyciu silnej zapory. W tym scenariuszu transport TCP z unikatowy MEP dupleksu i transportem HTTP z unikatowy MEPem żądania. Wspólna Topologia aplikacji równorzędnych ma mieć oba punkty końcowe za translatorem adresów sieciowych i zaporami. W tym scenariuszu i w scenariuszach, w których topologia sieci jest nieznana, należy wziąć pod uwagę następujące zalecenia:  
  
- Nie należy używać podwójnej transportów. Podwójny transport otwiera więcej połączeń, co zmniejsza prawdopodobieństwo pomyślnego nawiązania połączenia.  
  
- Obsługa ustanawiania kanałów z tyłu przy użyciu połączenia źródłowego. Korzystając z kanałów wstecz, takich jak w przypadku protokołu TCP dupleksowego, program otwiera mniejszą liczbę połączeń, co zwiększa prawdopodobieństwo pomyślnego nawiązania połączenia.  
  
- Korzystanie z dostępnej usługi do rejestrowania punktów końcowych lub przekazywania ruchu. Użycie usługi połączenia dostępnej globalnie, takiej jak serwer Teredo, znacznie zwiększa prawdopodobieństwo pomyślnego nawiązania połączenia, gdy topologia sieci jest restrykcyjna lub nieznana.  
  
 W poniższych tabelach przedstawiono jednokierunkową MEPs, żądanie-odpowiedź i dupleks oraz Standard TCP, TCP z Teredo oraz standardowe i podwójne transporty HTTP w programie WCF.  
  
|Adresowanie|Serwer bezpośredni|Serwer bezpośredni z przechodzeniem NAT|Translator adresów sieciowych serwera|Serwer NAT z przechodzeniem NAT|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Klient bezpośredni|Wszystkie transporty i unikatowy MEP|Wszystkie transporty i unikatowy MEP|Nieobsługiwane.|Nieobsługiwane.|  
|Klient z przechodzeniem NAT|Wszystkie transporty i unikatowy MEP.|Wszystkie transporty i unikatowy MEP.|Nieobsługiwane.|TCP z protokołem Teredo i dowolnym unikatowy MEP. System Windows Vista ma opcję konfiguracji dla całego komputera, która obsługuje protokół HTTP przy użyciu protokołu Teredo.|  
|Translator adresów sieciowych klienta|Wszystkie niepodwójne transport i unikatowy MEP. UNIKATOWY MEP dupleksu wymaga transportu TCP.|Wszystkie niepodwójne transport i unikatowy MEP. UNIKATOWY MEP dupleksu wymaga transportu TCP.|Nieobsługiwane.|Nieobsługiwane.|  
|Translator adresów sieciowych klienta z przechodzeniem NAT|Wszystkie niepodwójne transport i unikatowy MEP. UNIKATOWY MEP dupleksu wymaga transportu TCP.|Wszystkie, ale podwójne HTTP i wszystkie unikatowy MEP. UNIKATOWY MEP dupleksu wymaga transportu TCP. Podwójny transport TCP wymaga protokołu Teredo. System Windows Vista ma opcję konfiguracji dla całego komputera, która obsługuje protokół HTTP przy użyciu protokołu Teredo.|Nieobsługiwane.|TCP z protokołem Teredo i dowolnym unikatowy MEP. System Windows Vista ma opcję konfiguracji dla całego komputera, która obsługuje protokół HTTP przy użyciu protokołu Teredo.|  
  
|Ograniczenia zapory|Serwer otwarty|Serwer z zarządzaną zaporą|Serwer z zaporą obsługującą tylko protokół HTTP|Serwer z zaporą obsługującą tylko ruch wychodzący|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|Klient otwarty|Wszystkie transporty i unikatowy MEP.|Wszystkie transporty i unikatowy MEP.|Wszystkie transporty HTTP i unikatowy MEP.|Nieobsługiwane.|  
|Klient z zarządzaną zaporą|Wszystkie niepodwójne transport i unikatowy MEP. UNIKATOWY MEP dupleksu wymaga transportu TCP.|Wszystkie niepodwójne transport i unikatowy MEP. UNIKATOWY MEP dupleksu wymaga transportu TCP.|Wszystkie transporty HTTP i unikatowy MEP.|Nieobsługiwane.|  
|Klient z zaporą tylko HTTP|Wszystkie transporty HTTP i unikatowy MEP.|Wszystkie transporty HTTP i unikatowy MEP.|Wszystkie transporty HTTP i unikatowy MEP.|Nieobsługiwane.|  
|Klient z zaporą tylko wychodzącą|Wszystkie niepodwójne transport i unikatowy MEP. UNIKATOWY MEP dupleksu wymaga transportu TCP.|Wszystkie niepodwójne transport i unikatowy MEP. UNIKATOWY MEP dupleksu wymaga transportu TCP.|Dowolny transport HTTP i dowolny unikatowy MEP niebędący dupleksem.|Nieobsługiwane.|
