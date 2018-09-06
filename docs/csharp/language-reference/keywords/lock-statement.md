---
title: Lock — instrukcja (odwołanie w C#)
description: Użyj instrukcji lock języka C# do synchronizowania dostępu wątku do udostępnionego zasobu
ms.date: 08/28/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2b6fbfb2f81d7745c4effb9ea0087f34cc872a6c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43858359"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="04885-103">Lock — instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="04885-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="04885-104">`lock` Instrukcji uzyskuje blokadę wykluczania wzajemnego dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę.</span><span class="sxs-lookup"><span data-stu-id="04885-104">The `lock` statement obtains the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="04885-105">Gdy blokada jest używana, wątek, który posiada blokadę ponownie uzyskać i zwalnia blokadę.</span><span class="sxs-lookup"><span data-stu-id="04885-105">While a lock is held, the thread that holds the lock can again obtain and release the lock.</span></span> <span data-ttu-id="04885-106">Inne wątku jest zablokowana dla rezygnację z włączenia blokady i czeka, aż blokada jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="04885-106">Any other thread is blocked from obtaining the lock and waits until the lock is released.</span></span>

<span data-ttu-id="04885-107">`lock` Instrukcja jest formularza</span><span class="sxs-lookup"><span data-stu-id="04885-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="04885-108">gdzie `x` to wyrażenie [odwołania do typu](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="04885-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="04885-109">Jest to równoważne dokładnie</span><span class="sxs-lookup"><span data-stu-id="04885-109">It's precisely equivalent to</span></span>

```csharp
object __lockObj = x;
bool __lockWasTaken = false;
try
{
    System.Threading.Monitor.Enter(__lockObj, ref __lockWasTaken);
    // Your code...
}
finally
{
    if (__lockWasTaken) System.Threading.Monitor.Exit(__lockObj);
}
```

<span data-ttu-id="04885-110">Ponieważ kod używa [try... finally](try-finally.md) bloku, blokada jest zwalniany, nawet wtedy, gdy wyjątek jest zgłaszany w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="04885-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="04885-111">Nie można użyć [await](await.md) — słowo kluczowe w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="04885-111">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="04885-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="04885-112">Remarks</span></span>

<span data-ttu-id="04885-113">Podczas synchronizowania wątku dostęp do udostępnionego zasobu blokady w wystąpieniu obiektu dedykowane (na przykład `private readonly object balanceLock = new object();`) lub innego wystąpienia, który prawdopodobnie nie ma być używany jako obiekt blokady przez niezwiązanych części kodu.</span><span class="sxs-lookup"><span data-stu-id="04885-113">When you synchronize thread access to shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="04885-114">Należy unikać tego samego wystąpienia obiektu blokady dla różnych zasobów udostępnionych, ponieważ może to spowodować zakleszczenia lub lock rywalizacji o zasoby.</span><span class="sxs-lookup"><span data-stu-id="04885-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="04885-115">W szczególności należy unikać</span><span class="sxs-lookup"><span data-stu-id="04885-115">In particular, avoid using</span></span>

- <span data-ttu-id="04885-116">`this` (może być używana przez obiekty wywołujące jako blokady),</span><span class="sxs-lookup"><span data-stu-id="04885-116">`this` (might be used by the callers as a lock),</span></span>
- <span data-ttu-id="04885-117"><xref:System.Type> wystąpienia (może otrzymać [typeof](typeof.md) operatora lub odbicie),</span><span class="sxs-lookup"><span data-stu-id="04885-117"><xref:System.Type> instances (might be obtained by the [typeof](typeof.md) operator or reflection),</span></span>
- <span data-ttu-id="04885-118">wystąpienia ciągu, w tym literałów ciągów</span><span class="sxs-lookup"><span data-stu-id="04885-118">string instances, including string literals,</span></span>

<span data-ttu-id="04885-119">jako obiekty blokady.</span><span class="sxs-lookup"><span data-stu-id="04885-119">as lock objects.</span></span>

## <a name="example"></a><span data-ttu-id="04885-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="04885-120">Example</span></span>

<span data-ttu-id="04885-121">W poniższym przykładzie zdefiniowano `Account` klasę, która synchronizuje dostęp do jego prywatny `balance` pole blokowania na dedykowany `balanceLock` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="04885-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="04885-122">Przy użyciu tego samego wystąpienia dla blokowania masz pewność, że `balance` nie można zaktualizować pola jednocześnie przez dwa wątki, próba wywołania `Debit` lub `Credit` metod jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="04885-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="04885-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="04885-123">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="04885-124">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="04885-124">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="04885-125">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="04885-125">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="04885-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="04885-126">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="04885-127">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="04885-127">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="04885-128">Operacje blokowane</span><span class="sxs-lookup"><span data-stu-id="04885-128">Interlocked operations</span></span>](../../../standard/threading/interlocked-operations.md)
- [<span data-ttu-id="04885-129">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="04885-129">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)