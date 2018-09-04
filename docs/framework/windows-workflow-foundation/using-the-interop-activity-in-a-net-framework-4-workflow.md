---
title: Używanie działania Interop w przepływie pracy programu .NET Framework 4
ms.date: 03/30/2017
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
ms.openlocfilehash: 02eeaf5bb7ff484ba5982197fc395e247cd5a87f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43528113"
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>Używanie działania Interop w przepływie pracy programu .NET Framework 4
Działania utworzone za pomocą [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] lub [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] mogą być używane w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy przy użyciu <xref:System.Activities.Statements.Interop> działania. Ten temat zawiera omówienie sposobu użycia <xref:System.Activities.Statements.Interop> działania.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> w przyborniku projektanta przepływu pracy nie ma działania, chyba że projekt przepływu pracy ma jego **platformę docelową** ustawienie **.Net Framework 4** lub nowszej.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>Używanie działania Interop w przepływach pracy programu .NET Framework 4.5  
 W tym temacie [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] utworzeniu biblioteki działania, który zawiera `DiscountCalculator` działania. `DiscountCalculator` Oblicza rabat na wersję na podstawie kwoty zakupu i składa się z <xref:System.Workflow.Activities.SequenceActivity> zawierający <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Działanie utworzone w tym temacie używa <xref:System.Workflow.Activities.PolicyActivity> Aby zaimplementować logikę działania. Nie jest wymagane do użycia niestandardowej [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] działania lub <xref:System.Activities.Statements.Interop> działania, aby można było używać reguł w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy. Na przykład za pomocą reguł w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy bez użycia <xref:System.Activities.Statements.Interop> działania, zobacz [działanie zasad w programie .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) próbki.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>Aby utworzyć projekt biblioteki działań programu .NET Framework 3.5  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i wybierz **New** i następnie **projektu...** z **pliku** menu.  
  
2.  Rozwiń **inne typy projektów** w węźle **zainstalowane szablony** okienka, a następnie wybierz **Visual Studio Solutions**.  
  
3.  Wybierz **puste rozwiązanie** z **Visual Studio Solutions** listy. Typ `PolicyInteropDemo` w **nazwa** pole, a następnie kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **PolicyInteropDemo** w **Eksploratora rozwiązań** i wybierz **Dodaj** i następnie **nowy projekt...** .  
  
    > [!TIP]
    >  Jeśli **Eksploratora rozwiązań** okno nie jest widoczny, wybierz opcję **Eksploratora rozwiązań** z **widoku** menu.  
  
5.  W **zainstalowane szablony** listy wybierz **Visual C#** i następnie **przepływu pracy**. Wybierz **.NET Framework 3.5** z listy rozwijanej wersji .NET Framework, a następnie wybierz **biblioteki działania przepływu pracy** z **szablony** listy.  
  
6.  Typ `PolicyActivityLibrary` w **nazwa** pole, a następnie kliknij przycisk **OK**.  
  
7.  Kliknij prawym przyciskiem myszy **Activity1.cs** w **Eksploratora rozwiązań** i wybierz **Usuń**. Kliknij przycisk **OK** o potwierdzenie.  
  
#### <a name="to-create-the-discountcalculator-activity"></a>Aby utworzyć działanie DiscountCalculator  
  
1.  Kliknij prawym przyciskiem myszy **PolicyActivityLibrary** w **Eksploratora rozwiązań** i wybierz **Dodaj** i następnie **działanie...** .  
  
2.  Wybierz **działanie (z separacją kodu)** z **elementy Visual C#** listy. Typ `DiscountCalculator` w **nazwa** pole, a następnie kliknij przycisk **OK**.  
  
3.  Kliknij prawym przyciskiem myszy **DiscountCalculator.xoml** w **Eksploratora rozwiązań** i wybierz **Wyświetl kod**.  
  
4.  Dodaj następujące trzy właściwości, aby `DiscountCalculator` klasy.  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Kliknij prawym przyciskiem myszy **DiscountCalculator.xoml** w **Eksploratora rozwiązań** i wybierz **Projektant widoków**.  
  
6.  Przeciągnij **zasad** działanie z **Windows Workflow 3.0** części **przybornika** i upuść je **DiscountCalculator** działania .  
  
    > [!TIP]
    >  Jeśli **przybornika** okno nie jest widoczny, wybierz opcję **przybornika** z **widoku** menu.  
  
#### <a name="to-configure-the-rules"></a>Aby skonfigurować reguły  
  
1.  Kliknij nowo dodany **zasad** działanie, aby ją zaznaczyć, jeśli nie została jeszcze wybrana.  
  
2.  Kliknij przycisk **RuleSetReference** właściwość **właściwości** okna, aby go zaznaczyć, a następnie kliknij przycisk wielokropka z prawej strony właściwości.  
  
    > [!TIP]
    >  Jeśli **właściwości** okno nie jest widoczne, wybierz **okno właściwości** z **widoku** menu.  
  
3.  Wybierz **kliknij pozycję Nowy...** .  
  
4.  Kliknij przycisk **Dodaj regułę**.  
  
5.  Wpisz następujące wyrażenie do **warunek** pole.  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  Wpisz następujące wyrażenie do **następnie akcje** pole.  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  Kliknij przycisk **Dodaj regułę**.  
  
8.  Wpisz następujące wyrażenie do **warunek** pole.  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. Wpisz następujące wyrażenie do **następnie akcje** pole.  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. Kliknij przycisk **Dodaj regułę**.  
  
11. Wpisz następujące wyrażenie do **warunek** pole.  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. Wpisz następujące wyrażenie do **następnie akcje** pole.  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. Wpisz następujące wyrażenie do **inne akcje** pole.  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. Kliknij przycisk **OK** zamknąć **Edytor zestawu reguł** okno dialogowe.  
  
15. Upewnij się, że nowo utworzony <xref:System.Workflow.Activities.Rules.RuleSet> wybrano **nazwa** listy, a następnie kliknij przycisk **OK**.  
  
16. Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
 Dodane do reguły `DiscountCalculator` działania w tej procedurze przedstawiono w poniższym przykładzie kodu.  
  
```  
Rule1: IF this.Subtotal >= 50 && this.Subtotal < 100   
       THEN this.DiscountPercent = 0.075   
  
Rule2: IF this. Subtotal >= 100   
       THEN this.DiscountPercent = 0.15   
  
Rule3: IF this.DiscountPercent > 0   
       THEN this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent   
       ELSE this.Total = this.Subtotal  
```  
  
 Gdy <xref:System.Workflow.Activities.PolicyActivity> wykonuje te trzy zasady oceny i modyfikować `Subtotal`, `DiscountPercent`, i `Total` wartości właściwości `DiscountCalculator` działanie, aby obliczyć żądaną rabat.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>Przy użyciu działania DiscountCalculator przy użyciu działań Interop  
 Aby użyć `DiscountCalculator` działania wewnątrz [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy, <xref:System.Activities.Statements.Interop> to działanie służy. W tej sekcji dwa przepływy pracy są tworzone, jeden przy użyciu kodu i ją przy użyciu projektanta przepływów pracy, które przedstawiają, jak używać <xref:System.Activities.Statements.Interop> działanie przy użyciu `DiscountCalculator` działania. Ta sama aplikacja hosta jest używana w przypadku obu przepływów pracy.  
  
#### <a name="to-create-the-host-application"></a>Aby utworzyć aplikację hosta  
  
1.  Kliknij prawym przyciskiem myszy **PolicyInteropDemo** w **Eksploratora rozwiązań** i wybierz **Dodaj**, a następnie **nowy projekt...** .  
  
2.  Upewnij się, że **.NET Framework 4.5** jest zaznaczony na liście rozwijanej wersji .NET Framework, a następnie wybierz pozycję **Aplikacja konsoli przepływu pracy** z **elementy Visual C#** listy.  
  
3.  Typ `PolicyInteropHost` do **nazwa** pole, a następnie kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **właściwości**.  
  
5.  W **platformę docelową** listy rozwijanej listy, zmień zaznaczoną wartość z **.NET Framework 4 Client Profile** do **.NET Framework 4.5**. Kliknij przycisk **tak** o potwierdzenie.  
  
6.  Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie...** .  
  
7.  Wybierz **PolicyActivityLibrary** z **projektów** kartę, a następnie kliknij przycisk **OK**.  
  
8.  Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **Dodaj odwołanie...** .  
  
9. Wybierz **System.Workflow.Activities**, **System.Workflow.ComponentModel**, a następnie **System.Workflow.Runtime** z **.NET**kartę, a następnie kliknij przycisk **OK**.  
  
10. Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **Ustaw jako projekt startowy**.  
  
11. Naciśnij klawisze CTRL + SHIFT + B, aby skompilować rozwiązanie.  
  
### <a name="using-the-interop-activity-in-code"></a>Używanie działania Interop w kodzie  
 W tym przykładzie tworzona jest definicja przepływu pracy, przy użyciu kodu, który zawiera <xref:System.Activities.Statements.Interop> działania i `DiscountCalculator` działania. Ten przepływ pracy jest wywoływany przy użyciu <xref:System.Activities.WorkflowInvoker> i wyniki oceny reguły są zapisywane przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Aby użyć działania Interop w kodzie  
  
1.  Kliknij prawym przyciskiem myszy **Program.cs** w **Eksploratora rozwiązań** i wybierz **Wyświetl kod**.  
  
2.  Dodaj następujący kod `using` instrukcji w górnej części pliku.  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  Usuń zawartość `Main` metodę i Zastąp następującym kodem.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  Utworzenie nowej metody w `Program` klasę o nazwie `CalculateDiscountUsingCodeWorkflow` zawierający poniższy kod.  
  
    ```csharp  
    static void CalculateDiscountUsingCodeWorkflow()  
    {  
        Variable<double> Subtotal = new Variable<double>  
        {  
            Default = 75.99,  
            Name = "Subtotal"  
        };  
  
        Variable<double> DiscountPercent = new Variable<double>  
        {  
            Name = "DiscountPercent"  
        };  
  
        Variable<double> Total = new Variable<double>  
        {  
            Name = "Total"  
        };  
  
        Activity wf = new Sequence  
        {  
            Variables = { Subtotal, DiscountPercent, Total },  
            Activities =   
            {  
                new Interop  
                {  
                    ActivityType = typeof(DiscountCalculator),  
                    ActivityProperties =   
                    {  
                        { "Subtotal", new InArgument<double>(Subtotal) },  
                        { "DiscountPercentOut", new OutArgument<double>(DiscountPercent) },  
                        { "TotalOut", new OutArgument<double>(Total) }  
                    }  
                },  
                new WriteLine  
                {  
                    Text =  new InArgument<string>(env =>   
                        string.Format("Subtotal: {0:C}, Discount {1}%, Total {2:C}",   
                        Subtotal.Get(env), DiscountPercent.Get(env) * 100, Total.Get(env)))  
                }  
            }  
        };  
  
        WorkflowInvoker.Invoke(wf);  
    }  
    ```  
  
    > [!NOTE]
    >  `Subtotal`, `DiscountPercent`, I `Total` właściwości `DiscountCalculator` działania są udostępniane jako argumenty <xref:System.Activities.Statements.Interop> działania i przepływu pracy jest powiązana z lokalnych zmiennych w <xref:System.Activities.Statements.Interop> działania <xref:System.Activities.Statements.Interop.ActivityProperties%2A> Kolekcja. `Subtotal` jest dodawany jako <xref:System.Activities.ArgumentDirection.In> argument ponieważ `Subtotal` dane są przesyłane <xref:System.Activities.Statements.Interop> działania i `DiscountPercent` i `Total` są dodawane jako <xref:System.Activities.ArgumentDirection.Out> argumentów, ponieważ ich dane przepływają z <xref:System.Activities.Statements.Interop> działania. Należy pamiętać, że dwa <xref:System.Activities.ArgumentDirection.Out> argumenty są dodawane przy użyciu nazw `DiscountPercentOut` i `TotalOut` do wskazania, że reprezentują <xref:System.Activities.ArgumentDirection.Out> argumentów. `DiscountCalculator` Typ jest określony jako <xref:System.Activities.Statements.Interop> działania <xref:System.Activities.Statements.Interop.ActivityType%2A>.  
  
5.  Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację. Zastąp różne wartości `Subtotal` wartość do przetestowania poziomy różnych rabatów, dostarczone przez `DiscountCalculator` działania.  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Używanie działania Interop w Projektancie przepływu pracy  
 W tym przykładzie przepływ pracy jest tworzony za pomocą projektanta przepływów pracy. Ten przepływ pracy ma taką samą funkcjonalność jak w poprzednim przykładzie, z wyjątkiem niż zamiast <xref:System.Activities.Statements.WriteLine> działanie, aby wyświetlić ten rabat aplikacji hosta pobiera i wyświetla informacje o rabat, po zakończeniu przepływu pracy. Ponadto zamiast używania zmiennych lokalnych przepływu pracy, aby zawierać dane, argumenty są tworzone w Projektancie przepływów pracy i wartości są przekazywane w z hosta, gdy przepływ pracy zostanie wywołany.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>Do hostowania działania PolicyActivity za pomocą przepływu pracy utworzone w Projektancie przepływu pracy  
  
1.  Kliknij prawym przyciskiem myszy **Workflow1.xaml** w **Eksploratora rozwiązań** i wybierz **Usuń**. Kliknij przycisk **OK** o potwierdzenie.  
  
2.  Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element...** .  
  
3.  Rozwiń **elementy Visual C#** a następnie wybierz węzeł **przepływu pracy**. Wybierz **działania** z **elementy Visual C#** listy.  
  
4.  Typ `DiscountWorkflow` do **nazwa** pole, a następnie kliknij przycisk **Dodaj**.  
  
5.  Kliknij przycisk **argumenty** przycisku w lewej dolnej części projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.  
  
6.  Kliknij przycisk **utworzenia argumentu**.  
  
7.  Typ `Subtotal` do **nazwa** wybierz opcję **w** z **kierunek** listę rozwijaną, wybierz opcję **Double** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.  
  
    > [!NOTE]
    >  Jeśli **Double** nie znajduje się w **typ argumentu** listy rozwijanej wybierz **vyhledat typy...** , typ `System.Double` w **nazwy typu** polu, a następnie kliknij przycisk **OK**.  
  
8.  Kliknij przycisk **utworzenia argumentu**.  
  
9. Typ `DiscountPercent` do **nazwa** wybierz opcję **się** z **kierunek** listę rozwijaną, wybierz opcję **Double** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.  
  
10. Kliknij przycisk **utworzenia argumentu**.  
  
11. Typ `Total` do **nazwa** wybierz opcję **się** z **kierunek** listę rozwijaną, wybierz opcję **Double** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argumentu.  
  
12. Kliknij przycisk **argumenty** przycisku w lewej dolnej części projektanta przepływów pracy, aby zamknąć **argumenty** okienka.  
  
13. Przeciągnij **sekwencji** działanie z **przepływ sterowania** części **przybornika** i upuść go na powierzchnię projektanta przepływu pracy.  
  
14. Przeciągnij **międzyoperacyjności** działanie z **migracji** części **przybornika** i upuść je **sekwencji** działania.  
  
15. Kliknij przycisk **międzyoperacyjności** działanie **kliknij, aby przeglądać...** etykiety, wpisz **DiscountCalculator** w **nazwy typu** polu, a następnie kliknij przycisk **OK**.  
  
    > [!NOTE]
    >  Gdy <xref:System.Activities.Statements.Interop> dodaniu działania do przepływu pracy i `DiscountCalculator` typ jest określony jako jego <xref:System.Activities.Statements.Interop.ActivityType%2A>, <xref:System.Activities.Statements.Interop> działalność opisuje trzy <xref:System.Activities.ArgumentDirection.In> argumentów i trzy <xref:System.Activities.ArgumentDirection.Out> argumenty, które reprezentują trzy publiczny właściwości `DiscountCalculator` działania. <xref:System.Activities.ArgumentDirection.In> Argumenty mają taką samą nazwę jak trzy właściwości publiczne i trzy <xref:System.Activities.ArgumentDirection.Out> argumenty mają takie same nazwy z **się** dołączana do nazwy właściwości. W poniższych krokach argumenty przepływu pracy, utworzony w poprzednich krokach jest powiązana z <xref:System.Activities.Statements.Interop> argumentów tego działania.  
  
16. Typ `DiscountPercent` do **wprowadź wyrażenie VB** pole po prawej stronie **DiscountPercentOut** właściwość i naciśnij klawisz TAB.  
  
17. Typ `Subtotal` do **wprowadź wyrażenie VB** pole po prawej stronie **Suma częściowa** właściwość i naciśnij klawisz TAB.  
  
18. Typ `Total` do **wprowadź wyrażenie VB** pole po prawej stronie **TotalOut** właściwość i naciśnij klawisz TAB.  
  
19. Kliknij prawym przyciskiem myszy **Program.cs** w **Eksploratora rozwiązań** i wybierz **Wyświetl kod**.  
  
20. Dodaj następujący kod `using` instrukcji w górnej części pliku.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. Komentarz wywołanie `CalculateDiscountInCode` method in Class metoda `Main` metody i Dodaj następujący kod.  
  
    > [!NOTE]
    >  Jeśli użytkownik nie korzystał z poprzedniej procedury oraz domyślnych `Main` kod, Zastąp zawartość `Main` następującym kodem.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. Utworzenie nowej metody w `Program` klasę o nazwie `CalculateDiscountUsingDesignerWorkflow` zawierający poniższy kod.  
  
    ```csharp  
    static void CalculateDiscountUsingDesignerWorkflow()  
    {  
        double SubtotalValue = 125.99;  
        Dictionary<string, object> wfargs = new Dictionary<string, object>  
        {  
            {"Subtotal", SubtotalValue}  
        };  
  
        Activity wf = new DiscountWorkflow();  
  
        IDictionary<string, object> outputs =  
            WorkflowInvoker.Invoke(wf, wfargs);  
  
        Console.WriteLine("Subtotal: {0:C}, Discount {1}%, Total {2:C}",  
            SubtotalValue, (double)outputs["DiscountPercent"] * 100,  
            outputs["Total"]);  
    }  
    ```  
  
23. Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację. Aby określić inną `Subtotal` amount, zmień wartość właściwości `SubtotalValue` w poniższym kodzie.  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>Omówienie funkcji reguły  
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] Aparatu reguł umożliwia przetwarzanie reguł w sposób oparte na priorytetach obsługę do przodu łańcucha. Zasady mogą być obliczane dla pojedynczego elementu lub elementów w kolekcji. Omówienie zasad i informacji na temat funkcji określone zasady można znaleźć w poniższej tabeli.  
  
|Funkcja reguł|Dokumentacja|  
|-------------------|-------------------|  
|Omówienie reguł|[Wprowadzenie do aparatu reguł programu Windows Workflow Foundation](https://go.microsoft.com/fwlink/?LinkID=152836)|  
|Zestaw reguł|[Używanie zestawów reguł w przepływach pracy](https://go.microsoft.com/fwlink/?LinkId=178516) i <xref:System.Workflow.Activities.Rules.RuleSet>|  
|Ocena zasad|[Obliczanie reguł w zestawy reguł](https://go.microsoft.com/fwlink/?LinkId=178517)|  
|Zasady łańcucha|[Do przodu łańcucha kontroli](https://go.microsoft.com/fwlink/?LinkId=178518) i [do przodu łańcucha reguł](https://go.microsoft.com/fwlink/?LinkId=178519)|  
|Przetwarzanie kolekcje reguł|[Przetwarzanie kolekcje reguł](https://go.microsoft.com/fwlink/?LinkId=178520)|  
|Za pomocą działania PolicyActivity|[Przy użyciu działania działania PolicyActivity](https://go.microsoft.com/fwlink/?LinkId=178521) i <xref:System.Workflow.Activities.PolicyActivity>|  
  
 Przepływy pracy utworzone w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] nie należy używać wszystkich reguł funkcji oferowanych przez [!INCLUDE[wf1](../../../includes/wf1-md.md)], takich jak warunki deklaratywne działania i warunkowego działań, takich jak <xref:System.Workflow.Activities.ConditionedActivityGroup> i <xref:System.Workflow.Activities.ReplicatorActivity>. Jeśli jest to wymagane, ta funkcja jest dostępna dla przepływów pracy utworzony za pomocą [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Aby uzyskać więcej informacji, zobacz [wskazówek dotyczących migracji](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).
