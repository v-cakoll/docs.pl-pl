---
title: lock — Instrukcja (odwołanie w C#)
description: Używanie instrukcji blokowania języka C# do synchronizowania dostępu do wątku z udostępnionym zasobem
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 6e9a6975977588ba7692c925d7940cd2ec26671f
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406693"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="992bc-103">lock — Instrukcja (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="992bc-103">lock statement (C# reference)</span></span>

<span data-ttu-id="992bc-104">`lock`Instrukcja uzyskuje blokadę wykluczania wzajemnego dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę.</span><span class="sxs-lookup"><span data-stu-id="992bc-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="992bc-105">Gdy blokada jest utrzymywana, wątek, który przechowuje blokadę, może ponownie uzyskać i zwolnić blokadę.</span><span class="sxs-lookup"><span data-stu-id="992bc-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="992bc-106">Każdy inny wątek jest blokowany przed uzyskaniem blokady i czeka na zwolnienie blokady.</span><span class="sxs-lookup"><span data-stu-id="992bc-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="992bc-107">`lock`Instrukcja ma postać</span><span class="sxs-lookup"><span data-stu-id="992bc-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="992bc-108">gdzie `x` jest wyrażeniem [typu odwołania](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="992bc-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="992bc-109">Jest to dokładnie równoważne</span><span class="sxs-lookup"><span data-stu-id="992bc-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="992bc-110">Ponieważ kod używa [try... blok finally](try-finally.md) jest uwalniany nawet wtedy, gdy wyjątek jest zgłaszany w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="992bc-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="992bc-111">Nie można użyć [operatora await](../operators/await.md) w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="992bc-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="guidelines"></a><span data-ttu-id="992bc-112">Wytyczne</span><span class="sxs-lookup"><span data-stu-id="992bc-112">Guidelines</span></span>

<span data-ttu-id="992bc-113">Podczas synchronizowania dostępu do wątku z udostępnionym zasobem należy zablokować wystąpienie obiektu dedykowanego (na przykład `private readonly object balanceLock = new object();` ) lub inne wystąpienie, które prawdopodobnie nie będzie używane jako obiekt blokady przez niepowiązane części kodu.</span><span class="sxs-lookup"><span data-stu-id="992bc-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="992bc-114">Należy unikać używania tego samego wystąpienia obiektu blokady dla różnych udostępnionych zasobów, ponieważ może to spowodować zakleszczenie lub zablokowanie rywalizacji.</span><span class="sxs-lookup"><span data-stu-id="992bc-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="992bc-115">W szczególności należy unikać używania następujących funkcji jako obiektów blokowania:</span><span class="sxs-lookup"><span data-stu-id="992bc-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="992bc-116">`this`, ponieważ mogą one być używane przez wywołujących jako blokadę.</span><span class="sxs-lookup"><span data-stu-id="992bc-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="992bc-117"><xref:System.Type>wystąpienia, ponieważ mogą być uzyskane przez operatora lub odbicie [typeof](../operators/type-testing-and-cast.md#typeof-operator) .</span><span class="sxs-lookup"><span data-stu-id="992bc-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="992bc-118">wystąpienia ciągów, w tym literały ciągów, ponieważ mogą być [internice](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="992bc-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

<span data-ttu-id="992bc-119">Przytrzymaj blokadę przez krótki czas, jak to możliwe, aby zmniejszyć rywalizację o blokady.</span><span class="sxs-lookup"><span data-stu-id="992bc-119">Hold a lock for as short time as possible to reduce lock contention.</span></span>

## <a name="example"></a><span data-ttu-id="992bc-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="992bc-120">Example</span></span>

<span data-ttu-id="992bc-121">W poniższym przykładzie zdefiniowano `Account` klasę, która synchronizuje dostęp do jego `balance` pola prywatnego przez zablokowanie na dedykowanym `balanceLock` wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="992bc-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="992bc-122">Użycie tego samego wystąpienia do blokowania gwarantuje, że `balance` nie można jednocześnie aktualizować pola przez dwa wątki próbujące wywołać `Debit` `Credit` metody lub.</span><span class="sxs-lookup"><span data-stu-id="992bc-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](snippets/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="992bc-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="992bc-123">C# language specification</span></span>

<span data-ttu-id="992bc-124">Aby uzyskać więcej informacji, zobacz sekcję [blokowanie instrukcji](~/_csharplang/spec/statements.md#the-lock-statement) w [specyfikacji języka C#](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="992bc-124">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="992bc-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="992bc-125">See also</span></span>

- [<span data-ttu-id="992bc-126">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="992bc-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="992bc-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="992bc-127">C# keywords</span></span>](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="992bc-128">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="992bc-128">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
