---
title: Uwidacznianie danych przy użyciu metody CacheMetadata
ms.date: 03/30/2017
ms.assetid: 34832f23-e93b-40e6-a80b-606a855a00d9
ms.openlocfilehash: a044c896e56541ee954fc33853376eb8293c6ede
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61945707"
---
# <a name="exposing-data-with-cachemetadata"></a><span data-ttu-id="6fc9e-102">Uwidacznianie danych przy użyciu metody CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="6fc9e-102">Exposing data with CacheMetadata</span></span>

<span data-ttu-id="6fc9e-103">Przed wykonaniem działanie, środowiska uruchomieniowego przepływu pracy uzyskuje wszystkie informacje dotyczące działania wymagające utrzymane, gdy jej wykonanie.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-103">Before executing an activity, the workflow runtime obtains all of the information about the activity that it needs in order to maintain its execution.</span></span> <span data-ttu-id="6fc9e-104">Środowisko wykonawcze przepływów pracy pobiera te informacje podczas wykonywania <xref:System.Activities.Activity.CacheMetadata%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-104">The workflow runtime gets this information during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="6fc9e-105">Domyślna implementacja tej metody zawiera środowiska uruchomieniowego wszystkie publiczne argumentów, zmienne i działania podrzędne udostępnianych przez działanie w czasie, który jest ono wykonywane; Jeśli działanie musi podać więcej informacji do środowiska uruchomieniowego niż to (np. składowe prywatne lub działań na zaplanowane przez działanie), ta metoda może być zastąpiona podać go.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-105">The default implementation of this method provides the runtime with all of the public arguments, variables, and child activities exposed by the activity at the time it is executed; if the activity needs to give more information to the runtime than this (such as private members, or activities to be scheduled by the activity), this method can be overridden to provide it.</span></span>

## <a name="default-cachemetadata-behavior"></a><span data-ttu-id="6fc9e-106">Domyślne zachowanie użyciu metody CacheMetadata</span><span class="sxs-lookup"><span data-stu-id="6fc9e-106">Default CacheMetadata behavior</span></span>

<span data-ttu-id="6fc9e-107">Domyślna implementacja klasy <xref:System.Activities.NativeActivity.CacheMetadata%2A> działań, które wynikają z <xref:System.Activities.NativeActivity> przetwarza następujące metody w następujący sposób:</span><span class="sxs-lookup"><span data-stu-id="6fc9e-107">The default implementation of <xref:System.Activities.NativeActivity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.NativeActivity> processes the following method types in the following ways:</span></span>

- <span data-ttu-id="6fc9e-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, lub <xref:System.Activities.InOutArgument%601> (argumenty ogólne): Te argumenty są widoczne dla środowiska uruchomieniowego jako argumenty o nazwie i wpisz równa nazwy uwidocznione właściwości i typ, kierunku odpowiedniego argumentu i pewne dane weryfikacji.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-108"><xref:System.Activities.InArgument%601>, <xref:System.Activities.OutArgument%601>, or <xref:System.Activities.InOutArgument%601> (generic arguments): These arguments are exposed to the runtime as arguments with a name and type equal to the exposed property name and type, the appropriate argument direction, and some validation data.</span></span>

- <span data-ttu-id="6fc9e-109"><xref:System.Activities.Variable> lub jego każdej podklasy: Te elementy członkowskie są widoczne środowisko uruchomieniowe jako zmienne publicznych.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-109"><xref:System.Activities.Variable> or any subclass thereof: These members are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="6fc9e-110"><xref:System.Activities.Activity> lub jego każdej podklasy: Te elementy członkowskie są widoczne środowisko uruchomieniowe jako działania podrzędne publicznych.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-110"><xref:System.Activities.Activity> or any subclass thereof: These members are exposed to the runtime as public child activities.</span></span> <span data-ttu-id="6fc9e-111">Zachowanie domyślne można zaimplementować jawnie przez wywołanie metody <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, przekazując działania podrzędnego.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-111">The default behavior can be implemented explicitly by calling <xref:System.Activities.ActivityMetadata.AddImportedChild%2A>, passing in the child activity.</span></span>

- <span data-ttu-id="6fc9e-112"><xref:System.Activities.ActivityDelegate> lub jego każdej podklasy: Te elementy członkowskie są udostępniane do środowiska uruchomieniowego pełnomocnikiem publicznych.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-112"><xref:System.Activities.ActivityDelegate> or any subclass thereof: These members are exposed to the runtime as public delegates.</span></span>

- <span data-ttu-id="6fc9e-113"><xref:System.Collections.ICollection> typu <xref:System.Activities.Variable>: Wszystkie elementy w kolekcji są dostępne do środowiska uruchomieniowego jako zmienne publicznego.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-113"><xref:System.Collections.ICollection> of type <xref:System.Activities.Variable>: All elements in the collection are exposed to the runtime as public variables.</span></span>

- <span data-ttu-id="6fc9e-114"><xref:System.Collections.ICollection> typu <xref:System.Activities.Activity>: Wszystkie elementy w kolekcji są dostępne do środowiska uruchomieniowego jako publiczne elementy podrzędne.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-114"><xref:System.Collections.ICollection> of type <xref:System.Activities.Activity>: All elements in the collection are exposed to the runtime as public children.</span></span>

- <span data-ttu-id="6fc9e-115"><xref:System.Collections.ICollection> typu <xref:System.Activities.ActivityDelegate>: Wszystkie elementy w kolekcji są dostępne do środowiska uruchomieniowego pełnomocnikiem publicznych.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-115"><xref:System.Collections.ICollection> of type <xref:System.Activities.ActivityDelegate>: All elements in the collection are exposed to the runtime as public delegates.</span></span>

<span data-ttu-id="6fc9e-116"><xref:System.Activities.Activity.CacheMetadata%2A> Działań, które wynikają z <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, i <xref:System.Activities.AsyncCodeActivity> również działać tak jak powyżej, z wyjątkiem następujących różnic:</span><span class="sxs-lookup"><span data-stu-id="6fc9e-116">The <xref:System.Activities.Activity.CacheMetadata%2A> for activities that derive from <xref:System.Activities.Activity>, <xref:System.Workflow.Activities.CodeActivity>, and <xref:System.Activities.AsyncCodeActivity> also function as above, except for the following differences:</span></span>

- <span data-ttu-id="6fc9e-117">Klasy, które wynikają z <xref:System.Activities.Activity> nie można zaplanować działania podrzędne lub delegatów, więc takich elementów członkowskich są widoczne jako zaimportowane elementy podrzędne i delegatów;</span><span class="sxs-lookup"><span data-stu-id="6fc9e-117">Classes that derive from <xref:System.Activities.Activity> cannot schedule child activities or delegates, so such members are exposed as imported children and delegates; the</span></span>

- <span data-ttu-id="6fc9e-118">Klasy, które wynikają z <xref:System.Activities.CodeActivity> i <xref:System.Activities.AsyncCodeActivity> nie obsługują zmiennych, elementy podrzędne lub delegatów, więc tylko argumenty zostaną ujawnione.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-118">Classes that derive from <xref:System.Activities.CodeActivity> and <xref:System.Activities.AsyncCodeActivity> do not support variables, children, or delegates, so only arguments will be exposed.</span></span>

## <a name="overriding-cachemetadata-to-provide-information-to-the-runtime"></a><span data-ttu-id="6fc9e-119">Zastępowanie użyciu metody CacheMetadata, aby podać informacje do środowiska uruchomieniowego</span><span class="sxs-lookup"><span data-stu-id="6fc9e-119">Overriding CacheMetadata to provide information to the runtime</span></span>

<span data-ttu-id="6fc9e-120">Poniższy fragment kodu przedstawia sposób dodawania informacji na temat elementów członkowskich do metadanych działania podczas wykonywania <xref:System.Activities.Activity.CacheMetadata%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-120">The following code snippet demonstrates how to add information about members to an activity’s metadata during the execution of the <xref:System.Activities.Activity.CacheMetadata%2A> method.</span></span> <span data-ttu-id="6fc9e-121">Należy pamiętać, że podstawowy metody jest wywoływana, aby wszystkie publiczne dane o działaniu z pamięci podręcznej.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-121">Note that the base of the method is called to cache all public data about the activity.</span></span>

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

## <a name="using-cachemetadata-to-expose-implementation-children"></a><span data-ttu-id="6fc9e-122">Za pomocą użyciu metody CacheMetadata do udostępnienia implementacji elementy podrzędne</span><span class="sxs-lookup"><span data-stu-id="6fc9e-122">Using CacheMetadata to expose implementation children</span></span>

<span data-ttu-id="6fc9e-123">Aby można było przekazać dane do działania podrzędne, które mają być zaplanowane przez działanie, korzystając ze zmiennych, należy go dodać zmienne jako zmienne w implementacji; zmienne publiczny nie może mieć wartości ustawiana w ten sposób.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-123">In order to pass data to child activities that are to be scheduled by an activity using variables, it is necessary to add the variables as implementation variables; public variables cannot have their values set this way.</span></span> <span data-ttu-id="6fc9e-124">Przyczyną jest, czy działania są przeznaczone do wykonywania bardziej jako implementacji funkcji, (które mają parametry), a nie klasy zhermetyzowany, (które mają właściwości).</span><span class="sxs-lookup"><span data-stu-id="6fc9e-124">The reason for this is that activities are intended to be executed more as implementations of functions (which have parameters), rather than encapsulated classes (which have properties).</span></span> <span data-ttu-id="6fc9e-125">Jednak istnieją sytuacje, w których argumenty muszą być jawnie ustawione, takie jak kiedy przy użyciu <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, ponieważ zaplanowanego działania nie ma dostępu do argumentów działania nadrzędnego w taki sposób, czy działanie podrzędne.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-125">However, there are situations in which the arguments must be explicitly set, such as when using <xref:System.Activities.NativeActivityContext.ScheduleActivity%2A>, since the scheduled activity doesn't have access to the parent activity's arguments in the way a child activity would.</span></span>

<span data-ttu-id="6fc9e-126">Poniższy fragment kodu pokazuje, jak przekazać argument formularza działania natywnego do zaplanowanych działań przy użyciu <xref:System.Activities.Activity.CacheMetadata%2A>.</span><span class="sxs-lookup"><span data-stu-id="6fc9e-126">The following code snippet demonstrates how to pass an argument form a native activity into a scheduled activity using <xref:System.Activities.Activity.CacheMetadata%2A>.</span></span>

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
