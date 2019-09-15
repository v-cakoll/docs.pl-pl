---
title: Używanie rozszerzeń działania
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 551ce24db8c0adc8225ac94a1d05f998a26873a9
ms.sourcegitcommit: 005980b14629dfc193ff6cdc040800bc75e0a5a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/14/2019
ms.locfileid: "70988633"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="e78dc-102">Używanie rozszerzeń działania</span><span class="sxs-lookup"><span data-stu-id="e78dc-102">Using Activity Extensions</span></span>
<span data-ttu-id="e78dc-103">Działania mogą współdziałać z rozszerzeniami aplikacji przepływu pracy, które umożliwiają hostowi dostarczanie dodatkowych funkcji, które nie są jawnie modelowane w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="e78dc-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="e78dc-104">W tym temacie opisano sposób tworzenia i używania rozszerzenia w celu zliczenia liczby wykonywanych działań.</span><span class="sxs-lookup"><span data-stu-id="e78dc-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>

### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="e78dc-105">Aby użyć rozszerzenia działania do zliczenia wykonywania</span><span class="sxs-lookup"><span data-stu-id="e78dc-105">To use an activity extension to count executions</span></span>

1. <span data-ttu-id="e78dc-106">Open Visual Studio 2010.</span><span class="sxs-lookup"><span data-stu-id="e78dc-106">Open Visual Studio 2010.</span></span> <span data-ttu-id="e78dc-107">Wybierz pozycję **Nowy**, **projekt**.</span><span class="sxs-lookup"><span data-stu-id="e78dc-107">Select **New**, **Project**.</span></span> <span data-ttu-id="e78dc-108">W węźle **Wizualizacja C#**  wybierz pozycję **przepływ pracy**.</span><span class="sxs-lookup"><span data-stu-id="e78dc-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="e78dc-109">Z listy szablonów wybierz pozycję **aplikacja konsoli przepływu pracy** .</span><span class="sxs-lookup"><span data-stu-id="e78dc-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="e78dc-110">Nadaj nazwę projektowi `Extensions`.</span><span class="sxs-lookup"><span data-stu-id="e78dc-110">Name the project `Extensions`.</span></span> <span data-ttu-id="e78dc-111">Kliknij przycisk **OK** , aby utworzyć projekt.</span><span class="sxs-lookup"><span data-stu-id="e78dc-111">Click **OK** to create the project.</span></span>

2. <span data-ttu-id="e78dc-112">Dodaj instrukcję w pliku program.cs dla przestrzeni nazw **System. Collections. Generic.** `using`</span><span class="sxs-lookup"><span data-stu-id="e78dc-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>

    ```csharp
    using System.Collections.Generic;
    ```

3. <span data-ttu-id="e78dc-113">W pliku Program.cs Utwórz nową klasę o nazwie **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="e78dc-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="e78dc-114">Poniższy kod tworzy rozszerzenie przepływu pracy, które śledzi identyfikatory wystąpień w przypadku wywołania metody **register** .</span><span class="sxs-lookup"><span data-stu-id="e78dc-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>

    ```csharp
    // This extension collects a list of workflow Ids
    public class ExecutionCountExtension
    {
        IList<Guid> instances = new List<Guid>();

        public int ExecutionCount
        {
            get
            {
                return this.instances.Count;
            }
        }

        public IEnumerable<Guid> InstanceIds
        {
            get
            {
                return this.instances;
            }
        }

        public void Register(Guid activityInstanceId)
        {
            if (!this.instances.Contains<Guid>(activityInstanceId))
            {
                instances.Add(activityInstanceId);
            }
        }
    }
    ```

4. <span data-ttu-id="e78dc-115">Utwórz działanie, które wykorzystuje **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="e78dc-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="e78dc-116">Poniższy kod definiuje działanie, które pobiera obiekt **ExecutionCountExtension** z środowiska uruchomieniowego i wywołuje metodę **register** , gdy działanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="e78dc-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>

    ```csharp
    // Activity that consumes an extension provided by the host. If the extension is available
    // in the context, it will invoke (in this case, registers the Id of the executing workflow)
    public class MyActivity: CodeActivity
    {
        protected override void Execute(CodeActivityContext context)
        {
            ExecutionCountExtension ext = context.GetExtension<ExecutionCountExtension>();
            if (ext != null)
            {
                ext.Register(context.WorkflowInstanceId);
            }

        }
    }
    ```

5. <span data-ttu-id="e78dc-117">Zaimplementuj działanie w metodzie **Main** pliku program.cs.</span><span class="sxs-lookup"><span data-stu-id="e78dc-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="e78dc-118">Poniższy kod zawiera metody generowania dwóch różnych przepływów pracy, wykonywania każdego przepływu pracy kilka razy i wyświetlania wyników zawartych w rozszerzeniu.</span><span class="sxs-lookup"><span data-stu-id="e78dc-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>

    ```csharp
    class Program
    {
        // Creates a workflow that uses the activity that consumes the extension
        static Activity CreateWorkflow1()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity()
                }
            };
        }

        // Creates a workflow that uses two instances of the activity that consumes the extension
        static Activity CreateWorkflow2()
        {
            return new Sequence
            {
                Activities =
                {
                    new MyActivity(),
                    new MyActivity()
                }
            };
        }

        static void Main(string[] args)
        {
            // create the extension
            ExecutionCountExtension executionCountExt = new ExecutionCountExtension();

            // configure the first invoker and execute 3 times
            WorkflowInvoker invoker = new WorkflowInvoker(CreateWorkflow1());
            invoker.Extensions.Add(executionCountExt);
            invoker.Invoke();
            invoker.Invoke();
            invoker.Invoke();

            // configure the second invoker and execute 2 times
            WorkflowInvoker invoker2 = new WorkflowInvoker(CreateWorkflow2());
            invoker2.Extensions.Add(executionCountExt);
            invoker2.Invoke();
            invoker2.Invoke();

            // show the data in the extension
            Console.WriteLine("Executed {0} times", executionCountExt.ExecutionCount);
            executionCountExt.InstanceIds.ToList().ForEach(i => Console.WriteLine("...{0}", i));
        }
    }
    ```
