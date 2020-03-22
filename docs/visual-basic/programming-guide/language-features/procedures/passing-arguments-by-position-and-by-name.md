---
title: Przekazywanie argumentów według pozycji i według nazwy
ms.date: 02/01/2018
helpviewer_keywords:
- arguments [Visual Basic], passing by name
- procedures [Visual Basic], arguments
- := passing arguments
- procedure arguments
- Visual Basic code, procedures
- named arguments [Visual Basic], passing arguments
- arguments [Visual Basic], passing by position
- Function procedures [Visual Basic], passing arguments
- named parameters [Visual Basic], passing arguments
- named arguments
- passing parameters [Visual Basic], named parameter arguments
- passing parameters [Visual Basic], by position
- procedures [Visual Basic], calling
- named parameters
- Sub procedures [Visual Basic], passing arguments
- argument passing
- passing parameters [Visual Basic], by name
- argument passing [Visual Basic], by position
- arguments [Visual Basic], listing by name
ms.assetid: 1ad7358f-1da9-48da-a95b-f3c7ed41eff3
ms.openlocfilehash: b6588335f7634cc87a9fc14cbfc4ba80baad1abb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400856"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)

Podczas wywoływania `Sub` `Function` lub procedury, można przekazać argumenty *według pozycji* — w kolejności, w jakiej pojawiają się one w definicji procedury — lub można przekazać je *po imieniu*, bez względu na pozycję.

Podczas przekazywania argumentu według nazwy, należy określić zadeklarowaną nazwę argumentu, po której następuje dwukropek i znak równości (`:=`), a następnie wartość argumentu. Nazwane argumenty można podać w dowolnej kolejności.

Na przykład w `Sub` poniższej procedurze wybierze trzy argumenty:

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

Podczas wywoływania tej procedury, można podać argumenty według pozycji, według nazwy lub przy użyciu mieszaniny obu.

## <a name="passing-arguments-by-position"></a>Przekazywanie argumentów według pozycji

Metodę można `Display` wywołać z jej argumentami przekazywanymi przez położenie i rozdzielanymi przecinkami, jak pokazano w poniższym przykładzie:

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

Jeśli pominięto opcjonalny argument na liście argumentów pozycyjnych, musisz utrzymać jego miejsce przecinkiem. Poniższy przykład `Display` wywołuje metodę `age` bez argumentu:

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Przekazywanie argumentów według nazwy

Alternatywnie można wywołać `Display` z argumentami przekazanymi przez nazwę, również rozdzielone przecinkami, jak pokazano w poniższym przykładzie:

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Przekazywanie argumentów według nazwy w ten sposób jest szczególnie przydatne podczas wywoływania procedury, która ma więcej niż jeden opcjonalny argument. Jeśli podajesz argumenty według nazwy, nie trzeba używać kolejnych przecinków do oznaczania brakujących argumentów pozycyjnych. Przekazywanie argumentów według nazwy ułatwia również śledzenie, które argumenty przechodzisz, a które pomijasz.

## <a name="mixing-arguments-by-position-and-by-name"></a>Mieszanie argumentów według pozycji i nazwy

Argumenty można podawać zarówno według pozycji, jak i według nazwy w wywołaniu pojedynczej procedury, jak pokazano w poniższym przykładzie:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

W poprzednim przykładzie nie jest konieczne dodatkowe przecinek do `age` przechowywania miejsca `birth` pominiętego argumentu, ponieważ jest przekazywana przez nazwę.

W wersjach języka Visual Basic przed 15.5, podczas pokazywanie argumentów przez mieszaninę pozycji i nazwy, argumenty pozycyjne muszą być na pierwszym miejscu. Po podaniu argumentu według nazwy wszystkie pozostałe argumenty muszą być przekazywane według nazwy.  Na przykład następujące wywołanie `Display` metody wyświetla błąd kompilatora [BC30241: Oczekiwany argument nazwany.](../../../misc/bc30241.md)

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

Począwszy od języka Visual Basic 15.5, argumenty pozycyjne mogą być zgodne z nazwanymi argumentami, jeśli końcowe argumenty pozycyjne znajdują się we właściwej pozycji. Jeśli skompilowane w języku Visual Basic 15.5, poprzednie wywołanie `Display` metody kompiluje się pomyślnie i nie generuje już błąd kompilatora [BC30241](../../../misc/bc30241.md).

Ta możliwość mieszania i dopasowywania argumentów nazwanych i pozycyjnych w dowolnej kolejności jest szczególnie przydatna, gdy chcesz użyć nazwanego argumentu, aby kod był bardziej czytelny. Na przykład konstruktor następującej `Person` klasy `Person`wymaga dwóch argumentów `Nothing`typu , z których oba mogą być .

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

Za pomocą mieszanych nazwanych i pozycyjnych argumentów pomaga `father` `mother` uczynić `Nothing`intencję kodu jasne, gdy wartość i argumenty jest:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

Aby śledzić argumenty pozycyjne z nazwanymi argumentami, należy\*dodać następujący element do pliku projektu języka Visual Basic ( .vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Aby uzyskać więcej informacji, zobacz [ustawianie wersji językowej języka Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Ograniczenia dotyczące dostarczania argumentów według nazwy

Nie można przekazać argumentów według nazwy, aby uniknąć wprowadzania wymaganych argumentów. Można pominąć tylko opcjonalne argumenty.

Nie można przekazać tablicy parametrów według nazwy. Dzieje się tak, ponieważ podczas wywoływania procedury, należy podać nieokreśloną liczbę argumentów oddzielonych przecinkami dla tablicy parametrów, a kompilator nie może skojarzyć więcej niż jeden argument z jedną nazwą.

## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Parameter — Tablice](./parameter-arrays.md)
- [Opcjonalne](../../../../visual-basic/language-reference/modifiers/optional.md)
- [ParamArray](../../../../visual-basic/language-reference/modifiers/paramarray.md)
