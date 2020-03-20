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
# <a name="workflow-execution-properties"></a>Właściwości wykonania przepływu pracy
Za pośrednictwem magazynu lokalnego wątku (TLS), CLR utrzymuje kontekst wykonywania dla każdego wątku. Ten kontekst wykonywania reguluje dobrze znane właściwości wątku, takie jak tożsamość wątku, transakcja otoczenia i bieżący zestaw uprawnień oprócz właściwości wątku zdefiniowanych przez użytkownika, takich jak nazwane gniazda.  
  
 W przeciwieństwie do programów bezpośrednio docelowych CLR, programy przepływu pracy są hierarchicznie zakres drzew działań, które są wykonywane w środowisku niezależnego od wątku. Oznacza to, że standardowe mechanizmy TLS nie mogą być bezpośrednio używane do określenia, jaki kontekst jest w zakresie dla danego elementu pracy. Na przykład dwie równoległe gałęzie wykonywania mogą używać różnych transakcji, ale harmonogram może przeplatać ich wykonanie w tym samym wątku CLR.  
  
 Właściwości wykonywania przepływu pracy zapewniają mechanizm dodawania właściwości kontekstu do środowiska działania. Dzięki temu działanie do deklarowania, które właściwości są w zakresie jego poddrzewa, a także zapewnia haki do konfigurowania i burzenia TLS prawidłowo współdziałać z obiektami CLR.  
  
## <a name="creating-and-using-workflow-execution-properties"></a>Tworzenie i używanie właściwości wykonywania przepływu pracy  
 Właściwości wykonywania przepływu pracy <xref:System.Activities.IExecutionProperty> zwykle implementują interfejs, chociaż właściwości <xref:System.ServiceModel.Activities.ISendMessageCallback> <xref:System.ServiceModel.Activities.IReceiveMessageCallback> koncentruje się na wiadomości może implementować i zamiast tego. Aby utworzyć właściwość wykonywania przepływu pracy, należy <xref:System.Activities.IExecutionProperty> utworzyć klasę, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A>która implementuje interfejs i zaimplementować elementy członkowskie oraz program . Te elementy członkowskie zapewniają właściwość wykonywania z możliwością prawidłowego konfigurowania i burzenia wątku magazynu lokalnego podczas każdego impulsu pracy działania, który zawiera właściwość, w tym wszelkie działania podrzędne. W tym przykładzie `ConsoleColorProperty` tworzony jest `Console.ForegroundColor`plik, który ustawia plik .  
  
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
  
 Autorzy działań mogą używać tej właściwości, rejestrując ją w zastępowaniu wykonania działania. W tym `ConsoleColorScope` przykładzie zdefiniowano działanie, `ConsoleColorProperty` które rejestruje, <xref:System.Activities.NativeActivityContext.Properties%2A> dodając go <xref:System.Activities.NativeActivityContext>do kolekcji bieżącego .  
  
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
  
 Gdy treść działania rozpoczyna puls pracy, <xref:System.Activities.IExecutionProperty.SetupWorkflowThread%2A> wywoływana jest metoda właściwości, a po zakończeniu pulsu <xref:System.Activities.IExecutionProperty.CleanupWorkflowThread%2A> pracy jest wywoływana. W tym przykładzie tworzony jest przepływ <xref:System.Activities.Statements.Parallel> pracy, który używa działania z trzema gałęziami. Pierwsze dwie gałęzie `ConsoleColorScope` używają działania, a trzecia gałąź nie. Wszystkie trzy gałęzie <xref:System.Activities.Statements.WriteLine> zawierają dwa <xref:System.Activities.Statements.Delay> działania i działanie. Podczas <xref:System.Activities.Statements.Parallel> wykonywania działania działania zawarte w gałęziach są wykonywane w sposób przeplatany, ale jak każde działanie podrzędne wykonuje poprawny `ConsoleColorProperty`kolor konsoli jest stosowany przez program .  
  
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
  
```console  
Start blue text.  
Start red text.  
Start default text.  
End blue text.  
End red text.  
End default text.  
```  
  
> [!NOTE]
> Chociaż nie jest wyświetlany w poprzednim wyjściu, każdy wiersz tekstu w oknie konsoli jest wyświetlany we wskazanym kolorze.  
  
 Właściwości wykonywania przepływu pracy mogą być używane przez autorów działań niestandardowych, a <xref:System.ServiceModel.Activities.CorrelationScope> także <xref:System.Activities.Statements.TransactionScope> zapewniają mechanizm obsługi zarządzania dla działań, takich jak i działania.  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Activities.IExecutionProperty>
- <xref:System.Activities.IPropertyRegistrationCallback>
- <xref:System.Activities.RegistrationContext>
