---
title: Przy użyciu rozszerzeń działania
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: 32c465ae42a1f0238fab7bba5ea795486db3b562
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="using-activity-extensions"></a>Przy użyciu rozszerzeń działania
Działania mogą współdziałać z rozszerzeniami aplikacji przepływu pracy zezwalających na hoście oferowanie dodatkowych funkcji, która nie jest jawnie modelowane w przepływie pracy.  W tym temacie opisano sposób tworzenia i umożliwia rozszerzenie liczbę razy, który wykonuje działania.  
  
### <a name="to-use-an-activity-extension-to-count-executions"></a>Na potrzeby zliczania wykonaniami rozszerzenie działania  
  
1.  Otwórz [!INCLUDE[vs2010](../../../includes/vs2010-md.md)]. Wybierz **nowe**, **projektu**. W obszarze **Visual C#** węzła, wybierz opcję **przepływu pracy**.  Wybierz **Aplikacja konsoli przepływu pracy** z listy szablonów. Nazwij projekt `Extensions`. Kliknij przycisk **OK** Aby utworzyć projekt.  
  
2.  Dodaj `using` instrukcji w pliku Program.cs **system.Collections.Generic —** przestrzeni nazw.  
  
    ```  
    using System.Collections.Generic;  
    ```  
  
3.  W pliku Program.cs, Utwórz nową klasę o nazwie **ExecutionCountExtension**. Poniższy kod tworzy rozszerzenia przepływu pracy, śledzący identyfikatorów wystąpienia podczas jego **zarejestrować** metoda jest wywoływana.  
  
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
  
4.  Utwórz działanie, który wykorzystuje **ExecutionCountExtension**. Poniższy kod definiuje to działanie, które pobiera **ExecutionCountExtension** obiektu wynikające ze środowiska uruchomieniowego i wywołania jego **zarejestrować** metody, gdy działanie wykonuje.  
  
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
  
5.  Implementowanie działania w **Main** metody pliku program.cs. Poniższy kod zawiera metody do wygenerowania dwóch różnych przepływów pracy, wykonać kilka razy każdego przepływu pracy i wyświetlić wynikowe dane znajdujące się w rozszerzeniu.  
  
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
