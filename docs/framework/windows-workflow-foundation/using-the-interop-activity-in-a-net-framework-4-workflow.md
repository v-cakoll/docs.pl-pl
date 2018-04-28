---
title: Za pomocą działania Interop w przepływie pracy .NET Framework 4
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9bb747f0-eb33-4f70-84cd-317382372dcd
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: ebef74097d22c9624a29470f4cda231bbb32fe90
ms.sourcegitcommit: 03ee570f6f528a7d23a4221dcb26a9498edbdf8c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2018
---
# <a name="using-the-interop-activity-in-a-net-framework-4-workflow"></a>Za pomocą działania Interop w przepływie pracy .NET Framework 4
Działania utworzone przy użyciu [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] lub [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] mogą być używane w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy przy użyciu <xref:System.Activities.Statements.Interop> działania. Ten temat zawiera omówienie sposobu użycia <xref:System.Activities.Statements.Interop> działania.  
  
> [!NOTE]
>  <xref:System.Activities.Statements.Interop> Przybornika projektanta przepływów pracy nie ma działania, chyba że ma projektu przepływu pracy jego **platformy docelowej** ustawienie **.Net Framework 4** lub nowszym.  
  
## <a name="using-the-interop-activity-in-net-framework-45-workflows"></a>Za pomocą działania Interop w przepływach pracy programu .NET Framework 4.5  
 W tym temacie [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] utworzeniu biblioteki działania, który zawiera `DiscountCalculator` działania. `DiscountCalculator` Jest obliczana na podstawie kwoty zakupu rabat i składa się z <xref:System.Workflow.Activities.SequenceActivity> zawierający <xref:System.Workflow.Activities.PolicyActivity>.  
  
> [!NOTE]
>  [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] Używa działanie utworzone w tym temacie <xref:System.Workflow.Activities.PolicyActivity> wdrożyć logikę działania. Nie jest wymagane do używania niestandardowej [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)] działania lub <xref:System.Activities.Statements.Interop> działania, aby można było używać reguł w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy. Na przykład przy użyciu reguł w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy bez użycia <xref:System.Activities.Statements.Interop> działania, zobacz [działania zasad w programie .NET Framework 4.5](../../../docs/framework/windows-workflow-foundation/samples/policy-activity-in-net-framework-4-5.md) próbki.  
  
#### <a name="to-create-the-net-framework-35-activity-library-project"></a>Aby utworzyć projekt biblioteki działań programu .NET Framework 3.5  
  
1.  Otwórz [!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] i wybierz **nowy** , a następnie **projektu...** z **pliku** menu.  
  
2.  Rozwiń węzeł **inne typy projektów** w węźle **zainstalowane szablony** okienka, a następnie wybierz **rozwiązań programu Visual Studio**.  
  
3.  Wybierz **puste rozwiązanie** z **rozwiązań programu Visual Studio** listy. Typ `PolicyInteropDemo` w **nazwa** polu i kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **PolicyInteropDemo** w **Eksploratora rozwiązań** i wybierz **Dodaj** , a następnie **nowy projekt...** .  
  
    > [!TIP]
    >  Jeśli **Eksploratora rozwiązań** okno nie jest widoczny, wybierz pozycję **Eksploratora rozwiązań** z **widoku** menu.  
  
5.  W **zainstalowane szablony** listy, wybierz **Visual C#** , a następnie **przepływu pracy**. Wybierz **.NET Framework 3.5** z listy rozwijanej wersji .NET Framework, a następnie wybierz **biblioteki działań przepływów pracy** z **szablony** listy.  
  
6.  Typ `PolicyActivityLibrary` w **nazwa** polu i kliknij przycisk **OK**.  
  
7.  Kliknij prawym przyciskiem myszy **Activity1.cs** w **Eksploratora rozwiązań** i wybierz **usunąć**. Kliknij przycisk **OK** o potwierdzenie.  
  
#### <a name="to-create-the-discountcalculator-activity"></a>Aby utworzyć działanie DiscountCalculator  
  
1.  Kliknij prawym przyciskiem myszy **PolicyActivityLibrary** w **Eksploratora rozwiązań** i wybierz **Dodaj** , a następnie **działanie...** .  
  
2.  Wybierz **działania (z separacją kodu)** z **Visual C# elementów** listy. Typ `DiscountCalculator` w **nazwa** polu i kliknij przycisk **OK**.  
  
3.  Kliknij prawym przyciskiem myszy **DiscountCalculator.xoml** w **Eksploratora rozwiązań** i wybierz **kod widoku**.  
  
4.  Dodaj następujące trzy właściwości `DiscountCalculator` klasy.  
  
    ```csharp  
    public partial class DiscountCalculator : SequenceActivity  
    {  
        public double Subtotal { get; set; }  
        public double DiscountPercent { get; set; }  
        public double Total { get; set; }  
    }  
    ```  
  
5.  Kliknij prawym przyciskiem myszy **DiscountCalculator.xoml** w **Eksploratora rozwiązań** i wybierz **Widok projektanta**.  
  
6.  Przeciągnij **zasad** działania z **Windows Workflow 3.0** sekcji **przybornika** i upuść je w **DiscountCalculator** działania .  
  
    > [!TIP]
    >  Jeśli **przybornika** okno nie jest widoczny, wybierz pozycję **przybornika** z **widoku** menu.  
  
#### <a name="to-configure-the-rules"></a>Aby skonfigurować reguły  
  
1.  Kliknij nowo dodany **zasad** działania, aby wybrać, jeśli nie została jeszcze wybrana.  
  
2.  Kliknij przycisk **RuleSetReference** właściwości w **właściwości** okno, aby go zaznaczyć, a następnie kliknij przycisk wielokropka z prawej strony właściwości.  
  
    > [!TIP]
    >  Jeśli **właściwości** okna nie jest widoczne, wybierz **okna właściwości** z **widoku** menu.  
  
3.  Wybierz **kliknij nowy...** .  
  
4.  Kliknij przycisk **Dodaj regułę**.  
  
5.  Wpisz następujące wyrażenie w **warunku** pole.  
  
    ```  
    this.Subtotal >= 50 && this.Subtotal < 100  
    ```  
  
6.  Wpisz następujące wyrażenie w **następnie akcje** pole.  
  
    ```  
    this.DiscountPercent = 0.075  
    ```  
  
7.  Kliknij przycisk **Dodaj regułę**.  
  
8.  Wpisz następujące wyrażenie w **warunku** pole.  
  
    ```  
    this.Subtotal >= 100  
    ```  
  
9. Wpisz następujące wyrażenie w **następnie akcje** pole.  
  
    ```  
    this.DiscountPercent = 0.15  
    ```  
  
10. Kliknij przycisk **Dodaj regułę**.  
  
11. Wpisz następujące wyrażenie w **warunku** pole.  
  
    ```  
    this.DiscountPercent > 0  
    ```  
  
12. Wpisz następujące wyrażenie w **następnie akcje** pole.  
  
    ```  
    this.Total = this.Subtotal - this.Subtotal * this.DiscountPercent  
    ```  
  
13. Wpisz następujące wyrażenie w **Else akcje** pole.  
  
    ```  
    this.Total = this.Subtotal  
    ```  
  
14. Kliknij przycisk **OK** zamknąć **Edytor ustawić reguły** okno dialogowe.  
  
15. Upewnij się, że nowo utworzonego <xref:System.Workflow.Activities.Rules.RuleSet> wybrano **nazwa** listy, a następnie kliknij przycisk **OK**.  
  
16. Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
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
  
 Podczas <xref:System.Workflow.Activities.PolicyActivity> wykonuje te trzy zasady oceny i zmodyfikuj `Subtotal`, `DiscountPercent`, i `Total` wartości właściwości `DiscountCalculator` do obliczania rabatu odpowiednie działania.  
  
## <a name="using-the-discountcalculator-activity-with-the-interop-activity"></a>Używanie działania DiscountCalculator z działania Interop  
 Aby użyć `DiscountCalculator` działania wewnątrz [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] przepływu pracy, <xref:System.Activities.Statements.Interop> to działanie służy. W tej sekcji dwa przepływy pracy są tworzone, jeden przy użyciu kodu i jeden za pomocą projektanta przepływów pracy, które pokazują, jak używać <xref:System.Activities.Statements.Interop> działania `DiscountCalculator` działania. Ta sama aplikacja hosta jest używana dla obu przepływów pracy.  
  
#### <a name="to-create-the-host-application"></a>Aby utworzyć aplikację hosta  
  
1.  Kliknij prawym przyciskiem myszy **PolicyInteropDemo** w **Eksploratora rozwiązań** i wybierz **Dodaj**, a następnie **nowy projekt...** .  
  
2.  Upewnij się, że **.NET Framework 4.5** jest zaznaczona na liście rozwijanej wersji .NET Framework, a następnie wybierz **Aplikacja konsoli przepływu pracy** z **Visual C# elementów** listy.  
  
3.  Typ `PolicyInteropHost` do **nazwa** polu i kliknij przycisk **OK**.  
  
4.  Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **właściwości**.  
  
5.  W **platformy docelowej** listy rozwijanej liście, wybór z **.NET Framework 4 Client Profile** do **.NET Framework 4.5**. Kliknij przycisk **tak** o potwierdzenie.  
  
6.  Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **Dodawanie odwołania...** .  
  
7.  Wybierz **PolicyActivityLibrary** z **projekty** i kliknij polecenie **OK**.  
  
8.  Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **Dodawanie odwołania...** .  
  
9. Wybierz **System.Workflow.Activities**, **System.Workflow.ComponentModel**, a następnie **System.Workflow.Runtime** z **.NET**i kliknij polecenie **OK**.  
  
10. Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **Ustaw jako projekt startowy**.  
  
11. Naciśnij klawisze CTRL + SHIFT + B w celu skompilowania rozwiązania.  
  
### <a name="using-the-interop-activity-in-code"></a>Za pomocą działania Interop w kodzie  
 W tym przykładzie definicji przepływu pracy jest tworzony przy użyciu kodu, który zawiera <xref:System.Activities.Statements.Interop> działania i `DiscountCalculator` działania. Ten przepływ pracy jest wywoływana przy użyciu <xref:System.Activities.WorkflowInvoker> i wyniki oceny reguły są zapisywane w konsoli przy użyciu <xref:System.Activities.Statements.WriteLine> działania.  
  
##### <a name="to-use-the-interop-activity-in-code"></a>Aby użyć działania Interop w kodzie  
  
1.  Kliknij prawym przyciskiem myszy **Program.cs** w **Eksploratora rozwiązań** i wybierz **kod widoku**.  
  
2.  Dodaj następujące `using` instrukcji w górnej części pliku.  
  
    ```csharp  
    using PolicyActivityLibrary;  
    ```  
  
3.  Usuń zawartość `Main` metodę i Zastąp następujący kod.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
4.  Utworzenie nowej metody w `Program` klasy o nazwie `CalculateDiscountUsingCodeWorkflow` zawierający następujący kod.  
  
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
    >  `Subtotal`, `DiscountPercent`, I `Total` właściwości `DiscountCalculator` działania są udostępniane jako argumenty <xref:System.Activities.Statements.Interop> działania i zmienne powiązane z lokalnego przepływu pracy w <xref:System.Activities.Statements.Interop> działania <xref:System.Activities.Statements.Interop.ActivityProperties%2A> Kolekcja. `Subtotal` zostanie dodany jako <xref:System.Activities.ArgumentDirection.In> argument ponieważ `Subtotal` dane przepływają w <xref:System.Activities.Statements.Interop> działania, i `DiscountPercent` i `Total` są dodawane jako <xref:System.Activities.ArgumentDirection.Out> argumenty ponieważ ich dane przepływają poza <xref:System.Activities.Statements.Interop> działania. Należy pamiętać, że dwa <xref:System.Activities.ArgumentDirection.Out> argumenty są dodawane z nazwami `DiscountPercentOut` i `TotalOut` aby wskazać, że reprezentują <xref:System.Activities.ArgumentDirection.Out> argumentów. `DiscountCalculator` Typ jest określony jako <xref:System.Activities.Statements.Interop> działania <xref:System.Activities.Statements.Interop.ActivityType%2A>.  
  
5.  Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację. Zastąp różnych wartości `Subtotal` wartość przetestować poziomy różnych rabat pochodzącymi `DiscountCalculator` działania.  
  
    ```csharp  
    Variable<double> Subtotal = new Variable<double>  
    {  
        Default = 75.99, // Change this value.  
        Name = "Subtotal"  
    };  
    ```  
  
### <a name="using-the-interop-activity-in-the-workflow-designer"></a>Za pomocą działania Interop w Projektancie przepływów pracy  
 W tym przykładzie przepływ pracy jest tworzony przy użyciu projektanta przepływów pracy. Ten przepływ pracy ma te same funkcje co w poprzednim przykładzie, z wyjątkiem niż zamiast <xref:System.Activities.Statements.WriteLine> działanie, aby wyświetlić rabatu aplikacji hosta pobiera i wyświetla informacje o rabat po zakończeniu przepływu pracy. Ponadto zamiast za pomocą zmiennych lokalnych przepływu pracy zawierają dane, argumenty są tworzone w Projektancie przepływów pracy i wartości są przekazywane w z hosta po wywołaniu przepływ pracy.  
  
##### <a name="to-host-the-policyactivity-using-a-workflow-designer-created-workflow"></a>Do obsługi działania PolicyActivity za pomocą przepływu pracy utworzone w Projektancie przepływów pracy  
  
1.  Kliknij prawym przyciskiem myszy **Workflow1.xaml** w **Eksploratora rozwiązań** i wybierz **usunąć**. Kliknij przycisk **OK** o potwierdzenie.  
  
2.  Kliknij prawym przyciskiem myszy **PolicyInteropHost** w **Eksploratora rozwiązań** i wybierz **Dodaj**, **nowy element...** .  
  
3.  Rozwiń węzeł **Visual C# elementów** a następnie wybierz węzeł **przepływu pracy**. Wybierz **działania** z **Visual C# elementów** listy.  
  
4.  Typ `DiscountWorkflow` do **nazwa** polu i kliknij przycisk **Dodaj**.  
  
5.  Kliknij przycisk **argumenty** przycisk na dole po lewej stronie projektanta przepływów pracy, aby wyświetlić **argumenty** okienka.  
  
6.  Kliknij przycisk **utworzenia argumentu**.  
  
7.  Typ `Subtotal` do **nazwa** wybierz opcję **w** z **kierunek** listy rozwijanej, wybierz pozycję **podwójne** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
    > [!NOTE]
    >  Jeśli **podwójne** nie znajduje się w **typ argumentu** listy rozwijanej wybierz **Przeglądaj w poszukiwaniu typów...** , typ `System.Double` w **nazwy typu** i kliknij **OK**.  
  
8.  Kliknij przycisk **utworzenia argumentu**.  
  
9. Typ `DiscountPercent` do **nazwa** wybierz opcję **limit** z **kierunek** listy rozwijanej, wybierz pozycję **podwójne** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
10. Kliknij przycisk **utworzenia argumentu**.  
  
11. Typ `Total` do **nazwa** wybierz opcję **limit** z **kierunek** listy rozwijanej, wybierz pozycję **podwójne** z **Typ argumentu** listy rozwijanej, a następnie naciśnij klawisz ENTER, aby zapisać argument.  
  
12. Kliknij przycisk **argumenty** przycisk na dole po lewej stronie projektanta przepływów pracy, aby zamknąć **argumenty** okienka.  
  
13. Przeciągnij **sekwencji** działania z **przepływ sterowania** sekcji **przybornika** i upuść ją na powierzchnię projektanta przepływów pracy.  
  
14. Przeciągnij **międzyoperacyjności** działania z **migracji** sekcji **przybornika** i upuść je w **sekwencji** działania.  
  
15. Kliknij przycisk **międzyoperacyjności** działania na **kliknij, aby przeglądać...** Etykieta, wpisz **DiscountCalculator** w **nazwy typu** i kliknij **OK**.  
  
    > [!NOTE]
    >  Gdy <xref:System.Activities.Statements.Interop> działania zostanie dodany do przepływu pracy i `DiscountCalculator` typ jest określony jako jego <xref:System.Activities.Statements.Interop.ActivityType%2A>, <xref:System.Activities.Statements.Interop> działania udostępnia trzy <xref:System.Activities.ArgumentDirection.In> argumentów i trzy <xref:System.Activities.ArgumentDirection.Out> argumenty, które reprezentują trzy publicznego właściwości `DiscountCalculator` działania. <xref:System.Activities.ArgumentDirection.In> Argumenty mają taką samą nazwę jak trzy właściwości publiczne i trzech <xref:System.Activities.ArgumentDirection.Out> argumenty mają takie same nazwy z **limit** dołączonym do nazwy właściwości. W poniższych krokach argumenty przepływu pracy utworzone w poprzednich krokach jest powiązana z <xref:System.Activities.Statements.Interop> argumentów działania.  
  
16. Typ `DiscountPercent` do **wprowadź wyrażenia języka VB.** pole z prawej strony **DiscountPercentOut** właściwości i naciśnij klawisz TAB.  
  
17. Typ `Subtotal` do **wprowadź wyrażenia języka VB.** pole z prawej strony **Suma częściowa** właściwości i naciśnij klawisz TAB.  
  
18. Typ `Total` do **wprowadź wyrażenia języka VB.** pole z prawej strony **TotalOut** właściwości i naciśnij klawisz TAB.  
  
19. Kliknij prawym przyciskiem myszy **Program.cs** w **Eksploratora rozwiązań** i wybierz **kod widoku**.  
  
20. Dodaj następujące `using` instrukcji w górnej części pliku.  
  
    ```csharp  
    using System.Collections.Generic;  
    ```  
  
21. Komentarz wywołanie `CalculateDiscountInCode` metoda `Main` — metoda i Dodaj następujący kod.  
  
    > [!NOTE]
    >  Jeśli nie wykonaniu poprzedniej procedury i domyślnie `Main` kodu, Zastąp zawartość `Main` z następującym kodem.  
  
    ```csharp  
    static void Main(string[] args)  
    {  
        CalculateDiscountUsingDesignerWorkflow();  
        //CalculateDiscountUsingCodeWorkflow();  
    }  
    ```  
  
22. Utworzenie nowej metody w `Program` klasy o nazwie `CalculateDiscountUsingDesignerWorkflow` zawierający następujący kod.  
  
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
  
23. Naciśnij klawisze CTRL + F5, aby skompilować i uruchomić aplikację. Aby określić inną `Subtotal` ilość, zmień wartość `SubtotalValue` w poniższym kodzie.  
  
    ```csharp  
    double SubtotalValue = 125.99; // Change this value.  
    ```  
  
## <a name="rules-features-overview"></a>Przegląd funkcji reguły  
 [!INCLUDE[wf1](../../../includes/wf1-md.md)] Aparatu reguł zapewnia obsługę przetwarzania reguły w sposób oparte na priorytetach obsługę do przodu łańcucha. Reguły może przyjąć pojedynczy element lub elementy w kolekcji. Omówienie zasad i informacji na temat reguł określonych funkcji można znaleźć w poniższej tabeli.  
  
|Funkcja reguł|Dokumentacja|  
|-------------------|-------------------|  
|Przegląd zasad|[Wprowadzenie do aparatu reguł systemu Windows Workflow Foundation](http://go.microsoft.com/fwlink/?LinkID=152836)|  
|Zestaw reguł|[Używanie zestawów reguł w przepływach pracy](http://go.microsoft.com/fwlink/?LinkId=178516) i <xref:System.Workflow.Activities.Rules.RuleSet>|  
|Ocena zasad|[Zasady oceny w zestawy reguł](http://go.microsoft.com/fwlink/?LinkId=178517)|  
|Reguły łańcucha|[Przekazuj łańcucha kontroli](http://go.microsoft.com/fwlink/?LinkId=178518) i [do przodu łańcucha zasad](http://go.microsoft.com/fwlink/?LinkId=178519)|  
|Przetwarzanie kolekcje reguł|[Przetwarzanie kolekcje reguł](http://go.microsoft.com/fwlink/?LinkId=178520)|  
|Za pomocą działania PolicyActivity|[Za pomocą działania działania PolicyActivity](http://go.microsoft.com/fwlink/?LinkId=178521) i <xref:System.Workflow.Activities.PolicyActivity>|  
  
 Przepływy pracy utworzone w [!INCLUDE[netfx_current_short](../../../includes/netfx-current-short-md.md)] nie korzystać ze wszystkich funkcji zasad udostępnionych przez [!INCLUDE[wf1](../../../includes/wf1-md.md)], takie jak warunki deklaratywne działania i warunkowego działań, takich jak <xref:System.Workflow.Activities.ConditionedActivityGroup> i <xref:System.Workflow.Activities.ReplicatorActivity>. Jeśli jest to wymagane, ta funkcja jest dostępna dla przepływów pracy utworzony za pomocą [!INCLUDE[vstecwinfx](../../../includes/vstecwinfx-md.md)] i [!INCLUDE[netfx35_short](../../../includes/netfx35-short-md.md)]. Aby uzyskać więcej informacji, zobacz [wskazówki dotyczące migracji](../../../docs/framework/windows-workflow-foundation/migration-guidance.md).
