---
title: Tworzenie przepływów pracy, działań i wyrażenia przy użyciu kodu Imperatywne
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: ebc093bf8cd3e87bc04c20e93415aa1d2d2f7867
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33520477"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Tworzenie przepływów pracy, działań i wyrażenia przy użyciu kodu Imperatywne
Definicji przepływu pracy jest drzewa obiektów skonfigurowane działania. Tego drzewa działania można zdefiniować wiele sposobów, łącznie z ręcznie edytować XAML lub za pomocą projektanta przepływów pracy do produkcji XAML. Korzystanie z języka XAML, jednak nie jest wymagane. Można także programowo utworzyć definicji przepływu pracy. Ten temat zawiera omówienie tworzenia definicji przepływu pracy, działań i wyrażenia przy użyciu kodu. Przykłady z przepływów pracy XAML przy użyciu kodu) (Praca można znaleźć [serializacji przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Tworzenie definicji przepływu pracy  
 Definicji przepływu pracy można utworzyć instancji typu działania i konfigurując właściwości obiektu działania. Dla działań, które nie zawierają działania podrzędne można to zrobić przy użyciu kilku wierszy kodu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
>  Przykłady w tym temacie <xref:System.Activities.WorkflowInvoker> do uruchamiania przepływów pracy próbki. Aby uzyskać więcej informacji na temat wywoływania przepływy pracy, przekazywanie argumentów i różnych opcji obsługi, które są dostępne, zobacz [przy użyciu WorkflowInvoker i działanie obiektu WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md).  
  
 W tym przykładzie przepływ pracy, który składa się pojedyncza <xref:System.Activities.Statements.WriteLine> utworzeniu działania. <xref:System.Activities.Statements.WriteLine> Działania <xref:System.Activities.Statements.WriteLine.Text%2A> argument ma wartość i jest wywoływane przez przepływ pracy. Jeśli działanie występują działania podrzędne, przypomina metody konstrukcji. W poniższym przykładzie użyto <xref:System.Activities.Statements.Sequence> działania, która zawiera dwa <xref:System.Activities.Statements.WriteLine> działań.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Przy użyciu inicjatory obiektów  
 Przykłady w tym temacie należy użyć składni inicjalizacji obiektu. Składnia inicjalizacji obiektu może być przydatne do tworzenia definicji przepływu pracy w kodzie, ponieważ zawiera hierarchiczny widok działań w przepływie pracy i przedstawiono relacje między działaniami. Nie jest wymagany do programowego tworzenia przepływów pracy, użyj składni inicjalizacji obiektu. Poniższy przykład jest funkcjonalnym odpowiednikiem poprzedniego przykładu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Aby uzyskać więcej informacji na temat inicjatory obiektów, zobacz [porady: Inicjowanie obiektów bez wywoływania konstruktora (C# przewodnik programowania w języku)](http://go.microsoft.com/fwlink/?LinkId=161015) i [porady: deklarowanie obiektu za pomocą inicjatora obiektów](http://go.microsoft.com/fwlink/?LinkId=161016).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Praca z zmiennych, wartości literałów i wyrażenia  
 Podczas tworzenia definicji przepływu pracy, przy użyciu kodu, należy pamiętać o jakie kod wykonywany w ramach tworzenia definicji przepływu pracy i jakie kod wykonywany w ramach wykonywania wystąpienia przepływ pracy. Na przykład poniższy przepływ pracy ma na celu Generowanie liczby losowej i zapisują do konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Po wykonaniu tego kodu definicji przepływu pracy, wywołanie `Random.Next` staje się wynik jest przechowywana w definicji przepływu pracy jako wartość literału. Wiele wystąpień tego przepływu pracy może być wywoływany, a wszystkie wyświetla ten sam numer. Ma wystąpić podczas wykonywania przepływu pracy, czyli musi użyć wyrażenia Generowanie liczby losowej następuje za każdym razem, który uruchamia przepływ pracy. W poniższym przykładzie wyrażenia języka Visual Basic jest używany z <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Wyrażenie w poprzednim przykładzie można również implementowana przy użyciu <xref:Microsoft.CSharp.Activities.CSharpValue%601> i wyrażeń C#.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 Muszą być skompilowane wyrażeń C#, zanim je zawierające przepływu pracy jest wywoływany. Jeśli nie są kompilowane wyrażeń C#, <xref:System.NotSupportedException> jest generowany, gdy przepływ pracy jest wywoływana z komunikatu podobnego do następującego: `Expression Activity type 'CSharpValue`1" wymaga kompilacji, aby można było uruchomić.  Upewnij się, że przepływ pracy został skompilowany. "w większości scenariuszy dotyczących przepływów pracy tworzonych w Visual Studio C# wyrażenia są kompilowane automatycznie, ale w niektórych scenariuszach, takich jak przepływ kodu wyrażenia języka C# musi ręcznie skompilowany. Na przykład jak skompilować wyrażeń C#, zobacz [wyrażenia przy użyciu języka C# w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) sekcji [wyrażeń C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md) tematu.  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> reprezentuje wyrażenie w składni języka Visual Basic, który może służyć jako r w wyrażeniu, a <xref:Microsoft.CSharp.Activities.CSharpValue%601> reprezentuje wyrażenie w składni języka C#, który może służyć jako r w wyrażeniu. Wyrażenia te są oceniane pod każdym razem, gdy jest wykonywane działanie zawierającego. Wynikiem wyrażenia jest przypisany do zmiennej przepływu pracy `n`, a te wyniki są używane przez następne działanie w przepływie pracy. Aby uzyskać dostęp do wartości zmiennej przepływu pracy `n` w czasie wykonywania, <xref:System.Activities.ActivityContext> jest wymagana. To jest możliwy za pomocą następującego wyrażenia lambda.  
  
> [!NOTE]
>  Należy pamiętać, że oba te kodu przedstawiono przykłady są przy użyciu języka C# jako języka programowania, ale korzysta z jednego <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i korzysta z jednego <xref:Microsoft.CSharp.Activities.CSharpValue%601>. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i <xref:Microsoft.CSharp.Activities.CSharpValue%601> mogą być używane w projektach zarówno Visual Basic i C#. Domyślnie wyrażenia utworzone w Projektancie przepływów pracy język projektu hostingu. Podczas tworzenia przepływów pracy w kodzie, jest odpowiedni język, według uznania Autor przepływu pracy.  
  
 W tych przykładach wynikiem wyrażenia jest przypisany do zmiennej przepływu pracy `n`, a te wyniki są używane przez następne działanie w przepływie pracy. Aby uzyskać dostęp do wartości zmiennej przepływu pracy `n` w czasie wykonywania, <xref:System.Activities.ActivityContext> jest wymagana. To jest możliwy za pomocą następującego wyrażenia lambda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda (C# przewodnik programowania w języku)](http://go.microsoft.com/fwlink/?LinkID=152436) lub [wyrażenia Lambda (Visual Basic)](http://go.microsoft.com/fwlink/?LinkID=152437).  
  
 Wyrażenia lambda nie są można serializować do formatu XAML. Jeśli podejmowana jest próba do serializacji przepływu pracy za pomocą wyrażeń lambda, <xref:System.Activities.Expressions.LambdaSerializationException> zostanie zgłoszony następujący komunikat o błędzie: "ten przepływ pracy zawiera wyrażenia lambda określone w kodzie. Wyrażenia te nie są XAML do serializacji. Aby przepływ pracy do serializacji XAML, użyj obiektu VisualBasicValue/VisualBasicReference lub metody ExpressionServices.Convert(lambda). Spowoduje to przekonwertowanie wyrażenia lambda na działania wyrażeń." Aby to wyrażenie zgodne z XAML, użyj <xref:System.Activities.Expressions.ExpressionServices> i <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> można również. Należy pamiętać, że żadne wyrażenie lambda jest wymagana przy użyciu wyrażenia języka Visual Basic.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 W czasie wykonywania wyrażenia języka Visual Basic są kompilowane do wyrażenia LINQ. W poprzednich przykładach jest możliwy do serializacji w języku XAML, ale jeśli serializacji XAML ma można wyświetlić i edytować w Projektancie przepływów pracy, użyj <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> dla wyrażenia. Serializowany przepływy pracy używające `ExpressionServices.Convert` może być otwarty w projektancie, ale wartość wyrażenia będzie puste. Aby uzyskać więcej informacji na temat serializacji przepływów pracy w języku XAML, zobacz [serializacji przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Wyrażenia dosłowne i typy referencyjne  
 Wyrażenia dosłowne są reprezentowane w przepływach pracy przez <xref:System.Activities.Expressions.Literal%601> działania. Następujące <xref:System.Activities.Statements.WriteLine> działania działają tak samo.  
  
```csharp  
new WriteLine  
{  
    Text = "Hello World."  
},  
new WriteLine  
{  
    Text = new Literal<string>("Hello World.")  
}  
```  
  
 Nie można zainicjować wyrażenie literału typu odniesienia z wyjątkiem <xref:System.String>. W poniższym przykładzie <xref:System.Activities.Statements.Assign> działania <xref:System.Activities.Statements.Assign.Value%2A> właściwość jest inicjowana z za pomocą wyrażenia literału `List<string>`.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Podczas sprawdzania poprawności przepływu pracy zawierające działanie, jest zwracany następujący błąd sprawdzania poprawności: "literał obsługuje tylko typy wartości i niezmiennego typu System.String. Typ System.Collections.Generic.List'1[System.String] nie może być używany jako literału." Jeśli przepływ pracy zostanie wywołany, <xref:System.Activities.InvalidWorkflowException> jest zgłaszany zawierający tekst błędu sprawdzania poprawności. Jest to błąd sprawdzania poprawności, ponieważ tworzenie wyrażenie literału typu odniesienia nie tworzy nowe wystąpienie typu odwołania dla każdego wystąpienia przepływu pracy. Aby rozwiązać ten problem, Zamień wyrażenie literału, który tworzy i zwraca nowe wystąpienie typu referencyjnego.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 Aby uzyskać więcej informacji na temat wyrażeń, zobacz [wyrażenia](../../../docs/framework/windows-workflow-foundation/expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Wywoływanie metod obiektów przy użyciu wyrażeń i działania InvokeMethod  
 <xref:System.Activities.Expressions.InvokeMethod%601> Działanie może być używane do wywołania statyczne i wystąpienie metody klas w programie .NET Framework. W poprzednim przykładzie, w tym temacie, liczbę losową został wygenerowany za pomocą <xref:System.Random> klasy.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> Działania można również zostały już użyte do wywołania <xref:System.Random.Next%2A> metody <xref:System.Random> klasy.  
  
```csharp  
new InvokeMethod<int>  
{  
    TargetObject = new InArgument<Random>(new VisualBasicValue<Random>("New Random()")),  
    MethodName = "Next",  
    Parameters =   
    {  
        new InArgument<int>(1),  
        new InArgument<int>(101)  
    },  
    Result = n  
}  
```  
  
 Ponieważ <xref:System.Random.Next%2A> nie jest metodą statyczną wystąpienia <xref:System.Random> dostarczonej klasy dla <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> właściwości. W tym przykładzie nowe wystąpienie zostało utworzone przy użyciu wyrażenia języka Visual Basic, ale jego można również zostały utworzone wcześniej i przechowywane w zmiennej przepływu pracy. W tym przykładzie będzie prostszy użyć <xref:System.Activities.Statements.Assign%601> działania zamiast <xref:System.Activities.Expressions.InvokeMethod%601> działania. Jeśli wywołanie metody ostatecznie wywoływane przez <xref:System.Activities.Statements.Assign%601> lub <xref:System.Activities.Expressions.InvokeMethod%601> działania jest długa uruchomiona, <xref:System.Activities.Expressions.InvokeMethod%601> ma więcej możliwości, ponieważ ma ona <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> właściwości. Jeśli ta właściwość jest równa `true`, wywołana metoda będą wykonywane asynchronicznie w odniesieniu do przepływu pracy. Jeśli inne działania równoległe, ich nie zostanie zablokowane podczas asynchronicznie wykonuje metodę. Ponadto jeśli wywoływanej metody nie ma zwracanych wartości, następnie <xref:System.Activities.Expressions.InvokeMethod%601> odpowiedni sposób wywołania metody.  
  
## <a name="arguments-and-dynamic-activities"></a>Argumenty i dynamicznych działania  
 Definicji przepływu pracy jest tworzona w kodzie przez zebrania działań w drzewie działań oraz konfigurowania właściwości i argumenty. Może być powiązana istniejących argumentów, ale nowych argumentów nie można dodać do działania. W tym przepływie pracy Argumenty przekazane do działania głównego. W kodzie imperatywnych argumenty przepływu pracy są określone jako właściwości na nowy typ CLR, a w języku XAML są zadeklarowane za pomocą `x:Class` i `x:Member`. Ponieważ nie ma nowych typu CLR, które są tworzone podczas tworzenia definicji przepływu pracy jako drzewa obiektów w pamięci, nie można dodać argumentów. Jednak argumentów można dodać do <xref:System.Activities.DynamicActivity>. W tym przykładzie <xref:System.Activities.DynamicActivity%601> jest tworzony w tym przyjmuje dwa argumenty liczba całkowita, dodaje je ze sobą i zwraca wynik. A <xref:System.Activities.DynamicActivityProperty> jest tworzony dla każdego argumentu i wyniku operacji jest przypisany do <xref:System.Activities.Activity%601.Result%2A> argument <xref:System.Activities.DynamicActivity%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Aby uzyskać więcej informacji o działaniach dynamicznej, zobacz [tworzenia działania w czasie wykonywania](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Skompilowany działań  
 Dynamiczne działania są jednym ze sposobów zdefiniuj działanie, które zawiera argumenty, przy użyciu kodu, ale również można tworzyć w kodzie i skompilować do typów działań. Proste można tworzyć działania pochodzące z <xref:System.Activities.CodeActivity>oraz asynchroniczne działania, które pochodzi od <xref:System.Activities.AsyncCodeActivity>. Te działania mogą mieć argumentów, zwracać wartości i definiowanie ich logiki przy użyciu kodu imperatywnych. Przykłady tworzenia tych typów działań, zobacz [klasa podstawowa klasy CodeActivity](../../../docs/framework/windows-workflow-foundation/workflow-activity-authoring-using-the-codeactivity-class.md) i [tworzenia działań asynchroniczne](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 Działania, które pochodzą z <xref:System.Activities.NativeActivity> można zdefiniować ich logiki przy użyciu kodu imperatywnych i mogą również zawierać działania podrzędne, które definiują logiki. Mają one również pełny dostęp do funkcji aparatu plików wykonywalnych, takich jak tworzenie zakładek. Przykłady tworzenia <xref:System.Activities.NativeActivity>— na podstawie działania, zobacz [klasę Base działania NativeActivity](../../../docs/framework/windows-workflow-foundation/nativeactivity-base-class.md), [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)i [niestandardowe złożonego za pomocą działania natywnego](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-using-native-activity.md)próbki.  
  
 Działania, które pochodzą z <xref:System.Activities.Activity> zdefiniować ich logiki wyłącznie przy użyciu działań podrzędnych. Te działania są zazwyczaj tworzone za pomocą projektanta przepływów pracy, ale może być także definiowane przy użyciu kodu. W poniższym przykładzie `Square` działania jest zdefiniowany, która pochodzi z `Activity<int>`. `Square` Działanie ma jeden <xref:System.Activities.InArgument%601> o nazwie `Value`i definiuje swojej logiki, określając <xref:System.Activities.Statements.Sequence> działania przy użyciu <xref:System.Activities.Activity.Implementation%2A> właściwości. <xref:System.Activities.Statements.Sequence> Zawiera działanie <xref:System.Activities.Statements.WriteLine> działania i <xref:System.Activities.Statements.Assign%601> działania. Ze sobą, działania te trzy implementacji logiki `Square` działania.  
  
```csharp  
class Square : Activity<int>  
{  
    [RequiredArgument]  
    public InArgument<int> Value { get; set; }  
  
    public Square()  
    {  
        this.Implementation = () => new Sequence  
        {  
            Activities =  
            {  
                new WriteLine  
                {  
                    Text = new InArgument<string>((env) => "Squaring the value: " + this.Value.Get(env))  
                },  
                new Assign<int>  
                {  
                    To = new OutArgument<int>((env) => this.Result.Get(env)),  
                    Value = new InArgument<int>((env) => this.Value.Get(env) * this.Value.Get(env))  
                }  
            }  
        };  
    }  
}  
```  
  
 W poniższym przykładzie definicji przepływu pracy, składającą się z pojedynczej `Square` działania jest wywoływana przy użyciu <xref:System.Activities.WorkflowInvoker>.  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 Po wywołaniu przepływu pracy, wyświetlane są następujące dane wyjściowe do konsoli:  
  
 **Wartość squaring: 5**  
**Wynik: 25**
