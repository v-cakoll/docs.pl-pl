---
title: Wartości zerowe (F#)
description: Dowiedz się, jak używana jest wartość null w języku programowania F#.
ms.date: 05/16/2016
ms.openlocfilehash: 8751ac402c43ddb07fb62e08b6c6d5403cbe9acc
ms.sourcegitcommit: db8b83057d052c1f9f249d128b08d4423af0f7c2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/02/2018
ms.locfileid: "43787905"
---
# <a name="null-values"></a>Wartości zerowe

W tym temacie opisano, jak używana jest wartość null w języku F#.

## <a name="null-value"></a>Wartość null

Wartość null nie używa się zazwyczaj w F# dla wartości lub zmienne. Jednak jako nietypowe wartości w niektórych sytuacjach pojawia się o wartości null. Jeśli typ jest zdefiniowany w języku F#, wartość null nie jest dozwolona jako standardowa, chyba że [allownullliteral —](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atrybut jest stosowany do typu. Jeśli typ jest zdefiniowany w innych językach .NET, wartość null jest możliwa wartość, a podczas współdziałania takich typów, mogą występować w kodzie języka F# wartości null.

Dla typu zdefiniowane w języku F# i używane wyłącznie z języka F#, jedynym sposobem tworzenia wartości null bezpośrednio przy użyciu biblioteki języka F# jest użycie [Unchecked.defaultof](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) lub [Array.zeroCreate](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Dla typów języka F#, która jest używana z innymi językami .NET, lub, jeśli używasz tego typu za pomocą interfejsu API, które nie są zapisywane w języku F#, takie jak .NET Framework, może wystąpić wartości null.

Możesz użyć `option` typ w języku F# podczas może użyć zmiennej odwołania o wartości null możliwe w innym języku .NET. Zamiast wartości null przy użyciu języka F# `option` typu, użyj wartości opcji `None` Jeśli nie ma obiektu. Użyj wartości opcji `Some(obj)` z obiektem `obj` po obiektu. Aby uzyskać więcej informacji, zobacz [opcje](../options.md).

`null` — Słowo kluczowe jest nieprawidłowy — słowo kluczowe w języku F# i trzeba użyć, jeśli pracujesz z interfejsów API programu .NET Framework lub innych interfejsów API, które są zapisywane w innym języku .NET. Dwie sytuacje, w których możesz potrzebować wartości null są podczas wywoływania interfejsu API platformy .NET i przekazać wartości null jako argument i zinterpretować wartość zwracana lub parametr wyjściowy z wywołania metody .NET.

Aby przekazać wartości null do metody .NET, wystarczy użyć `null` — słowo kluczowe w wywoływanym kodzie. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Aby zinterpretować wartość null, jest uzyskiwana z metody .NET, użyj dopasowanie wzorca, jeżeli jest to możliwe. Poniższy przykład kodu pokazuje sposób użycia dopasowywania do wzorca, aby zinterpretować wartość null, która jest zwracana z `ReadLine` podczas próby odczytu poza końcem strumienia wejściowego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Wartości null dla typów F# mogą być też generowane w inny sposób, na przykład przy użyciu `Array.zeroCreate`, która wywołuje metodę `Unchecked.defaultof`. Musisz być ostrożnym z taki kod, aby zachować wartości null hermetyzowane. W bibliotece przeznaczone tylko dla języka F# nie ma pod kątem wartości null w każdej funkcji. Jeśli piszesz biblioteki do współpracy z innymi językami .NET może być konieczne Dodaj sprawdza, czy wartości null parametrów wejściowych i zgłosić `ArgumentNullException`tak samo jak w kodzie języka C# lub Visual Basic.

Poniższy kod służy do Sprawdź, czy dowolną wartość null.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Zobacz także

- [Wartości](index.md)
- [Wyrażenia dopasowania](../match-expressions.md)
