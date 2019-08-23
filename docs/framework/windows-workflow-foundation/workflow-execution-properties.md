---
title: Właściwości wykonania przepływu pracy
ms.date: 03/30/2017
ms.assetid: a50e088e-3a45-4267-bd51-1a3e6c2d246d
ms.openlocfilehash: 61bf53d9cab3ddefae3709958bd1e445fb4e69dd
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913609"
---
# <a name="workflow-execution-properties"></a>Właściwości wykonania przepływu pracy
Za pomocą lokalnego magazynu wątków środowisko CLR utrzymuje kontekst wykonywania dla każdego wątku. Ten kontekst wykonywania reguluje dobrze znane właściwości wątku, takie jak tożsamość wątku, otoczenia transakcji i bieżący zestaw uprawnień, oprócz właściwości wątku zdefiniowanego przez użytkownika, takich jak nazwane gniazda.  
  
 W przeciwieństwie do programów bezpośrednio ukierunkowanych na środowisko CLR, programy Workflow są drzewami działań, które są wykonywane w środowisku niezależny od wątku. Oznacza to, że standardowe mechanizmy TLS nie mogą być bezpośrednio używane do określenia kontekstu, który znajduje się w zakresie dla danego elementu pracy. Na przykład dwie równoległe gałęzie wykonywania mogą korzystać z różnych transakcji, ale harmonogram może pozostawać w tym samym wątku CLR.  
  
 Właściwości wykonywania przepływu pracy zapewniają mechanizm dodawania właściwości specyficznych dla kontekstu do środowiska działania. Dzięki temu działanie może zadeklarować, które właściwości znajdują się w zakresie dla jego poddrzewa, a także podpunkty zaczepienia umożliwiające skonfigurowanie i przebicie protokołu TLS w celu prawidłowego współdziałania z obiektami CLR.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Tworzenie i używanie właściwości wykonywania przepływu pracy  
 Właściwości wykonywania przepływu pracy zwykle implementują interfejs, ale właściwości, które koncentrują <xref:System.Activities.IExecutionProperty> się <xref:System.ServiceModel.Activities.IReceiveMessageCallback> na wiadomościach mogą implementować <xref:System.ServiceModel.Activities.ISendMessageCallback> i zamiast tego. Aby utworzyć właściwość wykonywania przepływu pracy, Utwórz klasę implementującą <xref:System.Activities.IExecutionProperty> interfejs i implementującą elementy członkowskie <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> i <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>. Ci członkowie udostępniają Właściwość wykonywania z możliwością poprawnego skonfigurowania i oderwania lokalnego magazynu wątków podczas każdego impulsu pracy działania, które zawiera właściwość, w tym wszystkich działań podrzędnych. W tym przykładzie `ConsoleColorProperty` tworzony jest `Console.ForegroundColor`zestaw, który ustawia.  
  
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
  
 Autorzy działań mogą używać tej właściwości, rejestrując ją w przesłonięciu wykonywania działania. W tym przykładzie `ConsoleColorScope` zdefiniowano działanie, które `ConsoleColorProperty` rejestruje <xref:System.Activities.NativeActivityContext.Properties%2A> przez dodanie go do kolekcji bieżącej <xref:System.Activities.NativeActivityContext>.  
  
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
  
 Gdy treść działania zaczyna przepływ pracy, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> wywoływana jest metoda właściwości, a po zakończeniu <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> impulsu pracy jest wywoływana. W tym przykładzie tworzony jest przepływ pracy, który używa <xref:System.Activities.Statements.Parallel> działania z trzema gałęziami. Pierwsze dwie gałęzie używają `ConsoleColorScope` działania, a trzecia gałąź nie jest. Wszystkie trzy gałęzie zawierają <xref:System.Activities.Statements.WriteLine> dwa działania <xref:System.Activities.Statements.Delay> i działanie. Gdy działanie jest wykonywane, działania, które są zawarte w gałęziach, są wykonywane w sposób przeplotowy, ale gdy każde działanie podrzędne wykonuje prawidłowy kolor konsoli jest stosowane `ConsoleColorProperty`przez. <xref:System.Activities.Statements.Parallel>  
  
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
  
 Po wywołaniu przepływu pracy następujące dane wyjściowe są zapisywane w oknie konsoli.  
  
```  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> Chociaż nie jest on wyświetlany w poprzednich danych wyjściowych, każdy wiersz tekstu w oknie konsoli jest wyświetlany w określonym kolorze.  
  
 Właściwości wykonywania przepływu pracy mogą być używane przez niestandardowych autorów działań i udostępniają również mechanizm do obsługi zarządzania działaniami, takimi jak <xref:System.ServiceModel.Activities.CorrelationScope> działania <xref:System.Activities.Statements.TransactionScope> i.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
