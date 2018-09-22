---
title: out — słowo kluczowe (modyfikator ogólny) (odwołanie w C#)
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: fedbdb12c1da108d17636770fb5c628195dce0d4
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580385"
---
# <a name="out-generic-modifier-c-reference"></a>out (modyfikator ogólny) (odwołanie w C#)

Dla parametrów typu genetycznego `out` — słowo kluczowe Określa, że parametr typu jest kowariantny. Możesz użyć `out` — słowo kluczowe w interfejsach ogólnych i delegatach.

Kowariancja umożliwia użycie typu bardziej pochodnego niż określona przez parametr ogólny. Umożliwia to niejawna konwersja klasy, które implementują interfejsów typu variant i niejawnej konwersji typów obiektów delegowanych. Kowariancja i kontrawariancja są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.

Interfejs, który ma kowariantnego parametru typu umożliwia jego metod zwrócić więcej typów pochodnych niż określony przez parametr typu. Na przykład ponieważ w programie .NET Framework 4 w <xref:System.Collections.Generic.IEnumerable%601>typu T jest kowariantny, można przypisać obiektu `IEnumerable(Of String)` typ obiektu `IEnumerable(Of Object)` typu bez przy użyciu dowolnej metody konwersji specjalne.

Kowariantne delegata można przypisać inną delegata tego samego typu, ale także z bardziej pochodnego parametr typu ogólnego.

Aby uzyskać więcej informacji, zobacz [kowariancji i kontrawariancji](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="example---covariant-generic-interface"></a>Przykład — kowariantne interfejs ogólny

Poniższy przykład pokazuje, jak deklarować, rozszerzanie i implementować interfejs ogólny kowariantny. Pokazano również, jak używać niejawna konwersja dla klas, które implementują interfejs kowariantny.

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

W interfejsie ogólnego parametr typu mogą być deklarowane jako kowariantny, jeśli spełnia następujące warunki:

- Parametr typu jest używany tylko jako zwracany typ metody interfejsu i nie jest używany jako typ argumentów metody.

    > [!NOTE]
    > Istnieje jeden wyjątek od tej reguły. Jeśli w interfejsie kowariantne Delegat ogólny kontrawariantny, jako parametru metody, można użyć kowariantnego typu co parametr typu ogólnego, dla tego delegata. Aby uzyskać więcej informacji na temat kowariantne i kontrawariantne delegatów ogólnych, zobacz [wariancje w Delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [przy użyciu wariancji dla akcji delegatów ogólnych Func i](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Parametr typu nie jest używany jako ograniczenia typu ogólnego dla metod interfejsu.

## <a name="example---covariant-generic-delegate"></a>Przykład — kowariantne Delegat ogólny

Poniższy przykład pokazuje, jak deklarować, Utwórz wystąpienie i wywołania kowariantne Delegat ogólny. Pokazano również, jak można niejawnie przekonwertować typy delegatów.

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

Delegat ogólny typ może być zadeklarowana kowariantne Jeśli jest używany tylko jako typ zwracany metody i nie są używane dla argumentów metody.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Wariancje w interfejsach ogólnych](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [in](in-generic-modifier.md)
- [Modyfikatory](modifiers.md)