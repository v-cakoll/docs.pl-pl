---
title: "Właściwości wykonania przepływu pracy"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
caps.latest.revision: "9"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: d119d721964df7ea1c007eadd17a8db54f4f8cd9
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="workflow-execution-properties"></a><span data-ttu-id="1eda6-102">Właściwości wykonania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1eda6-102">Workflow Execution Properties</span></span>
<span data-ttu-id="1eda6-103">Za pomocą lokalny magazyn wątków (TLS) środowisko CLR przechowuje kontekstu wykonywania dla każdego wątku.</span><span class="sxs-lookup"><span data-stu-id="1eda6-103">Through thread local storage (TLS), the CLR maintains an execution context for each thread.</span></span> <span data-ttu-id="1eda6-104">Ten kontekst wykonywania kontroluje wątku dobrze znane właściwości, takie jak tożsamości wątku, transakcja otoczenia, oraz uprawnienia bieżącego zestawu właściwości wątku zdefiniowane przez użytkownika, takie jak o nazwie gniazda.</span><span class="sxs-lookup"><span data-stu-id="1eda6-104">This execution context governs well-known thread properties such as the thread identity, the ambient transaction, and the current permission set in addition to user-defined thread properties like named slots.</span></span>  
  
 <span data-ttu-id="1eda6-105">W odróżnieniu od programów bezpośrednio przeznaczonych dla środowiska CLR programy przepływu pracy są drzew hierarchicznie zakresie działań, które są wykonywane w środowisku niezależny od wątku.</span><span class="sxs-lookup"><span data-stu-id="1eda6-105">Unlike programs directly targeting the CLR, workflow programs are hierarchically scoped trees of activities that execute in a thread-agnostic environment.</span></span> <span data-ttu-id="1eda6-106">Oznacza to, że stosowanie standardowych mechanizmów TLS bezpośrednio nie można użyć do określenia, jakie kontekstu znajduje się w zakresie dla elementu roboczego danego.</span><span class="sxs-lookup"><span data-stu-id="1eda6-106">This implies that the standard TLS mechanisms cannot directly be used to determine what context is in scope for a given work item.</span></span> <span data-ttu-id="1eda6-107">Na przykład mogą korzystać z dwóch równoległych gałęziach wykonywania różnych transakcji, ale planista może interleave ich wykonania na tym samym wątku CLR.</span><span class="sxs-lookup"><span data-stu-id="1eda6-107">For example, two parallel branches of execution might use different transactions, yet the scheduler might interleave their execution on the same CLR thread.</span></span>  
  
 <span data-ttu-id="1eda6-108">Właściwości wykonania przepływu pracy udostępniają mechanizm do dodania do środowiska działania właściwości specyficzne dla kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1eda6-108">Workflow execution properties provide a mechanism to add context specific properties to an activity’s environment.</span></span> <span data-ttu-id="1eda6-109">Dzięki temu działanie, aby zadeklarować, właściwości, które znajdują się w zakresie dla jego poddrzewa i udostępnia punkty zaczepienia dotyczące konfigurowania i przerwanie dół TLS prawidłowo współdziałanie z obiektami środowiska CLR.</span><span class="sxs-lookup"><span data-stu-id="1eda6-109">This allows an activity to declare which properties are in scope for its sub-tree and also provides hooks for setting up and tearing down TLS to properly interoperate with CLR objects.</span></span>  
  
## <a name="creating-and-using-workflow-execution-properties"></a><span data-ttu-id="1eda6-110">Tworzenie i korzystanie z właściwości wykonania przepływu pracy</span><span class="sxs-lookup"><span data-stu-id="1eda6-110">Creating and Using Workflow Execution Properties</span></span>  
 <span data-ttu-id="1eda6-111">Właściwości wykonania przepływu pracy jest zwykle zaimplementować <xref:System.Activities.IExecutionProperty> interfejsu, chociaż może wdrożyć właściwości koncentruje się na wiadomości <xref:System.ServiceModel.Activities.ISendMessageCallback> i <xref:System.ServiceModel.Activities.IReceiveMessageCallback> zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="1eda6-111">Workflow execution properties usually implement the <xref:System.Activities.IExecutionProperty> interface, though properties focused on messaging may implement <xref:System.ServiceModel.Activities.ISendMessageCallback> and <xref:System.ServiceModel.Activities.IReceiveMessageCallback> instead.</span></span> <span data-ttu-id="1eda6-112">Aby utworzyć właściwość wykonywania przepływu pracy, należy utworzyć klasę implementującą <xref:System.Activities.IExecutionProperty> interfejsu i implementować członków <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> i <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span><span class="sxs-lookup"><span data-stu-id="1eda6-112">To create a workflow execution property, create a class that implements the <xref:System.Activities.IExecutionProperty> interface and implement the members <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> and <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>.</span></span> <span data-ttu-id="1eda6-113">Te elementy członkowskie Podaj właściwość wykonywania możliwość poprawnie skonfigurować i zniszcz lokalny magazyn wątków podczas każdego pulse pracy działania zawierającego właściwości, łącznie z żadnych działań podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="1eda6-113">These members provide the execution property with an opportunity to properly set up and tear down the thread local storage during each pulse of work of the activity that contains the property, including any child activities.</span></span> <span data-ttu-id="1eda6-114">W tym przykładzie `ConsoleColorProperty` jest tworzony w tym zestawy `Console.ForegroundColor`.</span><span class="sxs-lookup"><span data-stu-id="1eda6-114">In this example, a `ConsoleColorProperty` is created that sets the `Console.ForegroundColor`.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1eda6-115">Poniższy przykładowy kod w tym temacie jest oparta na [właściwości wykonania](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md) próbki.</span><span class="sxs-lookup"><span data-stu-id="1eda6-115">The following example code in this topic is based on the [Execution Properties](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md) sample.</span></span>  
  
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
  
 <span data-ttu-id="1eda6-116">Działanie autorzy mogą używać tej właściwości w zarejestrowani zastąpienie wykonania działania.</span><span class="sxs-lookup"><span data-stu-id="1eda6-116">Activity authors can use this property by registering it in the activity’s execute override.</span></span> <span data-ttu-id="1eda6-117">W tym przykładzie `ConsoleColorScope` zdefiniowano działania, który rejestruje `ConsoleColorProperty` przez dodanie go do <xref:System.Activities.NativeActivityContext.Properties%2A> kolekcji bieżącego <xref:System.Activities.NativeActivityContext>.</span><span class="sxs-lookup"><span data-stu-id="1eda6-117">In this example, a `ConsoleColorScope` activity is defined that registers the `ConsoleColorProperty` by adding it to the <xref:System.Activities.NativeActivityContext.Properties%2A> collection of the current <xref:System.Activities.NativeActivityContext>.</span></span>  
  
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
  
 <span data-ttu-id="1eda6-118">Podczas działania treści uruchamiania pulse pracy, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> wywoływana jest metoda właściwości, a po zakończeniu pulse pracy <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="1eda6-118">When the activity’s body starts a pulse of work, the <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> method of the property is called, and when the pulse of work is complete, the <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> is called.</span></span> <span data-ttu-id="1eda6-119">W tym przykładzie przepływ pracy jest tworzony, który używa <xref:System.Activities.Statements.Parallel> działania o trzy gałęzie.</span><span class="sxs-lookup"><span data-stu-id="1eda6-119">In this example, a workflow is created that uses a <xref:System.Activities.Statements.Parallel> activity with three branches.</span></span> <span data-ttu-id="1eda6-120">Użyć dwóch pierwszych gałęzie `ConsoleColorScope` działania i trzeci gałęzi nie.</span><span class="sxs-lookup"><span data-stu-id="1eda6-120">The first two branches use the `ConsoleColorScope` activity and the third branch does not.</span></span> <span data-ttu-id="1eda6-121">Wszystkie trzy gałęzie zawierać dwa <xref:System.Activities.Statements.WriteLine> działań i <xref:System.Activities.Statements.Delay> działania.</span><span class="sxs-lookup"><span data-stu-id="1eda6-121">All three branches contain two <xref:System.Activities.Statements.WriteLine> activities and a <xref:System.Activities.Statements.Delay> activity.</span></span> <span data-ttu-id="1eda6-122">Gdy <xref:System.Activities.Statements.Parallel> wykonuje działania, wykonywania działań, które są zawarte w gałęzi w sposób przeplotem, ale ponieważ wykonuje każde działanie podrzędne kolor poprawne konsoli jest stosowana przez `ConsoleColorProperty`.</span><span class="sxs-lookup"><span data-stu-id="1eda6-122">When the <xref:System.Activities.Statements.Parallel> activity executes, the activities that are contained in the branches execute in an interleaved manner, but as each child activity executes the correct console color is applied by the `ConsoleColorProperty`.</span></span>  
  
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
  
 <span data-ttu-id="1eda6-123">Jeśli przepływ pracy zostanie wywołane, następujące dane wyjściowe są zapisywane w oknie konsoli.</span><span class="sxs-lookup"><span data-stu-id="1eda6-123">When the workflow is invoked, the following output is written to the console window.</span></span>  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  <span data-ttu-id="1eda6-124">Chociaż nie jest wyświetlany w danych wyjściowych poprzedniej, każdy wiersz tekstu w oknie konsoli jest wyświetlane w kolorze wskazane.</span><span class="sxs-lookup"><span data-stu-id="1eda6-124">Although it is not shown in the previous output, each line of text in the console window is displayed in the indicated color.</span></span>  
  
 <span data-ttu-id="1eda6-125">Właściwości wykonania przepływu pracy mogą być używane przez autora działania niestandardowego, a także zapewniają mechanizm zarządzania dojścia do działań takich jak <xref:System.ServiceModel.Activities.CorrelationScope> i <xref:System.Activities.Statements.TransactionScope> działań.</span><span class="sxs-lookup"><span data-stu-id="1eda6-125">Workflow execution properties can be used by custom activity authors, and they also provide the mechanism for handle management for activities such as the <xref:System.ServiceModel.Activities.CorrelationScope> and <xref:System.Activities.Statements.TransactionScope> activities.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1eda6-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1eda6-126">See Also</span></span>  
 <xref:System.Activities.IExecutionProperty>  
 <xref:System.Activities.IPropertyRegistrationCallback>  
 <xref:System.Activities.RegistrationContext>
