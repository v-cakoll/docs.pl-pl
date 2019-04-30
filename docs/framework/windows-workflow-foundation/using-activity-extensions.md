---
title: Używanie rozszerzeń działania
ms.date: 03/30/2017
ms.assetid: 500eb96a-c009-4247-b6b5-b36faffdf715
ms.openlocfilehash: e524f7e7127eb215be85b0c317474eee70830c2b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61669514"
---
# <a name="using-activity-extensions"></a>Używanie rozszerzeń działania
Działania mogą wchodzić w interakcje z rozszerzeniami aplikacji przepływu pracy, które zezwala na hostów w celu zapewnienia dodatkowych funkcji, która nie jest jawnie modelowane w przepływie pracy.  W tym temacie opisano sposób tworzenia i liczbę przypadków, gdy działanie wykonuje za pomocą rozszerzenia.

### <a name="to-use-an-activity-extension-to-count-executions"></a>Liczba wykonań przy użyciu rozszerzenia działania

1. Open Visual Studio 2010. Wybierz **nowe**, **projektu**. W obszarze **Visual C#** węzeł **przepływu pracy**.  Wybierz **Aplikacja konsoli przepływu pracy** z listy szablonów. Nadaj projektowi nazwę `Extensions`. Kliknij przycisk **OK** do tworzenia projektu.

2. Dodaj `using` instrukcja w pliku Program.cs **System.Collections.Generic** przestrzeni nazw.

    ```
    using System.Collections.Generic;
    ```

3. W pliku Program.cs, Utwórz nową klasę o nazwie **ExecutionCountExtension**. Poniższy kod tworzy rozszerzenia przepływu pracy, który śledzi identyfikatorów wystąpień podczas jego **zarejestrować** metoda jest wywoływana.

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

4. Utwórz działanie, które zużywa **ExecutionCountExtension**. Poniższy kod definiuje działanie, które pobiera **ExecutionCountExtension** obiektu na podstawie czasu wykonywania i wywołuje jego **zarejestrować** metody, gdy działanie wykonuje.

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

5. Implementowanie działania w **Main** metoda części pliku program.cs. Poniższy kod zawiera metody do generowania dwóch różnych przepływów pracy, wykonaj kilka razy każdego przepływu pracy i wyświetlić dane wynikowe, który jest zawarty w rozszerzeniu.

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
