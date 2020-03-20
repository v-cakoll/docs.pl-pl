---
title: Zmienne i argumenty
ms.date: 03/30/2017
ms.assetid: d03dbe34-5b2e-4f21-8b57-693ee49611b8
ms.openlocfilehash: f975f46a1858d204d12588f7570b7ea5a365e650
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182682"
---
# <a name="variables-and-arguments"></a>Zmienne i argumenty
W programie Windows Workflow Foundation (WF) zmienne reprezentują przechowywanie danych, a argumenty reprezentują przepływ danych do i z działania. Działanie ma zestaw argumentów i tworzą podpis działania. Ponadto działanie może obsługiwać listę zmiennych, do których deweloper może dodawać lub usuwać zmienne podczas projektowania przepływu pracy. Argument jest powiązany przy użyciu wyrażenia, które zwraca wartość.  
  
## <a name="variables"></a>Zmienne  
 Zmienne są lokalizacjami przechowywania danych. Zmienne są deklarowane jako część definicji przepływu pracy. Zmienne przyjmują wartości w czasie wykonywania i te wartości są przechowywane jako część stanu wystąpienia przepływu pracy. Definicja zmiennej określa typ zmiennej i opcjonalnie nazwę. Poniższy kod pokazuje, jak zadeklarować zmienną, <xref:System.Activities.Statements.Assign%601> przypisać do niej wartość za pomocą <xref:System.Activities.Statements.WriteLine> działania, a następnie wyświetlić jej wartość w konsoli przy użyciu działania.  
  
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
  
 Domyślne wyrażenie wartości można opcjonalnie określić jako część deklaracji zmiennej. Zmienne mogą również mieć modyfikatory. Na przykład jeśli zmienna jest tylko do <xref:System.Activities.VariableModifiers> odczytu, można zastosować modyfikator tylko do odczytu. W poniższym przykładzie jest tworzona zmienna tylko do odczytu, która ma przypisaną wartość domyślną.  
  
```csharp  
// Define a read-only variable with a default value.  
Variable<string> var = new Variable<string>  
{  
    Default = "Hello World.",  
    Modifiers = VariableModifiers.ReadOnly  
};  
```  
  
## <a name="variable-scoping"></a>Zakres zmiennej  
 Okres istnienia zmiennej w czasie wykonywania jest równy okresowi istnienia działania, które ją deklaruje. Po zakończeniu działania jego zmienne są czyszczone i nie można już odwoływać się.  
  
## <a name="arguments"></a>Argumenty  
 Autorzy działań używają argumentów do definiowania sposobu przepływu danych do i z działania. Każdy argument ma określony <xref:System.Activities.ArgumentDirection.In> <xref:System.Activities.ArgumentDirection.Out>kierunek: <xref:System.Activities.ArgumentDirection.InOut>, , lub .  
  
 Środowisko wykonawcze przepływu pracy daje następujące gwarancje dotyczące czasu przenoszenia danych do i z działań:  
  
1. Po rozpoczęciu wykonywania działania obliczane są wartości wszystkich jego argumentów wejściowych i wejściowych/wyjściowych. Na przykład, niezależnie <xref:System.Activities.Argument.Get%2A> od tego, kiedy jest wywoływana, zwracana wartość jest wartością obliczoną przez środowisko wykonawcze przed wywołaniem . `Execute`  
  
2. Po <xref:System.Activities.InOutArgument%601.Set%2A> wywołaniu środowisko wykonawcze natychmiast ustawia wartość.  
  
3. Argumenty mogą opcjonalnie <xref:System.Activities.Argument.EvaluationOrder%2A> mieć ich określony. <xref:System.Activities.Argument.EvaluationOrder%2A>jest wartością od zera, która określa kolejność, w jakiej argument jest oceniany. Domyślnie kolejność oceny argumentu jest nieokreślony i jest <xref:System.Activities.Argument.UnspecifiedEvaluationOrder> równa wartości. Ustaw <xref:System.Activities.Argument.EvaluationOrder%2A> wartość większą lub równą zero, aby określić kolejność oceny dla tego argumentu. Fundacja przepływu pracy systemu Windows ocenia argumenty o określonej kolejności oceny w porządku rosnącym. Należy zauważyć, że argumenty z nieokreśloną kolejnością oceny są oceniane przed argumentami z określoną kolejnością oceny.  
  
 Autor działania można użyć mechanizmu silnie typizowane do uwidaczniania jego argumenty. Odbywa się to poprzez deklarowanie <xref:System.Activities.InArgument%601>właściwości <xref:System.Activities.OutArgument%601>typu <xref:System.Activities.InOutArgument%601>, i . Dzięki temu autor działania do ustanowienia określonej umowy o danych wchodząc i wychodząc z działania.  
  
### <a name="defining-the-arguments-on-an-activity"></a>Definiowanie argumentów w działaniu  
 Argumenty można zdefiniować w działaniu, określając <xref:System.Activities.InArgument%601> <xref:System.Activities.OutArgument%601>właściwości <xref:System.Activities.InOutArgument%601>typu , i . Poniższy kod pokazuje, jak zdefiniować argumenty dla `Prompt` działania, które ma w ciągu do wyświetlenia do użytkownika i zwraca ciąg, który zawiera odpowiedź użytkownika.  
  
```csharp  
public class Prompt : Activity  
{  
    public InArgument<string> Text { get; set; }  
    public OutArgument<string> Response { get; set; }  
    // Rest of activity definition omitted.  
}  
```  
  
> [!NOTE]
> Działania zwracające pojedynczą wartość mogą <xref:System.Activities.Activity%601> <xref:System.Activities.NativeActivity%601>pochodzić <xref:System.Activities.CodeActivity%601>z , lub . Te działania mają dobrze <xref:System.Activities.OutArgument%601> zdefiniowaną nazwę, <xref:System.Activities.Activity%601.Result%2A> która zawiera zwracaną wartość działania.  
  
### <a name="using-variables-and-arguments-in-workflows"></a>Używanie zmiennych i argumentów w przepływach pracy  
 Poniższy przykład pokazuje, jak zmienne i argumenty są używane w przepływie pracy. Przepływ pracy jest sekwencją, która deklaruje `var1` `var2`trzy `var3`zmienne: , , i . Pierwsze działanie w przepływie `Assign` pracy to działanie, które `var1` przypisuje `var2`wartość zmiennej do zmiennej . Po tym następuje `WriteLine` działanie, które drukuje wartość zmiennej. `var2` Dalej jest `Assign` inne działanie, które `var2` przypisuje wartość `var3`zmiennej do zmiennej . Na koniec istnieje `WriteLine` inne działanie, które `var3` drukuje wartość zmiennej. Pierwsze `Assign` działanie używa `InArgument<string>` `OutArgument<string>` i obiektów, które jawnie reprezentują powiązania dla argumentów działania. `InArgument<string>`jest <xref:System.Activities.Statements.Assign.Value%2A> używany, ponieważ wartość jest <xref:System.Activities.Statements.Assign%601> przepływa <xref:System.Activities.Statements.Assign.Value%2A> do działania `OutArgument<string>` za <xref:System.Activities.Statements.Assign.To%2A> pośrednictwem jego argumentu i <xref:System.Activities.Statements.Assign.To%2A> jest używany, ponieważ wartość jest wypływa z argumentu do zmiennej. Drugie `Assign` działanie wykonuje to samo z bardziej kompaktowe, ale równoważne składni, która używa rzutowań niejawnych. Działania `WriteLine` również użyć składni kompaktowej.  
  
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
 Poprzednie przykłady pokazują, jak używać argumentów i zmiennych w przepływach pracy i działaniach deklaratywnych. Argumenty i zmienne są również używane w działaniach opartych na kodzie. Koncepcyjnie użycie jest bardzo podobne. Zmienne reprezentują magazyn danych w ramach działania, a argumenty reprezentują przepływ danych do lub z działania i są powiązane przez autora przepływu pracy z innymi zmiennymi lub argumentami w przepływie pracy, które reprezentują, gdzie dane są przepływa do lub z. Aby uzyskać lub ustawić wartość zmiennej lub argumentu w działaniu, kontekst działania musi być używany, który reprezentuje bieżące środowisko wykonywania działania. Jest to przekazywane <xref:System.Activities.CodeActivity%601.Execute%2A> do metody działania przez środowisko wykonawcze przepływu pracy. W tym przykładzie `Add` zdefiniowano działanie <xref:System.Activities.ArgumentDirection.In> niestandardowe, które ma dwa argumenty. Aby uzyskać dostęp do wartości <xref:System.Activities.Argument.Get%2A> argumentów, używana jest metoda i używany jest kontekst, który został przekazany przez środowisko wykonawcze przepływu pracy.  
  
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
  
 Aby uzyskać więcej informacji na temat pracy z argumentami, zmiennymi i wyrażeniami w kodzie, zobacz [Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywu](authoring-workflows-activities-and-expressions-using-imperative-code.md) oraz [wymaganych argumentów i grup przeciążenia](required-arguments-and-overload-groups.md).
