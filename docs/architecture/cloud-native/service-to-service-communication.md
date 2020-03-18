---
title: Komunikacja między serwisem
description: Dowiedz się, jak zapleczu mikrousług w chmurze natywne komunikować się z innymi mikrousług zaplecza.
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: a5124b8b83f62ff17b1230ead63db26e0c1f2a5b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401600"
---
# <a name="service-to-service-communication"></a>Komunikacja między serwisem

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Przenoszenie z klienta frontonu, teraz adres mikrousług zaplecza komunikować się ze sobą.

Podczas konstruowania aplikacji natywnej dla chmury, należy zachować czułą na sposób świadczenia usług zaplecza komunikować się ze sobą. Idealnie, im mniej komunikacji między usługami, tym lepiej. Jednak unikanie nie zawsze jest możliwe, ponieważ usługi zaplecza często polegają na sobie nawzajem, aby ukończyć operację.

Istnieje kilka powszechnie akceptowanych podejść do wdrażania komunikacji między usługami. *Rodzaj interakcji komunikacyjnej* często określa najlepsze podejście.

Należy wziąć pod uwagę następujące typy interakcji:

- *Kwerenda* — gdy mikrousługi wywołujące wymaga odpowiedzi z wywoływanej mikrousługi, takich jak "Hej, daj mi informacje o nabywcy dla danego identyfikatora klienta."

- *Polecenie* — gdy mikrousługi wywołujące wymaga innej mikrousługi do wykonania akcji, ale nie wymaga odpowiedzi, takich jak "Hej, po prostu wysłać to zamówienie."

- *Zdarzenie* — gdy mikrousługi, o nazwie wydawcy, wywołuje zdarzenie, że stan został zmieniony lub wystąpiła akcja. Inne mikrousługi, o nazwie subskrybentów, którzy są zainteresowani, może odpowiednio reagować na zdarzenie. Wydawca i subskrybenci nie są świadomi siebie nawzajem.

Systemy mikrousług zazwyczaj używają kombinacji tych typów interakcji podczas wykonywania operacji, które wymagają interakcji między usługami. Przyjrzyjmy się bliżej każdemu z nich i temu, jak możesz je zaimplementować.

## <a name="queries"></a>Zapytania

Wiele razy jedna mikrousługa może być konieczne *zapytanie* innego, wymagające natychmiastowej odpowiedzi, aby zakończyć operację. Mikrousługi koszyka zakupów mogą wymagać informacji o produkcie i ceny, aby dodać element do koszyka. Istnieje wiele metod implementowania operacji kwerendy.

### <a name="requestresponse-messaging"></a>Żądanie/odpowiadanie wiadomości

Jedną z opcji implementacji tego scenariusza jest dla mikrousługi zaplecza wywołującego do bezpośredniego żądania HTTP do mikrousług, które należy wykonać, pokazano na rysunku 4-8.

![Bezpośrednia komunikacja HTTP](./media/direct-http-communication.png)

**Rysunek 4-8**. Bezpośrednia komunikacja HTTP

Podczas bezpośrednich wywołań HTTP między mikrousług ami są stosunkowo proste do zaimplementowania, należy zachować ostrożność, aby zminimalizować tę praktykę. Aby rozpocząć, te wywołania są zawsze *synchroniczne* i zablokuje operację, dopóki wynik nie zostanie zwrócony lub limity czasu żądania. To, co kiedyś było niezależnymi, niezależnymi usługami, zdolnymi do samodzielnego rozwoju i częstego wdrażania, teraz staje się ze sobą powiązane. Wraz ze wzrostem sprzężenia między mikrousługami zmniejszają się ich korzyści architektoniczne.

Wykonywanie rzadkie żądanie, które sprawia, że pojedyncze bezpośrednie wywołanie HTTP do innej mikrousługi może być dopuszczalne dla niektórych systemów. Jednak wywołania dużych woluminów, które wywołują bezpośrednie wywołania HTTP do wielu mikrousług nie są wskazane. Mogą one zwiększyć opóźnienia i negatywnie wpłynąć na wydajność, skalowalność i dostępność systemu. Co gorsza, długa seria bezpośredniej komunikacji HTTP może prowadzić do głębokich i złożonych łańcuchów synchronicznych wywołań mikrousług, pokazano na rysunku 4-9:

![Łączenie zapytań HTTP](./media/chaining-http-queries.png)

**Rysunek 4-9**. Łączenie zapytań HTTP

Z pewnością można sobie wyobrazić ryzyko w projekcie pokazanym na poprzednim obrazie. Co się \#stanie, jeśli krok 3 nie powiedzie się? Albo \#krok 8 nie powiedzie się? Jak odzyskać? Co zrobić, jeśli krok \#6 jest powolny, ponieważ podstawowa usługa jest zajęta? Jak kontynuować? Nawet jeśli wszystko działa poprawnie, należy myśleć o opóźnienie, które spowoduje to wywołanie, która jest sumą opóźnienia każdego kroku.

Duży stopień sprzężenia w poprzednim obrazie sugeruje, że usługi nie były optymalnie modelowane. Byłoby behoove zespół do ponownego ich projektu.

### <a name="materialized-view-pattern"></a>Wzorzec zmaterializowanego widoku

Popularną opcją usuwania sprzężenia mikrousług jest [wzorzec widoku zmaterializowany](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). Za pomocą tego wzorca mikrousługi przechowuje własne lokalne, nieznormalizowane kopię danych, która jest własnością innych usług. Zamiast mikrousługi koszyka koszyka kwerendy katalogu produktów i cenmikrousług, utrzymuje własną lokalną kopię tych danych. Ten wzorzec eliminuje niepotrzebne sprzężenie i poprawia niezawodność i czas reakcji. Cała operacja jest wykonywana wewnątrz jednego procesu. Badamy ten wzorzec i inne problemy z danymi w rozdziale 5.

### <a name="service-aggregator-pattern"></a>Wzorzec agregatora usług

Inną opcją eliminacji sprzężenia mikrousług do mikrousług jest [mikrousługi aggregatora](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/), pokazane w kolorze fioletowym na rysunku 4-10.

![Usługa agregatora](./media/aggregator-service.png)

**Rysunek 4-10**. Mikroobsługa agregatora

Wzorzec izoluje operację, która wywołuje wiele mikrousług zaplecza, centralizując jego logiki do wyspecjalizowanej mikrousługi.  Purpurowy mikrousługi agregatora wyewidencjonowania na poprzedniej rysunku organizuje przepływ pracy dla operacji realizacji. Obejmuje wywołania kilku mikrousług zaplecza w kolejności sekwencjonowane. Dane z przepływu pracy są agregowane i zwracane do obiektu wywołującego. Mimo że nadal implementuje bezpośrednie wywołania HTTP, mikrousługi agregatora zmniejsza bezpośrednie zależności między mikrousług zaplecza.

### <a name="requestreply-pattern"></a>Wzorzec żądania/odpowiedzi

Innym podejściem do oddzielenia synchronicznych komunikatów HTTP jest [wzorzec żądania i odpowiedzi,](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html)który używa komunikacji kolejkowej. Komunikacja przy użyciu kolejki jest zawsze kanałem jednokierunkowym, z producentem wysyłającym wiadomość i odbiorcą, który ją odbiera. W tym wzorcu zaimplementowano zarówno kolejkę żądań, jak i kolejkę odpowiedzi, pokazaną na rysunku 4-11.

![Wzorzec żądania i odpowiedzi](./media/request-reply-pattern.png)

**Rysunek 4-11**. Wzorzec żądania i odpowiedzi

W tym miejscu producent wiadomości tworzy komunikat oparty na kwerendzie, który zawiera unikatowy identyfikator korelacji i umieszcza go w kolejce żądań. Usługa zużywająca się usuwa wiadomości, przetwarza je i umieszcza odpowiedź w kolejce odpowiedzi o tym samym identyfikatorze korelacji. Usługa producenta usuwa komunikat w kolejce, dopasowuje ją do identyfikatora korelacji i kontynuuje przetwarzanie. Szczegółowo opisujemy kolejki w następnej sekcji.

## <a name="commands"></a>Polecenia

Innym typem interakcji komunikacyjnej jest *polecenie*. Mikrousługi mogą wymagać innej mikrousługi do wykonania akcji. Mikrousługi zamawiania może wymagać mikrousługi wysyłki, aby utworzyć przesyłkę dla zatwierdzonego zamówienia. Na rysunku 4-12 jeden mikrousługi, o nazwie Producent, wysyła komunikat do innej mikrousługi, Konsumenta, nakazując mu coś zrobić.

![Interakcja polecenia z kolejką](./media/command-interaction-with-queue.png)

**Rysunek 4-12**. Interakcja polecenia z kolejką

Najczęściej producent nie wymaga odpowiedzi i może *wystrzelić i zapomnieć* o wiadomości. Jeśli potrzebna jest odpowiedź, konsument wysyła oddzielną wiadomość z powrotem do producenta na innym kanale. Wiadomość polecenia jest najlepiej wysyłana asynchronicznie z kolejką komunikatów. obsługiwane przez lekki broker wiadomości. Na poprzednim diagramie należy zauważyć, jak kolejka oddziela i oddziela obie usługi.

Kolejka komunikatów jest konstrukcją pośredniczącą, za pomocą której producent i konsument przekazują komunikat. Kolejki implementują asynchroniczny wzorzec obsługi wiadomości typu punkt-punkt. Producent wie, gdzie polecenie musi zostać wysłane i odpowiednio tras. Kolejka gwarantuje, że wiadomość jest przetwarzana przez dokładnie jedno z wystąpień konsumenta, które są odczytywane z kanału. W tym scenariuszu producent lub usługi konsumenckiej można skalować w sposób skalowany bez wpływu na inne. Ponadto technologie mogą być różne z każdej strony, co oznacza, że możemy mieć mikrousługi Java wywołujące mikrousługi [Golang.](https://golang.org)

W rozdziale 1 rozmawialiśmy o *usługach wspierających*. Usługi tworzenia kopii zapasowych są zasobami pomocniczymi, od których zależą systemy natywne dla chmury. Kolejki komunikatów są usługi tworzenia kopii zapasowych. Chmura platformy Azure obsługuje dwa typy kolejek komunikatów, które systemy natywne dla chmury mogą korzystać z zaimplementowania komunikatów polecenia: kolejki usługi Azure Storage queues i kolejki usługi Azure Service Bus.

### <a name="azure-storage-queues"></a>Kolejki usługi Azure Storage

Kolejki magazynu platformy Azure oferują prostą infrastrukturę kolejkowania, która jest szybka, przystępna cenowo i wspierana przez konta magazynu platformy Azure.

[Kolejki usługi Azure Storage](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction) są wyposażone w mechanizm kolejkowania oparty na architekturze REST z niezawodnymi i trwałymi wiadomościami. Zapewniają one minimalny zestaw funkcji, ale są niedrogie i przechowują miliony wiadomości. Ich pojemność wynosi do 500 TB. Pojedynczy komunikat może mieć rozmiar do 64 KB.

Dostęp do wiadomości z dowolnego miejsca na świecie można uzyskać za pośrednictwem uwierzytelnionych wywołań za pomocą protokołu HTTP lub HTTPS. Kolejki magazynu można skalować w sposób skalowany do dużej liczby równoczesnych klientów do obsługi skoków ruchu.

To powiedziawszy, istnieją ograniczenia z usługą:

- Kolejność wiadomości nie jest gwarantowana.

- Wiadomość może utrzymywać się tylko przez siedem dni, zanim zostanie automatycznie usunięta.

- Obsługa zarządzania stanem, wykrywania duplikatów lub transakcji nie jest dostępna.

Rysunek 4–13 przedstawia hierarchię kolejki usługi Azure Storage.

![Hierarchia kolejki magazynu](./media/storage-queue-hierarchy.png)

**Rysunek 4-13**. Hierarchia kolejki magazynu

Na poprzednim rysunku należy zauważyć, jak kolejki magazynu przechowują swoje wiadomości na podstawowym koncie usługi Azure Storage.

Dla deweloperów firma Microsoft udostępnia kilka bibliotek po stronie klienta i serwera do przetwarzania kolejki magazynu. Większość głównych platform jest obsługiwana, w tym .NET, Java, JavaScript, Ruby, Python i Go. Deweloperzy nigdy nie powinni komunikować się bezpośrednio z tymi bibliotekami. W ten sposób ciasno połącz kod mikrousługi z usługą Kolejki usługi Azure Storage. Jest to lepsza praktyka, aby ocieplić szczegóły implementacji interfejsu API. Wprowadzenie warstwy pośrednictwa lub pośredniego interfejsu API, który udostępnia operacje ogólne i hermetyzuje biblioteki betonowej. To luźne sprzęgło umożliwia zamianę jednej usługi kolejkowania na inną bez konieczności wprowadzania zmian w kodzie usługi linii głównej.

Kolejki usługi Azure Storage to ekonomiczna opcja implementowania komunikatów poleceń w aplikacjach natywnych dla chmury. Zwłaszcza, gdy rozmiar kolejki przekroczy 80 GB lub prosty zestaw funkcji jest dopuszczalny. Płacisz tylko za przechowywanie wiadomości; nie ma stałych opłat godzinowych.

### <a name="azure-service-bus-queues"></a>Kolejki usługi Azure Service Bus

Aby uzyskać bardziej złożone wymagania dotyczące obsługi wiadomości, należy wziąć pod uwagę kolejki usługi Azure Service Bus.

Siedząc na szczycie niezawodnej infrastruktury komunikatów, [usługa Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) obsługuje model obsługi wiadomości obsługiwany przez *brokera*. Wiadomości są niezawodnie przechowywane w brokerze (kolejki) do momentu odebrania przez konsumenta. Kolejka gwarantuje dostarczanie wiadomości FIFO (First-In/First-Out), z poszanowaniem kolejności, w jakiej wiadomości zostały dodane do kolejki.

Rozmiar wiadomości może być znacznie większy, do 256 KB. Wiadomości są zachowywane w kolejce przez nieograniczony okres czasu. Usługa Service Bus obsługuje nie tylko wywołania oparte na protokole HTTP, ale także zapewnia pełną obsługę [protokołu AMPQ.](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview) AMPQ jest otwartym standardem dla wszystkich dostawców, który obsługuje protokół binarny i wyższy stopień niezawodności.

Usługa Service Bus zapewnia bogaty zestaw funkcji, w tym [obsługę transakcji](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) i [funkcję wykrywania duplikatów.](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) Kolejka gwarantuje "co najwyżej raz dostarczenie" na wiadomość. Automatycznie odrzuca wiadomość, która została już wysłana. Jeśli producent ma wątpliwości, może ponownie wysłać ten sam komunikat, a usługa Service Bus gwarantuje, że zostanie przetworzona tylko jedna kopia. Wykrywanie duplikatów zwalnia cię z konieczności tworzenia dodatkowej infrastruktury hydraulicznej.

Dwie kolejne funkcje przedsiębiorstwa to partycjonowanie i sesje. Kolejka usługi Service Bus jest obsługiwana przez brokera pojedynczych komunikatów i przechowywana w magazynie pojedynczych komunikatów. Jednak [partycjonowanie magistrali usług](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) rozkłada kolejkę na wielu brokerów komunikatów i magazyny komunikatów. Ogólna przepływalność nie jest już ograniczona przez wydajność brokera pojedynczej wiadomości lub magazynu obsługi wiadomości. Tymczasowa awaria magazynu obsługi wiadomości nie powoduje, że kolejka partycjonowana jest niedostępna.

[Sesje magistrali usług](https://codingcanvas.com/azure-service-bus-sessions/) umożliwiają wiadomości związane z grupą. Wyobraź sobie scenariusz przepływu pracy, w którym wiadomości muszą być przetwarzane razem, a operacja została ukończona na końcu. Aby skorzystać, sesje muszą być jawnie włączone dla kolejki, a każda powiązana wiadomość musi zawierać ten sam identyfikator sesji.

Istnieją jednak pewne ważne zastrzeżenia: rozmiar kolejek usługi Service Bus jest ograniczony do 80 GB, co jest znacznie mniejsze niż to, co jest dostępne w kolejkach sklepu. Ponadto kolejki usługi Service Bus ponoszą podstawowy koszt i opłatę za operację.

Rysunek 4-14 przedstawia architekturę wysokiego poziomu kolejki usługi Service Bus.

![Kolejka usługi Service Bus](./media/service-bus-queue.png)

**Rysunek 4-14**. Kolejka usługi Service Bus

Na poprzedniej rysunku należy zwrócić uwagę na relację punkt-punkt. Dwa wystąpienia tego samego dostawcy są enqueuing wiadomości w jednej kolejce usługi Service Bus. Każda wiadomość jest używana tylko przez jeden z trzech wystąpień konsumenta po prawej stronie. Następnie omówimy sposób implementacji obsługi wiadomości, w przypadku gdy różni konsumenci mogą być zainteresowani tym samym komunikatem.

## <a name="events"></a>Zdarzenia

Kolejkowanie wiadomości jest skutecznym sposobem zaimplementowania komunikacji, w którym producent może asynchronicznie wysłać konsumentowi wiadomość. Co jednak się dzieje, gdy *wielu różnych konsumentów* jest zainteresowanych tym samym przesłaniem? Dedykowana kolejka komunikatów dla każdego konsumenta nie będzie dobrze skalowana i stałaby się trudna do zarządzania.

Aby rozwiązać ten scenariusz, przechodzimy do trzeciego typu interakcji wiadomości, *zdarzenia*. Jedna mikrousługa informuje, że wystąpiła akcja. Inne mikrousługi, jeśli zainteresowany, reagują na akcję lub zdarzenie.

Eventing jest procesem dwuetapowym. Dla zmiany danego stanu mikrousługi publikuje zdarzenie do brokera komunikatów, udostępniając go do wszystkich innych zainteresowanych mikrousług. Zainteresowanych mikrousługi jest powiadamiany przez subskrybowanie zdarzenia w brokera komunikatów. Wzorca [Publikowania/Subskrybowania](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) służy do implementowania [komunikacji opartej na zdarzeniach.](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications)

Rysunek 4-15 przedstawia mikrousługi koszyka zakupów publikujące zdarzenie z dwoma innymi mikrousługami subskrybującymi go.

![Komunikaty oparte na zdarzeniach](./media/event-driven-messaging.png)

**Rysunek 4-15**. Komunikaty oparte na zdarzeniach

Należy zwrócić uwagę na składnik *magistrali zdarzeń,* który znajduje się w środku kanału komunikacji. Jest to klasa niestandardowa, która hermetyzuje brokera komunikatów i oddziela go od podstawowej aplikacji. Mikrousługi zamawiania i inwentaryzacji niezależnie obsługiwać zdarzenie bez wiedzy o sobie nawzajem, ani mikrousługi koszyka zakupów. Gdy zarejestrowane zdarzenie zostanie opublikowane w autobusie wydarzenia, działają na nim.

Z eventing, przechodzimy od technologii kolejkowania do *tematów*. [Temat](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) jest podobny do kolejki, ale obsługuje jeden do wielu wzorca obsługi wiadomości. Jedna mikrousługa publikuje komunikat. Wiele mikrousług subskrybujących można wybrać do odbierania i działać na tej wiadomości. Rysunek 4-16 przedstawia architekturę tematu.

![Architektura tematu](./media/topic-architecture.png)

**Rysunek 4-16**. Architektura tematu

Na poprzedniej rysunku wydawcy wysyłają wiadomości do tematu. Na koniec subskrybenci otrzymują wiadomości z subskrypcji. W środku temat przekazuje wiadomości do subskrypcji na podstawie zestawu *reguł*, wyświetlanych w ciemnoniebieskich polach. Reguły działają jako filtr, który przekazuje określone wiadomości do subskrypcji. W tym miejscu zdarzenie "CreateOrder" \#zostanie wysłane \#do subskrypcji 1 \#i subskrypcji 3, ale nie do subskrypcji 2. Zdarzenie "OrderCompleted" zostanie wysłane \#do subskrypcji \#2 i subskrypcji 3.

Chmura platformy Azure obsługuje dwie różne usługi tematyczne: Tematy usługi Azure Service Bus i Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Tematy usługi Azure Service Bus

Siedząc na szczycie tego samego modelu komunikatów pośrednictwa niezawodnego kolejek usługi Azure Service Bus są [tematy usługi Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Temat może odbierać wiadomości od wielu niezależnych wydawców i wysyłać wiadomości do maksymalnie 2000 subskrybentów. Subskrypcje mogą być dynamicznie dodawane lub usuwane w czasie wykonywania bez zatrzymywania systemu lub ponownego tworzenia tematu.

Wiele zaawansowanych funkcji z kolejek usługi Azure Service Bus są również dostępne dla tematów, w tym [wykrywanie duplikatów](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) i [obsługa transakcji](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions). Domyślnie tematy usługi Service Bus są obsługiwane przez brokera pojedynczych komunikatów i przechowywane w magazynie pojedynczych komunikatów. Ale [partycjonowanie magistrali usług](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) skaluje temat, rozsyłając go na wielu brokerów wiadomości i magazynów komunikatów.

[Zaplanowane dostarczanie wiadomości](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing) oznacza wiadomość z określonym czasem przetwarzania. Wiadomość nie pojawi się w temacie przed tym czasem. [Odroczenie wiadomości](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral) umożliwia odroczenie pobierania wiadomości do późniejszego czasu. Oba są powszechnie używane w scenariuszach przetwarzania przepływu pracy, w których operacje są przetwarzane w określonej kolejności. Możesz odroczyć przetwarzanie odebranych wiadomości do czasu zakończenia wcześniejszej pracy.

Tematy usługi Service Bus to niezawodna i sprawdzona technologia umożliwiająca komunikację publikowania/subskrybowania w systemach natywnych dla chmury.

### <a name="azure-event-grid"></a>Azure Event Grid

Usługa Azure Service Bus jest sprawdzonym brokerem obsługi wiadomości z pełnym zestawem funkcji przedsiębiorstwa, [usługa Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) jest nowym elementem bloku.

Na pierwszy rzut oka usługa Event Grid może wyglądać jak inny system obsługi wiadomości oparty na temacie. Jednak różni się pod wieloma względami. Koncentruje się na obciążeniach opartych na zdarzeniach, umożliwia przetwarzanie zdarzeń w czasie rzeczywistym, głęboką integrację platformy Azure i otwartą platformę — wszystko na infrastrukturze bezserwerowej. Jest przeznaczony dla współczesnych aplikacji natywnych w chmurze i bez serwerów

Jako scentralizowany *backplane zdarzenia*lub potoku, usługa Event Grid reaguje na zdarzenia wewnątrz zasobów platformy Azure i z własnych usług.

Powiadomienia o zdarzeniach są publikowane w temacie siatki zdarzeń, który z kolei kieruje każde zdarzenie do subskrypcji. Subskrybenci map do subskrypcji i zużywają zdarzenia. Podobnie jak usługa Service Bus, usługa Event Grid obsługuje *model filtrowanego subskrybenta,* w którym subskrypcja ustawia regułę dla zdarzeń, które chce otrzymywać. Usługa Event Grid zapewnia szybką przepływwę z gwarancją 10 milionów zdarzeń na sekundę, umożliwiając dostarczanie w czasie zbliżonym do rzeczywistego — znacznie więcej niż usługa Azure Service Bus może generować.

Sweet spot dla usługi Event Grid to jego głęboka integracja z siecią szkieletową infrastruktury platformy Azure. Zasób platformy Azure, takich jak usługi Cosmos DB, można publikować wbudowane zdarzenia bezpośrednio do innych zainteresowanych zasobów platformy Azure — bez konieczności kodu niestandardowego. Usługa Event Grid może publikować zdarzenia z subskrypcji platformy Azure, grupy zasobów lub usługi, dając deweloperom precyzyjną kontrolę nad cyklem życia zasobów w chmurze. Jednak usługa Event Grid nie jest ograniczona do platformy Azure. Jest to otwarta platforma, która może korzystać z niestandardowych zdarzeń HTTP publikowanych z aplikacji lub usług innych firm i kierować zdarzenia do abonentów zewnętrznych.

Podczas publikowania i subskrybowania zdarzeń natywnych z zasobów platformy Azure, nie jest wymagane kodowanie. Dzięki prostej konfiguracji można zintegrować zdarzenia z jednego zasobu platformy Azure do innego, wykorzystując wbudowaną instalację wodno-kanalizacyjną dla tematów i subskrypcji. Rysunek 4-17 przedstawia anatomię event gridu.

![Anatomia siatki zdarzeń](./media/event-grid-anatomy.png)

**Rysunek 4-17**. Anatomia siatki zdarzeń

Główną różnicą między EventGrid i Service Bus jest podstawowy *wzorzec wymiany wiadomości*.

Usługa Service Bus implementuje starszy *model ściągania* stylu, w którym subskrybent podrzędny aktywnie sonduje subskrypcję tematu dla nowych wiadomości. Z drugiej strony, takie podejście daje abonentowi pełną kontrolę nad tempem, w jakim przetwarza wiadomości. Kontroluje, kiedy i ile wiadomości do przetworzenia w danym momencie. Nieprzeczytane wiadomości pozostają w subskrypcji do czasu przetworzenia. Istotnym mankamentem jest opóźnienie między czas zdarzenia jest generowany i operacji sondowania, który pobiera ten komunikat do subskrybenta do przetwarzania. Ponadto obciążenie związane z ciągłym sondowaniem dla następnego zdarzenia zużywa zasoby i pieniądze.

EventGrid, jednak jest inna. Implementuje *model wypychania,* w którym zdarzenia są wysyłane do EventHandlers jako odebrane, dając w czasie zbliżonym do dostarczania zdarzeń w czasie rzeczywistym. Zmniejsza również koszty, ponieważ usługa jest wyzwalana tylko wtedy, gdy jest to konieczne do użycia zdarzenia — nie stale, jak w przypadku sondowania. To powiedziawszy, program obsługi zdarzeń musi obsługiwać przychodzące obciążenie i zapewnić mechanizmy ograniczania przepustowości, aby chronić się przed staniem się przytłoczony. Wiele usług platformy Azure, które używają tych zdarzeń, takich jak funkcje azure i aplikacje logiki zapewniają funkcje automatycznego skalowania automatycznego do obsługi zwiększonych obciążeń.  

Event Grid to w pełni zarządzana usługa w chmurze bezserwerowa. Dynamicznie skaluje się na podstawie ruchu i pobiera opłaty tylko za rzeczywiste użycie, a nie wstępnie zakupioną pojemność. Pierwsze 100 000 operacji miesięcznie jest bezpłatnych — operacje są definiowane jako przychodzące zdarzenia (powiadomienia o zdarzeniach przychodzących), próby dostarczenia subskrypcji, wywołania zarządzania i filtrowanie według tematu. Dzięki dostępności na 99,99% EventGrid gwarantuje dostawę zdarzenia w ciągu 24 godzin, z wbudowaną funkcją ponawiania prób w przypadku nieudanej dostawy. Niedostarczone wiadomości można przenieść do kolejki "utraconych wiadomości" w celu rozwiązania problemu.  W przeciwieństwie do usługi Azure Service Bus usługa Event Grid jest dostrojony do szybkiej wydajności i nie obsługuje funkcji, takich jak uporządkowane wiadomości, transakcji i sesji.

### <a name="streaming-messages-in-the-azure-cloud"></a>Przesyłanie strumieniowe wiadomości w chmurze platformy Azure

Usługa Azure Service Bus i usługa Event Grid zapewniają doskonałą obsługę aplikacji, które udostępniają pojedyncze, dyskretne zdarzenia, takie jak nowy dokument został wstawiony do usługi Cosmos DB. Ale co zrobić, jeśli system natywny w chmurze musi przetworzyć *strumień powiązanych zdarzeń?* [Strumienie zdarzeń](https://docs.microsoft.com/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems) są bardziej złożone. Są one zazwyczaj uporządkowane w czasie, ze sobą powiązane i muszą być przetwarzane jako grupa.

[Usługa Azure Event Hub](https://azure.microsoft.com/services/event-hubs/) to platforma przesyłania strumieniowego danych i usługa pozyskiwania zdarzeń, która zbiera, przekształca i przechowuje zdarzenia. Jest dostrojony do przechwytywania danych przesyłania strumieniowego, takich jak ciągłe powiadomienia o zdarzeniach emitowanych z kontekstu telemetrii. Usługa jest wysoce skalowalna i może przechowywać i [przetwarzać miliony zdarzeń na sekundę.](https://docs.microsoft.com/azure/event-hubs/event-hubs-about) Pokazane na rysunku 4-18 często jest to drzwi wejściowe dla potoku zdarzeń, odsprzęgające strumień pozyskiwania od zużycia zdarzeń.

![Centrum zdarzeń Azure](./media/azure-event-hub.png)

**Rysunek 4-18**. Centrum zdarzeń Azure

Centrum zdarzeń obsługuje małe opóźnienia i konfigurowalne przechowywanie czasu. W przeciwieństwie do kolejek i tematów Centra zdarzeń przechowują dane zdarzeń po ich odczytaniu przez konsumenta. Ta funkcja umożliwia innym usługom analizy danych, zarówno wewnętrznym, jak i zewnętrznym, odtworzenie danych w celu dalszej analizy. Zdarzenia przechowywane w Centrum zdarzeń są usuwane tylko po upływie okresu przechowywania, który jest domyślnie jeden dzień, ale konfigurowalny.

Centrum zdarzeń obsługuje typowe protokoły publikowania zdarzeń, w tym https i AMQP. Obsługuje również kafka 1.0. [Istniejące aplikacje platformy Kafka mogą komunikować się z Centrum zdarzeń](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) przy użyciu protokołu Platformy Kafka, zapewniając alternatywę dla zarządzania dużymi klastrami platformy Kafka. Wiele systemów natywnych dla chmury typu open source obejmuje platformę Kafka.

Event Hubs implementuje przesyłanie strumieniowe komunikatów za pośrednictwem [podzielonego na partycje modelu konsumenta,](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) w którym każdy konsument odczytuje tylko określony podzbiór lub partycję strumienia komunikatów. Ten wzorzec umożliwia ogromną skalę poziomą do przetwarzania zdarzeń i udostępnia inne funkcje skoncentrowane na strumieniu, które są niedostępne w kolejkach i tematach. Partycja to uporządkowana sekwencja zdarzeń przechowywana w centrum zdarzeń. Wraz z nadejściem nowszych zdarzeń są one dodawane do końca tej sekwencji.Rysunek 4-19 pokazuje partycjonowanie w Centrum zdarzeń.

![Partycjonowanie Centrum zdarzeń](./media/event-hub-partitioning.png)

**Rysunek 4-19**. Partycjonowanie Centrum zdarzeń

Zamiast odczytywać z tego samego zasobu, każda grupa konsumentów odczytuje przez podzbiór lub partycję strumienia wiadomości.

W przypadku aplikacji natywnych dla chmury, które muszą przesyłać strumieniowo dużą liczbę zdarzeń, usługa Azure Event Hub może być niezawodnym i niedrogim rozwiązaniem.

>[!div class="step-by-step"]
>[Poprzedni](front-end-communication.md)
>[następny](rest-grpc.md)
