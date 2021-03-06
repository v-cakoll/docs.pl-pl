---
title: Out (modyfikator ogólny)
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceOut
helpviewer_keywords:
- Out keyword [Visual Basic]
- covariance, Out keyword [Visual Basic]
ms.assetid: c4418369-1518-4a46-9a1e-054c61038eca
ms.openlocfilehash: 28ae7d6fd51170aa822072fc2f5357443f51a353
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392096"
---
# <a name="out-generic-modifier-visual-basic"></a>Out (modyfikator ogólny) (Visual Basic)

W przypadku parametrów typu ogólnego `Out` słowo kluczowe Określa, że typ jest współwariantem.

## <a name="remarks"></a>Uwagi

Kowariancja umożliwia użycie bardziej pochodnego typu niż określony przez parametr generyczny. Pozwala to na niejawną konwersję klas, które implementują interfejsy wariantów i niejawną konwersję typów delegatów.

Aby uzyskać więcej informacji, zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>Reguły

Możesz użyć `Out` słowa kluczowego w interfejsach ogólnych i delegatach.

W interfejsie ogólnym parametr typu może być zadeklarowany jako współwariant, jeśli spełnia następujące warunki:

- Parametr typu jest używany tylko jako typ zwracany metod interfejsu i nie jest używany jako typ argumentów metody.

    > [!NOTE]
    > Istnieje jeden wyjątek dla tej reguły. Jeśli w interfejsie o niezmiennym jest kontrawariantne delegat generyczny jako parametr metody, można użyć typu współwariantu jako parametru typu ogólnego dla tego delegata. Aby uzyskać więcej informacji na temat elementów delegowanych i kontrawariantne ogólnych, zobacz [Wariancja w delegatach](../../programming-guide/concepts/covariance-contravariance/variance-in-delegates.md) i [Używanie wariancji dla delegatów typu Func i akcja](../../programming-guide/concepts/covariance-contravariance/using-variance-for-func-and-action-generic-delegates.md).

- Parametr typu nie jest używany jako ograniczenie ogólne metod interfejsu.

W delegatze ogólnym parametr typu może być zadeklarowany jako współvariant, jeśli jest używany tylko jako zwracany typ metody i nie jest używany dla argumentów metody.

Dla typów referencyjnych są obsługiwane Kowariancja i kontrawariancja, ale nie są one obsługiwane w przypadku typów wartości.

W Visual Basic nie można zadeklarować zdarzeń w interfejsach współvariant bez określania typu delegata. Ponadto interfejsy współwariantowe nie mogą mieć klas zagnieżdżonych, wyliczeniowych ani struktur, ale mogą mieć zagnieżdżone interfejsy.

## <a name="behavior"></a>Zachowanie

Interfejs, który ma parametr typu klasy współdzielonej, umożliwia jej metodom zwrócenie większej liczby typów pochodnych niż te określone przez parametr typu. Na przykład, ponieważ w .NET Framework 4, in <xref:System.Collections.Generic.IEnumerable%601> , typu T jest współwariantem, można przypisać obiekt `IEnumerable(Of String)` typu do obiektu `IEnumerable(Of Object)` typu bez użycia żadnych specjalnych metod konwersji.

Delegata, do którego można przypisać inny delegat tego samego typu, ale z bardziej pochodnym parametrem typu ogólnego.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować, zwiększyć i zaimplementować interfejs ogólny typu "współvariant". Przedstawiono w nim również sposób użycia niejawnej konwersji dla klas, które implementują interfejs współvariant.

[!code-vb[vbVarianceKeywords#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#3)]

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak zadeklarować, utworzyć wystąpienie i wywołać delegata ogólnego typu. Pokazano również, jak można użyć niejawnej konwersji typów delegatów.

[!code-vb[vbVarianceKeywords#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#4)]

## <a name="see-also"></a>Zobacz też

- [Wariancje w interfejsach](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [W](in-generic-modifier.md)
