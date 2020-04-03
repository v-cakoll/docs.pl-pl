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
# <a name="lock-statement-c-reference"></a>instrukcja lock (odwołanie do języka C#)

Instrukcja `lock` uzyskuje blokadę wzajemnego wykluczenia dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę. Podczas blokady jest utrzymywany, wątek, który posiada blokadę można ponownie uzyskać i zwolnić blokady. Każdy inny wątek jest zablokowany przed uzyskaniem blokady i czeka, aż blokada zostanie zwolniona.

Oświadczenie `lock` jest w formularzu

```csharp
lock (x)
{
    // Your code...
}
```

gdzie `x` jest wyrażeniem [typu odwołania](reference-types.md). Jest to dokładnie równoważne

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

Ponieważ kod używa [try... finally](try-finally.md) block, blokada jest zwalniana, nawet jeśli `lock` wyjątek jest zgłaszany w treści instrukcji.

Nie można użyć [operatora await](../operators/await.md) w treści `lock` instrukcji.

## <a name="guidelines"></a>Wytyczne

Podczas synchronizowania dostępu wątku do zasobu udostępnionego, zablokować `private readonly object balanceLock = new object();`wystąpienie obiektu dedykowanego (na przykład) lub innego wystąpienia, które jest mało prawdopodobne, aby być używane jako obiekt blokady przez niepowiązanych części kodu. Należy unikać używania tego samego wystąpienia obiektu blokady dla różnych zasobów udostępnionych, ponieważ może to spowodować zakleszczenie lub rywalizację blokady. W szczególności należy unikać używania następujących obiektów jako obiektów blokady:

- `this`, ponieważ może być używany przez dzwoniących jako blokada.
- <xref:System.Type>przypadków, ponieważ mogą być uzyskane przez [typeof](../operators/type-testing-and-cast.md#typeof-operator) operatora lub odbicia.
- wystąpień ciągów, w tym literałów ciągów, ponieważ mogą być [internowane](/dotnet/api/system.string.intern#remarks).

Przytrzymaj blokadę przez jak najkrótszy czas, aby zmniejszyć rywalizację o blokadę.

## <a name="example"></a>Przykład

Poniższy przykład definiuje `Account` klasę, która synchronizuje `balance` dostęp do swojego `balanceLock` pola prywatnego przez zablokowanie w dedykowanym wystąpieniu. Przy użyciu tego samego wystąpienia do `balance` blokowania zapewnia, że pole nie może być `Debit` `Credit` aktualizowana jednocześnie przez dwa wątki próby wywołania lub metody jednocześnie.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję instrukcji blokady](~/_csharplang/spec/statements.md#the-lock-statement) [specyfikacji języka języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Słowa kluczowe języka C#](index.md)
- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [Przegląd elementów podstawowych synchronizacji](../../../standard/threading/overview-of-synchronization-primitives.md)
