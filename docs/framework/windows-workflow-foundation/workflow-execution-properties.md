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
# <a name="workflow-execution-properties"></a>Właściwości wykonania przepływu pracy
Za pomocą lokalny magazyn wątków (TLS) środowisko CLR utrzymuje kontekst wykonania dla każdego wątku. Ten kontekst wykonywania kontroluje wątku dobrze znane właściwości, takich jak tożsamość wątku otoczenia transakcji, oraz uprawnień bieżącego zestawu właściwości wątków użytkownika, takie jak o nazwie miejsc.  
  
 W odróżnieniu od programów bezpośrednio przeznaczonych dla środowiska CLR programy przepływu pracy są hierarchicznie zakresie drzewa działań, które są wykonywane w środowisku niezależny od wątku. Oznacza to, że standardowych mechanizmów TLS nie bezpośrednio można określić, jakie kontekstu znajduje się w zakresie dla elementu roboczego danego. Na przykład dwie gałęzie równoległego wykonywania mogą używać różnych transakcji, ale harmonogram może przeplot ich wykonanie w tym samym wątku środowiska CLR.  
  
 Właściwości wykonania przepływu pracy zapewniają mechanizm, aby dodać określonej właściwości kontekstu do działania środowiska. Dzięki temu działanie, aby zadeklarować właściwości, które znajdują się w zakresie dla jego poddrzewa i udostępnia również punkty zaczepienia dotyczące konfigurowania i zniszczenia TLS do prawidłowego współdziałania z obiektów CLR.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Tworzenie i używanie właściwości wykonania przepływu pracy  
 Właściwości wykonania przepływu pracy jest zwykle implementuje <xref:System.Activities.IExecutionProperty> interfejsu, chociaż może wdrożyć właściwości koncentruje się na komunikaty <xref:System.ServiceModel.Activities.ISendMessageCallback> i <xref:System.ServiceModel.Activities.IReceiveMessageCallback> zamiast tego. Aby utworzyć właściwości wykonania przepływu pracy, należy utworzyć klasę, która implementuje <xref:System.Activities.IExecutionProperty> interfejsu i zaimplementuj elementy członkowskie <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> i <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Te elementy członkowskie Podaj właściwości wykonywania z szansą sprzedaży poprawnie skonfigurować i zatrzymywania pamięci lokalnej wątku podczas każdego pulse pracy działania, który zawiera właściwości, łącznie z dowolnego działania podrzędne. W tym przykładzie `ConsoleColorProperty` jest tworzony w tym zestawy `Console.ForegroundColor`.  
  
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
  
 Autorzy aktywności można użyć tej właściwości, rejestrując je w działania wykonywania zastąpienie. W tym przykładzie `ConsoleColorScope` działania jest zdefiniowany, który rejestruje `ConsoleColorProperty` przez dodanie jej do <xref:System.Activities.NativeActivityContext.Properties%2A> kolekcji bieżącego <xref:System.Activities.NativeActivityContext>.  
  
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
  
 Uruchomienia działania treści pulse pracy <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> nosi nazwę metody, właściwości, a po zakończeniu pulse pracy <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> jest wywoływana. W tym przykładzie przepływ pracy jest tworzony, który używa <xref:System.Activities.Statements.Parallel> działanie przy użyciu trzech gałęzi. Użyj najpierw dwie gałęzie `ConsoleColorScope` działanie i trzeci gałęzi, nie ma. Wszystkie trzy gałęzie zawierać dwa <xref:System.Activities.Statements.WriteLine> działań i <xref:System.Activities.Statements.Delay> działania. Gdy <xref:System.Activities.Statements.Parallel> wykonuje działania, wykonywania działań, które są zawarte w gałęzi, w sposób przeplotem, ale ponieważ wykonuje każde działanie podrzędne przez stosowania kolorów poprawnej konsoli `ConsoleColorProperty`.  
  
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
  
 Jeśli przepływ pracy zostanie wywołane, następujące dane wyjściowe są zapisywane do okna konsoli.  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
>  Chociaż nie jest wyświetlany w danych wyjściowych poprzedniej, każdy wiersz tekstu w oknie konsoli jest wyświetlane w kolorze wskazane.  
  
 Właściwości wykonania przepływu pracy mogą być używane przez autorów niestandardowe działanie oraz zapewniają także przy użyciu mechanizmu zarządzania uchwyt działań takich jak <xref:System.ServiceModel.Activities.CorrelationScope> i <xref:System.Activities.Statements.TransactionScope> działań.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
