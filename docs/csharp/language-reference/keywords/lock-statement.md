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
# <a name="lock-statement-c-reference"></a>Lock — instrukcja (odwołanie w C#)

`lock` Instrukcji uzyskuje blokadę wykluczania wzajemnego dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę. Gdy blokada jest używana, wątek, który posiada blokadę ponownie uzyskać i zwalnia blokadę. Inne wątku jest zablokowana dla rezygnację z włączenia blokady i czeka, aż blokada jest zwalniana.

`lock` Instrukcja jest formularza

```csharp
lock (x)
{
    // Your code...
}
```

gdzie `x` to wyrażenie [odwołania do typu](reference-types.md). Jest to równoważne dokładnie

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

Ponieważ kod używa [try... finally](try-finally.md) bloku, blokada jest zwalniany, nawet wtedy, gdy wyjątek jest zgłaszany w treści `lock` instrukcji.

Nie można użyć [await](await.md) — słowo kluczowe w treści `lock` instrukcji.

## <a name="remarks"></a>Uwagi

Podczas synchronizowania wątku dostęp do udostępnionego zasobu blokady w wystąpieniu obiektu dedykowane (na przykład `private readonly object balanceLock = new object();`) lub innego wystąpienia, który prawdopodobnie nie ma być używany jako obiekt blokady przez niezwiązanych części kodu. Należy unikać tego samego wystąpienia obiektu blokady dla różnych zasobów udostępnionych, ponieważ może to spowodować zakleszczenia lub lock rywalizacji o zasoby. W szczególności należy unikać

- `this` (może być używana przez obiekty wywołujące jako blokady),
- <xref:System.Type> wystąpienia (może otrzymać [typeof](typeof.md) operatora lub odbicie),
- wystąpienia ciągu, w tym literałów ciągów

jako obiekty blokady.

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano `Account` klasę, która synchronizuje dostęp do jego prywatny `balance` pole blokowania na dedykowany `balanceLock` wystąpienia. Przy użyciu tego samego wystąpienia dla blokowania masz pewność, że `balance` nie można zaktualizować pola jednocześnie przez dwa wątki, próba wywołania `Debit` lub `Credit` metod jednocześnie.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Słowa kluczowe instrukcji](statement-keywords.md)
- [Operacje blokowane](../../../standard/threading/interlocked-operations.md)
- [Przegląd elementów podstawowych synchronizacji](../../../standard/threading/overview-of-synchronization-primitives.md)