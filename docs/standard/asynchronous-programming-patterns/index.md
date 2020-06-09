---
title: Wzorce programowania asynchronicznego
description: Informacje na temat wzorca asynchronicznego opartego na zadaniach (TAP), asynchronicznego wzorca opartego na zdarzeniach (EAP), & asynchronicznego modelu programowania (APM) w programie .NET.
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: bd4d44d8de8a64be82e9ce6af593a86719b59fcf
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/09/2020
ms.locfileid: "84583508"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="0df5e-103">Wzorce programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="0df5e-103">Asynchronous programming patterns</span></span>

<span data-ttu-id="0df5e-104">Platforma .NET udostępnia trzy wzorce do wykonywania operacji asynchronicznych:</span><span class="sxs-lookup"><span data-stu-id="0df5e-104">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="0df5e-105">**Wzorzec asynchroniczny oparty na zadaniach (TAP)**, który używa pojedynczej metody do reprezentowania inicjacji i ukończenia operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="0df5e-105">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="0df5e-106">Naciśnij przycisk został wprowadzony w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="0df5e-106">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="0df5e-107">**Jest to zalecane podejście do programowania asynchronicznego w programie .NET.**</span><span class="sxs-lookup"><span data-stu-id="0df5e-107">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="0df5e-108">Słowa kluczowe [Async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) w języku C# oraz operatory [Async](../../visual-basic/language-reference/modifiers/async.md) i [await](../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic Dodaj obsługę języka dla programu TAP.</span><span class="sxs-lookup"><span data-stu-id="0df5e-108">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="0df5e-109">Aby uzyskać więcej informacji, zobacz [wzorzec asynchroniczny oparty na zadaniach (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="0df5e-109">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="0df5e-110">**Wzorzec asynchroniczny oparty na zdarzeniach (EAP)**, który jest oparty na zdarzeniach starszym modelu do zapewniania zachowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="0df5e-110">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="0df5e-111">Wymaga metody, która ma `Async` sufiks i jedno lub więcej zdarzeń, typy delegatów obsługi zdarzeń i `EventArg` Typy pochodne.</span><span class="sxs-lookup"><span data-stu-id="0df5e-111">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="0df5e-112">Protokół EAP został wprowadzony w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="0df5e-112">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="0df5e-113">Nie jest już zalecane w przypadku nowych rozwiązań programistycznych.</span><span class="sxs-lookup"><span data-stu-id="0df5e-113">It's no longer recommended for new development.</span></span> <span data-ttu-id="0df5e-114">Aby uzyskać więcej informacji, zobacz [asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="0df5e-114">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="0df5e-115">Wzorzec **modelu programowania asynchronicznego (APM)** (nazywany również <xref:System.IAsyncResult> wzorcem), który jest starszym modelem, który używa <xref:System.IAsyncResult> interfejsu w celu zapewnienia zachowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="0df5e-115">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="0df5e-116">W tym wzorcu operacje synchroniczne wymagają, `Begin` a `End` metody (na przykład `BeginWrite` i `EndWrite` w celu zaimplementowania asynchronicznej operacji zapisu).</span><span class="sxs-lookup"><span data-stu-id="0df5e-116">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="0df5e-117">Ten wzorzec nie jest już zalecany w przypadku nowych rozwiązań programistycznych.</span><span class="sxs-lookup"><span data-stu-id="0df5e-117">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="0df5e-118">Aby uzyskać więcej informacji, zobacz [asynchroniczny model programowania (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="0df5e-118">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="0df5e-119">Porównanie wzorców</span><span class="sxs-lookup"><span data-stu-id="0df5e-119">Comparison of patterns</span></span>

<span data-ttu-id="0df5e-120">Aby szybko porównać sposób wykonywania operacji asynchronicznych przez trzy wzorce, należy rozważyć `Read` metodę, która odczytuje określoną ilość danych do podanego buforu, rozpoczynając od określonego przesunięcia:</span><span class="sxs-lookup"><span data-stu-id="0df5e-120">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="0df5e-121">Odpowiedniki TAP dla tej metody uwidaczniają następujące pojedyncze `ReadAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="0df5e-121">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="0df5e-122">Odpowiedniki protokołu EAP uwidaczniają następujący zestaw typów i członków:</span><span class="sxs-lookup"><span data-stu-id="0df5e-122">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="0df5e-123">Odpowiedniki APM uwidaczniają `BeginRead` metody i `EndRead` :</span><span class="sxs-lookup"><span data-stu-id="0df5e-123">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="0df5e-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0df5e-124">See also</span></span>

- [<span data-ttu-id="0df5e-125">Na poziomie Async</span><span class="sxs-lookup"><span data-stu-id="0df5e-125">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="0df5e-126">Programowanie asynchroniczne w języku C #</span><span class="sxs-lookup"><span data-stu-id="0df5e-126">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="0df5e-127">Programowanie asynchroniczne w F #</span><span class="sxs-lookup"><span data-stu-id="0df5e-127">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="0df5e-128">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0df5e-128">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
