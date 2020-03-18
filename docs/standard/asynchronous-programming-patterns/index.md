---
title: Wzorce programowania asynchronicznego
ms.date: 10/16/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- asynchronous design patterns, .NET
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
ms.openlocfilehash: e1efe9c3eb57f317def91e527506c358eb086679
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "78160056"
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="a29cc-102">Wzorce programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="a29cc-102">Asynchronous programming patterns</span></span>

<span data-ttu-id="a29cc-103">.NET udostępnia trzy wzorce do wykonywania operacji asynchronicznych:</span><span class="sxs-lookup"><span data-stu-id="a29cc-103">.NET provides three patterns for performing asynchronous operations:</span></span>  

- <span data-ttu-id="a29cc-104">**Oparty na zadaniach wzorzec asynchroniczny (TAP),** który używa pojedynczej metody do reprezentowania inicjowania i zakończenia operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="a29cc-104">**Task-based Asynchronous Pattern (TAP)**, which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="a29cc-105">TAP został wprowadzony w .NET Framework 4.</span><span class="sxs-lookup"><span data-stu-id="a29cc-105">TAP was introduced in the .NET Framework 4.</span></span> <span data-ttu-id="a29cc-106">**Jest to zalecane podejście do programowania asynchronicznego w .NET.**</span><span class="sxs-lookup"><span data-stu-id="a29cc-106">**It's the recommended approach to asynchronous programming in .NET.**</span></span> <span data-ttu-id="a29cc-107">[Async](../../csharp/language-reference/keywords/async.md) i [await](../../csharp/language-reference/operators/await.md) słów kluczowych w języku C# i [Async](../../visual-basic/language-reference/modifiers/async.md) i [await](../../visual-basic/language-reference/operators/await-operator.md) operatorów w języku Visual Basic dodać obsługę języka tap.</span><span class="sxs-lookup"><span data-stu-id="a29cc-107">The [async](../../csharp/language-reference/keywords/async.md) and [await](../../csharp/language-reference/operators/await.md) keywords in C# and the [Async](../../visual-basic/language-reference/modifiers/async.md) and [Await](../../visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic add language support for TAP.</span></span> <span data-ttu-id="a29cc-108">Aby uzyskać więcej informacji, zobacz [Asynchroniczny wzorzec (TAP) oparty na zadaniach](task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="a29cc-108">For more information, see [Task-based Asynchronous Pattern (TAP)](task-based-asynchronous-pattern-tap.md).</span></span>  

- <span data-ttu-id="a29cc-109">**Oparty na zdarzeniach wzorzec asynchroniczny (EAP),** który jest opartym na zdarzeniach starszym modelu zapewniającym zachowanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="a29cc-109">**Event-based Asynchronous Pattern (EAP)**, which is the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="a29cc-110">Wymaga metody, która `Async` ma sufiks i jeden lub więcej zdarzeń, typy delegatów obsługi obsługi zdarzeń i `EventArg`typy pochodne.</span><span class="sxs-lookup"><span data-stu-id="a29cc-110">It requires a method that has the `Async` suffix and one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="a29cc-111">EAP został wprowadzony w .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="a29cc-111">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="a29cc-112">Nie jest już zalecany do nowego rozwoju.</span><span class="sxs-lookup"><span data-stu-id="a29cc-112">It's no longer recommended for new development.</span></span> <span data-ttu-id="a29cc-113">Aby uzyskać więcej informacji, zobacz [Wzorce asynchroniczne oparte na zdarzeniach (EAP).](event-based-asynchronous-pattern-eap.md)</span><span class="sxs-lookup"><span data-stu-id="a29cc-113">For more information, see [Event-based Asynchronous Pattern (EAP)](event-based-asynchronous-pattern-eap.md).</span></span>  

- <span data-ttu-id="a29cc-114">**Asynchroniczny model programowania (APM)** wzorzec (nazywany również <xref:System.IAsyncResult> wzorzec), który jest starszy model, który używa <xref:System.IAsyncResult> interfejsu, aby zapewnić zachowanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="a29cc-114">**Asynchronous Programming Model (APM)** pattern (also called the <xref:System.IAsyncResult> pattern), which is the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="a29cc-115">W tym wzorcu operacje `Begin` `End` synchroniczne wymagają `BeginWrite` i `EndWrite` metody (na przykład i zaimplementować operację zapisu asynchronicznego).</span><span class="sxs-lookup"><span data-stu-id="a29cc-115">In this pattern, synchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` to implement an asynchronous write operation).</span></span> <span data-ttu-id="a29cc-116">Ten wzorzec nie jest już zalecany do nowego rozwoju.</span><span class="sxs-lookup"><span data-stu-id="a29cc-116">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="a29cc-117">Aby uzyskać więcej informacji, zobacz [Asynchroniczny model programowania (APM)](asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="a29cc-117">For more information, see [Asynchronous Programming Model (APM)](asynchronous-programming-model-apm.md).</span></span>  
  
## <a name="comparison-of-patterns"></a><span data-ttu-id="a29cc-118">Porównanie wzorców</span><span class="sxs-lookup"><span data-stu-id="a29cc-118">Comparison of patterns</span></span>

<span data-ttu-id="a29cc-119">Aby uzyskać szybkie porównanie sposobu, w jaki trzy wzorce modelu operacji asynchronicznych, należy wziąć pod uwagę `Read` metodę, która odczytuje określoną ilość danych do dostarczonego buforu, począwszy od określonego odsunięcia:</span><span class="sxs-lookup"><span data-stu-id="a29cc-119">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  

<span data-ttu-id="a29cc-120">Odpowiednik TAP tej metody uwidacznia następujące pojedynczej `ReadAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="a29cc-120">The TAP counterpart of this method would expose the following single `ReadAsync` method:</span></span>  
  
```csharp
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```

<span data-ttu-id="a29cc-121">Odpowiednik EAP będzie narazić następujący zestaw typów i elementów członkowskich:</span><span class="sxs-lookup"><span data-stu-id="a29cc-121">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="a29cc-122">Odpowiednik APM będzie `BeginRead` narazić i `EndRead` metody:</span><span class="sxs-lookup"><span data-stu-id="a29cc-122">The APM counterpart would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  

## <a name="see-also"></a><span data-ttu-id="a29cc-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a29cc-123">See also</span></span>

- [<span data-ttu-id="a29cc-124">Async w głębi</span><span class="sxs-lookup"><span data-stu-id="a29cc-124">Async in depth</span></span>](../async-in-depth.md)
- [<span data-ttu-id="a29cc-125">Programowanie asynchroniczne w języku C #</span><span class="sxs-lookup"><span data-stu-id="a29cc-125">Asynchronous programming in C#</span></span>](../../csharp/async.md)
- [<span data-ttu-id="a29cc-126">Programowanie asynchroniczne w f #</span><span class="sxs-lookup"><span data-stu-id="a29cc-126">Async Programming in F#</span></span>](../../fsharp/tutorials/asynchronous-and-concurrent-programming/async.md)
- [<span data-ttu-id="a29cc-127">Programowanie asynchroniczne z asynchroniczną i oczekiwaną (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a29cc-127">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](../../visual-basic/programming-guide/concepts/async/index.md)
