---
title: Wyrażenia z opóźnieniem
description: Dowiedz się, jak F# z opóźnieniem wyrażeń może zwiększyć wydajność aplikacji i bibliotek.
ms.date: 03/13/2019
ms.openlocfilehash: 6d53d53093f4e93f53e1c956b94e2f1e4a1bbd55
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904114"
---
# <a name="lazy-expressions"></a>Wyrażenia z opóźnieniem

*Wyrażenia z opóźnieniem* są wyrażeniami, które nie są oceniane natychmiast, ale zamiast tego są oceniane, gdy wynik jest potrzebny. Może to pomóc poprawić wydajność kodu.

## <a name="syntax"></a>Składnia

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *wyrażenie* kodu, które jest oceniane tylko wtedy, gdy wynik jest wymagane, i *identyfikator* jest wartością, która zapisuje wynik. Wartość jest typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), gdy faktyczny typ, które służy do `'T` jest określana na podstawie wynik wyrażenia.

Wyrażenia z opóźnieniem umożliwiają poprawianie wydajności poprzez ograniczenie wykonywania wyrażenia do sytuacji, w których wynikiem jest wymagana.

Aby wymusić wyrażenia do wykonania, należy wywołać metodę `Force`. `Force` powoduje wykonanie można wykonać tylko jeden raz. Kolejne wywołania `Force` zwracać taki sam wynik, ale nie wykonać żadnego kodu.

Poniższy kod ilustruje użycie wyrażenia z opóźnieniem i umożliwia korzystanie z `Force`. W tym kodzie typ `result` jest `Lazy<int>`i `Force` metoda zwraca `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Obliczanie z opóźnieniem, ale nie `Lazy` typu, jest również używany w sekwencji. Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Lazyextensions — moduł](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
