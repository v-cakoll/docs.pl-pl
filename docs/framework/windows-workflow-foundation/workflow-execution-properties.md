---
title: Właściwości wykonania przepływu pracy
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 2681152ba89baa2f65d5402a8c8c9d872cadb65b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33518647"
---
# <a name="workflow-execution-properties"></a>Właściwości wykonania przepływu pracy
Za pomocą lokalny magazyn wątków (TLS) środowisko CLR przechowuje kontekstu wykonywania dla każdego wątku. Ten kontekst wykonywania kontroluje wątku dobrze znane właściwości, takie jak tożsamości wątku, transakcja otoczenia, oraz uprawnienia bieżącego zestawu właściwości wątku zdefiniowane przez użytkownika, takie jak o nazwie gniazda.  
  
 W odróżnieniu od programów bezpośrednio przeznaczonych dla środowiska CLR programy przepływu pracy są drzew hierarchicznie zakresie działań, które są wykonywane w środowisku niezależny od wątku. Oznacza to, że stosowanie standardowych mechanizmów TLS bezpośrednio nie można użyć do określenia, jakie kontekstu znajduje się w zakresie dla elementu roboczego danego. Na przykład mogą korzystać z dwóch równoległych gałęziach wykonywania różnych transakcji, ale planista może interleave ich wykonania na tym samym wątku CLR.  
  
 Właściwości wykonania przepływu pracy udostępniają mechanizm do dodania do środowiska działania właściwości specyficzne dla kontekstu. Dzięki temu działanie, aby zadeklarować, właściwości, które znajdują się w zakresie dla jego poddrzewa i udostępnia punkty zaczepienia dotyczące konfigurowania i przerwanie dół TLS prawidłowo współdziałanie z obiektami środowiska CLR.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Tworzenie i korzystanie z właściwości wykonania przepływu pracy  
 Właściwości wykonania przepływu pracy jest zwykle zaimplementować <xref:System.Activities.IExecutionProperty> interfejsu, chociaż może wdrożyć właściwości koncentruje się na wiadomości <xref:System.ServiceModel.Activities.ISendMessageCallback> i <xref:System.ServiceModel.Activities.IReceiveMessageCallback> zamiast tego. Aby utworzyć właściwość wykonywania przepływu pracy, należy utworzyć klasę implementującą <xref:System.Activities.IExecutionProperty> interfejsu i implementować członków <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> i <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Te elementy członkowskie Podaj właściwość wykonywania możliwość poprawnie skonfigurować i zniszcz lokalny magazyn wątków podczas każdego pulse pracy działania zawierającego właściwości, łącznie z żadnych działań podrzędnych. W tym przykładzie `ConsoleColorProperty` jest tworzony w tym zestawy `Console.ForegroundColor`.  
  
> [!NOTE]
>  Poniższy przykładowy kod w tym temacie jest oparta na [właściwości wykonania](../../../docs/framework/windows-workflow-foundation/samples/execution-properties.md) próbki.  
  
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
  
 Działanie autorzy mogą używać tej właściwości w zarejestrowani zastąpienie wykonania działania. W tym przykładzie `ConsoleColorScope` zdefiniowano działania, który rejestruje `ConsoleColorProperty` przez dodanie go do <xref:System.Activities.NativeActivityContext.Properties%2A> kolekcji bieżącego <xref:System.Activities.NativeActivityContext>.  
  
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
  
 Podczas działania treści uruchamiania pulse pracy, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> wywoływana jest metoda właściwości, a po zakończeniu pulse pracy <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> jest wywoływana. W tym przykładzie przepływ pracy jest tworzony, który używa <xref:System.Activities.Statements.Parallel> działania o trzy gałęzie. Użyć dwóch pierwszych gałęzie `ConsoleColorScope` działania i trzeci gałęzi nie. Wszystkie trzy gałęzie zawierać dwa <xref:System.Activities.Statements.WriteLine> działań i <xref:System.Activities.Statements.Delay> działania. Gdy <xref:System.Activities.Statements.Parallel> wykonuje działania, wykonywania działań, które są zawarte w gałęzi w sposób przeplotem, ale ponieważ wykonuje każde działanie podrzędne kolor poprawne konsoli jest stosowana przez `ConsoleColorProperty`.  
  
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
  
 Jeśli przepływ pracy zostanie wywołane, następujące dane wyjściowe są zapisywane w oknie konsoli.  
  
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
  
 Właściwości wykonania przepływu pracy mogą być używane przez autora działania niestandardowego, a także zapewniają mechanizm zarządzania dojścia do działań takich jak <xref:System.ServiceModel.Activities.CorrelationScope> i <xref:System.Activities.Statements.TransactionScope> działań.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Activities.IExecutionProperty>  
 <xref:System.Activities.IPropertyRegistrationCallback>  
 <xref:System.Activities.RegistrationContext>
