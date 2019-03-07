---
title: Uwidacznianie danych przy użyciu metody CacheMetadata
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: a044c896e56541ee954fc33853376eb8293c6ede
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57482681"
---
# <a name="exposing-data-with-cachemetadata"></a>Uwidacznianie danych przy użyciu metody CacheMetadata

Przed wykonaniem działanie, środowiska uruchomieniowego przepływu pracy uzyskuje wszystkie informacje dotyczące działania wymagające utrzymane, gdy jej wykonanie. Środowisko wykonawcze przepływów pracy pobiera te informacje podczas wykonywania <xref:System.Activities.Activity.CacheMetadata%2A> metody. Domyślna implementacja tej metody zawiera środowiska uruchomieniowego wszystkie publiczne argumentów, zmienne i działania podrzędne udostępnianych przez działanie w czasie, który jest ono wykonywane; Jeśli działanie musi podać więcej informacji do środowiska uruchomieniowego niż to (np. składowe prywatne lub działań na zaplanowane przez działanie), ta metoda może być zastąpiona podać go.

## <a name="default-cachemetadata-behavior"></a>Domyślne zachowanie użyciu metody CacheMetadata

Domyślna implementacja klasy <xref:System.Activities.NativeActivity.CacheMetadata%2A> działań, które wynikają z <xref:System.Activities.NativeActivity> przetwarza następujące metody w następujący sposób:

- <xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, lub <xref:System.Activities.InOutArgument%601> (argumenty ogólne): Te argumenty są widoczne dla środowiska uruchomieniowego jako argumenty o nazwie i wpisz równa nazwy uwidocznione właściwości i typ, kierunku odpowiedniego argumentu i pewne dane weryfikacji.

- <xref:System.Activities.Variable> lub jego każdej podklasy: Te elementy członkowskie są widoczne środowisko uruchomieniowe jako zmienne publicznych.

- <xref:System.Activities.Activity> lub jego każdej podklasy: Te elementy członkowskie są widoczne środowisko uruchomieniowe jako działania podrzędne publicznych. Zachowanie domyślne można zaimplementować jawnie przez wywołanie metody <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, przekazując działania podrzędnego.

- <xref:System.Activities.ActivityDelegate> lub jego każdej podklasy: Te elementy członkowskie są udostępniane do środowiska uruchomieniowego pełnomocnikiem publicznych.

- <xref:System.Collections.ICollection> typu <xref:System.Activities.Variable>: Wszystkie elementy w kolekcji są dostępne do środowiska uruchomieniowego jako zmienne publicznego.

- <xref:System.Collections.ICollection> typu <xref:System.Activities.Activity>: Wszystkie elementy w kolekcji są dostępne do środowiska uruchomieniowego jako publiczne elementy podrzędne.

- <xref:System.Collections.ICollection> typu <xref:System.Activities.ActivityDelegate>: Wszystkie elementy w kolekcji są dostępne do środowiska uruchomieniowego pełnomocnikiem publicznych.

<xref:System.Activities.Activity.CacheMetadata%2A> Działań, które wynikają z <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, i <xref:System.Activities.AsyncCodeActivity> również działać tak jak powyżej, z wyjątkiem następujących różnic:

- Klasy, które wynikają z <xref:System.Activities.Activity> nie można zaplanować działania podrzędne lub delegatów, więc takich elementów członkowskich są widoczne jako zaimportowane elementy podrzędne i delegatów;

- Klasy, które wynikają z <xref:System.Activities.CodeActivity> i <xref:System.Activities.AsyncCodeActivity> nie obsługują zmiennych, elementy podrzędne lub delegatów, więc tylko argumenty zostaną ujawnione.

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a>Zastępowanie użyciu metody CacheMetadata, aby podać informacje do środowiska uruchomieniowego

Poniższy fragment kodu przedstawia sposób dodawania informacji na temat elementów członkowskich do metadanych działania podczas wykonywania <xref:System.Activities.Activity.CacheMetadata%2A> metody. Należy pamiętać, że podstawowy metody jest wywoływana, aby wszystkie publiczne dane o działaniu z pamięci podręcznej.

```csharp
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

## <a name="using-cachemetadata-to-expose-implementation-children"></a>Za pomocą użyciu metody CacheMetadata do udostępnienia implementacji elementy podrzędne

Aby można było przekazać dane do działania podrzędne, które mają być zaplanowane przez działanie, korzystając ze zmiennych, należy go dodać zmienne jako zmienne w implementacji; zmienne publiczny nie może mieć wartości ustawiana w ten sposób. Przyczyną jest, czy działania są przeznaczone do wykonywania bardziej jako implementacji funkcji, (które mają parametry), a nie klasy zhermetyzowany, (które mają właściwości). Jednak istnieją sytuacje, w których argumenty muszą być jawnie ustawione, takie jak kiedy przy użyciu <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, ponieważ zaplanowanego działania nie ma dostępu do argumentów działania nadrzędnego w taki sposób, czy działanie podrzędne.

Poniższy fragment kodu pokazuje, jak przekazać argument formularza działania natywnego do zaplanowanych działań przy użyciu <xref:System.Activities.Activity.CacheMetadata%2A>.

```csharp
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
