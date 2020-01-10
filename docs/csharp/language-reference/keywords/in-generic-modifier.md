---
title: in (modyfikator ogólny) — C# odwołanie
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: 57da13f6dc6719166b9051afeb2532ba5fbeff3a
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713486"
---
# <a name="in-generic-modifier-c-reference"></a>in (modyfikator ogólny) (odwołanie w C#)

W przypadku parametrów typu ogólnego `in` słowo kluczowe Określa, że parametr typu jest kontrawariantne. Możesz użyć słowa kluczowego `in` w interfejsach ogólnych i delegatach.

Kontrawariancja umożliwia użycie mniej pochodnego typu niż określony przez parametr generyczny. Pozwala to na niejawną konwersję klas, które implementują interfejsy kontrawariantne i niejawną konwersję typów delegatów. W przypadku typów referencyjnych są obsługiwane Kowariancja i kontrawariancja w parametrach typu ogólnego, ale nie są one obsługiwane w przypadku typów wartości.

Typ może być zadeklarowany jako kontrawariantne w ogólnym interfejsie lub delegatze tylko wtedy, gdy definiuje typ parametrów metody, a nie typ zwracany metody. parametry `In`, `ref`i `out` muszą być niezmienne, co oznacza, że nie są one ani współvariant ani kontrawariantne.

Interfejs, który ma parametr typu kontrawariantne, umożliwia jej metodom akceptowanie argumentów o mniejszych typach pochodnych niż te określone przez parametr typu interfejsu. Na przykład, w interfejsie <xref:System.Collections.Generic.IComparer%601>, wpisz T to kontrawariantne, można przypisać obiekt typu `IComparer<Person>` do obiektu typu `IComparer<Employee>` bez użycia żadnych specjalnych metod konwersji, jeśli `Employee` dziedziczy `Person`.

Delegatowi kontrawariantne można przypisać inny delegat tego samego typu, ale przy użyciu mniej pochodnego parametru typu ogólnego.

Aby uzyskać więcej informacji, zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Kontrawariantne — interfejs ogólny

Poniższy przykład pokazuje, jak zadeklarować, zwiększyć i zaimplementować interfejs ogólny kontrawariantne. Pokazano również, jak można użyć niejawnej konwersji dla klas implementujących ten interfejs.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Delegat ogólny kontrawariantne

Poniższy przykład pokazuje, jak zadeklarować, utworzyć wystąpienie i wywołać delegata generycznego kontrawariantne. Pokazuje również, jak można niejawnie skonwertować typ delegata.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [out](out-generic-modifier.md)
- [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)
- [Modyfikatory](index.md)
