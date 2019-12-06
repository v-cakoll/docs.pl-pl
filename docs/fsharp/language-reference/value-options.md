---
title: Opcje wartości
description: Dowiedz się F# więcej o typie opcji wartość, która jest wersją struktury typu opcji.
ms.date: 12/04/2019
ms.openlocfilehash: 0e9882ab4acdf2757705ef6022516d3572d87ef2
ms.sourcegitcommit: a4f9b754059f0210e29ae0578363a27b9ba84b64
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/05/2019
ms.locfileid: "74837119"
---
# <a name="value-options"></a>Opcje wartości

Typ opcji wartość w jest F# używany w przypadku, gdy są utrzymywane następujące dwa sytuacje:

1. Scenariusz jest odpowiedni dla [ F# opcji](options.md).
2. Użycie struktury zapewnia korzyść wydajności w danym scenariuszu.

Nie wszystkie scenariusze z uwzględnieniem wydajności są "rozwiązane" przy użyciu struktur. Należy wziąć pod uwagę dodatkowy koszt kopiowania, gdy są używane zamiast typów referencyjnych. Jednak duże F# programy często żądają wielu opcjonalnych typów, które przepływają przez ścieżki gorąca, a w takich przypadkach struktury mogą często dać lepszą wydajność w okresie istnienia programu.

## <a name="definition"></a>Definicja

Opcja Value jest definiowana jako [związek rozłącznych struktur](discriminated-unions.md#struct-discriminated-unions) , który jest podobny do typu opcji odwołania. Jego definicję można traktować w następujący sposób:

```fsharp
[<StructuralEquality; StructuralComparison>]
[<Struct>]
type ValueOption<'T> =
    | ValueNone
    | ValueSome of 'T
```

Opcja wartości jest zgodna z kryterium równości i porównywania strukturalnego. Główną różnicą jest to, że skompilowana nazwa, nazwa typu i nazwy przypadków wskazują, że jest to typ wartości.

## <a name="using-value-options"></a>Korzystanie z opcji wartości

Opcje wartości są używane podobnie jak [Opcje](options.md). `ValueSome` jest używany do wskazania, że wartość jest obecna, a `ValueNone` jest używana, gdy wartość nie jest obecna:

```fsharp
let tryParseDateTime (s: string) =
    match System.DateTime.TryParse(s) with
    | (true, dt) -> ValueSome dt
    | (false, _) -> ValueNone

let possibleDateString1 = "1990-12-25"
let possibleDateString2 = "This is not a date"

let result1 = tryParseDateTime possibleDateString1
let result2 = tryParseDateTime possibleDateString2

match (result1, result2) with
| ValueSome d1, ValueSome d2 -> printfn "Both are dates!"
| ValueSome d1, ValueNone -> printfn "Only the first is a date!"
| ValueNone, ValueSome d2 -> printfn "Only the second is a date!"
| ValueNone, ValueNone -> printfn "None of them are dates!"
```

Podobnie jak w przypadku [opcji](options.md), Konwencja nazewnictwa dla funkcji, która zwraca `ValueOption`, to prefiks z `try`.

## <a name="value-option-properties-and-methods"></a>Właściwości opcji wartości i metody

W tej chwili istnieje jedna Właściwość opcji wartości: `Value`. <xref:System.InvalidOperationException> jest wywoływane, jeśli żadna wartość nie jest obecna, gdy ta właściwość jest wywoływana.

## <a name="value-option-functions"></a>Funkcje opcji wartości

Moduł `ValueOption` w FSharp. Core zawiera funkcje równoważne do modułu `Option`. Istnieje kilka różnic nazw, takich jak `defaultValueArg`:

```fsharp
val defaultValueArg : arg:'T voption -> defaultValue:'T -> 'T
```

Działa tak samo jak `defaultArg` w module `Option`, ale działa w zamian opcji Value.

## <a name="see-also"></a>Zobacz także

- [Opcje](options.md)
