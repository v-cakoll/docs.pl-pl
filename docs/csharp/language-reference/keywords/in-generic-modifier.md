---
title: in (modyfikator ogólny) - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- contravariance, in keyword [C#]
- in keyword [C#]
ms.openlocfilehash: ea11fabd7974c67b1f1b3af017db1f34178bfae8
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53238601"
---
# <a name="in-generic-modifier-c-reference"></a>in (modyfikator ogólny) (odwołanie w C#)

Dla parametrów typu genetycznego `in` — słowo kluczowe Określa, że parametr typu jest kontrawariantny. Możesz użyć `in` — słowo kluczowe w interfejsach ogólnych i delegatach.

Kontrawariancja umożliwia używania typu mniej pochodnego niż określona przez parametr ogólny. Umożliwia to niejawna konwersja klasy, które implementują interfejsów typu variant i niejawnej konwersji typów obiektów delegowanych. Kowariancji i kontrawariancji w parametrach typu ogólnego są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.

Typ może być zadeklarowana kontrawariantnego w ogólny interfejs lub delegat tylko wtedy, gdy definiuje typ parametrów metody, a nie typ zwracany metody. `In`, `ref`, i `out` parametry muszą być niezmiennej, co oznacza, są one ani kowariantny lub kontrawariantny.

Interfejs, który ma kontrawariantnego parametru typu umożliwia jego metod przyjmowały argumenty mniej pochodne typy niż określony przez parametr typu interfejsu. Na przykład w <xref:System.Collections.Generic.IComparer%601> interfejsu typu T jest kontrawariantny, można przypisać obiektu `IComparer<Person>` typ obiektu `IComparer<Employee>` typu bez przy użyciu dowolnej metody konwersji specjalne, jeśli `Employee` dziedziczy `Person`.

Kontrawariantnego delegata można przypisać inną delegata tego samego typu, ale mniej pochodnego parametr typu ogólnego.

Aby uzyskać więcej informacji, zobacz [kowariancji i kontrawariancji](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="contravariant-generic-interface"></a>Kontrawariantnego interfejs ogólny

Poniższy przykład pokazuje, jak deklarować, rozszerzanie i implementować interfejs ogólny kontrawariantny. Pokazuje również, jak można użyć niejawna konwersja dla klas, które implementują ten interfejs.

[!code-csharp[csVarianceKeywords#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#1)]

## <a name="contravariant-generic-delegate"></a>Delegat ogólny kontrawariantnego

Poniższy przykład pokazuje, jak deklarować, Utwórz wystąpienie i wywołania to delegat generyczny kontrawariantny. Pokazuje również, jak można niejawnie przekonwertować typu delegata.

[!code-csharp[csVarianceKeywords#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [out](out-generic-modifier.md)  
- [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md)  
- [Modyfikatory](modifiers.md)  