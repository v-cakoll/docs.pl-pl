---
title: Wzorce programowania asynchronicznego
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 50d76aef201fead37923a65cfeead16638b09842
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "62031177"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="2da99-102">Wzorce programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="2da99-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="2da99-103">.NET zawiera trzy wzorce do wykonywania operacji asynchronicznych:</span><span class="sxs-lookup"><span data-stu-id="2da99-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="2da99-104">**Oparta na zadaniach asynchronicznej wzorca (TAP)**, który używa jednej metody do reprezentowania rozpoczęcie i zakończenie operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="2da99-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="2da99-105">Naciśnij pozycję została wprowadzona w programie .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="2da99-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="2da99-106">**Jest to zalecane podejście do programowania asynchronicznego w .NET.**</span><span class="sxs-lookup"><span data-stu-id="2da99-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="2da99-107">[Async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) słów kluczowych w C# i [Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operatory w języku Visual Basic Dodaj Obsługa języków w programie TAP.</span><span class="sxs-lookup"><span data-stu-id="2da99-107">The [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) keywords in C# and the [Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="2da99-108">Aby uzyskać więcej informacji, zobacz [opartego na zadaniach asynchronicznej wzorca (TAP)](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="2da99-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="2da99-109">**Oparte na zdarzeniach asynchroniczny wzorzec (EAP)**, który jest oparty na zdarzeniach model starszej wersji zapewniające zachowanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="2da99-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="2da99-110">Wymaga metody, która ma `Async` sufiks i jeden lub więcej zdarzeń, typów delegatów obsługi zdarzeń, a `EventArg`— typy pochodne.</span><span class="sxs-lookup"><span data-stu-id="2da99-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="2da99-111">Protokół EAP został wprowadzony w programie .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="2da99-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="2da99-112">Zaleca się już w nowych wdrożeniach.</span><span class="sxs-lookup"><span data-stu-id="2da99-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="2da99-113">Aby uzyskać więcej informacji, zobacz [oparte na zdarzeniach asynchroniczny wzorzec (EAP)](event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="2da99-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="2da99-114">**Modelu programowania asynchronicznego (APM)** wzorca (nazywane również <xref:System.IAsyncResult> wzorca), czyli starszego modelu, który wykorzystuje <xref:System.IAsyncResult> interfejsu, aby zapewnić zachowanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="2da99-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="2da99-115">W tym wzorcu synchroniczne operacje wymagają `Begin` i `End` metod (na przykład `BeginWrite` i `EndWrite` do implementacji asynchronicznego zapisu operacji).</span><span class="sxs-lookup"><span data-stu-id="2da99-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="2da99-116">Ten wzorzec nie jest zalecane w przypadku nowych wdrożeń.</span><span class="sxs-lookup"><span data-stu-id="2da99-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="2da99-117">Aby uzyskać więcej informacji, zobacz [modelu programowania asynchronicznego (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="2da99-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="2da99-118">Porównanie wzorców</span><span class="sxs-lookup"><span data-stu-id="2da99-118">Comparison of patterns</span></span>

<span data-ttu-id="2da99-119">Porównanie szybki sposób trzy wzorce operacji asynchronicznych w modelu, należy wziąć pod uwagę `Read` metodę, która odczytuje określoną ilość danych do dostarczonego buforu, rozpoczynając od określonego przesunięcia:</span><span class="sxs-lookup"><span data-stu-id="2da99-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="2da99-120">Odpowiednikiem tej metody wzorca TAP może narazić następujące pojedynczego `ReadAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="2da99-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="2da99-121">Odpowiednikiem EAP wystawi następujący zestaw typów i elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="2da99-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="2da99-122">Odpowiednikiem APM może narazić `BeginRead` i `EndRead` metody:</span><span class="sxs-lookup"><span data-stu-id="2da99-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="2da99-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="2da99-123">See also</span></span>

- [<span data-ttu-id="2da99-124">Asynchroniczne szczegółowo</span><span class="sxs-lookup"><span data-stu-id="2da99-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="2da99-125">Programowanie asynchroniczne w języku C#</span><span class="sxs-lookup"><span data-stu-id="2da99-125">Asynchronous programming in C#</span></span>](~/docs/csharp/async.md)
- [<span data-ttu-id="2da99-126">Async — Programowanie wF#</span><span class="sxs-lookup"><span data-stu-id="2da99-126">Async Programming in F#</span></span>](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="2da99-127">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="2da99-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
