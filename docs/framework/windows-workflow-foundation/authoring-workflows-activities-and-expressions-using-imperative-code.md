---
title: Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: 7f22880a965274961006f999b1170634377fcf1c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79183027"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego
Definicja przepływu pracy jest drzewem skonfigurowanych obiektów działania. To drzewo działań można zdefiniować na wiele sposobów, w tym przez ręczną edycję XAML lub za pomocą Projektanta przepływu pracy do tworzenia kodu XAML. Użycie XAML nie jest jednak wymagane. Definicje przepływu pracy można również tworzyć programowo. Ten temat zawiera omówienie tworzenia definicji przepływu pracy, działań i wyrażeń przy użyciu kodu. Aby zapoznać się z przykładami pracy z przepływami pracy XAML przy użyciu kodu, zobacz [Serialowanie przepływów pracy i działań do i z języka XAML](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Tworzenie definicji przepływu pracy  
 Definicję przepływu pracy można utworzyć, tworząc wystąpienie typu działania i konfigurując właściwości obiektu działania. Dla działań, które nie zawierają działań podrzędnych, można to osiągnąć za pomocą kilku wierszy kodu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
> Przykłady w tym <xref:System.Activities.WorkflowInvoker> temacie służy do uruchamiania przykładowych przepływów pracy. Aby uzyskać więcej informacji na temat wywoływania przepływów pracy, przekazywania argumentów i różnych dostępnych opcji hostingu, zobacz [Korzystanie z funkcji WorkflowInvoker i WorkflowApplication](using-workflowinvoker-and-workflowapplication.md).  
  
 W tym przykładzie tworzony jest przepływ <xref:System.Activities.Statements.WriteLine> pracy, który składa się z pojedynczego działania. <xref:System.Activities.Statements.WriteLine.Text%2A> Argument <xref:System.Activities.Statements.WriteLine> działania jest ustawiony, a przepływ pracy jest wywoływany. Jeśli działanie zawiera działania podrzędne, metoda budowy jest podobna. W poniższym przykładzie <xref:System.Activities.Statements.Sequence> użyto <xref:System.Activities.Statements.WriteLine> działania, które zawiera dwa działania.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Korzystanie z inicjatorów obiektów  
 W przykładach w tym temacie użyto składni inicjowania obiektu. Składnia inicjowania obiektów może być użytecznym sposobem tworzenia definicji przepływu pracy w kodzie, ponieważ zapewnia hierarchiczny widok działań w przepływie pracy i pokazuje relację między działaniami. Nie ma wymogu używania składni inicjowania obiektów podczas programowego tworzenia przepływów pracy. Poniższy przykład jest funkcjonalnie równoważne z poprzednim przykładem.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Aby uzyskać więcej informacji na temat inicjatorów obiektów, zobacz [Jak: Inicjowanie obiektów bez wywoływania konstruktora (Przewodnik programowania Języka C#)](../../csharp/programming-guide/classes-and-structs/how-to-initialize-objects-by-using-an-object-initializer.md) i [Jak: Deklarowanie obiektu przy użyciu inicjatora obiektu](../../visual-basic/programming-guide/language-features/objects-and-classes/how-to-declare-an-object-by-using-an-object-initializer.md).  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Praca ze zmiennymi, wartościami literału i wyrażeniami  
 Podczas tworzenia definicji przepływu pracy przy użyciu kodu, należy pamiętać, jaki kod jest wykonywany w ramach tworzenia definicji przepływu pracy i jaki kod jest wykonywany w ramach wykonywania wystąpienia tego przepływu pracy. Na przykład następujący przepływ pracy jest przeznaczony do generowania liczby losowej i zapisu go w konsoli.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Po wykonaniu tego kodu definicji przepływu `Random.Next` pracy jest wywoływane, a wynik jest przechowywany w definicji przepływu pracy jako wartość literału. Wiele wystąpień tego przepływu pracy można wywołać, a wszystkie będą wyświetlać ten sam numer. Aby podczas wykonywania przepływu pracy wystąpiło generowanie liczb losowych, należy użyć wyrażenia, które jest oceniane przy każdym uruchomieniu przepływu pracy. W poniższym przykładzie wyrażenie Visual Basic <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>jest używane z .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Wyrażenie w poprzednim przykładzie można również <xref:Microsoft.CSharp.Activities.CSharpValue%601> zaimplementować przy użyciu wyrażenia C# i.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 Wyrażenia C# muszą być kompilowane przed wywołaniem przepływu pracy zawierającego je. Jeśli wyrażenia C# nie są kompilowane, a <xref:System.NotSupportedException> jest generowany, gdy przepływ pracy ``Expression Activity type 'CSharpValue`1' requires compilation in order to run.  Please ensure that the workflow has been compiled.`` jest wywoływany z komunikatem podobnym do następującego: W większości scenariuszy obejmujących przepływy pracy utworzone w programie Visual Studio wyrażenia C# są kompilowane automatycznie, ale w niektórych scenariuszach, takich jak przepływy pracy kodu, wyrażenia C# muszą być kompilowane ręcznie. Na przykład, jak skompilować wyrażenia C#, zobacz [using C# wyrażenia c#](csharp-expressions.md#CodeWorkflows) sekcji przepływów pracy w temacie wyrażenia [C#.](csharp-expressions.md)  
  
 Reprezentuje <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> wyrażenie w składni języka Visual Basic, które mogą być używane jako <xref:Microsoft.CSharp.Activities.CSharpValue%601> wartość r w wyrażeniu i reprezentuje wyrażenie w składni C#, które mogą być używane jako r-wartość w wyrażeniu. Wyrażenia te są oceniane za każdym razem, gdy wykonywane jest działanie zawierające. Wynik wyrażenia jest przypisany do zmiennej `n`przepływu pracy, a te wyniki są używane przez następne działanie w przepływie pracy. Aby uzyskać dostęp do wartości `n` zmiennej przepływu <xref:System.Activities.ActivityContext> pracy w czasie wykonywania, jest wymagane. Dostęp do tego można uzyskać za pomocą następującego wyrażenia lambda.  
  
> [!NOTE]
> Należy zauważyć, że oba te kody są przy użyciu języka C# jako języka programowania, ale jeden używa <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> a i jeden używa . <xref:Microsoft.CSharp.Activities.CSharpValue%601> <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>i <xref:Microsoft.CSharp.Activities.CSharpValue%601> może być używany zarówno w projektach języka Visual Basic, jak i C#. Domyślnie wyrażenia utworzone w projektancie przepływu pracy są zgodne z językiem projektu hostingowego. Podczas tworzenia przepływów pracy w kodzie żądany język jest w gestii autora przepływu pracy.  
  
 W tych przykładach wynik wyrażenia jest przypisany do `n`zmiennej przepływu pracy, a te wyniki są używane przez następne działanie w przepływie pracy. Aby uzyskać dostęp do wartości `n` zmiennej przepływu <xref:System.Activities.ActivityContext> pracy w czasie wykonywania, jest wymagane. Dostęp do tego można uzyskać za pomocą następującego wyrażenia lambda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [Wyrażenia Lambda (Przewodnik programowania C# lub](../../csharp/programming-guide/statements-expressions-operators/lambda-expressions.md) Wyrażenia [Lambda (Visual Basic)](../../visual-basic/programming-guide/language-features/procedures/lambda-expressions.md).  
  
 Wyrażenia Lambda nie są serializable do formatu XAML. Jeśli zostanie podjęta próba serializacji przepływu pracy z wyrażeniami lambda, jest generowany z następującym komunikatem: <xref:System.Activities.Expressions.LambdaSerializationException> "Ten przepływ pracy zawiera wyrażenia lambda określone w kodzie. Wyrażenia te nie są serializable XAML. Aby ułatwić procesowanie z programem XAML,użyj języka VisualBasicValue/VisualBasicReference lub ExpressionServices.Convert(lambda). Spowoduje to przekształcenie wyrażeń lambda w działania ekspresji." Aby to wyrażenie było zgodne z <xref:System.Activities.Expressions.ExpressionServices> <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>kodem XAML, należy użyć i , jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 Można <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> również użyć. Należy zauważyć, że wyrażenie lambda nie jest wymagane podczas korzystania z wyrażenia Visual Basic.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 W czasie wykonywania wyrażenia języka Visual Basic są kompilowane do wyrażeń LINQ. Oba poprzednie przykłady są serializable do XAML, ale jeśli serializowane XAML jest przeznaczony do wyświetlania <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> i edytowania w projektancie przepływu pracy, użyj dla wyrażeń. Serializowane przepływy pracy, które używają `ExpressionServices.Convert` mogą być otwierane w projektancie, ale wartość wyrażenia będzie pusta. Aby uzyskać więcej informacji na temat serializacji przepływów pracy do xaml, zobacz [Serialowanie przepływów pracy i działań do i z XAML](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Wyrażenia literalne i typy odwołań  
 Wyrażenia dosłowne są reprezentowane w <xref:System.Activities.Expressions.Literal%601> przepływach pracy przez działanie. Następujące <xref:System.Activities.Statements.WriteLine> działania są funkcjonalnie równoważne.  
  
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
  
 Inicjowanie dosłownego wyrażenia z dowolnym <xref:System.String>typem odwołania jest nieprawidłowe z wyjątkiem . W poniższym przykładzie <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.Assign.Value%2A> właściwość działania jest inicjowana `List<string>`za pomocą dosłownego wyrażenia przy użyciu pliku .  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Po sprawdzeniu poprawności przepływu pracy zawierającego to działanie zwracany jest następujący błąd sprawdzania poprawności: "Literal obsługuje tylko typy wartości i niezmienny typ System.String. Typ System.Collections.Generic.List'1[System.String] nie może być używany jako literał." Jeśli przepływ pracy jest wywoływany, <xref:System.Activities.InvalidWorkflowException> jest generowany, który zawiera tekst błędu sprawdzania poprawności. Jest to błąd sprawdzania poprawności, ponieważ utworzenie wyrażenia dosłownego z typem odwołania nie tworzy nowego wystąpienia typu odwołania dla każdego wystąpienia przepływu pracy. Aby rozwiązać ten problem, zastąp wyrażenie dosłowne wyrażenie, które tworzy i zwraca nowe wystąpienie typu odwołania.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 Aby uzyskać więcej informacji na temat wyrażeń, zobacz [Wyrażenia](expressions.md).  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Wywoływanie metod w obiektach przy użyciu wyrażeń i działania InvokeMethod  
 Działanie <xref:System.Activities.Expressions.InvokeMethod%601> może służyć do wywoływania metod statycznych i instancji klas w .NET Framework. W poprzednim przykładzie w tym temacie losowa <xref:System.Random> liczba została wygenerowana przy użyciu klasy.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Działanie <xref:System.Activities.Expressions.InvokeMethod%601> może również służyć do <xref:System.Random.Next%2A> wywoływania <xref:System.Random> metody klasy.  
  
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
  
 Ponieważ <xref:System.Random.Next%2A> nie jest metodą statyczną, <xref:System.Random> wystąpienie klasy <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> jest dostarczane dla właściwości. W tym przykładzie nowe wystąpienie jest tworzone przy użyciu wyrażenia Języka Visual Basic, ale może również zostać utworzone wcześniej i przechowywane w zmiennej przepływu pracy. W tym przykładzie byłoby łatwiej używać <xref:System.Activities.Statements.Assign%601> działania zamiast <xref:System.Activities.Expressions.InvokeMethod%601> działania. Jeśli wywołanie metody ostatecznie wywoływane <xref:System.Activities.Statements.Assign%601> <xref:System.Activities.Expressions.InvokeMethod%601> przez lub działania <xref:System.Activities.Expressions.InvokeMethod%601> jest długotrwałe, ma <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> przewagę, ponieważ ma właściwość. Gdy ta właściwość `true`jest ustawiona na , wywoływana metoda będzie działać asynchronicznie w odniesieniu do przepływu pracy. Jeśli inne działania są równolegle, nie zostaną zablokowane, gdy metoda jest asynchronicznie wykonywania. Ponadto jeśli metoda, która ma być wywoływana <xref:System.Activities.Expressions.InvokeMethod%601> ma wartość zwracaną, a następnie jest odpowiedni sposób wywołania metody.  
  
## <a name="arguments-and-dynamic-activities"></a>Argumenty i działania dynamiczne  
 Definicja przepływu pracy jest tworzona w kodzie przez zmontowanie działań w drzewo działań i skonfigurowanie wszystkich właściwości i argumentów. Istniejące argumenty mogą być powiązane, ale nowe argumenty nie mogą być dodawane do działań. Obejmuje to argumenty przepływu pracy przekazywane do działania głównego. W kodzie imperatywnym argumenty przepływu pracy są określane jako właściwości nowego typu CLR, a w XAML są one deklarowane przy użyciu `x:Class` i `x:Member`. Ponieważ nie ma nowego typu CLR utworzonego, gdy definicja przepływu pracy jest tworzona jako drzewo obiektów w pamięci, nie można dodać argumentów. Jednak argumenty można dodać <xref:System.Activities.DynamicActivity>do . W tym przykładzie <xref:System.Activities.DynamicActivity%601> jest tworzony, który przyjmuje dwa argumenty całkowite, dodaje je razem i zwraca wynik. A <xref:System.Activities.DynamicActivityProperty> jest tworzony dla każdego argumentu, a wynik <xref:System.Activities.Activity%601.Result%2A> operacji jest <xref:System.Activities.DynamicActivity%601>przypisany do argumentu .  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Aby uzyskać więcej informacji na temat działań dynamicznych, zobacz [Tworzenie działania w czasie wykonywania](creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Skompilowane działania  
 Działania dynamiczne są jednym ze sposobów definiowania działania, które zawiera argumenty przy użyciu kodu, ale działania mogą być również tworzone w kodzie i kompilowane w typy. Można tworzyć proste działania, które <xref:System.Activities.CodeActivity>wynikają z działań asynchronicznych, które wynikają z <xref:System.Activities.AsyncCodeActivity>. Te działania mogą mieć argumenty, zwracać wartości i definiować ich logikę przy użyciu kodu imperatywu. Aby zapoznać się z przykładami tworzenia tego typu działań, zobacz [Klasa podstawowa CodeActivity](workflow-activity-authoring-using-the-codeactivity-class.md) i [Tworzenie działań asynchronicznych](creating-asynchronous-activities-in-wf.md).  
  
 Działania, które wynikają z <xref:System.Activities.NativeActivity> można zdefiniować ich logiki przy użyciu kodu imperatywu i mogą również zawierać działania podrzędne, które definiują logikę. Mają również pełny dostęp do funkcji środowiska wykonawczego, takich jak tworzenie zakładek. Aby zapoznać się <xref:System.Activities.NativeActivity>z przykładami tworzenia działania opartego na aktywności, zobacz [NativeActivity Base Class](nativeactivity-base-class.md), [How to: Create an Activity](how-to-create-an-activity.md)i Custom Composite using Native [Activity](./samples/custom-composite-using-native-activity.md) sample.  
  
 Działania, które wynikają z <xref:System.Activities.Activity> definiowania ich logiki wyłącznie za pomocą działań podrzędnych. Te działania są zazwyczaj tworzone przy użyciu projektanta przepływu pracy, ale można również zdefiniować przy użyciu kodu. W poniższym przykładzie zdefiniowano `Square` działanie, `Activity<int>`które wywodzi się z . Działanie `Square` ma jeden <xref:System.Activities.InArgument%601> `Value`o nazwie i definiuje jego <xref:System.Activities.Statements.Sequence> logikę, <xref:System.Activities.Activity.Implementation%2A> określając działanie przy użyciu właściwości. Działanie <xref:System.Activities.Statements.Sequence> zawiera <xref:System.Activities.Statements.WriteLine> działanie i <xref:System.Activities.Statements.Assign%601> działanie. Razem te trzy działania implementują `Square` logikę działania.  
  
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
  
 W poniższym przykładzie wywoływana jest `Square` definicja przepływu <xref:System.Activities.WorkflowInvoker>pracy składająca się z pojedynczego działania przy użyciu programu .  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 Po wywołaniu przepływu pracy do konsoli są wyświetlane następujące dane wyjściowe:  
  
 **Kwadratura wartości: 5**  
**Wynik: 25**
