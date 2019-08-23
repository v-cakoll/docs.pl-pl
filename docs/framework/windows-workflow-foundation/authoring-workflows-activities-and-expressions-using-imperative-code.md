---
title: Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego
ms.date: 03/30/2017
ms.assetid: cefc9cfc-2882-4eb9-8c94-7a6da957f2b2
ms.openlocfilehash: 22f5928dda55d77fde2ee518510eb2890e55b446
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69940895"
---
# <a name="authoring-workflows-activities-and-expressions-using-imperative-code"></a>Tworzenie przepływów pracy, działań i wyrażeń przy użyciu kodu imperatywnego
Definicja przepływu pracy jest drzewem skonfigurowanych obiektów działania. To drzewo działań można zdefiniować na wiele sposobów, w tym poprzez ręczne edytowanie kodu XAML lub użycie Projektant przepływu pracy do tworzenia kodu XAML. Jednak użycie języka XAML nie jest wymagane. Definicje przepływów pracy można także tworzyć programowo. Ten temat zawiera omówienie tworzenia definicji przepływu pracy, działań i wyrażeń przy użyciu kodu. Aby zapoznać się z przykładami pracy z przepływami pracy XAML przy użyciu kodu, zobacz [Serializowanie przepływów pracy i działań do i z języka XAML](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
## <a name="creating-workflow-definitions"></a>Tworzenie definicji przepływu pracy  
 Definicję przepływu pracy można utworzyć przez utworzenie wystąpienia typu działania i skonfigurowanie właściwości obiektu działania. W przypadku działań, które nie zawierają działań podrzędnych, można to zrobić za pomocą kilku wierszy kodu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#47](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#47)]  
  
> [!NOTE]
> Przykłady w tym temacie służą <xref:System.Activities.WorkflowInvoker> do uruchamiania przykładowych przepływów pracy. Aby uzyskać więcej informacji na temat wywoływania przepływów pracy, przekazywania argumentów i różnych dostępnych opcji hostingu, zobacz [using WorkflowInvoker and WorkflowApplication](using-workflowinvoker-and-workflowapplication.md).  
  
 W tym przykładzie tworzony jest przepływ pracy, który składa <xref:System.Activities.Statements.WriteLine> się z pojedynczego działania. Argument<xref:System.Activities.Statements.WriteLine.Text%2A>działaniajest ustawiony, a przepływ pracy jest wywoływany. <xref:System.Activities.Statements.WriteLine> Jeśli działanie zawiera działania podrzędne, Metoda konstrukcji jest podobna. W poniższym przykładzie zastosowano <xref:System.Activities.Statements.Sequence> działanie zawierające dwa <xref:System.Activities.Statements.WriteLine> działania.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#48](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#48)]  
  
### <a name="using-object-initializers"></a>Korzystanie z inicjatorów obiektów  
 W przykładach w tym temacie użyto składni inicjowania obiektu. Składnia inicjowania obiektu może być przydatnym sposobem tworzenia definicji przepływu pracy w kodzie, ponieważ zawiera hierarchiczny widok działań w przepływie pracy i pokazuje relację między działaniami. Nie ma potrzeby używania składni inicjowania obiektów podczas programistycznego tworzenia przepływów pracy. Poniższy przykład jest funkcjonalnie równoważny z poprzednim przykładem.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#49](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#49)]  
  
 Aby uzyskać więcej informacji na temat inicjatorów obiektów [, zobacz How to: Inicjuj obiekty bez wywoływania konstruktora (C# Przewodnik programowania)](https://go.microsoft.com/fwlink/?LinkId=161015) i [instrukcje: Zadeklaruj obiekt za pomocą inicjatora](https://go.microsoft.com/fwlink/?LinkId=161016)obiektów.  
  
### <a name="working-with-variables-literal-values-and-expressions"></a>Praca ze zmiennymi, literałami i wyrażeniami  
 Podczas tworzenia definicji przepływu pracy przy użyciu kodu należy wiedzieć, jaki kod jest wykonywany w ramach tworzenia definicji przepływu pracy i jaki kod jest wykonywany w ramach wykonywania wystąpienia tego przepływu pracy. Na przykład poniższy przepływ pracy jest przeznaczony do generowania liczby losowej i zapisywania jej w konsoli programu.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#50](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#50)]  
  
 Gdy ten kod definicji przepływu pracy jest wykonywany, wywołanie `Random.Next` jest wykonywane, a wynik jest przechowywany w definicji przepływu pracy jako wartość literału. Wiele wystąpień tego przepływu pracy można wywołać, a wszystkie będą wyświetlać ten sam numer. Aby wygenerowanie losowej liczby wystąpiło podczas wykonywania przepływu pracy, należy użyć wyrażenia, które jest oceniane za każdym razem, gdy przepływ pracy zostanie uruchomiony. W poniższym przykładzie wyrażenie Visual Basic jest używane z <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Wyrażenie w poprzednim przykładzie mogło być również zaimplementowane przy użyciu <xref:Microsoft.CSharp.Activities.CSharpValue%601> C# wyrażenia i.  
  
```csharp  
new Assign<int>  
{  
    To = n,  
    Value = new CSharpValue<int>("new Random().Next(1, 101)")  
}  
```  
  
 C#wyrażenia muszą być kompilowane przed wywołaniem przepływu pracy zawierającego je. Jeśli C# wyrażenia nie są kompilowane, <xref:System.NotSupportedException> jest zgłaszany, gdy przepływ pracy jest wywoływany z komunikatem podobnym do poniższego: `Expression Activity type 'CSharpValue`1 ' wymaga kompilacji w celu uruchomienia.  Upewnij się, że przepływ pracy został skompilowany. "w większości scenariuszy obejmujących przepływy pracy utworzone w C# programie Visual Studio wyrażenia są kompilowane automatycznie, ale w niektórych scenariuszach, takich jak przepływy pracy kodu, C# wyrażenia muszą być ręczne tworzone. Aby zapoznać się z przykładem kompilowania C# wyrażeń, zobacz sekcję [using C# Expressions in Code przepływy pracy w](csharp-expressions.md#CodeWorkflows) temacie [ C# Expressions](csharp-expressions.md) .  
  
 Reprezentuje wyrażenie w składni Visual Basic, które może być używane jako wartość r w wyrażeniu, <xref:Microsoft.CSharp.Activities.CSharpValue%601> a reprezentuje wyrażenie C# , które może być użyte jako wartość języka r w wyrażeniu. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> Te wyrażenia są oceniane przy każdym wykonywaniu działania zawierającego. Wynik wyrażenia jest przypisywany do zmiennej `n`przepływu pracy, a wyniki są używane przez następne działanie w przepływie pracy. Aby uzyskać dostęp do wartości zmiennej `n` przepływu pracy w czasie wykonywania <xref:System.Activities.ActivityContext> , jest to wymagane. Dostęp do niego można uzyskać za pomocą następującego wyrażenia lambda.  
  
> [!NOTE]
> Należy zauważyć, że oba te kody są przykładami C# użycia jako język programowania, ale jeden <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> <xref:Microsoft.CSharp.Activities.CSharpValue%601>z nich używa a. <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601>i <xref:Microsoft.CSharp.Activities.CSharpValue%601> mogą być używane zarówno w Visual Basic, C# jak i w projektach. Domyślnie wyrażenia utworzone w Projektancie przepływu pracy pasują do języka projektu hostingu. W przypadku tworzenia przepływów pracy w kodzie żądany język jest według uznania autora przepływu pracy.  
  
 W tych przykładach wynik wyrażenia jest przypisywany do zmiennej `n`przepływu pracy, a wyniki są używane przez następne działanie w przepływie pracy. Aby uzyskać dostęp do wartości zmiennej `n` przepływu pracy w czasie wykonywania <xref:System.Activities.ActivityContext> , jest to wymagane. Dostęp do niego można uzyskać za pomocą następującego wyrażenia lambda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#52](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#52)]  
  
 Aby uzyskać więcej informacji na temat wyrażeń lambda, zobacz [wyrażeniaC# lambda (Przewodnik programowania)](https://go.microsoft.com/fwlink/?LinkID=152436) lub [wyrażenia lambda (Visual Basic)](https://go.microsoft.com/fwlink/?LinkID=152437).  
  
 Wyrażenia lambda nie są możliwe do serializacji na format XAML. Jeśli zostanie podjęta próba serializacji przepływu pracy z wyrażeniami lambda, <xref:System.Activities.Expressions.LambdaSerializationException> zostanie zgłoszony następujący komunikat: "Ten przepływ pracy zawiera wyrażenia lambda określone w kodzie. Te wyrażenia nie są możliwym do serializacji XAML. Aby można było serializować kod XAML przepływu pracy, należy użyć VisualBasicValue/VisualBasicReference lub ExpressionServices. Convert (lambda). Spowoduje to przekonwertowanie wyrażeń lambda na działania wyrażeń. " Aby to wyrażenie było zgodne z XAML, użyj <xref:System.Activities.Expressions.ExpressionServices> i <xref:System.Activities.Expressions.ExpressionServices.Convert%2A>, jak pokazano w poniższym przykładzie.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#53](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#53)]  
  
 <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> Można również użyć. Należy pamiętać, że w przypadku używania wyrażenia Visual Basic nie jest wymagane wyrażenie lambda.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#54](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#54)]  
  
 W czasie wykonywania wyrażenia Visual Basic są kompilowane do wyrażeń LINQ. Oba poprzednie przykłady można serializować do języka XAML, ale jeśli serializowany kod XAML jest przeznaczony do wyświetlania i edytowania w Projektancie przepływów pracy, użyj <xref:Microsoft.VisualBasic.Activities.VisualBasicValue%601> dla wyrażeń. Serializowane przepływy `ExpressionServices.Convert` pracy, które mogą być otwierane w projektancie, ale wartości wyrażenia będą puste. Aby uzyskać więcej informacji na temat serializowania przepływów pracy do języka XAML, zobacz [Serializowanie przepływów pracy i działań do i z języka XAML](serializing-workflows-and-activities-to-and-from-xaml.md).  
  
#### <a name="literal-expressions-and-reference-types"></a>Wyrażenia literału i typy odwołań  
 Wyrażenia literałów są reprezentowane w przepływach <xref:System.Activities.Expressions.Literal%601> pracy przez działanie. Poniższe <xref:System.Activities.Statements.WriteLine> działania są funkcjonalnie równoważne.  
  
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
  
 Nie można zainicjować wyrażenia literału z dowolnym typem referencyjnym z wyjątkiem <xref:System.String>. W poniższym przykładzie <xref:System.Activities.Statements.Assign> <xref:System.Activities.Statements.Assign.Value%2A> Właściwość działania jest inicjowana z wyrażeniem literału używającym elementu `List<string>`.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new List<string>())  
},  
```  
  
 Gdy przepływ pracy zawierający to działanie zostanie sprawdzony, zwracany jest następujący błąd sprawdzania poprawności: "Literał obsługuje tylko typy wartości i niezmienny typ System. String. Nie można użyć typu System. Collections. Generic. list "1 [System. String] jako literału". Jeśli przepływ pracy jest wywoływany, <xref:System.Activities.InvalidWorkflowException> zostanie zgłoszony, który zawiera tekst błędu walidacji. Jest to błąd walidacji, ponieważ utworzenie wyrażenia literału z typem referencyjnym nie powoduje utworzenia nowego wystąpienia typu odwołania dla każdego wystąpienia przepływu pracy. Aby rozwiązać ten problem, zastąp wyrażenie literału, które tworzy i zwraca nowe wystąpienie typu odwołania.  
  
```csharp  
new Assign  
{  
    To = new OutArgument<List<string>>(items),  
    Value = new InArgument<List<string>>(new VisualBasicValue<List<string>>("New List(Of String)"))  
},  
```  
  
 Aby uzyskać więcej informacji na temat wyrażeń [](expressions.md), zobacz Expressions.  
  
#### <a name="invoking-methods-on-objects-using-expressions-and-the-invokemethod-activity"></a>Wywoływanie metod dla obiektów przy użyciu wyrażeń i działania InvokeMethod  
 <xref:System.Activities.Expressions.InvokeMethod%601> Działanie może służyć do wywoływania metod statycznych i wystąpień klas w .NET Framework. W poprzednim przykładzie w tym temacie Wygenerowano losową liczbę przy użyciu <xref:System.Random> klasy.  
  
 [!code-csharp[CFX_WorkflowApplicationExample#51](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#51)]  
  
 Działanie mogło również zostać użyte do <xref:System.Random.Next%2A> wywołania metody <xref:System.Random> klasy. <xref:System.Activities.Expressions.InvokeMethod%601>  
  
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
  
 Ponieważ <xref:System.Random.Next%2A> nie jest to metoda statyczna, wystąpienie <xref:System.Random> <xref:System.Activities.Expressions.InvokeMethod%601.TargetObject%2A> klasy jest dostarczane dla właściwości. W tym przykładzie nowe wystąpienie jest tworzone przy użyciu wyrażenia Visual Basic, ale mogło być również wcześniej utworzone i przechowywane w zmiennej przepływu pracy. W tym przykładzie łatwiej będzie użyć <xref:System.Activities.Statements.Assign%601> działania zamiast <xref:System.Activities.Expressions.InvokeMethod%601> działania. Jeśli wywołanie metody ostatecznie <xref:System.Activities.Statements.Assign%601> wywołane przez albo <xref:System.Activities.Expressions.InvokeMethod%601> działania jest długotrwałe, ma korzyść <xref:System.Activities.Expressions.InvokeMethod%601> , ponieważ ma <xref:System.Activities.Expressions.InvokeMethod%601.RunAsynchronously%2A> właściwość. Gdy ta właściwość jest ustawiona na `true`, wywoływana metoda zostanie uruchomiona asynchronicznie w odniesieniu do przepływu pracy. Jeśli inne działania są równolegle, nie będą blokowane, gdy metoda jest wykonywana asynchronicznie. Ponadto, jeśli metoda, która ma zostać wywołana nie ma wartości zwracanej <xref:System.Activities.Expressions.InvokeMethod%601> , jest odpowiednim sposobem wywołania metody.  
  
## <a name="arguments-and-dynamic-activities"></a>Argumenty i działania dynamiczne  
 Definicja przepływu pracy jest tworzona w kodzie przez umieszczenie działań w drzewie aktywności i skonfigurowanie wszelkich właściwości i argumentów. Istniejące argumenty mogą być powiązane, ale nie można dodać nowych argumentów do działań. Obejmuje to argumenty przepływu pracy przekazane do działania głównego. W kodzie bezwzględnym argumenty przepływu pracy są określane jako właściwości dla nowego typu CLR, a w języku XAML są one deklarowane `x:Member`za pomocą `x:Class` i. Ponieważ nie istnieje nowy typ CLR tworzony podczas tworzenia definicji przepływu pracy jako drzewa obiektów w pamięci, nie można dodawać argumentów. Jednak argumenty mogą być dodawane do <xref:System.Activities.DynamicActivity>. W tym przykładzie <xref:System.Activities.DynamicActivity%601> jest tworzony, który przyjmuje dwa argumenty całkowite, dodaje je razem i zwraca wynik. Jest tworzony dla każdego argumentu, a wynik operacji jest przypisywany <xref:System.Activities.Activity%601.Result%2A> do argumentu <xref:System.Activities.DynamicActivity%601>obiektu. <xref:System.Activities.DynamicActivityProperty>  
  
 [!code-csharp[CFX_WorkflowApplicationExample#55](~/samples/snippets/csharp/VS_Snippets_CFX/cfx_workflowapplicationexample/cs/program.cs#55)]  
  
 Aby uzyskać więcej informacji o działaniach dynamicznych, zobacz [Tworzenie działania w czasie wykonywania](creating-an-activity-at-runtime-with-dynamicactivity.md).  
  
## <a name="compiled-activities"></a>Skompilowane działania  
 Działania dynamiczne są jednym ze sposobów definiowania działania, które zawiera argumenty przy użyciu kodu, ale działania mogą być również tworzone w kodzie i kompilowane do typów. Proste działania można utworzyć, które pochodzą z <xref:System.Activities.CodeActivity>i działań asynchronicznych, które pochodzą <xref:System.Activities.AsyncCodeActivity>z. Działania te mogą mieć argumenty, wartości zwracane i definiować ich logiki przy użyciu kodu bezwzględnego. Przykłady tworzenia tego typu działań można znaleźć w temacie [elementu CodeActivity Base Class (klasa bazowa](workflow-activity-authoring-using-the-codeactivity-class.md) ) i [Tworzenie działań asynchronicznych](creating-asynchronous-activities-in-wf.md).  
  
 Działania, które pochodzą <xref:System.Activities.NativeActivity> z programu, mogą definiować swoje logiki przy użyciu bezwzględnego kodu i mogą również zawierać działania podrzędne, które definiują logikę. Mają także pełny dostęp do funkcji środowiska uruchomieniowego, takich jak tworzenie zakładek. Przykłady tworzenia <xref:System.Activities.NativeActivity>działań opartych na programie można znaleźć w temacie [Klasa bazowa natywna](nativeactivity-base-class.md), [jak: Utwórz działanie](how-to-create-an-activity.md)oraz [niestandardowy kompozyt przy użyciu natywnego działania](./samples/custom-composite-using-native-activity.md) .  
  
 Działania, które wynikają z <xref:System.Activities.Activity> definiowania logiki wyłącznie przy użyciu działań podrzędnych. Te działania są zwykle tworzone za pomocą projektanta przepływów pracy, ale można je również zdefiniować za pomocą kodu. W poniższym przykładzie `Square` zdefiniowano działanie, które pochodzi od `Activity<int>`. <xref:System.Activities.InArgument%601> <xref:System.Activities.Statements.Sequence> Działanie ma jedną nazwę`Value`i definiuje<xref:System.Activities.Activity.Implementation%2A> jej logikę, określając działanie przy użyciu właściwości. `Square` Działanie zawiera działanie i<xref:System.Activities.Statements.Assign%601>działanie. <xref:System.Activities.Statements.WriteLine> <xref:System.Activities.Statements.Sequence> Razem te trzy działania implementują logikę `Square` działania.  
  
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
  
 W poniższym przykładzie definicja przepływu pracy składająca się z pojedynczego `Square` działania jest wywoływana przy użyciu. <xref:System.Activities.WorkflowInvoker>  
  
```csharp  
Dictionary<string, object> inputs = new Dictionary<string, object> {{ "Value", 5}};  
int result = WorkflowInvoker.Invoke(new Square(), inputs);  
Console.WriteLine("Result: {0}", result);  
```  
  
 Po wywołaniu przepływu pracy następujące dane wyjściowe są wyświetlane w konsoli programu:  
  
 **Podniesienie wartość: 5**  
**Wynika 25**
