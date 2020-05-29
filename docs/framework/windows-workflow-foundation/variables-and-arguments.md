---
title: Zmienne i argumenty
description: W tym artykule opisano zmienne, które reprezentują magazyn danych i argumenty reprezentujące przepływ danych do/z działania w programie Workflow Foundation.
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 5cce9931e9b0a37d5fafbfb84527ffd543a0a50f
ms.sourcegitcommit: 71b8f5a2108a0f1a4ef1d8d75c5b3e129ec5ca1e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/29/2020
ms.locfileid: "84201955"
---
# <a name="variables-and-arguments"></a>Zmienne i argumenty
W Windows Workflow Foundation (WF) zmienne reprezentują magazyn danych i argumenty reprezentują przepływ danych do i z działania. Działanie ma zestaw argumentów i składają się na podpis działania. Ponadto działanie może obsługiwać listę zmiennych, do których deweloper może dodawać lub usuwać zmienne podczas projektowania przepływu pracy. Argument jest powiązany przy użyciu wyrażenia, które zwraca wartość.  
  
## <a name="variables"></a>Zmienne  
 Zmienne są lokalizacjami przechowywania danych. Zmienne są zadeklarowane jako część definicji przepływu pracy. Zmienne przyjmują wartości w czasie wykonywania, a te wartości są przechowywane jako część stanu wystąpienia przepływu pracy. Definicja zmiennej określa typ zmiennej i opcjonalnie nazwę. Poniższy kod pokazuje, jak zadeklarować zmienną, przypisać do niej wartość za pomocą <xref:System.Activities.Statements.Assign%601> działania, a następnie wyświetlić jej wartość w konsoli programu za pomocą <xref:System.Activities.Statements.WriteLine> działania.  
  
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
  
 Opcjonalnie można określić wyrażenie wartości domyślnej jako część deklaracji zmiennej. Zmienne mogą również mieć modyfikatory. Na przykład jeśli zmienna jest tylko do odczytu, można zastosować modyfikator tylko do odczytu <xref:System.Activities.VariableModifiers> . W poniższym przykładzie jest tworzona zmienna tylko do odczytu z przypisaną wartością domyślną.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Określanie zakresu zmiennych  
 Okres istnienia zmiennej w czasie wykonywania jest równy okresowi istnienia działania, które deklaruje je. Po zakończeniu działania jego zmienne są czyszczone i nie można już do nich odwoływać się.  
  
## <a name="arguments"></a>Argumenty  
 Autorzy działań używają argumentów do definiowania sposobu, w jaki dane są przesyłane do i z działania. Każdy argument ma określony kierunek: <xref:System.Activities.ArgumentDirection.In> , <xref:System.Activities.ArgumentDirection.Out> , lub <xref:System.Activities.ArgumentDirection.InOut> .  
  
 Środowisko uruchomieniowe przepływu pracy zapewnia następujące gwarancje dotyczące chronometrażu przenoszenia danych do i z działań:  
  
1. Po rozpoczęciu działania wykonywane są wartości wszystkich argumentów wejściowych i wejściowych i wyjściowych. Na przykład bez względu <xref:System.Activities.Argument.Get%2A> na to, że zwracana wartość jest wartością obliczoną przez środowisko uruchomieniowe przed wywołaniem metody `Execute` .  
  
2. Gdy <xref:System.Activities.InOutArgument%601.Set%2A> jest wywoływana, środowisko uruchomieniowe natychmiast ustawia wartość.  
  
3. Argumenty mogą opcjonalnie mieć <xref:System.Activities.Argument.EvaluationOrder%2A> określone. <xref:System.Activities.Argument.EvaluationOrder%2A>jest wartością zerową, która określa kolejność, w której argument jest oceniany. Domyślnie kolejność oceny argumentu nie jest określona i jest równa <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> wartości. Ustaw <xref:System.Activities.Argument.EvaluationOrder%2A> wartość większą lub równą zero, aby określić kolejność szacowania dla tego argumentu. Windows Workflow Foundation ocenia argumenty z określoną kolejnością szacowania w kolejności rosnącej. Należy zauważyć, że argumenty z nieokreśloną kolejnością szacowania są oceniane przed tymi z określoną kolejnością szacowania.  
  
 Autor działania może użyć mechanizmu o jednoznacznie określonym typie do ujawnienia swoich argumentów. Jest to realizowane przez deklarując właściwości typu <xref:System.Activities.InArgument%601> , <xref:System.Activities.OutArgument%601> , i <xref:System.Activities.InOutArgument%601> . Dzięki temu autor działania może ustanowić konkretną umowę dotyczącą danych przechodzących do działania i z niego.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Definiowanie argumentów dla działania  
 Argumenty można definiować w działaniu, określając właściwości typu <xref:System.Activities.InArgument%601> , <xref:System.Activities.OutArgument%601> , i <xref:System.Activities.InOutArgument%601> . Poniższy kod ilustruje sposób definiowania argumentów dla `Prompt` działania pobierającego ciąg, który ma być wyświetlany użytkownikowi i zwraca ciąg zawierający odpowiedź użytkownika.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> Działania zwracające pojedynczą wartość mogą pochodzić od <xref:System.Activities.Activity%601> , <xref:System.Activities.NativeActivity%601> , lub <xref:System.Activities.CodeActivity%601> . Te działania mają dobrze zdefiniowaną <xref:System.Activities.OutArgument%601> nazwę <xref:System.Activities.Activity%601.Result%2A> , która zawiera wartość zwracaną działania.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Używanie zmiennych i argumentów w przepływach pracy  
 Poniższy przykład pokazuje, jak zmienne i argumenty są używane w przepływie pracy. Przepływ pracy to sekwencja, która deklaruje trzy zmienne: `var1` , `var2` , i `var3` . Pierwsze działanie w przepływie pracy to `Assign` działanie, które przypisuje wartość zmiennej `var1` do zmiennej `var2` . Następuje to `WriteLine` działanie, które drukuje wartość `var2` zmiennej. Dalej jest innym `Assign` działaniem, które przypisuje wartość zmiennej `var2` do zmiennej `var3` . Na koniec istnieje inne `WriteLine` działanie, które drukuje wartość `var3` zmiennej. Pierwsze `Assign` działanie korzysta z `InArgument<string>` `OutArgument<string>` obiektów, które jawnie reprezentują powiązania dla argumentów działania. `InArgument<string>`jest używany w przypadku <xref:System.Activities.Statements.Assign.Value%2A> , gdy wartość jest przepływa do <xref:System.Activities.Statements.Assign%601> działania za pomocą jego <xref:System.Activities.Statements.Assign.Value%2A> argumentu i `OutArgument<string>` jest używana dla, <xref:System.Activities.Statements.Assign.To%2A> ponieważ wartość przepływa z <xref:System.Activities.Statements.Assign.To%2A> argumentu do zmiennej. Drugie działanie wykonuje tę `Assign` samą czynność z bardziej zwartą, ale równoważną składnią, która używa niejawnych rzutowania. `WriteLine`Działania również używają składni kompaktowej.  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Używanie zmiennych i argumentów w działaniach opartych na kodzie  
 Poprzednie przykłady pokazują, jak używać argumentów i zmiennych w przepływach pracy i działaniach deklaratywnych. Argumenty i zmienne są również używane w działaniach opartych na kodzie. Koncepcje użycia są bardzo podobne. Zmienne reprezentują magazyn danych w ramach działania, a argumenty reprezentują przepływ danych do działania lub z niego, i są powiązane przez autora przepływu pracy z innymi zmiennymi lub argumentami w przepływie pracy, które reprezentują miejsce, do którego dane są przesyłane do lub z. Aby uzyskać lub ustawić wartość zmiennej lub argumentu w działaniu, należy użyć kontekstu działania, który reprezentuje bieżące środowisko wykonywania działania. Jest to przesyłane do <xref:System.Activities.CodeActivity%601.Execute%2A> metody działania przez środowisko uruchomieniowe przepływu pracy. W tym przykładzie `Add` zdefiniowano działanie niestandardowe, które ma dwa <xref:System.Activities.ArgumentDirection.In> argumenty. Aby uzyskać dostęp do wartości argumentów, używana jest <xref:System.Activities.Argument.Get%2A> Metoda oraz kontekst, który został przekazane przez środowisko uruchomieniowe przepływu pracy.  
  
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
  
 Aby uzyskać więcej informacji na temat pracy z argumentami, zmiennymi i wyrażeniami w kodzie, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md) [obowiązkowego oraz wymaganych argumentów i grup przeciążeń](required-arguments-and-overload-groups.md).
