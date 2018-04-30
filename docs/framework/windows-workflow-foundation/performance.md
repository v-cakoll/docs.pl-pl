---
title: Windows Workflow Foundation 4 wydajności
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 67d2b3e8-3777-49f8-9084-abbb33b5a766
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 4db761d2e6ba0231cb83d4ef5d1ee663c99178c5
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/30/2018
---
# <a name="windows-workflow-foundation-4-performance"></a>Windows Workflow Foundation 4 wydajności
Dustin Metzgar  
  
 Wenlong Dong  
  
 We wrześniu 2010 Microsoft Corporation  
  
 Microsoft [!INCLUDE[netfx40_long](../../../includes/netfx40-long-md.md)] zawiera znaczne zmiany z systemu Windows Workflow Foundation (WF) z dużych inwestycji w wydajności.  Ta nowa wersja wprowadza znaczących zmian z poprzednich wersji [!INCLUDE[wf1](../../../includes/wf1-md.md)] dostarczonego w ramach programu .NET Framework 3.0 i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Została zmieniona z rdzenia modelu programowania, środowiska uruchomieniowego i narzędzi, aby znacznie zwiększyć wydajność i użyteczność. W tym temacie przedstawiono ważne charakterystyki tych zmian i porównuje je z tych funkcji w poprzedniej wersji.  
  
 Zwiększa wydajność składników przepływu pracy o rzędów między WF3 i WF4.  To pozostawia odstęp między kodowane ręcznie [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] usług i [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług przepływu pracy będzie bardzo mała.  Opóźnienie przepływu pracy została znacząco zmniejszona w WF4.  Zwiększa wydajność trwałości przez współczynnik 2.5 3.0.  Monitorowanie kondycji za pomocą śledzenia przepływu pracy ma znacznie mniejsze koszty.  Są one istotne powody migrację do lub przyjąć WF4 w aplikacji.  
  
## <a name="terminology"></a>Terminologia  
 Wersja [!INCLUDE[wf1](../../../includes/wf1-md.md)] wprowadzone w systemie [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] zostaną określone jako WF4 w pozostałej części tego tematu.  [!INCLUDE[wf1](../../../includes/wf1-md.md)] został wprowadzony w .net 3.0 i ma kilka drobne poprawki za pośrednictwem [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] z dodatkiem SP1. [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Wersji programu Workflow Foundation zostaną określone jako WF3 w pozostałej części tego tematu. WF3 jest dostarczany w [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)] side-by-side z WF4. Aby uzyskać więcej informacji na temat migrowania artefakty WF3 do WF4 zobacz: [Przewodnik migracji systemu Windows Workflow Foundation 4](http://go.microsoft.com/fwlink/?LinkID=153313)  
  
 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] jest firmy Microsoft ujednolicony model programowania do tworzenia aplikacji korzystających z usług. Została wprowadzona jako część .net 3.0 oraz WF3, a teraz jest jednym z kluczowych składników [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
 Windows Server AppFabric to zestaw zintegrowanych technologii, które ułatwiają tworzenie, skalowanie i zarządzanie nimi w sieci Web i aplikacji złożonych, które w środowisku usług IIS. Udostępnia narzędzia do monitorowania i zarządzania usługami i przepływami pracy. Aby uzyskać więcej informacji, zobacz [systemu Windows Server AppFabric](http://msdn.microsoft.com/windowsserver/ee695849.aspx)  
  
## <a name="goals"></a>Cele  
 Celem tego tematu jest pokazanie charakterystyki wydajności WF4 z danymi mierzone dla różnych scenariuszy. Dostępne są także szczegółowe porównanie WF4 WF3 i zawiera doskonały ulepszeń, które zostały wprowadzone w tej nowej wersji. Scenariusze i dane podane w tym artykule określenie podstawowego koszt różnych aspektów WF4 i WF3. Te dane są przydatne w zrozumienia charakterystyki wydajności WF4 i mogą być pomocne w planowanie migracji z WF3 do WF4 lub przy użyciu WF4 w projektowanie aplikacji. Jednak należy zachować ostrożność w wnioski wyciągnięte z danych przedstawionych w tym artykule. Wydajność aplikacji złożonych przepływu pracy jest wysoce zależne implementowania przepływu pracy i różnych składników są zintegrowane. Jeden musi pomiarów każdej aplikacji, aby określić charakterystyki wydajności tej aplikacji.  
  
## <a name="overview-of-wf4-performance-enhancements"></a>Omówienie WF4 ulepszenia wydajności  
 WF4 dokładnie został opracowany i jest implementowana przy użyciu wysokiej wydajności i skalowalności, które są opisane w poniższych sekcjach.  
  
### <a name="wf-runtime"></a>Środowisko uruchomieniowe WF  
 Stanowiącej podstawę [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowisko wykonawcze jest asynchroniczne harmonogramu, którego wykonanie działań w przepływie pracy. Zapewnia wydajność, środowisku przewidywalną wykonywania działań. Środowisko zawiera kontrakt dobrze zdefiniowany dla wykonywania, kontynuacji ukończenia, anulowania, wyjątków i przewidywalne modelu wątkowości.  
  
 W odróżnieniu od WF3 WF4 runtime ma efektywniejsze harmonogramu. Go korzysta z tej samej puli wątków We/Wy używanego do [!INCLUDE[indigo2](../../../includes/indigo2-md.md)], który jest bardzo wydajny w wykonywania umieścić w zadaniu wsadowym elementów roboczych. Kolejki harmonogramu elementu wewnętrznego pracy jest zoptymalizowana pod kątem typowych wzorców użycia. Środowisko uruchomieniowe WF4 zarządza także stanów wykonania w sposób bardzo lekki z minimalnym synchronizacji i obsługi logiki, podczas gdy WF3 zależy od rejestracji ciężki zdarzenia i wywołanie do przeprowadzenia synchronizacji złożonych przejść stanu zdarzeń.  
  
### <a name="data-storage-and-flow"></a>Magazyn danych i przepływu  
 W WF3, dane skojarzone z działaniem jest modelowana za pośrednictwem właściwości zależności zaimplementowany przez typ <xref:System.Windows.DependencyProperty>. Wzorzec właściwości zależności została wprowadzona w systemie Windows Presentation Foundation (WPF). Ogólnie rzecz biorąc ten wzorzec jest bardzo elastyczne obsługuje powiązanie danych łatwe i inne funkcje interfejsu użytkownika. Wzorzec wymaga jednak właściwości określone jako pola statyczne w definicji przepływu pracy. Zawsze, gdy [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowiska uruchomieniowego Ustawia lub pobiera wartość właściwości, obejmuje ona logiki silnie ważone wyszukiwania.  
  
 WF4 używa Wyczyść dane zakresu logikę do znacznie zwiększyć sposobu obsługi danych w przepływie pracy. Umożliwia oddzielenie od danych przechowywanych w działaniu ze źródła danych, który jest przechodzenia przez granice działania za pomocą dwóch różnych pojęcia: zmienne i argumenty. Przy użyciu wyczyść hierarchiczna zakres dla zmiennych i argumenty "W/Out/InOut", złożoność danych użycia dla działania jest znacznie zmniejszyć i okres istnienia danych jest automatycznie zakres. Działania mają dobrze zdefiniowanego podpisu opisanego przez argumenty. Sprawdzając, czy po prostu działanie można określić oczekuje na odbieranie danych i jakie dane zostaną utworzone przez nią w wyniku działania.  
  
 W WF3 działania zostały zainicjowane, gdy przepływ pracy został utworzony. W przypadku WF 4 działania są inicjowane tylko wtedy, gdy odpowiednie działania są wykonywane. Dzięki temu prostsze cykl działania bez wykonywania operacji inicjowania/Uninitialize po utworzeniu nowego wystąpienia przepływu pracy i w związku z tym osiągnął więcej wydajności  
  
### <a name="control-flow"></a>Przepływ sterowania  
 Tak jak w przypadku dowolnego języka programowania [!INCLUDE[wf1](../../../includes/wf1-md.md)] zapewnia obsługę przepływami sterowania dla definicji przepływu pracy dzięki zastosowaniu zbiór działań przepływu sterowania do sekwencjonowania, pętle, wzorce rozgałęziania i innych. W WF3, gdy to samo działanie musi ponownie uruchomić nowy <xref:System.Workflow.ComponentModel.ActivityExecutionContext> jest tworzony i działania został sklonowany za pośrednictwem ciężki serializacji i deserializacji logiki na podstawie <xref:System.Runtime.Serialization.Formatters.Binary.BinaryFormatter>. Zwykle wydajność iteracyjny kontroli przepływów jest znacznie mniejsza niż wykonywania sekwencję działań.  
  
 WF4 obsługuje to odbywa się zupełnie inaczej. Go przyjmuje szablon działania, tworzy nowy obiekt ActivityInstance i dodaje go do kolejki harmonogramu. Tylko całego tego procesu obejmuje tworzenie obiektów jawne i jest bardzo lekki.  
  
### <a name="asynchronous-programming"></a>Programowanie asynchroniczne  
 Aplikacje zazwyczaj mają lepszą wydajność i skalowalność programowania asynchronicznego długotrwałej operacji blokowania, takich jak We/Wy lub operacji przetwarzania rozproszonego. WF4 zapewnia obsługę asynchroniczną za pośrednictwem podstawowego elementu activity typów <xref:System.Activities.AsyncCodeActivity>, <xref:System.Activities.AsyncCodeActivity%601>. Środowiska uruchomieniowego natywnie obsługuje usługę asynchroniczne działań i w związku z tym można automatycznie umieszcza wystąpienia w strefie no-persist zablokowaniu zaległe asynchroniczne. Niestandardowe działania może pochodzić od tych typów do wykonywania asynchronicznych pracy bez zawierający wątku harmonogramu przepływu pracy i blokuje żadnych działań, które można uruchomić równolegle.  
  
### <a name="messaging"></a>Obsługa wiadomości  
 Początkowo zawierała WF3 bardzo ograniczone komunikatów za pomocą zewnętrznego zdarzenia lub sieci web pomocy technicznej wywołań. W środowisku .net 3.5, przepływy pracy można zaimplementowane jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] klientów lub narażonych jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usług za pośrednictwem <xref:System.Workflow.Activities.SendActivity> i <xref:System.Workflow.Activities.ReceiveActivity>. W WF4, pojęcie opartym na przepływie pracy programowania wiadomości ma zostały wzmocnione za pośrednictwem ścisłej integracji z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] wiadomości logikę do WF.  
  
 W potoku przetwarzania komunikatów ujednoliconego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] w .net 4 pomaga WF4 usług mają znacznie lepszą wydajność i skalowalność niż WF3. WF4 zapewnia także bardziej zaawansowane funkcje obsługi wiadomości obsługę programowania, który modelu złożonego wzorce wymiany wiadomości (MEPs). Deweloperzy mogą używać albo kontraktów typu usługi umożliwia łatwe programowanie lub kontraktów usług wyrażeniami bez typu, aby osiągnąć lepszą wydajność bez płatności kosztów serializacji. Obsługa buforowania za pośrednictwem kanału po stronie klienta <xref:System.ServiceModel.Activities.SendMessageChannelCache> klasy w WF4 ułatwia deweloperom tworzenie aplikacji szybki przy minimalnym wysiłku. Aby uzyskać więcej informacji, zobacz [Zmienianie poziomów współużytkowania pamięci podręcznej dla działań wysyłania](../../../docs/framework/wcf/feature-details/changing-the-cache-sharing-levels-for-send-activities.md).  
  
### <a name="declarative-programming"></a>Programowanie deklaratywne  
 WF4 zapewnia czyste i proste deklaratywne programowania platformę do modelu procesów biznesowych i usług. Model programowania obsługuje w pełni deklaracyjnego kompozycji działań z nie kodu obok, co znacznie upraszcza tworzenie przepływu pracy. W [!INCLUDE[netfx40_short](../../../includes/netfx40-short-md.md)], opartych na języku XAML deklaratywne struktury programistycznej używanej ma zostać unified w jednym zestawie System.Xaml.dll do obsługi WPF i WF.  
  
 W WF4 XAML zapewnia obsługę naprawdę deklaratywne i umożliwia całej definicji przepływu pracy należy zdefiniować w znaczniku XML odwołuje się do działań i typy skompilowane przy użyciu platformy .NET. To było trudne do wykonania w WF3 formatu XOML nie angażując kodem niestandardowej logiki. Nowego stosu XAML w programie .net 4 ma znacznie większą wydajność w serializacji/deserializacji artefaktów przepływu pracy i sprawia, że programowanie deklaratywne bardziej atrakcyjne i stałe.  
  
### <a name="workflow-designer"></a>Projektant przepływu pracy  
 Pełni deklaracyjnego obsługę programowania WF4 nakłada jawnie wyższe wymagania dotyczące wydajności w czasie projektowania dla dużych przepływów pracy. Projektant przepływu pracy w WF4 ma znacznie lepszą skalowalność dla dużych przepływów pracy niż WF3. Z obsługą wirtualizacji interfejsu użytkownika Projektant można łatwo załadować dużych przepływu pracy 1000 działań w ciągu kilku sekund jest praktycznie niemożliwe załadować kilka kilkuset działań przepływu pracy przy użyciu projektanta WF3.  
  
## <a name="component-level-performance-comparisons"></a>Porównanie wydajności na poziomie składników  
 Ta sekcja zawiera dane na bezpośrednie porównanie poszczególne działania w przepływach pracy WF3 i WF4.  Kluczowych obszarach, takich jak trwałości ma więcej poważny wpływ na wydajność niż składniki poszczególnych działań.  Lepsza wydajność programu poszczególnymi składnikami w programie WF4 są ważne, jednak ponieważ składniki programu są teraz szybkie, aby porównać z logiki aranżacji kodowane ręcznie.  Przykładem jest omówiona w następnej sekcji: "Usługa kompozycji scenariusz".  
  
### <a name="environment-setup"></a>Konfigurowanie środowiska  
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
 Rysunku powyżej przedstawiono konfigurację maszyny, używany do pomiaru wydajności na poziomie składników. Pojedynczy serwer i klienci pięć połączone ponad jeden interfejs sieciowy Ethernet 1 GB. Łatwe pomiarów serwer jest skonfigurowany do użycia pojedynczego rdzenia proc/quad dwurdzeniowy serwera z systemem Windows Server 2008 x86. Użycie procesora CPU systemu utrzymywana jest prawie 100%.  
  
### <a name="test-details"></a>Szczegóły testu  
 WF3 <xref:System.Workflow.Activities.CodeActivity> prawdopodobnie jest najprostsza działanie, które mogą być używane w przepływie pracy WF3.  Działanie wywołuje metodę w CodeBehind który programisty przepływu pracy można wprowadzić kod niestandardowy do.  W WF4, nie ma żadnych bezpośrednich analogowy do WF3 <xref:System.Workflow.Activities.CodeActivity> zapewnia te same funkcje.  Należy pamiętać, że istnieje <xref:System.Activities.CodeActivity> podstawowa klasa w WF4, który nie jest powiązana z WF3 <xref:System.Workflow.Activities.CodeActivity>.  Autorzy przepływu pracy są zachęcani do tworzenia niestandardowych działań i tworzenia przepływów pracy XAML — tylko do.  W przypadku testów działania o nazwie `Comment` używany zamiast pustą <xref:System.Workflow.Activities.CodeActivity> w przepływach pracy WF4.  Kod w `Comment` działania ma następującą składnię:  
  
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
  
### <a name="empty-workflow"></a>Pusty przepływu pracy  
 Ten test używa sekwencji przepływu pracy z żadne działania podrzędne.  
  
### <a name="single-activity"></a>Pojedyncze działanie  
 Przepływ pracy jest przepływ pracy sekwencji zawierających jedno działanie podrzędne.  Działanie jest <xref:System.Workflow.Activities.CodeActivity> z żadnego kodu w przypadku WF3 i `Comment` działanie w przypadku WF4.  
  
### <a name="while-with-1000-iterations"></a>Podczas z 1000 iteracji  
 Sekwencyjny przepływ pracy zawiera jeden <xref:System.Activities.Statements.While> działania o jeden element podrzędny działania w pętli, które wykonuje pracę.  
  
### <a name="replicator-compared-to-parallelforeach"></a>W porównaniu do działania ParallelForEach replikatora  
 <xref:System.Workflow.Activities.ReplicatorActivity> w WF3 wykonywanie równoległe i sekwencyjny trybach.  W trybie sekwencyjnych wydajności działania jest podobny do <xref:System.Workflow.Activities.WhileActivity>.  <xref:System.Workflow.Activities.ReplicatorActivity> Jest najbardziej przydatny w przypadku przetwarzania równoległego.  Analogowy WF4 tego jest <xref:System.Activities.Statements.ParallelForEach%601> działania.  
  
 Na poniższym diagramie przedstawiono przepływ używany dla tego testu. Przepływ pracy WF3 jest po lewej stronie i WF4 przepływu pracy jest po prawej stronie.  
  
 ![WF3 Działanie ReplicatorActivity i działania ParallelForEach WF4](../../../docs/framework/windows-workflow-foundation/media/replicatorandparallelforeach.gif "ReplicatorAndParallelForEach")  
  
### <a name="sequential-workflow-with-five-activities"></a>Sekwencyjny przepływ pracy z pięciu działań  
 Ten test jest przeznaczona do Pokaż efekt o kilka działania wykonywane w sekwencji.  Ma pięć działań w sekwencji.  
  
### <a name="transaction-scope"></a>Zakresu transakcji  
 Test zakresu transakcji różni się od innych testów w tym nowe wystąpienie przepływu pracy nie został utworzony dla każdej iteracji.  Zamiast tego przepływu pracy składa się z chwilę zawierający pętli <xref:System.Activities.Statements.TransactionScope> działania, które zawiera pojedyncze działanie, które nie działa.  Uruchom każdej partii 50 iteracji za pośrednictwem while pętli jest liczone jako jedna operacja.  
  
### <a name="compensation"></a>kompensacji  
 Przepływ pracy WF3 ma jednego możliwy do kompensacji działania o nazwie `WorkScope`.  Działanie po prostu implementuje <xref:System.Workflow.ComponentModel.ICompensatableActivity> interfejsu:  
  
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
  
 Obiekty docelowe obsługi błędów `WorkScope` działania. Przepływ pracy WF4 jest równie simplistic.  A <xref:System.Activities.Statements.CompensableActivity> ma treści i obsługi kompensacji.  Jawne compensate jest dalej w sekwencji.  Działanie dotyczące treści i działanie procedury obsługi kompensacji są oba pusty implementacji:  
  
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
  
 ![Przepływy pracy podstawowe kompensacji WF3 i WF](../../../docs/framework/windows-workflow-foundation/media/basiccompensationworkflows.gif "BasicCompensationWorkflows")  
  
 Rysunek 2 — WF3 (po lewej) i przepływów pracy (po prawej) podstawowych kompensacji WF4  
  
### <a name="performance-test-results"></a>Wyniki testów wydajności  
 ![Wyniki testów wydajności](../../../docs/framework/windows-workflow-foundation/media/performancedata.gif "elementu PerformanceData")  
  
 ![Wykres danych testu wydajności](../../../docs/framework/windows-workflow-foundation/media/performancetestchart.gif "PerformanceTestChart")  
  
 Wszystkie testy są mierzone w przepływach pracy na sekundę, z wyjątkiem testu zakresu transakcji.  Jak podano powyżej, [!INCLUDE[wf1](../../../includes/wf1-md.md)] wydajność środowiska uruchomieniowego uległa poprawie w tablicy, zwłaszcza w obszarach, które wymagają wykonania wielu to samo działanie jak while pętli.  
  
## <a name="service-composition-scenario"></a>Usługa kompozycji scenariusza  
 Opisane w poprzedniej sekcji "składnika poziom wydajności porównania" wprowadzono znaczące zmniejszenie obciążenia między WF3 i WF4.  [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi przepływu pracy teraz może dopasować prawie wydajność kodowane ręcznie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi, ale nadal mają korzystać z [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowiska wykonawczego.  Ten scenariusz testu porównuje [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi przed [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi przepływu pracy w WF4.  
  
### <a name="online-store-service"></a>Usługi online magazynu  
 Jedną z możliwości programu Windows Workflow Foundation jest możliwość tworzenia procesy korzystające z kilku usług.  W tym przykładzie jest usługą sklepu, która organizuje zakup dwóch wywołania usługi.  Pierwszym krokiem jest do sprawdzania poprawności kolejności przy użyciu usługi sprawdzania poprawności zamówienia.  Drugim krokiem jest do wypełnienia kolejności przy użyciu usługi magazynu.  
  
 Te dwie usługi wewnętrznej bazy danych usługi sprawdzania poprawności kolejności i magazynu, pozostają takie same, w obu.  Element, który zmienia jest Online usługi magazynu, który wykonuje orchestration.  W przypadku jednego, usługa jest ręcznie zakodowane jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi.  W przypadku usługi są zapisywane jako [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi przepływu pracy w WF4. [!INCLUDE[wf1](../../../includes/wf1-md.md)]-określone funkcje, takie jak śledzenie i trwałości są wyłączone dla tego testu.  
  
### <a name="environment"></a>Środowisko  
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
 Żądania klienta są kierowane do usługi Online magazynu za pośrednictwem protokołu HTTP z wielu komputerów.  Pojedynczy komputer obsługuje wszystkie trzy usługi.  Warstwa transportu między Online usługi magazynu i usługi wewnętrznej bazy danych jest TCP lub HTTP.  Pomiar operacji na sekundę jest oparta na liczbę ukończone `PurchaseOrder` wywołania Online usługi magazynu.  Korzystanie z puli kanału to nowa funkcja dostępna w WF4.  W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] fabrycznej nie podano część tego testu kanału korzystanie z puli, więc kodowane ręcznie wykonania prostego technika buforowania został użyty w Online usługi magazynu.  
  
### <a name="performance"></a>Wydajność  
 ![Wykres wydajności usługi Sklep internetowy](../../../docs/framework/windows-workflow-foundation/media/onlinestoreperfgraph.gif "OnlineStorePerfGraph")  
  
 Łączenie z usługami TCP wewnętrznej bazy danych bez puli kanału [!INCLUDE[wf1](../../../includes/wf1-md.md)] usługi ma wpływ 17.2% przepływności.  Z puli kanału kary wynosi około 23,8%.  W przypadku protokołu HTTP wpływ jest znacznie mniej: % 4.3 bez buforowania i % 8.1 z puli.  Jest również należy pamiętać, że buforowanie kanału zapewnia korzyści bardzo mało przy użyciu protokołu HTTP.  
  
 Gdy istnieje nakłady pracy związane z WF4 środowiska uruchomieniowego w porównaniu z kodowane ręcznie [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi w tym teście należy uważać najgorszym przypadku.  Te dwie usługi wewnętrznej bazy danych, w tym teście zrobić bardzo małego wysiłku.  W przypadku rzeczywistych end-to-end te usługi przeprowadza się bardziej kosztowne operacje, takie jak wywołania bazy danych, co mniej istotny wpływ na wydajność warstwy transportowej.  To plus z zalet funkcji dostępnych w WF4 sprawia, że Workflow Foundation działało wyboru do tworzenia usług aranżacji.  
  
## <a name="key-performance-considerations"></a>Kluczowe zagadnienia dotyczące wydajności  
 Obszary funkcji w tej sekcji, z wyjątkiem interop, zmieniły się znacznie między WF3 i WF4.  Ma to wpływ na projekt aplikacji przepływu pracy, a także wydajności.  
  
#### <a name="workflow-activation-latency"></a>Opóźnienie aktywacji przepływu pracy  
 W [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] aplikacja usługi przepływu pracy, czas oczekiwania na uruchomienie nowego przepływu pracy lub ładowania istniejącego przepływu pracy jest ważne, jak mogą być blokowane.  Przypadek testowy środków hosta WF3 XOML przed WF4 XAMLX hosta w typowy scenariusz.  
  
##### <a name="environment-setup"></a>Konfigurowanie środowiska  
 ![Konfigurowanie środowiska testów opóźnienia i przepływności](../../../docs/framework/windows-workflow-foundation/media/latencyandthroughputenvironment.gif "LatencyAndThroughputEnvironment")  
  
##### <a name="test-setup"></a>Testuj ustawienia  
 W tym scenariuszu, kontakty komputera klienta [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi przepływu pracy przy użyciu kontekstowa korelacji.  Kontekst korelacji wymaga specjalnych kontekst powiązania i używa nagłówka kontekstu lub plik cookie powiązać wiadomości do wystąpienia przepływu pracy poprawne.  Ma ona wydajności korzystać w tym korelacji, więc treść komunikatu musi być analizowana identyfikator znajduje się w nagłówku wiadomości. Aby uzyskać więcej informacji o kontekście korelacji zobacz [korelacja wymiany kontekstu](../../../docs/framework/wcf/feature-details/context-exchange-correlation.md)  
  
 Usługa tworzenia nowego przepływu pracy z żądaniem i Przenieś natychmiastowej reakcji, tak aby pomiar opóźnienia nie obejmuje czas uruchamiania przepływu pracy.  Przepływ pracy WF3 jest XOML z kodem i WF4 przepływu pracy jest całkowicie XAML.  Przepływ pracy WF4 wygląda następująco:  
  
 ![Zakresu korelacji 4 WF](../../../docs/framework/windows-workflow-foundation/media/correlationscopeworkflow.gif "CorrelationScopeWorkflow")  
  
 <xref:System.ServiceModel.Activities.Receive> Działanie tworzy wystąpienie przepływu pracy.  Wartość przekazana odebranej wiadomości jest powtarzana w komunikacie odpowiedzi.  Sekwencja po odpowiedzi zawiera pozostałej części przepływu pracy.  W przypadku powyżej jest wyświetlany tylko jeden komentarz działania.  Liczba działań w komentarz zostanie zmieniona do symulowania złożoności przepływu pracy.  Działanie komentarz jest odpowiednikiem WF3 <xref:System.Workflow.Activities.CodeActivity> który nie wykonuje żadnych operacji. Aby uzyskać więcej informacji o działaniu komentarza zobacz sekcję "porównanie wydajności poziomie składników" w tym artykule.  
  
##### <a name="test-results"></a>Wyniki tekstu  
 ![Wyniki opóźnienia](../../../docs/framework/windows-workflow-foundation/media/latencyresultsgraph.gif "LatencyResultsGraph")  
  
 Rysunek 3 – zimnej i ogrzewać opóźnienie dla usług przepływu pracy WCF  
  
 Na wykresie powyżej chłodni odwołuje się do sytuacji, gdy nie istnieje <xref:System.ServiceModel.WorkflowServiceHost> dla danego przepływu pracy.  Innymi słowy zimnych opóźnienia jest, gdy przepływ pracy jest używany po raz pierwszy i XOML lub XAML musi być kompilowana.  Ciepłych opóźnienie to czas do utworzenia nowego wystąpienia przepływu pracy, gdy już została skompilowana typu przepływu pracy.  Złożoność przepływu pracy sprawia, że bardzo mała różnica w przypadku WF4, ale ma liniowej postępu w przypadku WF3.  
  
#### <a name="correlation-throughput"></a>Przepływność korelacji  
 WF4 wprowadzono nową funkcję korelacji na podstawie zawartości.  WF3 podać tylko na podstawie kontekstu korelacji.  Korelacja na podstawie kontekstu może być wykonana tylko przez określonych [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] powiązania kanału.  Identyfikator przepływu pracy są wstawiane do nagłówka wiadomości, korzystając z tych powiązań.  Środowisko uruchomieniowe WF3 tylko można zidentyfikować przepływu pracy przez jego identyfikator.  Na podstawie zawartości korelacji Autor przepływu pracy umożliwia tworzenie klucza korelacji poza odpowiednich element danych, takich jak numer konta lub odbiorcy identyfikatora. Aby uzyskać więcej informacji na temat na podstawie zawartości korelacji zobacz [zawartości na podstawie korelacji](../../../docs/framework/wcf/feature-details/content-based-correlation.md).  
  
 Kontekstowa korelacji ma korzystać wydajności, w tym klucz korelacji znajduje się w nagłówku wiadomości.  Klucz można odczytać z wiadomość bez dezaktywuje-serialization/komunikat kopiowania.  W zawartości na podstawie korelacji klucz korelacji jest przechowywany w treści wiadomości.  Wyrażenie XPath jest używany do lokalizowania klucza.  Koszt tego dodatkowego przetwarzania zależy od rozmiaru komunikatu głębokość klucza w treści i liczba kluczy.  Ten test porównuje korelacji na podstawie kontekstu i zawartości i zawiera także spadek wydajności, korzystając z wielu kluczy.  
  
#### <a name="environment-setup"></a>Konfigurowanie środowiska  
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
#### <a name="test-setup"></a>Testuj ustawienia  
 ![Korelacji przepływności przepływu pracy Test](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputworkflow.gif "CorrelationThroughputWorkflow")  
  
 Powyższy przepływu pracy jest taka sama jak używane w sekcji "Trwałość" poniżej.  Dla testów korelacji bez trwałości Brak dostawcy trwałości zainstalowany w środowisku wykonawczym.  Korelacji występuje w dwóch miejscach: CreateOrder i CompleteOrder.  
  
#### <a name="test-results"></a>Wyniki tekstu  
 ![Przepływność korelacji](../../../docs/framework/windows-workflow-foundation/media/correlationthroughputgraph.gif "CorrelationThroughputGraph")  
  
 Ten wykres pokazuje spadek wydajności jako liczba kluczy używanych wzrost na podstawie zawartości korelacji.  Podobieństwa między TCP i HTTP krzywych wskazuje obciążenia związanego z tych protokołów.  
  
#### <a name="correlation-with-persistence"></a>Korelacji z trwałości  
 Z utrwalonego przepływu pracy wykorzystanie procesora CPU od na podstawie zawartości korelacji przewiduje ze środowiska uruchomieniowego przepływu pracy z bazą danych SQL.  Procedury składowane SQL dostawcy trwałości pracy zgodnymi kluczami można znaleźć odpowiedniego przepływu pracy.  
  
 ![Wyniki korelacji i trwałości](../../../docs/framework/windows-workflow-foundation/media/correlationandpersistencegraph.gif "CorrelationAndPersistenceGraph")  
  
 Kontekstowa korelacji jest nadal szybsze niż korelacji na podstawie zawartości.  Jednak różnica jest mniejsza Wymowa trwałości, ma więcej wpływ na wydajność niż korelacji.  
  
### <a name="complex-workflow-throughput"></a>Przepływność złożonych przepływów prac  
 Złożoność przepływu pracy nie jest mierzony tylko przez liczbę działań.  Działań złożonych może zawierać wielu elementów podrzędnych i te elementy podrzędne można też działań złożonych.  Jako liczby poziomów zagnieżdżenia rośnie co powoduje liczbę działań, które mogą być obecnie w stanie wykonywania i liczba zmiennych, które mogą być w stanie.  Ten test porównuje przepustowość między WF3 i WF4 podczas wykonywania złożonych przepływów pracy.  
  
### <a name="test-setup"></a>Testuj ustawienia  
 Te testy zostały wykonane na Intel Xeon X5355 @ 2,66 GHz 4 sposób komputera z 4 GB pamięci RAM z systemem Windows Server 2008 x64.  Kod testu jest uruchamiany w ramach jednego procesu o jeden wątek na każdym core do 100% wykorzystanie Procesora.  
  
 Przepływy pracy, generowany dla tego testu ma dwa główne zmiennych: głębokość i liczbę aktywności w poszczególnych sekwencji.  Każdy poziom głębokości zawiera działanie równoległe, podczas pętli, decyzji, przydziały i sekwencji.  W Projektancie WF4 przedstawianych poniżej przedstawiono najwyższego poziomu schematu blokowego.  Każde działanie flowchart podobny głównego schematu blokowego.  Może to być można wyobrazić sobie fraktalowy podczas picturing ten przepływ pracy, której głębokość jest ograniczona do parametrów testu.  
  
 Liczba działań w danym testu zależy od głębokości i liczba działań w sekwencji.  Następujące równanie oblicza liczbę działań w teście WF4:  
  
 ![Równości można obliczyć liczbę działań](../../../docs/framework/windows-workflow-foundation/media/numberofactivitiesequation.gif "NumberOfActivitiesEquation")  
  
 Liczba działań testów WF3 można obliczyć z nieco inne równości z powodu sekwencję dodatkowe:  
  
 ![Równości można obliczyć liczbę działań](../../../docs/framework/windows-workflow-foundation/media/w3numberofactivitiesequation.gif "W3NumberOfActivitiesEquation")  
  
 W przypadku d głębokość, a co jest liczba działań w sekwencji.  Logiki stojącej za tymi równania jest, że pierwszej stałej pomnożona przez, jest numer sekwencji, a druga stała jest statyczny liczbę działań zawartych w bieżącym poziomie.  Istnieją trzy działania podrzędne schemat blokowy w każdym schemacie blokowym.  Na dolnym poziomie głębokość zaprezentowane te są puste, ale na innych poziomach są kopie głównego schematu blokowego.  Liczba działań w definicji przepływu pracy odmiany każdego testu podane w poniższej tabeli:  
  
 ![Porównuje liczbę działań używanych w poszczególnych testów](../../../docs/framework/windows-workflow-foundation/media/comparechart.gif "CompareChart")  
  
 Liczba działań w definicji przepływu pracy znacznie zwiększa się, każdy poziom głębokości.  Ale tylko jedną ścieżkę na podjęcie decyzji, czy jest wykonywane w wystąpieniu przepływu są wykonywane tylko mały podzbiór rzeczywistych działań.  
  
 ![Złożonych przepływów prac](../../../docs/framework/windows-workflow-foundation/media/complexworkflowthroughputworkflow.gif "ComplexWorkflowThroughputWorkflow")  
  
 Odpowiednik przepływ pracy został utworzony dla WF3. Projektant WF3 pokazuje całego przepływu pracy w obszarze projektu zamiast zagnieżdżenia, dlatego jest zbyt duży do wyświetlenia w tym temacie. Poniżej przedstawiono fragment przepływu pracy.  
  
 ![WF3 Przepływ pracy](../../../docs/framework/windows-workflow-foundation/media/wf3workflow.gif "WF3Workflow")  
  
 Wykonywanie zagnieżdżenia w ekstremalnych przypadkach, innego przepływu pracy, który jest częścią tego testu używa 100 sekwencje zagnieżdżone.  Najbardziej sekwencji jest jeden `Comment` lub <xref:System.Workflow.Activities.CodeActivity>.  
  
 ![Zagnieżdżone sekwencje](../../../docs/framework/windows-workflow-foundation/media/nestedsequencewf.gif "NestedSequenceWF")  
  
 Śledzenie i trwałości nie są używane jako część tego testu.  
  
### <a name="test-results"></a>Wyniki tekstu  
 ![Wykres przepływności](../../../docs/framework/windows-workflow-foundation/media/testresults1.gif "TestResults1")  
  
 Nawet w przypadku złożonych przepływów pracy z dużą głębokość i dużą liczbę działań wyniki są spójne z innych numerów przepływności przedstawionej w tym artykule.  Przepływność w WF4 szybciej jest rzędów i musi zostać porównane na skali logarytmicznej.  
  
### <a name="memory"></a>Pamięć  
 Obciążenie pamięci Windows Workflow Foundation jest mierzony w dwóch podstawowych obszarach: złożoności przepływu pracy i liczbę definicji przepływu pracy.  Pomiary pamięci zostały pobrane na stacji roboczej 64-bitowym systemie Windows 7.  Istnieje wiele sposobów uzyskiwania pomiaru pracy Ustaw rozmiar, takie jak monitorowanie liczników wydajności, sondowanie Environment.WorkingSet lub przy użyciu narzędzia, takiego jak VMMap dostępnej w sklepie [VMMap](http://technet.microsoft.com/sysinternals/dd535533.aspx). Kombinacji metod był używany do uzyskania i sprawdź wyniki każdego z testów.  
  
### <a name="workflow-complexity-test"></a>Test złożoności przepływu pracy  
 Przepływ pracy środki testu złożoności zestaw roboczy różnica zależnie od stopnia złożoności przepływu pracy.  Oprócz złożonych przepływów pracy, używane w poprzedniej sekcji, nowych zmian zostaną dodane do obejmuje dwa podstawowe przypadków: pojedynczego działania przepływu pracy i sekwencję działań 1000.  Te testy przepływy pracy są zainicjowany i wykonywany w celu zakończenia w jednej pętli serial okres jednej minuty.  Odmiana każdego testu zostanie uruchomione trzy razy, a dane zarejestrowane jest średnią z tych trzech działa.  
  
 Dwa nowe testy podstawowe są przepływy pracy, które wyglądają jak pokazano poniżej:  
  
 ![Przepływy pracy złożonych](../../../docs/framework/windows-workflow-foundation/media/complexworkflowboth.gif "ComplexWorkflowBoth")  
  
 W przepływie pracy WF3 pokazanym powyżej pusta <xref:System.Workflow.Activities.CodeActivity> działania są używane.  Przepływ pracy WF4 powyżej używa `Comment` działań.  `Comment` Działania został opisany w sekcji porównania wydajności poziomie składnika w tym artykule.  
  
 ![Wykres użycia pamięci](../../../docs/framework/windows-workflow-foundation/media/complexmemoryusage.gif "ComplexMemoryUsage")  
  
 Jednym z wyczyść trendów można zauważyć na tym wykresie jest czy zagnieżdżenia ma stosunkowo minimalny wpływ na użycie pamięci w WF3 i WF4.  Największy wpływ pamięci pochodzi z liczba działań w danym przepływie pracy.  Podane dane z sekwencji 1000, złożonych głębokość 5 sekwencji 5 i głębokość złożonych sekwencji 7 1 zmian, jest jasne, czy podczas liczbę działań tysięcy, wzrost użycia pamięci staje się bardziej zauważalne.  W przypadku extreme (głębokość 7 sekwencji 1) w przypadku działań ~ 29K WF4 przy użyciu prawie 79% mniej pamięci niż WF3.  
  
### <a name="multiple-workflow-definitions-test"></a>Wiele testów definicji przepływu pracy  
 Pomiaru pamięci dla definicji przepływu pracy jest podzielona na dwie różne testy z powodu dostępne opcje hostingu przepływów pracy w WF3 i WF4.  Testy są uruchamiane w inny sposób niż badanie złożoności przepływu pracy, w tym danego przepływu pracy jest instancji i wykonywane tylko raz w każdej definicji.  Jest to spowodowane definicji przepływu pracy i jej hosta pozostawać w pamięci przez czas ich istnienia elementu AppDomain.  Pamięć używana przez uruchomienie wystąpienia danego przepływu pracy należy wyczyścić podczas wyrzucania elementów bezużytecznych.  Wskazówki dotyczące migracji dla WF4 zawiera bardziej szczegółowe informacje na temat opcji obsługi. Aby uzyskać więcej informacji, zobacz [WF migracji Cookbook: przepływu pracy obsługującego](http://go.microsoft.com/fwlink/?LinkID=153313).  
  
 Tworzenie wielu definicji przepływu pracy dla definicji przepływu pracy test może odbywać się na kilka sposobów.  Na przykład jedna Użyj generowania kodu, aby utworzyć zbiór 1000 przepływy pracy, które są identyczne z wyjątkiem w nazwie i zapisać każdy z tych przepływów pracy do oddzielnych plików.  Ta metoda została wykonana dla testu hostowanych w konsoli.  W WF3 <xref:System.Workflow.Runtime.WorkflowRuntime> klasa została użyta do uruchomienia definicji przepływu pracy.  WF4 musi <xref:System.Activities.WorkflowApplication> można utworzyć wystąpienia przepływu pracy pojedynczego lub bezpośrednio przy użyciu <xref:System.Activities.WorkflowInvoker> do uruchamiania działania, jak w przypadku wywołania metody.  <xref:System.Activities.WorkflowApplication> host wystąpienia jednego przepływu pracy i ma bliżej parzystość funkcji do <xref:System.Workflow.Runtime.WorkflowRuntime> tak, aby została użyta w tego testu.  
  
 Odnośnie do hostowania przepływów pracy w usługach IIS jest możliwość użycia <xref:System.Web.Hosting.VirtualPathProvider> do tworzenia nowego <xref:System.ServiceModel.WorkflowServiceHost> zamiast generowania wszystkie pliki XAMLX lub pliku XOML.  <xref:System.Web.Hosting.VirtualPathProvider> Obsługuje żądania przychodzącego i odpowiada "wirtualnego plik", które mogą być ładowane z bazy danych lub, w tym przypadku jest generowane w locie.  Jest konieczne utworzyć pliki fizyczne 1000.  
  
 Definicji przepływu pracy w badaniu konsoli zostały prosty sekwencyjny przepływy pracy z jednego działania.  Pojedyncze działanie była pusta <xref:System.Workflow.Activities.CodeActivity> w przypadku WF3 i `Comment` działanie w przypadku WF4.  W przypadku hostowanych przez usługi IIS używane przepływów pracy uruchamianych na odbieranie komunikatów i końcowych na wysyłanie odpowiedzi:  
  
 ![Usługi przepływu pracy w WF3 i WF4](../../../docs/framework/windows-workflow-foundation/media/receiveworkflowboth.gif "ReceiveWorkflowBoth")  
  
 Rysunek 4 — przepływ pracy WF3 z ReceiveActivity i WF4 przepływu pracy z wzorcem żądań i odpowiedzi  
  
 W poniższej tabeli przedstawiono różnicowej w zestawie roboczym między definicji jednym przepływie pracy i definicje 1001:  
  
|Opcje hostingu|WF3 Różnica zestawu roboczego|WF4 Różnica zestawu roboczego|  
|---------------------|---------------------------|---------------------------|  
|Przepływy pracy hostowanej aplikacji konsoli|18 MB|9 MB|  
|Przepływ pracy usług hostowanych w programie IIS|446 MB|364 MB|  
  
 Hosting definicji przepływu pracy w programie IIS wykorzystuje znacznie większej ilości pamięci z powodu <xref:System.ServiceModel.WorkflowServiceHost>, są szczegółowe [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] artefaktów i przetwarzania logiki skojarzonej z hostem wiadomości.  
  
 Hosting w WF3 przepływy pracy konsoli zostały wprowadzone w kodzie zamiast pliku XOML.  WF4 wartość domyślna to użyj XAML.  XAML jest przechowywana jako osadzonego zasobu w zestawie i kompilowane w czasie wykonywania do implementacji przepływu pracy.  Brak niektórych koszty związane z tym procesem.  W celu odpowiedniego porównanie WF3 WF4, kodowane przepływy pracy zostały użyte zamiast XAML.  Poniżej przedstawiono przykładową przepływów pracy WF4:  
  
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
  
 Istnieje wiele czynników, które mogą wpłynąć na zmniejszenie zużycia pamięci. Nadal ma zastosowanie tego samego porady dla wszystkich programów zarządzanych.  W środowiskach hostowanych przez usługi IIS <xref:System.ServiceModel.WorkflowServiceHost> obiektu utworzonego dla definicji przepływu pracy pozostaje w pamięci, dopóki jest pula aplikacji.  Powinny być utrzymywane w uwadze podczas zapisywania rozszerzenia.  Ponadto warto uniknąć zmienne "globalne" (zmienne zakresu do całego przepływu pracy) i ograniczyć zakres zmiennych, gdy jest to możliwe.  
  
## <a name="workflow-runtime-services"></a>Usługi czasu wykonywania przepływu pracy  
  
### <a name="persistence"></a>Trwałość  
 WF3 i WF4 zarówno składnikiem dostawca trwałości SQL.  Dostawca trwałości WF3 SQL jest prostych implementacji, który serializuje wystąpienia przepływu pracy i zapisuje go w obiekcie blob.  Z tego powodu wydajności dostawcy silnie zależna od rozmiaru wystąpienia przepływu pracy.  W WF3 jak opisano wcześniej w tym dokumencie, wielu powodów, można zwiększyć rozmiar wystąpienia.  Wielu klientów, wybierz nie użyć domyślnego dostawcy trwałości SQL, ponieważ przechowywane w bazie danych serializacji wystąpienia daje nie wgląd w stan przepływu pracy.  Aby można było znaleźć określonego przepływu pracy bez wiedzy o identyfikator przepływu pracy, co musi deserializacji każdego wystąpienia utrwalonego i sprawdź, czy zawartość.  Wielu deweloperów wolą pisanie własnych dostawców trwałości, aby obejść ten problem.  
  
 Dostawca trwałości WF4 SQL próbował rozwiązać niektóre z tych problemów.  Tabele trwałości ujawnia niektóre informacje, takie jak active zakładek i Awansowanie właściwości.  Nowa funkcja na podstawie zawartości korelacji w WF4 nie przeprowadza się również za pomocą podejście trwałości WF3 SQL, które ma obsługiwanego niektóre zmiany w organizacji wystąpienia utrwalonego przepływu pracy.  To sprawia, że dostawca trwałości bardziej złożone i umieszcza dodatkowego obciążenia w bazie danych.  
  
### <a name="environment-setup"></a>Konfigurowanie środowiska  
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-setup"></a>Testuj ustawienia  
 Nawet w przypadku zestawu ulepszonych funkcji i lepszą obsługę współbieżności dostawca trwałości SQL w WF4 jest szybsza niż podany w WF3.  Aby to pokazują, dwa przepływy pracy wykonujące zasadniczo tych samych operacji w WF3 i WF4 są porównywane poniżej.  
  
 ![Przepływy pracy trwałości](../../../docs/framework/windows-workflow-foundation/media/persistworkflow.gif "PersistWorkflow")  
  
 Rysunek 5 — przepływ pracy trwałości w WF3 w lewo i WF4 po prawej stronie  
  
 Dwa przepływy pracy są tworzone przez odebranego komunikatu.  Po wysłaniu odpowiedzi na wiadomość początkowej, przepływ pracy jest trwały.  W przypadku WF3 pustą <xref:System.Workflow.ComponentModel.TransactionScopeActivity> służy do inicjowania trwałość.  Taki sam może być uzyskane w WF3 przez oznaczenie działania jako "utrwalić Zamknij".  Drugi skorelowany komunikat zakończeniu przepływu pracy.  Przepływy pracy są zachowywane, ale nie został zwolniony.  
  
### <a name="test-results"></a>Wyniki tekstu  
 ![Przepływność trwałości](../../../docs/framework/windows-workflow-foundation/media/throughputpersistence.gif "ThroughputPersistence")  
  
 Podczas transportu między klientem a warstwy środkowej, jest protokół HTTP, trwałość WF4 wykazuje wzrost 2.6 razy.  Transportu TCP zwiększa współczynnik godziny 3.0.  We wszystkich przypadkach, użycie procesora CPU na warstwy środkowej to 98% lub nowszego.  Przyczyny, że przepływność WF4 jest większa jest spowodowane szybsze środowiska uruchomieniowego przepływu pracy.  Rozmiar serializowanym wystąpieniu brakuje w obu przypadkach i nie jest głównym elementem uczestniczących w takiej sytuacji.  
  
 WF3 i WF4 przepływów pracy w tym teście użyć działania, aby jawnie wskazać podczas utrwalania powinna się odbyć.  Zaletą utrwalanie przepływu pracy bez wyładowywanie to ustawienie.  W WF3, również jest możliwy do utrwalenia przy użyciu <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> funkcji, ale zwalnia wystąpienie przepływu pracy z pamięci.  Jeśli przy użyciu WF3 Deweloper chce upewnij się, że przepływ pracy będzie się powtarzać, w niektórych punktach, albo muszą zmieniać definicji przepływu pracy lub zwrócić koszt zwolnienie i ponowne ładowanie wystąpienia przepływu pracy.  Nową funkcją w WF4 umożliwia utrwalić bez zwalnianie: <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToPersist%2A>.  Ta funkcja umożliwia wystąpienia przepływu pracy utrwalone w stanie bezczynności, ale pozostaje w pamięci do <xref:System.ServiceModel.Activities.Description.WorkflowIdleBehavior.TimeToUnload%2A> zostały spełnione warunki progowe lub wykonywania zostanie wznowione.  
  
 Należy pamiętać, że dostawca trwałości WF4 SQL wykonuje więcej pracy w warstwie bazy danych.  Bazy danych SQL może stać się wąskiego gardła, dlatego ważne jest, aby monitorować wykorzystanie Procesora i dysku.  Należy uwzględnić następujące liczniki wydajności z SQL bazy danych podczas testowania aplikacji przepływu pracy:  
  
-   Dysk fizyczny\\czas odczytu z dysku %  
  
-   Dysk fizyczny\\czas dysku (%)  
  
-   Dysk fizyczny\\czas zapisu dysku %  
  
-   Dysk fizyczny\\% średni Długość kolejki dysku  
  
-   Dysk Fizyczny\średni Długość kolejki odczytu dysku  
  
-   Dysk Fizyczny\średni Długość kolejki dysku zapisu  
  
-   Długość kolejki dysku PhysicalDisk\Current  
  
-   Informacje o procesorze\\czas procesora (%)  
  
-   Czas oczekiwania zatrzaśnięcia SQLServer:Latches\Average (ms)  
  
-   SQLServer:Latches\Latch czeka na sekundę  
  
### <a name="tracking"></a>Śledzenie  
 Śledzenia przepływu pracy można śledzić postęp przepływ pracy.  Informacje, które są dołączane do zdarzeń śledzenia jest określana przez profilu śledzenia.  Im bardziej złożonych staje się profilu śledzenia droższe śledzenia.  
  
 WF3 zostały wydane z usługą SQL na podstawie śledzenia.  Ta usługa może działa w trybach wsadów i niewsadowego.  Trybu niewsadowego zdarzenia śledzenia są zapisywane bezpośrednio w bazie danych.  W trybie wsadów zdarzenia śledzenia są zbierane w tej samej partii jako stan wystąpienia przepływu pracy.  Tryb wsadów ma najlepszą wydajność dla najszerszego zakresu projektów przepływu pracy.  Jednak przetwarzanie wsadowe może mieć negatywny wpływ na wydajność, jeśli przepływ pracy działa wiele działań bez utrwalanie i te działania są śledzone.  To powszechnie się stanie w pętli i najlepszym sposobem uniknięcia tego scenariusza jest zaprojektować dużych pętli do zawiera punktu trwałości.  Wprowadzenie punktu trwałości w pętlę może negatywnie wpłynąć na wydajność, a także tak ważne jest, aby zmierzyć kosztów każdego i opracowywane równowagi.  
  
 WF4 nie jest dostarczany z usługi śledzenia SQL.  Rejestrowanie śledzenia informacji do bazy danych SQL można być lepiej obsłużone z serwera aplikacji zamiast wbudowanych w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]. W związku z tym śledzenia SQL jest teraz obsługiwany przez AppFabric.  Dostawca śledzenia poza pole w WF4 jest oparta na funkcji Śledzenie zdarzeń systemu Windows ().  
  
 ETW jest systemem zdarzeń jądra poziom, małe opóźnienia wbudowanego w systemie Windows.  Używa modelu dostawcy/klienta, który umożliwia tylko uniknięcie kary do śledzenia zdarzeń po faktycznie konsumenta.  Oprócz zdarzeń jądra, np. procesora, dysku, pamięci i obciążenie sieci wiele aplikacji również korzystać z funkcji ETW.  Zdarzenia ETW są bardziej efektywne niż liczniki wydajności, gdyż zdarzenia można dostosować do aplikacji.  Zdarzenie może zawierać tekstu, takiego jak identyfikator przepływu pracy lub komunikat informacyjny.  Ponadto zdarzenia są skategoryzowane masek bitowych tak, aby korzystanie z podzbioru zdarzeń będzie miał mniejszą wpływ na wydajność niż przechwytywania wszystkich zdarzeń.  
  
 Aby podejście za pomocą funkcji ETW śledzenia zamiast SQL korzyści:  
  
-   Kolekcja śledzenia zdarzeń można podzielić na inny proces.  Daje to większą elastyczność w jaki sposób są rejestrowane zdarzenia.  
  
-   Zdarzenia ETW śledzenia łatwo są łączone z [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] ETW zdarzeń lub innych dostawców ETW, takiego jak dostawca programu SQL Server lub jądra.  
  
-   Autorzy przepływu pracy nie trzeba zmieniać przepływu pracy, aby lepiej współpracuje z implementacji programu konkretnego śledzenia, takich jak Usługa śledzenia WF3 SQL trybie wsadowym.  
  
-   Administrator może włączyć śledzenie lub wyłączyć bez odtwarzania procesu hosta.  
  
 Korzyści w zakresie wydajności do śledzenia funkcji ETW są dostarczane z wadą.  Zdarzenia ETW mogą zostać utracone, jeśli system jest wykorzystanie zasobów intensywny.  Przetwarzanie zdarzeń nie jest przeznaczone do blokowania normalnego działania programu i w związku z tym nie ma żadnej gwarancji czy wszystkie zdarzenia ETW będzie emisji do subskrybentów.  Dzięki temu śledzenia funkcji ETW doskonałe rozwiązanie dla monitorowanie kondycji, ale nie nadaje się do inspekcji.  
  
 Gdy WF4 nie ma dostawcy śledzenia SQL, wykonuje AppFabric.  Podejście śledzenia SQL w AppFabric jest subskrybowanie zdarzeń ETW za pomocą usługi systemu Windows, która partii zdarzeń i zapisuje je w tabeli SQL przeznaczony do wstawienia szybkie.  Osobne zadanie wstrzymanie danych z tej tabeli i reforms go do tabel, które mogą być wyświetlane na pulpicie nawigacyjnym AppFabric raportowania.  Oznacza to, że partia śledzenia zdarzeń jest obsługiwane niezależnie od przepływu pracy, pochodzi z, a w związku z tym nie ma upłynąć punktu trwałości rejestrowane.  
  
 Zdarzenia ETW może zostać zarejestrowana przy użyciu narzędzi, takich jak logman lub program xperf.  Można wyświetlić z narzędzia, takiego jak xperfview lub przekonwertować na bardziej czytelnym formacie XML, np. z tracerpt compact pliku ETL.  W WF3 tylko opcja pobierania śledzenia zdarzeń bez bazy danych SQL jest tworzenie niestandardowych śledzenia usługi. Aby uzyskać więcej informacji dotyczących funkcji ETW, zobacz [usługi WCF i śledzenia zdarzeń dla systemu Windows](../../../docs/framework/wcf/samples/wcf-services-and-event-tracing-for-windows.md) i [śledzenia zdarzeń dla systemu Windows](http://msdn.microsoft.com/library/ff190903.aspx\)).  
  
 Włączanie śledzenia przepływu pracy będzie miało wpływ na wydajność w różnym stopniu.  Testu porównawczego poniżej używa narzędzia logman do wykorzystania ETW śledzenia zdarzeń i zarejestruj je do pliku ETL.  Koszt śledzenia w AppFabric SQL nie jest w zakres tego artykułu.  Profil śledzenia podstawowego, również w AppFabric, jest wyświetlana w testu wydajności.  Dołączone są także koszt tylko kondycji monitorowanie zdarzeń śledzenia.  Zdarzenia te są przydatne podczas rozwiązywania problemów oraz określania średniej przepływności systemu.  
  
### <a name="environment-setup"></a>Konfigurowanie środowiska  
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-results"></a>Wyniki tekstu  
 ![Przepływ pracy śledzenie kosztów](../../../docs/framework/windows-workflow-foundation/media/workflowtracingcost.gif "WorkflowTracingCost")  
  
 Monitorowanie kondycji ma około 3% wpływ na wydajność.  Koszt profilu podstawowego wynosi około 8%.  
  
## <a name="interop"></a>Współdziałanie  
 WF4 jest prawie pełna poprawione [!INCLUDE[wf1](../../../includes/wf1-md.md)] i w związku z tym WF3 przepływów pracy i działań nie są bezpośrednio zgodne z WF4.  Wielu klientów, które wcześniej przyjęte Windows Workflow Foundation ma wewnętrznych lub innych firm definicji przepływu pracy i działań niestandardowych do WF3.  Jednym ze sposobów ułatwić przejście WF4 ma użyć działania Interop, które można wykonywać działania WF3 z WF4 przepływu pracy.  Zalecane jest <xref:System.Activities.Statements.Interop> działania można używać tylko gdy jest to konieczne. Aby uzyskać więcej informacji na temat migracji do WF4 wyewidencjonować [wskazówki dotyczące migracji WF4](http://go.microsoft.com/fwlink/?LinkID=153313).  
  
### <a name="environment-setup"></a>Konfigurowanie środowiska  
 ![Środowisko testowania wydajności przepływu pracy](../../../docs/framework/windows-workflow-foundation/media/wfperfenvironment.gif "WFPerfEnvironment")  
  
### <a name="test-results"></a>Wyniki tekstu  
 W poniższej tabeli przedstawiono wyniki działania przepływu pracy zawierające pięć działań w sekwencji w różnych konfiguracjach.  
  
|Test|Przepływność (przepływy pracy/s)|  
|----------|-----------------------------------|  
|Sekwencja WF3 w środowisku uruchomieniowym WF3|1,576|  
|Sekwencja WF3 w środowisku uruchomieniowym WF4 za pomocą międzyoperacyjności|2,745|  
|WF4 sekwencji|153,582|  
  
 Zwiększenie wydajności zauważalne za pomocą międzyoperacyjności za pośrednictwem prostych WF3 nie istnieje.  Jednak gdy porównane z działaniami WF4, wzrost jest niewielka.  
  
## <a name="summary"></a>Podsumowanie  
 Wysokie inwestycje wydajności WF4 zapłacić w wielu obszarach kluczową rolę.  Wydajność składników przepływu pracy jest w niektórych przypadkach kilkaset razy szybsze w porównaniu z powodu leaner WF3 WF4 [!INCLUDE[wf1](../../../includes/wf1-md.md)] środowiska wykonawczego.  Znacznie lepszą są również wartościami opóźnień.  To oznacza spadek wydajności przy użyciu [!INCLUDE[wf1](../../../includes/wf1-md.md)] przeciwieństwie programowania ręcznego [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] usługi orchestration jest bardzo mała, biorąc pod uwagę przy użyciu dodatkowych zalet [!INCLUDE[wf1](../../../includes/wf1-md.md)].  Zwiększa wydajność trwałości przez współczynnik 2.5 3.0.  Monitorowanie kondycji za pomocą przepływu pracy śledzenia teraz ma nadmiernego obciążenia.  Kompleksowy zestaw przewodniki dotyczące migracji są dostępne dla tych, które są uwzględnieniu przenoszenie z WF3 do WF4.  Wszystkie te należy wykonać WF4 atrakcyjną opcję do pisania aplikacji złożonych.  
  
## <a name="acknowledgements"></a>Potwierdzeń  
 Wiele dzięki użyciu następujące współautorzy i osoby dokonujące przeglądu dla ich wysiłków:  
  
-   Leon Welicki firma Microsoft Corporation  
  
-   Ryszard Kwiecinski firma Microsoft Corporation  
  
-   Emil Velinov, firma Microsoft Corporation  
  
-   Jan Talbert, firma Microsoft Corporation  
  
-   Robert Schmidt, firma Microsoft Corporation  
  
-   Stefan Batres, firma Microsoft Corporation
