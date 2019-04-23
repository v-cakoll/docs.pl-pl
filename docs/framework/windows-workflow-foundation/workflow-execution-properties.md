---
title: Właściwości wykonania przepływu pracy
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 0f87e58a034cbc11565fc74347e6b4362952093c
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/22/2019
ms.locfileid: "59974009"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="acab9-102">Właściwości wykonania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="acab9-102">Workflow Execution Properties</span></span>
<span data-ttu-id="acab9-103">Za pomocą lokalny magazyn wątków (TLS) środowisko CLR utrzymuje kontekst wykonania dla każdego wątku.</span><span class="sxs-lookup"><span data-stu-id="acab9-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="acab9-104">Ten kontekst wykonywania kontroluje wątku dobrze znane właściwości, takich jak tożsamość wątku otoczenia transakcji, oraz uprawnień bieżącego zestawu właściwości wątków użytkownika, takie jak o nazwie miejsc.</span><span class="sxs-lookup"><span data-stu-id="acab9-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="acab9-105">W odróżnieniu od programów bezpośrednio przeznaczonych dla środowiska CLR programy przepływu pracy są hierarchicznie zakresie drzewa działań, które są wykonywane w środowisku niezależny od wątku.</span><span class="sxs-lookup"><span data-stu-id="acab9-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="acab9-106">Oznacza to, że standardowych mechanizmów TLS nie bezpośrednio można określić, jakie kontekstu znajduje się w zakresie dla elementu roboczego danego.</span><span class="sxs-lookup"><span data-stu-id="acab9-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="acab9-107">Na przykład dwie gałęzie równoległego wykonywania mogą używać różnych transakcji, ale harmonogram może przeplot ich wykonanie w tym samym wątku środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="acab9-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="acab9-108">Właściwości wykonania przepływu pracy zapewniają mechanizm, aby dodać określonej właściwości kontekstu do działania środowiska.</span><span class="sxs-lookup"><span data-stu-id="acab9-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="acab9-109">Dzięki temu działanie, aby zadeklarować właściwości, które znajdują się w zakresie dla jego poddrzewa i udostępnia również punkty zaczepienia dotyczące konfigurowania i zniszczenia TLS do prawidłowego współdziałania z obiektów CLR.</span><span class="sxs-lookup"><span data-stu-id="acab9-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="acab9-110">Tworzenie i używanie właściwości wykonania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="acab9-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="acab9-111">Właściwości wykonania przepływu pracy jest zwykle implementuje <xref:System.Activities.IExecutionProperty> interfejsu, chociaż może wdrożyć właściwości koncentruje się na komunikaty <xref:System.ServiceModel.Activities.ISendMessageCallback> i <xref:System.ServiceModel.Activities.IReceiveMessageCallback> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="acab9-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="acab9-112">Aby utworzyć właściwości wykonania przepływu pracy, należy utworzyć klasę, która implementuje <xref:System.Activities.IExecutionProperty> interfejsu i zaimplementuj elementy członkowskie <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> i <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="acab9-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="acab9-113">Te elementy członkowskie Podaj właściwości wykonywania z szansą sprzedaży poprawnie skonfigurować i zatrzymywania pamięci lokalnej wątku podczas każdego pulse pracy działania, który zawiera właściwości, łącznie z dowolnego działania podrzędne.</span><span class="sxs-lookup"><span data-stu-id="acab9-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="acab9-114">W tym przykładzie `ConsoleColorProperty` jest tworzony w tym zestawy `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="acab9-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
```csharp  
class ConsoleColorProperty : IExecutionProperty  
{  
    public const string Name = "ConsoleColorProperty";  
  
    ConsoleColor original;  
    ConsoleColor color;  
  
    public ConsoleColorProperty(ConsoleColor color)  
    {  
        this.color = color;  
    }  
  
    void IExecutionProperty.SetupWorkflowThread()  
    {  
        original = Console.ForegroundColor;  
        Console.ForegroundColor = color;  
    }  
  
    void IExecutionProperty.CleanupWorkflowThread()  
    {  
        Console.ForegroundColor = original;  
    }  
}  
```  
  
 <span data-ttu-id="acab9-115">Autorzy aktywności można użyć tej właściwości, rejestrując je w działania wykonywania zastąpienie.</span><span class="sxs-lookup"><span data-stu-id="acab9-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="acab9-116">W tym przykładzie `ConsoleColorScope` działania jest zdefiniowany, który rejestruje `ConsoleColorProperty` przez dodanie jej do <xref:System.Activities.NativeActivityContext.Properties%2A> kolekcji bieżącego <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="acab9-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
```csharp  
public sealed class ConsoleColorScope : NativeActivity  
{  
    public ConsoleColorScope()  
        : base()  
    {  
    }  
  
    public ConsoleColor Color { get; set; }  
    public Activity Body { get; set; }  
  
    protected override void Execute(NativeActivityContext context)  
    {  
        context.Properties.Add(ConsoleColorProperty.Name, new ConsoleColorProperty(this.Color));  
  
        if (this.Body != null)  
        {  
            context.ScheduleActivity(this.Body);  
        }  
    }  
}  
```  
  
 <span data-ttu-id="acab9-117">Uruchomienia działania treści pulse pracy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> nosi nazwę metody, właściwości, a po zakończeniu pulse pracy <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="acab9-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="acab9-118">W tym przykładzie przepływ pracy jest tworzony, który używa <xref:System.Activities.Statements.Parallel> działanie przy użyciu trzech gałęzi.</span><span class="sxs-lookup"><span data-stu-id="acab9-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="acab9-119">Użyj najpierw dwie gałęzie `ConsoleColorScope` działanie i trzeci gałęzi, nie ma.</span><span class="sxs-lookup"><span data-stu-id="acab9-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="acab9-120">Wszystkie trzy gałęzie zawierać dwa <xref:System.Activities.Statements.WriteLine> działań i <xref:System.Activities.Statements.Delay> działania.</span><span class="sxs-lookup"><span data-stu-id="acab9-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="acab9-121">Gdy <xref:System.Activities.Statements.Parallel> wykonuje działania, wykonywania działań, które są zawarte w gałęzi, w sposób przeplotem, ale ponieważ wykonuje każde działanie podrzędne przez stosowania kolorów poprawnej konsoli `ConsoleColorProperty`.</span><span class="sxs-lookup"><span data-stu-id="acab9-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
```csharp  
Activity wf = new Parallel  
{  
    Branches =   
    {  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Blue,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start blue text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End blue text."  
                    }  
                }  
            }  
        },  
        new ConsoleColorScope  
        {  
            Color = ConsoleColor.Red,  
            Body = new Sequence  
            {  
                Activities =   
                {  
                    new WriteLine  
                    {  
                        Text = "Start red text."  
                    },  
                    new Delay  
                    {  
                        Duration = TimeSpan.FromSeconds(1)  
                    },  
                    new WriteLine  
                    {  
                        Text = "End red text."  
                    }  
                }  
            }  
        },  
        new Sequence  
        {  
            Activities =   
            {  
                new WriteLine  
                {  
                    Text = "Start default text."  
                },  
                new Delay  
                {  
                    Duration = TimeSpan.FromSeconds(1)  
                },  
                new WriteLine  
                {  
                    Text = "End default text."  
                }  
            }  
        }  
    }  
};  
  
WorkflowInvoker.Invoke(wf);  
```  
  
 <span data-ttu-id="acab9-122">Jeśli przepływ pracy zostanie wywołane, następujące dane wyjściowe są zapisywane do okna konsoli.</span><span class="sxs-lookup"><span data-stu-id="acab9-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  <span data-ttu-id="acab9-123">Chociaż nie jest wyświetlany w danych wyjściowych poprzedniej, każdy wiersz tekstu w oknie konsoli jest wyświetlane w kolorze wskazane.</span><span class="sxs-lookup"><span data-stu-id="acab9-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="acab9-124">Właściwości wykonania przepływu pracy mogą być używane przez autorów niestandardowe działanie oraz zapewniają także przy użyciu mechanizmu zarządzania uchwyt działań takich jak <xref:System.ServiceModel.Activities.CorrelationScope> i <xref:System.Activities.Statements.TransactionScope> działań.</span><span class="sxs-lookup"><span data-stu-id="acab9-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="acab9-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="acab9-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
