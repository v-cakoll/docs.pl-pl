---
title: Praca z translatorami adresów sieciowych i zaporami
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
- firewalls [WCF]
- NATs [WCF]
ms.assetid: 74db0632-1bf0-428b-89c8-bd53b64332e7
caps.latest.revision: 12
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: fe74b4bd86a25a8e6b769be1abe5fd81e5ffe5f9
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="working-with-nats-and-firewalls"></a>Praca z translatorami adresów sieciowych i zaporami
Klient i serwer połączenia sieciowego często nie mają bezpośredniego i ścieżki do komunikacji. Pakiety są filtrowane, kierowane przeanalizowane i przekształcony zarówno na komputerach punktu końcowego i pośredniego komputerów w sieci. Translacji adresów sieciowych (NAT) i zapory są typowe przykłady pośrednich aplikacji, które mogą uczestniczyć w komunikacji sieciowej.  
  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] Transporty i wiadomości exchange wzorce (MEPs) inaczej do reagowania obecności NAT i zapory. W tym temacie opisano, jak translatorami adresów sieciowych i zaporami wspólnych funkcji topologii sieci. Zalecenia dotyczące konkretnych kombinacji [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] transportów MEPs podano i który sprawić, że aplikacje bardziej niezawodne translatory adresów sieciowych i zaporami w sieci.  
  
## <a name="how-nats-affect-communication"></a>Wpływ komunikacji NAT  
 NAT został utworzony w celu włączenia kilka maszyn do udostępniania jednego zewnętrznego adresu IP. Translatora adresów Sieciowych ponownego mapowania portów mapuje zewnętrzny adres IP z nowym numerem portu wewnętrznego adresu IP i portu dla połączenia. Nowy numer portu umożliwia NAT służące do skorelowania ruchu zwrotu z oryginalnego komunikacji. W przypadku wielu użytkowników domowych teraz ma adres IP, który jest tylko prywatnie routingu i polegać na NAT zapewnienie globalne routing pakietów.  
  
 Translator NAT nie zapewnia granicy zabezpieczeń. Jednak typowe konfiguracje translatora adresów Sieciowych uniemożliwić bezpośrednio adresowane wewnętrzny maszyny. To zarówno chroni wewnętrzny maszyny z niektórych niechciane połączenia i utrudnia pisanie aplikacji serwerowych, które muszą asynchronicznie wysyłania danych do klienta. Translatora adresów Sieciowych ponownie zapisuje adresy w pakietach, aby była są pochodzą połączeń na komputerze translatora adresów Sieciowych. Powoduje to, że serwer zakończyć się niepowodzeniem podczas próby otwarcia połączenia do klienta. Jeśli serwer używa postrzegana adres klienta, nie działa, ponieważ adres klienta nie może być kierowane publicznie. Jeśli serwer używa adres NAT, nie może nawiązać połączenia, ponieważ żadna aplikacja nie nasłuchuje na tej maszynie.  
  
 Niektóre NAT obsługuje konfigurację przekazywania reguły zezwalające na zewnętrzne maszyny nawiązać połączenia z określonego komputera i wewnętrznych. Instrukcje dotyczące konfigurowania zasady przekazywania zmienia się między różnych NAT, a pytania użytkowników końcowych, aby zmienić konfigurację ich NAT nie jest zalecane dla większości aplikacji. Użytkownicy końcowi wielu nie może lub nie chcesz zmienić ich konfiguracji translatora adresów Sieciowych dla określonej aplikacji.  
  
## <a name="how-firewalls-affect-communication"></a>Wpływ komunikacji zapór  
 A *zapory* to oprogramowania lub sprzętu urządzenie, które dotyczą reguły ruchu przechodzącej przez zdecydować, czy zezwalające lub niezezwalające przejście. Można skonfigurować zapory do sprawdzenia przychodzących i wychodzących strumieni ruchu. Zapora zapewnia granicy zabezpieczeń sieci na albo granicy sieci na hoście punktu końcowego. Użytkownicy biznesowi tradycyjnie zachował serwerach za zaporą, aby zapobiec złośliwych ataków. Od czasu wprowadzenia zapory osobistej w [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)], liczbę użytkowników domowych za zaporą znacznie zwiększono również. Sprawia to jednym lub obu końców połączenia ma zapory, sprawdzając pakietów.  
  
 Zapory się znacznie różnić pod względem ich złożoność i możliwości badania pakietów. Proste zapór Zastosuj reguły na podstawie źródłowe i docelowe adresy i porty w pakietach. Inteligentnego zapory można także sprawdzić zawartość pakietów do podejmowania decyzji. Te zapory są dostępne w wielu różnych konfiguracji i są często używane dla aplikacji specjalne.  
  
 Typowa konfiguracja zapory użytkownika jest Zabroń używania połączenia przychodzące, chyba że połączenia wychodzącego został wcześniej wprowadzone do tej maszyny. Typowa konfiguracja zapory firm użytkownika ma Zabroń używania połączenia przychodzące na portach wszystkie z wyjątkiem grupy dokładnie zidentyfikowana. Przykładem jest zaporą, która uniemożliwia połączeń na wszystkich portach, z wyjątkiem porty 80 i 443 do obsługi protokołu HTTP i HTTPS. Zarządzane zapór istnieją dla użytkowników firmowymi i macierzystego, pozwalające Zaufany użytkownik lub proces na komputerze, aby zmienić konfigurację zapory. Zarządzane zapory są częściej dla użytkowników domowych przypadku nie zasady firmowe kontrolowanie użycia sieci.  
  
## <a name="using-teredo"></a>Przy użyciu protokołu Teredo  
 Protokół Teredo jest technologii przejściowej IPv6, który umożliwia bezpośrednie adresowanie maszyn za urządzeniem NAT Teredo opiera się na korzystanie z serwera, które mogą być publicznie i globalnie przesyłane do anonsowania potencjalnych połączenia. Serwer Teredo daje aplikacji klienta i serwera, wspólnego punktu spotkania, jaką mogą wymieniać informacje o połączeniu. Maszyny następnie zażądać tymczasowego adresu Teredo, a pakiety są tunneled za pomocą istniejącej sieci. Obsługa protokołu Teredo w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] wymaga włączania obsługi protokołu IPv6 i Teredo w systemie operacyjnym. [!INCLUDE[wxp](../../../../includes/wxp-md.md)] i nowszych systemów operacyjnych obsługuje Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)] i nowszych systemów operacyjnych obsługiwać protokół IPv6 domyślnie tylko wymagają od użytkownika włączyć protokół Teredo. [!INCLUDE[wxpsp2](../../../../includes/wxpsp2-md.md)] i [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)] wymagają od użytkownika do włączenia protokołu IPv6 i Teredo. Aby uzyskać więcej informacji, zobacz [omówienie Teredo](http://go.microsoft.com/fwlink/?LinkId=87571).  
  
## <a name="choosing-a-transport-and-message-exchange-pattern"></a>Wybieranie transportu i wymiany komunikatów  
 Wybieranie transportu i MEP jest procesem trzech etapów:  
  
1.  Przeanalizuj adresowanie maszyn punktu końcowego. Serwerów przedsiębiorstwa często jest bezpośrednie adresowanie, podczas użytkownicy końcowi często jest ich adresowanie zablokowanych przez translatory adresów sieciowych. Jeśli oba punkty końcowe znajdują się za translatorem adresów Sieciowych, takich jak w scenariuszach peer-to-peer od użytkowników końcowych, następnie może zaistnieć technologii, takich jak Teredo, aby zapewnić adresowanie.  
  
2.  Przeanalizuj ograniczenia protokół i port punktu końcowego maszyny. Serwery w przedsiębiorstwie są zazwyczaj za zaporą silne tego bloku wielu portów. Jednak port 80 jest często otwarty, aby zezwolić na ruch HTTP i port 443 jest otwarty, aby zezwolić na ruch protokołu HTTPS. Użytkownicy końcowi są mniej prawdopodobnie będą istnieć ograniczenia portu, ale może być za zaporą, która zezwala na tylko połączeń wychodzących. Niektóre zapory umożliwienia zarządzania przez aplikacje w punkcie końcowym selektywnie otworzyć połączenia.  
  
3.  Obliczenia bazy danych transportu i MEPs pozwalające ograniczenia adresowania i portu sieci.  
  
 Typowe topologii dla aplikacji klient serwer jest klientów, którzy znajdują się za translatorem adresów Sieciowych bez Teredo tylko ruchu wychodzącego zapory i serwera, który jest bezpośrednio mogą być adresowane za pomocą silnych zapory. W tym scenariuszu, transportu TCP z dupleksu MEP i protokół transportu HTTP z żądanie odpowiedź MEP działa prawidłowo. Typowe topologii dla aplikacji peer-to-peer jest zarówno punktów końcowych za NAT i zapory. W tym scenariuszu, a w scenariuszach, w którym topologii sieci jest nieznany należy wziąć pod uwagę następujące zalecenia:  
  
-   Nie należy używać podwójną transportów. Podwójna transportu otwiera więcej połączeń, co zmniejsza ryzyko łączący się pomyślnie.  
  
-   Obsługuje ustanowienia kanałów wstecz za pośrednictwem połączenia źródłowego. Za pomocą kanałów Wstecz, takich jak dupleksu protokołu TCP, otwiera mniejszą liczbę połączeń, co zwiększa prawdopodobieństwo łączący się pomyślnie.  
  
-   Stosować dostępne usługi dla rejestracji punktów końcowych lub przekazywania ruchu. Przy użyciu usługi globalnie dostępny połączenia, takich jak serwer Teredo, znacznie ułatwia łączenie pomyślnie po ograniczające lub nieznany topologii sieci.  
  
 Poniższe tabele analizować jednokierunkowe, żądanie odpowiedź i dupleksu MEPs i standardowe TCP, TCP z Teredo i standard i podwójna transport HTTP w [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].  
  
|Adresowanie|Bezpośrednie serwera|Serwer bezpośrednio z przechodzeniem translatora adresów Sieciowych|Serwer translatora adresów Sieciowych|Serwer NAT z przechodzeniem translatora adresów Sieciowych|  
|--------------------|-------------------|--------------------------------------|----------------|-----------------------------------|  
|Klienckie bezpośrednie|Wszelkie transportu i MEP|Wszelkie transportu i MEP|Nieobsługiwane.|Nieobsługiwane.|  
|Klienckie bezpośrednie z przechodzeniem translatora adresów Sieciowych|Transport i MEP.|Transport i MEP.|Nieobsługiwane.|TCP z klientów Teredo i wszelkie MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)] jest dostępna opcji konfiguracji komputera do obsługi protokołu Teredo HTTP.|  
|Klient translatora adresów Sieciowych|Wszystkie procesory z systemem innym niż transportu i MEP. Dupleks MEP wymaga transportu TCP.|Wszystkie procesory z systemem innym niż transportu i MEP. Dupleks MEP wymaga transportu TCP.|Nieobsługiwane.|Nieobsługiwane.|  
|Klient translatora adresów Sieciowych z przechodzeniem translatora adresów Sieciowych|Wszystkie procesory z systemem innym niż transportu i MEP. Dupleks MEP wymaga transportu TCP.|Wszystkie elementy oprócz dwóch HTTP i wszelkie MEP. Dupleks MEP wymaga transportu TCP. Podwójna transportu TCP wymaga protokołu Teredo. [!INCLUDE[wv](../../../../includes/wv-md.md)] jest dostępna opcji konfiguracji komputera do obsługi protokołu Teredo HTTP.|Nieobsługiwane.|TCP z klientów Teredo i wszelkie MEP. [!INCLUDE[wv](../../../../includes/wv-md.md)] jest dostępna opcji konfiguracji komputera do obsługi protokołu Teredo HTTP.|  
  
|Ograniczeń zapory|Otwórz serwera|Serwer z zarządzanego zapory|Serwer z zapory tylko HTTP|Serwer z zapory tylko ruchu wychodzącego|  
|---------------------------|-----------------|----------------------------------|-------------------------------------|-----------------------------------------|  
|Otwórz klienta|Transport i MEP.|Transport i MEP.|HTTP transport i MEP.|Nieobsługiwane.|  
|Klient z zarządzanego zapory|Wszystkie procesory z systemem innym niż transportu i MEP. Dupleks MEP wymaga transportu TCP.|Wszystkie procesory z systemem innym niż transportu i MEP. Dupleks MEP wymaga transportu TCP.|HTTP transport i MEP.|Nieobsługiwane.|  
|Klient z zapory tylko HTTP|HTTP transport i MEP.|HTTP transport i MEP.|HTTP transport i MEP.|Nieobsługiwane.|  
|Klient z zapory tylko ruchu wychodzącego|Wszystkie procesory z systemem innym niż transportu i MEP. Dupleks MEP wymaga transportu TCP.|Wszystkie procesory z systemem innym niż transportu i MEP. Dupleks MEP wymaga transportu TCP.|Każdy transport HTTP i wszelkie MEP-duplex.|Nieobsługiwane.|
