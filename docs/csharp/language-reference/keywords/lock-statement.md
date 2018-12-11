---
title: Lock — instrukcja (odwołanie w C#)
description: Umożliwia synchronizację dostępu wątków we współdzielonym zasobie przez instrukcję lock języka C#
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: cacc703e40f268c1dbca4174dc866ecae83cbd6c
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53125759"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="a1ad4-103">Lock — instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a1ad4-103">lock statement (C# Reference)</span></span>

<span data-ttu-id="a1ad4-104">`lock` Instrukcji uzyskuje blokadę wykluczania wzajemnego dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="a1ad4-105">Dopóki blokada jest utrzymywana, wątek, który posiada blokadę można ponownie pobrać i zwalnia blokadę.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="a1ad4-106">Inne wątku Zablokowano pobieranie blokady i czeka, aż blokada jest zwalniana.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="a1ad4-107">`lock` Instrukcja jest formularza</span><span class="sxs-lookup"><span data-stu-id="a1ad4-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="a1ad4-108">gdzie `x` to wyrażenie [odwołania do typu](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="a1ad4-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="a1ad4-109">Jest to równoważne dokładnie</span><span class="sxs-lookup"><span data-stu-id="a1ad4-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="a1ad4-110">Ponieważ kod używa [try... finally](try-finally.md) bloku, blokada jest zwalniany, nawet wtedy, gdy wyjątek jest zgłaszany w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="a1ad4-111">Nie można użyć [await](await.md) — słowo kluczowe w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-111">You can't use the [await](await.md) keyword in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="a1ad4-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="a1ad4-112">Remarks</span></span>

<span data-ttu-id="a1ad4-113">Podczas synchronizowania dostępu wątków we współdzielonym zasobie blokady w wystąpieniu obiektu dedykowane (na przykład `private readonly object balanceLock = new object();`) lub innego wystąpienia, który prawdopodobnie nie ma być używany jako obiekt blokady przez niezwiązanych części kodu.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="a1ad4-114">Należy unikać tego samego wystąpienia obiektu blokady dla różnych zasobów udostępnionych, ponieważ może to spowodować zakleszczenia lub lock rywalizacji o zasoby.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="a1ad4-115">W szczególności należy unikać następujące jako obiekty blokady:</span><span class="sxs-lookup"><span data-stu-id="a1ad4-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="a1ad4-116">`this`, jak mogą być używane przez obiekty wywołujące jako blokadę.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="a1ad4-117"><xref:System.Type> wystąpienia jako te, można uzyskać przez [typeof](typeof.md) operatora lub odbicia.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-117"><xref:System.Type> instances, as those might be obtained by the [typeof](typeof.md) operator or reflection.</span></span>
- <span data-ttu-id="a1ad4-118">ciąg wystąpienia, w tym Literały ciągu, ponieważ te mogą być [interned](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="a1ad4-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

## <a name="example"></a><span data-ttu-id="a1ad4-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="a1ad4-119">Example</span></span>

<span data-ttu-id="a1ad4-120">W poniższym przykładzie zdefiniowano `Account` klasę, która synchronizuje dostęp do jego prywatny `balance` pole blokowania na dedykowany `balanceLock` wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-120">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="a1ad4-121">Przy użyciu tego samego wystąpienia dla blokowania masz pewność, że `balance` nie można zaktualizować pola jednocześnie przez dwa wątki, próba wywołania `Debit` lub `Credit` metod jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="a1ad4-121">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="a1ad4-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a1ad4-122">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="a1ad4-123">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a1ad4-123">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="a1ad4-124">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a1ad4-124">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a1ad4-125">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a1ad4-125">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a1ad4-126">Słowa kluczowe instrukcji</span><span class="sxs-lookup"><span data-stu-id="a1ad4-126">Statement Keywords</span></span>](statement-keywords.md)
- [<span data-ttu-id="a1ad4-127">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="a1ad4-127">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)