---
title: Wartości zerowe
description: Dowiedz się, jak używana jest wartość null w F# języka programowania.
ms.date: 03/22/2019
ms.openlocfilehash: 93ac48eddf36981b9df550e76405c3175ae92e0a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61902281"
---
# <a name="null-values"></a>Wartości zerowe

W tym temacie opisano, jak używana jest wartość null w F#.

## <a name="null-value"></a>Wartość null

Wartość null nie jest zwykle używany w F# dla wartości lub zmienne. Jednak jako nietypowe wartości w niektórych sytuacjach pojawia się o wartości null. Jeśli typ jest zdefiniowany w F#, o wartości null nie jest dozwolona jako standardowa, chyba że [allownullliteral —](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atrybut jest stosowany do typu. Jeśli typ jest zdefiniowany w innych językach .NET, wartość null jest możliwa wartość i kiedy są współdziałanie z takich typów usługi F# kodu mogą występować w wartości null.

Dla typu zdefiniowanego w F# i używane wyłącznie z F#, jedynym sposobem utworzyć przy użyciu wartości null F# bezpośrednio biblioteki jest użycie [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) lub [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Jednak w przypadku F# typ, który jest używany z innymi językami .NET lub jeśli używasz tego typu za pomocą interfejsu API, które nie są zapisywane w F#, takich jak .NET Framework, może wystąpić wartości null.

Możesz użyć `option` wpisać F# może zastosowania zmienną odwołania o wartości null możliwe w innym języku .NET. Zamiast wartości null za pomocą F# `option` typu, użyj wartości opcji `None` , jeśli nie ma obiektu. Użyj wartości opcji `Some(obj)` z obiektem `obj` po obiektu. Aby uzyskać więcej informacji, zobacz [opcje](../options.md). Należy zauważyć, że nadal dodatkiem Service pack `null` wartości do opcji if, for `Some x`, `x` ma miejsce `null`. W związku z tym jest ważne, możesz użyć `None` po wartości `null`.

`null` — Słowo kluczowe jest nieprawidłowy — słowo kluczowe w F# języka i trzeba go było używać podczas pracy z interfejsów API programu .NET Framework lub innych interfejsów API, które są zapisywane w innym języku .NET. Dwie sytuacje, w których możesz potrzebować wartości null są podczas wywoływania interfejsu API platformy .NET i przekazać wartości null jako argument i zinterpretować wartość zwracana lub parametr wyjściowy z wywołania metody .NET.

Aby przekazać wartości null do metody .NET, wystarczy użyć `null` — słowo kluczowe w wywoływanym kodzie. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Aby zinterpretować wartość null, jest uzyskiwana z metody .NET, użyj dopasowanie wzorca, jeżeli jest to możliwe. Poniższy przykład kodu pokazuje sposób użycia dopasowywania do wzorca, aby zinterpretować wartość null, która jest zwracana z `ReadLine` podczas próby odczytu poza końcem strumienia wejściowego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Wartość null, wartości F# typy mogą być też generowane w inny sposób, na przykład przy użyciu `Array.zeroCreate`, która wywołuje metodę `Unchecked.defaultof`. Musisz być ostrożnym z taki kod, aby zachować wartości null hermetyzowane. W bibliotece przeznaczona tylko dla F#, ma pod kątem wartości null w każdej funkcji. Jeśli piszesz biblioteki do współpracy z innymi językami .NET może być konieczne Dodaj sprawdza, czy wartości null parametrów wejściowych i zgłosić `ArgumentNullException`tak samo jak w kodzie języka C# lub Visual Basic.

Poniższy kod służy do Sprawdź, czy dowolną wartość null.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Zobacz także

- [Wartości](index.md)
- [Wyrażenia dopasowania](../match-expressions.md)
