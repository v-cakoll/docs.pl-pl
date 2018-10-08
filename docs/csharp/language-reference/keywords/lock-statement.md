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
ms.openlocfilehash: 802f447e1ae01020fa80fa3048e3783ea24db3d3
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/08/2018
ms.locfileid: "48850104"
---
# <a name="lock-statement-c-reference"></a>Lock — instrukcja (odwołanie w C#)

`lock` Instrukcji uzyskuje blokadę wykluczania wzajemnego dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę. Dopóki blokada jest utrzymywana, wątek, który posiada blokadę można ponownie pobrać i zwalnia blokadę. Inne wątku Zablokowano pobieranie blokady i czeka, aż blokada jest zwalniana.

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

Podczas synchronizowania dostępu wątków we współdzielonym zasobie blokady w wystąpieniu obiektu dedykowane (na przykład `private readonly object balanceLock = new object();`) lub innego wystąpienia, który prawdopodobnie nie ma być używany jako obiekt blokady przez niezwiązanych części kodu. Należy unikać tego samego wystąpienia obiektu blokady dla różnych zasobów udostępnionych, ponieważ może to spowodować zakleszczenia lub lock rywalizacji o zasoby. W szczególności należy unikać następujące jako obiekty blokady:

- `this`, jak mogą być używane przez obiekty wywołujące jako blokadę.
- <xref:System.Type> wystąpienia jako te, można uzyskać przez [typeof](typeof.md) operatora lub odbicia.
- ciąg wystąpienia, w tym Literały ciągu, ponieważ te mogą być [interned](/dotnet/api/system.string.intern#remarks).

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