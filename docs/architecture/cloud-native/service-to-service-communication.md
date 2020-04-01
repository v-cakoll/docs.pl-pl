---
title: Komunikacja między usługami
description: Dowiedz się, jak zaplecza chmury natywnych mikrousług komunikować się z innymi mikrousług zaplecza.
author: robvet
ms.date: 09/09/2019
ms.openlocfilehash: 926be3c2eb4513c89ebcd1f31dceb7d58639dc6f
ms.sourcegitcommit: 79b0dd8bfc63f33a02137121dd23475887ecefda
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/01/2020
ms.locfileid: "80523562"
---
# <a name="service-to-service-communication"></a>Komunikacja między usługami

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Przechodząc od klienta front-end, teraz adres mikrousług zaplecza komunikować się ze sobą.

Podczas tworzenia aplikacji natywnej dla chmury, należy być poufne, jak usługi zaplecza komunikować się ze sobą. Najlepiej, im mniej komunikacji między usługami, tym lepiej. Jednak unikanie nie zawsze jest możliwe, ponieważ usługi zaplecza często polegają na sobie nawzajem, aby zakończyć operację.

Istnieje kilka powszechnie akceptowanych podejść do wdrażania komunikacji między usługami. *Rodzaj interakcji komunikacyjnej* często określa najlepsze podejście.

Należy wziąć pod uwagę następujące typy interakcji:

- *Zapytanie* — gdy wywołanie mikrousługi wymaga odpowiedzi z o nazwie mikrousługi, takich jak "Hej, daj mi informacje kupującego dla danego identyfikatora klienta."

- *Polecenie* — gdy wywołanie mikrousługi potrzebuje innej mikrousługi do wykonania akcji, ale nie wymaga odpowiedzi, takich jak "Hej, po prostu wyślij to zamówienie."

- *Zdarzenie* — gdy mikrousługi, o nazwie wydawca, wywołuje zdarzenie, że stan został zmieniony lub wystąpiła akcja. Inne mikrousługi, o nazwie subskrybentów, którzy są zainteresowani, można odpowiednio reagować na zdarzenie. Wydawca i subskrybenci nie są świadomi siebie nawzajem.

Systemy mikrousług zazwyczaj używają kombinacji tych typów interakcji podczas wykonywania operacji, które wymagają interakcji między usługami. Przyjrzyjmy się uważnie każdemu i temu, jak możesz je zaimplementować.

## <a name="queries"></a>Zapytania

Wiele razy jedna mikrousługa może wymagać *kwerendy* innego, wymagając natychmiastowej odpowiedzi, aby zakończyć operację. Mikrousługa koszyka zakupów może wymagać informacji o produkcie i ceny, aby dodać element do koszyka. Istnieje wiele podejść do implementowania operacji kwerendy.

### <a name="requestresponse-messaging"></a>Wiadomości z prośbą/odpowiedzią

Jedną z opcji implementacji tego scenariusza jest dla wywoływania mikrousług zaplecza do bezpośredniego żądania HTTP do mikrousług, które należy zbadać, pokazano na rysunku 4-8.

![Bezpośrednia komunikacja HTTP](./media/direct-http-communication.png)

**Rysunek 4-8**. Bezpośrednia komunikacja HTTP

Podczas gdy bezpośrednie wywołania HTTP między mikrousługami są stosunkowo proste do zaimplementowania, należy zwrócić uwagę, aby zminimalizować tę praktykę. Aby rozpocząć, te wywołania są zawsze *synchroniczne* i zablokuje operację, dopóki wynik nie zostanie zwrócony lub outs czasu żądania. To, co kiedyś było samodzielnymi, niezależnymi służbami, zdolnymi do samodzielnego rozwoju i częstego wdrażania, teraz staje się ze sobą powiązane. Wraz ze wzrostem sprzężenia między mikrousługami ich korzyści architektoniczne zmniejszają się.

Wykonywanie rzadkich żądań, które sprawia, że pojedyncze bezpośrednie wywołanie HTTP do innej mikrousługi może być dopuszczalne dla niektórych systemów. Jednak wywołania dużej ilości, które wywołują bezpośrednie wywołania HTTP do wielu mikrousług nie są wskazane. Mogą one zwiększyć opóźnienia i negatywnie wpłynąć na wydajność, skalowalność i dostępność systemu. Co gorsza, długa seria bezpośredniej komunikacji HTTP może prowadzić do głębokich i złożonych łańcuchów wywołań mikrousług synchronicznych, pokazano na rysunku 4-9:

![Tworzenie łańcucha zapytań HTTP](./media/chaining-http-queries.png)

**Rysunek 4-9**. Tworzenie łańcucha zapytań HTTP

Z pewnością można sobie wyobrazić ryzyko w projekcie pokazanym na poprzednim obrazie. Co się \#stanie, jeśli krok 3 nie powiedzie się? Albo \#krok 8 nie powiedzie się? Jak odzyskać? Co zrobić, jeśli krok \#6 jest powolny, ponieważ podstawowa usługa jest zajęta? Jak kontynuować? Nawet jeśli wszystkie działa poprawnie, pomyśl o opóźnieniu to wywołanie spowoduje, która jest sumą opóźnienia każdego kroku.

Duży stopień sprzężenia na poprzednim obrazie sugeruje, że usługi nie były optymalnie modelowane. Byłoby behoove zespół do ponownego ich projektu.

### <a name="materialized-view-pattern"></a>Wzorzec zmaterializowanego widoku

Popularną opcją usuwania sprzężenia mikrousług jest [wzorzec Widok materializowany.](https://docs.microsoft.com/azure/architecture/patterns/materialized-view) Za pomocą tego wzorca mikrousługi przechowuje własną lokalną, zdenormalizowane kopię danych, która jest własnością innych usług. Zamiast mikrousług koszyka zakupów kwerendy katalogu produktów i mikrousług cenowych, przechowuje własną lokalną kopię tych danych. Ten wzór eliminuje niepotrzebne sprzężenie i poprawia niezawodność i czas reakcji. Cała operacja jest wykonywana wewnątrz pojedynczego procesu. Badamy ten wzorzec i inne problemy związane z danymi w rozdziale 5.

### <a name="service-aggregator-pattern"></a>Wzorzec agregatora usług

Inną opcją eliminowania sprzężenia mikrousług do mikrousług jest [mikrousługa agregatora,](https://devblogs.microsoft.com/cesardelatorre/designing-and-implementing-api-gateways-with-ocelot-in-a-microservices-and-container-based-architecture/)pokazana w kolorze fioletowym na rysunku 4-10.

![Usługa agregatora](./media/aggregator-service.png)

**Rysunek 4-10**. Mikrousługa agregatora

Wzorzec izoluje operację, która sprawia, że wywołania wielu mikrousług zaplecza, centralizując jego logiki do specjalistycznych mikrousług.  Fioletowy mikrousługi agregatora wyewidencjonowania w poprzednim rysunku organizuje przepływ pracy dla operacji Wyewidencjonowania. Zawiera wywołania kilku mikrousług zaplecza w kolejności sekwencjonowane. Dane z przepływu pracy są agregowane i zwracane do obiektu wywołującego. Chociaż nadal implementuje bezpośrednie wywołania HTTP, mikrousługi agregatora zmniejsza bezpośrednie zależności między mikrousług zaplecza.

### <a name="requestreply-pattern"></a>Wzorzec żądania/odpowiedzi

Innym podejściem do oddzielenia synchronicznych wiadomości HTTP jest [wzorzec żądania i odpowiedzi,](https://www.enterpriseintegrationpatterns.com/patterns/messaging/RequestReply.html)który używa komunikacji kolejkowania. Komunikacja przy użyciu kolejki jest zawsze kanałem jednokierunkowym, a producent wysyła wiadomość, a konsument ją odbiera. Za pomocą tego wzorca zaimplementowano zarówno kolejkę żądań, jak i kolejkę odpowiedzi, przedstawioną na rysunku 4-11.

![Wzorzec żądania odpowiedzi](./media/request-reply-pattern.png)

**Rysunek 4-11**. Wzorzec żądania odpowiedzi

W tym miejscu producent komunikatów tworzy komunikat oparty na kwerendach, który zawiera unikatowy identyfikator korelacji i umieszcza go w kolejce żądań. Usługa zużywająca usuwa wiadomości, przetwarza ją i umieszcza odpowiedź w kolejce odpowiedzi o tym samym identyfikatorze korelacji. Usługa producenta usuwa komunikat w kolejce, dopasowuje ją do identyfikatora korelacji i kontynuuje przetwarzanie. Szczegółowo opisujemy kolejki w następnej sekcji.

## <a name="commands"></a>Polecenia

Innym rodzajem interakcji komunikacyjnej jest *polecenie*. Mikrousługi może wymagać innej mikrousługi do wykonania akcji. Mikrousługa zamawiania może wymagać mikrousługi wysyłkowej do utworzenia przesyłki dla zatwierdzonego zamówienia. Na rysunku 4-12 jednej mikrousługi, o nazwie Producent, wysyła wiadomość do innej mikrousługi, konsumenta, nakazując jej coś zrobić.

![Interakcja polecenia z kolejką](./media/command-interaction-with-queue.png)

**Rysunek 4-12**. Interakcja polecenia z kolejką

Najczęściej Producent nie wymaga odpowiedzi i może *fire-and-forget* wiadomości. Jeśli odpowiedź jest potrzebna, konsument wysyła osobną wiadomość z powrotem do producenta na innym kanale. Komunikat polecenia najlepiej jest wysyłać asynchronicznie z kolejką wiadomości. obsługiwane przez lekki broker wiadomości. Na poprzednim diagramie należy zwrócić uwagę, jak kolejka oddziela i oddziela obie usługi.

Kolejka komunikatów jest konstrukcją pośredniczącą, za pośrednictwem której producent i konsument przekazują wiadomość. Kolejki implementują asynchroniczne wzorzec obsługi wiadomości typu point-to-point. Producent wie, gdzie należy wysłać polecenie i odpowiednio trasuje. Kolejka gwarantuje, że wiadomość jest przetwarzana przez dokładnie jedno z wystąpień konsumenta, które są odczytywały z kanału. W tym scenariuszu producent lub usługa konsumenta można skalować w poziomie bez wpływu na inne. Jak również technologie mogą być różne z każdej strony, co oznacza, że możemy mieć mikrousługi Java wywołując mikrousługi [Golang.](https://golang.org)

W rozdziale 1 rozmawialiśmy o *usługach wspierających.* Usługi pomocnicze to zasoby pomocnicze, od których zależą systemy natywne dla chmury. Kolejki komunikatów są tworzeniem kopii zapasowych usług. Chmura platformy Azure obsługuje dwa typy kolejek komunikatów, które systemy natywne w chmurze mogą korzystać w celu zaimplementowania obsługi poleceń: kolejek usługi Azure Storage i kolejek usługi Azure Service Bus.

### <a name="azure-storage-queues"></a>Kolejki usługi Azure Storage

Kolejki magazynu platformy Azure oferują prostą infrastrukturę kolejkowania, która jest szybka, przystępna cenowo i wspierana przez konta magazynu platformy Azure.

[Kolejki usługi Azure Storage](https://docs.microsoft.com/azure/storage/queues/storage-queues-introduction) są wyposażone w mechanizm kolejkowania oparty na rest z niezawodnymi i trwałymi wiadomościami. Zapewniają minimalny zestaw funkcji, ale są niedrogie i przechowują miliony wiadomości. Ich pojemność wynosi do 500 TB. Pojedyncza wiadomość może mieć rozmiar do 64 KB.

Możesz uzyskiwać dostęp do wiadomości z dowolnego miejsca na świecie za pośrednictwem uwierzytelnionych połączeń przy użyciu protokołu HTTP lub HTTPS. Kolejki magazynu można skalować w poziomie do dużej liczby równoczesnych klientów do obsługi skoków ruchu.

To powiedziawszy, istnieją ograniczenia związane z usługą:

- Kolejność wiadomości nie jest gwarantowana.

- Wiadomość może być zachowywana tylko przez siedem dni, zanim zostanie automatycznie usunięta.

- Obsługa zarządzania stanem, wykrywania duplikatów lub transakcji nie jest dostępna.

Rysunek 4-13 przedstawia hierarchię kolejki usługi Azure Storage.

![Hierarchia kolejek magazynu](./media/storage-queue-hierarchy.png)

**Rysunek 4-13**. Hierarchia kolejek magazynu

Na poprzedniej ilustracji należy zwrócić uwagę, jak kolejki magazynu przechowywać swoje wiadomości na podstawowym koncie usługi Azure Storage.

Dla deweloperów firma Microsoft udostępnia kilka bibliotek po stronie klienta i serwera do przetwarzania kolejek magazynu. Większość głównych platform są obsługiwane w tym .NET, Java, JavaScript, Ruby, Python i Go. Deweloperzy nigdy nie powinni komunikować się bezpośrednio z tymi bibliotekami. W ten sposób będzie ściśle łącze kodu mikrousług do usługi Azure Storage Queue. Jest to lepsza praktyka, aby ocieplić szczegóły implementacji interfejsu API. Wprowadzenie warstwy pośrednictwa lub pośredniego interfejsu API, który udostępnia operacje ogólne i hermetyzuje bibliotekę betonu. To luźne sprzężenie umożliwia zamianę jednej usługi kolejkowania na inną bez konieczności wprowadzania zmian w kodzie usługi mainline.

Kolejki usługi Azure Storage są ekonomiczną opcją implementacji obsługi wiadomości poleceń w aplikacjach natywnych dla chmury. Zwłaszcza, gdy rozmiar kolejki przekroczy 80 GB lub dopuszczalny jest prosty zestaw funkcji. Płacisz tylko za przechowywanie wiadomości; nie ma stałych opłat godzinowych.

### <a name="azure-service-bus-queues"></a>Kolejki usługi Azure Service Bus

Aby uzyskać bardziej złożone wymagania dotyczące obsługi wiadomości, należy wziąć pod uwagę kolejki usługi Azure Service Bus.

Siedząc na szczycie niezawodnej infrastruktury komunikatów, [usługa Azure Service Bus](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-messaging-overview) obsługuje model obsługi wiadomości z *brokerem.* Wiadomości są niezawodnie przechowywane w brokera (kolejki) do momentu odebrania przez konsumenta. Kolejka gwarantuje dostarczanie wiadomości FIFO (First-In/First-Out), respektując kolejność, w jakiej wiadomości zostały dodane do kolejki.

Rozmiar wiadomości może być znacznie większy, do 256 KB. Wiadomości są zachowywane w kolejce przez nieograniczony okres czasu. Usługa Service Bus obsługuje nie tylko wywołania oparte na protokole HTTP, ale także zapewnia pełną obsługę [protokołu AMPQ.](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-amqp-overview) AMPQ jest otwartym standardem dla dostawców, który obsługuje protokół binarny i wyższy stopień niezawodności.

Usługa Service Bus oferuje bogaty zestaw funkcji, w tym [obsługę transakcji](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) i [funkcję wykrywania duplikatów.](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) Kolejka gwarantuje "co najwyżej raz dostarczanie" na wiadomość. Automatycznie odrzuca wiadomość, która została już wysłana. Jeśli producent ma wątpliwości, może ponownie wysłać tę samą wiadomość, a usługa Service Bus gwarantuje, że tylko jedna kopia zostanie przetworzona. Wykrywanie duplikatów uwalnia cię od konieczności budowy dodatkowej infrastruktury wodociągowej.

Dwie kolejne funkcje przedsiębiorstwa są partycjonowanie i sesje. Konwencjonalna kolejka usługi Service Bus jest obsługiwana przez brokera pojedynczych wiadomości i przechowywana w magazynie pojedynczych wiadomości. Ale [usługa Service Bus partycjonowanie](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) rozprzestrzenia kolejki w wielu brokerów wiadomości i magazynów komunikatów. Ogólna przepływność nie jest już ograniczona przez wydajność jednego brokera wiadomości lub magazynu wiadomości. Tymczasowa awaria magazynu obsługi wiadomości nie powoduje, że kolejka podzielona na partycje jest niedostępna.

[Sesje usługi Service Bus](https://codingcanvas.com/azure-service-bus-sessions/) umożliwiają dostarczanie wiadomości związanych z grupą. Wyobraź sobie scenariusz przepływu pracy, w którym wiadomości muszą być przetwarzane razem i operacja zakończona na końcu. Aby skorzystać, sesje muszą być jawnie włączone dla kolejki i każdy związany z messaged musi zawierać ten sam identyfikator sesji.

Istnieją jednak pewne ważne zastrzeżenia: rozmiar kolejek usługi Service Bus jest ograniczony do 80 GB, co jest znacznie mniejsze niż dostępne w kolejkach sklepu. Ponadto kolejki usługi Service Bus ponoszą koszt podstawowy i obciążenie za operację.

Rysunek 4-14 przedstawia architekturę wysokiego poziomu kolejki usługi Service Bus.

![Kolejka usługi Service Bus](./media/service-bus-queue.png)

**Rysunek 4-14**. Kolejka usługi Service Bus

Na poprzednim rysunku zanotuj relację punkt-punkt. Dwa wystąpienia tego samego dostawcy są umieszczania w kolejce wiadomości w jednej kolejce usługi Service Bus. Każda wiadomość jest zużywana tylko przez jedno z trzech wystąpień konsumenta po prawej stronie. Następnie omówimy sposób implementowania wiadomości, w których różni konsumenci mogą być zainteresowani tą samą wiadomością.

## <a name="events"></a>Zdarzenia

Kolejkowanie wiadomości jest skutecznym sposobem implementacji komunikacji, w której producent może asynchronicznie wysłać do konsumenta wiadomość. Co się jednak dzieje, gdy *wielu różnych konsumentów* jest zainteresowanych tą samą wiadomością? Dedykowana kolejka komunikatów dla każdego konsumenta nie będzie dobrze skalowana i stałaby się trudna do zarządzania.

Aby rozwiązać ten scenariusz, przechodzimy do trzeciego typu interakcji wiadomości, *zdarzenia*. Jedna mikrousługa informuje, że wystąpiła akcja. Inne mikrousługi, jeśli są zainteresowane, reagować na akcję lub zdarzenia.

Eventing jest procesem dwuetapowym. Dla danej zmiany stanu mikrousługi publikuje zdarzenie do brokera komunikatów, udostępniając go do innych zainteresowanych mikrousług. Zainteresowanych mikrousługi jest powiadamiany przez subskrybowanie zdarzenia w brokera komunikatów. Wzorzec [publikowania/subskrybowania](https://docs.microsoft.com/azure/architecture/patterns/publisher-subscriber) służy do implementowania [komunikacji opartej na zdarzeniach](https://docs.microsoft.com/dotnet/standard/microservices-architecture/multi-container-microservice-net-applications/integration-event-based-microservice-communications).

Rysunek 4-15 przedstawia mikrousługi koszyka zakupów publikowania zdarzenia z dwóch innych mikrousług subskrybujących go.

![Wiadomości sterowane zdarzeniami](./media/event-driven-messaging.png)

**Rysunek 4-15**. Wiadomości sterowane zdarzeniami

Zwróć uwagę na składnik *magistrali zdarzeń,* który znajduje się w środku kanału komunikacyjnego. Jest to klasa niestandardowa, która hermetyzuje brokera komunikatów i oddziela go od podstawowej aplikacji. Mikrousługi zamawiania i zapasów niezależnie obsługują zdarzenie bez znajomości siebie nawzajem, ani mikrousług koszyka zakupów. Gdy zarejestrowane zdarzenie zostanie opublikowane w autobusie zdarzeń, działają na nim.

Wraz z eventingiem przechodzimy od technologii kolejkowania do *tematów.* [Temat](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) jest podobny do kolejki, ale obsługuje wzorzec obsługi wiadomości jeden do wielu. Jedna mikrousługa publikuje komunikat. Wiele mikrousług subskrybujących można wybrać do odbierania i działania na tej wiadomości. Rysunek 4-16 przedstawia architekturę tematu.

![Architektura tematu](./media/topic-architecture.png)

**Rysunek 4-16**. Architektura tematu

Na poprzedniej ilustracji wydawcy wysyłają wiadomości do tematu. Na końcu subskrybenci otrzymują wiadomości z subskrypcji. W środku temat przekazuje wiadomości do subskrypcji na podstawie zestawu *reguł,* wyświetlanych w ciemnoniebieskich polach. Reguły działają jako filtr, który przekazuje określone wiadomości do subskrypcji. W tym miejscu zdarzenie "CreateOrder" \#zostanie wysłane \#do subskrypcji 1 \#i subskrypcji 3, ale nie do subskrypcji 2. Zdarzenie "OrderCompleted" zostanie wysłane \#do subskrypcji \#2 i subskrypcji 3.

Chmura platformy Azure obsługuje dwie różne usługi tematu: Tematy usługi Azure Service Bus i Usługi Azure EventGrid.

### <a name="azure-service-bus-topics"></a>Tematy usługi Azure Service Bus

Obok tego samego niezawodnego modelu wiadomości obsługiwanych przez brokera kolejek usługi Azure Service Bus znajdują się [tematy usługi Azure Service Bus.](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-dotnet-how-to-use-topics-subscriptions) Temat może odbierać wiadomości od wielu niezależnych wydawców i wysyłać wiadomości do maksymalnie 2000 subskrybentów. Subskrypcje mogą być dynamicznie dodawane lub usuwane w czasie wykonywania bez zatrzymywania systemu lub ponownego tworzenia tematu.

Wiele zaawansowanych funkcji kolejek usługi Azure Service Bus jest również dostępnych dla tematów, w tym [wykrywania duplikatów](https://docs.microsoft.com/azure/service-bus-messaging/duplicate-detection) i [obsługi transakcji.](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-transactions) Domyślnie tematy usługi Service Bus są obsługiwane przez brokera pojedynczych wiadomości i przechowywane w magazynie pojedynczych wiadomości. Ale [usługa Service Bus partycjonowanie](https://docs.microsoft.com/azure/service-bus-messaging/service-bus-partitioning) skaluje temat, rozprzestrzeniając go na wielu brokerów wiadomości i magazynów wiadomości.

[Zaplanowane dostarczanie wiadomości](https://docs.microsoft.com/azure/service-bus-messaging/message-sequencing) oznacza wiadomość z określonym czasem przetwarzania. Komunikat nie pojawi się w temacie przed tym czasem. [Odroczenie wiadomości](https://docs.microsoft.com/azure/service-bus-messaging/message-deferral) umożliwia odroczenie pobierania wiadomości do późniejszego czasu. Oba są powszechnie używane w scenariuszach przetwarzania przepływu pracy, w których operacje są przetwarzane w określonej kolejności. Przetwarzanie odebranych wiadomości można odroczyć do czasu zakończenia wcześniejszej pracy.

Tematy usługi Service Bus to niezawodna i sprawdzona technologia umożliwiająca publikowanie/subskrybowanie komunikacji w systemach natywnych dla chmury.

### <a name="azure-event-grid"></a>Azure Event Grid

Usługa Azure Service Bus jest testowanym w bitwa brokerem obsługi wiadomości z pełnym zestawem funkcji przedsiębiorstwa, [usługa Azure Event Grid](https://docs.microsoft.com/azure/event-grid/overview) jest nowym elementem programu typu kid w bloku.

Na pierwszy rzut oka usługa Event Grid może wyglądać jak inny system obsługi wiadomości oparty na temacie. Jednak pod wieloma względami jest inny. Koncentruje się na obciążeniach opartych na zdarzeniach, umożliwia przetwarzanie zdarzeń w czasie rzeczywistym, głęboką integrację z platformą Azure i otwartą platformę — wszystko na infrastrukturze bezserwerowej. Jest przeznaczony do nowoczesnych aplikacji natywnych dla chmury i bezserwerowych

Jako scentralizowana *zasuń i*potoku usługa Event Grid reaguje na zdarzenia wewnątrz zasobów platformy Azure i z własnych usług.

Powiadomienia o zdarzeniach są publikowane w temacie siatki zdarzeń, który z kolei kieruje każde zdarzenie do subskrypcji. Subskrybenci mapują subskrypcje i korzystają ze zdarzeń. Podobnie jak usługa Service Bus, usługa Event Grid obsługuje *filtrowany model subskrybenta,* w którym reguła subskrypcji ustawia dla zdarzeń, które chce otrzymać. Usługa Event Grid zapewnia szybką przepływność z gwarancją 10 milionów zdarzeń na sekundę, umożliwiając dostarczanie w pobliżu czasu rzeczywistego — znacznie więcej niż może generować usługa Azure Service Bus.

Sweet spot dla usługi Event Grid jest jego głębokiej integracji z sieci szkieletowej infrastruktury platformy Azure. Zasób platformy Azure, taki jak Usługa Cosmos DB, może publikować wbudowane zdarzenia bezpośrednio do innych zainteresowanych zasobów platformy Azure — bez konieczności stosowania kodu niestandardowego. Usługa Event Grid może publikować zdarzenia z subskrypcji platformy Azure, grupy zasobów lub usługi, zapewniając deweloperom szczegółową kontrolę nad cyklem życia zasobów w chmurze. Jednak usługa Event Grid nie jest ograniczona do platformy Azure. Jest to otwarta platforma, która może korzystać z niestandardowych zdarzeń HTTP opublikowanych z aplikacji lub usług innych firm i kierować zdarzenia do subskrybentów zewnętrznych.

Podczas publikowania i subskrybowania zdarzeń natywnych z zasobów platformy Azure nie jest wymagane kodowanie. Za pomocą prostej konfiguracji można integrować zdarzenia z jednego zasobu platformy Azure do innego, wykorzystując wbudowaną instalację wodno-kanalizacyjną dla tematów i subskrypcji. Rysunek 4-17 przedstawia anatomię siatki zdarzeń.

![Anatomia siatki zdarzeń](./media/event-grid-anatomy.png)

**Rysunek 4-17**. Anatomia siatki zdarzeń

Główną różnicą między EventGrid i Service Bus jest podstawowy *wzorzec wymiany komunikatów*.

Usługa Service Bus implementuje *model ściągania* starszego stylu, w którym subskrybent podrzędny aktywnie sonduje subskrypcję tematu dla nowych wiadomości. Z drugiej strony takie podejście daje subskrybentowi pełną kontrolę nad tempem, w jakim przetwarza wiadomości. Kontroluje, kiedy i ile wiadomości do przetworzenia w danym momencie. Nieprzeczytane wiadomości pozostają w subskrypcji do czasu przetworzenia. Istotnym mankamentem jest opóźnienie między czasem generowania zdarzenia a operacją sondowania, która pobiera tę wiadomość do subskrybenta w celu przetworzenia. Ponadto obciążenie ciągłego sondowania dla następnego zdarzenia zużywa zasoby i pieniądze.

EventGrid jest jednak inny. Implementuje *model wypychania,* w którym zdarzenia są wysyłane do EventHandlers jako odebrane, dając niemal w czasie rzeczywistym dostarczania zdarzeń. Zmniejsza również koszty, ponieważ usługa jest wyzwalana tylko wtedy, gdy jest to potrzebne do korzystania ze zdarzenia — nie stale, jak w przypadku sondowania. Mimo to program obsługi zdarzeń musi obsługiwać obciążenia przychodzącego i zapewnić mechanizmy ograniczania przepustowości, aby chronić się przed przeciążeniem. Wiele usług platformy Azure, które korzystają z tych zdarzeń, takich jak usługi Azure Functions i aplikacje logiki zapewniają możliwości automatycznego skalowania automatycznego do obsługi zwiększonych obciążeń.  

Event Grid to w pełni zarządzana usługa w chmurze bezserwerowa. Dynamicznie skaluje się w zależności od ruchu i pobiera opłaty tylko za rzeczywiste użycie, a nie za wcześniej zakupioną pojemność. Pierwsze 100 000 operacji miesięcznie jest bezpłatnych — operacje są definiowane jako przychodzące zdarzenia (powiadomienia o zdarzeniach przychodzących), próby dostarczenia subskrypcji, wywołania zarządzania i filtrowanie według tematu. Dzięki dostępności 99,99% EventGrid gwarantuje dostarczenie zdarzenia w ciągu 24 godzin, z wbudowaną funkcją ponawiania prób w przypadku nieudanej dostawy. Niedostarczone wiadomości można przenieść do kolejki "ślepej wiadomości" do rozwiązania.  W przeciwieństwie do usługi Azure Service Bus, usługa Event Grid jest dostrojona pod kątem szybkiej wydajności i nie obsługuje funkcji, takich jak uporządkowane wiadomości, transakcje i sesje.

### <a name="streaming-messages-in-the-azure-cloud"></a>Przesyłanie strumieniowe wiadomości w chmurze platformy Azure

Usługa Azure Service Bus i event grid zapewniają doskonałą obsługę aplikacji, które udostępniają pojedyncze, dyskretne zdarzenia, takie jak nowy dokument został wstawiony do usługi Cosmos DB. Ale co zrobić, jeśli system natywny dla chmury musi przetwarzać *strumień powiązanych zdarzeń?* [Strumienie zdarzeń](https://docs.microsoft.com/archive/msdn-magazine/2015/february/microsoft-azure-the-rise-of-event-stream-oriented-systems) są bardziej złożone. Są one zazwyczaj uporządkowane w czasie, powiązane ze sobą i muszą być przetwarzane jako grupa.

[Usługa Azure Event Hub](https://azure.microsoft.com/services/event-hubs/) to platforma przesyłania strumieniowego danych i usługa pozyskiwania zdarzeń, która zbiera, przekształca i przechowuje zdarzenia. Jest dostrojony do przechwytywania danych przesyłania strumieniowego, takich jak powiadomienia o zdarzeniach ciągłych emitowane z kontekstu telemetrycznego. Usługa jest wysoce skalowalna i może przechowywać i [przetwarzać miliony zdarzeń na sekundę.](https://docs.microsoft.com/azure/event-hubs/event-hubs-about) Pokazano na rysunku 4-18, często jest drzwiami frontowymi dla potoku zdarzeń, odłączając strumień pozyskiwania od zużycia zdarzeń.

![Centrum zdarzeń Azure](./media/azure-event-hub.png)

**Rysunek 4-18**. Centrum zdarzeń Azure

Usługa Event Hub obsługuje małe opóźnienia i konfigurowalne przechowywanie czasu. W przeciwieństwie do kolejek i tematów centra zdarzeń przechowują dane zdarzeń po ich odczytywanie przez konsumenta. Ta funkcja umożliwia innym usługom analitycznym danych, zarówno wewnętrznym, jak i zewnętrznym, odtwarzanie danych w celu dalszej analizy. Zdarzenia przechowywane w Centrum zdarzeń są usuwane tylko po upływie okresu przechowywania, który jest domyślnie jeden dzień, ale konfigurowalne.

Centrum zdarzeń obsługuje typowe protokoły publikowania zdarzeń, w tym HTTPS i AMQP. Obsługuje również platformę Kafka 1.0. [Istniejące aplikacje platformy Kafka mogą komunikować się z Centrum zdarzeń](https://docs.microsoft.com/azure/event-hubs/event-hubs-for-kafka-ecosystem-overview) przy użyciu protokołu platformy Kafka, zapewniając alternatywę dla zarządzania dużymi klastrami platformy Kafka. Wiele systemów typu open source natywnych dla chmury obejmuje platformę Kafka.

Usługa Event Hubs implementuje przesyłanie strumieniowe wiadomości za pośrednictwem [modelu konsumenta na partycje,](https://docs.microsoft.com/azure/event-hubs/event-hubs-features) w którym każdy konsument odczytuje tylko określony podzbiór lub partycję strumienia komunikatów. Ten wzorzec umożliwia ogromną skalę poziomą do przetwarzania zdarzeń i zapewnia inne funkcje skoncentrowane na strumieniu, które są niedostępne w kolejkach i tematach. Partycja to uporządkowana sekwencja zdarzeń przechowywana w centrum zdarzeń. W miarę pojawiania się nowszych zdarzeń są one dodawane na końcu tej sekwencji.Rysunek 4-19 przedstawia partycjonowanie w Centrum zdarzeń.

![Partycjonowanie Centrum zdarzeń](./media/event-hub-partitioning.png)

**Rysunek 4-19**. Partycjonowanie Centrum zdarzeń

Zamiast odczytywania z tego samego zasobu, każda grupa odbiorców odczytuje w podzbiorze lub partycji strumienia komunikatów.

W przypadku aplikacji natywnych dla chmury, które muszą przesyłać strumieniowo dużą liczbę zdarzeń, usługa Azure Event Hub może być niezawodnym i przystępnym cenowo rozwiązaniem.

>[!div class="step-by-step"]
>[Poprzedni](front-end-communication.md)
>[następny](grpc.md)
