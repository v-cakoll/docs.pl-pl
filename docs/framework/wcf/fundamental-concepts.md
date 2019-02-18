---
title: Podstawowe pojęcia programu Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: b28f9c0575d1031c2f542ffa0de4ac5b848d3da1
ms.sourcegitcommit: bef803e2025642df39f2f1e046767d89031e0304
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/15/2019
ms.locfileid: "56305548"
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Podstawowe pojęcia programu Windows Communication Foundation
Ten dokument zawiera ogólny widok architektury usług Windows Communication Foundation (WCF). Jej celem jest zrozumienie podstawowych pojęć i jak one współdziałają ze sobą. Aby uzyskać samouczek dotyczący tworzenia najprostszym wersję usługi i klienta WCF, zobacz [Samouczek wprowadzający](../../../docs/framework/wcf/getting-started-tutorial.md). Programowanie WCF można znaleźć [programowanie WCF Basic](../../../docs/framework/wcf/basic-wcf-programming.md).  
  
## <a name="wcf-fundamentals"></a>Podstawy usługi WCF  
 Usługi WCF jest środowisko uruchomieniowe i zestaw interfejsów API do tworzenia systemów, które wysyłają wiadomości między usług i klientów. Tej samej infrastruktury i interfejsy API służą do tworzenia aplikacji, które komunikują się z innymi aplikacjami, w tym samym systemie komputera lub w systemie, który znajduje się w innej firmie i jest dostępny za pośrednictwem Internetu.  
  
### <a name="messaging-and-endpoints"></a>Obsługa komunikatów i punktów końcowych  
 Usługi WCF opiera się na koncepcji komunikacja oparta na komunikatach i nic, które mogą być modelowane zgodnie z komunikatu (na przykład żądanie HTTP lub wiadomości usługi MSMQ (MSMQ)) mogą być reprezentowane w jednolity sposób w modelu programowania. Dzięki temu ujednoliconego interfejsu API przez różne mechanizmy transportu.  
  
 Rozróżnia modelu *klientów*, które są aplikacje, które inicjują komunikację, i *usług*, służą do aplikacji, które oczekiwania dla klientów w celu komunikowania się z nimi i odpowiedzieć na to Komunikacja. Jedna aplikacja może pełnić zarówno klient, jak i usługi. Aby uzyskać przykłady, zobacz [usługi dwukierunkowe](../../../docs/framework/wcf/feature-details/duplex-services.md) i [sieci Peer-to-Peer](../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).  
  
 Komunikaty są wysyłane między punktami końcowymi. *Punkty końcowe* miejsca, w której wiadomości są wysyłane lub odbierane (lub obie) oraz definiują wszystkie informacje wymagane do wymiany komunikatów. Usługa uwidacznia punkty końcowe aplikacji (a także zero lub więcej punktów końcowych infrastruktury), a klient generuje punkt końcowy, który jest zgodny z jednego z punktów końcowych usługi.  
  
 *Punktu końcowego* opisano w taki sposób, oparta na standardach, gdzie mają być wysyłane wiadomości, jak mają być wysyłane i jak powinien wyglądać komunikaty. Usługi można ujawnić te informacje jako metadane, która pozwala na przetwarzanie do generowania odpowiednich klientów usługi WCF i komunikacji klientów *stosy*.  
  
### <a name="communication-protocols"></a>Protokoły komunikacyjne  
 Jeden wymagany jest element stosu komunikacji *protokół transportowy*. Komunikaty mogą być wysyłane za pośrednictwem intranetowych i internetowych za pomocą transportu wspólne, takie jak HTTP i TCP. Uwzględniono innych transportów obsługujące komunikację z aplikacjami usługi kolejkowania komunikatów i węzły w sieci równorzędnej siatki. Można dodać więcej mechanizmy transportu za pomocą punktów wbudowane rozszerzenia programu WCF.  
  
 Innego wymaganego elementu w stosie komunikacji jest kodowania, które określa sposób formatowania dowolnego z podanym komunikatem. Usługi WCF zapewnia formie następującego kodowania:  
  
-   Kodowanie, interoperacyjne kodowania tekstu.  
  
-   Komunikat transmisji optymalizacji mechanizm (MTOM) kodowanie, czyli sposób interoperacyjny efektywne wysyłanie danych binarnych bez struktury, do i z usługi.  
  
-   Binarny kodowanie transferu wydajne.  
  
 Mechanizmy bardziej kodowania (na przykład kompresji kodowanie) można dodać za pomocą punktów wbudowane rozszerzenia programu WCF.  
  
### <a name="message-patterns"></a>Wzorce wiadomości  
 Usługi WCF obsługuje kilka wzorce obsługi komunikatów, w tym typu żądanie odpowiedź, jednokierunkowe i komunikację dupleksową. Innego transportu obsługują różne wzorce obsługi komunikatów, a zatem wpływają na typy interakcji, które obsługują. Interfejsy API usługi WCF i środowisko uruchomieniowe również ułatwić do wysyłania wiadomości w sposób bezpieczny i niezawodny.  
  
## <a name="wcf-terms"></a>WCF Terms  
 Innych pojęć i terminów używanych w dokumentacji usługi WCF m.in.  
  
  — komunikat  
 Niezależna jednostka danych, który może zawierać kilka elementów, w tym nagłówki i treść.  
  
 usługa  
 Konstrukcja, która udostępnia jeden lub więcej punktów końcowych z każdego punktu końcowego udostępnianie co najmniej jednej operacji usługi.  
  
 endpoint  
 Konstrukcja w wiadomości, które są wysyłane lub odbierane (lub obu). Składa się z lokalizacji (adres), która określa, gdzie mogą być wysyłane wiadomości, specyfikacja mechanizm komunikacji (powiązanie), który opisuje, jak mają być wysyłane wiadomości, i definicji zestaw komunikatów, które mogą być wysyłane lub odbierane (lub obie) w tym Lokalizacja (kontraktu usługi), który w tym artykule opisano, jakie komunikaty mogą być wysyłane.  
  
 Usługa WCF jest uwidaczniany w świecie jako kolekcja punktów końcowych.  
  
 punkt końcowy aplikacji  
 Punktu końcowego uwidocznionego przez aplikację i który odnosi się do umowy serwisowej implementowane przez aplikację.  
  
 punkt końcowy infrastruktury  
 Punkt końcowy, który jest udostępniany przez infrastruktury w celu ułatwienia funkcji, które jest wymagane lub udostępniony przez usługę, która odnosi się do umowy serwisowej. Na przykład usługa może być punktem końcowym infrastruktury, która dostarcza informacje o metadanych.  
  
 adres  
 Określa lokalizację, w której wiadomości są odbierane. Został określony jako jednolite zasobów identyfikator (URI). Część schematu identyfikatora URI nazwy mechanizm transportu, aby osiągnąć adres, takie jak HTTP i TCP. Hierarchiczna część identyfikatora URI zawiera unikatową lokalizację, w których format jest zależny od mechanizm transportu.  
  
 Adres punktu końcowego można tworzyć adresy unikatowych punktów końcowych dla każdego punktu końcowego w usłudze, lub w określonych warunkach, aby udostępnić adres między punktami końcowymi. Poniższy przykład pokazuje adres przy użyciu protokołu HTTPS przy użyciu portów innych niż domyślne:  
  
```  
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService  
```  
  
 powiązanie  
 Definiuje, jak punkt końcowy komunikuje się dla całego świata. Klucz jest tworzony zestaw o nazwie elementy wiązania, które "stos" jedną nad drugą do tworzenia infrastruktury komunikacji składników. Co najmniej powiązanie definiuje transportu (np. HTTP lub TCP) i kodowanie używane (np. tekstowo lub binarnie). Powiązanie może zawierać elementy wiązania, które określają szczegóły, takie jak mechanizmów zabezpieczeń używanych do zabezpieczenia wiadomości lub wzorzec wiadomości, używany przez punkt końcowy. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług](../../../docs/framework/wcf/configuring-services.md).  
  
 element powiązania  
 Reprezentuje określonym wystąpieniem powiązania, takich jak transportu, kodowania, implementacja protokołu poziomie infrastruktury (na przykład WS-ReliableMessaging) lub jakikolwiek inny składnik stosu komunikacji.  
  
 zachowania  
 Składnik, który kontroluje różne aspekty środowiska wykonawczego usługi, punkt końcowy, określoną operację lub klienta. Zachowania są pogrupowane według zakresu: wspólny zbiór wykonywanych czynności mają wpływ na wszystkie punkty końcowe globalnie, zachowania usług mają wpływ na aspektach związanych tylko z usługą, zachowań punktu końcowego wpływa na tylko właściwości powiązanych z punktu końcowego i zachowania poziomu operacji mają wpływ na określonym operacje. Na przykład jeden zachowanie usługi jest ograniczanie przepustowości, która określa, w jaki sposób usługa reaguje, gdy nadmiar wiadomości nękania przeciąży jego możliwości obsługi. Zachowanie punktu końcowego, z drugiej strony, określa tylko aspektów, które są istotne dla punktów końcowych, takich jak i gdzie można znaleźć poświadczenia zabezpieczeń.  
  
 powiązania dostarczane przez system  
 Usługi WCF obejmuje wiele powiązań dostarczanych przez system. Te są kolekcjami elementów, które są zoptymalizowane pod kątem konkretnych scenariuszy wiązania. Na przykład <xref:System.ServiceModel.WSHttpBinding> zaprojektowano na potrzeby współdziałania z usługami, które implementują różne WS-* specyfikacji. Te wstępnie zdefiniowanych powiązań zaoszczędzić czas, przez umożliwienie korzystania z tych opcji, które można poprawnie zastosować do danego scenariusza. Jeśli wstępnie zdefiniowanych powiązań nie spełnia wymagań, można utworzyć własnego niestandardowego powiązania.  
  
 Konfiguracja i kodowania  
 Kontrola aplikacji może odbywać się albo za pomocą kodowania, za pomocą konfiguracji lub jako kombinację obu tych. Konfiguracja ma tę zaletę, umożliwiając kogoś innego niż dla deweloperów (na przykład administrator sieci), aby ustawić parametry klienta i usługi, po zapisaniu kod bez konieczności ponownego kompilowania. Konfiguracja nie tylko umożliwia ustawianie wartości, takie jak adresy punktów końcowych, ale umożliwia także ściślej kontrolować, umożliwiając Dodaj punkty końcowe, powiązania i zachowania. Kodowania umożliwia deweloperowi zachować ścisłą kontrolę nad wszystkie składniki usługi lub klienta, a wszystkie ustawienia zrobić za pomocą konfiguracji można być kontrolowane i w razie potrzeby zastąpione przez kod.  
  
 Operacja usługi  
 Procedura zdefiniowane w kodzie usługi, który implementuje funkcje dla danej operacji. Ta operacja jest uwidaczniany dla klientów jako metody dla klienta programu WCF. Metoda może zwracają wartość, można wykonać opcjonalne liczbę argumentów, lub nie przyjmują argumentów i zwrócić odpowiedź nie. Na przykład operacja, która działa jako prosty "Hello" może służyć jako powiadomienie o obecności klienta lub w celu rozpoczęcia serii operacji.  
  
 kontrakt usługi  
 Łączy ze sobą wiele powiązanych operacji w pojedynczą jednostkę funkcjonalności. Kontrakt można zdefiniować ustawienia poziomu usługi, takie jak przestrzeń nazw usługi, odpowiedni kontrakt wywołania zwrotnego i inne takie ustawienia. W większości przypadków kontrakt jest definiowany przez tworzenie interfejsu w wybranym języku programowania i stosowanie <xref:System.ServiceModel.ServiceContractAttribute> atrybutu do interfejsu. Wyniki kodu rzeczywistej usługi przez zaimplementowanie interfejsu.  
  
 Kontrakt operacji  
 Kontrakt operacji określa parametry oraz zwracany typ operacji. Podczas tworzenia interfejsu, który definiuje kontrakt usługi, oznaczającego kontrakt operacji, stosując <xref:System.ServiceModel.OperationContractAttribute> atrybut do każdej definicji metody, która jest częścią kontraktu. Operacje mogą być modelowane jako biorąc pojedynczy komunikat i zwraca pojedynczą wiadomość lub pobierania zestaw typów i zwracająca typ. W tym ostatnim przypadku system określi format wiadomości, które muszą być wymieniane dla tej operacji.  
  
 kontrakt komunikatu  
 W tym artykule opisano formatu wiadomości. Na przykład deklaruje, czy elementy wiadomości powinny przejść w nagłówki i treść, jaki poziom zabezpieczeń powinny być stosowane do elementy wiadomości i tak dalej.  
  
 kontrakt błędu  
 Może być skojarzony z operacją usługi do określenia błędów, które mogą być zwracane do obiektu wywołującego. Operacja może mieć zero lub więcej błędów skojarzonych z nim. Takie błędy występują błędy protokołu SOAP, które są modelowane jako wyjątki w modelu programowania.  
  
 kontrakt danych  
 Opisy w metadanych typów danych, które korzysta z usługi. Dzięki temu inne osoby do współdziałania z usługą. Typy danych można w dowolnej części wiadomości, na przykład, jako parametry typów lub je zwracają. Usługa używa tylko typów prostych, czy nie trzeba jawnie użyć kontraktów danych.  
  
 hosting  
 Usługa musi być obsługiwana przez niektóre procesy. A *hosta* to aplikacja, która określa okres istnienia usługi. Usługi można samodzielnie hostowane lub zarządza istniejącego procesu hostingu.  
  
 hostowanie samoobsługowe  
 Usługa, która działa w ramach aplikacji procesu utworzonego przez dewelopera. Deweloper określa jego okres istnienia, ustawia właściwości usługi, zostanie otwarty usługi (która ustawia go w trybie nasłuchiwania) i zamknięcie usługi.  
  
 proces hostingu  
 Aplikacja, która jest przeznaczona do hostowania usług. Obejmują one Internet Information Services (IIS), usługi aktywacji Windows (WAS) i usługi Windows. W tych scenariuszach hostowanych host steruje okres istnienia usługi. Na przykład za pomocą usług IIS można skonfigurować katalog wirtualny, który zawiera plik zestawu i konfiguracji usługi. Gdy wiadomość zostaje odebrana, usługi IIS uruchamia usługę i kontroluje cały okres ich istnienia.  
  
 tworzenie instancji  
 Usługa wykorzystuje model wystąpień. Istnieją trzy modele wystąpień: "jeden" w jakiej pojedynczy obiekt CLR usług wszystkich klientów; " dla połączenia"w jakiej tworzony jest nowy obiekt CLR, aby obsłużyć każde wywołanie klienta; i "wg"sesji, w której zestaw CLR obiektów, zostanie utworzony, jeden dla każdego oddzielną sesję. Wybór modelu wystąpień, zależy od wymagań aplikacji i oczekiwanego wzorca użycia usługi.  
  
 Aplikacja kliencka  
 Program, który wymienia komunikatów za pomocą jednego lub więcej punktów końcowych. Aplikacja kliencka rozpoczyna się od tworzenia wystąpienia obiektu klienta programu WCF i wywoływania metod klienta platformy WCF. Należy pamiętać, że pojedynczej aplikacji może być zarówno klient, jak i usługi.  
  
 Kanał  
 Konkretną implementację elementu powiązania. Powiązanie reprezentuje konfiguracji, a kanał jest implementacja skojarzone z tej konfiguracji. Dlatego jest skojarzony z każdego elementu powiązania kanału. Kanały stosu na siebie, aby utworzyć konkretną implementację powiązania: stos kanału.  
  
 Klienta programu WCF  
 Konstrukcja aplikacji klienckiej, która udostępnia operacje usługi jako metody (w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] programowania w języku, np. Visual Basic lub Visual C#). Każda aplikacja może obsługiwać klienta WCF, łącznie z aplikacją, który jest hostem usługi. W związku z tym istnieje możliwość utworzyć usługę, która obejmuje klienci WCF innych usług.  
  
 Klienta programu WCF mogą być generowane automatycznie za pomocą [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) i wskazując uruchomiona usługa, która publikuje metadane.  
  
 metadane  
 W usłudze opisuje cechy usługa, która musi wiedzieć, do komunikowania się z usługą zewnętrznej jednostki. Metadane mogą być używane przez [narzędzia narzędzie metadanych elementu ServiceModel (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) do generowania klienta WCF i towarzyszące konfiguracji, który aplikacja kliencka może służyć do interakcji z usługą.  
  
 Metadane udostępnianych przez usługę obejmuje dokumentów schematu XML definiujące kontraktu danych, usługi i dokumenty WSDL, które opisują metody usługi.  
  
 Po włączeniu metadanych dla usługi jest generowany automatycznie przez architekturę WCF, sprawdzając usługę i jej punkty końcowe. Aby opublikować metadanych z usługi, musisz jawnie włączyć zachowanie metadanych.  
  
 zabezpieczenia  
 W programie WCF obejmuje poufność (szyfrowanie wiadomości, aby zapobiec podsłuchiwaniu), integralność (oznacza wykrywania naruszeniu wiadomości), uwierzytelniania (oznacza sprawdzanie poprawności serwery i klienci) i autoryzacji (kontrola dostępu do zasoby). Te funkcje są udostępniane przez albo wykorzystaniem istniejących mechanizmów zabezpieczeń, np. TLS za pośrednictwem protokołu HTTP (znany także jako HTTPS) lub wdrażanie co najmniej jedną z różnych WS-* specyfikacje zabezpieczeń.  
  
 Tryb zabezpieczeń Transport  
 Określa, że poufność, integralność i uwierzytelniania są udostępniane przez mechanizmy warstwy transportu (np. HTTPS). Korzystając z transportu, takich jak HTTPS, w tym trybie ma tę zaletę, są wydajne pod względem wydajności i dobrze zrozumiałych ze względu na jego występowania w Internecie. Wadą jest to, że tego rodzaju zabezpieczeń są stosowane osobno na każdy przeskok w ścieżce komunikacji wprowadzania komunikacji podatny na ataki man-in middle".  
  
 Tryb zabezpieczeń komunikatów  
 Określa, czy zabezpieczenia dzięki wdrożeniu co najmniej jednym specyfikacji zabezpieczenia, takie jak specyfikację o nazwie [zabezpieczeń usług sieci Web: Zabezpieczenia komunikatów SOAP](https://go.microsoft.com/fwlink/?LinkId=94684). Każdy komunikat zawiera mechanizmy niezbędne do zapewnienia bezpieczeństwa podczas jego przesyłania i włączyć odbiorniki naruszeniem i do odszyfrowywania wiadomości. W tym sensie zabezpieczenia są hermetyzowane w ramach każdej wiadomości, zapewniając bezpieczeństwo end-to-end wielu przeskoków. Ponieważ informacje o zabezpieczeniach staje się częścią wiadomości, istnieje również możliwość obejmują wiele rodzajów poświadczenia za pomocą komunikatu (są one określane jako *oświadczeń*). Takie podejście również ma tę zaletę, włączania komunikat, aby bezpiecznie przesyłane za pośrednictwem dowolnego transportu, w tym wiele transportu między jego początkowego i docelowego. Wadą tego podejścia jest złożoności mechanizmów kryptograficznych zatrudnieni, wynikiem wpływ na wydajność.  
  
 transportu przy użyciu trybu zabezpieczenia poświadczeń wiadomości  
 Określa użycie warstwy transportowej zapewnienie poufności, uwierzytelniania i integralności wiadomości, gdy każda komunikatów może zawierać wiele poświadczeń (oświadczenia) są wymagane przez odbiorców w wiadomości.  
  
 WS-*  
 Skrót dla elementów z wciąż rosnącego zestawu specyfikacji usługi sieci Web (WS), takich jak usługi WS-Security, WS-ReliableMessaging i tak dalej, które są implementowane w usłudze WCF.  
  
## <a name="see-also"></a>Zobacz także
- [Co to jest program Windows Communication Foundation](../../../docs/framework/wcf/whats-wcf.md)
- [Architektura WCF (Windows Communication Foundation)](../../../docs/framework/wcf/architecture.md)
