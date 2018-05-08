---
title: Obliczenia powolne (F#)
description: 'Dowiedz się, jak poprawić wydajność aplikacji i bibliotek obliczenia powolne F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 1c4eb6ab247c44a04a9d145185e2de7ec01b8e0a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="lazy-computations"></a>Obliczenia powolne

*Obliczenia powolne* są obliczenia, które nie są oceniane natychmiast, ale zamiast tego są oceniane, gdy potrzebny jest wynik. To może pomóc zwiększyć wydajność kodu.

## <a name="syntax"></a>Składnia

```fsharp
let identifier = lazy ( expression )
```

## <a name="remarks"></a>Uwagi

W poprzednich składni *wyrażenie* jest kod, który jest oceniane tylko wtedy, gdy wynik jest wymagana, i *identyfikator* to wartość, która zapisuje wynik. Wartość jest typu [ `Lazy<'T>` ](https://msdn.microsoft.com/library/b29d0af5-6efb-4a55-a278-2662a4ecc489), gdzie rzeczywisty typ, które służy do `'T` jest określana na podstawie wyniku wyrażenia.

Obliczenia powolne pozwalają poprawić wydajność przez ograniczenie wykonywania obliczeń w sytuacjach, w których wynikiem jest wymagana.

Aby wymusić obliczeń do wykonania, należy wywołać metodę `Force`. `Force` powoduje wykonanie zostać wykonana tylko raz. Kolejne wywołania `Force` zwracać taki sam wyniku, ale nie wykonuje żadnego kodu.

Poniższy kod ilustruje korzystanie z opóźnieniem obliczania i stosowania `Force`. W tym kodzie typ `result` jest `Lazy<int>`i `Force` metoda zwraca `int`.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-2/snippet73011.fs)]

Obliczanie leniwe, ale nie `Lazy` wpisz, służy także do sekwencji. Aby uzyskać więcej informacji, zobacz [sekwencji](sequences.md).

## <a name="see-also"></a>Zobacz też

[Dokumentacja języka F#](index.md)

[Lazyextensions — moduł](https://msdn.microsoft.com/library/86671f40-84a0-402a-867d-ae596218d948)
