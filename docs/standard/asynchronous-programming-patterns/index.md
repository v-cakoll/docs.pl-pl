---
title: Wzorce programowania asynchronicznego
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: dfce69ee18b8346cd802b4934de63bf0a39c72f0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124269"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="8a626-102">Wzorce programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="8a626-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="8a626-103">Platforma .NET udostępnia trzy wzorce do wykonywania operacji asynchronicznych:</span><span class="sxs-lookup"><span data-stu-id="8a626-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="8a626-104">**Wzorzec asynchroniczny oparty na zadaniach (TAP)** , który używa pojedynczej metody do reprezentowania inicjacji i ukończenia operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="8a626-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="8a626-105">Naciśnij przycisk został wprowadzony w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="8a626-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="8a626-106">**Jest to zalecane podejście do programowania asynchronicznego w programie .NET.**</span><span class="sxs-lookup"><span data-stu-id="8a626-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="8a626-107">Słowa kluczowe [Async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) w C# programie oraz operatory [Async](../../visual-basic/language-reference/modifiers/async.md) i [await](../../visual-basic/language-reference/operators/await-operator.md) w Visual Basic Dodaj obsługę języka dla TAP.</span><span class="sxs-lookup"><span data-stu-id="8a626-107">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="8a626-108">Aby uzyskać więcej informacji, zobacz [wzorzec asynchroniczny oparty na zadaniach (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="8a626-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="8a626-109">**Wzorzec asynchroniczny oparty na zdarzeniach (EAP)** , który jest oparty na zdarzeniach starszym modelu do zapewniania zachowania asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="8a626-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="8a626-110">Wymaga metody, która ma `Async` sufiks i co najmniej jedno zdarzenie, typy delegatów obsługi zdarzeń i typy pochodne `EventArg`.</span><span class="sxs-lookup"><span data-stu-id="8a626-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="8a626-111">Protokół EAP został wprowadzony w .NET Framework 2,0.</span><span class="sxs-lookup"><span data-stu-id="8a626-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="8a626-112">Nie jest już zalecane w przypadku nowych rozwiązań programistycznych.</span><span class="sxs-lookup"><span data-stu-id="8a626-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="8a626-113">Aby uzyskać więcej informacji, zobacz [asynchroniczny wzorzec oparty na zdarzeniach (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="8a626-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="8a626-114">Wzorzec **modelu programowania asynchronicznego (APM)** (nazywany również wzorcem <xref:System.IAsyncResult>), który jest starszym modelem, który używa interfejsu <xref:System.IAsyncResult>, aby zapewnić asynchroniczne zachowanie.</span><span class="sxs-lookup"><span data-stu-id="8a626-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="8a626-115">W tym wzorcu operacje synchroniczne wymagają `Begin` i `End` metod (na przykład `BeginWrite` i `EndWrite` do implementowania asynchronicznej operacji zapisu).</span><span class="sxs-lookup"><span data-stu-id="8a626-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="8a626-116">Ten wzorzec nie jest już zalecany w przypadku nowych rozwiązań programistycznych.</span><span class="sxs-lookup"><span data-stu-id="8a626-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="8a626-117">Aby uzyskać więcej informacji, zobacz [asynchroniczny model programowania (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="8a626-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="8a626-118">Porównanie wzorców</span><span class="sxs-lookup"><span data-stu-id="8a626-118">Comparison of patterns</span></span>

<span data-ttu-id="8a626-119">Aby szybko porównać sposób wykonywania operacji asynchronicznych przez trzy modele wzorców, należy rozważyć metodę `Read`, która odczytuje określoną ilość danych do podanego buforu, rozpoczynając od określonego przesunięcia:</span><span class="sxs-lookup"><span data-stu-id="8a626-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="8a626-120">Odpowiedniki TAP dla tej metody uwidaczniają następujące pojedyncze metody `ReadAsync`:</span><span class="sxs-lookup"><span data-stu-id="8a626-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="8a626-121">Odpowiedniki protokołu EAP uwidaczniają następujący zestaw typów i członków:</span><span class="sxs-lookup"><span data-stu-id="8a626-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="8a626-122">Odpowiednika APM uwidacznia `BeginRead` i `EndRead` metody:</span><span class="sxs-lookup"><span data-stu-id="8a626-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="8a626-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8a626-123">See also</span></span>

- [<span data-ttu-id="8a626-124">Na poziomie Async</span><span class="sxs-lookup"><span data-stu-id="8a626-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="8a626-125">Programowanie asynchroniczne wC#</span><span class="sxs-lookup"><span data-stu-id="8a626-125">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="8a626-126">Programowanie asynchroniczne wF#</span><span class="sxs-lookup"><span data-stu-id="8a626-126">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="8a626-127">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="8a626-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
