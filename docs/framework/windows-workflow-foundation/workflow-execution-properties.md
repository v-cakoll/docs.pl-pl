---
title: Właściwości wykonania przepływu pracy
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 87775ba6efb9ec26ed2445e1f9d0944c379ba04f
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988598"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="c4de4-102">Właściwości wykonania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c4de4-102">Workflow Execution Properties</span></span>
<span data-ttu-id="c4de4-103">Za pomocą lokalnego magazynu wątków środowisko CLR utrzymuje kontekst wykonywania dla każdego wątku.</span><span class="sxs-lookup"><span data-stu-id="c4de4-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="c4de4-104">Ten kontekst wykonywania reguluje dobrze znane właściwości wątku, takie jak tożsamość wątku, otoczenia transakcji i bieżący zestaw uprawnień, oprócz właściwości wątku zdefiniowanego przez użytkownika, takich jak nazwane gniazda.</span><span class="sxs-lookup"><span data-stu-id="c4de4-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="c4de4-105">W przeciwieństwie do programów bezpośrednio ukierunkowanych na środowisko CLR, programy Workflow są drzewami działań, które są wykonywane w środowisku niezależny od wątku.</span><span class="sxs-lookup"><span data-stu-id="c4de4-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="c4de4-106">Oznacza to, że standardowe mechanizmy TLS nie mogą być bezpośrednio używane do określenia kontekstu, który znajduje się w zakresie dla danego elementu pracy.</span><span class="sxs-lookup"><span data-stu-id="c4de4-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="c4de4-107">Na przykład dwie równoległe gałęzie wykonywania mogą korzystać z różnych transakcji, ale harmonogram może pozostawać w tym samym wątku CLR.</span><span class="sxs-lookup"><span data-stu-id="c4de4-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="c4de4-108">Właściwości wykonywania przepływu pracy zapewniają mechanizm dodawania właściwości specyficznych dla kontekstu do środowiska działania.</span><span class="sxs-lookup"><span data-stu-id="c4de4-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="c4de4-109">Dzięki temu działanie może zadeklarować, które właściwości znajdują się w zakresie dla jego poddrzewa, a także podpunkty zaczepienia umożliwiające skonfigurowanie i przebicie protokołu TLS w celu prawidłowego współdziałania z obiektami CLR.</span><span class="sxs-lookup"><span data-stu-id="c4de4-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="c4de4-110">Tworzenie i używanie właściwości wykonywania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="c4de4-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="c4de4-111">Właściwości wykonywania przepływu pracy zwykle implementują interfejs, ale właściwości, które koncentrują <xref:System.Activities.IExecutionProperty> się <xref:System.ServiceModel.Activities.IReceiveMessageCallback> na wiadomościach mogą implementować <xref:System.ServiceModel.Activities.ISendMessageCallback> i zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="c4de4-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="c4de4-112">Aby utworzyć właściwość wykonywania przepływu pracy, Utwórz klasę implementującą <xref:System.Activities.IExecutionProperty> interfejs i implementującą elementy członkowskie <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> i <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="c4de4-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="c4de4-113">Ci członkowie udostępniają Właściwość wykonywania z możliwością poprawnego skonfigurowania i oderwania lokalnego magazynu wątków podczas każdego impulsu pracy działania, które zawiera właściwość, w tym wszystkich działań podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="c4de4-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="c4de4-114">W tym przykładzie `ConsoleColorProperty` tworzony jest `Console.ForegroundColor`zestaw, który ustawia.</span><span class="sxs-lookup"><span data-stu-id="c4de4-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
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
  
 <span data-ttu-id="c4de4-115">Autorzy działań mogą używać tej właściwości, rejestrując ją w przesłonięciu wykonywania działania.</span><span class="sxs-lookup"><span data-stu-id="c4de4-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="c4de4-116">W tym przykładzie `ConsoleColorScope` zdefiniowano działanie, które `ConsoleColorProperty` rejestruje <xref:System.Activities.NativeActivityContext.Properties%2A> przez dodanie go do kolekcji bieżącej <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="c4de4-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="c4de4-117">Gdy treść działania zaczyna przepływ pracy, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> wywoływana jest metoda właściwości, a po zakończeniu <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> impulsu pracy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="c4de4-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="c4de4-118">W tym przykładzie tworzony jest przepływ pracy, który używa <xref:System.Activities.Statements.Parallel> działania z trzema gałęziami.</span><span class="sxs-lookup"><span data-stu-id="c4de4-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="c4de4-119">Pierwsze dwie gałęzie używają `ConsoleColorScope` działania, a trzecia gałąź nie jest.</span><span class="sxs-lookup"><span data-stu-id="c4de4-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="c4de4-120">Wszystkie trzy gałęzie zawierają <xref:System.Activities.Statements.WriteLine> dwa działania <xref:System.Activities.Statements.Delay> i działanie.</span><span class="sxs-lookup"><span data-stu-id="c4de4-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="c4de4-121">Gdy działanie jest wykonywane, działania, które są zawarte w gałęziach, są wykonywane w sposób przeplotowy, ale gdy każde działanie podrzędne wykonuje prawidłowy kolor konsoli jest stosowane `ConsoleColorProperty`przez. <xref:System.Activities.Statements.Parallel></span><span class="sxs-lookup"><span data-stu-id="c4de4-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="c4de4-122">Po wywołaniu przepływu pracy następujące dane wyjściowe są zapisywane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="c4de4-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> <span data-ttu-id="c4de4-123">Chociaż nie jest on wyświetlany w poprzednich danych wyjściowych, każdy wiersz tekstu w oknie konsoli jest wyświetlany w określonym kolorze.</span><span class="sxs-lookup"><span data-stu-id="c4de4-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="c4de4-124">Właściwości wykonywania przepływu pracy mogą być używane przez niestandardowych autorów działań i udostępniają również mechanizm do obsługi zarządzania działaniami, takimi jak <xref:System.ServiceModel.Activities.CorrelationScope> działania <xref:System.Activities.Statements.TransactionScope> i.</span><span class="sxs-lookup"><span data-stu-id="c4de4-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c4de4-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="c4de4-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
