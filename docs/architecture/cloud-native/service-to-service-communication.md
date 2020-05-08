---
title: Komunikacja między usługami
description: Dowiedz się, jak mikrousługi zaplecza w chmurze komunikują się z innymi mikrousługami zaplecza.
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: 556617a9e2df5a4d9ff9adb9d19e714ca94930ea
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895492"
---
# <a name="service-to-service-communication"></a>Komunikacja między usługami

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Po przeniesieniu się z klienta frontonu firma Microsoft komunikuje się ze sobą.

Podczas konstruowania aplikacji natywnej w chmurze warto mieć szczególną ostrożność, jak usługi zaplecza komunikują się ze sobą. W idealnym przypadku mniejsza komunikacja między usługami jest lepsza. Jednak unikanie nie zawsze jest możliwe, ponieważ usługi zaplecza często korzystają ze sobą, aby ukończyć operację.

Istnieje kilka powszechnie zaakceptowanych podejścia do implementowania komunikacji między usługami. *Typ interakcji komunikacji* często decyduje o najlepszym podejściu.

Należy wziąć pod uwagę następujące typy interakcji:

- *Query* — gdy wywołująca mikrousługa wymaga odpowiedzi z wywołanej mikrousługi, np. "Hej, podaj informacje o kupującym dla danego identyfikatora klienta".

- *Polecenie* — gdy wywołująca mikrousługa potrzebuje innej mikrousługi do wykonania akcji, ale nie wymaga odpowiedzi, takiej jak "Hej, po prostu Wyślij tę kolejność".

- *Event* — gdy mikrousługa, nazywana wydawcą, wywołuje zdarzenie, że stan zmienił się lub wystąpił akcja. Inne mikrousługi, nazywane abonentami, które interesują się, mogą odpowiednio reagować na zdarzenie. Wydawca i Subskrybenci nie są od siebie nawzajem świadomi.

Systemy mikrousług zazwyczaj używają kombinacji tych typów interakcji podczas wykonywania operacji wymagających interakcji między usługami. Przyjrzyjmy się, jak można je wdrożyć.

## <a name="queries"></a>Zapytania

Wiele mikrousług może wymagać wykonania *zapytania* do innej, co wymaga natychmiastowej reakcji na ukończenie operacji. Mikrousługa koszyka zakupów może potrzebować informacji o produkcie i ceny, aby dodać element do jego koszyka. Istnieje kilka podejścia do implementowania operacji zapytań.

### <a name="requestresponse-messaging"></a>Komunikaty żądania/odpowiedzi

Jedną z opcji implementowania tego scenariusza jest wywoływanie mikrousług zaplecza w celu skierowania żądań HTTP do mikrousług potrzebnych do wykonywania zapytań, jak pokazano na rysunku 4-8.

![Bezpośrednia komunikacja HTTP](./media/direct-http-communication.png)

**Rysunek 4-8**. Bezpośrednia komunikacja HTTP

Mimo że bezpośrednie wywołania protokołu HTTP między mikrousługami są stosunkowo proste do wdrożenia, należy wziąć pod uwagę, aby zminimalizować to rozwiązanie. Aby rozpocząć, te wywołania są zawsze *synchroniczne* i blokują operację do momentu zwrócenia wyniku lub przekroczenia limitu czasu żądania. Co się stało z samodzielnymi, niezależnymi usługami, które można rozdzielić niezależnie i wdrażać, są teraz połączone ze sobą. W miarę zwiększania się sprzężenia między mikrousługami ich zalety architektury zmniejszają się.

Wykonywanie sporadycznego żądania, które powoduje, że jedno bezpośrednie wywołanie protokołu HTTP do innej mikrousługi może być akceptowalne dla niektórych systemów. Jednak wywołania dużej ilości, które wywołują bezpośrednie wywołania protokołu HTTP do wielu mikrousług, nie są zalecane. Mogą zwiększyć opóźnienia i mieć negatywny wpływ na wydajność, skalowalność i dostępność systemu. Nawet gorsza, długa seria bezpośredniej komunikacji HTTP może prowadzić do głębokiego i złożonego łańcucha synchronicznych wywołań mikrousług, jak pokazano na rysunku 4-9:

![Łączenie kwerend HTTP](./media/chaining-http-queries.png)

**Rysunek 4-9**. Łączenie kwerend HTTP

Można wyobrazić ryzyko związane z projektem pokazanym na powyższym obrazie. Co się stanie w \#przypadku niepowodzenia kroku 3? Lub krok \#8 kończy się niepowodzeniem? Jak odzyskać? Co zrobić, \#Jeśli krok 6 jest wolny, ponieważ podstawowa usługa jest zajęta? Jak kontynuować? Nawet jeśli wszystkie działania działają prawidłowo, należy wziąć pod uwagę opóźnienie tego wywołania, czyli sumę opóźnienia każdego kroku.

Duży stopień sprzęgania w poprzednim obrazie sugeruje, że usługi nie były optymalnie modelowane. Behoove zespół do ponownego odwiedzania projektu.

### <a name="materialized-view-pattern"></a>Wzorzec zmaterializowanego widoku

Popularną opcją usunięcia sprzęgu mikrousług jest [wzorzec widoku materiału](https://docs.microsoft.com/azure/architecture/patterns/materialized-view). W tym wzorcu mikrousługa przechowuje własną, nieznormalizowaną kopię danych, która jest własnością innych usług. W przypadku mikrousług w koszyku zakupów i mikrousług do obsługi cennika usługa ta utrzymuje własną lokalną kopię tych danych. Ten wzorzec eliminuje zbędny sprzężenie i zwiększa niezawodność i czas odpowiedzi. Cała operacja jest wykonywana w ramach jednego procesu. Omawiamy ten wzorzec i inne zagadnienia dotyczące danych w rozdziale 5.

### <a name="service-aggregator-pattern"></a>Wzorzec agregatora usług

Kolejną opcją wyeliminowania mikrousług na mikrousługach jest mikrousługa [agregatora](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/), pokazana w kolorze purpurowym na rysunku 4-10.

![Usługa agregatora](./media/aggregator-service.png)

**Rysunek 4-10**. Mikrousługa agregatora

Wzorzec izoluje operację, która polega na wywołaniach do wielu mikrousług zaplecza, co pozwala na scentralizowanie jej logiki do wyspecjalizowanej mikrousługi.  Fioletowa funkcja agregatora wyewidencjonowania na poprzedniej ilustracji organizuje przepływ pracy dla operacji wyewidencjonowania. Obejmuje to wywołania kilku mikrousług zaplecza w kolejności sekwencyjnej. Dane z przepływu pracy są agregowane i zwracane do obiektu wywołującego. Mimo że nadal implementuje bezpośrednie wywołania protokołu HTTP, mikrousługa agregatora zmniejsza bezpośrednie zależności między mikrousługami zaplecza.

### <a name="requestreply-pattern"></a>Wzorzec żądania/odpowiedzi

Innym podejściem do oddzielania synchronicznych komunikatów HTTP jest [wzorzec żądanie-odpowiedź](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html), który używa komunikacji kolejkowania. Komunikacja przy użyciu kolejki jest zawsze jednokierunkowym kanałem, przez co producent wysyła wiadomość i odbiorcę. W tym wzorcu są zaimplementowane kolejki żądań i kolejki odpowiedzi, pokazane na rysunku 4-11.

![Wzorzec żądanie-odpowiedź](./media/request-reply-pattern.png)

**Rysunek 4-11**. Wzorzec żądanie-odpowiedź

W tym miejscu producent komunikatu tworzy komunikat oparty na zapytaniach zawierający unikatowy identyfikator korelacji i umieszcza go w kolejce żądań. Usługa korzystająca z kolejkowania komunikatów, przetwarza je i umieszcza w kolejce odpowiedzi ten sam identyfikator korelacji. Usługa producenta usuwa komunikat, dopasowuje go wraz z IDENTYFIKATORem korelacji i kontynuuje przetwarzanie. W następnej sekcji omówiono kolejki szczegółowo.

## <a name="commands"></a>Polecenia

Innym typem interakcji komunikacji jest *polecenie*. Mikrousługa może potrzebować innej mikrousługi do wykonania akcji. Mikrousługa porządkowania może potrzebować mikrousługi wysyłkowej w celu utworzenia wysyłki dla zatwierdzonej kolejności. Na rysunku 4-12 jedna mikrousługa, nazywana producentem, wysyła komunikat do innej mikrousługi, a konsument, polecenia, aby wykonać coś.

![Interakcja z poleceniem z kolejką](./media/command-interaction-with-queue.png)

**Rysunek 4-12**. Interakcja z poleceniem z kolejką

Najczęściej producenci nie wymagają odpowiedzi i mogą ją *uruchamiać i zapominać* . Jeśli wymagana jest odpowiedź, odbiorca wysyła oddzielny komunikat z powrotem do producenta w innym kanale. Komunikat polecenia jest najlepiej wysyłany asynchronicznie z kolejką komunikatów. obsługiwane przez uproszczony Broker komunikatów. Na poprzednim diagramie należy zwrócić uwagę, jak Kolejka oddzieli i oddziela obie usługi.

Kolejka komunikatów to pośrednik pośredniczący, za pomocą którego producent i odbiorca przekazują komunikat. Kolejki implementują wzorzec komunikatów typu punkt-punkt. Producent wie, gdzie należy odpowiednio wysłać polecenie i trasy. Kolejka gwarantuje, że komunikat jest przetwarzany dokładnie jednym z wystąpień konsumenta odczytywanych z kanału. W tym scenariuszu Usługa producent lub konsument może skalować w poziomie bez wpływu na inne. Technologie te mogą być również różne po obu stronach, co oznacza, że firma Microsoft może korzystać z mikrousługi w języku Java wywołującej mikrousługę [golang](https://golang.org) .

W rozdziale 1 zostały omówione *usługi zapasowe*. Usługi zapasowe są zasobami dodatkowymi, na których zależą systemy natywne w chmurze. Kolejki komunikatów to usługi zapasowe. Chmura systemu Azure obsługuje dwa typy kolejek komunikatów, których systemy natywne w chmurze mogą wykorzystać do implementacji komunikatów poleceń: kolejki usługi Azure Storage i kolejki Azure Service Bus.

### <a name="azure-storage-queues"></a>Kolejki usługi Azure Storage

Kolejki usługi Azure Storage oferują prostą infrastrukturę obejmującą szybkie, niedrogie i obsługiwane przez konta usługi Azure Storage.

[Kolejki usługi Azure Storage](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction) to mechanizm kolejkowania oparty na protokole REST z niezawodnymi i trwałymi wiadomościami. Zapewniają one minimalny zestaw funkcji, ale są niedrogie i przechowują miliony komunikatów. Zakresy pojemności do 500 TB. Pojedynczy komunikat może mieć rozmiar do 64 KB.

Możesz uzyskiwać dostęp do komunikatów z dowolnego miejsca na świecie za pośrednictwem uwierzytelnionych połączeń przy użyciu protokołu HTTP lub HTTPS. Kolejki magazynu można skalować w poziomie do dużej liczby współbieżnych klientów, aby obsługiwać skoki ruchu.

Wspomniane istnieją pewne ograniczenia dotyczące usługi:

- Kolejność wiadomości nie jest gwarantowana.

- Komunikat może się utrzymywać tylko przez siedem dni, zanim zostanie automatycznie usunięty.

- Obsługa zarządzania stanami, wykrywania duplikatów lub transakcji jest niedostępna.

Rysunek 4-13 przedstawia hierarchię kolejki usługi Azure Storage.

![Hierarchia kolejki magazynu](./media/storage-queue-hierarchy.png)

**Rysunek 4-13**. Hierarchia kolejki magazynu

Na poprzedniej ilustracji Zauważ, jak kolejki magazynu przechowują swoje wiadomości na podstawowym koncie usługi Azure Storage.

W przypadku deweloperów firma Microsoft udostępnia kilka bibliotek po stronie klienta i serwera na potrzeby przetwarzania kolejki magazynu. Obsługiwane są większość najważniejszych platform, w tym .NET, Java, JavaScript, Ruby, Python i go. Deweloperzy nigdy nie muszą komunikować się bezpośrednio z tymi bibliotekami. Spowoduje to ścisłe przełączenie kodu mikrousług do usługa kolejki usługi Azure Storage. Lepszym rozwiązaniem jest izolowanie szczegółów implementacji interfejsu API. Wprowadzenie do warstwy biokorekty lub pośredniego interfejsu API, który uwidacznia operacje ogólne i hermetyzuje konkretną bibliotekę. Ten luźny sprzężenie umożliwia zamianę jednej usługi kolejkowania na inną bez konieczności wprowadzania zmian w kodzie usługi linii głównej.

Kolejki usługi Azure Storage to ekonomiczne rozwiązanie do implementowania komunikatów poleceń w aplikacjach natywnych w chmurze. Szczególnie w przypadku, gdy rozmiar kolejki przekroczy 80 GB lub jest akceptowalny prosty zestaw funkcji. Płacisz tylko za magazyn komunikatów; nie są naliczane żadne opłaty godzinowe.

### <a name="azure-service-bus-queues"></a>Kolejki usługi Azure Service Bus

Aby uzyskać bardziej złożone wymagania dotyczące komunikatów, należy wziąć pod uwagę Azure Service Bus kolejki.

Zakorzystającego się z niezawodną infrastrukturą komunikatów, [Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) obsługuje *model komunikatów obsługiwanych przez brokera*. Komunikaty są niezawodnie przechowywane w brokerze (kolejce) do momentu odebrania przez konsumenta. Kolejka gwarantuje dostarczanie komunikatów First-In/First-Out (FIFO), z uwzględnieniem kolejności, w jakiej komunikaty zostały dodane do kolejki.

Rozmiar wiadomości może być znacznie większy, do 256 KB. Komunikaty są utrwalane w kolejce przez nieograniczony okres. Service Bus obsługuje nie tylko wywołania oparte na protokole HTTP, ale również zapewnia pełną obsługę [protokołu AMQP](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview). AMQP to wersja typu Open-Standard dla wielu dostawców, która obsługuje protokół binarny i wyższy poziom niezawodności.

Service Bus oferuje bogaty zestaw funkcji, w tym [obsługę transakcji](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) i [funkcję wykrywania duplikatów](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection). Kolejka "co najwyżej raz zagwarantuje" w przypadku wiadomości. Automatycznie odrzuca już wysłany komunikat. Jeśli producent jest w stanie wątpliwości, może ponownie wysłać ten sam komunikat, a Service Bus gwarantuje, że tylko jedna kopia zostanie przetworzona. Wykrywanie duplikatów zwalnia użytkownika z konieczności tworzenia dodatkowej infrastruktury instalacji.

Dwie więcej funkcji przedsiębiorstwa to partycjonowanie i sesje. Kolejka konwencjonalnych Service Bus jest obsługiwana przez jednego brokera komunikatów i przechowywana w jednym magazynie komunikatów. Jednak [Service Bus partycjonowanie](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) rozkłada kolejkę na wiele brokerów komunikatów i magazynów komunikatów. Ogólna przepływność nie jest już ograniczona przez wydajność jednego brokera komunikatów lub magazynu komunikatów. Tymczasowa awaria magazynu komunikatów nie powoduje niedostępności kolejki partycjonowanej.

[Sesje Service Bus](https://codingcanvas.com/azure-service-bus-sessions/) zapewniają sposób grupowania komunikatów związanych z grupą. Wyobraź sobie scenariusz przepływu pracy, w którym wiadomości muszą być przetwarzane razem, a operacja zakończona na końcu. Aby skorzystać z zalet, należy jawnie włączyć sesje dla kolejki, a każdy powiązany komunikat musi zawierać ten sam identyfikator sesji.

Istnieją jednak pewne istotne zastrzeżenia: rozmiar kolejek Service Bus jest ograniczony do 80 GB, co jest znacznie mniejsze niż dostępne w kolejkach magazynu. Ponadto kolejki Service Bus powodują koszt podstawowy i opłaty za operację.

Rysunek 4-14 przedstawia architekturę wysokiego poziomu kolejki Service Bus.

![Kolejka usługi Service Bus](./media/service-bus-queue.png)

**Rysunek 4-14**. Kolejka usługi Service Bus

Na poprzedniej ilustracji należy zwrócić uwagę na relację punkt-punkt. Dwa wystąpienia tego samego dostawcy są umieszczenie komunikatów w jednej kolejce Service Bus. Każdy komunikat jest zużywany przez tylko jeden z trzech wystąpień konsumentów po prawej stronie. Następnie omawiamy sposób implementacji komunikatów, w przypadku których różni konsumenci mogą korzystać z tego samego komunikatu.

## <a name="events"></a>Zdarzenia

Usługa kolejkowania komunikatów jest efektywnym sposobem na wdrożenie komunikacji, w której producent może asynchronicznie wysyłać do niego wiadomość. Jednak co się stanie, gdy *wielu różnych konsumentów* interesuje ten sam komunikat? Dedykowana kolejka komunikatów dla każdego konsumenta nie będzie dobrze skalowana i utrudnia zarządzanie nimi.

Aby rozwiązać ten scenariusz, przejdziemy do innego typu interakcji z komunikatem, *zdarzenie*. Jedna mikrousług ogłasza, że wystąpiła akcja. Inne mikrousługi, jeśli są zainteresowane, reagują na działanie lub zdarzenie.

Tworzenie zdarzeń jest procesem dwuetapowym. Dla danej zmiany stanu mikrousługa publikuje zdarzenie w brokerze komunikatów, udostępniając go innym zainteresowanym mikrousługom. Zainteresowana mikrousługa jest powiadamiana przez zasubskrybowanie zdarzenia w brokerze komunikatów. Wzorzec [publikowania/subskrybowania](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) służy do implementowania [komunikacji opartej na zdarzeniach](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications).

Na rysunku 4-15 przedstawiono mikrousługi koszyka zakupów wydarzenie z dwoma innymi subskrybowanymi mikrousług.

![Obsługa komunikatów opartych na zdarzeniach](./media/event-driven-messaging.png)

**Rysunek 4-15**. Obsługa komunikatów opartych na zdarzeniach

Zanotuj składnik *magistrali zdarzeń* , który znajduje się w środku kanału komunikacyjnego. Jest to Klasa niestandardowa, która hermetyzuje brokera komunikatów i oddziela ją od aplikacji źródłowej. Mikrousługi zamawiania i spisu niezależnie obsługują zdarzenia bez znajomości siebie ani do mikrousługi koszyka zakupów. Po opublikowaniu zarejestrowanego zdarzenia w usłudze Event Bus działają one na nim.

Dzięki zdarzeniom przechodźmy od technologii kolejkowania do *tematów*. [Temat](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) jest podobny do kolejki, ale obsługuje wzorzec obsługi komunikatów jeden-do-wielu. Jedna mikrousługa publikuje komunikat. Wiele zasubskrybowanych mikrousług może być w stanie otrzymywać i korzystać z tego komunikatu. Rysunek 4-16 przedstawia architekturę tematu.

![Architektura tematu](./media/topic-architecture.png)

**Rysunek 4-16**. Architektura tematu

Na powyższym rysunku wydawcy wysyłają komunikaty do tematu. Na koniec Subskrybenci odbierają wiadomości z subskrypcji. W środku tematu przekazuje komunikaty do subskrypcji na podstawie zestawu *reguł*, które są wyświetlane w ciemnych polach. Reguły działają jako filtr, który przekazuje dalej określone wiadomości do subskrypcji. W tym miejscu zostanie wysłane zdarzenie "Zamów" do subskrypcji \#1 i subskrypcji \#3, ale nie do subskrypcji \#2. Do subskrypcji \#2 i subskrypcji \#3 zostanie wysłane zdarzenie "OrderCompleted".

Chmura systemu Azure obsługuje dwie różne usługi tematu: Tematy Azure Service Bus i Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Tematy usługi Azure Service Bus

W oparciu o ten sam niezawodny model komunikatów obsługiwanych przez brokera Azure Service Bus kolejek są [Azure Service Bus tematy](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions). Temat może odbierać komunikaty od wielu niezależnych wydawców i wysyłać komunikaty do 2 000 subskrybentów. Subskrypcje mogą być dynamicznie dodawane lub usuwane w czasie wykonywania bez zatrzymywania systemu ani ponownego tworzenia tematu.

Wiele zaawansowanych funkcji z kolejek Azure Service Busych są również dostępne dla tematów, takich jak [Wykrywanie duplikatów](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) i [Obsługa transakcji](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions). Domyślnie tematy Service Bus są obsługiwane przez jednego brokera komunikatów i przechowywane w jednym magazynie komunikatów. Ale [Service Bus partycjonowanie](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) skaluje temat, rozkładając go na wielu brokerów komunikatów i magazynów komunikatów.

[Zaplanowana dostarczanie komunikatów](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing) oznacza komunikat z określonym czasem do przetwarzania. Wiadomość nie zostanie wyświetlona w temacie przed upływem tego czasu. [Odroczenie komunikatów](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral) pozwala na odroczenie pobierania komunikatu w późniejszym czasie. Oba są często używane w scenariuszach przetwarzania przepływu pracy, w których operacje są przetwarzane w określonej kolejności. Możesz odroczyć przetwarzanie odebranych komunikatów do momentu ukończenia wcześniejszej pracy.

Tematy Service Bus to niezawodna i sprawdzona technologia umożliwiająca umożliwienie komunikacji z publikowaniem/subskrypcją w systemach natywnych w chmurze.

### <a name="azure-event-grid"></a>Azure Event Grid

Mimo że Azure Service Bus jest przetestowanym sprawdzonej brokerem obsługi komunikatów z pełnym zestawem funkcji dla przedsiębiorstw, [Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) jest nowym dzieciem w bloku.

Na pierwszy rzut oka Event Grid może wyglądać podobnie jak w przypadku innego systemu obsługi komunikatów opartego na temacie. Jest to jednak różne na wiele sposobów. Skoncentrowanie się na obciążeniach opartych na zdarzeniach pozwala na przetwarzanie zdarzeń w czasie rzeczywistym, integrację z platformą Azure oraz platformę Open-All w infrastrukturze bezserwerowej. Jest ona przeznaczona do współczesnych aplikacji natywnych dla chmury i bezserwerowych

Jako scentralizowany *plan zdarzeń*lub potok, Event Grid reaguje na zdarzenia wewnątrz zasobów platformy Azure i z własnych usług.

Powiadomienia o zdarzeniach są publikowane w temacie Event Grid, co z kolei kieruje każde zdarzenie do subskrypcji. Subskrybenci są zamapowane na subskrypcje i zużywają zdarzenia. Podobnie jak Service Bus, Event Grid obsługuje *filtrowany model subskrybenta* , w którym zestaw subskrypcji ma regułę dla zdarzeń, które chce otrzymywać. Event Grid zapewnia szybką przepływność z gwarancją 10 000 000 zdarzeń na sekundę, co pozwala na dostarczanie niemal w czasie rzeczywistym więcej niż to, co Azure Service Bus może generować.

Słodka plamka dla Event Grid jest jej głębokiej integracji z siecią szkieletową infrastruktury platformy Azure. Zasób platformy Azure, taki jak Cosmos DB, może publikować wbudowane zdarzenia bezpośrednio do innych interesujących zasobów platformy Azure — bez konieczności stosowania kodu niestandardowego. Event Grid mogą publikować zdarzenia z subskrypcji platformy Azure, grupy zasobów lub usługi, zapewniając precyzyjne sterowanie cyklem życia zasobów w chmurze przez deweloperów. Event Grid nie jest jednak ograniczona do platformy Azure. Jest to otwarta platforma, która może zużywać niestandardowe zdarzenia HTTP publikowane z aplikacji lub usług innych firm i kierować zdarzenia do subskrybentów zewnętrznych.

W przypadku publikowania i subskrybowania zdarzeń natywnych z zasobów platformy Azure nie jest wymagane kodowanie. Przy użyciu prostej konfiguracji możesz zintegrować zdarzenia z jednego zasobu platformy Azure z innym wykorzystując wbudowaną instalację wodociągową dla tematów i subskrypcji. Na rysunku 4-17 przedstawiono anatomię Event Grid.

![Event Grid Anatomia](./media/event-grid-anatomy.png)

**Rysunek 4-17**. Event Grid Anatomia

Główna różnica między EventGrid i Service Bus jest *wzorcem wymiany komunikatów*.

Service Bus implementuje *model ściągania* starszego stylu, w którym subskrybent podrzędny aktywnie sonduje subskrypcję tematu pod kątem nowych komunikatów. Na odniesieniu do osi odnoszącej się do siebie, ta metoda zapewnia subskrybentowi pełną kontrolę nad tym, w jaki sposób proces przetwarza komunikaty. Określa, kiedy i ile komunikatów ma być przetwarzanych w danym momencie. Nieprzeczytane wiadomości pozostają w subskrypcji do momentu przetworzenia. Znaczący brak to opóźnienie między czasem wygenerowania zdarzenia a operacją sondowania, która ściąga ten komunikat do subskrybenta w celu przetworzenia. Ponadto narzuty stałe sondowania dla następnego zdarzenia zużywa zasoby i pieniądze.

EventGrid, jednak różni się. Implementuje *model wypychania* , w którym zdarzenia są wysyłane do EventHandlers jako otrzymane, co pozwala na dostarczanie zdarzeń niemal w czasie rzeczywistym. Zmniejsza to również koszty, ponieważ usługa jest wyzwalana tylko wtedy, gdy jest wymagana do użycia zdarzenia — nie jest to stale zgodne z sondowaniem. Tak samo, program obsługi zdarzeń musi obsłużyć obciążenie przychodzące i zapewnić mechanizmy ograniczania przepustowości w celu samodzielnego zabezpieczenia. Wiele usług platformy Azure, które zużywa te zdarzenia, takich jak Azure Functions i Logic Apps, zapewniają automatyczne skalowanie w celu obsługi zwiększonych obciążeń.  

Event Grid to w pełni zarządzana usługa w chmurze bezserwerowej. Dynamicznie skaluje się w oparciu o ruch i opłaty tylko za rzeczywiste użycie, a nie zakupione wcześniej. Pierwsze 100 000 operacji miesięcznie są bezpłatne — operacje są definiowane jako zdarzenia związane z ruchem przychodzącym (powiadomienia o zdarzeniach przychodzących), próby dostarczenia subskrypcji, wywołania zarządzania i filtrowanie według podmiotu. Dzięki dostępności na 99,99% EventGrid gwarantuje dostarczenie zdarzenia w ciągu 24-godzinnym i wbudowaną funkcję ponawiania prób w przypadku niepowodzenia dostawy. Komunikaty niedostarczone można przenieść do kolejki "utraconych" w celu rozwiązania problemu.  W przeciwieństwie do Azure Service Bus, Event Grid jest dostrojony do szybkiej wydajności i nie obsługuje funkcji, takich jak uporządkowane wiadomości, transakcje i sesje.

### <a name="streaming-messages-in-the-azure-cloud"></a>Przesyłanie strumieniowe komunikatów w chmurze platformy Azure

Azure Service Bus i Event Grid zapewniają doskonałą pomoc techniczną dla aplikacji, które uwidaczniają pojedyncze, dyskretne zdarzenia, takie jak nowy dokument został wstawiony do Cosmos DB. Ale co zrobić, jeśli system natywny w chmurze musi przetworzyć *strumień powiązanych zdarzeń*? [Strumienie zdarzeń](https://docs.microsoft.com/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems) są bardziej skomplikowane. Są one zazwyczaj uporządkowane według czasu, wzajemnie powiązane i muszą być przetwarzane jako Grupa.

[Azure Event Hub](https://azure.microsoft.com/services/event-hubs/) to usługa przesyłania strumieniowego danych i usługi pozyskiwania zdarzeń, która gromadzi, przekształca i zapisuje zdarzenia. Jest to dostrajane do przechwytywania danych przesyłanych strumieniowo, takich jak ciągłe powiadomienia o zdarzeniach emitowane z kontekstu telemetrii. Usługa jest wysoce skalowalna i może przechowywać i [przetwarzać miliony zdarzeń na sekundę](https://docs.microsoft.com/azure/event-hubs/event-hubs-about). Pokazano na rysunku 4-18, często są to drzwi czołowe dla potoku zdarzeń, oddzielania strumienia pozyskiwania od zużycia zdarzeń.

![Centrum zdarzeń Azure](./media/azure-event-hub.png)

**Rysunek 4-18**. Centrum zdarzeń Azure

Centrum zdarzeń obsługuje małe opóźnienia i konfigurowalne przechowywanie czasu. W przeciwieństwie do kolejek i tematów Event Hubs zachować dane zdarzenia po ich odczytaniu przez konsumenta. Ta funkcja umożliwia innym usługom analitycznym danych, zarówno wewnętrznym, jak i zewnętrznym, odtwarzanie danych w celu dalszej analizy. Zdarzenia przechowywane w centrum zdarzeń są usuwane dopiero po upływie okresu przechowywania, który jest domyślnie jeden dzień, ale konfigurowalne.

Centrum zdarzeń obsługuje typowe protokoły publikowania zdarzeń, w tym HTTPS i AMQP. Obsługuje także Kafka 1,0. [Istniejące aplikacje Kafka mogą komunikować się z centrum zdarzeń](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) przy użyciu protokołu Kafka, co zapewnia alternatywę dla zarządzania dużymi klastrami Kafka. Wiele systemów natywnych dla chmury "open source" obejmuje Kafka.

Event Hubs implementuje przesyłanie strumieniowe komunikatów za pomocą [partycjonowanego modelu konsumenta](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) , w którym każdy odbiorca odczytuje tylko konkretny podzbiór lub partycję strumienia komunikatów. Ten wzorzec zapewnia nieogromne skalowanie w poziomie na potrzeby przetwarzania zdarzeń oraz udostępnia inne funkcje ukierunkowane na przesyłanie strumieniowe, które są niedostępne w kolejkach i tematach. Partycja to uporządkowana sekwencja zdarzeń przechowywana w centrum zdarzeń. Po nadejściu nowszych zdarzeń są one dodawane na końcu tej sekwencji.Rysunek 4-19 pokazuje partycjonowanie w centrum zdarzeń.

![Partycjonowanie centrum zdarzeń](./media/event-hub-partitioning.png)

**Rysunek 4-19**. Partycjonowanie centrum zdarzeń

Zamiast odczytywania z tego samego zasobu, każda grupa odbiorców odczytuje między podzbiorem lub partycją strumienia komunikatów.

W przypadku aplikacji natywnych w chmurze, które muszą przesyłać strumieniowo dużą liczbę zdarzeń, usługa Azure Event Hub może być niezawodna i niedrogie rozwiązanie.

>[!div class="step-by-step"]
>[Poprzedni](front-end-communication.md)
>[Następny](grpc.md)
