---
title: Lock — instrukcja (odwołanie w C#)
description: 'Lock — słowo kluczowe jest używany w wielowątkowości '
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6ed46837482642dfd7e1a96cd120fc18023c5e9f
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753949"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="a5b15-103">Lock — instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a5b15-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="a5b15-104">`lock` — Słowo kluczowe oznacza blok instrukcji jako sekcję krytyczną uzyskując blokadę wykluczania wzajemnego dla danego obiektu, wykonując instrukcję i następnie zwalniając blokadę.</span><span class="sxs-lookup"><span data-stu-id="a5b15-104">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="a5b15-105">Poniższy przykład zawiera `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a5b15-105">The following example includes a `lock` statement.</span></span>

```csharp
class Account
{
    decimal balance;
    private Object thisLock = new Object();

    public void Withdraw(decimal amount)
    {
        lock (thisLock)
        {
            if (amount > balance)
            {
                throw new Exception("Insufficient funds");
            }
            balance -= amount;
        }
    }
}
```

<span data-ttu-id="a5b15-106">Aby uzyskać więcej informacji, zobacz [synchronizacji wątków](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="a5b15-106">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>

## <a name="remarks"></a><span data-ttu-id="a5b15-107">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a5b15-107">Remarks</span></span>

<span data-ttu-id="a5b15-108">`lock` — Słowo kluczowe gwarantuje, że jeden wątek nie wprowadził krytycznych części kodu, podczas gdy inny wątek znajduje się w sekcji krytycznych.</span><span class="sxs-lookup"><span data-stu-id="a5b15-108">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="a5b15-109">Jeśli inny wątek próbuje wprowadzić kod zablokowany, po upływie, zablokować, dopóki obiekt jest zwalniane.</span><span class="sxs-lookup"><span data-stu-id="a5b15-109">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>

<span data-ttu-id="a5b15-110">Sekcja [wątki](../../programming-guide/concepts/threading/index.md) w tym artykule omówiono, wątki.</span><span class="sxs-lookup"><span data-stu-id="a5b15-110">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>

<span data-ttu-id="a5b15-111">`lock` Wywołania — słowo kluczowe <xref:System.Threading.Monitor.Enter%2A> na początku bloku i <xref:System.Threading.Monitor.Exit%2A> na końcu bloku.</span><span class="sxs-lookup"><span data-stu-id="a5b15-111">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="a5b15-112">A <xref:System.Threading.ThreadInterruptedException> jest generowany, jeśli <xref:System.Threading.Thread.Interrupt%2A> przerywa działanie wątku, który oczekuje na wprowadzenie `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a5b15-112">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>

<span data-ttu-id="a5b15-113">Ogólnie rzecz biorąc, należy unikać blokowania na `public` typu lub wystąpień będące poza kontrolą swój kod.</span><span class="sxs-lookup"><span data-stu-id="a5b15-113">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="a5b15-114">Typowe konstrukcje `lock (this)`, `lock (typeof (MyType))`, i `lock ("myLock")` naruszenia niniejszych wytycznych:</span><span class="sxs-lookup"><span data-stu-id="a5b15-114">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>

- <span data-ttu-id="a5b15-115">`lock (this)` jest to problem, jeśli wystąpienie może być publicznie dostępne.</span><span class="sxs-lookup"><span data-stu-id="a5b15-115">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>

- <span data-ttu-id="a5b15-116">`lock (typeof (MyType))` jest to problem, jeśli `MyType` jest publicznie dostępny.</span><span class="sxs-lookup"><span data-stu-id="a5b15-116">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>

- <span data-ttu-id="a5b15-117">`lock("myLock")` jest to problem, ponieważ każdy inny kod proces, korzystając z tych samych parametrach współużytkują ten sam blokady.</span><span class="sxs-lookup"><span data-stu-id="a5b15-117">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>

<span data-ttu-id="a5b15-118">Najlepszym rozwiązaniem jest zdefiniowanie `private` obiektu można zablokować, lub `private static` zmiennej obiektu, aby chronić dane wspólne dla wszystkich wystąpień.</span><span class="sxs-lookup"><span data-stu-id="a5b15-118">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>

<span data-ttu-id="a5b15-119">Nie można użyć [await](await.md) — słowo kluczowe w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a5b15-119">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="example---threads-without-locking"></a><span data-ttu-id="a5b15-120">Przykład — wątki bez blokowania</span><span class="sxs-lookup"><span data-stu-id="a5b15-120">Example - Threads without locking</span></span>

<span data-ttu-id="a5b15-121">Poniższy przykład pokazuje prosty użytkowania wątki bez blokowania w języku C#:</span><span class="sxs-lookup"><span data-stu-id="a5b15-121">The following sample shows a simple use of threads without locking in C#:</span></span>

[!code-csharp[csrefKeywordsFixedLock#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#5)]

## <a name="example---threads-using-locking"></a><span data-ttu-id="a5b15-122">Przykład — wątków przy użyciu blokady</span><span class="sxs-lookup"><span data-stu-id="a5b15-122">Example - Threads using locking</span></span>

<span data-ttu-id="a5b15-123">W poniższym przykładzie użyto wątków i `lock`.</span><span class="sxs-lookup"><span data-stu-id="a5b15-123">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="a5b15-124">Tak długo, jak `lock` instrukcji, blok instrukcji to sekcja krytycznego i `balance` nigdy nie będzie ujemna:</span><span class="sxs-lookup"><span data-stu-id="a5b15-124">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number:</span></span>

[!code-csharp[csrefKeywordsFixedLock#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsFixedLock/CS/csrefKeywordsFixedLock.cs#6)]

## <a name="c-language-specification"></a><span data-ttu-id="a5b15-125">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a5b15-125">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a5b15-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a5b15-126">See also</span></span>

- <xref:System.Reflection.MethodImplAttributes>
- <xref:System.Threading.Mutex>
- <xref:System.Threading.Monitor>
- [<span data-ttu-id="a5b15-127">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a5b15-127">C# Reference</span></span>](../../language-reference/index.md)
- [<span data-ttu-id="a5b15-128">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a5b15-128">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a5b15-129">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="a5b15-129">Threading</span></span>](../../programming-guide/concepts/threading/index.md)
- [<span data-ttu-id="a5b15-130">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a5b15-130">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a5b15-131">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="a5b15-131">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="a5b15-132">Operacje blokowane</span><span class="sxs-lookup"><span data-stu-id="a5b15-132">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)
- [<span data-ttu-id="a5b15-133">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="a5b15-133">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)
- [<span data-ttu-id="a5b15-134">Synchronizacja wątku</span><span class="sxs-lookup"><span data-stu-id="a5b15-134">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)