---
title: Obliczenia powolne
description: Dowiedz się, jak F# obliczenia powolne może zwiększyć wydajność aplikacji i bibliotek.
ms.date: 05/16/2016
ms.openlocfilehash: 35f4a3f7a88ef1650497e0c943234b3574d13b38
ms.sourcegitcommit: fa38fe76abdc8972e37138fcb4dfdb3502ac5394
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/19/2018
ms.locfileid: "53610076"
---
# <a name="lazy-computations"></a>Obliczenia powolne

*Obliczenia powolne* są obliczeń, które nie są oceniane natychmiast, ale zamiast tego są oceniane, gdy wynik jest potrzebny. Może to pomóc poprawić wydajność kodu.

## <a name="syntax"></a>Składnia

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Uwagi

W poprzedniej składni *wyrażenie* kodu, które jest oceniane tylko wtedy, gdy wynik jest wymagane, i *identyfikator* jest wartością, która zapisuje wynik. Wartość jest typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), gdy faktyczny typ, które służy do `'T` jest określana na podstawie wynik wyrażenia.

Obliczenia powolne pozwalają zwiększyć wydajność przez ograniczenie możliwości wykonywania wykonywania obliczeń do sytuacji, w których wynikiem jest wymagana.

Aby wymusić obliczenie, które mają zostać wykonane, należy wywołać metodę `Force`. `Force` powoduje wykonanie można wykonać tylko jeden raz. Kolejne wywołania `Force` zwracać taki sam wynik, ale nie wykonać żadnego kodu.

Poniższy kod ilustruje użycie obliczanie z opóźnieniem i umożliwia korzystanie z `Force`. W tym kodzie typ `result` jest `Lazy<int>`i `Force` metoda zwraca `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Obliczanie z opóźnieniem, ale nie `Lazy` typu, jest również używany w sekwencji. Aby uzyskać więcej informacji, zobacz [sekwencje](sequences.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Lazyextensions — moduł](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)