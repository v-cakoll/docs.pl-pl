---
title: lock statement - odwołanie do języka C#
description: Użyj instrukcji blokady Języka C# do synchronizacji dostępu wątku do zasobu udostępnionego
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 467881dd36c97b6b18b7f31d4e4af25152b0d012
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713386"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="bfdf3-103">lock instrukcji (odwołanie C#)</span><span class="sxs-lookup"><span data-stu-id="bfdf3-103">lock statement (C# reference)</span></span>

<span data-ttu-id="bfdf3-104">Instrukcja `lock` uzyskuje blokady wzajemnego wykluczenia dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="bfdf3-105">Podczas blokady jest wstrzymany, wątek, który posiada blokadę można ponownie nabyć i zwolnić blokady.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="bfdf3-106">Każdy inny wątek jest zablokowany przed uzyskaniem blokady i czeka, aż blokada zostanie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="bfdf3-107">Oświadczenie `lock` ma formę</span><span class="sxs-lookup"><span data-stu-id="bfdf3-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="bfdf3-108">gdzie `x` jest [wyrażenietypu odniesienia](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="bfdf3-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="bfdf3-109">Jest to dokładnie równoznaczne z</span><span class="sxs-lookup"><span data-stu-id="bfdf3-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="bfdf3-110">Ponieważ kod używa [try... finally](try-finally.md) bloku, blokada jest zwalniana, nawet jeśli wyjątek `lock` jest zgłaszany w treści instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="bfdf3-111">Nie można użyć [await operatora](../operators/await.md) w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="remarks"></a><span data-ttu-id="bfdf3-112">Uwagi</span><span class="sxs-lookup"><span data-stu-id="bfdf3-112">Remarks</span></span>

<span data-ttu-id="bfdf3-113">Podczas synchronizowania dostępu wątku do zasobu udostępnionego, zablokować `private readonly object balanceLock = new object();`na wystąpienie obiektu dedykowanego (na przykład) lub innego wystąpienia, które jest mało prawdopodobne, aby być używane jako obiekt blokady przez niepowiązanych części kodu.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="bfdf3-114">Należy unikać używania tego samego wystąpienia obiektu blokady dla różnych zasobów udostępnionych, ponieważ może to spowodować zakleszczenie lub rywalizacji blokady.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="bfdf3-115">W szczególności należy unikać używania następujących obiektów blokady:</span><span class="sxs-lookup"><span data-stu-id="bfdf3-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="bfdf3-116">`this`, ponieważ może być używany przez obiekty wywołujące jako blokada.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="bfdf3-117"><xref:System.Type>przypadkach, ponieważ można je uzyskać przez [operatora typu](../operators/type-testing-and-cast.md#typeof-operator) lub odbicie.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="bfdf3-118">wystąpień ciągów, w tym literały ciągów, ponieważ te mogą być [internowane](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="bfdf3-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

## <a name="example"></a><span data-ttu-id="bfdf3-119">Przykład</span><span class="sxs-lookup"><span data-stu-id="bfdf3-119">Example</span></span>

<span data-ttu-id="bfdf3-120">W poniższym `Account` przykładzie definiuje klasę, która `balance` synchronizuje dostęp do jego `balanceLock` pola prywatnego, blokując w dedykowanym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-120">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="bfdf3-121">Przy użyciu tego samego wystąpienia do `balance` blokowania zapewnia, że pole nie może być `Debit` aktualizowana jednocześnie przez dwa wątki próbuje wywołać lub `Credit` metody jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="bfdf3-121">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="bfdf3-122">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bfdf3-122">C# language specification</span></span>

<span data-ttu-id="bfdf3-123">Aby uzyskać więcej informacji, zobacz sekcję [instrukcja blokady](~/_csharplang/spec/statements.md#the-lock-statement) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="bfdf3-123">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="bfdf3-124">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bfdf3-124">See also</span></span>

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="bfdf3-125">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="bfdf3-125">C# reference</span></span>](../index.md)
- [<span data-ttu-id="bfdf3-126">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="bfdf3-126">C# keywords</span></span>](index.md)
- [<span data-ttu-id="bfdf3-127">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="bfdf3-127">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
