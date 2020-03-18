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
# <a name="lock-statement-c-reference"></a>lock instrukcji (odwołanie C#)

Instrukcja `lock` uzyskuje blokady wzajemnego wykluczenia dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę. Podczas blokady jest wstrzymany, wątek, który posiada blokadę można ponownie nabyć i zwolnić blokady. Każdy inny wątek jest zablokowany przed uzyskaniem blokady i czeka, aż blokada zostanie zwolniona.

Oświadczenie `lock` ma formę

```csharp
lock (x)
{
    // Your code...
}
```

gdzie `x` jest [wyrażenietypu odniesienia](reference-types.md). Jest to dokładnie równoznaczne z

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

Ponieważ kod używa [try... finally](try-finally.md) bloku, blokada jest zwalniana, nawet jeśli wyjątek `lock` jest zgłaszany w treści instrukcji.

Nie można użyć [await operatora](../operators/await.md) w treści `lock` instrukcji.

## <a name="remarks"></a>Uwagi

Podczas synchronizowania dostępu wątku do zasobu udostępnionego, zablokować `private readonly object balanceLock = new object();`na wystąpienie obiektu dedykowanego (na przykład) lub innego wystąpienia, które jest mało prawdopodobne, aby być używane jako obiekt blokady przez niepowiązanych części kodu. Należy unikać używania tego samego wystąpienia obiektu blokady dla różnych zasobów udostępnionych, ponieważ może to spowodować zakleszczenie lub rywalizacji blokady. W szczególności należy unikać używania następujących obiektów blokady:

- `this`, ponieważ może być używany przez obiekty wywołujące jako blokada.
- <xref:System.Type>przypadkach, ponieważ można je uzyskać przez [operatora typu](../operators/type-testing-and-cast.md#typeof-operator) lub odbicie.
- wystąpień ciągów, w tym literały ciągów, ponieważ te mogą być [internowane](/dotnet/api/system.string.intern#remarks).

## <a name="example"></a>Przykład

W poniższym `Account` przykładzie definiuje klasę, która `balance` synchronizuje dostęp do jego `balanceLock` pola prywatnego, blokując w dedykowanym wystąpieniu. Przy użyciu tego samego wystąpienia do `balance` blokowania zapewnia, że pole nie może być `Debit` aktualizowana jednocześnie przez dwa wątki próbuje wywołać lub `Credit` metody jednocześnie.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [instrukcja blokady](~/_csharplang/spec/statements.md#the-lock-statement) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Przegląd elementów podstawowych synchronizacji](../../../standard/threading/overview-of-synchronization-primitives.md)
