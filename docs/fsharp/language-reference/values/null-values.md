---
title: Wartości zerowe (F#)
description: 'Dowiedz się, jak używana jest wartość null w języku programowania w języku F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 7367b35cb6e910f926179e52992d5533e5cdda0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33563912"
---
# <a name="null-values"></a>Wartości zerowe

W tym temacie opisano, jak wartość null jest używana w języku F #.


## <a name="null-value"></a>Wartość null
Wartość null jest zwykle nieużywane w języku F # dla wartości lub zmienne. Jednak null pojawia się jako nieprawidłowej wartości w niektórych sytuacjach. Jeśli typ jest zdefiniowany w języku F #, wartość null nie jest dozwolona jako standardowa, chyba że [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) atrybut jest stosowany do typu. Jeśli typ jest zdefiniowany w innym języku .NET, wartość null jest możliwą wartość, a gdy współdziałania takich typów, mogą występować w kodzie języka F # wartości null.

Typ zdefiniowany w języku F # i używane wyłącznie z języka F #, jedynym sposobem, aby utworzyć wartość null, bezpośrednio za pomocą biblioteki F # jest użycie [unchecked.defaultof —](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) lub [Array.zerocreate —](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Dla typu F # używany z innymi językami .NET, lub, jeśli używasz tego typu z interfejsu API, który nie jest napisany w języku F #, takich jak .NET Framework, może wystąpić wartości null.

Można użyć `option` typu w języku F # podczas może użyć zmiennej odwołania o możliwych wartości null w innym języku .NET. Zamiast wartości null w języku F # `option` typu, możesz użyć wartości opcji `None` Jeśli nie ma żadnego obiektu. Użyj wartości opcji `Some(obj)` z obiektem `obj` po obiektu. Aby uzyskać więcej informacji, zobacz [opcje](../options.md).

`null` — Słowo kluczowe jest nieprawidłowy — słowo kluczowe w języku F # i należy go używać w przypadku korzystania z interfejsów API architektury .NET Framework lub innych interfejsów API, które są zapisywane w innym języku .NET. Dwie sytuacje, w których może być konieczne wartości null są wywołać interfejs API .NET i przekazać wartość null jako argumentu i interpretowania wartości zwracanej lub parametru wyjściowego po wywołaniu metody .NET.

Aby przekazać wartości null do metody .NET, wystarczy użyć `null` — słowo kluczowe w wywoływanym kodzie. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Aby zinterpretować wartość null, uzyskany z metody .NET, użyj wzorca dopasowania, jeśli to możliwe. Poniższy przykładowy kod przedstawia użycie dopasowanie wzorca, aby zinterpretować wartość null, która jest zwracana z `ReadLine` podczas próby odczytu poza końcem strumienia wejściowego.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Wartości null dla typów F # może być również generowany w inny sposób, na przykład przy użyciu `Array.zeroCreate`, które wywołuje `Unchecked.defaultof`. Należy zachować ostrożność przy taki kod, aby zachować wartości null hermetyzowany. W bibliotece przeznaczone tylko do F # nie masz do sprawdzenia wartości null w każdej funkcji. Jeśli piszesz biblioteki współdziałanie z innymi językami .NET, może być konieczne Dodaj sprawdza, czy wartości null parametrów wejściowych i zgłosić `ArgumentNullException`, tak jak w kodzie C# lub Visual Basic.

Poniższy kod służy do sprawdzania, jeśli wartość dowolnego ma wartość null.

[!code-fsharp[Main](../../../../samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Zobacz też
[Wartości](index.md)

[Wyrażenia dopasowania](../match-expressions.md)
