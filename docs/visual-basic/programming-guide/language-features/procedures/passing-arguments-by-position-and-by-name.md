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
ms.openlocfilehash: 686b64977f086c8128e56298a0ed8c5aa0c51efa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84364035"
---
# <a name="passing-arguments-by-position-and-by-name-visual-basic"></a>Przekazywanie argumentów według pozycji i według nazwy (Visual Basic)

Po wywołaniu `Sub` procedury lub można `Function` przekazać argumenty *według położenia* — w kolejności, w jakiej są wyświetlane w definicji procedury — lub można przekazać je *według nazwy*, bez względu na położenie.

W przypadku przekazania argumentu według nazwy należy określić zadeklarowaną nazwę argumentu, po którym następuje dwukropek i znak równości ( `:=` ), po którym następuje wartość argumentu. Argumenty nazwane można podawać w dowolnej kolejności.

Na przykład Poniższa `Sub` procedura przyjmuje trzy argumenty:

[!code-vb[SampleProcedure](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#1)]

Po wywołaniu tej procedury można podać argumenty według pozycji według nazwy lub kombinacji obu tych metod.

## <a name="passing-arguments-by-position"></a>Przekazywanie argumentów według pozycji

Można wywołać `Display` metodę z argumentami przekazane według pozycji i rozdzielonymi przecinkami, jak pokazano w następującym przykładzie:

[!code-vb[ByPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#2)]

W przypadku pominięcia opcjonalnego argumentu na liście argumentów pozycyjnych należy trzymać miejsce z przecinkiem. Poniższy przykład wywołuje `Display` metodę bez `age` argumentu:

[!code-vb[ByPositionWithOptionalArgument](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#3)]

## <a name="passing-arguments-by-name"></a>Przekazywanie argumentów według nazwy

Alternatywnie można wywołać `Display` z argumentami przekazaną przez nazwę, również rozdzielonymi przecinkami, jak pokazano w następującym przykładzie:

[!code-vb[ByName](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#4)]

Przekazywanie argumentów według nazwy w ten sposób jest szczególnie przydatne w przypadku wywołania procedury, która ma więcej niż jeden argument opcjonalny. Jeśli podasz argumenty według nazwy, nie trzeba używać kolejnych przecinków do określenia brakujących argumentów pozycyjnych. Przekazywanie argumentów według nazwy ułatwia również śledzenie argumentów, które są przekazywane i które są pomijane.

## <a name="mixing-arguments-by-position-and-by-name"></a>Mieszanie argumentów według pozycji i według nazwy

Argumenty można podawać zarówno według pozycji, jak i według nazwy w ramach pojedynczego wywołania procedury, jak pokazano w następującym przykładzie:

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#5)]

W poprzednim przykładzie żaden dodatkowy przecinek nie jest wymagany do przechowywania pominiętego `age` argumentu, ponieważ `birth` jest przenoszona według nazwy.

W wersjach Visual Basic przed 15,5, gdy podasz argumenty przy użyciu kombinacji pozycji i nazwy, argumenty pozycyjne muszą być wszystkie. Po podaniu argumentu według nazwy wszystkie pozostałe argumenty muszą być przekazane przez nazwę.  Na przykład następujące wywołanie `Display` metody wyświetla błąd kompilatora [BC30241: Oczekiwano argumentu nazwanego](../../../misc/bc30241.md).

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#6)]

Począwszy od Visual Basic 15,5, argumenty pozycyjne mogą następować po nazwanych argumentach, jeśli końcowe argumenty pozycyjne znajdują się w poprawnej pozycji. W przypadku skompilowania w obszarze Visual Basic 15,5 poprzednie wywołanie `Display` metody kompiluje się pomyślnie i nie generuje już błędu kompilatora [BC30241](../../../misc/bc30241.md).

Ta możliwość mieszania i dopasowywania argumentów nazwanych i pozycyjnych w dowolnej kolejności jest szczególnie przydatna, gdy chcesz użyć argumentu nazwanego, aby kod był bardziej czytelny. Na przykład następujący `Person` Konstruktor klasy wymaga dwóch argumentów typu `Person` , które mogą być `Nothing` .

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#7)]

Używanie mieszanych argumentów o nazwach i pozycyjnych ułatwia przeznaczenie kodu, gdy wartość `father` `mother` argumentów i jest `Nothing` :

[!code-vb[ByNameAndPosition](../../../../../samples/snippets/visualbasic/programming-guide/language-features/passing-named-arguments/module1.vb#8)]

Aby użyć argumentów pozycyjnych z nazwanymi argumentami, należy dodać następujący element do pliku projektu Visual Basic ( \* vbproj):

```xml
<PropertyGroup>
  <LangVersion>15.5</LangVersion>
</PropertyGroup>
```

Aby uzyskać więcej informacji [, zobacz Ustawianie wersji językowej Visual Basic](../../../language-reference/configure-language-version.md).

## <a name="restrictions-on-supplying-arguments-by-name"></a>Ograniczenia dotyczące dostarczania argumentów według nazwy

Nie można przekazać argumentów według nazwy, aby uniknąć wprowadzania wymaganych argumentów. Można pominąć tylko opcjonalne argumenty.

Nie można przekazać tablicy parametrów według nazwy. Jest to spowodowane tym, że po wywołaniu procedury należy podać nieokreśloną liczbę argumentów oddzielonych przecinkami dla tablicy parametrów, a kompilator nie może skojarzyć więcej niż jednego argumentu z pojedynczą nazwą.

## <a name="see-also"></a>Zobacz też

- [Procedury](./index.md)
- [Parametry i argumenty procedur](./procedure-parameters-and-arguments.md)
- [Instrukcje: przekazywanie argumentów do procedury](./how-to-pass-arguments-to-a-procedure.md)
- [Przekazywanie argumentów według wartości i według odwołania](./passing-arguments-by-value-and-by-reference.md)
- [Parametry opcjonalne](./optional-parameters.md)
- [Parameter — Tablice](./parameter-arrays.md)
- [Opcjonalne](../../../language-reference/modifiers/optional.md)
- [ParamArray](../../../language-reference/modifiers/paramarray.md)
