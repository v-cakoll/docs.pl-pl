---
title: Lock — instrukcja C# — odwołanie
description: Używanie instrukcji C# Lock do synchronizowania dostępu do wątku z udostępnionym zasobem
ms.date: 10/01/2018
f1_keywords:
- lock_CSharpKeyword
- lock
helpviewer_keywords:
- lock keyword [C#]
ms.assetid: 656da1a4-707e-4ef6-9c6e-6d13b646af42
ms.openlocfilehash: 467881dd36c97b6b18b7f31d4e4af25152b0d012
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713386"
---
# <a name="lock-statement-c-reference"></a>Lock — instrukcjaC# (odwołanie)

Instrukcja `lock` uzyskuje blokadę wzajemnego wykluczania dla danego obiektu, wykonuje blok instrukcji, a następnie zwalnia blokadę. Gdy blokada jest utrzymywana, wątek, który przechowuje blokadę, może ponownie uzyskać i zwolnić blokadę. Każdy inny wątek jest blokowany przed uzyskaniem blokady i czeka na zwolnienie blokady.

Instrukcja `lock` ma postać

```csharp
lock (x)
{
    // Your code...
}
```

gdzie `x` jest wyrażeniem [typu referencyjnego](reference-types.md). Jest to dokładnie równoważne

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

Ponieważ kod używa [try... blok finally](try-finally.md) jest uwalniany nawet wtedy, gdy wyjątek jest zgłaszany w treści instrukcji `lock`.

Nie można użyć [operatora await](../operators/await.md) w treści instrukcji `lock`.

## <a name="remarks"></a>Uwagi

Podczas synchronizowania dostępu do wątku z udostępnionym zasobem należy zablokować wystąpienie obiektu dedykowanego (na przykład `private readonly object balanceLock = new object();`) lub inne wystąpienie, które prawdopodobnie nie będzie używane jako obiekt blokady przez niepowiązane części kodu. Należy unikać używania tego samego wystąpienia obiektu blokady dla różnych udostępnionych zasobów, ponieważ może to spowodować zakleszczenie lub zablokowanie rywalizacji. W szczególności należy unikać używania następujących funkcji jako obiektów blokowania:

- `this`, ponieważ mogą one być używane przez wywołujących jako blokadę.
- wystąpienia <xref:System.Type>, ponieważ mogą być uzyskane przez operatora lub odbicie [typeof](../operators/type-testing-and-cast.md#typeof-operator) .
- wystąpienia ciągów, w tym literały ciągów, ponieważ mogą być [internice](/dotnet/api/system.string.intern#remarks).

## <a name="example"></a>Przykład

W poniższym przykładzie zdefiniowano klasę `Account`, która synchronizuje dostęp do jego prywatnego `balance` pola przez zablokowanie na dedykowanym wystąpieniu `balanceLock`. Użycie tego samego wystąpienia do blokowania gwarantuje, że nie można jednocześnie aktualizować pola `balance` przez dwa wątki próbujące wywołać metody `Debit` lub `Credit` jednocześnie.

[!code-csharp[lock-statement-example](~/samples/snippets/csharp/keywords/LockStatementExample.cs)]

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [blokowanie instrukcji](~/_csharplang/spec/statements.md#the-lock-statement) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- <xref:System.Threading.Monitor?displayProperty=nameWithType>
- <xref:System.Threading.SpinLock?displayProperty=nameWithType>
- <xref:System.Threading.Interlocked?displayProperty=nameWithType>
- [C#odwoła](../index.md)
- [Słowa kluczowe języka C#](index.md)
- [Przegląd elementów podstawowych synchronizacji](../../../standard/threading/overview-of-synchronization-primitives.md)
