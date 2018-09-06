---
title: Obliczenia powolne (F#)
description: 'Dowiedz się, jak poprawić wydajność aplikacji i bibliotek obliczenia powolne F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 8afe815f26978de96291a52973d54a9dbcc5eaf2
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44037071"
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
