---
title: Wydajność programu Windows Workflow Foundation 4
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: c656d1e23c7314cfd7b772faef842296d03e4af1
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70989580"
---
# <a name="windows-workflow-foundation-4-performance"></a>Wydajność programu Windows Workflow Foundation 4

 Firma [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] Microsoft oferuje poważną wersję Windows Workflow Foundation (WF) z dużymi inwestycjami w wydajność.  Ta nowa poprawka wprowadza istotne zmiany projektowe z poprzednich wersji programu [!INCLUDE[wf1](../../../includes/wf1-md.md)] , które zostały dostarczone w ramach .NET Framework 3,0 [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]i. Został on jeszcze zaprojektowany z myślą o rozbudowaniu modelu programowania, środowiska uruchomieniowego i narzędzi, aby znacznie poprawić wydajność i użyteczność. W tym temacie przedstawiono ważne cechy wydajności tych poprawek i porównuje je z poprzednimi wersjami.

 Wydajność poszczególnych składników przepływu pracy zwiększyła się o kolejność wielkości między WF3 i WF4.  Spowoduje to pozostawienie przerwy między kodowanymi ręcznie usługami Windows Communication Foundation (WCF) i usługi przepływu pracy WCF, aby były dość małe.  Opóźnienie przepływu pracy zostało znacznie zmniejszone w WF4.  Wydajność trwałości wzrosła przez współczynnik 2,5-3,0.  Monitorowanie kondycji przy użyciu śledzenia przepływu pracy ma znacznie mniej obciążenia.  Są to przydatne powody do migracji lub przyjęcia WF4 w aplikacjach.

## <a name="terminology"></a>Terminologia
 Wersja [!INCLUDE[wf1](../../../includes/wf1-md.md)] wprowadzona w programie [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] będzie określana jako WF4 w pozostałej części tego tematu.  [!INCLUDE[wf1](../../../includes/wf1-md.md)]wprowadzono w programie .NET 3,0 i wprowadzono kilka drobnych poprawek [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] w programie SP1. [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Wersja programu Workflow Foundation będzie określana jako WF3 w pozostałej części tego tematu. WF3 jest wysyłana [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] obok WF4. Aby uzyskać więcej informacji na temat migrowania artefaktów WF3 do WF4, zobacz: [Przewodnik migracji Windows Workflow Foundation 4](https://go.microsoft.com/fwlink/?LinkID=153313)

 Windows Communication Foundation (WCF) to ujednolicony model programowania firmy Microsoft służący do tworzenia aplikacji zorientowanych na usługę. Najpierw została wprowadzona jako część programu .NET 3,0 wraz z WF3 i teraz jest jednym z najważniejszych składników .NET Framework.

 Windows Server AppFabric to zestaw zintegrowanych technologii, które ułatwiają tworzenie, skalowanie i zarządzanie aplikacjami sieci Web i złożonymi, które działają w usługach IIS. Zapewnia narzędzia do monitorowania usług i przepływów pracy oraz zarządzania nimi. Aby uzyskać więcej informacji, zobacz [Windows Server AppFabric 1,0](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)).

## <a name="goals"></a>Cele
 Celem tego tematu jest przedstawienie charakterystyki wydajności WF4 z danymi mierzonymi dla różnych scenariuszy. Zawiera również szczegółowe porównania między WF4 i WF3, a tym samym przedstawia doskonałe ulepszenia, które zostały wprowadzone w tej nowej wersji. Scenariusze i dane przedstawione w tym artykule określają bazowy koszt różnych aspektów WF4 i WF3. Te dane są przydatne w zrozumieniu charakterystyki wydajności WF4 i mogą być przydatne w planowaniu migracji z WF3 do WF4 lub przy użyciu WF4 podczas opracowywania aplikacji. Należy jednak zadbać o to, aby pochodziły z danych przedstawionych w tym artykule. Wydajność aplikacji złożonego przepływu pracy jest wysoce zależna od implementacji przepływu pracy i sposobu integrowania różnych składników. Jeden musi mierzyć każdą aplikację, aby określić charakterystykę wydajności tej aplikacji.

## <a name="overview-of-wf4-performance-enhancements"></a>Omówienie ulepszeń wydajności WF4
 WF4 został starannie zaprojektowany i wdrożony z wysoką wydajnością i skalowalnością, które opisano w poniższych sekcjach.

### <a name="wf-runtime"></a>Środowisko uruchomieniowe WF
 Rdzeń [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowiska uruchomieniowego to asynchroniczny harmonogram, który umożliwia wykonywanie działań w przepływie pracy. Zapewnia wydajne, przewidywalne środowisko wykonawcze dla działań. Środowisko zawiera dobrze zdefiniowaną umowę na potrzeby wykonywania, kontynuacji, uzupełniania, anulowania, wyjątków i prognozowanego modelu wątkowości.

 W porównaniu do WF3 środowisko uruchomieniowe WF4 ma wydajniejszy harmonogram. Wykorzystuje tę samą pulę wątków we/wy, która jest używana na potrzeby WCF, co jest bardzo wydajne przy wykonywaniu wsadowych elementów roboczych. Kolejka harmonogramu wewnętrznego elementu pracy jest zoptymalizowana pod kątem większości typowych wzorców użytkowania. Środowisko uruchomieniowe WF4 zarządza również Stanami wykonywania w bardzo lekkim stopniu z minimalną logiką obsługi zdarzeń i synchronizacji, podczas gdy WF3 zależy od dużej ilości rejestracji i wywołań zdarzeń w celu przeprowadzenia złożonej synchronizacji w celu przejścia stanu.

### <a name="data-storage-and-flow"></a>Magazyn danych i przepływ
 W WF3 dane skojarzone z działaniem są modelowane za pomocą właściwości zależności implementowanych przez typ <xref:System.Windows.DependencyProperty>. Wzorzec właściwości zależności został wprowadzony w Windows Presentation Foundation (WPF). Ogólnie rzecz biorąc, ten wzorzec jest bardzo elastyczny do obsługi prostego powiązania danych i innych funkcji interfejsu użytkownika. Jednak wzorzec wymaga, aby właściwości były zdefiniowane jako pola statyczne w definicji przepływu pracy. Za każdym razem, gdy środowiskouruchomienioweustawialubpobierawartościwłaściwości,obejmujesilnieważonąlogikęwyszukiwania.[!INCLUDE[wf1](../../../includes/wf1-md.md)]

 WF4 używa logiki określania zakresu danych, aby znacznie poprawić sposób obsługi danych w przepływie pracy. Oddzieli dane przechowywane w działaniu z danych, które przepływają między granicami działania przy użyciu dwóch różnych koncepcji: zmiennych i argumentów. Przy użyciu jasnego zakresu hierarchicznego dla zmiennych i argumentów "in/out/InOut" złożoność użycia danych dla działań jest znacznie ograniczona i okres istnienia danych jest również automatycznie objęty zakresem. Działania mają dobrze zdefiniowany podpis opisany przez jego argumenty. Po prostu Inspekcja aktywności można określić, jakie dane mają być odbierane, oraz jakie dane zostaną przez niego utworzone w wyniku jego wykonania.

 W działaniach WF3 zostały zainicjowane podczas tworzenia przepływu pracy. W działaniach WF 4 są inicjowane tylko wtedy, gdy wykonywane są odpowiednie działania. Dzięki temu można uprościć cykl życia aktywności bez wykonywania operacji inicjacji/odinicjowania, gdy zostanie utworzone nowe wystąpienie przepływu pracy, co spowodowało zwiększenie wydajności

### <a name="control-flow"></a>Przepływ sterowania
 Podobnie jak w przypadku dowolnego języka programowania [!INCLUDE[wf1](../../../includes/wf1-md.md)] , zapewnia obsługę przepływów sterowania dla definicji przepływu pracy przez wprowadzenie zestawu działań przepływu sterowania dla sekwencjonowania, pętli, rozgałęzień i innych wzorców. W WF3, gdy konieczne jest ponowne wykonanie tego samego działania, tworzony jest nowy <xref:System.Workflow.ComponentModel.ActivityExecutionContext> element, a działanie jest klonowane przy użyciu dużej ilości logiki serializacji i deserializacji <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>na podstawie. Zwykle wydajność dla przebiegów kontroli iteracyjnej jest znacznie wolniejsza niż wykonywanie sekwencji działań.

 WF4 obsługuje to zupełnie inaczej. Przyjmuje szablon działania, tworzy nowy obiekt ActivityInstance i dodaje go do kolejki harmonogramu. Ten cały proces obejmuje tylko jawne Tworzenie obiektów i jest bardzo lekki.

### <a name="asynchronous-programming"></a>Programowanie asynchroniczne
 Aplikacje mają zwykle lepszą wydajność i skalowalność dzięki programowaniu asynchronicznym na długotrwałe operacje blokowania, takie jak operacje we/wy lub rozproszone procesy obliczeniowe. WF4 zapewnia obsługę asynchroniczną za pomocą podstawowych <xref:System.Activities.AsyncCodeActivity>typów <xref:System.Activities.AsyncCodeActivity%601>działań. Środowisko uruchomieniowe natywnie rozumie działania asynchroniczne i w związku z tym może automatycznie umieścić wystąpienie w strefie no-utrwalania, gdy Praca asynchroniczna jest zaległa. Działania niestandardowe mogą pochodzić od tych typów w celu wykonywania operacji asynchronicznych bez przytrzymywania wątku harmonogramu przepływu pracy i blokowania działań, które mogą być uruchamiane równolegle.

### <a name="messaging"></a>Obsługa komunikatów
 Początkowo WF3 bardzo ograniczoną obsługę komunikatów przez zewnętrzne zdarzenia lub wywołania usług sieci Web. W programie .NET 3,5 przepływy pracy mogą być implementowane jako klienci WCF lub udostępniane jako <xref:System.Workflow.Activities.SendActivity> usługi <xref:System.Workflow.Activities.ReceiveActivity>WCF za poorednictwem systemów i. W WF4 koncepcji programowania komunikatów opartych na przepływach pracy został jeszcze bardziej wzmocniony przez ścisłą integrację logiki obsługi komunikatów WCF z WF.

 Potok przetwarzania ujednoliconych komunikatów zapewniany w programie WCF w programie .NET 4 pomaga WF4 usługom w znacznie lepszą wydajność i skalowalność niż WF3. WF4 zapewnia także bogatszą obsługę programowania komunikatów, która może modelować złożone wzorce wymiany komunikatów (MEPs). Deweloperzy mogą korzystać z umów usług z systemem, aby w łatwy sposób programistyczny lub nieokreślony z nieokreślonymi typami umów uzyskać lepszą wydajność bez płacenia kosztów serializacji. Obsługa buforowania kanału po stronie klienta za pośrednictwem <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy w WF4 ułatwia deweloperom tworzenie szybkich aplikacji z minimalnym nakładem pracy. Aby uzyskać więcej informacji, zobacz [Zmienianie poziomów udostępniania pamięci podręcznej dla działań wysyłania](../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).

### <a name="declarative-programming"></a>Programowanie deklaracyjne
 WF4 zapewnia czysty i prosty, deklaracyjne środowisko programistyczne do modelowania procesów i usług firmy. Model programowania obsługuje w pełni deklaratywne składowe działań bez kodu, co znacznie upraszcza tworzenie przepływu pracy. W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)]systemie deklaracyjne środowisko programistyczne oparte na języku XAML zostało ujednolicone w jednym zestawie System. XAML. dll do obsługi programów WPF i WF.

 W WF4, język XAML zapewnia prawdziwie deklaracyjne środowisko i umożliwia zdefiniowanie całej definicji przepływu pracy w znaczniku XML, odwołujące się do działań i typów utworzonych przy użyciu platformy .NET. Było to trudne do wykonania w WF3 z formatem XOML, bez uwzględniania niestandardowej logiki związanej z kodem. Nowy stos XAML w programie .NET 4 ma znacznie lepszą wydajność podczas serializowania/deserializacji artefaktów przepływu pracy i sprawia, że deklaratywne programowanie jest bardziej atrakcyjne i trwałe.

### <a name="workflow-designer"></a>Projektant przepływów pracy
 W pełni deklaracyjne wsparcie programistyczne dla WF4 jawnie nakłada wyższe wymagania dotyczące wydajności czasu projektowania dla dużych przepływów pracy. Projektant przepływu pracy w programie WF4 ma znacznie lepszą skalowalność dla dużych przepływów pracy niż w przypadku WF3. Dzięki obsłudze wirtualizacji interfejsu użytkownika Projektant może łatwo ładować duże przepływy pracy 1000 działań w ciągu kilku sekund, podczas gdy niemal niemożliwe jest załadowanie przepływu pracy kilku setek działań za pomocą projektanta WF3.

## <a name="component-level-performance-comparisons"></a>Porównania wydajności na poziomie składników
 Ta sekcja zawiera dane dotyczące bezpośredniego porównania między poszczególnymi działaniami w przepływach pracy WF3 i WF4.  Kluczowe obszary, takie jak trwałość, mają bardziej głęboki wpływ na wydajność niż poszczególne składniki działania.  Udoskonalenia wydajności w poszczególnych składnikach WF4 są ważne, ponieważ składniki są teraz wystarczająco szybkie, aby można je było porównać z logiką aranżacji.  Przykład, który został omówiony w następnej sekcji: "Scenariusz tworzenia usług".

### <a name="environment-setup"></a>Konfiguracja środowiska
 ![Konfiguracja środowiska dla pomiaru wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

 Powyższy rysunek przedstawia konfigurację komputera używaną do pomiaru wydajności na poziomie składnika. Jeden serwer i pięć klientów połączonych za pośrednictwem jednego interfejsu sieciowego Ethernet 1 GB/s. W celu ułatwienia pomiarów serwer jest skonfigurowany do korzystania z jednego rdzenia serwera dwuprocesowego/Quad-Core z systemem Windows Server 2008 x86. Użycie procesora CPU systemu jest utrzymywane o niemal 100%.

### <a name="test-details"></a>Szczegóły testu
 WF3 <xref:System.Workflow.Activities.CodeActivity> jest prawdopodobnie najprostszym działaniem, które może być używane w przepływie pracy WF3.  Działanie wywołuje metodę w kodzie, za pomocą którego programista przepływu pracy może umieścić kod niestandardowy.  W programie WF4 nie ma bezpośredniego analogu do WF3 <xref:System.Workflow.Activities.CodeActivity> , który zapewnia te same funkcje.  Należy zauważyć, że istnieje <xref:System.Activities.CodeActivity> Klasa bazowa w WF4, która nie jest powiązana z <xref:System.Workflow.Activities.CodeActivity>WF3.  Autorzy przepływu pracy zachęca się do tworzenia działań niestandardowych i tworzenia przepływów pracy tylko w języku XAML.  W poniższych testach użyto wywoływanego `Comment` działania zamiast pustego <xref:System.Workflow.Activities.CodeActivity> w przepływie pracy WF4.  Kod w `Comment` działaniu jest następujący:

```csharp
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
 Ten test używa przepływu pracy sekwencji bez działań podrzędnych.

### <a name="single-activity"></a>Pojedyncze działanie
 Przepływ pracy jest przepływem pracy sekwencji zawierającym jedno działanie podrzędne.  Działanie to <xref:System.Workflow.Activities.CodeActivity> bez kodu w przypadku WF3 `Comment` i działania w przypadku WF4.

### <a name="while-with-1000-iterations"></a>While z 1000 iteracji
 Przepływ pracy sekwencji zawiera jedno <xref:System.Activities.Statements.While> działanie z jednym działaniem podrzędnym w pętli, które nie wykonuje żadnej pracy.

### <a name="replicator-compared-to-parallelforeach"></a>Replikator w porównaniu do ParallelForEach
 <xref:System.Workflow.Activities.ReplicatorActivity>w programie WF3 są tryby wykonywania sekwencyjnego i równoległego.  W trybie sekwencyjnym wydajność działania jest podobna do <xref:System.Workflow.Activities.WhileActivity>.  <xref:System.Workflow.Activities.ReplicatorActivity> Jest najbardziej przydatny do wykonywania równoległego.  Wartość WF4 jest <xref:System.Activities.Statements.ParallelForEach%601> analogiczna dla tego działania.

 Na poniższym diagramie przedstawiono przepływy pracy używane do tego testu. Przepływ pracy WF3 jest po lewej stronie, a przepływ pracy WF4 znajduje się po prawej stronie.

 ![WF3 Replikator i WF4 ParallelForEach](./media/performance/replicator-parallel-wf3-wf4.gif)

### <a name="sequential-workflow-with-five-activities"></a>Sekwencyjny przepływ pracy z pięcioma działaniami
 Ten test ma na celu pokazanie efektu wykonywania kilku działań w sekwencji.  Sekwencja obejmuje pięć działań.

### <a name="transaction-scope"></a>Zakres transakcji
 Test zakresu transakcji różni się od innych testów w niewielkim stopniu w przypadku, gdy nowe wystąpienie przepływu pracy nie jest tworzone dla każdej iteracji.  Zamiast tego przepływ pracy jest strukturalny przy użyciu pętli while zawierającej <xref:System.Activities.Statements.TransactionScope> działanie zawierające pojedyncze działanie, które nie działa.  Każdy przebieg wsadu 50 iteracji przez pętlę while jest liczony jako jedna operacja.

### <a name="compensation"></a>Kompensacja
 Przepływ pracy WF3 ma pojedyncze działanie kompensowane o nazwie `WorkScope`.  Działanie po prostu implementuje <xref:System.Workflow.ComponentModel.ICompensatableActivity> interfejs:

```csharp
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

 Procedura obsługi błędów odwołuje `WorkScope` się do działania. Przepływ pracy WF4 jest równie uproszczony.  <xref:System.Activities.Statements.CompensableActivity> Ma program obsługi treści i kompensacji.  W sekwencji są dalej wyrównane kompensacje.  Działanie treści i działania programu obsługi kompensacji są pustymi implementacjami:

```csharp
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

Na poniższym diagramie przedstawiono podstawowy przepływ pracy związane z wynagrodzeniem. Przepływ pracy WF3 jest po lewej stronie, a przepływ pracy WF4 znajduje się po prawej stronie.

![Podstawowe przepływy pracy dotyczące WF3 i WF4](./media/performance/basic-compensation-workflows-wf3-wf4.gif)

### <a name="performance-test-results"></a>Wyniki testów wydajności

 ![Tabela przedstawiająca dane wyników testu wydajnościowego](./media/performance/performance-test-data.gif)

 ![Wykres kolumnowy porównujący dane testu wydajności WF3 i WF4](./media/performance/performance-test-chart.gif)

 Wszystkie testy są mierzone w przepływach pracy na sekundę z wyjątkiem testu zakresu transakcji.  Jak widać powyżej, [!INCLUDE[wf1](../../../includes/wf1-md.md)] wydajność środowiska uruchomieniowego została ulepszona w całej tablicy, szczególnie w obszarach wymagających wielokrotnych wykonań tego samego działania, takich jak Pętla WHILE.

## <a name="service-composition-scenario"></a>Scenariusz tworzenia usługi
 Jak pokazano w poprzedniej sekcji "porównania wydajności na poziomie składników", nastąpił znaczny spadek obciążenia między WF3 i WF4.  Usługi przepływu pracy WCF mogą teraz prawie odpowiadać wydajności kodowanym ręcznie usługom WCF, ale nadal mają wszystkie zalety [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowiska uruchomieniowego.  Ten scenariusz testu porównuje usługę WCF z usługą przepływu pracy WCF w WF4.

### <a name="online-store-service"></a>Usługa sklepu online
 Jedną z zalet Windows Workflow Foundation jest możliwość tworzenia procesów przy użyciu kilku usług.  W tym przykładzie istnieje usługa sklepu online, która organizuje dwa wywołania usługi, aby zakupić zamówienie.  Pierwszym krokiem jest sprawdzenie kolejności przy użyciu usługi Order Validate Service.  Drugim krokiem jest wypełnienie zamówienia przy użyciu usługi magazynu.

 Dwa usługi zaplecza, zamawianie walidacji usługi i usługi magazynu, pozostają takie same dla obu testów.  Częścią, która zmienia się, jest usługa sklepu online, która wykonuje aranżację.  W jednym przypadku usługa jest zapisana ręcznie jako usługa WCF.  W przypadku innych przypadków usługa jest zapisywana jako usługa przepływu pracy WCF w WF4. [!INCLUDE[wf1](../../../includes/wf1-md.md)]dla tego testu są wyłączone określone funkcje, takie jak śledzenie i trwałość.

### <a name="environment"></a>Środowisko
![Konfiguracja środowiska dla pomiaru wydajności](./media/performance/performance-test-environment.gif)

 Żądania klientów są wysyłane do usługi sklepu online za pośrednictwem protokołu HTTP z wielu komputerów.  Pojedynczy komputer obsługuje wszystkie trzy usługi.  Warstwa transportu między usługą sklepu online a usługami zaplecza to TCP lub HTTP.  Pomiar operacji na sekundę jest oparty na liczbie ukończonych `PurchaseOrder` wywołań do usługi sklepu online.  Buforowanie kanałów jest nową funkcją dostępną w WF4.  W części WCF tej puli kanałów testowych nie jest dostarczany poza Box, dlatego w usłudze sklepu online użyto rozmieszczonej ręcznie implementacji techniki prostego buforowania.

### <a name="performance"></a>Wydajność
![Wykres kolumnowy przedstawiający wydajność usługi sklepu online](./media/performance/online-store-performance-graph.gif)

 Połączenie z usługami TCP zaplecza bez buforowania [!INCLUDE[wf1](../../../includes/wf1-md.md)] kanałów usługa ma wpływ na przepływność na 17,2%.  W przypadku używania puli kanałów kara wynosi około 23,8%.  W przypadku protokołu HTTP wpływ jest znacznie mniejszy: 4,3% bez pul i 8,1% z buforowaniem.  Należy również pamiętać, że w przypadku korzystania z protokołu HTTP buforowanie kanałów zapewnia bardzo mało korzyści.

 Chociaż w tym teście WF4 środowisko uruchomieniowe w porównaniu z zaręczną usługą WCF, można go traktować jako najgorszy scenariusz.  Dwa usługi zaplecza w tym teście wykonują bardzo mało pracy.  W codziennym scenariuszu te usługi będą wykonywać bardziej kosztowne operacje, takie jak wywołania bazy danych, co zmniejsza wpływ na wydajność warstwy transportowej.  Dzięki temu można korzystać z zalet funkcji dostępnych w programie WF4, co sprawia, że usługa Workflow Foundation umożliwia tworzenie usług aranżacji.

## <a name="key-performance-considerations"></a>Kluczowe zagadnienia dotyczące wydajności
 Obszary funkcji w tej sekcji, z wyjątkiem międzyoperacyjności, zostały znacząco zmienione między WF3 i WF4.  Ma to wpływ na projekt aplikacji przepływu pracy, a także wydajność.

#### <a name="workflow-activation-latency"></a>Opóźnienie aktywacji przepływu pracy
 W aplikacji usługi przepływu pracy WCF czas oczekiwania na uruchomienie nowego przepływu pracy lub załadowanie istniejącego przepływu pracy jest istotny, ponieważ może być blokowany.  Ten przypadek testowy mierzy WF3 hosta XOML dla hosta WF4 XAMLX w typowym scenariuszu.

##### <a name="environment-setup"></a>Konfiguracja środowiska
 ![Konfiguracja środowiska dla testów opóźnienia i przepływności](./media/performance/latency-throughput-environment-setup.gif)

##### <a name="test-setup"></a>Konfiguracja testu
 W tym scenariuszu komputer kliencki kontaktuje się z usługą przepływu pracy WCF przy użyciu korelacji opartej na kontekście.  Korelacja kontekstu wymaga specjalnego powiązania kontekstu i używa nagłówka kontekstu lub pliku cookie do powiązania komunikatów z prawidłowym wystąpieniem przepływu pracy.  Ma korzyść wydajności w przypadku, gdy identyfikator korelacji znajduje się w nagłówku komunikatu, dlatego nie trzeba analizować treści komunikatu.

 Usługa utworzy nowy przepływ pracy z żądaniem i wyśle natychmiastową odpowiedź, aby pomiar opóźnienia nie obejmował czasu, w którym przepływ pracy został uruchomiony.  Przepływ pracy WF3 jest elementem XOML z kodem, a przepływ pracy WF4 jest całkowicie XAML.  Przepływ pracy WF4 wygląda następująco:

 ![Przepływ pracy zakresu korelacji WF4](./media/performance/wf4-correlationscope-workflow.gif)

 <xref:System.ServiceModel.Activities.Receive> Działanie tworzy wystąpienie przepływu pracy.  Wartość przeniesiona w odebranej wiadomości jest echo w komunikacie odpowiedzi.  Sekwencja po odpowiedzi zawiera resztę przepływu pracy.  W powyższym przypadku wyświetlane jest tylko jedno działanie komentarza.  Liczba działań związanych z komentarzem została zmieniona w celu symulowania złożoności przepływu pracy.  Działanie comment jest równoznaczne z WF3 <xref:System.Workflow.Activities.CodeActivity> , który nie wykonuje żadnych działań. Aby uzyskać więcej informacji na temat działania komentarza, zobacz sekcję "porównanie wydajności na poziomie składników" wcześniej w tym artykule.

##### <a name="test-results"></a>Wyniki tekstu

 Oczekiwanie na zimne i ciepłe usługi przepływu pracy WCF:

 ![Wykres kolumnowy przedstawiający czas oczekiwania na zimne i ciepłe usługi przepływu pracy WCF przy użyciu WF3 i WF4](./media/performance/latency-results-graph.gif)

 Na poprzednim wykresie zimny odnosi się do przypadku, gdy nie istnieje istniejący <xref:System.ServiceModel.WorkflowServiceHost> dla danego przepływu pracy.  Innymi słowy, podczas gdy przepływ pracy jest używany po raz pierwszy, a plik XOML lub XAML musi zostać skompilowany.  Opóźnienie rozgrzane to czas, aby utworzyć nowe wystąpienie przepływu pracy, gdy typ przepływu pracy został już skompilowany.  Złożoność przepływu pracy powoduje bardzo małą różnicę w przypadku WF4, ale ma liniowy postęp w przypadku WF3.

#### <a name="correlation-throughput"></a>Przepływność korelacji
 WF4 wprowadza nową funkcję korelacji opartą na zawartości.  WF3 udostępnia tylko korelację opartą na kontekście.  Korelację opartą na kontekście można wykonać tylko dla określonych powiązań kanałów WCF.  Identyfikator przepływu pracy jest wstawiany do nagłówka komunikatu podczas korzystania z tych powiązań.  Środowisko uruchomieniowe WF3 może zidentyfikować tylko przepływ pracy na podstawie jego identyfikatora.  W przypadku korelacji opartej na zawartości Autor przepływu pracy może utworzyć klucz korelacji z odpowiedniego fragmentu danych, takiego jak numer konta lub identyfikator klienta.

 Korelacja oparta na kontekście ma zalety wydajności w przypadku, gdy klucz korelacji znajduje się w nagłówku komunikatu.  Klucz można odczytać z komunikatu bez deserializacji/kopiowania komunikatów.  W korelacji opartej na zawartości klucz korelacji jest przechowywany w treści komunikatu.  Wyrażenie XPath służy do lokalizowania klucza.  Koszt tego dodatkowego przetwarzania zależy od rozmiaru wiadomości, głębokości klucza w treści i liczby kluczy...  Ten test porównuje korelację opartą na kontekście i treści, a także pokazuje spadek wydajności podczas korzystania z wielu kluczy.

#### <a name="environment-setup"></a>Konfiguracja środowiska
![Konfiguracja środowiska dla testu wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

#### <a name="test-setup"></a>Konfiguracja testu
![Test przepływu pracy korelacji przepływności](./media/performance/correlation-throughput-workflow.gif "Konfiguracja testu przepływu pracy korelacji przepływności")

 Poprzedni przepływ pracy jest taki sam, jak użyty w sekcji [trwałość](#persistence) . W przypadku testów korelacji bez trwałości nie ma żadnego dostawcy trwałości zainstalowanego w czasie wykonywania. Korelacja występuje w dwóch miejscach: Porządkuj i CompleteOrder.

#### <a name="test-results"></a>Wyniki tekstu
![Przepływność korelacji](./media/performance/correlation-throughput-graph.gif "Wykres przepływności korelacji")

 Ten wykres przedstawia spadek wydajności w miarę zwiększania się liczby kluczy używanych w ramach korelacji opartej na zawartości.  Podobieństwo krzywej między TCP i HTTP wskazuje obciążenie związane z tymi protokołami.

#### <a name="correlation-with-persistence"></a>Korelacja z trwałością
 W przypadku utrwalonego przepływu pracy wykorzystanie procesora CPU z korelacji opartej na zawartości jest przesunięte ze środowiska uruchomieniowego przepływu pracy do bazy danych SQL.  Procedury składowane w dostawcy trwałości SQL wykonują zadania pasujące do kluczy, aby zlokalizować odpowiedni przepływ pracy.

 ![Wykres liniowy przedstawiający korelację i wyniki trwałości](./media/performance/correlation-persistence-graph.gif)

 Korelacja oparta na kontekście jest ciągle szybsza niż korelacja oparta na zawartości.  Różnica jest jednak mniej wymawiana, ponieważ trwałość ma większy wpływ na wydajność niż korelacja.

### <a name="complex-workflow-throughput"></a>Przepływność złożonych przepływów pracy
 Złożoność przepływu pracy nie jest mierzona tylko przez liczbę działań.  Działania złożone mogą zawierać wiele elementów podrzędnych i te elementy podrzędne mogą również być działaniami złożonymi.  Liczba poziomów wzrostu zagnieżdżenia, dlatego liczba działań, które mogą być obecnie w stanie wykonywania, oraz liczba zmiennych, które mogą być w stanie.  Ten test porównuje przepływność między WF3 i WF4 podczas wykonywania złożonych przepływów pracy.

### <a name="test-setup"></a>Konfiguracja testu
 Te testy zostały wykonane na komputerze z procesorem Intel Xeon X5355 @ ośmiordzeniowy 2,66 GHz, a 4 GB pamięci RAM z systemem Windows Server 2008 x64.  Kod testu jest uruchamiany w jednym procesie z jednym wątkiem na rdzeń, aby osiągnąć 100% użycia procesora CPU.

 Przepływy pracy wygenerowane dla tego testu mają dwie zmienne główne: głębokość i liczbę działań w każdej sekwencji.  Każdy poziom głębokości obejmuje aktywność równoległą, podczas gdy pętla, decyzje, przypisania i sekwencje.  W programie WF4 Designer poniżej znajduje się wykres przepływu najwyższego poziomu.  Każde działanie Flowchart jest podobne do głównego schematu blokowego.  Pomocne może być Fractal, gdy Picturing ten przepływ pracy, gdzie głębokość jest ograniczona do parametrów testu.

 Liczba działań w danym teście zależy od głębokości i liczby działań na sekwencję.  Poniższe równanie oblicza liczbę działań w teście WF4:

 ![Równanie do liczby działań obliczeniowych](./media/performance/number-activities-equation.gif)

 Liczba działań testu WF3 można obliczyć przy użyciu nieco innego równania z powodu dodatkowej sekwencji:

 ![Równanie do liczby obliczeń WF3 działań](./media/performance/wf3-number-activities-equation.gif)

 Gdzie d to głębokość, a to liczba działań na sekwencję.  Logika za te równania polega na tym, że pierwsza stała, pomnożona przez, jest liczbą sekwencji, a druga stała jest statyczną liczbą działań na bieżącym poziomie.  Każdy schemat blokowy zawiera trzy działania podrzędne schematu blokowego.  Na niższym poziomie głębokości te schematy blokowe są puste, ale na innych poziomach są to kopie głównego schematu blokowego.  W poniższej tabeli przedstawiono liczbę działań w definicji przepływu pracy każdej z odmian testowych:

 ![Tabela przedstawiająca liczbę działań użytych w każdym teście](./media/performance/workflow-variation-compare-table.gif)

 Liczba działań w definicji przepływu pracy rośnie gwałtownie z każdym poziomem głębokości.  Ale tylko jedna ścieżka na punkt decyzyjny jest wykonywana w danym wystąpieniu przepływu pracy, więc wykonywane jest tylko niewielki podzestaw rzeczywistych działań.

 ![Schemat blokowy przepływu pracy złożonej przepływności](./media/performance/complex-workflow-throughput-workflow.gif)

 Utworzono równoważny przepływ pracy dla WF3. Projektant WF3 wyświetla cały przepływ pracy w obszarze projektowania zamiast zagnieżdżania, w związku z czym jest zbyt duży do wyświetlenia w tym temacie. Poniżej przedstawiono fragment przepływu pracy.

 ![Fragment kodu schematu przepływu pracy WF3](./media/performance/wf3-workflow-snippet.gif)

 Aby wykonać zagnieżdżenie w skrajnym przypadku, inny przepływ pracy, który jest częścią tego testu, korzysta z 100 sekwencji zagnieżdżonych.  W wewnętrznej sekwencji jest pojedyncza `Comment` lub. <xref:System.Workflow.Activities.CodeActivity>

 ![Schemat blokowy sekwencji zagnieżdżonej](./media/performance/nested-sequence-workflow.gif)

 Śledzenie i trwałość nie są używane w ramach tego testu.

### <a name="test-results"></a>Wyniki tekstu
 ![Wykres kolumnowy przedstawiający wyniki wydajności przepływności](./media/performance/throughput-performance-results.gif)

 Nawet w przypadku złożonych przepływów pracy ze znaczną głębokością i dużą liczbą działań wyniki wydajności są spójne z innymi numerami przepływności przedstawionymi wcześniej w tym artykule.  WF4's przepływność jest znacznie szybsza i musi być porównana z skalą logarytmiczną.

### <a name="memory"></a>Pamięć
 Obciążenie pamięcią Windows Workflow Foundation jest mierzone w dwóch kluczowych obszarach: złożoność przepływu pracy i liczba definicji przepływu pracy.  Pomiary pamięci zostały wykonane na stacji roboczej systemu Windows 7 64-bitowego.  Istnieje wiele sposobów uzyskania pomiaru rozmiaru zestawu roboczego, takiego jak monitorowanie liczników wydajności, środowisko sondowania środowiska. zestaw roboczy lub używanie narzędzia, takiego jak VMMap dostępne z [VMMap](/sysinternals/downloads/vmmap). Kombinacja metod została użyta w celu uzyskania i sprawdzenia wyników każdego testu.

### <a name="workflow-complexity-test"></a>Test złożoności przepływu pracy
 Test złożoności przepływu pracy mierzy różnicę zestawu roboczego na podstawie złożoności przepływu pracy.  Oprócz złożonych przepływów pracy używanych w poprzedniej sekcji nowe odmiany są dodawane w celu pokrycia dwóch podstawowych przypadków: przepływu pracy pojedynczego działania i sekwencji z 1000 działaniami.  Dla tych testów przepływy pracy są inicjowane i wykonywane do ukończenia w pojedynczej pętli szeregowej przez okres jednej minuty.  Każda odmiana testowa jest uruchamiana trzy razy, a dane zarejestrowane to średnia z tych trzech przebiegów.

 Dwa nowe podstawowe testy mają przepływy pracy, które wyglądają jak te pokazane poniżej:

 ![Złożony przepływ pracy dla zarówno WF3, jak i WF4](./media/performance/complex-workflow-wf3-wf4.gif)

 W pokazanym powyżej przepływie pracy <xref:System.Workflow.Activities.CodeActivity> WF3 są używane puste działania.  W przepływie pracy WF4 `Comment` powyżej są wykorzystywane działania.  `Comment` Działanie zostało opisane w sekcji porównania wydajności na poziomie składnika wcześniej w tym artykule.

 ![Wykres kolumnowy przedstawiający złożone użycie pamięci przepływu pracy dla przepływów pracy WF3 i WF4](./media/performance/complex-memory-usage-wf3-wf4.gif)

 Jedną z oczywistych trendów, które należy zwrócić na ten Graf, jest to, że zagnieżdżanie ma stosunkowo minimalny wpływ na użycie pamięci zarówno w WF3, jak i w WF4.  Najbardziej znaczący wpływ na pamięć pochodzi z liczby działań w danym przepływie pracy.  Dane z sekwencji 1000, złożonej głębokości 5 sekwencji 5 i złożoności złożonej 7 sekwencji 1 są oczywiste, ponieważ liczba działań przejdzie do tysięcy, a wzrost wykorzystania pamięci będzie bardziej zauważalny.  W skrajnym przypadku (głębokość 7 sekwencji 1), w której znajdują się 29K działania, WF4 używa niemal 79% mniej pamięci niż WF3.

### <a name="multiple-workflow-definitions-test"></a>Test wielu definicji przepływu pracy
 Pomiar ilości pamięci na definicję przepływu pracy jest podzielony na dwa różne testy ze względu na dostępne opcje hostingu przepływów pracy w WF3 i WF4.  Testy są uruchamiane w inny sposób niż w teście złożoności przepływu pracy w przypadku wystąpienia danego przepływu pracy, który jest wykonywany tylko raz dla każdej definicji.  Wynika to z faktu, że definicja przepływu pracy i jego host pozostają w pamięci przez okres istnienia elementu AppDomain.  Podczas wyrzucania elementów bezużytecznych należy oczyścić pamięć używaną przez uruchomienie danego wystąpienia przepływu pracy.  Wskazówki dotyczące migracji WF4 zawierają bardziej szczegółowe informacje na temat opcji hostingu. Aby uzyskać więcej informacji, [Zobacz Cookbook migracji WF: Hosting](https://go.microsoft.com/fwlink/?LinkID=153313)przepływu pracy.

 Tworzenie wielu definicji przepływu pracy dla testu definicji przepływu pracy można wykonać na kilka sposobów.  Na przykład, jeden może użyć generowania kodu, aby utworzyć zestaw 1000 przepływów pracy, które są identyczne, z wyjątkiem nazwy i Zapisz każdy z tych przepływów pracy w oddzielnych plikach.  To podejście zostało wykonane dla testu obsługiwanego przez konsolę.  W WF3, <xref:System.Workflow.Runtime.WorkflowRuntime> Klasa była używana do uruchamiania definicji przepływu pracy.  WF4 może użyć <xref:System.Activities.WorkflowApplication> , aby utworzyć pojedyncze wystąpienie przepływu pracy lub bezpośrednio użyć <xref:System.Activities.WorkflowInvoker> do uruchomienia działania tak, jakby było wywołaniem metody.  <xref:System.Activities.WorkflowApplication>jest hostem pojedynczego wystąpienia przepływu pracy i ma bliższą parzystość <xref:System.Workflow.Runtime.WorkflowRuntime> funkcji, która została użyta w tym teście.

 Podczas hostowania przepływów pracy w usługach IIS można użyć <xref:System.Web.Hosting.VirtualPathProvider> programu, aby utworzyć <xref:System.ServiceModel.WorkflowServiceHost> nowy zamiast generować wszystkie pliki xamlx lub xoml.  <xref:System.Web.Hosting.VirtualPathProvider> Obsługuje przychodzące żądanie i odpowiada za pomocą "pliku wirtualnego", który można załadować z bazy danych lub, w tym przypadku, generowany na bieżąco.  W związku z tym nie trzeba tworzyć plików fizycznych 1000.

 Definicje przepływów pracy używane w teście konsoli były prostymi sekwencyjnymi przepływami pracy z pojedynczym działaniem.  Pojedyncze działanie było puste <xref:System.Workflow.Activities.CodeActivity> dla przypadku WF3 `Comment` i działania w przypadku WF4 przypadku.  Oparte na usługach IIS przepływy pracy, które zaczynają się otrzymywać po odebraniu komunikatu i kończący wysyłanie odpowiedzi:

Na poniższej ilustracji przedstawiono przepływ pracy WF3 z funkcją Receives i przepływ pracy WF4 z wzorcem żądania/odpowiedzi:

 ![Usługi przepływu pracy w WF3 i WF4](./media/performance/workflow-receive-activity.gif)

 W poniższej tabeli przedstawiono różnice w zestawie roboczym między jedną definicją przepływu pracy i definicjami 1001:

|Opcje hostingu|WF3 Delta zestawu roboczego|WF4 Delta zestawu roboczego|
|---------------------|---------------------------|---------------------------|
|Hostowane przepływy pracy aplikacji konsolowej|18 MB|9 MB|
|Hostowane usługi przepływu pracy usług IIS|446 MB|364 MB|

 Hostowanie definicji przepływu pracy w usługach IIS zużywa znacznie więcej pamięci ze <xref:System.ServiceModel.WorkflowServiceHost>względu na szczegółowe artefakty usługi WCF i logikę przetwarzania komunikatów skojarzoną z hostem.

 W przypadku hostingu konsoli w programie WF3 przepływy pracy zostały zaimplementowane w kodzie zamiast pliku XOML.  W WF4 wartość domyślna to użycie języka XAML.  KOD XAML jest przechowywany jako zasób osadzony w zestawie i kompilowany w czasie wykonywania, aby zapewnić implementację przepływu pracy.  Ten proces wiąże się z pewnym obciążeniem.  Aby zapewnić rzetelne porównanie między WF3 i WF4, zamiast języka XAML były używane kodowane przepływy pracy.  Poniżej przedstawiono przykład jednego z przepływów pracy WF4:

```csharp
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

 Istnieje wiele innych czynników, które mogą mieć wpływ na użycie pamięci. Te same porady dotyczące wszystkich programów zarządzanych nadal mają zastosowanie.  W środowiskach <xref:System.ServiceModel.WorkflowServiceHost> hostowanych przez usługi IIS obiekt utworzony dla definicji przepływu pracy pozostaje w pamięci do momentu odtworzenia puli aplikacji.  Należy pamiętać o tym podczas pisania rozszerzeń.  Ponadto najlepiej jest unikać zmiennych "Global" (zmiennych w zakresie całego przepływu pracy) i ograniczyć zakres zmiennych wszędzie tam, gdzie to możliwe.

## <a name="workflow-runtime-services"></a>Usługi środowiska uruchomieniowego przepływu pracy

### <a name="persistence"></a>Trwałość
 WF3 i WF4 są dostarczane z dostawcą trwałości SQL.  Dostawca trwałości SQL WF3 jest prostą implementacją, która serializować wystąpienie przepływu pracy i zapisuje je w obiekcie blob.  Z tego powodu wydajność tego dostawcy zależy w dużym stopniu od rozmiaru wystąpienia przepływu pracy.  W WF3 rozmiar wystąpienia może wzrosnąć z wielu powodów, jak opisano wcześniej w tym dokumencie.  Wielu klientów zdecyduje się nie używać domyślnego dostawcy trwałości SQL, ponieważ przechowywanie serializowanego wystąpienia w bazie danych nie zapewnia wglądu w stan przepływu pracy.  Aby znaleźć konkretny przepływ pracy bez znajomości identyfikatora przepływu pracy, jeden z nich będzie musiał rozszeregować każde trwałe wystąpienie i sprawdzić zawartość.  Wielu deweloperów woli napisać własnych dostawców trwałości do pokonania tej przeszkody.

 Dostawca trwałości SQL WF4 próbował rozwiązać niektóre z tych problemów.  Tabele trwałości uwidaczniają pewne informacje, takie jak aktywne zakładki i właściwości promocji.  Nowa funkcja korelacji oparta na zawartości w programie WF4 nie będzie działać prawidłowo przy użyciu metody trwałości SQL WF3, która jest oparta na pewnych zmianach w organizacji wystąpienia utrwalonego przepływu pracy.  Dzięki temu zadanie dostawcy trwałości jest bardziej złożone i ma dodatkowe obciążenie bazy danych.

### <a name="environment-setup"></a>Konfiguracja środowiska
![Konfiguracja środowiska dla testu wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

### <a name="test-setup"></a>Konfiguracja testu
 Nawet przy ulepszonym zestawie funkcji i lepszym obsłudze współbieżności dostawca trwałości SQL w programie WF4 jest szybszy niż dostawca w WF3.  Aby to zaprezentować, dwa przepływy pracy, które wykonują zasadniczo te same operacje w WF3 i WF4 są porównane poniżej.

 ![Przepływ pracy trwałości w WF3 po lewej stronie i WF4 po prawej](./media/performance/persist-workflow-wf3-wf4.gif)

 Dwa przepływy pracy są tworzone przez odebraną wiadomość.  Po wysłaniu początkowej odpowiedzi przepływ pracy zostanie utrwalony.  W przypadku WF3 wartość pusta <xref:System.Workflow.ComponentModel.TransactionScopeActivity> jest używana do inicjowania trwałości.  To samo można osiągnąć w WF3 przez oznaczenie działania jako "utrwalanie przy zamykaniu".  Drugi skorelowany komunikat kończy przepływ pracy.  Przepływy pracy są utrwalane, ale nie są zwalniane.

### <a name="test-results"></a>Wyniki tekstu
 ![Wykres kolumnowy przedstawiający trwałość przepływności](./media/performance/throughput-persistence-graph.gif)

 Gdy transport między klientem a warstwą środkową jest HTTP, trwałość w WF4 wykazuje zwiększenie 2,6 razy.  Transport TCP zwiększa ten współczynnik do 3,0 razy.  We wszystkich przypadkach użycie procesora CPU w warstwie środkowej ma wartość 98% lub wyższą.  Przyczyna WF4 przepływności jest większa z powodu szybszego środowiska uruchomieniowego przepływu pracy.  Rozmiar serializowanego wystąpienia jest niski dla obu przypadków i nie jest głównym elementem, w tej sytuacji.

 Przepływy pracy WF3 i WF4 w tym teście używają działania, aby jawnie określić, kiedy powinna wystąpić trwałość.  Umożliwia to utrwalanie przepływu pracy bez jego wyładowania.  W programie WF3 można również nadal korzystać <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> z funkcji, ale spowoduje to odciążenie wystąpienia przepływu pracy z pamięci.  Jeśli deweloper korzystający z usługi WF3 chce upewnić się, że przepływ pracy utrzymuje się w określonych punktach, musi zmienić definicję przepływu pracy lub uregulować koszt wyładowania i ponownego załadowania wystąpienia przepływu pracy.  Nowa funkcja w programie WF4 umożliwia utrwalanie bez rozładowywania: <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>.  Ta funkcja umożliwia utrwalanie wystąpienia przepływu pracy w trybie bezczynności, ale pozostaje w pamięci <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> do momentu spełnienia progu lub wznowienia wykonania.

 Należy pamiętać, że dostawca trwałości SQL WF4 wykonuje więcej pracy w warstwie bazy danych.  Baza danych SQL może stać się wąskim gardłem, dlatego ważne jest, aby monitorować użycie procesora i dysku w tym miejscu.  Podczas testowania wydajności aplikacji przepływu pracy należy uwzględnić następujące liczniki wydajności z bazy danych SQL:

- DyskFizyczny\\% czasu odczytu dysku

- DyskFizyczny\\% czasu dysku

- DyskFizyczny\\% czasu zapisu dysku

- DyskFizyczny\\% średniej Długość kolejki dysku

- PhysicalDisk\Avg. Długość kolejki odczytu dysku

- PhysicalDisk\Avg. Długość kolejki zapisu dysku

- Długość kolejki dysku fizyczny \ bieżąca

- Informacje o\\procesorze czas procesora (%)

- SQLServer: czas oczekiwania zamka Latches\Average (MS)

- SQLServer: Latches\Latch oczekiwania na sekundę

### <a name="tracking"></a>Śledzenie
 Śledzenie przepływu pracy może służyć do śledzenia postępu przepływu pracy.  Informacje zawarte w zdarzeniach śledzenia są określane przez profil śledzenia.  Im bardziej skomplikowany profil śledzenia, tym bardziej kosztowne jest śledzenie.

 WF3 dostarczana z usługą śledzenia opartą na języku SQL.  Ta usługa może współpracować w trybach wsadowych i niewsadowych.  W trybie bez partii zdarzenia śledzenia są zapisywane bezpośrednio w bazie danych.  W trybie wsadowym zdarzenia śledzenia są gromadzone w tej samej partii co stan wystąpienia przepływu pracy.  Tryb wsadowy ma najlepszą wydajność dla szerokiego zakresu projektów przepływu pracy.  Jednak przetwarzanie wsadowe może mieć negatywny wpływ na wydajność, jeśli przepływ pracy uruchamia wiele działań bez utrwalania i te działania są śledzone.  Zwykle zdarza się to w pętlach i najlepszym sposobem na uniknięcie tego scenariusza jest zaprojektowanie dużych pętli w celu uwzględnienia punktu trwałości.  Wprowadzenie punktu trwałości do pętli może negatywnie wpłynąć na wydajność, dlatego ważne jest, aby mierzyć koszty każdego z nich i mieć saldo.

 Usługa WF4 nie jest dostarczana z usługą śledzenia SQL.  Rejestrowanie informacji o śledzeniu do bazy danych SQL może być obsługiwane lepiej z serwera aplikacji, a nie wbudowane w .NET Framework. Dlatego śledzenie SQL jest teraz obsługiwane przez program AppFabric.  Wbudowany dostawca śledzenia w programie WF4 jest oparty na śledzeniu zdarzeń systemu Windows (ETW).

 ETW to system zdarzeń o niskim opóźnieniu, wbudowany w system Windows.  Używa modelu dostawcy/odbiorcy, który umożliwia naliczanie opłat za śledzenie zdarzeń tylko wtedy, gdy istnieje w rzeczywistości konsument.  Oprócz zdarzeń jądra, takich jak procesor, dysk, pamięć i użycie sieci, wiele aplikacji korzysta również z funkcji ETW.  Zdarzenia ETW są bardziej wydajne niż liczniki wydajności w tym zdarzeniu można dostosować do aplikacji.  Zdarzenie może zawierać tekst, taki jak identyfikator przepływu pracy lub komunikat informacyjny.  Ponadto zdarzenia są klasyfikowane przy użyciu masek bitowych, dzięki czemu używanie pewnego podzestawu zdarzeń będzie miało mniejszy wpływ na wydajność niż przechwytywanie wszystkich zdarzeń.

 Korzyści wynikające z używania funkcji ETW do śledzenia zamiast programu SQL obejmują:

- Zbieranie zdarzeń śledzenia może być oddzielone innym procesom.  Zapewnia to większą elastyczność w sposobie rejestrowania zdarzeń.

- Zdarzenia śledzenia funkcji ETW można łatwo łączyć z zdarzeniami ETW WCF lub innymi dostawcami ETW, takimi jak SQL Server lub dostawca jądra.

- Autorzy przepływu pracy nie muszą zmieniać przepływu pracy w celu lepszego działania z określoną implementacją śledzenia, taką jak tryb wsadowy usługi WF3 śledzenia SQL.

- Administrator może włączać lub wyłączać śledzenie bez konieczności odtwarzania procesu hosta.

 Korzyści wynikające z wydajności śledzenia ETW są uzyskiwane z wadą.  Zdarzenia ETW mogą zostać utracone, jeśli system ma intensywną siłę zasobów.  Przetwarzanie zdarzeń nie jest przeznaczone do blokowania normalnego wykonywania programu i w związku z tym nie jest gwarantowane, że wszystkie zdarzenia ETW będą emitowane do subskrybentów.  Dzięki temu śledzenie ETW jest doskonałe dla monitorowania kondycji, ale nie jest odpowiednie do inspekcji.

 Mimo że usługa WF4 nie ma dostawcy śledzenia SQL, program AppFabric wykonuje.  Podejście do śledzenia SQL w programie AppFabric ma na celu subskrybowanie zdarzeń ETW za pomocą usługi systemu Windows, która tworzy partię zdarzeń i zapisuje je w tabeli SQL zaprojektowanej do szybkiego wstawiania.  Osobne zadanie opróżnia dane z tej tabeli i replikuje je do tabel raportowania, które mogą być wyświetlane na pulpicie nawigacyjnym programu AppFabric.  Oznacza to, że partia zdarzeń śledzenia jest obsługiwana niezależnie od przepływu pracy, z którego pochodzi, i w związku z tym nie musi czekać na punkt trwałości przed zarejestrowaniem.

 Zdarzenia ETW można rejestrować za pomocą narzędzi, takich jak logman lub Xperf.  Kompaktowy plik ETL można wyświetlić za pomocą narzędzia, takiego jak XperfView lub przekonwertowanego do bardziej czytelnego formatu, takiego jak XML, z tracerpt.  W programie WF3 jedyną opcją pobierania zdarzeń śledzenia bez bazy danych SQL jest utworzenie niestandardowej usługi śledzenia. Aby uzyskać więcej informacji na temat funkcji ETW, zobacz [usługi WCF i śledzenie zdarzeń dla systemu Windows](../wcf/samples/wcf-services-and-event-tracing-for-windows.md) i [Śledzenie zdarzeń — aplikacje systemu Windows](/windows/desktop/etw/event-tracing-portal).

 Włączenie śledzenia przepływu pracy będzie miało wpływ na wydajność w różnych stopniach.  Poniższy wzorzec używa narzędzia Logman do użycia zdarzeń śledzenia ETW i rejestrowania ich w pliku ETL.  Koszt śledzenia SQL w programie AppFabric nie jest objęty zakresem tego artykułu.  W tym teście porównawczym jest wyświetlany podstawowy profil śledzenia, używany również w programie AppFabric.  Uwzględniono również koszt śledzenia tylko zdarzeń monitorowania kondycji.  Te zdarzenia są przydatne do rozwiązywania problemów i określania średniej przepływności systemu.

### <a name="environment-setup"></a>Konfiguracja środowiska
 ![Konfiguracja środowiska dla testu wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Wyniki tekstu

 ![Wykres kolumnowy przedstawiający koszty śledzenia przepływu pracy](./media/performance/workflow-tracking-costs.gif)

 Monitorowanie kondycji ma około 3% wpływu na przepływność.  Koszt profilu podstawowego wynosi około 8%.

## <a name="interop"></a>Interop
 WF4 to prawie pełna odpisana [!INCLUDE[wf1](../../../includes/wf1-md.md)] wartość i dlatego WF3 przepływy pracy i działania nie są bezpośrednio zgodne z WF4.  Wielu klientów, którzy wcześniej przyjęli Windows Workflow Foundation, będą mieć definicje przepływów pracy lub innych firm, a także niestandardowe działania dla WF3.  Jednym ze sposobów ułatwienia przejścia do WF4 jest użycie działania międzyoperacyjności, które może wykonywać działania WF3 z poziomu przepływu pracy WF4.  Zalecane jest, aby działanie <xref:System.Activities.Statements.Interop> było używane tylko wtedy, gdy jest to konieczne. Aby uzyskać więcej informacji na temat migracji do programu WF4, zapoznaj się ze [wskazówkami dotyczącymi migracji WF4](https://go.microsoft.com/fwlink/?LinkID=153313).

### <a name="environment-setup"></a>Konfiguracja środowiska
 ![Konfiguracja środowiska dla testu wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Wyniki tekstu
 
W poniższej tabeli przedstawiono wyniki przebiegu przepływu pracy zawierającego pięć działań w sekwencji w różnych konfiguracjach.

|Test|Przepływność (przepływy pracy/s)|
|----------|-----------------------------------|
|Sekwencja WF3 w środowisku uruchomieniowym WF3|1,576|
|Sekwencja WF3 w środowisku uruchomieniowym WF4 przy użyciu międzyoperacyjnego|2,745|
|Sekwencja WF4|153,582|

 Istnieje istotny wzrost wydajności dotyczący użycia międzyoperacyjności w przypadku prostych WF3.  Jednak w porównaniu z działaniami WF4 wzrost jest nieznaczny.

## <a name="summary"></a>Podsumowanie
 Duże inwestycje w wydajność dla WF4 są płatne w wielu kluczowych obszarach.  Wydajność poszczególnych składników przepływu pracy to w niektórych przypadkach setki razy szybsze w WF4 w porównaniu do WF3 ze względu na [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowisko uruchomieniowe programu leaner.  Liczby opóźnień również są znacznie lepsze.  Oznacza to, że spadek wydajności do [!INCLUDE[wf1](../../../includes/wf1-md.md)] użycia w przeciwieństwie do kodu ręcznego usług aranżacji WCF jest bardzo mały, biorąc pod uwagę, że [!INCLUDE[wf1](../../../includes/wf1-md.md)]dodano zalety korzystania z programu.  Wydajność trwałości wzrosła przez współczynnik 2,5-3,0.  Monitorowanie kondycji przy użyciu śledzenia przepływów pracy ma teraz bardzo niewielkie obciążenie.  Kompleksowy zestaw przewodników migracji jest dostępny dla tych, które rozważają przechodzenie od WF3 do WF4.  Wszystko to powinno WF4 atrakcyjną opcję tworzenia złożonych aplikacji.
