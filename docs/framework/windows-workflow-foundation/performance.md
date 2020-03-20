---
title: Wydajność programu Windows Workflow Foundation 4
ms.date: 03/30/2017
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
ms.openlocfilehash: 5fec41baacca0f35618dd5bc409b88ac792ad125
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182976"
---
# <a name="windows-workflow-foundation-4-performance"></a>Wydajność programu Windows Workflow Foundation 4

 Program .NET Framework 4 zawiera dużą wersję programu Windows Workflow Foundation (WF) z dużymi inwestycjami w wydajność. Ta nowa wersja wprowadza istotne zmiany w [!INCLUDE[wf1](../../../includes/wf1-md.md)] projekcie z poprzednich wersji, które zostały dostarczone w ramach .NET Framework 3.0 i .NET Framework 3.5. Został on ponownie zaprojektowany z rdzenia modelu programowania, środowiska uruchomieniowego i narzędzi, aby znacznie poprawić wydajność i użyteczność. W tym temacie przedstawiono ważne charakterystyki wydajności tych poprawek i porównuje je z tymi z poprzedniej wersji.

 Wydajność poszczególnych składników przepływu pracy wzrosła o rzędy wielkości między WF3 i WF4.  Pozostawia to lukę między ręcznie kodowane usługi Windows Communication Foundation (WCF) i WCF usług przepływu pracy być dość małe.  Opóźnienie przepływu pracy zostało znacznie zmniejszone w WF4.  Wydajność trwałości wzrosła o współczynnik 2,5 - 3,0.  Monitorowanie kondycji za pomocą śledzenia przepływu pracy ma znacznie mniej narzutów.  Są to ważne powody, aby przeprowadzić migrację do lub przyjąć WF4 w aplikacjach.

## <a name="terminology"></a>Terminologia

 Wersja [!INCLUDE[wf1](../../../includes/wf1-md.md)] wprowadzone w .NET Framework 4 będą określane jako WF4 dla pozostałej części tego tematu. [!INCLUDE[wf1](../../../includes/wf1-md.md)]został wprowadzony w .NET Framework 3.0 i miał kilka drobnych wersji za pośrednictwem programu .NET Framework 3.5 SP1. .NET Framework 3.5 wersja Workflow Foundation będzie określana jako WF3 dla pozostałej części tego tematu. WF3 jest dostarczany w .NET Framework 4 side-by-side with WF4. Aby uzyskać więcej informacji na temat migracji artefaktów WF3 do WF4, zobacz: [Przewodnik migracji programu Windows Workflow Foundation 4](migration-guidance.md).

 Windows Communication Foundation (WCF) to ujednolicony model programowania firmy Microsoft do tworzenia aplikacji zorientowanych na usługi. Po raz pierwszy został wprowadzony jako część .NET 3.0 wraz z WF3 i teraz jest jednym z kluczowych składników programu .NET Framework.

 Windows Server AppFabric to zestaw zintegrowanych technologii, które ułatwiają tworzenie, skalowanie i zarządzanie aplikacjami sieci Web i złożonymi działającymi na usługach IIS. Zapewnia narzędzia do monitorowania i zarządzania usługami i przepływami pracy. Aby uzyskać więcej informacji, zobacz [System Windows Server AppFabric 1.0](https://docs.microsoft.com/previous-versions/appfabric/ff384253(v=azure.10)).

## <a name="goals"></a>Cele
 Celem tego tematu jest pokazanie charakterystyki wydajności WF4 z danymi mierzonymi dla różnych scenariuszy. Zapewnia również szczegółowe porównania między WF4 i WF3, a tym samym pokazuje wielkie ulepszenia, które zostały wprowadzone w tej nowej wersji. Scenariusze i dane przedstawione w tym artykule kwantyfikują podstawowy koszt różnych aspektów WF4 i WF3. Te dane są przydatne w zrozumieniu charakterystyki wydajności WF4 i mogą być pomocne w planowaniu migracji z WF3 do WF4 lub przy użyciu WF4 w tworzeniu aplikacji. Należy jednak zwrócić uwagę na wnioski wyciągnięte z danych przedstawionych w tym artykule. Wydajność złożonej aplikacji przepływu pracy jest w dużym stopniu zależna od sposobu implementacji przepływu pracy i sposobu integracji różnych składników. Należy zmierzyć każdą aplikację w celu określenia właściwości wydajności tej aplikacji.

## <a name="overview-of-wf4-performance-enhancements"></a>Omówienie ulepszeń wydajności WF4
 WF4 został starannie zaprojektowany i wdrożony z wysoką wydajnością i skalowalnością, które są opisane w poniższych sekcjach.

### <a name="wf-runtime"></a>WF Środowisko uruchomieniowe
 W rdzeniu [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowiska wykonawczego jest harmonogram asynchroniczne, który napędza wykonywanie działań w przepływie pracy. Zapewnia wydajne, przewidywalne środowisko wykonywania dla działań. Środowisko ma dobrze zdefiniowany kontrakt na wykonanie, kontynuację, ukończenie, anulowanie, wyjątki i przewidywalny model wątków.

 W porównaniu do WF3 środowiska uruchomieniowego WF4 ma bardziej wydajny harmonogram. Wykorzystuje tę samą pulę wątków we/wy, która jest używana dla WCF, która jest bardzo wydajna w wykonywaniu wsadowych elementów roboczych. Wewnętrzna kolejka harmonogramu elementów roboczych jest zoptymalizowana pod kątem większości typowych wzorców użycia. Środowisko uruchomieniowe WF4 zarządza również stany wykonywania w sposób bardzo lekki z minimalną synchronizacji i logiki obsługi zdarzeń, podczas gdy WF3 zależy od rejestracji zdarzeń wagi wagi i wywołania do wykonywania złożonej synchronizacji dla przejść stanu.

### <a name="data-storage-and-flow"></a>Przechowywanie i przepływ danych
 W WF3 dane skojarzone z działaniem są modelowane za pomocą <xref:System.Windows.DependencyProperty>właściwości zależności implementowanych przez typ . Wzorzec właściwości zależności został wprowadzony w programie Windows Presentation Foundation (WPF). Ogólnie rzecz biorąc ten wzorzec jest bardzo elastyczny do obsługi łatwego wiązania danych i innych funkcji interfejsu użytkownika. Jednak wzorzec wymaga właściwości, które mają być zdefiniowane jako pola statyczne w definicji przepływu pracy. Ilekroć [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowisko uruchomieniowe ustawia lub pobiera wartości właściwości, obejmuje mocno ważone logiki wyszukiwania.

 WF4 używa logiki określania zakresu danych, aby znacznie poprawić sposób obsługi danych w przepływie pracy. Oddziela dane przechowywane w działaniu od danych, które przepływa przez granice działania przy użyciu dwóch różnych pojęć: zmienne i argumenty. Za pomocą jasnego zakresu hierarchicznego dla zmiennych i "W/Out/InOut" argumenty, złożoność użycia danych dla działań jest znacznie zmniejszona i okres istnienia danych jest również automatycznie zakres. Działania mają dobrze zdefiniowany podpis opisany przez jego argumenty. Po prostu sprawdzając działanie można określić, jakie dane oczekuje się otrzymać i jakie dane będą produkowane przez niego w wyniku jego wykonania.

 W WF3 działania zostały zainicjowane podczas tworzenia przepływu pracy. W WF 4 działania są inicjowane tylko wtedy, gdy wykonywane są odpowiednie działania. Pozwala to na prostszy cykl życia działania bez wykonywania operacji Inicjowanie/Uninitialize podczas tworzenia nowego wystąpienia przepływu pracy, a tym samym osiągnięto większą wydajność

### <a name="control-flow"></a>Przepływ sterowania
 Podobnie jak w każdym [!INCLUDE[wf1](../../../includes/wf1-md.md)] języku programowania, zapewnia obsługę przepływów sterowania dla definicji przepływu pracy, wprowadzając zestaw działań przepływu sterowania do sekwencjonowania, pętli, rozgałęzienia i innych wzorców. W WF3, gdy to samo działanie musi zostać <xref:System.Workflow.ComponentModel.ActivityExecutionContext> ponownie wykonane, tworzona jest nowa, a działanie jest klonowane za pomocą logiki serializacji i deserializacji o dużej wadze opartej na <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Zazwyczaj wydajność przepływów kontroli iteracyjnej jest znacznie wolniejszy niż wykonywanie sekwencji działań.

 WF4 radzi sobie z tym zupełnie inaczej. Przyjmuje szablon działania, tworzy nowy obiekt ActivityInstance i dodaje go do kolejki harmonogramu. Cały ten proces obejmuje tylko jawne tworzenie obiektów i jest bardzo lekki.

### <a name="asynchronous-programming"></a>Programowanie asynchroniczne
 Aplikacje mają zwykle lepszą wydajność i skalowalność dzięki programowaniu asynchroniiowemu dla długotrwałych operacji blokowania, takich jak operacje we/wy lub rozproszone operacje obliczeniowe. WF4 zapewnia asynchroniiową obsługę <xref:System.Activities.AsyncCodeActivity> <xref:System.Activities.AsyncCodeActivity%601>za pośrednictwem podstawowych typów aktywności , . Środowisko uruchomieniowe natywnie rozumie działania asynchroniczne i dlatego można automatycznie umieścić wystąpienie w strefie no-persist, gdy praca asynchronicznie jest zaległe. Działania niestandardowe mogą pochodzić z tych typów do wykonywania pracy asynchroniiowej bez przytrzymywać wątku harmonogramu przepływu pracy i blokowanie wszelkich działań, które mogą być w stanie uruchomić równolegle.

### <a name="messaging"></a>Obsługa komunikatów
 Początkowo WF3 miał bardzo ograniczoną obsługę obsługi wiadomości za pośrednictwem zdarzeń zewnętrznych lub wywołań usług sieci web. W .NET 3.5 przepływy pracy mogą być implementowane jako klienci WCF lub udostępniane jako usługi WCF za pośrednictwem <xref:System.Workflow.Activities.SendActivity> i <xref:System.Workflow.Activities.ReceiveActivity>. W WF4 koncepcja programowania wiadomości opartych na przepływie pracy została dodatkowo wzmocniona poprzez ścisłą integrację logiki obsługi wiadomości WCF z WF.

 Ujednolicony potok przetwarzania wiadomości dostarczony w WCF w .NET 4 pomaga usługom WF4 mieć znacznie lepszą wydajność i skalowalność niż WF3. WF4 also provides richer messaging programming support that can model complex Message Exchange Patterns (MEPs). Deweloperzy mogą używać wpisanych umów serwisowych w celu uzyskania łatwego programowania lub nieokreślonych umów serwisowych w celu uzyskania lepszej wydajności bez płacenia kosztów serializacji. Obsługa buforowania kanału po stronie <xref:System.ServiceModel.Activities.SendMessageChannelCache> klienta za pośrednictwem klasy w WF4 pomaga deweloperom tworzyć szybkie aplikacje przy minimalnym wysiłku. Aby uzyskać więcej informacji, zobacz [Zmienianie poziomów udostępniania pamięci podręcznej dla działań wysyłania](../wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).

### <a name="declarative-programming"></a>Programowanie deklaratywne
 WF4 zapewnia czyste i proste deklaratywne ramy programowania do modelowania procesów biznesowych i usług. Model programowania obsługuje w pełni deklaratywny skład działań, bez kodu obok, znacznie upraszczając tworzenie przepływu pracy. W programie .NET Framework 4 deklaratywna struktura programowania oparta na języku XAML została zunifikowana w pojedynczym zestawie System.Xaml.dll w celu obsługi zarówno WPF, jak i WF.

 W WF4 XAML zapewnia prawdziwie deklaratywne środowisko i umożliwia zdefiniowanie całej definicji przepływu pracy w znacznikach XML, odwołując się do działań i typów utworzonych przy użyciu platformy .NET. Było to trudne do zrobienia w WF3 w formacie XOML bez angażowania niestandardowej logiki związanej z kodem. Nowy stos XAML w .NET 4 ma znacznie lepszą wydajność w serializacji/deserializacji artefaktów przepływu pracy i sprawia, że programowanie deklaratywne jest bardziej atrakcyjne i stałe.

### <a name="workflow-designer"></a>Projektant przepływów pracy
 W pełni deklaratywna obsługa programowania dla WF4 jawnie nakłada wyższe wymagania dotyczące wydajności czasu projektowania dla dużych przepływów pracy. Projektant przepływu pracy w WF4 ma znacznie lepszą skalowalność dla dużych przepływów pracy niż dla WF3. Dzięki obsłudze wirtualizacji interfejsu użytkownika projektant może łatwo załadować duży przepływ pracy 1000 działań w ciągu kilku sekund, podczas gdy prawie niemożliwe jest załadowanie przepływu pracy kilkuset działań z projektantem WF3.

## <a name="component-level-performance-comparisons"></a>Porównania wydajności na poziomie komponentu
 Ta sekcja zawiera dane dotyczące bezpośrednich porównań między poszczególnymi działaniami w przepływach pracy WF3 i WF4.  Kluczowe obszary, takie jak trwałość mają głębszy wpływ na wydajność niż poszczególne składniki działania.  Ulepszenia wydajności w poszczególnych składników w WF4 są jednak ważne, ponieważ składniki są teraz wystarczająco szybko, aby można porównać z ręcznie kodowane logiki aranżacji.  Przykład, który jest omówiony w następnej sekcji: "Scenariusz składu usługi."

### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Konfiguracja środowiska do pomiaru wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

 Powyższy rysunek przedstawia konfigurację maszyny używaną do pomiaru wydajności na poziomie komponentu. Jeden serwer i pięciu klientów połączonych za pośrednictwem jednego interfejsu sieciowego Ethernet 1 Gb/s. W celu łatwego pomiaru serwer jest skonfigurowany do używania pojedynczego rdzenia serwera dwu-proc/czterordzeniowego z systemem Windows Server 2008 x86. Wykorzystanie procesora systemowego jest utrzymywane na poziomie prawie 100%.

### <a name="test-details"></a>Szczegóły testu
 WF3 <xref:System.Workflow.Activities.CodeActivity> jest prawdopodobnie najprostszym działaniem, które mogą być używane w przepływie pracy WF3.  Działanie wywołuje metodę w kodzie, do których programista przepływu pracy może umieścić kod niestandardowy.  W WF4 nie ma bezpośredniego analogu <xref:System.Workflow.Activities.CodeActivity> do WF3, który zapewnia taką samą funkcjonalność.  Należy zauważyć, <xref:System.Activities.CodeActivity> że istnieje klasa podstawowa w WF4, <xref:System.Workflow.Activities.CodeActivity>która nie jest związana z WF3 .  Autorzy przepływu pracy są zachęcani do tworzenia działań niestandardowych i tworzenia przepływów pracy tylko XAML.  W poniższych testach `Comment` działanie wywoływane jest <xref:System.Workflow.Activities.CodeActivity> używane zamiast pustego w przepływach pracy WF4.  Kod w `Comment` działaniu jest następujący:

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
 Przepływ pracy jest przepływem pracy sekwencji zawierającym jedno działanie podrzędne.  Działanie jest <xref:System.Workflow.Activities.CodeActivity> bez kodu w przypadku WF3 `Comment` i działania w przypadku WF4.

### <a name="while-with-1000-iterations"></a>Podczas gdy z 1000 iteracje
 Przepływ pracy sekwencji <xref:System.Activities.Statements.While> zawiera jedno działanie z jednym działaniem podrzędnym w pętli, która nie wykonuje żadnej pracy.

### <a name="replicator-compared-to-parallelforeach"></a>Replikator w porównaniu z ParallelForEach
 <xref:System.Workflow.Activities.ReplicatorActivity>w WF3 ma tryby wykonywania sekwencyjnego i równoległego.  W trybie sekwencyjnym wydajność działania jest <xref:System.Workflow.Activities.WhileActivity>podobna do .  Jest <xref:System.Workflow.Activities.ReplicatorActivity> najbardziej przydatne do wykonywania równoległego.  Analog WF4 do tego <xref:System.Activities.Statements.ParallelForEach%601> jest działanie.

 Na poniższym diagramie przedstawiono przepływy pracy używane dla tego testu. Przepływ pracy WF3 znajduje się po lewej stronie, a przepływ pracy WF4 znajduje się po prawej stronie.

 ![WF3 ReplicatorActivity i WF4 ParallelForEach](./media/performance/replicator-parallel-wf3-wf4.gif)

### <a name="sequential-workflow-with-five-activities"></a>Sekwencyjny przepływ pracy z pięcioma działaniami
 Ten test ma na celu pokazanie efektu wykonywania kilku działań w sekwencji.  Istnieje pięć działań w sekwencji.

### <a name="transaction-scope"></a>Zakres transakcji
 Test zakresu transakcji różni się nieco od innych testów tym, że nowe wystąpienie przepływu pracy nie jest tworzone dla każdej iteracji.  Zamiast tego przepływ pracy jest skonstruowany z while <xref:System.Activities.Statements.TransactionScope> pętli zawierającej działanie zawierające pojedyncze działanie, które nie działa.  Każde uruchomienie partii 50 iteracji za pośrednictwem while pętli jest liczony jako pojedyncza operacja.

### <a name="compensation"></a>Kompensacja
 Przepływ pracy WF3 ma jedno działanie compensatable o nazwie `WorkScope`.  Działanie po prostu <xref:System.Workflow.ComponentModel.ICompensatableActivity> implementuje interfejs:

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

 Program obsługi błędów jest przeznaczony dla `WorkScope` działania. Przepływ pracy WF4 jest równie uproszczony.  A <xref:System.Activities.Statements.CompensableActivity> ma treść i program obsługi wynagrodzeń.  Jawne kompensacji jest następny w sekwencji.  Działanie treści i działanie obsługi wynagrodzeń są zarówno puste implementacje:

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

Na poniższym diagramie przedstawiono podstawowy przepływ pracy wynagrodzeń. Przepływ pracy WF3 znajduje się po lewej stronie, a przepływ pracy WF4 znajduje się po prawej stronie.

![Podstawowe przepływy wynagrodzeń WF3 i WF4](./media/performance/basic-compensation-workflows-wf3-wf4.gif)

### <a name="performance-test-results"></a>Wyniki testu wydajności

 ![Tabela przedstawiająca dane wyników testów wydajności](./media/performance/performance-test-data.gif)

 ![Wykres kolumnowy porównujący dane z testu wydajności WF3 i WF4](./media/performance/performance-test-chart.gif)

 Wszystkie testy są mierzone w przepływach pracy na sekundę, z wyjątkiem testu zakresu transakcji.  Jak widać powyżej, [!INCLUDE[wf1](../../../includes/wf1-md.md)] wydajność środowiska uruchomieniowego poprawiła się we wszystkich dziedzinach, szczególnie w obszarach, które wymagają wielu wykonań tego samego działania, takich jak while pętli.

## <a name="service-composition-scenario"></a>Scenariusz składu usługi
 Jak pokazano w poprzedniej sekcji "Porównania wydajności na poziomie składnika", nastąpiło znaczne zmniejszenie narzutów między WF3 i WF4.  Usługi przepływu pracy WCF można teraz prawie dopasować wydajność ręcznie kodowane usługi WCF, ale nadal mają wszystkie zalety środowiska [!INCLUDE[wf1](../../../includes/wf1-md.md)] wykonawczego.  W tym scenariuszu testowym porównuje usługę WCF z usługą przepływu pracy WCF w WF4.

### <a name="online-store-service"></a>Serwis sklepu internetowego
 Jedną z mocnych stron programu Windows Workflow Foundation jest możliwość tworzenia procesów przy użyciu kilku usług.  W tym przykładzie istnieje usługa sklepu internetowego, która organizuje dwa wywołania usługi w celu zakupu zamówienia.  Pierwszym krokiem jest sprawdzenie poprawności zamówienia przy użyciu usługi sprawdzania poprawności zamówień.  Drugim krokiem jest wypełnienie zamówienia za pomocą usługi magazynowej.

 Dwie usługi wewnętrznej bazy danych, Usługa sprawdzania poprawności zamówień i usługa magazynu, pozostają takie same dla obu testów.  Część, która się zmienia, to usługa sklepu internetowego, która wykonuje aranżację.  W jednym przypadku usługa jest ręcznie kodowane jako usługa WCF.  W innym przypadku usługa jest zapisywana jako usługa przepływu pracy WCF w WF4. [!INCLUDE[wf1](../../../includes/wf1-md.md)]-specyficzne funkcje, takie jak śledzenie i trwałość są wyłączone dla tego testu.

### <a name="environment"></a>Środowisko
![Konfiguracja środowiska do pomiaru wydajności](./media/performance/performance-test-environment.gif)

 Żądania klientów są przesyłane do usługi sklepu internetowego za pośrednictwem protokołu HTTP z wielu komputerów.  Jeden komputer obsługuje wszystkie trzy usługi.  Warstwa transportu między usługą sklepu internetowego a usługami zaplecza to TCP lub HTTP.  Pomiar operacji/sekundy jest oparty na `PurchaseOrder` liczbie zakończonych połączeń wykonanych do Serwisu Sklepu Internetowego.  Buforowanie kanałów to nowa funkcja dostępna w WF4.  W części WCF tego kanału testowego buforowania nie jest dostarczany po wyjęciu z pudełka, więc ręcznie kodowane implementacji techniki prostego buforowania został użyty w usłudze sklepu internetowego.

### <a name="performance"></a>Wydajność
![Wykres kolumnowy przedstawiający wydajność usługi sklepu internetowego](./media/performance/online-store-performance-graph.gif)

 Łączenie się z usługami TCP wewnętrznej [!INCLUDE[wf1](../../../includes/wf1-md.md)] bazy danych bez buforowania kanałów, usługa ma 17,2% wpływ na przepływność.  W przypadku łączenia kanałów kara wynosi około 23,8%.  W przypadku protokołu HTTP wpływ jest znacznie mniejszy: 4,3% bez łączenia i 8,1% z pulą.  Należy również pamiętać, że buforowanie kanałów zapewnia bardzo niewielkie korzyści podczas korzystania z protokołu HTTP.

 Chociaż istnieje obciążenie ze środowiska wykonawczego WF4 w porównaniu z ręcznie kodowane WCF usługi w tym teście, można uznać za najgorszy scenariusz.  Dwie usługi wewnętrznej bazy danych w tym teście wykonują bardzo mało pracy.  W rzeczywistym scenariuszu end-to-end te usługi będą wykonywać droższe operacje, takie jak wywołania bazy danych, dzięki czemu wpływ na wydajność warstwy transportu mniej ważne.  To plus korzyści z funkcji dostępnych w WF4 sprawia, że Workflow Foundation realnym wyborem do tworzenia usług aranżacji.

## <a name="key-performance-considerations"></a>Najważniejsze zagadnienia dotyczące wydajności
 Obszary charakterystyczne w tej sekcji, z wyjątkiem interop, zostały radykalnie zmienione między WF3 i WF4.  Wpływa to na projektowanie aplikacji przepływu pracy, a także na wydajność.

#### <a name="workflow-activation-latency"></a>Opóźnienie aktywacji przepływu pracy
 W aplikacji usługi przepływu pracy WCF opóźnienie uruchamiania nowego przepływu pracy lub ładowania istniejącego przepływu pracy jest ważne, ponieważ może być blokowanie.  Ten przypadek testowy mierzy hostA XOML WF3 względem hosta WF4 XAMLX w typowym scenariuszu.

##### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Konfiguracja środowiska dla testów opóźnienia i przepływności](./media/performance/latency-throughput-environment-setup.gif)

##### <a name="test-setup"></a>Ustawienia testu
 W scenariuszu komputer kliencki kontaktuje się z usługą przepływu pracy WCF przy użyciu korelacji opartej na kontekście.  Korelacja kontekstu wymaga specjalnego powiązania kontekstu i używa nagłówka kontekstu lub pliku cookie do powiązania wiadomości z wystąpieniem poprawnego przepływu pracy.  Ma korzyści wydajności, ponieważ identyfikator korelacji znajduje się w nagłówku wiadomości, więc treść wiadomości nie musi być analizowana.

 Usługa utworzy nowy przepływ pracy z żądaniem i wyśle natychmiastową odpowiedź, aby pomiar opóźnienia nie uwzględniał czasu poświęconego na uruchomienie przepływu pracy.  Przepływ pracy WF3 to XOML z kodem, a przepływ pracy WF4 to całkowicie XAML.  Przepływ pracy WF4 wygląda następująco:

 ![Przepływ pracy zakresu korelacji WF4](./media/performance/wf4-correlationscope-workflow.gif)

 Działanie <xref:System.ServiceModel.Activities.Receive> tworzy wystąpienie przepływu pracy.  Wartość przekazana w odebranej wiadomości jest powtarzana w wiadomości odpowiedzi.  Sekwencja po odpowiedzi zawiera pozostałą część przepływu pracy.  W powyższym przypadku wyświetlane jest tylko jedno działanie komentarza.  Liczba działań komentarzy zostanie zmieniona w celu symulacji złożoności przepływu pracy.  Działanie komentarza jest odpowiednikiem WF3, <xref:System.Workflow.Activities.CodeActivity> który wykonuje żadnej pracy. Aby uzyskać więcej informacji na temat działania komentarz, zobacz sekcję "Porównanie wydajności na poziomie składnika" wcześniej w tym artykule.

##### <a name="test-results"></a>Wyniki tekstu

 Zimne i ciepłe opóźnienie usług przepływu pracy WCF:

 ![Wykres kolumnowy przedstawiający zimne i ciepłe opóźnienie dla usług przepływu pracy WCF przy użyciu WF3 i WF4](./media/performance/latency-results-graph.gif)

 Na poprzednim wykresie cold odnosi się do przypadku, <xref:System.ServiceModel.WorkflowServiceHost> gdy nie istnieje istniejący dla danego przepływu pracy.  Innymi słowy opóźnienie zimna jest, gdy przepływ pracy jest używany po raz pierwszy i XOML lub XAML musi zostać skompilowany.  Ogrzanie opóźnienie to czas, aby utworzyć nowe wystąpienie przepływu pracy, gdy typ przepływu pracy został już skompilowany.  Złożoność przepływu pracy sprawia, że bardzo niewiele różnicy w przypadku WF4, ale ma liniowy postęp w przypadku WF3.

#### <a name="correlation-throughput"></a>Przepływność korelacji
 WF4 wprowadza nową funkcję korelacji opartą na zawartości.  WF3 pod warunkiem tylko korelacji kontekstowej.  Korelacji opartej na kontekście można wykonać tylko za pomocą określonych powiązań kanału WCF.  Identyfikator przepływu pracy jest wstawiany do nagłówka wiadomości podczas korzystania z tych powiązań.  Środowisko uruchomieniowe WF3 może identyfikować przepływ pracy tylko przez jego identyfikator.  W połączeniu opartym na zawartości autor przepływu pracy może utworzyć klucz korelacji z odpowiedniego fragmentu danych, takiego jak numer konta lub identyfikator klienta.

 Korelacja oparta na kontekście ma przewagę wydajności, ponieważ klucz korelacji znajduje się w nagłówku wiadomości.  Klucz można odczytać z wiadomości bez de-serializacji/kopiowania wiadomości.  W korelacji opartej na zawartości klucz korelacji jest przechowywany w treści wiadomości.  Wyrażenie XPath jest używane do lokalizowania klucza.  Koszt tego dodatkowego przetwarzania zależy od rozmiaru wiadomości, głębokości klucza w treści i liczby kluczy.  Ten test porównuje korelacji kontekstu i zawartości, a także pokazuje spadek wydajności podczas korzystania z wielu kluczy.

#### <a name="environment-setup"></a>Konfigurowanie środowiska
![Konfiguracja środowiska do testu wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

#### <a name="test-setup"></a>Ustawienia testu
![Test przepływu przepływności korelacji](./media/performance/correlation-throughput-workflow.gif "Konfiguracja testu przepływu przepływności korelacji")

 Poprzedni przepływ pracy jest taki sam, który jest używany w sekcji [Trwałość.](#persistence) Dla testów korelacji bez trwałości, nie ma dostawcy trwałości zainstalowane w czasie wykonywania. Korelacja występuje w dwóch miejscach: CreateOrder i CompleteOrder.

#### <a name="test-results"></a>Wyniki tekstu
![Przepływność korelacji](./media/performance/correlation-throughput-graph.gif "Wykres przepływności korelacji")

 Ten wykres pokazuje spadek wydajności w miarę zwiększania liczby kluczy używanych w korelacji opartej na zawartości.  Podobieństwo w krzywych między TCP i HTTP wskazuje obciążenie związane z tymi protokołami.

#### <a name="correlation-with-persistence"></a>Korelacja z trwałością
 W przypadku utrwalonego przepływu pracy ciśnienie procesora CPU z korelacji opartej na zawartości przesuwa się ze środowiska wykonawczego przepływu pracy do bazy danych SQL.  Procedury przechowywane w dostawcy trwałości SQL wykonać pracę dopasowania kluczy, aby zlokalizować odpowiedni przepływ pracy.

 ![Wykres liniowy przedstawiający wyniki korelacji i trwałości](./media/performance/correlation-persistence-graph.gif)

 Korelacja oparta na kontekście jest nadal szybsza niż korelacja oparta na zawartości.  Jednak różnica jest mniej wyraźna, ponieważ trwałość ma większy wpływ na wydajność niż korelacja.

### <a name="complex-workflow-throughput"></a>Przepływność złożonego przepływu pracy
 Złożoność przepływu pracy nie jest mierzona tylko przez liczbę działań.  Zajęcia kompozytowe mogą zawierać wiele dzieci, a te dzieci mogą być również zajęciami złożonymi.  Wraz ze wzrostem liczby poziomów zagnieżdżania zwiększa się liczba działań, które mogą być obecnie w stanie wykonywania i liczba zmiennych, które mogą być w stanie.  Ten test porównuje przepływność między WF3 i WF4 podczas wykonywania złożonych przepływów pracy.

### <a name="test-setup"></a>Ustawienia testu
 Testy te zostały przeprowadzone na komputerze 4-krotnym Intel Xeon X5355 @ 2.66GHz z 4 GB pamięci RAM z systemem Windows Server 2008 x64.  Kod testowy jest uruchamiany w jednym procesie z jednym wątkiem na rdzeń, aby osiągnąć 100% wykorzystania procesora CPU.

 Przepływy pracy generowane dla tego testu mają dwie główne zmienne: głębokość i liczbę działań w każdej sekwencji.  Każdy poziom głębokości zawiera działanie równoległe, podczas gdy pętla, decyzje, przypisania i sekwencje.  W projektancie WF4 na zdjęciu poniżej, wykres blokowy najwyższego poziomu jest na zdjęciu.  Każde działanie schematu blokowego przypomina główny schemat blokowy.  Może być pomocne, aby myśleć o fraktalne podczas picturing tego przepływu pracy, gdzie głębokość jest ograniczona do parametrów testu.

 Liczba działań w danym teście jest określana przez głębokość i liczbę działań na sekwencję.  Następujące równanie oblicza liczbę działań w teście WF4:

 ![Równanie do obliczania liczby działań](./media/performance/number-activities-equation.gif)

 Liczba aktywności testu WF3 może być obliczona przy nieznacznie innym równaniu ze względu na dodatkową sekwencję:

 ![Równanie do obliczania liczby działań WF3](./media/performance/wf3-number-activities-equation.gif)

 Gdzie d jest głębokość i a jest liczba działań na sekwencję.  Logika leżąca u podstaw tych równań polega na tym, że pierwsza stała, pomnożona przez a, jest liczbą sekwencji, a drugą stałą jest statyczną liczbą działań na bieżącym poziomie.  Istnieją trzy działania podrzędne schematu blokowego w każdym schematze blokowym.  Na dolnym poziomie głębokości te schematy blokowe są puste, ale na innych poziomach są kopiami głównego schematu blokowego.  Liczba działań w definicji przepływu pracy każdej odmiany testu jest wskazana w poniższej tabeli:

 ![Tabela, która pokazuje liczbę działań używanych w każdym teście](./media/performance/workflow-variation-compare-table.gif)

 Liczba działań w definicji przepływu pracy gwałtownie wzrasta z każdym poziomem głębokości.  Ale tylko jedna ścieżka na punkt decyzji jest wykonywana w danym wystąpieniu przepływu pracy, więc wykonywany jest tylko niewielki podzbiór rzeczywistych działań.

 ![Schemat blokowy złożonego przepływu pracy przepływności](./media/performance/complex-workflow-throughput-workflow.gif)

 Dla WF3 utworzono równoważny przepływ pracy. Projektant WF3 pokazuje cały przepływ pracy w obszarze projektowania zamiast zagnieżdżania, dlatego jest zbyt duży, aby wyświetlić w tym temacie. Fragment kodu przepływu pracy jest pokazany poniżej.

 ![Fragment schematu blokowego przepływu pracy WF3](./media/performance/wf3-workflow-snippet.gif)

 Aby wykonywać zagnieżdżanie w skrajnym przypadku, inny przepływ pracy, który jest częścią tego testu używa 100 sekwencji zagnieżdżonych.  W najbardziej wewnętrznej sekwencji `Comment` <xref:System.Workflow.Activities.CodeActivity>jest pojedynczy lub .

 ![Schemat blokowy sekwencji zagnieżdżonej](./media/performance/nested-sequence-workflow.gif)

 Śledzenie i trwałość nie są używane jako część tego testu.

### <a name="test-results"></a>Wyniki tekstu
 ![Wykres kolumnowy z wynikami wydajności przepływności](./media/performance/throughput-performance-results.gif)

 Nawet w przypadku złożonych przepływów pracy z dużą głębią i dużą liczbą działań wyniki wydajności są zgodne z innymi liczbami przepływności pokazanymi wcześniej w tym artykule.  Przepustowość WF4 jest rzędy wielkości szybciej i musi być porównywany w skali logarytmicznej.

### <a name="memory"></a>Memory (Pamięć)
 Obciążenie pamięcią programu Windows Workflow Foundation jest mierzone w dwóch kluczowych obszarach: złożoności przepływu pracy i liczbie definicji przepływu pracy.  Pomiary pamięci zostały wykonane na 64-bitowej stacji roboczej systemu Windows 7.  Istnieje wiele sposobów uzyskania pomiaru rozmiaru zestawu roboczego, takiego jak monitorowanie liczników wydajności, sondowanie Environment.WorkingSet lub użycie narzędzia takiego jak VMMap dostępnego w [VMMap](/sysinternals/downloads/vmmap). W celu uzyskania i weryfikacji wyników każdego testu wykorzystano kombinację metod.

### <a name="workflow-complexity-test"></a>Test złożoności przepływu pracy
 Test złożoności przepływu pracy mierzy różnicę zestawu roboczego na podstawie złożoności przepływu pracy.  Oprócz złożonych przepływów pracy używanych w poprzedniej sekcji, nowe odmiany są dodawane w celu uwzględnienia dwóch podstawowych przypadków: pojedynczego przepływu pracy działania i sekwencji z 1000 działań.  W przypadku tych testów przepływy pracy są inicjowane i wykonywane do zakończenia w pojedynczej pętli szeregowej przez okres jednej minuty.  Każda odmiana testu jest uruchamiana trzy razy, a zarejestrowane dane są średnią z tych trzech przebiegów.

 Dwa nowe testy podstawowe mają przepływy pracy, które wyglądają jak te pokazane poniżej:

 ![Złożony przepływ pracy zarówno dla WF3, jak i WF4](./media/performance/complex-workflow-wf3-wf4.gif)

 W przepływie pracy WF3 <xref:System.Workflow.Activities.CodeActivity> pokazano powyżej, puste działania są używane.  Przepływ pracy WF4 powyżej `Comment` używa działań.  Działanie `Comment` zostało opisane w sekcji Porównania wydajności na poziomie składnika wcześniej w tym artykule.

 ![Wykres kolumnowy przedstawiający złożone użycie pamięci przepływu pracy dla przepływów pracy WF3 i WF4](./media/performance/complex-memory-usage-wf3-wf4.gif)

 Jednym z wyraźnych trendów, które należy zauważyć na tym wykresie jest to, że zagnieżdżanie ma stosunkowo minimalny wpływ na użycie pamięci w WF3 i WF4.  Najbardziej znaczący wpływ na pamięć pochodzi z liczby działań w danym przepływie pracy.  Biorąc pod uwagę dane z sekwencji 1000, złożonej głębokości 5 sekwencji 5 i złożonej głębokości 7 sekwencji 1 odmian, jest oczywiste, że jak liczba działań wchodzi w tysiące, wzrost użycia pamięci staje się bardziej zauważalne.  W skrajnym przypadku (głębokość 7 sekwencji 1), gdzie istnieją ~ 29K działań, WF4 używa prawie 79% mniej pamięci niż WF3.

### <a name="multiple-workflow-definitions-test"></a>Test wielu definicji przepływu pracy
 Pomiar pamięci na definicję przepływu pracy jest podzielony na dwa różne testy ze względu na dostępne opcje hostingu przepływów pracy w WF3 i WF4.  Testy są uruchamiane w inny sposób niż test złożoności przepływu pracy, w tym danego przepływu pracy jest wystąpienie i wykonywane tylko raz na definicję.  Jest to spowodowane definicją przepływu pracy i jego hosta pozostają w pamięci przez cały okres istnienia AppDomain.  Pamięć używana przez uruchomienie danego wystąpienia przepływu pracy powinny być czyszczone podczas wyrzucania elementów bezużytecznych.  Wskazówki dotyczące migracji dla WF4 zawiera bardziej szczegółowe informacje na temat opcji hostingu. Aby uzyskać więcej informacji, zobacz [WF Migration Cookbook: Workflow Hosting](migration-guidance.md).

 Tworzenie wielu definicji przepływu pracy dla testu definicji przepływu pracy można wykonać na kilka sposobów.  Na przykład można użyć generowania kodu, aby utworzyć zestaw 1000 przepływów pracy, które są identyczne, z wyjątkiem nazwy i zapisać każdy z tych przepływów pracy w oddzielnych plikach.  Takie podejście zostało podjęte w przypadku testu hostowanego przez konsolę.  W WF3 <xref:System.Workflow.Runtime.WorkflowRuntime> klasa została użyta do uruchomienia definicji przepływu pracy.  WF4 można użyć <xref:System.Activities.WorkflowApplication> do utworzenia wystąpienia pojedynczego <xref:System.Activities.WorkflowInvoker> przepływu pracy lub bezpośrednio użyć do uruchomienia działania, tak jakby było wywołanie metody.  <xref:System.Activities.WorkflowApplication>jest gospodarzem pojedynczego wystąpienia przepływu pracy i <xref:System.Workflow.Runtime.WorkflowRuntime> ma bliższą parzystość funkcji, aby była używana w tym teście.

 Podczas hostingu przepływów pracy w iis <xref:System.Web.Hosting.VirtualPathProvider> można użyć <xref:System.ServiceModel.WorkflowServiceHost> a, aby utworzyć nowy zamiast generowania wszystkich plików XAMLX lub XOML.  Obsługuje <xref:System.Web.Hosting.VirtualPathProvider> żądanie przychodzące i odpowiada za pomocą "pliku wirtualnego", który można załadować z bazy danych lub, w tym przypadku, generowane na bieżąco.  Dlatego nie jest konieczne tworzenie 1000 plików fizycznych.

 Definicje przepływu pracy używane w teście konsoli były prostymi sekwencyjnymi przepływami pracy z pojedynczym działaniem.  Pojedyncze działanie było <xref:System.Workflow.Activities.CodeActivity> puste dla sprawy WF3 i `Comment` działania dla sprawy WF4.  Przypadek hostowany przez usługi IIS używał przepływów pracy, które rozpoczynają się od otrzymania wiadomości, a kończą od wysłania odpowiedzi:

Na poniższej ilustracji przedstawiono przepływ pracy WF3 z receiveactivity i przepływ pracy WF4 ze wzorcem żądania/odpowiedzi:

 ![Usługi przepływu pracy w WF3 i WF4](./media/performance/workflow-receive-activity.gif)

 W poniższej tabeli przedstawiono różnicę w zestawie roboczym między definicją pojedynczego przepływu pracy a definicjami 1001:

|Opcje hostingu|WF3 Zestaw roboczy Delta|Zestaw roboczy WF4 Delta|
|---------------------|---------------------------|---------------------------|
|Przepływy pracy hostowane w aplikacji konsoli|18 MB|9 MB|
|Usługi hostowanego przepływu pracy usług IIS|446 MB|364 MB|

 Hosting definicji przepływu pracy w usługach IIS <xref:System.ServiceModel.WorkflowServiceHost>zużywa znacznie więcej pamięci ze względu na , szczegółowe artefakty usługi WCF i logiki przetwarzania wiadomości skojarzone z hostem.

 W przypadku hostingu konsoli w WF3 przepływy pracy zostały zaimplementowane w kodzie zamiast XOML.  W WF4 domyślnym ustawieniem jest użycie xaml.  Kod XAML jest przechowywany jako osadzony zasób w zestawie i kompilowany w czasie wykonywania w celu zapewnienia implementacji przepływu pracy.  Istnieje pewne obciążenie związane z tym procesem.  Aby dokonać uczciwego porównania między WF3 i WF4, zamiast XAML użyto zakodowanych przepływów pracy.  Poniżej przedstawiono przykład jednego z przepływów pracy WF4:

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

 Istnieje wiele innych czynników, które mogą mieć wpływ na zużycie pamięci. Ta sama rada dla wszystkich zarządzanych programów nadal ma zastosowanie.  W środowiskach hostowanych usługami <xref:System.ServiceModel.WorkflowServiceHost> IIS obiekt utworzony dla definicji przepływu pracy pozostaje w pamięci do momentu odtworzenia puli aplikacji.  Należy o tym pamiętać podczas pisania rozszerzeń.  Ponadto najlepiej jest unikać zmiennych "globalnych" (zmiennych o zakresie do całego przepływu pracy) i ograniczać zakres zmiennych tam, gdzie to możliwe.

## <a name="workflow-runtime-services"></a>Usługi przepływu pracy

### <a name="persistence"></a>Trwałość
 WF3 i WF4 zarówno statek z dostawcą trwałości SQL.  Dostawca trwałości SQL WF3 jest prostą implementacją, która serializuje wystąpienie przepływu pracy i przechowuje je w obiekcie blob.  Z tego powodu wydajność tego dostawcy zależy w dużej mierze od rozmiaru wystąpienia przepływu pracy.  W WF3 rozmiar wystąpienia może wzrosnąć z wielu powodów, jak zostało omówione wcześniej w tym dokumencie.  Wielu klientów nie chce używać domyślnego dostawcy trwałości SQL, ponieważ przechowywanie wystąpienia szeregowego w bazie danych nie daje wglądu w stan przepływu pracy.  Aby znaleźć określonego przepływu pracy bez znajomości identyfikator przepływu pracy, trzeba by deserialize każdego utrwalonego wystąpienia i zbadać zawartość.  Wielu programistów woli pisać własne dostawców trwałości, aby pokonać tę przeszkodę.

 Dostawca trwałości SQL WF4 próbował rozwiązać niektóre z tych problemów.  Tabele trwałości uwidaczniają pewne informacje, takie jak aktywne zakładki i właściwości, które można promować.  Nowa funkcja korelacji oparta na zawartości w WF4 nie będzie działać dobrze przy użyciu metody trwałości SQL WF3, co spowodowało pewne zmiany w organizacji wystąpienia utrwalonego przepływu pracy.  To sprawia, że zadanie dostawcy trwałości bardziej złożone i stawia dodatkowy nacisk na bazie danych.

### <a name="environment-setup"></a>Konfigurowanie środowiska
![Konfiguracja środowiska do testu wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

### <a name="test-setup"></a>Ustawienia testu
 Nawet z ulepszonym zestawem funkcji i lepszą obsługą współbieżności dostawca trwałości SQL w WF4 jest szybszy niż dostawca w WF3.  Aby to zaprezentować, dwa przepływy pracy, które wykonują zasadniczo te same operacje w WF3 i WF4 są porównywane poniżej.

 ![Przepływ pracy trwałości w WF3 po lewej i WF4 po prawej](./media/performance/persist-workflow-wf3-wf4.gif)

 Oba przepływy pracy są tworzone przez odebraną wiadomość.  Po wysłaniu początkowej odpowiedzi przepływ pracy jest utrwalony.  W przypadku WF3 puste <xref:System.Workflow.ComponentModel.TransactionScopeActivity> jest używany do inicjowania trwałości.  To samo można osiągnąć w WF3, oznaczając działanie jako "utrzymują się na zamknięciu".  Drugi, skorelowany komunikat kończy przepływ pracy.  Przepływy pracy są utrwalone, ale nie zwalniane.

### <a name="test-results"></a>Wyniki tekstu
 ![Wykres kolumnowy przedstawiający trwałość przepływności](./media/performance/throughput-persistence-graph.gif)

 Gdy transport między warstwą klienta i środkowej jest HTTP, trwałość w WF4 pokazuje poprawę 2,6 razy.  Transport TCP zwiększa ten współczynnik do 3,0 razy.  We wszystkich przypadkach wykorzystanie procesora CPU w warstwie środkowej wynosi 98% lub więcej.  Powodem, dla którego przepływność WF4 jest większa, jest szybsze środowisko wykonawcze przepływu pracy.  Rozmiar wystąpienia serializowanego jest niski dla obu przypadków i nie jest głównym elementem przyczyniającym się w tej sytuacji.

 Przepływy pracy WF3 i WF4 w tym teście używają działania, aby jawnie wskazać, kiedy powinna wystąpić trwałość.  Ma to zaletę utrwalania przepływu pracy bez zwalniania go.  W WF3 jest również możliwe do <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> utrwalenia przy użyciu funkcji, ale to zwalnia wystąpienie przepływu pracy z pamięci.  Jeśli deweloper przy użyciu WF3 chce upewnić się, że przepływ pracy utrzymuje się w niektórych punktach, muszą zmienić definicję przepływu pracy lub zapłacić koszt zwalniania i ponownego ładowania wystąpienia przepływu pracy.  Nowa funkcja w WF4 umożliwia utrzymywanie się <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>bez rozładunku: .  Ta funkcja umożliwia wystąpienie przepływu pracy do utrwalenia na <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> bezczynności, ale pozostanie w pamięci, dopóki próg zostanie osiągnięty lub wykonanie zostanie wznowione.

 Należy zauważyć, że dostawca trwałości SQL WF4 wykonuje więcej pracy w warstwie bazy danych.  Baza danych SQL może stać się wąskim gardłem, dlatego ważne jest, aby monitorować użycie procesora i dysku.  Podczas testowania wydajności aplikacji przepływu pracy należy dołączyć następujące liczniki wydajności z bazy danych SQL:

- Fizyczny\\dysk twardy %Czas odczytu dysku

- Fizyczny\\dysk % czasu dysku

- Fizyczny\\dysk procentowy czas zapisu dysku

- PhysicalDisk\\% Średnia długość kolejki dysku

- PhysicalDisk\Średnia długość kolejki odczytu dysku

- PhysicalDisk\Średnia długość kolejki zapisu dysku

- Dysk fizyczny\Bieżąca długość kolejki dysku

- Procesor\\— % czasu procesora

- SERWER SQL: Zatrzaski\Średni czas oczekiwania na zatrzask (ms)

- SERWER SQL: Zatrzaski\Zatrzask oczekiwania/s

### <a name="tracking"></a>Śledzenie
 Śledzenie przepływu pracy może służyć do śledzenia postępu przepływu pracy.  Informacje zawarte w zdarzeniach śledzenia są określane przez profil śledzenia.  Im bardziej złożony jest profil śledzenia, tym droższe staje się śledzenie.

 WF3 dostarczane z usługą śledzenia opartą na języku SQL.  Ta usługa może działać w trybach wsadowych i nieprzemierowanych.  W trybie niewymiernym zdarzenia śledzenia są zapisywane bezpośrednio do bazy danych.  W trybie wsadowym zdarzenia śledzenia są zbierane w tej samej partii co stan wystąpienia przepływu pracy.  Tryb wsadowy ma najlepszą wydajność dla najszerszego zakresu projektów przepływu pracy.  Jednak przetwarzanie wsadowe może mieć negatywny wpływ na wydajność, jeśli przepływ pracy uruchamia wiele działań bez utrwalania i te działania są śledzone.  Często zdarza się to w pętli i najlepszym sposobem uniknięcia tego scenariusza jest zaprojektowanie dużych pętli, aby zawierały punkt trwałości.  Wprowadzenie punktu trwałości do pętli może negatywnie wpłynąć na wydajność, więc ważne jest, aby zmierzyć koszty każdego z nich i wymyślić równowagę.

 WF4 nie jest dostarczany z usługą śledzenia SQL.  Rejestrowanie informacji śledzenia do bazy danych SQL mogą być obsługiwane lepiej z serwera aplikacji, a nie wbudowane w programie .NET Framework. W związku z tym śledzenie SQL jest teraz obsługiwane przez AppFabric.  Dostawca śledzenia out-of-the-box w WF4 jest oparty na śledzenie zdarzeń dla systemu Windows (ETW).

 ETW to system zdarzeń na poziomie jądra o małym opóźnieniu wbudowany w system Windows.  Używa modelu dostawcy/konsumenta, który umożliwia poniesienie kary za śledzenie zdarzeń tylko wtedy, gdy faktycznie istnieje konsument.  Oprócz zdarzeń jądra, takich jak procesor, dysk, pamięć i użycie sieci, wiele aplikacji wykorzystuje również ETW.  Zdarzenia ETW są bardziej wydajne niż liczniki wydajności, w tym zdarzenia można dostosować do aplikacji.  Zdarzenie może zawierać tekst, taki jak identyfikator przepływu pracy lub komunikat informacyjny.  Ponadto zdarzenia są klasyfikowane za pomocą masek bitowych, dzięki czemu użycie określonego podzbioru zdarzeń będzie miało mniejszy wpływ na wydajność niż przechwytywanie wszystkich zdarzeń.

 Korzyści z podejścia przy użyciu ETW do śledzenia zamiast SQL obejmują:

- Zbieranie zdarzeń śledzenia można podzielić na inny proces.  Daje to większą elastyczność w sposobie rejestrowania zdarzeń.

- Zdarzenia śledzenia ETW są łatwo łączone ze zdarzeniami WCF ETW lub innymi dostawcami ETW, takimi jak SQL Server lub dostawca jądra.

- Autorzy przepływu pracy nie trzeba zmieniać przepływu pracy, aby lepiej działać z określonej implementacji śledzenia, takich jak WF3 SQL śledzenia usługi wsadowego trybu.

- Administrator może włączyć lub wyłączyć śledzenie bez recyklingu procesu hosta.

 Korzyści z wydajności śledzenia ETW są wadą.  Zdarzenia ETW mogą zostać utracone, jeśli system znajduje się pod silną presją zasobów.  Przetwarzanie zdarzeń nie ma na celu zablokowania normalnego wykonywania programu i dlatego nie ma gwarancji, że wszystkie zdarzenia ETW będą transmitowane do ich subskrybentów.  To sprawia, że śledzenie ETW doskonale nadaje się do monitorowania kondycji, ale nie nadaje się do inspekcji.

 Chociaż WF4 nie ma dostawcy śledzenia SQL, AppFabric nie.  AppFabric's SQL tracking podejście jest subskrybować zdarzenia ETW z usługi systemu Windows, która partii zdarzeń i zapisuje je do tabeli SQL przeznaczone do szybkiego wstawienia.  Oddzielne zadanie opróżnia dane z tej tabeli i przekształca je w tabele raportowania, które można wyświetlić na pulpicie nawigacyjnym AppFabric.  Oznacza to, że partia zdarzeń śledzenia jest obsługiwana niezależnie od przepływu pracy, z których pochodzi i dlatego nie musi czekać na punkt trwałości przed zarejestrowaniem.

 Zdarzenia ETW mogą być rejestrowane za pomocą narzędzi, takich jak logman lub xperf.  Kompaktowy plik ETL można przeglądać za pomocą narzędzia, takiego jak xperfview lub konwertować na bardziej czytelny format, taki jak XML, z tracerpt.  W WF3 jedyną opcją pobierania śledzenia zdarzeń bez bazy danych SQL jest utworzenie niestandardowej usługi śledzenia. Aby uzyskać więcej informacji na temat ETW, zobacz [Usługi WCF i śledzenie zdarzeń dla systemu Windows](../wcf/samples/wcf-services-and-event-tracing-for-windows.md) i śledzenie zdarzeń — [aplikacje systemu Windows](/windows/desktop/etw/event-tracing-portal).

 Włączenie śledzenia przepływu pracy wpłynie na wydajność w różnym stopniu.  Poniższy benchmark używa narzędzia logman do korzystania ze zdarzeń śledzenia ETW i rejestrowania ich w pliku ETL.  Koszt śledzenia SQL w AppFabric nie jest w zakresie tego artykułu.  Podstawowy profil śledzenia, również używany w AppFabric, jest pokazany w tym benchmarku.  Uwzględniono również koszt śledzenia tylko zdarzeń monitorowania kondycji.  Zdarzenia te są przydatne do rozwiązywania problemów i określania średniej przepływności systemu.

### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Konfiguracja środowiska do testu wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Wyniki tekstu

 ![Wykres kolumnowy przedstawiający koszty śledzenia przepływu pracy](./media/performance/workflow-tracking-costs.gif)

 Monitorowanie kondycji ma około 3% wpływ na przepustowość.  Koszt profilu podstawowego wynosi około 8%.

## <a name="interop"></a>Interop
 WF4 jest prawie pełne [!INCLUDE[wf1](../../../includes/wf1-md.md)] przepisanie i dlatego WF3 przepływów pracy i działań nie są bezpośrednio zgodne z WF4.  Wielu klientów, którzy przyjęli Windows Workflow Foundation wcześnie będzie miał w domu lub innych firm definicji przepływu pracy i działań niestandardowych dla WF3.  Jednym ze sposobów ułatwienia przejścia do WF4 jest użycie działania Interop, które można wykonywać działania WF3 z poziomu przepływu pracy WF4.  Zaleca się, <xref:System.Activities.Statements.Interop> aby działanie było używane tylko wtedy, gdy jest to konieczne. Aby uzyskać więcej informacji na temat migracji do WF4, zapoznaj się z [wytycznymi dotyczącymi migracji WF4](migration-guidance.md).

### <a name="environment-setup"></a>Konfigurowanie środowiska
 ![Konfiguracja środowiska do testu wydajności przepływu pracy](./media/performance/performance-test-environment.gif)

### <a name="test-results"></a>Wyniki tekstu

W poniższej tabeli przedstawiono wyniki uruchamiania przepływu pracy zawierającego pięć działań w sekwencji w różnych konfiguracjach.

|Testowanie|Przepływność (przepływy pracy/s)|
|----------|-----------------------------------|
|Sekwencja WF3 w czasie wykonywania WF3|1,576|
|Sekwencja WF3 w czasie wykonywania WF4 przy użyciu interop|2,745|
|Sekwencja WF4|153,582|

 Istnieje znaczny wzrost wydajności przy użyciu Interop na prostej WF3.  Jednak w porównaniu z działalnością WF4 wzrost ten jest nieznaczny.

## <a name="summary"></a>Podsumowanie
 Duże inwestycje w wyniki dla WF4 opłaciły się w wielu kluczowych obszarach.  Wydajność poszczególnych składników przepływu pracy jest w niektórych przypadkach setki razy szybsza w [!INCLUDE[wf1](../../../includes/wf1-md.md)] WF4 w porównaniu do WF3 ze względu na szczuplejsze środowisko uruchomieniowe.  Numery opóźnień są znacznie lepsze, jak również.  Oznacza to, że [!INCLUDE[wf1](../../../includes/wf1-md.md)] kara za wykonanie za pomocą, w przeciwieństwie do ręcznego kodowania [!INCLUDE[wf1](../../../includes/wf1-md.md)]usług Aranżacji WCF jest bardzo mała, biorąc pod uwagę dodatkowe korzyści z używania .  Wydajność trwałości wzrosła o współczynnik 2,5 - 3,0.  Monitorowanie kondycji za pomocą śledzenia przepływu pracy ma teraz bardzo mało narzutów.  Kompleksowy zestaw przewodników migracji są dostępne dla tych, którzy rozważają przejście z WF3 do WF4.  Wszystko to powinno sprawić, że WF4 będzie atrakcyjną opcją do pisania złożonych aplikacji.
