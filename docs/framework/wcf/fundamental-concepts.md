---
title: Podstawowe pojęcia programu Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], concepts
- concepts [WCF]
- fundamentals [WCF]
- Windows Communication Foundation [WCF], concepts
ms.assetid: 3e7e0afd-7913-499d-bafb-eac7caacbc7a
ms.openlocfilehash: 360479a2ba17c4542d61a737856d23992296e276
ms.sourcegitcommit: 32a575bf4adccc901f00e264f92b759ced633379
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/04/2019
ms.locfileid: "74802311"
---
# <a name="fundamental-windows-communication-foundation-concepts"></a>Podstawowe pojęcia programu Windows Communication Foundation

Ten dokument zawiera ogólny widok architektury Windows Communication Foundation (WCF). Ma ona na celu wyjaśnienie najważniejszych pojęć i ich dopasowania. Aby zapoznać się z samouczkiem dotyczącym tworzenia najprostszej wersji usługi i klienta WCF, zobacz [samouczek wprowadzenie](getting-started-tutorial.md). Aby poznać programowanie WCF, zobacz [podstawowe programowanie WCF](basic-wcf-programming.md).

## <a name="wcf-fundamentals"></a>Podstawy WCF

WCF to środowisko uruchomieniowe i zestaw interfejsów API służących do tworzenia systemów wysyłających komunikaty między usługami i klientami. Ta sama infrastruktura i interfejsy API są używane do tworzenia aplikacji, które komunikują się z innymi aplikacjami w tym samym systemie komputerowym lub w systemie, który znajduje się w innej firmie i jest dostępny za pośrednictwem Internetu.

### <a name="messaging-and-endpoints"></a>Wiadomości i punkty końcowe

Program WCF jest oparty na koncepcji komunikacji opartej na komunikatach, a wszystkie elementy, które mogą być modelowane jako wiadomości (na przykład żądanie HTTP lub komunikat usługi kolejkowania komunikatów (znany również jako MSMQ), mogą być reprezentowane w jednolity sposób w modelu programowania. Umożliwia to ujednolicony interfejs API w różnych mechanizmach transportu.

Model odróżnia _klientów_, czyli aplikacje inicjujące komunikację i _usługi_, które są aplikacjami, które oczekują na komunikowanie się z nimi i odpowiadają na tę komunikację. Pojedyncza aplikacja może działać zarówno jako klient, jak i usługa. Aby zapoznać się z przykładami, zobacz [usługi dupleks](./feature-details/duplex-services.md) i [sieci peer-to-peer](./feature-details/peer-to-peer-networking.md).

Komunikaty są wysyłane między punktami końcowymi. _Punkty końcowe_ to miejsca, w których komunikaty są wysyłane lub odbierane (lub oba), a także definiują wszystkie informacje wymagane do wymiany komunikatów. Usługa udostępnia jeden lub więcej punktów końcowych aplikacji (a także zero lub więcej punktów końcowych infrastruktury), a klient generuje punkt końcowy, który jest zgodny z jednym z punktów końcowych usługi.

_Punkt końcowy_ opisuje w standardowym sposobie, w jaki wiadomości powinny być wysyłane, jak powinny być wysyłane i jak powinny wyglądać komunikaty. Usługa może uwidaczniać te informacje jako metadane, które klienci mogą przetwarzać w celu generowania odpowiednich _stosów_komunikacji i klientów programu WCF.

### <a name="communication-protocols"></a>Protokoły komunikacyjne

Jednym z wymaganych elementów stosu komunikacji jest _Protokół transportowy_. Komunikaty mogą być wysyłane za pośrednictwem sieci intranet i Internetu przy użyciu wspólnych transportów, takich jak HTTP i TCP. Dołączono inne transporty obsługujące komunikację z aplikacjami i węzłami usługi kolejkowania komunikatów w sieci równorzędnej. Więcej mechanizmów transportu można dodać przy użyciu wbudowanych punktów rozszerzenia programu WCF.

Innym wymaganym elementem w stosie komunikacyjnym jest kodowanie, które określa sposób formatowania danego komunikatu. Funkcja WCF udostępnia następujące kodowania:

- Kodowanie tekstu, kodowanie międzyoperacyjnego.

- Kodowanie mechanizmu optymalizacji transmisji wiadomości (MTOM), który jest międzyoperacyjnym sposobem wydajnego wysyłania danych binarnych bez struktury do i z usługi.

- Kodowanie binarne w celu wydajnego transferu.

Więcej mechanizmów kodowania (na przykład kodowania kompresji) można dodać przy użyciu wbudowanych punktów rozszerzenia programu WCF.

### <a name="message-patterns"></a>Wzorce komunikatów

Usługa WCF obsługuje kilka wzorców obsługi komunikatów, takich jak żądanie-odpowiedź, jednokierunkowe i dupleksowe. Różne transporty obsługują różne wzorce obsługi komunikatów i w ten sposób wpływają na typy interakcji, które są przez nie obsługiwane. Interfejsy API i środowisko uruchomieniowe WCF ułatwiają również bezpieczne i niezawodne wysyłanie komunikatów.

## <a name="wcf-terms"></a>Warunki WCF

Inne pojęcia i terminy używane w dokumentacji programu WCF obejmują następujące zagadnienia:

**Komunikat**  
 Samodzielna jednostka danych, która może składać się z kilku części, w tym treści i nagłówków.

**Usługa**  
 Konstrukcja, która uwidacznia jeden lub więcej punktów końcowych, przy czym każdy punkt końcowy uwidacznia jedną lub więcej operacji usługi.

**Punkt końcowy**  
 Konstrukcja, w której wysyłane lub odbierane są komunikaty (lub oba te elementy). Składa się z lokalizacji (adresu), która określa, gdzie mogą być wysyłane komunikaty, specyfikację mechanizmu komunikacji (powiązanie) opisującą sposób wysyłania komunikatów oraz definicję zestawu komunikatów, które mogą być wysyłane lub odbierane (lub oba te elementy). Lokalizacja (kontrakt usługi) opisująca, jaki komunikat można wysłać.

Usługa WCF jest narażona na świecie jako zbiór punktów końcowych.

**Punkt końcowy aplikacji**  
 Punkt końcowy uwidoczniony przez aplikację i odpowiadający kontraktowi usługi zaimplementowanemu przez aplikację.

**Punkt końcowy infrastruktury**  
 Punkt końcowy, który jest udostępniany przez infrastrukturę w celu ułatwienia funkcjonalności, która jest wymagana lub oferowana przez usługę, która nie jest powiązana z umową usługi. Na przykład usługa może mieć punkt końcowy infrastruktury, który zawiera informacje o metadanych.

**Adres**  
 Określa lokalizację, w której odbierane są komunikaty. Jest on określony jako Uniform Resource Identifier (URI). Część schematu identyfikatora URI nazywa mechanizm transportu, który ma być używany do uzyskiwania dostępu do adresu, takiego jak HTTP i TCP. Hierarchiczna część identyfikatora URI zawiera unikatową lokalizację, której format zależy od mechanizmu transportowego.

Adres punktu końcowego umożliwia tworzenie unikatowych adresów punktów końcowych dla każdego punktu końcowego w usłudze lub w określonych warunkach, aby udostępnić adres między punktami końcowymi. Poniższy przykład przedstawia adres przy użyciu protokołu HTTPS z portem innym niż domyślny:

```http
HTTPS://cohowinery:8005/ServiceModelSamples/CalculatorService
```

**Powiązanie**  
 Definiuje, w jaki sposób punkt końcowy komunikuje się ze światem. Jest zbudowana z zestawu składników nazywanych elementami powiązania, które "stosują" jeden na drugim, aby utworzyć infrastrukturę komunikacji. Co najmniej, powiązanie definiuje transport (na przykład HTTP lub TCP) i używane kodowanie (na przykład tekst lub binarny). Powiązanie może zawierać elementy wiążące, które określają szczegóły, takie jak mechanizmy zabezpieczeń używane do zabezpieczania komunikatów lub wzorzec wiadomości używany przez punkt końcowy. Aby uzyskać więcej informacji, zobacz [Konfigurowanie usług](configuring-services.md).

**Element powiązania**  
 Reprezentuje szczególny element powiązania, na przykład transport, kodowanie, implementację protokołu poziomu infrastruktury (na przykład WS-ReliableMessaging) lub dowolny inny składnik stosu komunikacji.

**Zachowania**  
 Składnik kontrolujący różne aspekty czasu wykonywania usługi, punkt końcowy, konkretną operację lub klienta. Zachowania są pogrupowane według zakresu: typowe zachowania mają na celu globalne wpływ na wszystkie punkty końcowe, zachowania usługi dotyczą tylko aspektów związanych z usługą, zachowania punktów końcowych wpływają wyłącznie na właściwości powiązane z punktem końcowym, a zachowania poziomu operacji mają wpływ na konkretną składowa. Na przykład, jedno zachowanie usługi ma ograniczenia, które określa, jak działa usługa, gdy nadmiarowe komunikaty grożą zaprzeciążeniem możliwości obsługi. Zachowanie punktu końcowego, z drugiej strony, kontroluje tylko aspekty, które są istotne dla punktów końcowych, takich jak i gdzie można znaleźć poświadczenia zabezpieczeń.

**Powiązania dostarczone przez system**  
 Program WCF zawiera wiele powiązań dostarczonych przez system. Są to kolekcje elementów powiązania, które są zoptymalizowane pod kątem określonych scenariuszy. Na przykład <xref:System.ServiceModel.WSHttpBinding> jest zaprojektowana pod kątem współdziałania z usługami, które implementują różne specyfikacje WS-\*. Te wstępnie zdefiniowane powiązania oszczędzają czas, wyświetlając tylko te opcje, które można prawidłowo zastosować do konkretnego scenariusza. Jeśli wstępnie zdefiniowane powiązanie nie spełnia wymagań użytkownika, można utworzyć własne niestandardowe powiązania.

**Konfiguracja a kodowanie**  
 Kontrolę nad aplikacją można wykonać za pomocą kodowania, za pomocą konfiguracji lub kombinacji obu tych elementów. W konfiguracji można umożliwić innym osobom niż deweloper (na przykład administratora sieci) Ustawianie parametrów klienta i usługi po napisaniu kodu i bez konieczności ponownego kompilowania. Konfiguracja umożliwia nie tylko Ustawianie wartości takich jak adresy punktów końcowych, ale również umożliwia dalsze kontrolowanie, umożliwiając dodawanie punktów końcowych, powiązań i zachowań. Kodowanie umożliwia deweloperowi zachowanie ścisłej kontroli nad wszystkimi składnikami usługi lub klienta, a także wszelkie ustawienia wykonywane przez konfigurację, a w razie potrzeby przesłonięte przez kod.

**Operacja usługi**  
 Procedura zdefiniowana w kodzie usługi, która implementuje funkcje dla operacji. Ta operacja jest udostępniana klientom jako metody na kliencie WCF. Metoda może zwracać wartość i może przyjmować opcjonalną liczbę argumentów lub nie przyjmować argumentów i nie zwraca odpowiedzi. Na przykład operacja, która działa jako prosta "Hello", może służyć jako powiadomienie o obecności klienta i rozpocząć serię operacji.

**Kontrakt usługi**  
 Łączy wiele operacji związanych z pojedynczą jednostką funkcjonalną. Kontrakt może definiować ustawienia poziomu usługi, takie jak przestrzeń nazw usługi, odpowiedni kontrakt wywołania zwrotnego i inne ustawienia. W większości przypadków umowa jest definiowana przez utworzenie interfejsu w wybranym języku programowania i zastosowanie atrybutu <xref:System.ServiceModel.ServiceContractAttribute> do interfejsu. Rzeczywisty kod usługi powstaje przez implementację interfejsu.

**Kontrakt operacji**  
 Kontrakt operacji definiuje parametry i zwracany typ operacji. Podczas tworzenia interfejsu, który definiuje kontrakt usługi, należy wykonać kontrakt operacji, stosując atrybut <xref:System.ServiceModel.OperationContractAttribute> do każdej definicji metody, która jest częścią kontraktu. Operacje mogą być modelowane jako przejmowanie pojedynczej wiadomości i zwracanie pojedynczej wiadomości lub jako zestawu typów i zwracanie typu. W tym drugim przypadku system określi Format komunikatów, które muszą być wymieniane dla tej operacji.

**Kontrakt komunikatu**  
 Opisuje format wiadomości. Na przykład deklaruje, czy elementy wiadomości powinny znajdować się w nagłówkach, a treści, jakiego poziomu zabezpieczeń należy zastosować do elementów tego komunikatu itd.

**Umowa dotycząca błędów**  
 Można skojarzyć z operacją usługi, aby zauważyć błędy, które mogą zostać zwrócone do obiektu wywołującego. Z operacją może być skojarzonych zero lub więcej błędów. Te błędy są błędami protokołu SOAP, które są modelowane jako wyjątki w modelu programowania.

**Kontrakt danych**  
 Opisy w metadanych typów danych używanych przez usługę. Dzięki temu inne osoby mogą współdziałać z usługą. Typy danych mogą być używane w dowolnej części komunikatu, na przykład jako parametry lub typy zwracane. Jeśli usługa używa tylko typów prostych, nie ma potrzeby jawnego używania kontraktów danych.

**Hosting**  
 Usługa musi być hostowana w pewnym procesie. _Host_ to aplikacja, która kontroluje okres istnienia usługi. Usługi mogą być samoobsługowe lub zarządzane przez istniejący proces hostingu.

**Usługa samodzielna**  
 Usługa działająca w ramach aplikacji przetwarzanej utworzonej przez dewelopera. Deweloper kontroluje swój okres istnienia, ustawia właściwości usługi, otwiera usługę (która ustawia ją w tryb nasłuchiwania) i zamyka usługę.

**Proces hostingu**  
 Aplikacja, która jest przeznaczona do hostowania usług. Obejmują one Internet Information Services (IIS), usługi aktywacji systemu Windows (WAS) i usługi systemu Windows. W tych scenariuszach hostowanych Host kontroluje okres istnienia usługi. Na przykład przy użyciu usług IIS można skonfigurować katalog wirtualny, który zawiera zestaw usługi i plik konfiguracji. Po odebraniu komunikatu Usługa IIS uruchamia usługę i kontroluje jej okres istnienia.

**Tworzenie wystąpienia**  
 Usługa ma model wystąpień. Istnieją trzy modele wystąpienia: "Single", w których pojedynczej usłudze obiektów CLR wszyscy klienci; " na wywołanie "w którym tworzony jest nowy obiekt CLR w celu obsługi każdego wywołania klienta; i "na sesję", w której tworzony jest zestaw obiektów CLR, po jednej dla każdej oddzielnej sesji. Wybór modelu wystąpienia zależy od wymagań aplikacji i oczekiwanego wzorca użycia usługi.

**Aplikacja kliencka**  
 Program, który wymienia komunikaty z co najmniej jednym elementem końcowym. Aplikacja kliencka rozpoczyna się od utworzenia wystąpienia klienta WCF i wywoływania metod klienta programu WCF. Należy pamiętać, że pojedyncza aplikacja może być zarówno klientem, jak i usługą.

**Channel**  
 Konkretna implementacja elementu powiązania. Powiązanie reprezentuje konfigurację, a kanał jest implementacją skojarzoną z tą konfiguracją. W związku z tym istnieje kanał skojarzony z każdym elementem powiązania. Stos kanałów na siebie, aby utworzyć konkretną implementację powiązania: stos kanałów.

**Klient WCF**  
 Konstrukcja klient-aplikacja, która uwidacznia operacje usługi jako metody (w wybranym języku programowania .NET Framework, takich jak Visual Basic lub Wizualizacja C#). Każda aplikacja może obsługiwać klienta WCF, w tym aplikację, która hostuje usługę. W związku z tym można utworzyć usługę, która obejmuje klientów programu WCF innych usług.

Klienta programu WCF można automatycznie wygenerować przy użyciu narzędzia do obsługi [metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) i wskazać w uruchomionej usłudze, która publikuje metadane.

**Metadane**  
 W usłudze program opisuje charakterystykę usługi, którą zewnętrzna jednostka musi zrozumieć, aby komunikować się z usługą. Metadane mogą być używane przez narzędzie do obsługi [metadanych ServiceModel (Svcutil. exe)](servicemodel-metadata-utility-tool-svcutil-exe.md) w celu wygenerowania klienta programu WCF i dołączonej konfiguracji, która może być używana przez aplikację kliencką do współpracy z usługą.

Metadane udostępniane przez usługę obejmują dokumenty schematu XML, które definiują kontrakt danych usługi i dokumenty WSDL opisujące metody usługi.

Po włączeniu tej funkcji metadane usługi są generowane automatycznie przez program WCF przez sprawdzenie usługi i jej punktów końcowych. Aby opublikować metadane z usługi, należy jawnie włączyć zachowanie metadanych.

**Security**  
 W programie WCF obejmuje poufność (szyfrowanie komunikatów, aby zapobiec podsłuchiwaniu), integralność (środki na potrzeby wykrywania manipulowania komunikatem), uwierzytelnianie (sposób sprawdzania poprawności serwerów i klientów) oraz autoryzację (kontrolę dostępu do zasoby). Te funkcje są udostępniane przy użyciu istniejących mechanizmów zabezpieczeń, takich jak TLS przez HTTP (znanego również jako HTTPS) lub przez implementację co najmniej jednej z różnych specyfikacji zabezpieczeń WS-\*.

**Tryb zabezpieczeń transportu**  
 Określa, że poufność, integralność i uwierzytelnianie są udostępniane przez mechanizmy warstwy transportowej (takie jak HTTPS). W przypadku korzystania z transportu, takiego jak HTTPS, ten tryb ma zaletę wydajnej wydajności i jest zrozumiały ze względu na jego powszechność w Internecie. Wadą jest to, że ten rodzaj zabezpieczeń jest stosowany osobno dla każdego przeskoku w ścieżce komunikacji, co sprawia, że komunikacja jest podatna na ataki "man in the middle".

**Tryb zabezpieczeń wiadomości**  
 Określa, że zabezpieczenia są zapewniane przez implementację co najmniej jednej specyfikacji zabezpieczeń, takiej jak specyfikacja o nazwie [zabezpieczenia usług w sieci Web: zabezpieczenia komunikatów protokołu SOAP](http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-soap-message-security-1.0.pdf). Każdy komunikat zawiera niezbędne mechanizmy zapewnienia bezpieczeństwa w trakcie jego przesyłania oraz umożliwienie odbiornikom wykrywania naruszenia i odszyfrowywania wiadomości. W tym sensie zabezpieczenia są hermetyzowane w każdym komunikacie, zapewniając kompleksowe zabezpieczenia dla wielu przeskoków. Ze względu na to, że informacje o zabezpieczeniach staną się częścią komunikatu, można również uwzględnić wiele rodzajów poświadczeń z komunikatem (są one określane jako _oświadczenia_). Takie podejście umożliwia również umożliwienie bezpiecznego przesyłania komunikatów w ramach dowolnego transportu, w tym wielu transportów między jej źródłem i miejscem docelowym. Wadą tej metody jest złożoność stosowanych mechanizmów kryptograficznych, co skutkuje wpływem na wydajność.

**Transport z użyciem poświadczeń komunikatów tryb zabezpieczeń**  
 Określa użycie warstwy transportowej w celu zapewnienia poufności, uwierzytelniania i integralności komunikatów, natomiast każdy komunikat może zawierać wiele poświadczeń (oświadczeń) wymaganych przez odbiorniki wiadomości.

**WS-\***  
 Skrót dla rosnącego zestawu specyfikacji usługi sieci Web (WS), takich jak WS-Security, WS-ReliableMessaging i tak dalej, które są implementowane w programie WCF.

## <a name="see-also"></a>Zobacz także

- [Co to jest program Windows Communication Foundation](whats-wcf.md)
- [Architektura WCF (Windows Communication Foundation)](architecture.md)
