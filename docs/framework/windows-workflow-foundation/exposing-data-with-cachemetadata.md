---
title: "Udostępnianie danych z CacheMetadata"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
caps.latest.revision: "4"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 26c68c24ad525d077d26f0b7bd917a936372e0a5
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/02/2017
---
# <a name="exposing-data-with-cachemetadata"></a>Udostępnianie danych z CacheMetadata
Przed wykonaniem działania, czas wykonywania przepływu pracy uzyskuje wszystkie informacje o działaniach wymaganych w celu zachowania jego wykonywania. Te informacje podczas wykonywania pobiera środowiska uruchomieniowego przepływu pracy <xref:System.Activities.Activity.CacheMetadata%2A> metody. Domyślna implementacja tej metody zawiera środowiska wykonawczego o wszystkich publicznych argumenty, zmienne i działań podrzędnych udostępnianych przez działania w czasie wykonania; Jeśli działanie wymaga więcej informacji do środowiska wykonawczego równą (na przykład prywatne elementy Członkowskie lub działań do zaplanowania przez działanie), ta metoda może zostać zastąpiona do tego celu.  
  
## <a name="default-cachemetadata-behavior"></a>Domyślne zachowanie CacheMetadata  
 Domyślna implementacja <xref:System.Activities.NativeActivity.CacheMetadata%2A> działań, które pochodzą z <xref:System.Activities.NativeActivity> przetwarza następujących typów — metoda w następujący sposób:  
  
-   <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, lub <xref:System.Activities.InOutArgument%601> (argumentów ogólnych): argumenty są widoczne do środowiska wykonawczego jako argumenty z nazwą i wpisz nazwę ujawnionych właściwości i typ, odpowiedni kierunek i niektórych danych sprawdzania poprawności.  
  
-   <xref:System.Activities.Variable>lub jego żadnych podklasa klasy: elementy te są widoczne dla środowiska uruchomieniowego jako zmiennych publicznych.  
  
-   <xref:System.Activities.Activity>lub jego żadnych podklasa klasy: elementy te są widoczne dla środowiska uruchomieniowego jako działania podrzędnego publicznego. Domyślne zachowanie może być jawnie implementowane przez wywołanie metody <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, przekazując działania podrzędnego.  
  
-   <xref:System.Activities.ActivityDelegate>lub jego żadnych podklasa klasy: elementy te są widoczne dla środowiska uruchomieniowego pełnomocnikiem publicznego.  
  
-   <xref:System.Collections.ICollection>typu <xref:System.Activities.Variable>: wszystkie elementy w kolekcji są widoczne dla środowiska uruchomieniowego jako zmiennych publicznych.  
  
-   <xref:System.Collections.ICollection>typu <xref:System.Activities.Activity>: wszystkie elementy w kolekcji są widoczne dla środowiska uruchomieniowego jako publiczne elementy podrzędne.  
  
-   <xref:System.Collections.ICollection>typu <xref:System.Activities.ActivityDelegate>: wszystkie elementy w kolekcji są widoczne dla środowiska uruchomieniowego pełnomocnikiem publicznego.  
  
 <xref:System.Activities.Activity.CacheMetadata%2A> Działań, które pochodzą z <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, i <xref:System.Activities.AsyncCodeActivity> również działać zgodnie z powyższym, z wyjątkiem następujących różnic:  
  
-   Klasy, które pochodzą z <xref:System.Activities.Activity> nie można zaplanować działania podrzędne lub delegatów, więc takich elementów są widoczne jako importowanych elementów podrzędnych i obiektów delegowanych;  
  
-   Klasy, które pochodzą z <xref:System.Activities.CodeActivity> i <xref:System.Activities.AsyncCodeActivity> nie obsługują zmiennych, elementów podrzędnych lub delegatów, więc tylko argumenty, które mają być widoczne.  
  
## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a>Zastępowanie CacheMetadata, aby podać informacje do środowiska wykonawczego  
 Poniższy fragment kodu przedstawia sposób dodawania informacji o elementach członkowskich metadanych działania podczas wykonywania <xref:System.Activities.Activity.CacheMetadata%2A> metody. Należy pamiętać, że podstawowej metody jest wywoływana w pamięci podręcznej wszystkie publiczne dane dotyczące działania.  
  
```  
protected override void CacheMetadata(NativeActivityMetadata metadata)  
{      
    base.CacheMetadata(metadata);  
    metadata.AddImplementationChild(this._writeLine);  
    metadata.AddVariable(this._myVariable);  
    metadata.AddImplementationVariable(this._myImplementationVariable);  
  
    RuntimeArgument argument = new RuntimeArgument("MyArgument", ArgumentDirection.In, typeof(SomeType));  
    metadata.Bind(argument, this.SomeName);  
    metadata.AddArgument(argument);  
}  
```  
  
## <a name="using-cachemetadata-to-expose-implementation-children"></a>Przy użyciu CacheMetadata do udostępnienia implementacji elementów podrzędnych  
 Aby przekazać dane do działania podrzędne, które mają być zaplanowane przez działanie za pomocą zmiennych, należy dodać zmienne jako zmienne implementacji; zmienne publiczne nie może mieć wartości skonfigurowane w ten sposób. Przyczyną tego jest działania mają więcej wykonywanej jako implementacji funkcji (które mają parametry), a nie klasy hermetyzowany, (które mają właściwości). Jednak istnieją sytuacje, w których argumentów musi być jawnie ustawiona, takich jak podczas obliczania przy użyciu <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, ponieważ zaplanowanego działania nie ma dostępu do argumentów działania nadrzędnego w taki sposób, czy działania podrzędnego.  
  
 Poniższy fragment kodu przedstawia sposób przekazania formularza argumentu działania natywnego do zaplanowanego działania przy użyciu <xref:System.Activities.Activity.CacheMetadata%2A>.  
  
```  
public sealed class ChildActivity : NativeActivity  
{  
    public WriteLine _writeLine;  
    public InArgument<string> Message { get; set; }  
    private Variable<string> MessageVariable { get; set; }  
    public ChildActivity()  
    {  
        MessageVariable = new Variable<string>();  
        _writeLine = new WriteLine  
        {  
            Text = new InArgument<string>(MessageVariable),  
        };  
    }  
    protected override void CacheMetadata(NativeActivityMetadata metadata)  
    {  
        base.CacheMetadata(metadata);  
        metadata.AddImplementationVariable(this.MessageVariable);  
        metadata.AddImplementationChild(this._writeLine);  
    }  
    protected override void Execute(NativeActivityContext context)  
    {  
        string configuredMessage = context.GetValue(Message);  
        context.SetValue(MessageVariable, configuredMessage);  
        context.ScheduleActivity(this._writeLine);  
    }  
}  
```
