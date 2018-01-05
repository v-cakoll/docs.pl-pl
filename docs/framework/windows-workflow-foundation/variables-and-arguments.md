---
title: Argumenty i zmienne
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d01c31cce9aa6ae6d87773fc8e616e0e08bbd8c8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="variables-and-arguments"></a>Argumenty i zmienne
W [!INCLUDE[wf](../../../includes/wf-md.md)], zmienne reprezentują magazynu danych i argumenty reprezentują przepływ danych do i z działania. Działanie ma zestaw argumentów i tworzą one podpisu działania. Ponadto działania można zachować listę zmiennych, których projektant można dodawać i usuwać zmienne podczas projektowania przepływu pracy. Argument jest powiązany za pomocą wyrażenia, która nie zwraca wartości.  
  
## <a name="variables"></a>Zmienne  
 Zmienne są lokalizacje magazynu dla danych. Zmienne są deklarowane jako część definicji przepływu pracy. Zmienne Przełącz wartości w czasie wykonywania, a te wartości są przechowywane w ramach stanu wystąpienia przepływu pracy. Definicja zmiennej określa typu zmienną, i opcjonalnie nazwy. Poniższy kod przedstawia sposób zadeklarować zmiennej, przypisywanie wartości do niej przy użyciu <xref:System.Activities.Statements.Assign%601> działania, a następnie wyświetl jego wartość przy użyciu konsoli <xref:System.Activities.Statements.WriteLine> działania.  
  
```csharp  
// Define a variable named "str" of type string.  
Variable<string> var = new Variable<string>  
{  
    Name = "str"  
};  
  
// Declare the variable within a Sequence, assign  
// a value to it, and then display it.  
Activity wf = new Sequence()  
{  
    Variables = { var },  
    Activities =  
    {  
        new Assign<string>  
        {  
            To = var,  
            Value = "Hello World."  
        },  
        new WriteLine  
        {  
            Text = var  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 Opcjonalnie można określić wyrażenie wartości domyślnej w ramach deklaracji zmiennej. Zmienne można również mieć modyfikatorów. Na przykład jeśli zmienna jest tylko do odczytu, a następnie tylko do odczytu <xref:System.Activities.VariableModifiers> modyfikator mogą być stosowane. W poniższym przykładzie utworzono zmiennej tylko do odczytu, która ma przypisaną wartość domyślną.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Zakres zmiennej  
 Okres istnienia zmienną w czasie wykonywania jest równa okres istnienia działania, który deklaruje go. Po zakończeniu działania, zmienne są wyczyszczone, a nie może być przywoływany.  
  
## <a name="arguments"></a>Argumenty  
 Autorzy działania używać argumentów do definiowania danych sposób przepływy do i z działania. Każdy argument ma kierunek określony: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, lub <xref:System.Activities.ArgumentDirection.InOut>.  
  
 Środowiska uruchomieniowego przepływu pracy wykonuje następujące gwarancje o czas przenoszenia danych do i z działania:  
  
1.  Po uruchomieniu działania wykonywane są obliczane wartości wszystkich argumentów wejściowych i operacjami wejścia/wyjścia. Na przykład, niezależnie od tego, kiedy <xref:System.Activities.Argument.Get%2A> jest wywoływana, zwracana wartość jest obliczana co w czasie wykonywania przed jej wywołanie `Execute`.  
  
2.  Gdy <xref:System.Activities.InOutArgument%601.Set%2A> jest wywoływana, środowisko uruchomieniowe ustawia wartość natychmiast.  
  
3.  Opcjonalnie może mieć argumentów ich <xref:System.Activities.Argument.EvaluationOrder%2A> określony. <xref:System.Activities.Argument.EvaluationOrder%2A>jest liczony od zera wartość, która określa kolejność, w jakiej są oceniane argument. Domyślnie kolejność obliczania argumentu nie jest określona i jest równa <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> wartość. Ustaw <xref:System.Activities.Argument.EvaluationOrder%2A> na wartość większą lub równą zero, aby określić kolejność obliczania dla tego argumentu. [!INCLUDE[wf2](../../../includes/wf2-md.md)]oblicza argumentów, których kolejność obliczania określony w kolejności rosnącej. Należy pamiętać, że argumenty z kolejnością obliczania nieokreślony są oceniane przed elementami z kolejnością obliczania określony.  
  
 Przez autora działania można używać mechanizmu jednoznacznie udostępnianie argumenty. Jest to osiągane przez deklarowanie właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>. Dzięki temu przez autora działania nawiązać z określonym kontraktem o danych, przechodząc do i z działania.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Definiowanie argumenty w działaniu  
 Argumenty można zdefiniować w działaniu, określając właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>. Poniższy kod przedstawia sposób definiowania argumenty `Prompt` działania, która przyjmuje w ciągu do wyświetlenia dla użytkownika i zwraca ciąg zawierający odpowiedzi użytkownika.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  Działania, które zwraca pojedynczą wartość może pochodzić od <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, lub <xref:System.Activities.CodeActivity%601>. Te działania mają dobrze zdefiniowanego <xref:System.Activities.OutArgument%601> o nazwie <xref:System.Activities.Activity%601.Result%2A> zawiera wartość zwracaną przez działanie.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Używanie zmiennych i argumenty w przepływach pracy  
 W poniższym przykładzie pokazano, jak argumenty i zmienne są używane w przepływie pracy. Przepływ pracy jest sekwencji, który deklaruje trzy zmienne: `var1`, `var2`, i `var3`. Pierwsze działanie w przepływie pracy jest `Assign` działania, która przypisuje wartość zmiennej `var1` do zmiennej `var2`. Następuje to `WriteLine` działanie, które wartości `var2` zmiennej. Następnie jest inny `Assign` działania, która przypisuje wartość zmiennej `var2` do zmiennej `var3`. Na koniec istnieje inny `WriteLine` działanie, które wartości `var3` zmiennej. Pierwszy `Assign` używa działania `InArgument<string>` i `OutArgument<string>` obiekty reprezentujące jawnie powiązań dla argumentów działania. `InArgument<string>`Służy do <xref:System.Activities.Statements.Assign.Value%2A> , ponieważ wartość wejściowa jest do <xref:System.Activities.Statements.Assign%601> działania za pomocą jego <xref:System.Activities.Statements.Assign.Value%2A> argumentu, i `OutArgument<string>` służy do <xref:System.Activities.Statements.Assign.To%2A> , ponieważ wartość jest wynikających z <xref:System.Activities.Statements.Assign.To%2A> argument do zmiennej. Drugi `Assign` działania wykonuje ten sam efekt z więcej compact ale równoważne składnię, która używa niejawnego rzutowania. `WriteLine` Działań również użyć zwięzłą składnią.  
  
```csharp  
// Declare three variables; the first one is given an initial value.  
Variable<string> var1 = new Variable<string>()  
{  
    Default = "one"  
};  
Variable<string> var2 = new Variable<string>();  
Variable<string> var3 = new Variable<string>();  
  
// Define the workflow  
Activity wf = new Sequence  
{  
    Variables = { var1, var2, var3 },  
    Activities =   
    {  
        new Assign<string>()  
        {  
            Value = new InArgument<string>(var1),  
            To = new OutArgument<string>(var2)  
        },  
        new WriteLine() { Text = var2 },  
        new Assign<string>()  
        {  
            Value = var2,  
            To = var3  
        },  
        new WriteLine() { Text = var3 }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Użycie zmiennych i argumentów działania oparte na kodzie  
 W powyższym przykładzie pokazano sposób użycia argumentów i zmiennych w przepływach pracy i deklaratywne działań. Argumenty i zmienne są również używane w działaniach opartej na kodzie. Koncepcyjnie jest bardzo podobne. Zmienne reprezentują magazynu danych w ramach działania i argumenty reprezentują przepływ danych do lub z działania i są powiązane przez autora przepływu pracy do innych zmiennych lub argumentów w przepływie pracy reprezentujące, w którym dane przepływają do lub z. Get lub zestaw, który należy użyć wartości zmiennej lub argumentu w działaniu, kontekst działania reprezentujący aktualnego środowiska wykonawczego działania. To jest przekazywany do <xref:System.Activities.CodeActivity%601.Execute%2A> metody działania przez środowisko wykonawcze przepływu pracy. W tym przykładzie niestandardowego `Add` zdefiniowano zawiera dwa działania <xref:System.Activities.ArgumentDirection.In> argumentów. Aby uzyskać dostęp do wartości argumentów <xref:System.Activities.Argument.Get%2A> metoda jest używana i jest używany w kontekście, który został przekazany w czasie wykonywania przepływu pracy.  
  
```csharp  
public sealed class Add : CodeActivity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Operand1 { get; set; }  
  
    [RequiredArgument]  
    public InArgument<int> Operand2 { get; set; }  
  
    protected override int Execute(CodeActivityContext context)  
    {  
        return Operand1.Get(context) + Operand2.Get(context);  
    }  
}  
```  
  
 [!INCLUDE[crabout](../../../includes/crabout-md.md)]Praca z argumentami, zmienne i wyrażenia w kodzie, zobacz [tworzenia przepływów pracy, działań i kod Imperatywne przy użyciu wyrażenia](../../../docs/framework/windows-workflow-foundation/authoring-workflows-activities-and-expressions-using-imperative-code.md) i [wymaganych argumentów i grup przeciążenia](../../../docs/framework/windows-workflow-foundation/required-arguments-and-overload-groups.md).
