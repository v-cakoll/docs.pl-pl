---
title: Przy użyciu rozszerzeń działania
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 32c465ae42a1f0238fab7bba5ea795486db3b562
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33517228"
---
# <a name="using-activity-extensions"></a><span data-ttu-id="02916-102">Przy użyciu rozszerzeń działania</span><span class="sxs-lookup"><span data-stu-id="02916-102">Using Activity Extensions</span></span>
<span data-ttu-id="02916-103">Działania mogą współdziałać z rozszerzeniami aplikacji przepływu pracy zezwalających na hoście oferowanie dodatkowych funkcji, która nie jest jawnie modelowane w przepływie pracy.</span><span class="sxs-lookup"><span data-stu-id="02916-103">Activities can interact with workflow application extensions that allow the host to provide additional functionality that is not explicitly modeled in the workflow.</span></span>  <span data-ttu-id="02916-104">W tym temacie opisano sposób tworzenia i umożliwia rozszerzenie liczbę razy, który wykonuje działania.</span><span class="sxs-lookup"><span data-stu-id="02916-104">This topic describes how to create and use an extension to count the number of times the activity executes.</span></span>  
  
### <a name="to-use-an-activity-extension-to-count-executions"></a><span data-ttu-id="02916-105">Na potrzeby zliczania wykonaniami rozszerzenie działania</span><span class="sxs-lookup"><span data-stu-id="02916-105">To use an activity extension to count executions</span></span>  
  
1.  <span data-ttu-id="02916-106">Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span><span class="sxs-lookup"><span data-stu-id="02916-106">Open [!INCLUDE[vs2010](../../../includes/vs2010-md.md)].</span></span> <span data-ttu-id="02916-107">Wybierz **nowe**, **projektu**.</span><span class="sxs-lookup"><span data-stu-id="02916-107">Select **New**, **Project**.</span></span> <span data-ttu-id="02916-108">W obszarze **Visual C#** węzła, wybierz opcję **przepływu pracy**.</span><span class="sxs-lookup"><span data-stu-id="02916-108">Under the **Visual C#** node, select **Workflow**.</span></span>  <span data-ttu-id="02916-109">Wybierz **Aplikacja konsoli przepływu pracy** z listy szablonów.</span><span class="sxs-lookup"><span data-stu-id="02916-109">Select **Workflow Console Application** from the list of templates.</span></span> <span data-ttu-id="02916-110">Nazwij projekt `Extensions`.</span><span class="sxs-lookup"><span data-stu-id="02916-110">Name the project `Extensions`.</span></span> <span data-ttu-id="02916-111">Kliknij przycisk **OK** Aby utworzyć projekt.</span><span class="sxs-lookup"><span data-stu-id="02916-111">Click **OK** to create the project.</span></span>  
  
2.  <span data-ttu-id="02916-112">Dodaj `using` instrukcji w pliku Program.cs **system.Collections.Generic —** przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="02916-112">Add a `using` statement in the Program.cs file for the **System.Collections.Generic** namespace.</span></span>  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
3.  <span data-ttu-id="02916-113">W pliku Program.cs, Utwórz nową klasę o nazwie **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="02916-113">In the Program.cs file, create a new class named **ExecutionCountExtension**.</span></span> <span data-ttu-id="02916-114">Poniższy kod tworzy rozszerzenia przepływu pracy, śledzący identyfikatorów wystąpienia podczas jego **zarejestrować** metoda jest wywoływana.</span><span class="sxs-lookup"><span data-stu-id="02916-114">The following code creates a workflow extension that tracks instance IDs when its **Register** method is called.</span></span>  
  
    ```  
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
  
4.  <span data-ttu-id="02916-115">Utwórz działanie, który wykorzystuje **ExecutionCountExtension**.</span><span class="sxs-lookup"><span data-stu-id="02916-115">Create an activity that consumes the **ExecutionCountExtension**.</span></span> <span data-ttu-id="02916-116">Poniższy kod definiuje to działanie, które pobiera **ExecutionCountExtension** obiektu wynikające ze środowiska uruchomieniowego i wywołania jego **zarejestrować** metody, gdy działanie wykonuje.</span><span class="sxs-lookup"><span data-stu-id="02916-116">The following code defines an activity that retrieves the **ExecutionCountExtension** object from the runtime and calls its **Register** method when the activity executes.</span></span>  
  
    ```  
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
  
5.  <span data-ttu-id="02916-117">Implementowanie działania w **Main** metody pliku program.cs.</span><span class="sxs-lookup"><span data-stu-id="02916-117">Implement the activity in the **Main** method of the program.cs file.</span></span> <span data-ttu-id="02916-118">Poniższy kod zawiera metody do wygenerowania dwóch różnych przepływów pracy, wykonać kilka razy każdego przepływu pracy i wyświetlić wynikowe dane znajdujące się w rozszerzeniu.</span><span class="sxs-lookup"><span data-stu-id="02916-118">The following code contains methods to generate two different workflows, execute each workflow several times, and display the resulting data that is contained in the extension.</span></span>  
  
    ```  
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
