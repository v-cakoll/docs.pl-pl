---
title: 'Instrukcje: Tworzenie ciągów przy użyciu elementu StringBuilder w Visual Basic'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: 19e036abc9d25ec7fdfd6c33ebb420ec4f503cbc
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700110"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Instrukcje: Tworzenie ciągów przy użyciu elementu StringBuilder w Visual Basic

Ten przykład konstruuje długi ciąg z wielu mniejszych ciągów przy użyciu klasy <xref:System.Text.StringBuilder>. Klasa <xref:System.Text.StringBuilder> jest bardziej wydajna niż operator `&=` do łączenia wielu ciągów.

## <a name="example"></a>Przykład

Poniższy przykład tworzy wystąpienie klasy <xref:System.Text.StringBuilder>, dołącza do tego wystąpienia ciągi 1 000, a następnie zwraca reprezentację ciągu:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Zobacz także

- [Używanie klasy StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&=, operator](../../../language-reference/operators/and-assignment-operator.md)
- [Ciągi](index.md)
- [Tworzenie nowych ciągów](../../../../standard/base-types/creating-new.md)
- [Manipulowanie ciągami](../../../../standard/base-types/manipulating-strings.md)
