---
title: Windows Workflow Foundation 4 wydajności
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: 78e9ac1cc350fe8c04222b2698569412961d3b52
ms.sourcegitcommit: 15d99019aea4a5c3c91ddc9ba23692284a7f61f3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/12/2018
ms.locfileid: "49123816"
---
# <a name="windows-workflow-foundation-4-performance"></a>Windows Workflow Foundation 4 wydajności
Dustin Metzgar

 Wenlong Dong

 We wrześniu 2010 Microsoft Corporation

 Microsoft [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] obejmuje znaczne zmiany programu Windows Workflow Foundation (WF) przy użyciu dużych inwestycji w wydajności.  Ta nowa poprawka wprowadza znaczących zmian z poprzednich wersji [!INCLUDE[wf1](../../../includes/wf1-md.md)] dostarczonego jako część .NET Framework 3.0 i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Została zmieniona od podstawowej w modelu programowania, środowiska uruchomieniowego i narzędzi znacznie zwiększyć wydajność i użyteczność. W tym temacie przedstawiono ważne właściwości działania tych zmian i porównuje je udostępnianych przez poprzednią wersję.

 O rzędów między WF3 i WF4 zwiększyła się wydajność składników określonego przepływu pracy.  Spowoduje to pozostawienie przerwa między kodowane ręcznie usług Windows Communication Foundation (WCF) i usług przepływu pracy WCF być całkiem mały.  Opóźnienie przepływu pracy został znacznie zmniejszony WF4.  Trwałość wydajności został zwiększony współczynnik 3.0 2.5.  Monitorowanie kondycji za pomocą śledzenia przepływu pracy ma znacznie mniejsze obciążenie.  Te są istotne powody do migracji do lub przyjmowania WF4 w swoich aplikacjach.

## <a name="terminology"></a>Terminologia
 Wersja [!INCLUDE[wf1](../../../includes/wf1-md.md)] wprowadzona w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] zostanie określone jako WF4 dla pozostałej części tego tematu.  [!INCLUDE[wf1](../../../includes/wf1-md.md)] wprowadzono w programie .net 3.0 i ma kilka drobnych poprawek przy użyciu [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] z dodatkiem SP1. [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Wersji programu Workflow Foundation będzie wcześniej określano WF3 dla pozostałej części tego tematu. WF3 jest dostarczany w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] side-by-side przy użyciu WF4. Aby uzyskać więcej informacji na temat migrowania artefaktami WF3 WF4 zobacz: [Przewodnik migracji programu Windows Workflow Foundation 4](https://go.microsoft.com/fwlink/?LinkID=153313)

 Windows Communication Foundation (WCF) jest jednolity model programowania firmy Microsoft do budowania aplikacji usługowych. Został po raz pierwszy wprowadzone jako część .net 3.0 wraz z WF3, a teraz jest jednym z głównych elementach [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].

 Windows Server AppFabric to zestaw zintegrowanych technologii, które ułatwiają tworzenie, skalowanie i zarządzanie nimi w sieci Web i aplikacji złożonych, działających w usługach IIS. Udostępnia narzędzia do monitorowania i zarządzania usługami i przepływami pracy. Aby uzyskać więcej informacji, zobacz [systemu Windows Server AppFabric](https://msdn.microsoft.com/windowsserver/ee695849.aspx)

## <a name="goals"></a>Cele
 Celem tego tematu jest pokazanie charakterystyki wydajności WF4 z danymi, mierzone w różnych scenariuszach. Udostępnia również szczegółowe porównanie WF4 WF3 i zawiera doskonałe ulepszeń, które zostały wprowadzone w tej nowej wersji. Scenariusze i dane przedstawione w tym artykule określenie podstawowych kosztów różnych aspektów WF4 WF3. Te dane są przydatne do zrozumienia charakterystyki wydajności WF4 i może być pomocny w planowaniu migracji z WF3 do WF4 lub używając WF4 podczas tworzenia aplikacji. Jednak należy zachować ostrożność w wyciągnięte wnioski dane znajdujące się w tym artykule. Wydajność aplikacji złożonych przepływów pracy jest wysoce zależy od implementacji przepływu pracy i jak różne składniki są zintegrowane. Jeden muszą mierzyć każdej aplikacji, aby określić właściwości działania tej aplikacji.

## <a name="overview-of-wf4-performance-enhancements"></a>Przegląd ulepszeń wydajności WF4
 WF4 dokładnie został opracowany i jest implementowane za pomocą o wysokiej wydajności i skalowalności, które są opisane w poniższych sekcjach.

### <a name="wf-runtime"></a>Środowisko uruchomieniowe programu WF
 W samym sercu [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowisko uruchomieniowe jest asynchroniczne harmonogramu, która napędza wykonywania działań w przepływie pracy. Zapewnia wydajne, środowiska wykonawczego przewidywalne działań. Środowisko ma dobrze zdefiniowanego kontraktu w celu wykonywania, kontynuacja, zakończenia, anulowania, wyjątki i przewidywalne modelu wątkowości.

 Porównaniu WF3 środowisko uruchomieniowe WF4 ma bardziej wydajne harmonogramu. Korzysta z tej samej puli wątków We/Wy, używany do usługi WCF, który jest bardzo wydajny w wykonywania elementów roboczych wsadowej. Wewnętrzny element harmonogramu kolejki jest zoptymalizowany pod kątem najbardziej typowe wzorce użycia. Środowisko uruchomieniowe WF4 zarządza także Państwa wykonanie przebiega bardzo lekkie z minimalnym synchronizacją i obsługi logiki, podczas gdy WF3 zależy od rejestracji ciężki zdarzenia i wywołania w celu przeprowadzenia synchronizacji złożonych stanami zdarzeń.

### <a name="data-storage-and-flow"></a>Magazyn danych i przepływu
 W WF3, dane związane z działaniem jest modelowane przy użyciu właściwości zależności implementowany przez typ. <xref:System.Windows.DependencyProperty>. Wzorzec właściwość zależności został wprowadzony w Windows Presentation Foundation (WPF). Ogólnie rzecz biorąc ten wzorzec jest bardzo elastyczny obsługuje powiązanie danych łatwy i inne funkcje interfejsu użytkownika. Wzorzec wymaga jednak właściwości można zdefiniować jako statyczne pola w definicji przepływu pracy. Zawsze, gdy [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowiska uruchomieniowego, ustawia lub pobiera wartości właściwości, spowodowałoby to logiki intensywnie ważona wyszukiwania.

 WF4 używa Wyczyść dane zakresu logiki znacznie zwiększyć sposobu obsługi danych w przepływie pracy. Rozdziela danych przechowywanych w działaniu z danych, które będą przepływać przez granice działania przy użyciu dwóch różnych pojęć: zmienne i argumenty. Za pomocą czyszczenia hierarchiczne zakres zmienne i argumenty "W/wyjście/wejście-wyjście", złożoność danych użycia dla działania jest znacznie mniejsze i okres istnienia danych również automatycznie o określonym zakresie. Działania mają podpis dobrze zdefiniowanych opisanego przez argumenty. Sprawdzając, czy po prostu działania można określić, jakie dane oczekuje, aby otrzymać i jakie dane zostaną wygenerowane przez nią w wyniku wykonywania.

 W WF3 działania zostały zainicjowane, podczas tworzenia przepływu pracy. W programie WF 4 działań są inicjowane tylko wtedy, gdy są wykonywane odpowiednie działania. Dzięki temu bez przeprowadzania operacji inicjowania/Uninitialize nowe wystąpienie przepływu pracy jest tworzony, gdy ten sposób zdobyła większe przyspiesza cykl życia aktywności

### <a name="control-flow"></a>Przepływ sterowania
 Podobnie jak w przypadku dowolnego języka programowania [!INCLUDE[wf1](../../../includes/wf1-md.md)] zapewnia obsługę przez wprowadzenie do zestawu działań przepływu sterowania do sekwencjonowania, pętli, rozgałęziania i inne wzorce przepływów sterowania dla definicji przepływu pracy. W WF3, gdy tego samego działania musi ponownie uruchomić nowej <xref:System.Workflow.ComponentModel.ActivityExecutionContext> jest tworzony i działanie został sklonowany za pośrednictwem ciężki serializacji i deserializacji logiki na podstawie <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Zwykle wydajność przepływów sterowania iteracyjne jest znacznie wolniejsze niż wykonywanie sekwencję działań.

 WF4 obsługuje to dość w inny sposób. Jego przyjmuje szablon działania, tworzy nowy obiekt ActivityInstance i dodaje go do kolejki harmonogramu. Całego tego procesu obejmuje tworzenie jawnych obiektów i tylko to bardzo lekkie.

### <a name="asynchronous-programming"></a>Programowanie asynchroniczne
 Aplikacje zazwyczaj mają lepszą wydajność i skalowalność za pomocą programowania asynchronicznego rozproszonych operacje obliczeniowe lub długotrwałe blokowania operacjami We/Wy. WF4 zapewnia obsługę asynchroniczną za pośrednictwem typów podstawowego elementu activity <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.AsyncCodeActivity%601>. Środowisko uruchomieniowe natywną obsługę działań asynchronicznych i w związku z tym można automatycznie umieść wystąpienia w strefie no-persist pracę asynchroniczną jest zaległe. Niestandardowe działania może pochodzić z tych typów do wykonywania zadań asynchronicznych bez przytrzymując wątku harmonogramu przepływów pracy i zablokowanie wszelkich działań, które można uruchomić równolegle.

### <a name="messaging"></a>Obsługa wiadomości
 Początkowo zawierała WF3 bardzo ograniczona obsługa komunikatów za pośrednictwem sieci web lub zdarzenia zewnętrzne usługi wywołania. Na platformie .net 3.5, przepływów pracy można zaimplementować jako klienci WCF lub widoczne jako usług WCF za pomocą <xref:System.Workflow.Activities.SendActivity> i <xref:System.Workflow.Activities.ReceiveActivity>. W WF4 koncepcji programowania obsługi komunikatów opartego o przepływ pracy ma zostały wzmocnione dzięki ścisłej integracji WCF komunikatów logikę do programu WF.

 Potok przetwarzania komunikatów ujednoliconego dostarczane w programie WCF w programie .net 4 pomaga WF4 usług znacznie lepszą wydajność i skalowalność niż WF3. WF4 udostępnia bogatszy komunikatów obsługę programowania, która umożliwia modelowanie złożonych wzorców wymiany komunikatów (MEPs). Deweloperzy mogą używać obu kontraktów usług wpisane do osiągnięcia łatwego programowania lub kontraktów usług bez osiągnąć większą wydajność bez ponoszenia kosztów serializacji. Po stronie klienta pamięci podręcznej techniczną za pośrednictwem witryny channel <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy w WF4 pomaga deweloperom wbudowywać szybkie aplikacje przy minimalnym nakładzie pracy. Aby uzyskać więcej informacji, zobacz [Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania](../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).

### <a name="declarative-programming"></a>Programowanie deklaratywne
 WF4 zapewnia prosty i przejrzysty deklaratywne programowania struktura model procesów biznesowych i usług. Model programowania obsługuje w pełni deklaracyjnego kompozycja działań z nie kodu — obok, co znacznie upraszcza tworzenie przepływu pracy. W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], oparte na XAML deklaratywne struktury programistycznej używanej ma zostały zunifikowane w jednym zestawie System.Xaml.dll do obsługiwania obydwu WPF i WF.

 W WF4 XAML zapewnia obsługę rzeczywiście deklaracyjne i umożliwia całą definicję przepływu pracy zdefiniowanych w znaczników XML odwołuje się do działalności i typy utworzone przy użyciu platformy .NET. Taka konfiguracja była trudna zrobić w WF3 przy użyciu formatu XOML, nie angażując logiki niestandardowej związanym z kodem. Nowy stos XAML na platformie .net 4 ma znacznie lepszą wydajność podczas serializacji/deserializacji artefaktów przepływu pracy i sprawia, że programowanie deklaratywne bardziej atrakcyjne wizualnie i stałe.

### <a name="workflow-designer"></a>Projektant przepływu pracy
 Pełni deklaracyjnego programowania obsługę WF4 nakłada jawnie wyższe wymagania dotyczące wydajności w czasie projektowania w przypadku dużych przepływów pracy. Projektant przepływu pracy w WF4 zapewnia znacznie lepszą skalowalność dla przepływów pracy dużych niż WF3. Obsługa wirtualizacji w interfejsie użytkownika Projektant można łatwo obciążenia dużych przepływu pracy 1000 działań w ciągu kilku sekund, podczas ładowania kilku kilkuset działań przepływu pracy za pomocą projektanta WF3 jest prawie niemożliwe.

## <a name="component-level-performance-comparisons"></a>Porównywanie wydajności na poziomie składnika
 Ta sekcja zawiera dane na bezpośrednie porównania między poszczególne działania w przepływach pracy WF3 i WF4.  Kluczowych obszarach, takich jak trwałości mieć dokładniejszych wpływ na wydajność niż składniki poszczególnych działań.  Ulepszenia wydajności w poszczególnych składnikach w WF4 są jednak ważne składniki są wystarczająco szybko, który będzie porównywany logiki aranżacji kodowane ręcznie.  Przykładem są omówione w następnej sekcji: "Scenariuszu składu usługi".

### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

 Powyższej ilustracji konfiguracji komputera, używany do pomiaru wydajności na poziomie składnika. Pojedynczy serwer i klienci pięć połączone jednego interfejsu sieciowego Ethernet 1 GB/s. Łatwe pomiarów serwer jest skonfigurowany do użycia pojedynczego rdzenia proc/quad dwurdzeniowy serwera działającego pod kontrolą systemu Windows Server 2008 x86. System wykorzystanie procesora CPU jest zachowywana w prawie 100%.

### <a name="test-details"></a>Szczegóły testu
 WF3 <xref:System.Workflow.Activities.CodeActivity> jest prawdopodobnie najprostszą działanie, które mogą być używane w przepływie pracy WF3.  Działanie wywołuje metodę w związanym z kodem, programisty przepływu pracy można umieścić kod niestandardowy do.  W WF4, nie istnieje żadne bezpośrednie analogowy na WF3 <xref:System.Workflow.Activities.CodeActivity> zapewniający taką samą funkcjonalność.  Należy zauważyć, że istnieje <xref:System.Activities.CodeActivity> podstawowej klasy w WF4, który nie jest powiązana z WF3 <xref:System.Workflow.Activities.CodeActivity>.  Autorzy przepływu pracy są zachęcani do tworzenia niestandardowych działań i tworzenie przepływów pracy XAML — tylko.  W przypadku testów o nazwie działanie `Comment` jest używany zamiast pustego <xref:System.Workflow.Activities.CodeActivity> w przepływach pracy WF4.  Kod w `Comment` działanie jest w następujący sposób:

```
[ContentProperty("Body")]
    public sealed class Comment : CodeActivity
    {
        public Comment()
            : base()
        {
        }

        [DefaultValue(null)]
        public Activity Body
        {
            get;
            set;
        }

        protected override void Execute(CodeActivityContext context)
        {
        }
    }
```

### <a name="empty-workflow"></a>Pusty przepływ pracy
 Ten test za nie działania podrzędne sekwencyjny przepływ pracy.

### <a name="single-activity"></a>Pojedyncze działanie
 Przepływ pracy jest przepływ pracy sekwencji zawierające jedną działania podrzędnego.  Działanie jest <xref:System.Workflow.Activities.CodeActivity> bez kodu, w tym przypadku WF3 i `Comment` działanie w przypadku WF4.

### <a name="while-with-1000-iterations"></a>Czas z 1000 iteracji
 Sekwencyjny przepływ pracy zawiera jeden <xref:System.Activities.Statements.While> działania o jeden element podrzędny działania w pętli, która nie wykonuje żadnych działań.

### <a name="replicator-compared-to-parallelforeach"></a>Replikator w porównaniu do ParallelForEach
 <xref:System.Workflow.Activities.ReplicatorActivity> w WF3 ma tryby wykonywania sekwencyjnego i równoległego.  W trybie sekwencyjne wydajności działania przypomina <xref:System.Workflow.Activities.WhileActivity>.  <xref:System.Workflow.Activities.ReplicatorActivity> Jest najbardziej przydatne do przetwarzania równoległego.  Jest analogowy WF4 tego <xref:System.Activities.Statements.ParallelForEach%601> działania.

 Na poniższym diagramie przedstawiono przepływów pracy, używane dla tego testu. Przepływ pracy WF3 znajduje się po lewej stronie i WF4 przepływ pracy znajduje się po prawej stronie.

 ![WF3 ReplicatorActivity i WF4 ParallelForEach](../../../docs/framework/windows-workflow-foundation/media/replicatorandparallelforeach.gif "ReplicatorAndParallelForEach")

### <a name="sequential-workflow-with-five-activities"></a>Sekwencyjny przepływ pracy z pięciu działań
 Ten test jest przeznaczona do wyświetlenia efekt posiadanie kilku działań wykonywanie było sekwencyjne.  Ma pięciu działań w sekwencji.

### <a name="transaction-scope"></a>Zakres transakcji
 Test zakresu transakcji różni się od innych testów, nowe wystąpienie przepływu pracy nie został utworzony dla każdej iteracji.  Zamiast tego przepływu pracy są skonstruowane z chwilę zawierający pętli <xref:System.Activities.Statements.TransactionScope> działania zawierające jedno działanie, które nie działa.  Każde uruchomienie partii 50 iteracji za pośrednictwem while pętli są traktowane jako pojedyncza operacja.

### <a name="compensation"></a>Kompensacja
 Przepływ pracy WF3 ma jedno działanie możliwy do kompensacji o nazwie `WorkScope`.  Działania po prostu implementuje <xref:System.Workflow.ComponentModel.ICompensatableActivity> interfejsu:

```
class WorkScope :
        CompositeActivity, ICompensatableActivity
    {
        public WorkScope() : base() { }

        public WorkScope(string name)
        {
            this.Name = name;
        }

        public ActivityExecutionStatus Compensate(
            ActivityExecutionContext executionContext)
        {
            return ActivityExecutionStatus.Closed;
        }
    }
```

 Elementy docelowe programu obsługi błędów `WorkScope` działania. Przepływ pracy WF4 jest równie uproszczony.  Element <xref:System.Activities.Statements.CompensableActivity> ma treść i procedurę obsługi.  Jawne compensate jest dalej w sekwencji.  Działanie treści i rekompensaty działanie procedury obsługi są obu implementacjach pusta:

```
public sealed class CompensableActivityEmptyCompensation : CodeActivity
    {
        public CompensableActivityEmptyCompensation()
            : base() { }

        public Activity Body { get; set; }

        protected override void Execute(CodeActivityContext context) { }
    }
    public sealed class CompensableActivityEmptyBody : CodeActivity
    {
        public CompensableActivityEmptyBody()
            : base() { }

        public Activity Body { get; set; }

        protected override void Execute(CodeActivityContext context) { }
    }
```

 ![Przepływy pracy podstawowe wynagrodzenie WF3 i WF](../../../docs/framework/windows-workflow-foundation/media/basiccompensationworkflows.gif "BasicCompensationWorkflows")

 Rysunek 2 — WF3 (po lewej) i przepływów pracy () po wybraniu właściwego wynagrodzenie WF4

### <a name="performance-test-results"></a>Wyniki testów wydajności
 ![Wyniki testów wydajności](../../../docs/framework/windows-workflow-foundation/media/performancedata.gif "elementu PerformanceData")

 ![Wykres danych testu wydajności](../../../docs/framework/windows-workflow-foundation/media/performancetestchart.gif "PerformanceTestChart")

 Wszystkie testy są mierzone w przepływach pracy na sekundę, z wyjątkiem testowych zakresu transakcji.  Jak widać w przedstawionym powyżej [!INCLUDE[wf1](../../../includes/wf1-md.md)] poprawiła wydajność środowiska uruchomieniowego w tablicy, zwłaszcza w obszarach, które wymagają wiele wykonań tego samego działania, takie jak while pętli.

## <a name="service-composition-scenario"></a>Scenariusz kompozycji obsługi
 Jak pokazano w poprzedniej sekcji "składnika poziom wydajności porównania" nastąpiła znaczny spadek obciążenie między WF3 i WF4.  Usługi przepływu pracy WCF można teraz prawie pasuje wydajność usług WCF kodowane ręcznie, ale nadal mieć wszystkie zalety [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowiska uruchomieniowego.  Ten scenariusz testów porównuje względem usługi przepływu pracy WCF w WF4 usługi WCF.

### <a name="online-store-service"></a>Usługi online Store
 Jedną z zalet programu Windows Workflow Foundation jest możliwość tworzenia procesów przy użyciu kilku usług.  W tym przykładzie jest usługą sklep online, która organizuje dwóch wywołań usług na zamówienie zakupu.  Pierwszym krokiem jest Sprawdź poprawność kolejności przy użyciu usługi z weryfikowanie zamówienia.  Drugim krokiem jest do realizacji zamówienia, korzystając z usługi magazynu.

 Te dwie usługi wewnętrznej bazy danych usługi weryfikowanie zamówienia i usługi magazynu, pozostają takie same dla obu testów.  Części, która zmienia się to usługa Online Store, która wykonuje aranżacji.  W przypadku jednego usługa jest ręcznie zakodowane jako usługa WCF.  W przypadku usługi są zapisywane jako usługi przepływu pracy WCF w WF4. [!INCLUDE[wf1](../../../includes/wf1-md.md)]-określone funkcje, takie jak śledzenie i trwałości są wyłączone dla tego testu.

### <a name="environment"></a>Środowisko
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

 Żądania klienta są kierowane do usługi Online Store za pośrednictwem protokołu HTTP z wielu komputerów.  Pojedynczy komputer obsługuje wszystkie trzy usługi.  Warstwa transportu między Online usługą Store i usługami zaplecza jest TCP lub HTTP.  Pomiar operacji na sekundę zależy od liczby ukończonych `PurchaseOrder` wywołań do usługi Online Store.  Buforowanie kanału to nowa funkcja dostępna w WF4.  W programie WCF część tej buforowanie kanału testu nie zostanie podany gotowych, kodowane ręcznie implementacji proste techniki buforowania został użyty w usłudze Store w trybie Online.

### <a name="performance"></a>Wydajność
 ![Wykres wydajności usługi online Store](../../../docs/framework/windows-workflow-foundation/media/onlinestoreperfgraph.gif "OnlineStorePerfGraph")

 Łączenie z usługami TCP wewnętrznej bazy danych, bez buforowania kanału, [!INCLUDE[wf1](../../../includes/wf1-md.md)] usługi ma wpływ 17.2% na przepływności.  Za pomocą kanału buforowanie, kary wynosi około 23,8%.  W przypadku protokołu HTTP wpływ jest znacznie mniej: % 4.3, bez buforowania i % 8.1 z puli.  Jest również pamiętać, że buforowanie kanału zapewnia bardzo niewielkie korzyści, gdy przy użyciu protokołu HTTP.

 Choć obciążenie ze środowiska wykonawczego WF4 w porównaniu z usługą WCF kodowane ręcznie w tym teście, należy uważać scenariuszu najgorszego przypadku.  Te dwie usługi wewnętrznej bazy danych, w tym teście zrobić bardzo małego wysiłku.  W scenariuszu rzeczywistym end-to-end te usługi przeprowadza się bardziej kosztowne operacje, takie jak wywołania bazy danych, co mniej istotny wpływ na wydajność warstwy transportowej.  To plus korzyści z funkcji dostępnych w WF4 sprawia, że Workflow Foundation wyboru możliwego do użycia do tworzenia usług aranżacji.

## <a name="key-performance-considerations"></a>Kluczowe zagadnienia dotyczące wydajności
 Obszary funkcji w tej sekcji, z wyjątkiem współdziałania, zmieniły się znacznie między WF3 i WF4.  Ma to wpływ na projekt aplikacji przepływu pracy, a także wydajność.

#### <a name="workflow-activation-latency"></a>Opóźnienie aktywacji przepływu pracy
 W aplikacji usługi przepływu pracy WCF czas oczekiwania na uruchomienie nowego przepływu pracy lub ładowania istniejącego przepływu pracy jest ważne, ponieważ może blokować.  Ten przypadek testowy środków hosta WF3 XOML przed hostem WF4 XAMLX w typowym scenariuszu.

##### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Konfigurowanie środowiska do testów opóźnienia i przepływności](../../../docs/framework/windows-workflow-foundation/media/latencyandthroughputenvironment.gif "LatencyAndThroughputEnvironment")

##### <a name="test-setup"></a>Testuj ustawienia
 W tym scenariuszu komputer kliencki kontaktuje się z usług przepływu pracy WCF dzięki wykorzystaniu korelacja oparta na kontekście.  Kontekst korelacji wymaga specjalnych kontekst powiązania i używa nagłówka kontekstu lub plik cookie do powiązania komunikatów dla wystąpienia przepływu pracy poprawne.  Ma ona wydajności korzyści w tym korelacji, której identyfikator znajduje się w nagłówku komunikatu, więc treść komunikatu musi zostać przeanalizowany.

 Usługa utworzy nowy przepływ pracy z tym żądaniem i Wyślij natychmiastowej reakcji pomiaru opóźnienia nie obejmuje czas uruchamiania przepływu pracy.  Przepływ pracy WF3 jest XOML związanego z kodem i WF4 przepływu pracy jest całkowicie XAML.  Przepływ pracy WF4 wygląda następująco:

 ![WF 4 korelacji zakresu](../../../docs/framework/windows-workflow-foundation/media/correlationscopeworkflow.gif "CorrelationScopeWorkflow")

 <xref:System.ServiceModel.Activities.Receive> Działanie tworzy wystąpienie przepływu pracy.  Wartość przekazana w odebranej wiadomości jest powtarzana w komunikacie odpowiedzi.  Sekwencja następujące odpowiedź zawiera przepływ pracy.  W przypadku powyższych działań tylko jeden komentarz jest wyświetlany.  Liczba działań w komentarz zostanie zmieniony na symulować złożoności przepływu pracy.  Działanie komentarza jest odpowiednikiem WF3 <xref:System.Workflow.Activities.CodeActivity> , nie wykonuje żadnych operacji. Aby uzyskać więcej informacji o działaniu komentarz zobacz sekcję "porównania wydajności poziomie składnika" wcześniej w tym artykule.

##### <a name="test-results"></a>Wyniki tekstu
 ![Czas oczekiwania na wyniki](../../../docs/framework/windows-workflow-foundation/media/latencyresultsgraph.gif "LatencyResultsGraph")

 Rysunek 3 — zimno i ogrzewać opóźnienia w przypadku usług przepływu pracy WCF

 Na powyższym wykresie zimnego odwołuje się do sprawy w przypadku, gdy nie ma, nie istnieje <xref:System.ServiceModel.WorkflowServiceHost> dla danego przepływu pracy.  Innymi słowy czas oczekiwania na zimno jest podczas przepływu pracy jest używany po raz pierwszy i XOML lub XAML musi być skompilowana.  Czas oczekiwania na ciepło to czas do utworzenia nowego wystąpienia przepływu pracy, gdy typ przepływu pracy został już wcześniej skompilowany.  Złożoność przepływu pracy sprawia, że bardzo niewielkie różnice w przypadku WF4, ale ma progresji liniowej w przypadku WF3.

#### <a name="correlation-throughput"></a>Przepływność korelacji
 WF4 wprowadzono nową funkcję korelacji na podstawie zawartości.  WF3 podany tylko korelacja oparta na kontekście.  Korelacja oparta na kontekście może być przeprowadzone wyłącznie za pośrednictwem określonego powiązania kanału WCF.  Identyfikator przepływu pracy są wstawiane do nagłówka wiadomości, korzystając z tych powiązań.  Środowisko uruchomieniowe WF3 tylko można zidentyfikować przepływu pracy za pomocą jego identyfikatora.  Za pomocą opartego na zawartości korelacji Autor przepływu pracy może utworzyć klucz korelacji poza odpowiednie części danych, takich jak numer konta lub klienta identyfikator.

 Korelacja oparta na kontekście ma korzystać wydajności, w tym, że klucz korelacji znajduje się w nagłówku komunikatu.  Klucz można odczytać z wiadomość bez cofania-serialization/komunikat kopiowania.  W korelacja oparta na zawartości klucz korelacji jest przechowywany w treści komunikatu.  Wyrażenie XPath jest używana do lokalizowania klucza.  Koszt tego dodatkowego przetwarzania zależy od rozmiaru wiadomości głębokość klucza w treści i liczbę kluczy.  Ten test porównuje korelacji na podstawie kontekstu i zawartości i pokazuje również obniżenia wydajności w przypadku korzystania z wielu kluczy.

#### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

#### <a name="test-setup"></a>Testuj ustawienia
 ![Test przepływu pracy przepływności korelacji](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputworkflow.gif "CorrelationThroughputWorkflow")

 Przepływ pracy powyżej jest taka sama, używany w sekcji "Trwałość" poniżej.  W przypadku testów korelacji bez trwałości nie ma trwałości dostawcy zainstalowane w środowisku uruchomieniowym.  Korelacja odbywa się w dwóch miejscach: CreateOrder i CompleteOrder.

#### <a name="test-results"></a>Wyniki tekstu
 ![Przepływność korelacji](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputgraph.gif "CorrelationThroughputGraph")

 Ten wykres pokazuje spadek wydajności jako liczba kluczy używanych do zwiększenia korelacji na podstawie zawartości.  Podobieństwa krzywych między TCP i HTTP wskazuje obciążenia związanego z tych protokołów.

#### <a name="correlation-with-persistence"></a>Korelacja z trwałości
 Za pomocą utrwalonych przepływu pracy wykorzystanie procesora CPU z korelacji na podstawie zawartości przenosi ze środowiska wykonawczego przepływów pracy z bazą danych SQL.  Procedur składowanych w dostawcy stanów trwałych programu SQL spełniała zgodności kluczy, aby zlokalizować odpowiedni przepływ pracy.

 ![Wyniki korelacji i trwałości](../../../docs/framework/windows-workflow-foundation/media/correlationandpersistencegraph.gif "CorrelationAndPersistenceGraph")

 Korelacja oparta na kontekście jest nadal szybciej niż korelacji na podstawie zawartości.  Jednak różnica jest mniejsza wymawiane jako trwałości ma większy wpływ na wydajność niż korelacji.

### <a name="complex-workflow-throughput"></a>Przepływność złożonych przepływów prac
 Złożoność przepływu pracy nie jest mierzona tylko przez liczbę działań.  Działań złożonych może zawierać wiele podrzędnych, a te elementy podrzędne mogą być również działań złożonych.  Jako liczba poziomów zagnieżdżenia zwiększa to samo dotyczy liczby działań, które mogą być obecnie w stanie Wykonywanie i liczba zmiennych, które mogą być w stanie.  Ten test porównuje przepływności między WF3 i WF4 podczas wykonywania złożonych przepływów pracy.

### <a name="test-setup"></a>Testuj ustawienia
 Te testy zostały wykonane na Intel Xeon X5355 @ procesor 2,66 GHz 4 sposób komputera z 4 GB pamięci RAM, systemem Windows Server 2008 x64.  Kod testu jest uruchamiany w ramach jednego procesu z jednego wątku na każdy rdzeń do osiągnięcia 100% wykorzystanie Procesora.

 Przepływy pracy, generowany dla tego testu mają dwóch głównych zmiennych: głębokość i liczbę działań zawartych w poszczególnych sekwencji.  Każdy poziom głębokość zawiera działania równoległego, podczas pętli, decyzje, przydziały i sekwencji.  W Projektancie WF4 na obrazku poniżej najwyższego poziomu blokowy jest przedstawiony.  Każde działanie schemat blokowy przypomina głównym schematu blokowego.  Może być można wyobrazić sobie fraktalowy podczas picturing ten przepływ pracy, gdzie głębokość jest ograniczona do parametrów testu.

 Liczba działań w dany test zależy od głębokości i liczba działań w sekwencji.  Poniższego równania oblicza liczbę działań w teście WF4:

 ![Równania do obliczenia liczby działań](../../../docs/framework/windows-workflow-foundation/media/numberofactivitiesequation.gif "NumberOfActivitiesEquation")

 Liczba działań testów WF3 może zostać obliczony z nieco równania ze względu na dodatkowe sekwencji:

 ![Równania do obliczenia liczby działań](../../../docs/framework/windows-workflow-foundation/media/w3numberofactivitiesequation.gif "W3NumberOfActivitiesEquation")

 Gdzie głębokość d, a jeśli tak, to a jest liczba działań w sekwencji.  Logiki stojącej za tymi równania jest, że pierwszym stała mnożona przez, jest numerem sekwencji, a drugi — stała jest statyczny liczbę działań zawartych w bieżącym poziomie.  Istnieją trzy działania podrzędne schemat blokowy w każdym schemacie blokowym.  Na najniższym poziomie głębokość blokowych te są puste, ale na innych poziomach są kopie głównym schematu blokowego.  Liczba działań w definicji przepływu pracy poszczególnych odmian test jest oznaczany w poniższej tabeli:

 ![Porównuje liczbę działań używanych w poszczególnych testów](../../../docs/framework/windows-workflow-foundation/media/comparechart.gif "CompareChart")

 Liczba działań w definicji przepływu pracy znacznie zwiększa się, każdy poziom głębi.  Ale tylko jedna ścieżka na podjęcie decyzji, czy jest wykonywana w wystąpienia danego przepływu pracy, wykonywane są tylko mały podzbiór rzeczywistych działań.

 ![Złożonych przepływów prac](../../../docs/framework/windows-workflow-foundation/media/complexworkflowthroughputworkflow.gif "ComplexWorkflowThroughputWorkflow")

 Przepływ pracy równoważnych został utworzony dla WF3. Projektant WF3 pokazuje całego przepływu pracy w obszarze projektowania zamiast zagnieżdżania, dlatego jest zbyt duży do wyświetlenia w tym temacie. Poniżej przedstawiono fragment przepływu pracy.

 ![WF3 Przepływ pracy](../../../docs/framework/windows-workflow-foundation/media/wf3workflow.gif "WF3Workflow")

 Do wykonania zagnieżdżenia w ekstremalnych przypadkach, inny przepływ pracy, który jest częścią tego testu używa 100 sekwencje zagnieżdżone.  Najbardziej wewnętrzny sekwencji jest pojedynczy `Comment` lub <xref:System.Workflow.Activities.CodeActivity>.

 ![Sekwencje zagnieżdżone](../../../docs/framework/windows-workflow-foundation/media/nestedsequencewf.gif "NestedSequenceWF")

 Śledzenie i trwałości nie są używane jako część tego testu.

### <a name="test-results"></a>Wyniki tekstu
 ![Wykres przepływności](../../../docs/framework/windows-workflow-foundation/media/testresults1.gif "TestResults1")

 Nawet w przypadku złożonych przepływów pracy za pomocą mnóstwo głębi i dużą liczbę działań wyniki są zgodne z inne liczby przepływności przedstawiony we wcześniejszej części tego artykułu.  Przepływność WF4 firmy jest szybsza rzędy wielkości i ma być porównywana na skali logarytmicznej.

### <a name="memory"></a>Pamięć
 Obciążenie pamięci programu Windows Workflow Foundation jest mierzony w dwóch podstawowych obszarach: złożoność przepływu pracy i liczbę definicji przepływu pracy.  Pomiary pamięci zostały pobrane na stacji roboczej x 64 Windows 7.  Istnieje wiele sposobów na uzyskanie pomiarów Ustaw rozmiar, takich jak monitorowanie liczników wydajności, sondowanie Environment.WorkingSet lub przy użyciu narzędzia, takiego jak VMMap dostępne praca [VMMap](/sysinternals/downloads/vmmap). Kombinacji metod został użyty do uzyskania i sprawdzić wyniki każdego testu.

### <a name="workflow-complexity-test"></a>Test złożoności przepływu pracy
 Złożoność przepływu pracy testu środków zestaw roboczy różnica, zależnie od stopnia złożoności przepływu pracy.  Oprócz złożone przepływy pracy, wykorzystywane w poprzedniej sekcji, nowe zmiany są dodawane do obejmuje dwa podstawowe przypadki: jedno działanie przepływu pracy i sekwencję działań 1000.  Testy te przepływy pracy są zainicjowany i wykonywane w celu ukończenia w jednej pętli szeregowe w okresie jednej minuty.  Poszczególnych odmian test jest uruchamiany trzy razy, a dane zapisane jest średnią z tych trzech przebiegów.

 Dwie nowe podstawowe testy mają przepływy pracy, wyglądające podobnie jak pokazano poniżej:

 ![Złożone przepływy pracy](../../../docs/framework/windows-workflow-foundation/media/complexworkflowboth.gif "ComplexWorkflowBoth")

 W przepływie pracy WF3 powyżej pusty <xref:System.Workflow.Activities.CodeActivity> działania są używane.  Przepływ pracy WF4 powyżej używa `Comment` działań.  `Comment` Działanie zostało opisane w sekcji porównania wydajności poziomie składników we wcześniejszej części tego artykułu.

 ![Wykres użycia pamięci](../../../docs/framework/windows-workflow-foundation/media/complexmemoryusage.gif "ComplexMemoryUsage")

 Jednym z wyczyść trendów, które należy zwrócić uwagę na tym wykresie jest, że zagnieżdżanie ma względnie minimalny wpływ na użycie pamięci w WF3 i WF4.  Największy wpływ pamięci pochodzi z liczbę działań w danym przepływu pracy.  Mając dane z sekwencji 1000, złożonych głębokość 5 sekwencji 5 i złożonych głębokość 7 sekwencji 1 odmiany, jest jasne, że podczas tysięcy liczbę działań, wzrost użycia pamięci staje się bardziej zauważalne.  W przypadku extreme (głębokość 7 sekwencji 1) w przypadku działania ~ 29K WF4 przy użyciu prawie 79% mniej pamięci niż WF3.

### <a name="multiple-workflow-definitions-test"></a>Wiele testów definicji przepływu pracy
 Ze względu na dostępne opcje do hostowania przepływów pracy w programie WF3 i WF4, pomiaru pamięci dla definicji przepływu pracy jest podzielony na dwóch różnych badań.  Testy są uruchamiane w inny sposób niż badanie złożoności przepływu pracy, w tym danego przepływu pracy jest wystąpienia i wykonywane tylko raz w każdej definicji.  Jest to spowodowane definicji przepływu pracy i jej hostem pozostają w pamięci dla okresu istnienia domeny aplikacji.  Można wyczyścić pamięci używanej przez uruchomione wystąpienie danego przepływu pracy w podczas wyrzucania elementów bezużytecznych.  Wskazówki dotyczące migracji dla WF4 zawiera bardziej szczegółowe informacje na temat opcji hostingu. Aby uzyskać więcej informacji, zobacz [Podręcznik migracji WF: hostowanie przepływu pracy](https://go.microsoft.com/fwlink/?LinkID=153313).

 Tworzenie wielu definicji przepływu pracy w celu przetestowania definicji przepływu pracy można wykonać na kilka sposobów.  Na przykład jedna Użyj generowania kodu, aby utworzyć zbiór 1000 przepływów pracy, które są identyczne, z wyjątkiem nazwy i zapisać każdy z tych przepływów pracy w osobnych plikach.  Ta metoda została wykonana dla testu hostowanymi w konsoli.  W WF3 <xref:System.Workflow.Runtime.WorkflowRuntime> klasy został użyty do uruchomienia definicji przepływu pracy.  WF4 można użyć <xref:System.Activities.WorkflowApplication> do utworzenia wystąpienia jeden przepływ pracy lub bezpośrednio przy użyciu <xref:System.Activities.WorkflowInvoker> do uruchomienia wybranego działania, jak w przypadku wywołania metody.  <xref:System.Activities.WorkflowApplication> host wystąpienia jeden przepływ pracy i ma bliżej równoważności funkcji, aby <xref:System.Workflow.Runtime.WorkflowRuntime> tak, aby został użyty w tym teście.

 W przypadku hostowania przepływów pracy w usługach IIS jest możliwość użycia <xref:System.Web.Hosting.VirtualPathProvider> do tworzenia nowego <xref:System.ServiceModel.WorkflowServiceHost> zamiast generować wszystkie pliki XAMLX lub pliku XOML.  <xref:System.Web.Hosting.VirtualPathProvider> Obsługuje przychodzące żądanie i odpowiada za pomocą "wirtualnego pliku", która może być załadowana z bazy danych lub, w tym przypadku jest generowane na bieżąco.  Jest konieczne utworzyć pliki fizyczne 1000.

 Definicje przepływów pracy używanych w teście konsoli były proste sekwencyjne przepływy pracy za pomocą jednego działania.  Pojedyncze działanie była pusta <xref:System.Workflow.Activities.CodeActivity> przypadku WF3 i `Comment` działanie w przypadku WF4.  W przypadku hostowanych przez usługi IIS używane przepływów pracy rozpoczynających się po odebraniu wiadomości i zakończenia na wysyłanie odpowiedzi:

 ![Usługi przepływu pracy w WF3 i WF4](../../../docs/framework/windows-workflow-foundation/media/receiveworkflowboth.gif "ReceiveWorkflowBoth")

 Rysunek 4 — WF3 przepływu pracy, za pomocą działania ReceiveActivity i WF4 przepływu pracy przy użyciu wzorca żądanie/odpowiedź

 W poniższej tabeli przedstawiono różnicowej w zestawie roboczym między definicji jeden przepływ pracy i definicje 1001:

|Opcje hostingu|WF3 Różnica zestawu roboczego|WF4 Różnica zestawu roboczego|
|---------------------|---------------------------|---------------------------|
|Aplikacja konsoli hostowana przepływów pracy|18 MB|9 MB|
|Przepływ pracy usługi hostowanej w programie IIS|446 MB|364 MB|

 Hosting definicji przepływu pracy w usługach IIS zużywa znacznie większej ilości pamięci, ze względu na <xref:System.ServiceModel.WorkflowServiceHost>, szczegółowe artefaktów usługi WCF i przetwarzania logiki skojarzonej z hostem wiadomości.

 Dla konsoli hostowanie WF3 przepływy pracy zostały wprowadzone w kodzie zamiast pliku XOML.  W WF4 wartość domyślna jest użycie XAML.  XAML jest przechowywany jako zasobu osadzonego w zestawie i kompilowane w czasie wykonywania, aby zapewnić implementację przepływu pracy.  Istnieje pewne nadmiarowe obciążenie związane z tym procesem.  W celu uczciwe porównanie WF3 WF4, kodowane przepływy pracy były używane zamiast XAML.  Na przykład jeden z przepływów pracy WF4 znajdują się poniżej:

```
public class Workflow1 : Activity
{
    protected override Func<Activity> Implementation
    {
        get
        {
            return new Func<Activity>(() =>
            {
                return new Sequence
                {
                    Activities = {
                        new Comment()
                    }
                };
            });
        }
        set
        {
            base.Implementation = value;
        }
    }
}
```

 Istnieje wiele czynników, które mogą mieć wpływ na zużycie pamięci. Nadal mają zastosowanie tego samego wskazówki dotyczące wszystkich programów zarządzanych.  W środowiskach hostowanych przez usługi IIS <xref:System.ServiceModel.WorkflowServiceHost> obiekt utworzony dla definicji przepływu pracy pozostaje w pamięci, dopóki pula aplikacji zostanie odtworzona.  Powinna być ograniczona pamiętać podczas zapisywania rozszerzenia.  Ponadto najlepiej jest uniknąć "global" zmienne (zmienne o zakresie do całego przepływu pracy) i ograniczyć zakres zmiennych, tam gdzie to możliwe.

## <a name="workflow-runtime-services"></a>Usługi czasu wykonywania przepływu pracy

### <a name="persistence"></a>Stan trwały
 WF3 oraz WF4 zarówno dostarczane z dostawcy stanów trwałych programu SQL.  Dostawcy stanów trwałych programu SQL WF3 jest proste wdrażanie, który serializuje wystąpienia przepływu pracy i zapisuje go w obiekcie blob.  Z tego powodu wydajności tego dostawcy intensywnie zależna od rozmiaru wystąpienia przepływu pracy.  W WF3 rozmiar wystąpienia może zwiększyć z wielu powodów, jak omówiono wcześniej w tym dokumencie.  Wielu klientów decyduje się nie należy używać domyślnego dostawcy stanów trwałych programu SQL, ponieważ przechowywania Zserializowany wystąpienie w bazie danych zapewniające nie wgląd w stan przepływu pracy.  Aby można było znaleźć określonego przepływu pracy, nie wiedząc o tym identyfikator przepływu pracy, jeden musi deserializacji każdego utrwalonego wystąpienia i sprawdzać zawartość.  Wielu programistów chce napisać własne dostawcy stanów trwałych, aby obejść ten problem.

 Dostawcy stanów trwałych programu SQL WF4 próbował rozwiązać niektóre z tych problemów.  Tabele trwałości ujawnić pewne informacje, takie jak active zakładek i Awansowanie właściwości.  Nowa funkcja korelacji na podstawie zawartości w WF4 nie przeprowadza się również za pomocą podejścia trwałości WF3 SQL ma opartych na niektóre zmiany w organizacji utrwalonego wystąpienia przepływu pracy.  To sprawia, że dostawcy stanów trwałych bardziej złożone i umieszcza dodatkowe obciążenia w bazie danych.

### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

### <a name="test-setup"></a>Testuj ustawienia
 Nawet w przypadku zestawu funkcji ulepszone i lepsza obsługa współbieżności dostawcy stanów trwałych programu SQL w WF4 jest szybsze niż dostawcy w WF3.  Aby zaprezentować, to, dwa przepływy pracy, które wykonują głównie operacje WF3 i WF4 są porównywane poniżej.

 ![Przepływy pracy trwałości](../../../docs/framework/windows-workflow-foundation/media/persistworkflow.gif "PersistWorkflow")

 Rysunek 5 — trwałość przepływu pracy WF3 w lewo i WF4 po prawej stronie

 Dwa przepływy pracy są tworzone przez odebranego komunikatu.  Po wysłaniu odpowiedzi na wiadomość początkowej, przepływ pracy jest trwały.  W przypadku WF3 pustą <xref:System.Workflow.ComponentModel.TransactionScopeActivity> służy do inicjowania trwałości.  Taki sam mógł zostać osiągnięty w WF3, oznaczając działanie jako "utrwalanie w pobliżu".  Drugi skorelowany komunikat kończy przepływ pracy.  Przepływy pracy są zachowywane, ale nie zostały załadowane.

### <a name="test-results"></a>Wyniki tekstu
 ![Trwałość przepływności](../../../docs/framework/windows-workflow-foundation/media/throughputpersistence.gif "ThroughputPersistence")

 Podczas transportu między klienta i warstwą środkową, jest protokół HTTP, trwałość WF4 wykazuje wzrost 2,6 razy.  Warstwy transportowej TCP zwiększa ten współczynnik na czas 3.0.  We wszystkich przypadkach, użycie procesora CPU w warstwie środkowej wynosi 98% lub nowszej.  Przyczyna czy WF4 przepływność wynosi powyżej wynika z szybsze środowisko wykonawcze przepływów pracy.  Rozmiar wystąpienia serializacji brakuje w obu przypadkach i nie jest głównym elementem mającym swój wkład w takiej sytuacji.

 WF3 i WF4 przepływów pracy w tym teście umożliwia jawnie wskazywać, kiedy stan trwały powinny być wykonywane działania.  To ma tę zaletę utrwalanie przepływu pracy bez rozładowywania go.  W WF3, jest również możliwe utrwalanie przy użyciu <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> funkcji, ale zwalnia wystąpienie przepływu pracy z pamięci.  Jeśli Deweloper przy użyciu WF3 chce upewnij się, że przepływ pracy będzie nadal występował w pewnych punktach, albo muszą zmienić definicję przepływu pracy lub naliczana jest opłata za zwalniania i ponownego ładowania wystąpienia przepływu pracy.  Nowa funkcja WF4 sprawia, że można utrwalić bez rozładowywania: <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>.  Ta funkcja umożliwia wystąpienie przepływu pracy utrwalone w stanie bezczynności, ale pozostanie w pamięci, dopóki <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> osiągnięty jest próg lub wykonanie zostanie wznowione.

 Należy pamiętać, że dostawcy stanów trwałych programu SQL WF4 wykonuje więcej pracy w warstwie bazy danych.  Bazy danych SQL może stać się wąskim gardłem tak ważne jest, aby monitorować istnieje użycie Procesora i dysku.  Należy uwzględnić następujące liczniki wydajności z SQL, bazy danych podczas testowania aplikacji przepływu pracy:

-   Dysk fizyczny\\czas odczytu z dysku %

-   Dysk fizyczny\\czas dysku (%)

-   Dysk fizyczny\\czas zapisu dysku %

-   Dysk fizyczny\\% średni Długość kolejki dysku

-   Dysk Fizyczny\średni Długość kolejki odczytu dysku

-   Dysk Fizyczny\średni Długość kolejki zapisu dysku

-   Długość kolejki dysku PhysicalDisk\Current

-   Informacje o procesorze\\czas procesora (%)

-   Czas oczekiwania zatrzaśnięcia SQLServer:Latches\Average (ms)

-   W tym czasie czeka SQLServer:Latches\Latch na sekundę

### <a name="tracking"></a>Śledzenie
 Śledzenie przepływu pracy może służyć do śledzenia postępu dla przepływu pracy.  Informacje, które są objęte zdarzeń śledzenia jest ustalany profilu śledzenia.  Bardziej złożone staje się profilu śledzenia śledzenia bardziej kosztowne.

 WF3 dostarczanych z usługą SQL na podstawie śledzenia.  Ta usługa może pracować w trybie wsadowej i -przetwarzanej.  W trybie-przetwarzanej zdarzenia śledzenia są zapisywane bezpośrednio w bazie danych.  W trybie wsadowej zdarzenia śledzenia są zbierane w tej samej partii jako stan wystąpienia przepływu pracy.  Tryb wsadowej ma lepszą wydajność dla najszerszą gamę projekty przepływu pracy.  Jednak przetwarzanie wsadowe może mieć negatywny wpływ na wydajność, jeśli wiele działań wykonywania przepływu pracy bez utrwalanie i te działania są śledzone.  To sytuacja często może mieć miejsce w pętli, a najlepszym sposobem uniknięcia tego scenariusza jest zaprojektowanie dużą pętli, aby zawierać punkt stanu trwałego.  Wprowadzenie do punktu stanu trwałego w pętli może negatywnie wpłynąć na również pod względem wydajności, więc jest ważne, aby zmierzyć koszty każdego z nich i stworzyć równowagi.

 WF4 nie jest dostarczany z usługi śledzenia SQL.  Rejestrowanie śledzenia informacji do usługi SQL database można być lepszego obsługiwane z serwera aplikacji zamiast wbudowane w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. W związku z tym śledzenie SQL jest teraz obsługiwane przez rozwiązania AppFabric.  Dostawcy śledzenia poza pole w WF4 opiera się na śledzenie zdarzeń dla Windows (ETW).

 ETW to system zdarzeń w poziomie jądra i niskim opóźnieniu wbudowane w Windows.  Używa modelu dostawcy i odbiorcy, który sprawia, że można tylko pociągnąć za sobą spadek do śledzenia zdarzeń po faktycznie konsumenta.  Oprócz zdarzeń jądra, np. procesora, dysku, pamięci i użycie sieci wiele aplikacji oraz korzystać z funkcji ETW.  Zdarzenia ETW są bardziej wydajne niż liczników wydajności, zdarzenia, które można dostosować do aplikacji.  Zdarzenie może zawierać tekst, takie jak identyfikator przepływu pracy lub komunikat informacyjny.  Ponadto zdarzenia są skategoryzowane przy użyciu masek bitowych, tak aby używania tylko podzbiór zdarzeń mają mniej wpływ na wydajność, niż przechwytywania wszystkich zdarzeń.

 Podejście za pomocą funkcji ETW śledzenia zamiast SQL korzyści:

-   Kolekcja zdarzenia śledzenia mogą być oddzielone do innego procesu.  Daje to większą elastyczność w jaki sposób są rejestrowane zdarzenia.

-   Zdarzenia śledzenia ETW łatwo są połączone z zdarzenia WCF ETW lub innych dostawców ETW, takiego jak dostawca programu SQL Server lub jądra.

-   Autorzy przepływu pracy nie trzeba zmienić przepływ pracy do lepszą współpracę z implementacją określonego śledzenia, takie jak Usługa śledzenia WF3 SQL trybie wsadowym.

-   Administrator może włączyć śledzenie lub wyłączyć bez odtwarzania procesu hosta.

 Korzyści w zakresie wydajności do śledzenia zdarzeń systemu Windows są dostarczane z systemem zwrotu.  Zdarzenia ETW mogą zostać utracone, jeśli system jest w dużym natężeniu zasobu.  Przetwarzanie zdarzeń nie jest przeznaczona do blokowania normalnego działania programu i dlatego nie ma żadnej gwarancji, wszystkie zdarzenia ETW zostanie emisji do subskrybentów.  To sprawia, że śledzenie zdarzeń systemu Windows idealne narzędzie do monitorowania kondycji, ale nie nadaje się do inspekcji.

 Gdy WF4 nie ma dostawcy śledzenia bazy danych SQL, wykonuje AppFabric.  Podejście śledzenia SQL w AppFabric jest do subskrybowania zdarzenia ETW za pomocą usługi Windows, która partii zdarzeń i zapisuje je do tabeli SQL przeznaczony do wstawienia szybkie.  Jako osobne zadanie wstrzymanie danych z tej tabeli i reforms go do tabel, które mogą być wyświetlane na pulpicie nawigacyjnym rozwiązania AppFabric raportowania.  Oznacza to, że partii śledzenia zdarzeń odbywa się niezależnie od przepływu pracy, pochodzi z i w związku z tym nie trzeba czekać na punkcie trwałości przed rejestrowane.

 Zdarzenia ETW mogą być rejestrowane za pomocą narzędzi takich jak logman lub narzędzia xperf.  Można wyświetlić za pomocą narzędzia, takiego jak xperfview lub przekonwertowane na bardziej czytelnym formacie, takich jak XML, za pomocą tracerpt compact pliku ETL.  W WF3 jedyną opcją, w celu uzyskania śledzenia zdarzeń, bez bazy danych SQL jest tworzenie niestandardowe śledzenia usługi. Aby uzyskać więcej informacji na temat funkcji ETW, zobacz [usługi WCF i zdarzenia śledzenia dla Windows](../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) i [Event Tracing for Windows](https://msdn.microsoft.com/library/ff190903.aspx\)).

 Włączanie śledzenia przepływu pracy wpływają na wydajność w różnym stopniu.  Test porównawczy poniżej używa narzędzia logman do wykorzystania funkcji ETW śledzenia zdarzeń i zarejestruj je w pliku ETL.  Koszt SQL śledzenia w AppFabric nie znajduje się w zakresie tego artykułu.  Profil śledzenia podstawowego, używany również w AppFabric, jest wyświetlany w tym testów porównawczych.  Również obejmuje koszt śledzenia tylko zdarzeń monitorowania kondycji.  Zdarzenia te są przydatne do rozwiązywania problemów i określania średniej przepływności systemu.

### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

### <a name="test-results"></a>Wyniki tekstu
 ![Przepływ pracy, śledzenie kosztów](../../../docs/framework/windows-workflow-foundation/media/workflowtracingcost.gif "WorkflowTracingCost")

 Monitorowanie kondycji ma około 3% wpływ na przepustowość.  Koszt profilu podstawowego jest około 8%.

## <a name="interop"></a>Usługa międzyoperacyjna
 WF4 jest niemal ukończone nadpisania [!INCLUDE[wf1](../../../includes/wf1-md.md)] i w związku z tym WF3 przepływów pracy i działań nie są bezpośrednio zgodne z WF4.  Wielu klientów, które wcześniej przyjęte Windows Workflow Foundation mają definicji przepływu pracy wewnętrznymi lub innych firm i niestandardowych działań dla WF3.  Jednym ze sposobów, aby ułatwić przejście na WF4 jest użyć międzyoperacyjny działania, które można wykonać działania WF3 z WF4 przepływu pracy.  Zalecane jest, <xref:System.Activities.Statements.Interop> działania można używać tylko gdy jest to konieczne. Aby uzyskać więcej informacji na temat migracji do WF4 zapoznaj się z [wskazówek dotyczących migracji WF4](https://go.microsoft.com/fwlink/?LinkID=153313).

### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")

### <a name="test-results"></a>Wyniki tekstu
 W poniższej tabeli przedstawiono wyniki działania przepływu pracy zawierający pięciu działań w Sekwencje w różnych konfiguracjach.

|Test|Przepływność (przepływy pracy/s)|
|----------|-----------------------------------|
|Sekwencja WF3 w środowisku uruchomieniowym WF3|1,576|
|Sekwencja WF3 w środowisku uruchomieniowym WF4 za pomocą międzyoperacyjności|2,745|
|Sekwencja WF4|153,582|

 Zwiększenie wydajności istotne za pomocą międzyoperacyjności za pośrednictwem prostej WF3 nie istnieje.  Jednak gdy porównywana WF4 działań, zwiększenie jest niewielki.

## <a name="summary"></a>Podsumowanie
 Dużych inwestycji w wydajności WF4 zapłaciły w wielu obszarach niezwykle istotne.  Wydajność składników określonego przepływu pracy jest w niektórych przypadkach kilkaset razy szybszy w WF4 w porównaniu do WF3 ze względu na bardziej oszczędny [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowiska uruchomieniowego.  Opóźnienie liczb są również znacznie lepszą.  To oznacza spadek wydajności przy użyciu [!INCLUDE[wf1](../../../includes/wf1-md.md)] w przeciwieństwie do programowania ręcznego aranżacji WCF jest bardzo mały, biorąc pod uwagę oraz dodatkowe zalety korzystania z usług [!INCLUDE[wf1](../../../includes/wf1-md.md)].  Trwałość wydajności został zwiększony współczynnik 3.0 2.5.  Monitorowanie kondycji za pomocą przepływu pracy śledzenia teraz ma niewielkim zapasem.  Kompleksowy zestaw przewodniki dotyczące migracji są dostępne dla osób, które rozważają przenoszenie z WF3 do WF4.  Wszystkie te powinny być WF4 atrakcyjną opcję do tworzenia złożonych aplikacji.

## <a name="acknowledgements"></a>Potwierdzanie
 Wiele dzięki poniższym współautorów i osób dokonujących przeglądu dla wysiłków:

-   Leon Welicki, firma Microsoft Corporation

-   Ryszard Kwiecinski, firma Microsoft Corporation

-   Emil Velinov, firma Microsoft Corporation

-   Nate Talbert, firma Microsoft Corporation

-   Robert Schmidt, firma Microsoft Corporation

-   Stefan Batres, firma Microsoft Corporation
