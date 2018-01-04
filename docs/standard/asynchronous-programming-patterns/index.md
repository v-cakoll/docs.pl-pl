---
title: Wzorce programowania asynchronicznego
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- asynchronous design patterns, .NET Framework
- .NET Framework, asynchronous design patterns
ms.assetid: 4ece5c0b-f8fe-4114-9862-ac02cfe5a5d7
caps.latest.revision: "5"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 42298bc8e3101b03f6c3e03fec453b72cd959efb
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="asynchronous-programming-patterns"></a><span data-ttu-id="21258-102">Wzorce programowania asynchronicznego</span><span class="sxs-lookup"><span data-stu-id="21258-102">Asynchronous Programming Patterns</span></span>

<span data-ttu-id="21258-103">.NET Framework udostępnia trzy wzorce do wykonywania operacji asynchronicznych:</span><span class="sxs-lookup"><span data-stu-id="21258-103">The .NET Framework provides three patterns for performing asynchronous operations:</span></span>  
  
- <span data-ttu-id="21258-104">Asynchroniczny wzorzec modelu programowania (APM) (nazywane również <xref:System.IAsyncResult> wzorzec), których wymagają operacji asynchronicznych `Begin` i `End` metody (na przykład `BeginWrite` i `EndWrite` dla asynchronicznego zapisu operacji).</span><span class="sxs-lookup"><span data-stu-id="21258-104">Asynchronous Programming Model (APM) pattern (also called the <xref:System.IAsyncResult> pattern), where asynchronous operations require `Begin` and `End` methods (for example, `BeginWrite` and `EndWrite` for asynchronous write operations).</span></span> <span data-ttu-id="21258-105">Ten wzorzec już zaleca się nowych wdrożeń.</span><span class="sxs-lookup"><span data-stu-id="21258-105">This pattern is no longer recommended for new development.</span></span> <span data-ttu-id="21258-106">Aby uzyskać więcej informacji, zobacz [asynchronicznego programowania modelu (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span><span class="sxs-lookup"><span data-stu-id="21258-106">For more information, see [Asynchronous Programming Model (APM)](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md).</span></span>  
  
- <span data-ttu-id="21258-107">Oparty na zdarzeniach asynchroniczne wzorca (EAP), która wymaga metody, która ma `Async` sufiks, a także wymaga co najmniej jednego zdarzenia, typów obiektu delegowanego obsługi zdarzeń, a `EventArg`-typów pochodnych.</span><span class="sxs-lookup"><span data-stu-id="21258-107">Event-based Asynchronous Pattern (EAP), which requires a method that has the `Async` suffix, and also requires one or more events, event handler delegate types, and `EventArg`-derived types.</span></span> <span data-ttu-id="21258-108">Protokół EAP został wprowadzony w .NET Framework 2.0.</span><span class="sxs-lookup"><span data-stu-id="21258-108">EAP was introduced in the .NET Framework 2.0.</span></span> <span data-ttu-id="21258-109">Zaleca się już w nowych wdrożeniach.</span><span class="sxs-lookup"><span data-stu-id="21258-109">It is no longer recommended for new development.</span></span> <span data-ttu-id="21258-110">Aby uzyskać więcej informacji, zobacz [oparty na zdarzeniach asynchroniczny wzorzec (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span><span class="sxs-lookup"><span data-stu-id="21258-110">For more information, see [Event-based Asynchronous Pattern (EAP)](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md).</span></span>  
  
- <span data-ttu-id="21258-111">Oparty na zadaniach asynchronicznej wzorca (TAP), który za pomocą pojedynczej metody reprezentują rozpoczęcie i zakończenie operacji asynchronicznej.</span><span class="sxs-lookup"><span data-stu-id="21258-111">Task-based Asynchronous Pattern (TAP), which uses a single method to represent the initiation and completion of an asynchronous operation.</span></span> <span data-ttu-id="21258-112">NACIŚNIJ została wprowadzona w .NET Framework 4 i jest zalecane podejście do asynchronicznego programowania w programie .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="21258-112">TAP was introduced in the .NET Framework 4 and is the recommended approach to asynchronous programming in the .NET Framework.</span></span> <span data-ttu-id="21258-113">[Async](~/docs/csharp/language-reference/keywords/async.md) i [await](~/docs/csharp/language-reference/keywords/await.md) słów kluczowych w języku C# i [Async](~/docs/visual-basic/language-reference/modifiers/async.md) i [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) Obsługa języków w programie TAP dodać operatory w języku Visual Basic.</span><span class="sxs-lookup"><span data-stu-id="21258-113">The [async](~/docs/csharp/language-reference/keywords/async.md) and [await](~/docs/csharp/language-reference/keywords/await.md) keywords in C# and the [Async](~/docs/visual-basic/language-reference/modifiers/async.md) and [Await](~/docs/visual-basic/language-reference/operators/await-operator.md) operators in Visual Basic Language add language support for TAP.</span></span> <span data-ttu-id="21258-114">Aby uzyskać więcej informacji, zobacz [opartego na zadaniach asynchronicznej wzorca (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span><span class="sxs-lookup"><span data-stu-id="21258-114">For more information, see [Task-based Asynchronous Pattern (TAP)](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md).</span></span>  
  
## <a name="comparing-patterns"></a><span data-ttu-id="21258-115">Porównywanie wzorce</span><span class="sxs-lookup"><span data-stu-id="21258-115">Comparing Patterns</span></span>  

<span data-ttu-id="21258-116">Porównanie szybki sposób trzy wzorce operacji asynchronicznych w modelu, należy wziąć pod uwagę `Read` metoda odczytuje określonej ilości danych do podanego buforu, zaczynając od określonego przesunięcia:</span><span class="sxs-lookup"><span data-stu-id="21258-116">For a quick comparison of how the three patterns model asynchronous operations, consider a `Read` method that reads a specified amount of data into a provided buffer starting at a specified offset:</span></span>  
  
```csharp  
public class MyClass  
{  
    public int Read(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="21258-117">Odpowiednikiem APM tej metody może narazić `BeginRead` i `EndRead` metod:</span><span class="sxs-lookup"><span data-stu-id="21258-117">The APM counterpart of this method would expose the `BeginRead` and `EndRead` methods:</span></span>  
  
```csharp  
public class MyClass  
{  
    public IAsyncResult BeginRead(  
        byte [] buffer, int offset, int count,   
        AsyncCallback callback, object state);  
    public int EndRead(IAsyncResult asyncResult);  
}  
```  
  
<span data-ttu-id="21258-118">Odpowiednik EAP wystawi następujący zestaw typów i członków:</span><span class="sxs-lookup"><span data-stu-id="21258-118">The EAP counterpart would expose the following set of types and members:</span></span>  
  
```csharp  
public class MyClass  
{  
    public void ReadAsync(byte [] buffer, int offset, int count);  
    public event ReadCompletedEventHandler ReadCompleted;  
}  
```  
  
<span data-ttu-id="21258-119">Odpowiednik NACIŚNIJ wystawi jednym następującego `ReadAsync` metody:</span><span class="sxs-lookup"><span data-stu-id="21258-119">The TAP counterpart would expose the following single `ReadAsync` method:</span></span>  
  
```csharp  
public class MyClass  
{  
    public Task<int> ReadAsync(byte [] buffer, int offset, int count);  
}  
```  
  
<span data-ttu-id="21258-120">Kompleksowe omówienie NACIŚNIJ APM i EAP, zobacz łączy znajdujących się w następnej sekcji.</span><span class="sxs-lookup"><span data-stu-id="21258-120">For a comprehensive discussion of TAP, APM, and EAP, see the links provided in the next section.</span></span>  
  
## <a name="related-topics"></a><span data-ttu-id="21258-121">Tematy pokrewne</span><span class="sxs-lookup"><span data-stu-id="21258-121">Related topics</span></span>

| <span data-ttu-id="21258-122">Tytuł</span><span class="sxs-lookup"><span data-stu-id="21258-122">Title</span></span> | <span data-ttu-id="21258-123">Opis</span><span class="sxs-lookup"><span data-stu-id="21258-123">Description</span></span> |
| ----- | ----------- |
| [<span data-ttu-id="21258-124">Model programowania asynchronicznego (APM)</span><span class="sxs-lookup"><span data-stu-id="21258-124">Asynchronous Programming Model (APM)</span></span>](../../../docs/standard/asynchronous-programming-patterns/asynchronous-programming-model-apm.md) | <span data-ttu-id="21258-125">W tym artykule opisano model starszej wersji, który używa <xref:System.IAsyncResult> interfejsu, aby zapewnić zachowanie asynchronicznego.</span><span class="sxs-lookup"><span data-stu-id="21258-125">Describes the legacy model that uses the <xref:System.IAsyncResult> interface to provide asynchronous behavior.</span></span> <span data-ttu-id="21258-126">Ten model nie jest już zalecany dla nowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21258-126">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="21258-127">Asynchroniczny wzorzec oparty na zdarzeniach (EAP)</span><span class="sxs-lookup"><span data-stu-id="21258-127">Event-based Asynchronous Pattern (EAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md) | <span data-ttu-id="21258-128">W tym artykule opisano oparty na zdarzeniach modelu starszych zapewniające zachowanie asynchroniczne.</span><span class="sxs-lookup"><span data-stu-id="21258-128">Describes the event-based legacy model for providing asynchronous behavior.</span></span> <span data-ttu-id="21258-129">Ten model nie jest już zalecany dla nowych aplikacji.</span><span class="sxs-lookup"><span data-stu-id="21258-129">This model is no longer recommended for new development.</span></span> |
| [<span data-ttu-id="21258-130">Wzorzec asynchroniczny oparty na zadaniach (TAP)</span><span class="sxs-lookup"><span data-stu-id="21258-130">Task-based Asynchronous Pattern (TAP)</span></span>](../../../docs/standard/asynchronous-programming-patterns/task-based-asynchronous-pattern-tap.md) | <span data-ttu-id="21258-131">W tym artykule opisano nowy asynchroniczny wzorzec oparty na <xref:System.Threading.Tasks> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="21258-131">Describes the new asynchronous pattern based on the <xref:System.Threading.Tasks> namespace.</span></span> <span data-ttu-id="21258-132">Ten model jest zalecane podejście do programowania asynchronicznego w programie .NET Framework 4 i nowsze wersje.</span><span class="sxs-lookup"><span data-stu-id="21258-132">This model is the recommended approach to asynchronous programming in the .NET Framework 4 and later versions.</span></span> |

## <a name="see-also"></a><span data-ttu-id="21258-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="21258-133">See also</span></span>

<span data-ttu-id="21258-134">[Programowanie asynchroniczne w języku C#](~/docs/csharp/async.md) </span><span class="sxs-lookup"><span data-stu-id="21258-134">[Asynchronous programming in C#](~/docs/csharp/async.md) </span></span>  
<span data-ttu-id="21258-135">[Programowanie asynchroniczne w języku F #](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md) </span><span class="sxs-lookup"><span data-stu-id="21258-135">[Async Programming in F#](~/docs/fsharp/tutorials/asynchronous-and-concurrent-programming/async.md) </span></span>  
[<span data-ttu-id="21258-136">Programowanie asynchroniczne z Async i Await (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="21258-136">Asynchronous Programming with Async and Await (Visual Basic)</span></span>](~/docs/visual-basic/programming-guide/concepts/async/index.md)
