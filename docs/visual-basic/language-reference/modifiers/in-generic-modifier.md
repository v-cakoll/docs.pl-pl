---
title: In (modyfikator ogólny) — Visual Basic
ms.date: 07/20/2015
f1_keywords:
- vb.VarianceIn
helpviewer_keywords:
- contravariance, In keyword [Visual Basic]
- In keyword [Visual Basic]
ms.assetid: 59bb13c5-fe96-42b8-8286-86293d1661c5
ms.openlocfilehash: 9c0f7d454767112e1e309af81407b5fdef22eee9
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004870"
---
# <a name="in-generic-modifier-visual-basic"></a>In (modyfikator ogólny) (Visual Basic)

W przypadku parametrów typu ogólnego słowo kluczowe `In` Określa, że parametr typu jest kontrawariantne.

## <a name="remarks"></a>Uwagi

Kontrawariancja umożliwia użycie mniej pochodnego typu niż określony przez parametr generyczny. Pozwala to na niejawną konwersję klas, które implementują interfejsy wariantów i niejawną konwersję typów delegatów.

Aby uzyskać więcej informacji, zobacz [Kowariancja i kontrawariancja](../../programming-guide/concepts/covariance-contravariance/index.md).

## <a name="rules"></a>Przepisy

Możesz użyć słowa kluczowego `In` w interfejsach ogólnych i delegatach.
  
Parametr typu może być zadeklarowany jako kontrawariantne w interfejsie generycznym lub delegatze, jeśli jest używany tylko jako typ argumentów metody i nie jest używany jako zwracany typ metody. parametry `ByRef` nie mogą być typu współvariant ani kontrawariantne.

Kowariancja i kontrawariancja są obsługiwane dla typów referencyjnych i nie są obsługiwane w przypadku typów wartości.

W Visual Basic nie można zadeklarować zdarzeń w interfejsach kontrawariantne bez określania typu delegata. Interfejsy kontrawariantne nie mogą również zawierać klas zagnieżdżonych, wyliczeniowych ani struktur, ale mogą mieć zagnieżdżone interfejsy.

## <a name="behavior"></a>Zachowanie

Interfejs, który ma parametr typu kontrawariantne, umożliwia jej metodom akceptowanie argumentów o mniejszych typach pochodnych niż te określone przez parametr typu interfejsu. Na przykład, ponieważ w .NET Framework 4, w interfejsie <xref:System.Collections.Generic.IComparer%601> typ T to kontrawariantne, można przypisać obiekt typu `IComparer(Of Person)` do obiektu typu `IComparer(Of Employee)` bez użycia żadnych specjalnych metod konwersji, jeśli `Employee` dziedziczy po `Person`.

Delegatowi kontrawariantne można przypisać inny delegat tego samego typu, ale przy użyciu mniej pochodnego parametru typu ogólnego.

## <a name="example---contravariant-generic-interface"></a>Przykład — kontrawariantne Generic Interface

Poniższy przykład pokazuje, jak zadeklarować, zwiększyć i zaimplementować interfejs ogólny kontrawariantne. Pokazano również, jak można użyć niejawnej konwersji dla klas implementujących ten interfejs.

[!code-vb[vbVarianceKeywords#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#1)]

## <a name="example---contravariant-generic-delegate"></a>Przykład — Delegat ogólny kontrawariantne

Poniższy przykład pokazuje, jak zadeklarować, utworzyć wystąpienie i wywołać delegata generycznego kontrawariantne. Pokazuje również, jak można niejawnie skonwertować typ delegata.

[!code-vb[vbVarianceKeywords#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/vbvariancekeywords/vb/module1.vb#2)]

## <a name="see-also"></a>Zobacz także

- [Wariancje w interfejsach ogólnych](../../programming-guide/concepts/covariance-contravariance/variance-in-generic-interfaces.md)
- [Określoną](out-generic-modifier.md)
