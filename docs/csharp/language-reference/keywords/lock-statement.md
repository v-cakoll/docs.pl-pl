---
title: instrukcja lock - odwołanie do języka C#
description: Instrukcja blokady języka C# służy do synchronizowania dostępu wątku do zasobu udostępnionego
ms.date: 04/02/2020
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 2f2d42ae02a07a5e1b82cefd004f4d03b2a16dff
ms.sourcegitcommit: 1c1a1f9ec0bd1efb3040d86a79f7ee94e207cca5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/03/2020
ms.locfileid: "80635379"
---
# <a name="lock-statement-c-reference"></a><span data-ttu-id="60537-103">instrukcja lock (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="60537-103">lock statement (C# reference)</span></span>

<span data-ttu-id="60537-104">Instrukcja `lock` uzyskuje blokadę wzajemnego wykluczenia dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę.</span><span class="sxs-lookup"><span data-stu-id="60537-104">The `lock` statement acquires the mutual-exclusion lock for a given object, executes a statement block, and then releases the lock.</span></span> <span data-ttu-id="60537-105">Podczas blokady jest utrzymywany, wątek, który posiada blokadę można ponownie uzyskać i zwolnić blokady.</span><span class="sxs-lookup"><span data-stu-id="60537-105">While a lock is held, the thread that holds the lock can again acquire and release the lock.</span></span> <span data-ttu-id="60537-106">Każdy inny wątek jest zablokowany przed uzyskaniem blokady i czeka, aż blokada zostanie zwolniona.</span><span class="sxs-lookup"><span data-stu-id="60537-106">Any other thread is blocked from acquiring the lock and waits until the lock is released.</span></span>

<span data-ttu-id="60537-107">Oświadczenie `lock` jest w formularzu</span><span class="sxs-lookup"><span data-stu-id="60537-107">The `lock` statement is of the form</span></span>

```csharp
lock (x)
{
    // Your code...
}
```

<span data-ttu-id="60537-108">gdzie `x` jest wyrażeniem [typu odwołania](reference-types.md).</span><span class="sxs-lookup"><span data-stu-id="60537-108">where `x` is an expression of a [reference type](reference-types.md).</span></span> <span data-ttu-id="60537-109">Jest to dokładnie równoważne</span><span class="sxs-lookup"><span data-stu-id="60537-109">It's precisely equivalent to</span></span>

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

<span data-ttu-id="60537-110">Ponieważ kod używa [try... finally](try-finally.md) block, blokada jest zwalniana, nawet jeśli `lock` wyjątek jest zgłaszany w treści instrukcji.</span><span class="sxs-lookup"><span data-stu-id="60537-110">Since the code uses a [try...finally](try-finally.md) block, the lock is released even if an exception is thrown within the body of a `lock` statement.</span></span>

<span data-ttu-id="60537-111">Nie można użyć [operatora await](../operators/await.md) w treści `lock` instrukcji.</span><span class="sxs-lookup"><span data-stu-id="60537-111">You can't use the [await operator](../operators/await.md) in the body of a `lock` statement.</span></span>

## <a name="guidelines"></a><span data-ttu-id="60537-112">Wytyczne</span><span class="sxs-lookup"><span data-stu-id="60537-112">Guidelines</span></span>

<span data-ttu-id="60537-113">Podczas synchronizowania dostępu wątku do zasobu udostępnionego, zablokować `private readonly object balanceLock = new object();`wystąpienie obiektu dedykowanego (na przykład) lub innego wystąpienia, które jest mało prawdopodobne, aby być używane jako obiekt blokady przez niepowiązanych części kodu.</span><span class="sxs-lookup"><span data-stu-id="60537-113">When you synchronize thread access to a shared resource, lock on a dedicated object instance (for example, `private readonly object balanceLock = new object();`) or another instance that is unlikely to be used as a lock object by unrelated parts of the code.</span></span> <span data-ttu-id="60537-114">Należy unikać używania tego samego wystąpienia obiektu blokady dla różnych zasobów udostępnionych, ponieważ może to spowodować zakleszczenie lub rywalizację blokady.</span><span class="sxs-lookup"><span data-stu-id="60537-114">Avoid using the same lock object instance for different shared resources, as it might result in deadlock or lock contention.</span></span> <span data-ttu-id="60537-115">W szczególności należy unikać używania następujących obiektów jako obiektów blokady:</span><span class="sxs-lookup"><span data-stu-id="60537-115">In particular, avoid using the following as lock objects:</span></span>

- <span data-ttu-id="60537-116">`this`, ponieważ może być używany przez dzwoniących jako blokada.</span><span class="sxs-lookup"><span data-stu-id="60537-116">`this`, as it might be used by the callers as a lock.</span></span>
- <span data-ttu-id="60537-117"><xref:System.Type>przypadków, ponieważ mogą być uzyskane przez [typeof](../operators/type-testing-and-cast.md#typeof-operator) operatora lub odbicia.</span><span class="sxs-lookup"><span data-stu-id="60537-117"><xref:System.Type> instances, as those might be obtained by the [typeof](../operators/type-testing-and-cast.md#typeof-operator) operator or reflection.</span></span>
- <span data-ttu-id="60537-118">wystąpień ciągów, w tym literałów ciągów, ponieważ mogą być [internowane](/dotnet/api/system.string.intern#remarks).</span><span class="sxs-lookup"><span data-stu-id="60537-118">string instances, including string literals, as those might be [interned](/dotnet/api/system.string.intern#remarks).</span></span>

<span data-ttu-id="60537-119">Przytrzymaj blokadę przez jak najkrótszy czas, aby zmniejszyć rywalizację o blokadę.</span><span class="sxs-lookup"><span data-stu-id="60537-119">Hold a lock for as short time as possible to reduce lock contention.</span></span>

## <a name="example"></a><span data-ttu-id="60537-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="60537-120">Example</span></span>

<span data-ttu-id="60537-121">Poniższy przykład definiuje `Account` klasę, która synchronizuje `balance` dostęp do swojego `balanceLock` pola prywatnego przez zablokowanie w dedykowanym wystąpieniu.</span><span class="sxs-lookup"><span data-stu-id="60537-121">The following example defines an `Account` class that synchronizes access to its private `balance` field by locking on a dedicated `balanceLock` instance.</span></span> <span data-ttu-id="60537-122">Przy użyciu tego samego wystąpienia do `balance` blokowania zapewnia, że pole nie może być `Debit` `Credit` aktualizowana jednocześnie przez dwa wątki próby wywołania lub metody jednocześnie.</span><span class="sxs-lookup"><span data-stu-id="60537-122">Using the same instance for locking ensures that the `balance` field cannot be updated simultaneously by two threads attempting to call the `Debit` or `Credit` methods simultaneously.</span></span>

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a><span data-ttu-id="60537-123">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="60537-123">C# language specification</span></span>

<span data-ttu-id="60537-124">Aby uzyskać więcej informacji, zobacz [sekcję instrukcji blokady](~/_csharplang/spec/statements.md#the-lock-statement) [specyfikacji języka języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="60537-124">For more information, see [The lock statement](~/_csharplang/spec/statements.md#the-lock-statement) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="60537-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="60537-125">See also</span></span>

- [<span data-ttu-id="60537-126">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="60537-126">C# reference</span></span>](../index.md)
- [<span data-ttu-id="60537-127">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="60537-127">C# keywords</span></span>](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [<span data-ttu-id="60537-128">Przegląd elementów podstawowych synchronizacji</span><span class="sxs-lookup"><span data-stu-id="60537-128">Overview of synchronization primitives</span></span>](../../../standard/threading/overview-of-synchronization-primitives.md)
