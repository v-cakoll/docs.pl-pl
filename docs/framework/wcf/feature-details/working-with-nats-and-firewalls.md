---
title: Praca z translatorami adresów sieciowych i zaporami
ms.date: 03/30/2017
helpviewer_keywords:
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
ms.openlocfilehash: 5495d8198d30f4462fa9772f7d663664c82c6dee
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59296345"
---
# <a name="working-with-nats-and-firewalls"></a>Praca z translatorami adresów sieciowych i zaporami
Klient i serwer połączenia sieciowego często nie mają bezpośredniego i otworzyć ścieżki komunikacji. Pakiety są filtrowane, kierowane, analizowane i przekształcone zarówno na komputerach punktu końcowego, jak i pośredniego maszyn w sieci. Translacje adresów sieciowych (NAT) i zapory są typowe przykłady pośrednich aplikacji, które mogą uczestniczyć w komunikacji sieciowej.  
  
 Transporty Windows Communication Foundation (WCF) i wiadomości programu exchange wzorców (MEPs) inaczej do reagują na obecność translatorami adresów sieciowych i zaporami. W tym temacie opisano, jak translatorami adresów sieciowych i zaporami w typowych funkcji topologii sieci. Zalecenia dotyczące konkretnej ich kombinacji transportów WCF i MEPs są podane który sprawić, że aplikacje bardziej niezawodne translatorami adresów sieciowych i zaporami w sieci.  
  
## <a name="how-nats-affect-communication"></a>Wpływ translatorami adresów sieciowych komunikacji  
 Translatora adresów Sieciowych została utworzona w celu włączenia kilka maszyn na udostępnianie jednego zewnętrznego adresu IP. Ponowne mapowanie portów NAT mapuje zewnętrzny adres IP za pomocą nowego numeru portu wewnętrzny adres IP i portu dla połączenia. Nowy numer portu umożliwia translatora adresów Sieciowych skorelować ruch powrotny z oryginalnego komunikacji. Wielu użytkowników domowych teraz mieć adres IP, będzie on prywatnie routingowi i zależą od NAT do dostarczania routingu globalnego pakietów.  
  
 Translator NAT nie zapewnia granicy zabezpieczeń. Jednak typowe konfiguracje adresów NAT. uniemożliwić adresowane bezpośrednio wewnętrznych maszyn. To zapewnia ochronę wewnętrznych maszyn z niektóre niechciane połączenia i utrudnia do pisania aplikacji serwera, których muszą asynchronicznie przesyłać dane do klienta. Translatora adresów Sieciowych ponownie zapisuje adresy z pakietów, które ułatwiają porównywalne połączeń są pochodzący maszyny translatora adresów Sieciowych. Powoduje to, że serwer zakończyć się niepowodzeniem podczas próby otwarcia połączenia do klienta. Jeśli serwer używa postrzegany adres klienta, nie działa, ponieważ adres klienta nie może być kierowany publicznie. Jeśli serwer używa adresów translatora adresów Sieciowych, nie może nawiązać połączenia, ponieważ żadna aplikacja nie nasłuchuje na tym komputerze.  
  
 Niektóre translatorami adresów sieciowych obsługuje konfigurację reguły, aby umożliwić maszynom zewnętrznych nawiązać połączenia z określonego komputera wewnętrzny przekazywania. Instrukcje dotyczące konfigurowania reguł przekazywania waha się między różnych translatorami adresów sieciowych i pytania użytkowników końcowych, aby zmienić ich konfigurację translatora adresów Sieciowych nie jest zalecane w przypadku większości aplikacji. Wielu użytkowników końcowych nie może lub nie chcesz zmienić ich konfiguracji translatora adresów Sieciowych dla określonej aplikacji.  
  
## <a name="how-firewalls-affect-communication"></a>Wpływ komunikacji zapory  
 A *zapory* to urządzenie oprogramowania lub sprzętu, które stosuje reguły dla ruchu przechodzącego zdecydować, czy należy udzielić lub odmówić przejścia. Można skonfigurować zapory, aby zbadać przychodzących i wychodzących strumieni ruchu. Zapora zapewnia granicę zabezpieczeń sieci na obu granicy sieci na hoście punktu końcowego. Użytkownicy biznesowi tradycyjnie przechowywano swoje serwery za zaporą, przed złośliwymi atakami. Od czasu wprowadzenia zapory osobistej w [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], liczbę użytkowników domowych zaporą znacznie zwiększono również. Sprawia to jednego lub obu końcach połączenia ma zapory, sprawdzając pakietów.  
  
 Zapory się znacznie różnić pod względem ich złożoności i możliwości badania pakietów. Proste zapory jest stosowanie reguł na podstawie źródłowych i docelowych adresów i portów w pakietach. Inteligentne zapory można także sprawdzić zawartość pakietów do podejmowania decyzji. Tymi dwiema zaporami w wielu różnych konfiguracji i są często używane do specjalnych aplikacji.  
  
 Typowa konfiguracja zapory użytkownika jest chyba, że połączenia wychodzącego dokonano na tym komputerze wcześniej Stanów Zjednoczonych zabraniają połączeń przychodzących. Typowa konfiguracja zapory użytkowników biznesowych jest ze Stanów Zjednoczonych zabraniają połączeń przychodzących na wszystkich portach, z wyjątkiem grupy wskazane. Przykładem jest zapora, która zakazuje połączeń na wszystkich portach, z wyjątkiem portów 80 i 443, aby zapewnić obsługę protokołu HTTP i HTTPS. Zapory zarządzanego istnieje głównego i biznesowych użytkownikom, pozwalające Zaufany użytkownik lub proces na komputerze, aby zmienić konfigurację zapory. Zarządzane zapory są typowe dla użytkowników domowych w przypadku, gdy istnieje nie zasady firmowe kontrolowanie użycia sieci.  
  
## <a name="using-teredo"></a>Przy użyciu protokołu Teredo  
 Protokół Teredo jest technologii przejściowej IPv6, która umożliwia bezpośrednie adresowanie maszyn za translatorem adresów sieciowych. Teredo opiera się na korzystanie z serwera, które mogą być publicznie i globalnie przesyłane anonsowanie potencjalnych połączeń. Serwer Teredo, udostępnia aplikacji klienta i serwera, wspólnego punktu spotkania, w którym mogą wymieniać informacje o połączeniu. Maszyny następnie żądanie tymczasowego adresu Teredo, a pakiety są tunelowane do istniejącej sieci. Obsługa klientów Teredo w programie WCF wymaga Włączanie obsługi protokołu IPv6 i Teredo w systemie operacyjnym. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i nowszych systemów operacyjnych obsługują protokół Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)] i nowszych systemów operacyjnych obsługuje protokół IPv6, domyślnie wymagają tylko użytkownika włączyć protokół Teredo. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] wymaga od użytkownika włączyć IPv6 i Teredo. Aby uzyskać więcej informacji, zobacz [Przegląd Teredo](https://go.microsoft.com/fwlink/?LinkId=87571).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Wybieranie transportu i wymiany komunikatów  
 Wybieranie transportu i MEP jest procesem trzech kroków:  
  
1. Analizuj adresowanie maszyn punktu końcowego. Serwerów przedsiębiorstwa często mają bezpośrednie adresowanie, a użytkownicy końcowi często ich adresowanie zablokowanych przez translatorami adresów sieciowych. Jeśli oba punkty końcowe są poza NAT, takie jak w scenariuszach peer-to-peer między użytkownicy końcowi mogą następnie możesz potrzebować technologii, takich jak protokół Teredo, aby zapewnić adresowanie.  
  
2. Analizuj ograniczenia protokół i port maszyn punktu końcowego. Serwery w przedsiębiorstwie są zazwyczaj za zaporami silne tego bloku wielu portów. Jednak port 80 jest często otwarty, aby zezwalać na ruch protokołu HTTP i port 443 został otwarty, aby zezwalać na ruch protokołu HTTPS. Użytkownicy końcowi są mniej prawdopodobne, mają ograniczenia portu, ale może być zaporą, która zezwala na tylko połączeń wychodzących. Niektóre zapory umożliwienia zarządzania przez aplikacje w punkcie końcowym, aby selektywnie otworzyć połączenia.  
  
3. Obliczenia transportu i MEPs zezwalające na adresowanie i port ograniczenia sieci.  
  
 Typowe topologii dla aplikacji klienckich i serwerowych jest klientów znajdujących się poza NAT bez Teredo przy użyciu tylko wychodzącego zapory i serwera, który jest staną się dostępne bezpośrednio z zaporą silne. W tym scenariuszu, warstwy transportowej TCP z dwukierunkowego MEP i protokół transportu HTTP za pomocą żądanie odpowiedź MEP działa poprawnie. Typowe topologii dla aplikacji peer-to-peer jest zarówno punkty końcowe poza translatorami adresów sieciowych i zaporami. W tym scenariuszu i w scenariuszach, gdzie jest nieznany topologią i konfiguracją sieci należy wziąć pod uwagę następujące zalecenia:  
  
-   Nie należy używać podwójnego transportów. Podwójna transportu otwiera więcej połączeń, co zmniejsza prawdopodobieństwo pomyślnie połączenie.  
  
-   Obsługuje ustanowienia kanały wstecz za pośrednictwem zainicjowanego połączenia. Przy użyciu zwrotnego kanałów, takich jak dwukierunkowego protokołu TCP, zostanie otwarty mniejszą liczbę połączeń, co zwiększa prawdopodobieństwo łączenia się pomyślnie.  
  
-   Stosować dostępne usługi rejestrowania punktów końcowych lub przekazywania ruchu. Za pomocą globalnie dostępne połączenia usługi, takie jak serwer Teredo, znacznie zwiększa prawdopodobieństwo pomyślnie nawiązywania topologii sieci jest restrykcyjne lub nieznany.  
  
 Następujące tabele badania, jednokierunkowe, żądanie odpowiedź i dwukierunkowego MEPs i standardowy protokół TCP, TCP za pomocą protokołu Teredo, i służy do transportu HTTP standardowych i podwójna w programie WCF.  
  
|Adresowanie|Bezpośrednie serwera|Serwer bezpośrednio Przechodzenie translatora adresów Sieciowych|Serwer translatora adresów Sieciowych|Serwer translatora adresów Sieciowych z Przechodzenie translatora adresów Sieciowych|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Bezpośrednie klienta|Wszelkie transportu i MEP|Wszelkie transportu i MEP|Nieobsługiwane.|Nieobsługiwane.|  
|Klient bezpośrednio Przechodzenie translatora adresów Sieciowych|Transport i MEP.|Transport i MEP.|Nieobsługiwane.|TCP z klientów Teredo i wszelkie MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)] jest dostępna opcja konfiguracji komputera, do obsługi protokołu HTTP przy użyciu protokołu Teredo.|  
|Klient translatora adresów Sieciowych|Transport niż procesory i MEP. MEP dwukierunkowe wymaga warstwy transportowej TCP.|Transport niż procesory i MEP. MEP dwukierunkowe wymaga warstwy transportowej TCP.|Nieobsługiwane.|Nieobsługiwane.|  
|Klient translatora adresów Sieciowych o Przechodzenie translatora adresów Sieciowych|Transport niż procesory i MEP. MEP dwukierunkowe wymaga warstwy transportowej TCP.|Wszystkie elementy oprócz podwójnego HTTP i wszelkie MEP. MEP dwukierunkowe wymaga warstwy transportowej TCP. Podwójna warstwy transportowej TCP wymaga protokołu Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)] jest dostępna opcja konfiguracji komputera, do obsługi protokołu HTTP przy użyciu protokołu Teredo.|Nieobsługiwane.|TCP z klientów Teredo i wszelkie MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)] jest dostępna opcja konfiguracji komputera, do obsługi protokołu HTTP przy użyciu protokołu Teredo.|  
  
|Ograniczenia dotyczące zapory|Otwórz serwer|Serwer z zarządzanego zapory|Serwer z zaporą tylko HTTP|Serwer z zaporą tylko ruchu wychodzącego|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|Otwórz klienta|Transport i MEP.|Transport i MEP.|Transportu HTTP i MEP.|Nieobsługiwane.|  
|Klient z zaporą zarządzanych|Transport niż procesory i MEP. MEP dwukierunkowe wymaga warstwy transportowej TCP.|Transport niż procesory i MEP. MEP dwukierunkowe wymaga warstwy transportowej TCP.|Transportu HTTP i MEP.|Nieobsługiwane.|  
|Klient z zaporą tylko HTTP|Transportu HTTP i MEP.|Transportu HTTP i MEP.|Transportu HTTP i MEP.|Nieobsługiwane.|  
|Klient z zaporą tylko ruchu wychodzącego|Transport niż procesory i MEP. MEP dwukierunkowe wymaga warstwy transportowej TCP.|Transport niż procesory i MEP. MEP dwukierunkowe wymaga warstwy transportowej TCP.|Wszelkie transportu HTTP i wszelkie MEP-duplex.|Nieobsługiwane.|
