---
title: 'Instrukcje: Tworzenie ciągów przy użyciu elementu StringBuilder'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 9295b9d0cdcfdb05dfc75f75f48c16c2354b09b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344379"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Instrukcje: Tworzenie ciągów przy użyciu elementu StringBuilder w Visual Basic

Ten przykład tworzy długi ciąg z wielu mniejszych ciągów przy użyciu klasy <xref:System.Text.StringBuilder>. Klasa <xref:System.Text.StringBuilder> jest bardziej wydajna niż operator `&=` do łączenia wielu ciągów.

## <a name="example"></a>Przykład

Poniższy przykład tworzy wystąpienie klasy <xref:System.Text.StringBuilder>, dołącza do tego wystąpienia ciągi 1 000, a następnie zwraca reprezentację ciągu:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Zobacz także

- [Używanie klasy StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&=, operator](../../../language-reference/operators/and-assignment-operator.md)
- [Ciągi](index.md)
- [Tworzenie nowych ciągów](../../../../standard/base-types/creating-new.md)
- [Manipulowanie ciągami](../../../../standard/base-types/manipulating-strings.md)
