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
# <a name="using-activity-extensions"></a>Używanie rozszerzeń działania
Działania mogą współdziałać z rozszerzeniami aplikacji przepływu pracy, które umożliwiają hostowi dostarczanie dodatkowych funkcji, które nie są jawnie modelowane w przepływie pracy.  W tym temacie opisano sposób tworzenia i używania rozszerzenia w celu zliczenia liczby wykonywanych działań.

### <a name="to-use-an-activity-extension-to-count-executions"></a>Aby użyć rozszerzenia działania do zliczenia wykonywania

1. Open Visual Studio 2010. Wybierz pozycję **Nowy**, **projekt**. W węźle **Wizualizacja C#**  wybierz pozycję **przepływ pracy**.  Z listy szablonów wybierz pozycję **aplikacja konsoli przepływu pracy** . Nadaj nazwę projektowi `Extensions`. Kliknij przycisk **OK** , aby utworzyć projekt.

2. Dodaj instrukcję w pliku program.cs dla przestrzeni nazw **System. Collections. Generic.** `using`

    ```csharp
    using System.Collections.Generic;
    ```

3. W pliku Program.cs Utwórz nową klasę o nazwie **ExecutionCountExtension**. Poniższy kod tworzy rozszerzenie przepływu pracy, które śledzi identyfikatory wystąpień w przypadku wywołania metody **register** .

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

4. Utwórz działanie, które wykorzystuje **ExecutionCountExtension**. Poniższy kod definiuje działanie, które pobiera obiekt **ExecutionCountExtension** z środowiska uruchomieniowego i wywołuje metodę **register** , gdy działanie jest wykonywane.

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

5. Zaimplementuj działanie w metodzie **Main** pliku program.cs. Poniższy kod zawiera metody generowania dwóch różnych przepływów pracy, wykonywania każdego przepływu pracy kilka razy i wyświetlania wyników zawartych w rozszerzeniu.

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
