---
title: 'Jak: tworzenie ciągów za pomocą Kreatora ciągów'
ms.date: 07/20/2015
helpviewer_keywords:
- StringBuilder class
- strings [Visual Basic], using StringBuilder
ms.assetid: 9c042880-aa16-432e-9ccb-cd00abda9ae3
ms.openlocfilehash: c41db584df83782dab99b90043045aa2cabcb6ff
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645330"
---
# <a name="how-to-create-strings-using-a-stringbuilder-in-visual-basic"></a>Jak: tworzenie ciągów przy użyciu Kreatora ciągów w języku Visual Basic

W tym przykładzie tworzy długi ciąg z <xref:System.Text.StringBuilder> wielu mniejszych ciągów przy użyciu klasy. Klasa <xref:System.Text.StringBuilder> jest bardziej wydajne niż `&=` operator do łączenia wielu ciągów.

## <a name="example"></a>Przykład

Poniższy przykład tworzy wystąpienie <xref:System.Text.StringBuilder> klasy, dołącza 1000 ciągów do tego wystąpienia, a następnie zwraca jego reprezentację ciągu:

 [!code-vb[VbVbalrStrings#70](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#70)]

## <a name="see-also"></a>Zobacz też

- [Używanie klasy StringBuilder](../../../../standard/base-types/stringbuilder.md)
- [&= Operator](../../../language-reference/operators/and-assignment-operator.md)
- [Ciągi](index.md)
- [Tworzenie nowych ciągów](../../../../standard/base-types/creating-new.md)
- [Manipulowanie ciągami](../../../../standard/base-types/best-practices-strings.md)
