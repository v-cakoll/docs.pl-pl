---
title: lock — Instrukcja (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2ce870e8caa67d780ce603a6f1dbcc7cd303b842
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33274222"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="03617-102">lock — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="03617-102">lock Statement (C# Reference)</span></span>
<span data-ttu-id="03617-103">`lock` — Słowo kluczowe oznacza blok instrukcji jako sekcja krytyczna uzyskania wzajemnego wykluczeń dla danego obiektu, wykonywania instrukcji, a następnie zwolnienie blokady.</span><span class="sxs-lookup"><span data-stu-id="03617-103">The `lock` keyword marks a statement block as a critical section by obtaining the mutual-exclusion lock for a given object, executing a statement, and then releasing the lock.</span></span> <span data-ttu-id="03617-104">Poniższy przykład zawiera `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="03617-104">The following example includes a `lock` statement.</span></span>  
  
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
  
 <span data-ttu-id="03617-105">Aby uzyskać więcej informacji, zobacz [wątku synchronizacji](../../programming-guide/concepts/threading/thread-synchronization.md).</span><span class="sxs-lookup"><span data-stu-id="03617-105">For more information, see [Thread Synchronization](../../programming-guide/concepts/threading/thread-synchronization.md).</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="03617-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="03617-106">Remarks</span></span>  
 <span data-ttu-id="03617-107">`lock` — Słowo kluczowe gwarantuje, że jeden wątek nie wprowadził krytyczne sekcji kodu podczas inny wątek znajduje się w sekcji krytyczne.</span><span class="sxs-lookup"><span data-stu-id="03617-107">The `lock` keyword ensures that one thread does not enter a critical section of code while another thread is in the critical section.</span></span> <span data-ttu-id="03617-108">Jeśli inny wątek próbował wprowadzić kod zablokowany, będzie czekać, blokowanie, dopóki nie zostanie zwolniony obiektu.</span><span class="sxs-lookup"><span data-stu-id="03617-108">If another thread tries to enter a locked code, it will wait, block, until the object is released.</span></span>  
  
 <span data-ttu-id="03617-109">Sekcja [wątki](../../programming-guide/concepts/threading/index.md) omówiono wątków.</span><span class="sxs-lookup"><span data-stu-id="03617-109">The section [Threading](../../programming-guide/concepts/threading/index.md) discusses threading.</span></span>  
  
 <span data-ttu-id="03617-110">`lock` Wywołania — słowo kluczowe <xref:System.Threading.Monitor.Enter%2A> na początku bloku i <xref:System.Threading.Monitor.Exit%2A> na końcu bloku.</span><span class="sxs-lookup"><span data-stu-id="03617-110">The `lock` keyword calls <xref:System.Threading.Monitor.Enter%2A> at the start of the block and <xref:System.Threading.Monitor.Exit%2A> at the end of the block.</span></span> <span data-ttu-id="03617-111">A <xref:System.Threading.ThreadInterruptedException> jest generowany, jeśli <xref:System.Threading.Thread.Interrupt%2A> przerwań wątku, który oczekuje na wprowadzenie `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="03617-111">A <xref:System.Threading.ThreadInterruptedException> is thrown if <xref:System.Threading.Thread.Interrupt%2A> interrupts a thread that is waiting to enter a `lock` statement.</span></span>  
  
 <span data-ttu-id="03617-112">Ogólnie rzecz biorąc, należy unikać blokowania na `public` typu lub wystąpień poza swój kod sterowania.</span><span class="sxs-lookup"><span data-stu-id="03617-112">In general, avoid locking on a `public` type, or instances beyond your code's control.</span></span> <span data-ttu-id="03617-113">Typowe konstrukcje `lock (this)`, `lock (typeof (MyType))`, i `lock ("myLock")` narusza niniejsze wytyczne:</span><span class="sxs-lookup"><span data-stu-id="03617-113">The common constructs `lock (this)`, `lock (typeof (MyType))`, and `lock ("myLock")` violate this guideline:</span></span>  
  
-   <span data-ttu-id="03617-114">`lock (this)` jest to problem, jeśli wystąpienie jest dostępny publicznie.</span><span class="sxs-lookup"><span data-stu-id="03617-114">`lock (this)` is a problem if the instance can be accessed publicly.</span></span>  
  
-   <span data-ttu-id="03617-115">`lock (typeof (MyType))` jest problem, jeśli `MyType` jest dostępny publicznie.</span><span class="sxs-lookup"><span data-stu-id="03617-115">`lock (typeof (MyType))` is a problem if `MyType` is publicly accessible.</span></span>  
  
-   <span data-ttu-id="03617-116">`lock("myLock")` jest to problem, ponieważ innego kodu w procesie przy użyciu tych samych parametrach współużytkują tego samego blokady.</span><span class="sxs-lookup"><span data-stu-id="03617-116">`lock("myLock")` is a problem because any other code in the process using the same string, will share the same lock.</span></span>  
  
 <span data-ttu-id="03617-117">Najlepszym rozwiązaniem jest określenie `private` obiekt, aby zablokować, lub `private static` zmienna obiektu, aby chronić dane wspólne dla wszystkich wystąpień.</span><span class="sxs-lookup"><span data-stu-id="03617-117">Best practice is to define a `private` object to lock on, or a `private static` object variable to protect data common to all instances.</span></span>  
  
 <span data-ttu-id="03617-118">Nie można użyć [await](../../../csharp/language-reference/keywords/await.md) — słowo kluczowe w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="03617-118">You can't use the [await](../../../csharp/language-reference/keywords/await.md) keyword in the body of a `lock` statement.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03617-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="03617-119">Example</span></span>  
 <span data-ttu-id="03617-120">Poniższy przykład zawiera proste używanie wątków bez blokowania w języku C#.</span><span class="sxs-lookup"><span data-stu-id="03617-120">The following sample shows a simple use of threads without locking in C#.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="03617-121">Przykład</span><span class="sxs-lookup"><span data-stu-id="03617-121">Example</span></span>  
 <span data-ttu-id="03617-122">W poniższym przykładzie użyto wątków i `lock`.</span><span class="sxs-lookup"><span data-stu-id="03617-122">The following sample uses threads and `lock`.</span></span> <span data-ttu-id="03617-123">Tak długo, jak `lock` instrukcji, blok instrukcji jest sekcja krytyczna i `balance` nigdy nie staną się liczbą ujemną.</span><span class="sxs-lookup"><span data-stu-id="03617-123">As long as the `lock` statement is present, the statement block is a critical section and `balance` will never become a negative number.</span></span>  
  
 [!code-csharp[csrefKeywordsFixedLock#6](../../../csharp/language-reference/keywords/codesnippet/CSharp/lock-statement_2.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="03617-124">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="03617-124">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="03617-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="03617-125">See Also</span></span>  
 <xref:System.Reflection.MethodImplAttributes>  
 <xref:System.Threading.Mutex>  
 [<span data-ttu-id="03617-126">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="03617-126">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="03617-127">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="03617-127">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="03617-128">Wątkowość</span><span class="sxs-lookup"><span data-stu-id="03617-128">Threading</span></span>](../../programming-guide/concepts/threading/index.md)  
 [<span data-ttu-id="03617-129">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="03617-129">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="03617-130">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="03617-130">Statement Keywords</span></span>](../../../csharp/language-reference/keywords/statement-keywords.md)  
 <xref:System.Threading.Monitor>  
 [<span data-ttu-id="03617-131">Operacje blokowane</span><span class="sxs-lookup"><span data-stu-id="03617-131">Interlocked Operations</span></span>](../../../standard/threading/interlocked-operations.md)  
 [<span data-ttu-id="03617-132">AutoResetEvent</span><span class="sxs-lookup"><span data-stu-id="03617-132">AutoResetEvent</span></span>](../../../standard/threading/autoresetevent.md)  
 [<span data-ttu-id="03617-133">Synchronizacja wątku</span><span class="sxs-lookup"><span data-stu-id="03617-133">Thread Synchronization</span></span>](../../programming-guide/concepts/threading/thread-synchronization.md)
