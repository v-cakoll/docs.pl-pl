---
title: Wyrażenia z opóźnionym obliczaniem
description: Dowiedz F# się, jak wyrażenia z opóźnieniem mogą zwiększyć wydajność aplikacji i bibliotek.
ms.date: 03/13/2019
ms.openlocfilehash: 97429e9a4c3838cbaa2ead197db4443e0820e8b3
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630741"
---
# <a name="lazy-expressions"></a>Wyrażenia z opóźnionym obliczaniem

*Wyrażenia* z opóźnieniem to wyrażenia, które nie są obliczane natychmiast, ale zamiast tego są oceniane, gdy wynik jest wymagany. Może to pomóc poprawić wydajność kodu.

## <a name="syntax"></a>Składnia

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *wyrażenie* ma kod, który jest oceniany tylko wtedy, gdy wynik jest wymagany, a *Identyfikator* jest wartością, która przechowuje wynik. Wartość jest typu [`Lazy<'T>`](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), gdzie rzeczywisty typ, który jest używany dla `'T` , jest określany na podstawie wyniku wyrażenia.

Wyrażenia z opóźnieniem umożliwiają poprawienie wydajności przez ograniczenie wykonywania wyrażeń tylko do tych sytuacji, w których jest wymagany wynik.

Aby wymusić wykonywanie wyrażeń, należy wywołać metodę `Force`. `Force`powoduje, że wykonywanie wykonuje się tylko jeden raz. Kolejne wywołania `Force` zwracają ten sam wynik, ale nie wykonują żadnego kodu.

Poniższy kod ilustruje użycie wyrażeń z opóźnieniem i użycie `Force`. W tym kodzie `result` typ jest `Lazy<int>`, `Force` a metoda zwraca. `int`

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Ocena z opóźnieniem, ale `Lazy` nie typ, jest również używana dla sekwencji. Aby uzyskać więcej informacji, [](sequences.md)Zobacz sekwencje.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Moduł LazyExtensions](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
