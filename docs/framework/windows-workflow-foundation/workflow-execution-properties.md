---
title: Właściwości wykonania przepływu pracy
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 0f958e7e112bfddc2740c2605d446493f2d49010
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182662"
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="3a00c-102">Właściwości wykonania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3a00c-102">Workflow Execution Properties</span></span>
<span data-ttu-id="3a00c-103">Za pośrednictwem magazynu lokalnego wątku (TLS), CLR utrzymuje kontekst wykonywania dla każdego wątku.</span><span class="sxs-lookup"><span data-stu-id="3a00c-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="3a00c-104">Ten kontekst wykonywania reguluje dobrze znane właściwości wątku, takie jak tożsamość wątku, transakcja otoczenia i bieżący zestaw uprawnień oprócz właściwości wątku zdefiniowanych przez użytkownika, takich jak nazwane gniazda.</span><span class="sxs-lookup"><span data-stu-id="3a00c-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="3a00c-105">W przeciwieństwie do programów bezpośrednio docelowych CLR, programy przepływu pracy są hierarchicznie zakres drzew działań, które są wykonywane w środowisku niezależnego od wątku.</span><span class="sxs-lookup"><span data-stu-id="3a00c-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="3a00c-106">Oznacza to, że standardowe mechanizmy TLS nie mogą być bezpośrednio używane do określenia, jaki kontekst jest w zakresie dla danego elementu pracy.</span><span class="sxs-lookup"><span data-stu-id="3a00c-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="3a00c-107">Na przykład dwie równoległe gałęzie wykonywania mogą używać różnych transakcji, ale harmonogram może przeplatać ich wykonanie w tym samym wątku CLR.</span><span class="sxs-lookup"><span data-stu-id="3a00c-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="3a00c-108">Właściwości wykonywania przepływu pracy zapewniają mechanizm dodawania właściwości kontekstu do środowiska działania.</span><span class="sxs-lookup"><span data-stu-id="3a00c-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="3a00c-109">Dzięki temu działanie do deklarowania, które właściwości są w zakresie jego poddrzewa, a także zapewnia haki do konfigurowania i burzenia TLS prawidłowo współdziałać z obiektami CLR.</span><span class="sxs-lookup"><span data-stu-id="3a00c-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="3a00c-110">Tworzenie i używanie właściwości wykonywania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="3a00c-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="3a00c-111">Właściwości wykonywania przepływu pracy <xref:System.Activities.IExecutionProperty> zwykle implementują interfejs, chociaż właściwości <xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback> koncentruje się na wiadomości może implementować i zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="3a00c-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="3a00c-112">Aby utworzyć właściwość wykonywania przepływu pracy, należy <xref:System.Activities.IExecutionProperty> utworzyć klasę, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>która implementuje interfejs i zaimplementować elementy członkowskie oraz program .</span><span class="sxs-lookup"><span data-stu-id="3a00c-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="3a00c-113">Te elementy członkowskie zapewniają właściwość wykonywania z możliwością prawidłowego konfigurowania i burzenia wątku magazynu lokalnego podczas każdego impulsu pracy działania, który zawiera właściwość, w tym wszelkie działania podrzędne.</span><span class="sxs-lookup"><span data-stu-id="3a00c-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="3a00c-114">W tym przykładzie `ConsoleColorProperty` tworzony jest `Console.ForegroundColor`plik, który ustawia plik .</span><span class="sxs-lookup"><span data-stu-id="3a00c-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
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
  
 <span data-ttu-id="3a00c-115">Autorzy działań mogą używać tej właściwości, rejestrując ją w zastępowaniu wykonania działania.</span><span class="sxs-lookup"><span data-stu-id="3a00c-115">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="3a00c-116">W tym `ConsoleColorScope` przykładzie zdefiniowano działanie, `ConsoleColorProperty` które rejestruje, <xref:System.Activities.NativeActivityContext.Properties%2A> dodając go <xref:System.Activities.NativeActivityContext>do kolekcji bieżącego .</span><span class="sxs-lookup"><span data-stu-id="3a00c-116">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="3a00c-117">Gdy treść działania rozpoczyna puls pracy, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> wywoływana jest metoda właściwości, a po zakończeniu pulsu <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> pracy jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="3a00c-117">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="3a00c-118">W tym przykładzie tworzony jest przepływ <xref:System.Activities.Statements.Parallel> pracy, który używa działania z trzema gałęziami.</span><span class="sxs-lookup"><span data-stu-id="3a00c-118">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="3a00c-119">Pierwsze dwie gałęzie `ConsoleColorScope` używają działania, a trzecia gałąź nie.</span><span class="sxs-lookup"><span data-stu-id="3a00c-119">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="3a00c-120">Wszystkie trzy gałęzie <xref:System.Activities.Statements.WriteLine> zawierają dwa <xref:System.Activities.Statements.Delay> działania i działanie.</span><span class="sxs-lookup"><span data-stu-id="3a00c-120">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="3a00c-121">Podczas <xref:System.Activities.Statements.Parallel> wykonywania działania działania zawarte w gałęziach są wykonywane w sposób przeplatany, ale jak każde działanie podrzędne wykonuje poprawny `ConsoleColorProperty`kolor konsoli jest stosowany przez program .</span><span class="sxs-lookup"><span data-stu-id="3a00c-121">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="3a00c-122">Po wywołaniu przepływu pracy następujące dane wyjściowe są zapisywane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="3a00c-122">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> <span data-ttu-id="3a00c-123">Chociaż nie jest wyświetlany w poprzednim wyjściu, każdy wiersz tekstu w oknie konsoli jest wyświetlany we wskazanym kolorze.</span><span class="sxs-lookup"><span data-stu-id="3a00c-123">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="3a00c-124">Właściwości wykonywania przepływu pracy mogą być używane przez autorów działań niestandardowych, a <xref:System.ServiceModel.Activities.CorrelationScope> także <xref:System.Activities.Statements.TransactionScope> zapewniają mechanizm obsługi zarządzania dla działań, takich jak i działania.</span><span class="sxs-lookup"><span data-stu-id="3a00c-124">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3a00c-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a00c-125">See also</span></span>

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
