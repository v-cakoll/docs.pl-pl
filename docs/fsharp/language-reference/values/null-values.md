---
title: Wartości zerowe
description: Dowiedz się, w jaki sposób wartość null F# jest używana w języku programowania.
ms.date: 03/22/2019
ms.openlocfilehash: 2038c0a461fec9884c51edd50c3c9f336104e30e
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/30/2019
ms.locfileid: "68630805"
---
# <a name="null-values"></a>Wartości zerowe

W tym temacie opisano, jak w programie F#jest używana wartość null.

## <a name="null-value"></a>Wartość zerowa

Wartość null nie jest zwykle używana w F# przypadku wartości lub zmiennych. Jednak wartość null pojawia się jako nietypowa wartość w pewnych sytuacjach. Jeśli typ jest zdefiniowany w F#, wartości null nie można używać jako zwykłej wartości, chyba że atrybut [AllowNullLiteral](https://msdn.microsoft.com/library/4f315196-f444-4cca-ba07-1176ff71eb0f) jest stosowany do typu. Jeśli typ jest zdefiniowany w innym języku .NET, wartość null jest możliwa i w przypadku współdziałania z takimi typami F# kod może napotkać wartości null.

Dla typu zdefiniowanego w F# i używanej wyłącznie F#z, jedynym sposobem utworzenia wartości null przy użyciu F# biblioteki bezpośrednio jest użycie opcji unchecked [. defaultof —](https://msdn.microsoft.com/library/9ff97f2a-1bd4-4f4c-afbe-5886a74ab977) lub [Array. zeroCreate —](https://msdn.microsoft.com/library/fa5b8e7a-1b5b-411c-8622-b58d7a14d3b2). Jednak dla F# typu, który jest używany z innych języków .NET lub jeśli używasz tego typu z interfejsem API, który nie jest zapisany w F#, na przykład .NET Framework, mogą wystąpić wartości null.

Można użyć typu w `option` F# , gdy można użyć zmiennej odwołania z wartością null w innym języku .NET. Zamiast wartości null, przy użyciu F# `option` typu, należy użyć wartości `None` opcji, jeśli nie ma obiektu. Możesz użyć wartości `Some(obj)` opcji z obiektem `obj` , gdy istnieje obiekt. Aby uzyskać więcej informacji, zobacz [Opcje](../options.md). Należy zauważyć, że nadal można spakować `null` wartość do opcji, jeśli, na `Some x`, `x` ma być `null`. W związku z tym ważne jest, aby użyć `None` , gdy wartość jest `null`.

Słowo kluczowe jest prawidłowym słowem kluczowym w F# języku i trzeba go używać podczas pracy z interfejsami API .NET Framework lub innymi interfejsami API, które są zapisywane w innym języku .NET. `null` Dwie sytuacje, w których może być wymagana wartość null, są wywoływane w przypadku wywołania interfejsu API platformy .NET i przekazania wartości null jako argumentu oraz podczas interpretowania wartości zwracanej lub parametru wyjściowego z wywołania metody .NET.

Aby przekazać wartość null do metody .NET, należy po prostu użyć `null` słowa kluczowego w kodzie wywołującym. Pokazano to w poniższym przykładzie kodu.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet701.fs)]

Aby interpretować wartość null, która jest uzyskiwana z metody .NET, należy użyć dopasowania wzorca, jeśli jest to możliwe. Poniższy przykład kodu pokazuje, jak używać dopasowywania wzorców do interpretowania wartości null, która jest zwracana `ReadLine` z podczas próby odczytu poza końcem strumienia wejściowego.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet702.fs)]

Wartości null dla F# typów można również generować w inny sposób, na przykład w przypadku użycia `Array.zeroCreate`, które wywołuje. `Unchecked.defaultof` Należy zachować ostrożność dzięki takiemu kodowi, aby zachować wartości null hermetyzowane. W bibliotece przeznaczonej tylko dla F#programu nie trzeba sprawdzać wartości null w każdej funkcji. Jeśli piszesz bibliotekę do międzyoperacyjności z innymi językami .NET, może być konieczne dodanie czeków dla parametrów wejściowych null i wyrzucanie `ArgumentNullException`, podobnie jak w C# przypadku kodu lub Visual Basic.

Możesz użyć poniższego kodu, aby sprawdzić, czy arbitralna wartość jest równa null.

[!code-fsharp[Main](~/samples/snippets/fsharp/lang-ref-1/snippet703.fs)]

## <a name="see-also"></a>Zobacz także

- [Wartości](index.md)
- [Wyrażenia dopasowania](../match-expressions.md)
