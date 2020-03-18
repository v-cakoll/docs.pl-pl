---
title: w (Modyfikator ogólny) — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713486"
---
# <a name="in-generic-modifier-c-reference"></a>in (modyfikator ogólny) (odwołanie w C#)

W przypadku parametrów typu `in` ogólnego słowo kluczowe określa, że parametr type jest zmienny. Słowa kluczowego `in` można użyć w ogólnych interfejsów i delegatów.

Contravariance umożliwia użycie mniej pochodnego typu niż określony przez parametr ogólny. Pozwala to na niejawną konwersję klas, które implementują interfejsy kontrawariantne i niejawną konwersję typów delegatów. Kowariancja i kontrawariancji w parametrach typu ogólnego są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.

Typ można zadeklarować kontrawarianty w interfejsie ogólnym lub delegować tylko wtedy, gdy definiuje typ parametrów metody, a nie typu zwracanego metody. `In`, `ref`a `out` parametry muszą być niezmienne, co oznacza, że nie są ani kowariantne, ani kontrawariantne.

Interfejs, który ma parametr typu kontrawariantnego umożliwia jego metody do akceptowania argumentów mniej pochodnych typów niż te określone przez parametr typu interfejsu. Na przykład w <xref:System.Collections.Generic.IComparer%601> interfejsie typ T jest kontrawariantny, można `IComparer<Person>` przypisać obiekt typu `IComparer<Employee>` do obiektu typu bez użycia `Employee` specjalnych `Person`metod konwersji, jeśli dziedziczy .

Kontrataki można przypisać innego delegata tego samego typu, ale z mniej pochodnym parametrem typu ogólnego.

Aby uzyskać więcej informacji, zobacz [Kowariancja i wariancja](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Przeciwwariantny interfejs ogólny

W poniższym przykładzie pokazano, jak zadeklarować, rozszerzyć i zaimplementować interfejs ogólny. Pokazuje również, jak można użyć niejawnej konwersji dla klas, które implementują ten interfejs.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Kontrataki generyczny delegat

W poniższym przykładzie pokazano, jak zadeklarować, utworzyć wystąpienia i wywołać kontratak ogólnedelegata. Pokazuje również, jak można niejawnie konwertować typ delegata.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [na zewnątrz](out-generic-modifier.md)
- [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Modyfikatory](index.md)
