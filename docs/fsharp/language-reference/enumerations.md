---
title: Wyliczenia (F#)
description: 'Dowiedz się, jak sprawić, że kod bardziej czytelny i łatwy w obsłudze za pomocą wyliczenia F # zamiast literałów.'
ms.date: 05/16/2016
ms.openlocfilehash: 47fb353c2698f8b1474834ebbd1b0eff2c7f76e7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44097090"
---
# <a name="enumerations"></a>Wyliczenia

*Wyliczenia*, znane również jako *wyliczenia*,, są typami całkowitymi, gdy etykiety są przypisane do podzbioru wartości. Można je zamiast literałów wprowadzić kod bardziej czytelny i łatwy w obsłudze.

## <a name="syntax"></a>Składnia

```fsharp
type enum-name =
| value1 = integer-literal1
| value2 = integer-literal2
...
```

## <a name="remarks"></a>Uwagi

Wyliczenie wygląda bardzo podobnie złożeniem dyskryminowanym, które ma prostych wartości, z tą różnicą, że można określić wartości. Wartości są zwykle liczb całkowitych, które rozpoczynają się od 0 lub 1 lub liczb całkowitych reprezentujących pozycji bitów. Jeśli wyliczenie jest przeznaczony do reprezentowania pozycje bitów, należy również użyć [flagi](xref:System.FlagsAttribute) atrybutu.

Podstawowym typem wyliczenia jest określana na podstawie literał, która jest używana, tak aby na przykład można literały z sufiksu, takich jak `1u`, `2u`i tak dalej na liczbę całkowitą bez znaku (`uint32`) typu.

W przypadku nazwanych wartości, należy użyć nazwy samego typu wyliczenia jako kwalifikator, oznacza to, `enum-name.value1`, nie tylko `value1`. To zachowanie różni się od sumy rozłączne. Jest to spowodowane wyliczenia zawsze mają [RequireQualifiedAccess](https://msdn.microsoft.com/library/8b9b6ade-0471-4413-ac5d-638cd0de5f15) atrybutu.

Poniższy kod ilustruje deklarowanie i używanie wyliczenia.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2101.fs)]

Można z łatwością przekształcić wyliczenia typem podstawowym za pomocą odpowiedniego operatora, jak pokazano w poniższym kodzie.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2102.fs)]

Typy wyliczone może mieć jedną z następujących typów podstawowych: `sbyte`, `byte`, `int16`, `uint16`, `int32`, `uint32`, `int64`, `uint16`, `uint64`, i `char`. Typy wyliczeniowe są reprezentowane w .NET Framework jako typy, które są dziedziczone z `System.Enum`, który z kolei jest odziedziczone po `System.ValueType`. Dlatego są typy wartości, które znajdują się w stos lub bezpośrednio w zawierającego go obiektu i dowolną wartość typu podstawowego jest prawidłową wartością wyliczenia. Jest to znaczące podczas dopasowania do wzorca w wyliczenia wartości, ponieważ musisz podać wzorzec, który przechwytuje nienazwanych wartości.

`enum` Funkcji biblioteki języka F # może służyć do generowania wartości wyliczenia, nawet wartość inna niż jeden z wstępnie zdefiniowanych, o nazwie wartości. Możesz użyć `enum` funkcji w następujący sposób.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2103.fs)]

Wartość domyślna `enum` funkcja działa z typem `int32`. W związku z tym nie można używać z typami wyliczenia, które mają innych typów podstawowych. Zamiast tego należy użyć.

[!code-fsharp[Main](../../../samples/snippets/fsharp/lang-ref-1/snippet2104.fs)]

Ponadto przypadków dla typów wyliczeniowych zawsze są emitowane jako `public`. Jest to tak, aby były wyrównane w języku C# i pozostałą część platformy .NET.

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka F#](index.md)
- [Rzutowanie i konwersje](casting-and-conversions.md)
