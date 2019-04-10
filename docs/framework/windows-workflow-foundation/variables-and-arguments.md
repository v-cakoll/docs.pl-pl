---
title: Zmienne i argumenty
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: 29ce5222435b68ed13cbc967e58e72a937625e8e
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2019
ms.locfileid: "59320746"
---
# <a name="variables-and-arguments"></a>Zmienne i argumenty
W Windows Workflow Foundation (WF), zmienne reprezentują przechowywania danych i argumenty reprezentują przepływ danych do i z działania. Działanie ma zestawu argumentów i stanowią one podpis działania. Ponadto działanie może zachować listę zmiennych, do których Deweloper można dodawać i usuwać zmiennych podczas projektowania przepływu pracy. Argument jest powiązany za pomocą wyrażenia, która nie zwraca wartości.  
  
## <a name="variables"></a>Zmienne  
 Zmienne są lokalizacje magazynu dla danych. Zmienne są deklarowane jako część definicji przepływu pracy. Zmienne przyjmą wartości w czasie wykonywania, a te wartości są przechowywane jako część stanu wystąpienia przepływu pracy. Definicja zmiennej określa typ zmiennej, i opcjonalnie nazwy. Poniższy kod pokazuje sposób deklarowania zmiennych, przypisz wartości do niego przy użyciu <xref:System.Activities.Statements.Assign%601> działania, a następnie wyświetl jego wartość za pomocą konsoli <xref:System.Activities.Statements.WriteLine> działania.  
  
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
  
 Opcjonalnie można określić wyrażenie wartości domyślnej jako część deklaracji zmiennej. Zmienne również może mieć modyfikatorów. Aby uzyskać przykład, jeśli zmienna jest tylko do odczytu, a następnie tylko do odczytu <xref:System.Activities.VariableModifiers> modyfikator mogą być stosowane. W poniższym przykładzie utworzono zmiennej tylko do odczytu, która ma przypisaną wartość domyślną.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Zmienna zakresu  
 Okres istnienia zmiennej w czasie wykonywania jest równy okres istnienia działania, który deklaruje ją. Po ukończeniu działania swoje zmienne są wyczyszczone, a nie będzie można się odwoływać.  
  
## <a name="arguments"></a>Argumenty  
 Autorzy działania używać argumentów do definiowania danych sposób przepływy do i z działania. Każdy argument ma określony kierunek: <xref:System.Activities.ArgumentDirection.In>, <xref:System.Activities.ArgumentDirection.Out>, lub <xref:System.Activities.ArgumentDirection.InOut>.  
  
 Środowisko wykonawcze przepływów pracy zapewnia następujące gwarancje, dotyczące czas przenoszenia danych do i z działań:  
  
1. Po uruchomieniu działania wykonywania jest obliczany wartości wszystkich argumentów wejściowych i wejścia/wyjścia. Na przykład, niezależnie od tego, kiedy <xref:System.Activities.Argument.Get%2A> jest wywoływana, wartość zwracana jest ten, który jest obliczana przez środowisko wykonawcze przed jej wywołanie `Execute`.  
  
2. Gdy <xref:System.Activities.InOutArgument%601.Set%2A> jest wywoływana, środowisko uruchomieniowe ustawia wartość natychmiast.  
  
3. Argumenty mogą opcjonalnie mieć ich <xref:System.Activities.Argument.EvaluationOrder%2A> określony. <xref:System.Activities.Argument.EvaluationOrder%2A> jest liczony od zera wartość, która określa kolejność szacowania argumentu. Domyślnie kolejność oceny argument jest nieokreślony i jest równa <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> wartość. Ustaw <xref:System.Activities.Argument.EvaluationOrder%2A> na wartość większą lub równą zero, aby określić kolejność obliczania dla tego argumentu. Windows Workflow Foundation ocenia argumenty w kolejności określonej wersji ewaluacyjnej, w kolejności rosnącej. Należy pamiętać, że argumenty z kolejnością nieokreślony oceny są obliczane przed elementami o kolejność oceny określonej.  
  
 Autor aktywności można użyć silnie typizowane mechanizm do udostępniania jej argumentów. Jest to realizowane przez zadeklarowanie właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>. Dzięki temu Autor działania ustalenie określonej umowy o dane przesyłane do i z działania.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Definiowanie argumenty w działaniu  
 Argumenty można zdefiniować w działaniu, określając właściwości typu <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, i <xref:System.Activities.InOutArgument%601>. Poniższy kod przedstawia sposób definiowania argumenty `Prompt` działanie, które przyjmuje w ciągu do wyświetlania użytkownikowi i zwraca ciąg, który zawiera odpowiedź użytkownika.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
>  Działania, które zwraca pojedynczą wartość może pochodzić z <xref:System.Activities.Activity%601>, <xref:System.Activities.NativeActivity%601>, lub <xref:System.Activities.CodeActivity%601>. Te działania muszą być dobrze zdefiniowane <xref:System.Activities.OutArgument%601> o nazwie <xref:System.Activities.Activity%601.Result%2A> zawierający wartość zwracaną przez działanie.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Używanie zmienne i argumenty w przepływach pracy  
 Poniższy przykład pokazuje, jak zmienne i argumenty są używane w przepływie pracy. Przepływ pracy jest sekwencji, która deklaruje trzy zmienne: `var1`, `var2`, i `var3`. Pierwsze działanie w przepływie pracy jest `Assign` działanie, które przypisuje wartość zmiennej `var1` do zmiennej `var2`. Następuje to `WriteLine` działań, która drukuje wartość `var2` zmiennej. Następnie jest kolejnym `Assign` działanie, które przypisuje wartość zmiennej `var2` do zmiennej `var3`. Na koniec istnieje inny `WriteLine` działań, która drukuje wartość `var3` zmiennej. Pierwszy `Assign` używa działania `InArgument<string>` i `OutArgument<string>` obiekty reprezentujące jawnie powiązania dla argumentów tego działania. `InArgument<string>` Służy do <xref:System.Activities.Statements.Assign.Value%2A> ponieważ wartość będą przepływać do <xref:System.Activities.Statements.Assign%601> działania za pośrednictwem jego <xref:System.Activities.Statements.Assign.Value%2A> argument i `OutArgument<string>` służy do <xref:System.Activities.Statements.Assign.To%2A> ponieważ wartość będą przepływać z <xref:System.Activities.Statements.Assign.To%2A> argument do zmiennej. Drugi `Assign` działanie wykonuje ten sam efekt więcej compact ale równoważne składnia, która używa niejawnego rzutowania. `WriteLine` Działania również użyć zwięzłą składnią.  
  
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
  
### <a name="using-variables-and-arguments-in-code-based-activities"></a>Za pomocą zmienne i argumenty w działaniach oparte na kodzie  
 Sposób używania argumentów i zmiennych w przepływach pracy i deklaratywne działania można znaleźć w poprzednich przykładach. Zmienne i argumenty są również używane w działaniach oparte na kodzie. Koncepcyjnie użycie jest bardzo podobne. Zmienne reprezentowania magazynu danych w ramach działania, a argumenty reprezentują przepływ danych do lub z działalności i są powiązane reprezentujące, gdzie dane są wczytywane do lub z innych zmienne i argumenty w przepływie pracy Autor przepływu pracy. Do pobierania lub zestaw, który należy użyć wartości zmiennej lub argumentu w działaniu, kontekst działania reprezentujący bieżące środowisko wykonywania działania. Te informacje są przekazywane do <xref:System.Activities.CodeActivity%601.Execute%2A> sposób działania w czasie wykonywania przepływu pracy. W tym przykładzie niestandardową `Add` działania jest zdefiniowany, który ma dwa <xref:System.Activities.ArgumentDirection.In> argumentów. Aby uzyskać dostęp do wartości argumentów, <xref:System.Activities.Argument.Get%2A> metoda jest używana i jest używany w kontekście, która została przekazana przez środowisko wykonawcze przepływów pracy.  
  
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
  
 Aby uzyskać więcej informacji na temat pracy z argumentami, zmienne i wyrażenia w kodzie, zobacz [tworzenia przepływów pracy, działań i wyrażeń przy użyciu technologii kodu](authoring-workflows-activities-and-expressions-using-imperative-code.md) i [wymagane argumenty i grupy przeciążenia](required-arguments-and-overload-groups.md).
