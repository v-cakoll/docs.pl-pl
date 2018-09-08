---
title: Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu Imperatywnego
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: a0566e01d5786c955562ef97d6d083d886278293
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/08/2018
ms.locfileid: "44197501"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu Imperatywnego
Definicja przepływu pracy jest drzewa obiektów skonfigurowane działania. Tego drzewa działań można zdefiniować wiele sposobów, w tym przez ręczną edycję XAML lub za pomocą projektanta przepływów pracy do produkcji XAML. Korzystanie z XAML, jednak nie jest to wymagane. Można także programowo tworzyć definicji przepływu pracy. Ten temat zawiera omówienie tworzenia definicji przepływu pracy, działań i wyrażeń przy użyciu kodu. Aby uzyskać przykłady pracy z przepływami pracy XAML przy użyciu kodu, zobacz [serializowanie przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Tworzenie definicji przepływu pracy  
 Definicja przepływu pracy można utworzyć instancji typu działania i konfigurując właściwości obiektu działania. Dla działań, które nie zawierają działania podrzędne można to zrobić przy użyciu kilku wierszy kodu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
>  Przykłady w tym temacie <xref:System.Activities.WorkflowInvoker> do uruchamiania przepływów pracy próbki. Aby uzyskać więcej informacji na temat wywoływania przepływy pracy, przekazywanie argumentów i różne opcje hostingu, które są dostępne, zobacz [przy użyciu obiektu WorkflowInvoker i WorkflowApplication](../../../docs/framework/windows-workflow-foundation/using-workflowinvoker-and-workflowapplication.md).  
  
 W tym przykładzie przepływ pracy, który składa się z pojedynczego <xref:System.Activities.Statements.WriteLine> utworzeniu działania. <xref:System.Activities.Statements.WriteLine> Działania <xref:System.Activities.Statements.WriteLine.Text%2A> argument ma wartość i jest wywoływane przez przepływ pracy. Jeśli działanie zawiera działania podrzędne, metoda konstrukcji jest podobny. W poniższym przykładzie użyto <xref:System.Activities.Statements.Sequence> działania, który zawiera dwa <xref:System.Activities.Statements.WriteLine> działań.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Za pomocą inicjatory obiektów  
 W przykładach w tym temacie używany składni inicjowania obiektu. Składnia inicjalizacji obiektu może być przydatny sposób do tworzenia definicji przepływu pracy w kodzie, ponieważ udostępnia hierarchiczny widok działań w przepływie pracy i przedstawiono relację między działaniami. Nie jest wymagane do programowego tworzenia przepływów pracy, użyj składni inicjowania obiektu. Poniższy przykład jest funkcjonalnie równoważny do poprzedniego przykładu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Aby uzyskać więcej informacji na temat inicjatorów obiektów, zobacz [instrukcje: Inicjowanie obiektów bez wywoływania konstruktora (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkId=161015) i [instrukcje: deklarowanie obiektu za pomocą inicjatora obiektów](https://go.microsoft.com/fwlink/?LinkId=161016).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Praca z zmiennych, wartości literałów i wyrażenia  
 Podczas tworzenia definicji przepływu pracy przy użyciu kodu, należy pamiętać, jaki kod jest wykonywany w ramach tworzenia definicji przepływu pracy i jaki kod jest wykonywany w ramach wykonywania wystąpienia na ten przepływ pracy. Na przykład poniższy przepływ pracy jest przeznaczona do generowania losową liczbę i zapisz je w konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Kiedy ten kod definicji przepływu pracy jest wykonywany, wywołanie `Random.Next` wykonano i wynik jest przechowywany w definicji przepływu pracy jako wartości literału. Może być wywołana wiele wystąpień tego przepływu pracy, a wszystkie zostanie wyświetlony ten sam numer. Zapewnienie Generowanie liczby losowej występują podczas wykonywania przepływu pracy, to znaczy należy użyć wyrażenia oceniane każdym razem, gdy jest uruchamiany przepływ pracy. W poniższym przykładzie wyrażenie języka Visual Basic jest używana z <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Wyrażenie w poprzednim przykładzie może być implementowane za pomocą <xref:Microsoft.CSharp.Activities.CSharpValue%601> i wyrażenia języka C#.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 Muszą być skompilowane wyrażeń języka C#, przed wywołaniem je zawierające przepływ pracy. Jeśli nie są kompilowane wyrażeń języka C#, <xref:System.NotSupportedException> jest zgłaszany, gdy przepływ pracy jest wywoływana z komunikat podobny do następującego: `Expression Activity type 'CSharpValue`1' wymaga kompilacji, aby można było uruchomić.  Upewnij się, że przepływ pracy został skompilowany. "w większości scenariuszy obejmujących przepływy pracy utworzone w programie Visual Studio C# wyrażenia są kompilowane automatycznie, ale w niektórych scenariuszach, na przykład w przypadku przepływów pracy kodu wyrażeń języka C# musi ręcznie skompilowany. Na przykład sposób kompilowania wyrażeń języka C# zobacz [wyrażeń przy użyciu języka C# w przepływach pracy kodu](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md#CodeWorkflows) części [wyrażeń języka C#](../../../docs/framework/windows-workflow-foundation/csharp-expressions.md) tematu.  
  
 A <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> reprezentuje wyrażenie w składni języka Visual Basic, który może służyć jako wartości w wyrażeniu, a <xref:Microsoft.CSharp.Activities.CSharpValue%601> reprezentuje wyrażenie w składni języka C#, które mogą być używane jako wartości w wyrażeniu. Te wyrażenia są obliczane w każdym razem, gdy jest wykonywane działanie zawierającego. Wynikiem wyrażenia jest przypisywana do zmiennej przepływu pracy `n`, oraz te wyniki są używane przez następne działanie w przepływie pracy. Aby uzyskać dostęp do wartości zmiennej przepływu pracy `n` w czasie wykonywania, <xref:System.Activities.ActivityContext> jest wymagana. To jest możliwy za pomocą następującego wyrażenia lambda.  
  
> [!NOTE]
>  Należy pamiętać, że oba te kodu są przykłady są przy użyciu języka C# jako języka programowania, ale jeden używa <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i jeden używa <xref:Microsoft.CSharp.Activities.CSharpValue%601>. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i <xref:Microsoft.CSharp.Activities.CSharpValue%601> mogą być używane w projektach Visual Basic i C#. Domyślnie wyrażenia utworzone w Projektancie przepływu pracy jest zgodny z językiem hostingu projektu. Podczas tworzenia przepływów pracy w kodzie, jest odpowiedni język, według uznania autora przepływu pracy.  
  
 W tych przykładach wynikiem wyrażenia jest przypisywana do zmiennej przepływu pracy `n`, oraz te wyniki są używane przez następne działanie w przepływie pracy. Aby uzyskać dostęp do wartości zmiennej przepływu pracy `n` w czasie wykonywania, <xref:System.Activities.ActivityContext> jest wymagana. To jest możliwy za pomocą następującego wyrażenia lambda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażenia Lambda (C# Programming Guide)](https://go.microsoft.com/fwlink/?LinkID=152436) lub [wyrażenia Lambda (Visual Basic)](https://go.microsoft.com/fwlink/?LinkID=152437).  
  
 Wyrażenia lambda nie są możliwe do serializacji w formacie XAML. Jeśli zostanie podjęta próba serializacji przepływu pracy przy użyciu wyrażeń lambda, <xref:System.Activities.Expressions.LambdaSerializationException> zostanie zgłoszony następujący komunikat o błędzie: "ten przepływ pracy zawiera wyrażenia lambda, określonym w kodzie. Te wyrażenia nie są możliwe do serializacji XAML. Aby było możliwe do serializacji XAML przepływu pracy, użyj VisualBasicValue/VisualBasicReference lub ExpressionServices.Convert(lambda). Spowoduje to przekonwertowanie wyrażenia lambda wyrażenia działania programu." Aby wprowadzić to wyrażenie jest zgodne z XAML, należy użyć <xref:System.Activities.Expressions.ExpressionServices> i <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 Element <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> może być również używana. Należy pamiętać, że brak wyrażenia lambda jest wymagany przy użyciu wyrażenia języka Visual Basic.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 W czasie wykonywania wyrażenia języka Visual Basic są kompilowane do wyrażenia LINQ. W poprzednich przykładach są serializacji do XAML, ale jeśli Zserializowany XAML jest przeznaczona do można wyświetlać i edytować w Projektancie przepływu pracy Użyj <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> dla wyrażenia. Serializowana przepływy pracy korzystające z `ExpressionServices.Convert` mogą być otwierane w projektancie, ale wartość wyrażenia będzie puste. Aby uzyskać więcej informacji na temat serializowanie przepływów pracy XAML, zobacz [serializowanie przepływów pracy i działań do i z XAML](../../../docs/framework/windows-workflow-foundation/serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Wyrażenia literału i typy odwołań  
 Wyrażeń literałów są reprezentowane w przepływach pracy przez <xref:System.Activities.Expressions.Literal%601> działania. Następujące <xref:System.Activities.Statements.WriteLine> działań są funkcjonalnie równoważne.  
  
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
  
 Jest on nieprawidłowy zainicjować wyrażenia literału z dowolnym typem referencyjnym, z wyjątkiem <xref:System.String>. W poniższym przykładzie <xref:System.Activities.Statements.Assign> działania <xref:System.Activities.Statements.Assign.Value%2A> właściwość jest inicjowana przy użyciu wyrażenia literału `List<string>`.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Podczas weryfikowania przepływu pracy zawierającego to działanie jest zwracany następujący błąd sprawdzania poprawności: "literał obsługuje tylko typy wartości i niezmienne typu System.String. Typ System.Collections.Generic.List'1[System.String] nie może służyć jako literał." Jeśli przepływ pracy zostanie wywołana, <xref:System.Activities.InvalidWorkflowException> zgłaszany zawierające tekst błędu sprawdzania poprawności. Jest to błąd sprawdzania poprawności, ponieważ tworzenie wyrażenia literału z typem referencyjnym nie tworzy nowe wystąpienie klasy typu odwołania dla każdego wystąpienia przepływu pracy. Aby rozwiązać ten problem, Zamień wyrażenia literału, który tworzy i zwraca nowe wystąpienie klasy typu odwołania.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 Aby uzyskać więcej informacji na temat wyrażeń, zobacz [wyrażenia](../../../docs/framework/windows-workflow-foundation/expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Wywoływanie metod na obiektów przy użyciu wyrażeń i działania InvokeMethod  
 <xref:System.Activities.Expressions.InvokeMethod%601> Działania może służyć do wywołania statycznych lub wystąpienie metody klas .NET Framework. W poprzednim przykładzie w tym temacie losową liczbę został wygenerowany za pomocą <xref:System.Random> klasy.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 <xref:System.Activities.Expressions.InvokeMethod%601> Działanie może również zostały użyte w celu wywołania <xref:System.Random.Next%2A> metody <xref:System.Random> klasy.  
  
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
  
 Ponieważ <xref:System.Random.Next%2A> nie jest statyczną metodę wystąpienia <xref:System.Random> klasy podano dla <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> właściwości. W tym przykładzie tworzone jest nowe wystąpienie, przy użyciu wyrażenia języka Visual Basic, ale go może również zostały wcześniej utworzone i przechowywane w zmiennej przepływu pracy. W tym przykładzie będzie łatwiejszy w obsłudze <xref:System.Activities.Statements.Assign%601> działania zamiast <xref:System.Activities.Expressions.InvokeMethod%601> działania. Jeśli wywołanie metody ostatecznie wywoływany przez <xref:System.Activities.Statements.Assign%601> lub <xref:System.Activities.Expressions.InvokeMethod%601> działania jest długa uruchomiona, <xref:System.Activities.Expressions.InvokeMethod%601> ma korzyści, ponieważ ma ona <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> właściwości. Jeśli ta właściwość jest równa `true`, wywołana metoda będą wykonywane asynchronicznie w odniesieniu do przepływu pracy. W przypadku innych działań w sposób równoległy, ich nie zostanie zablokowana, gdy metoda asynchronicznie jest wykonywane. Ponadto jeśli wywoływanej metody nie ma wartości zwracanej, następnie <xref:System.Activities.Expressions.InvokeMethod%601> jest odpowiedni sposób wywołania metody.  
  
## <a name="arguments-and-dynamic-activities"></a>Argumenty i dynamiczne działań  
 Definicja przepływu pracy jest tworzony w kodzie, złożenia działań do drzewa działań, a następnie konfigurując właściwości i argumentów. Istniejące argumenty mogą być powiązane, ale nie można dodać nowe argumenty do działań. W tym przepływie pracy argumenty przekazywane do działania głównego. W kodu imperatywnego argumenty przepływu pracy są określane jako właściwości dla nowego typu CLR, a w XAML są zadeklarowane za pomocą `x:Class` i `x:Member`. Ponieważ nie ma żadnych nowego typu CLR tworzone podczas tworzenia definicji przepływu pracy jako drzewa obiektów w pamięci, nie można dodawać argumenty. Jednakże argumenty można dodać do <xref:System.Activities.DynamicActivity>. W tym przykładzie <xref:System.Activities.DynamicActivity%601> jest tworzony w tym przyjmuje dwa argumenty liczby całkowitej, dodaje je ze sobą i zwraca wynik. A <xref:System.Activities.DynamicActivityProperty> jest tworzony dla każdego argumentu i wynik operacji jest przypisywana do <xref:System.Activities.Activity%601.Result%2A> argument <xref:System.Activities.DynamicActivity%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](../../../samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Aby uzyskać więcej informacji o działaniach dynamicznej, zobacz [tworzenia działania w czasie wykonywania](../../../docs/framework/windows-workflow-foundation/creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Skompilowany działań  
 Dynamiczne działań są jednym ze sposobów, aby zdefiniować działanie, które zawiera argumenty przy użyciu kodu, ale również można tworzyć w kodzie i kompilowane na typy działań. Proste można tworzyć działania wyprowadzonych z <xref:System.Activities.CodeActivity>i działań asynchronicznych, które wynikają z <xref:System.Activities.AsyncCodeActivity>. Te działania może mieć argumentów, zwracać wartości i zdefiniuj logikę przy użyciu kodu imperatywnego. Aby uzyskać przykłady tworzenia tych rodzajów działań, zobacz [klasa bazowa CodeActivity](../../../docs/framework/windows-workflow-foundation/workflow-activity-authoring-using-the-codeactivity-class.md) i [tworzenie działań asynchronicznych](../../../docs/framework/windows-workflow-foundation/creating-asynchronous-activities-in-wf.md).  
  
 Działania, które wynikają z <xref:System.Activities.NativeActivity> można zdefiniować logikę przy użyciu kodu imperatywnego i mogą także zawierać działania podrzędne, definiujące logiki. Również mają pełny dostęp do funkcji aparatu plików wykonywalnych, takich jak tworzenie zakładek. Przykłady tworzenia <xref:System.Activities.NativeActivity>— na podstawie aktywności, zobacz [klasa bazowa NativeActivity](../../../docs/framework/windows-workflow-foundation/nativeactivity-base-class.md), [porady: tworzenie działania](../../../docs/framework/windows-workflow-foundation/how-to-create-an-activity.md)i [złożonego niestandardowego przy użyciu działania Native](../../../docs/framework/windows-workflow-foundation/samples/custom-composite-using-native-activity.md)próbki.  
  
 Działania, które wynikają z <xref:System.Activities.Activity> zdefiniować logikę wyłącznie przy użyciu działania podrzędne. Działania te są zwykle tworzone za pomocą projektanta przepływów pracy, ale można też zdefiniować przy użyciu kodu. W poniższym przykładzie `Square` działania jest zdefiniowany, pochodzącą z `Activity<int>`. `Square` Działanie ma jeden <xref:System.Activities.InArgument%601> o nazwie `Value`i umożliwia zdefiniowanie swojej logiki, określając <xref:System.Activities.Statements.Sequence> przy użyciu działania <xref:System.Activities.Activity.Implementation%2A> właściwości. <xref:System.Activities.Statements.Sequence> Zawiera działanie <xref:System.Activities.Statements.WriteLine> działania i <xref:System.Activities.Statements.Assign%601> działania. Razem te trzy czynności zaimplementować logikę `Square` działania.  
  
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
  
 W poniższym przykładzie definicji przepływu pracy, składającą się z pojedynczej `Square` działania jest wywoływany przy użyciu <xref:System.Activities.WorkflowInvoker>.  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli:  
  
 **Squaring wartość: 5**  
**Wynik: 25**
