---
title: out — słowo kluczowe (modyfikator ogólny) — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- covariance, out keyword [C#]
- out keyword [C#]
ms.assetid: f8c20dec-a8bc-426a-9882-4076b1db1e00
ms.openlocfilehash: 97ddae2efe55be89840f7a483c18d61259020283
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713289"
---
# <a name="out-generic-modifier-c-reference"></a>out (ogólny modyfikator) (odwołanie do języka C#)

W przypadku parametrów typu `out` ogólnego słowo kluczowe określa, że parametr type jest kowariantny. Słowa kluczowego `out` można użyć w ogólnych interfejsów i delegatów.

Kowariancja umożliwia użycie typu bardziej pochodnego niż określony przez parametr ogólny. Pozwala to na niejawną konwersję klas, które implementują interfejsy kowariantne i niejawną konwersję typów delegatów. Kowariancja i contravariance są obsługiwane dla typów odwołań, ale nie są obsługiwane dla typów wartości.

Interfejs, który ma parametr typu kowariantnego umożliwia jego metody, aby zwrócić więcej typów pochodnych niż określone przez parametr typu. Na przykład, ponieważ w .NET <xref:System.Collections.Generic.IEnumerable%601>Framework 4 w typie T jest kowariantny, można przypisać obiekt `IEnumerable(Of String)` typu do obiektu `IEnumerable(Of Object)` typu bez użycia żadnych specjalnych metod konwersji.

Współwariantdelegata można przypisać innego delegata tego samego typu, ale z bardziej pochodnym parametrem typu ogólnego.

Aby uzyskać więcej informacji, zobacz [Kowariancja i wariancja](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="example---covariant-generic-interface"></a>Przykład — kowariantny interfejs ogólny

W poniższym przykładzie pokazano, jak zadeklarować, rozszerzyć i zaimplementować kowariantny interfejs ogólny. Pokazuje również, jak używać niejawnej konwersji dla klas, które implementują interfejs kowariantny.

[!code-csharp[csVarianceKeywords#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#3)]

W interfejsie ogólnym parametr typu można zadeklarować jako kowariantny, jeśli spełnia następujące warunki:

- Parametr type jest używany tylko jako zwracany typ metod interfejsu i nie jest używany jako typ argumentów metody.

    > [!NOTE]
    > Istnieje jeden wyjątek od tej reguły. Jeśli w interfejsie kowariantykowym masz kontrataki ogólnedelegatjako parametr metody, można użyć typu kowariantowego jako parametru typu ogólnego dla tego delegata. Aby uzyskać więcej informacji na temat kowariantyicznych i przeciwwariantowych delegatów ogólnych, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Używanie wariancji dla delegatów metodycznych akcji i akcji.](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md)

- Parametr type nie jest używany jako ograniczenie ogólne dla metod interfejsu.

## <a name="example---covariant-generic-delegate"></a>Przykład — współwariantowy delegat ogólny

W poniższym przykładzie pokazano, jak zadeklarować, utworzyć wystąpienia i wywołać kowariantycznego delegata ogólnego. Pokazuje również, jak niejawnie konwertować typy delegatów.

[!code-csharp[csVarianceKeywords#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csvariancekeywords/cs/program.cs#4)]

W delegacie rodzajowym typ można zadeklarować jako kowarianty, jeśli jest używany tylko jako typ zwracany metody i nie jest używany dla argumentów metody.

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Wariancje w interfejsach ogólnych](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Cala](in-generic-modifier.md)
- [Modyfikatory](index.md)
