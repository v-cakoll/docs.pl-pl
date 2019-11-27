---
title: Typy metod manipulowania ciągami
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: a02278abfb71efb2f31f239a89a22ad1c8ee7a18
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346268"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Typy metod manipulowania ciągami w Visual Basic
Istnieje kilka różnych sposobów analizowania ciągów i manipulowania nimi. Niektóre metody są częścią języka Visual Basic, a inne są związane z klasą `String`.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Visual Basic język i .NET Framework  
 Metody Visual Basic są używane jako funkcje związane z językiem. Mogą być używane bez kwalifikacji w kodzie. W poniższym przykładzie przedstawiono typowe użycie Visual Basic polecenie manipulowania ciągiem:  
  
 [!code-vb[VbVbalrStrings#44](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#44)]  
  
 W tym przykładzie funkcja `Mid` wykonuje bezpośrednią operację na `aString` i przypisuje wartość do `bString`.  
  
 Aby zapoznać się z listą metod manipulowania ciągami Visual Basic, zobacz [Podsumowanie manipulowania ciągami](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Metody udostępnione i metody wystąpień  
 Można również manipulować ciągami przy użyciu metod klasy `String`. Istnieją dwa typy metod w `String`: metody *Shared* i metody *wystąpień* .  
  
#### <a name="shared-methods"></a>Metody udostępnione  
 Metoda wspólna to metoda, która jest uruchamiana z samej klasy `String` i nie wymaga wystąpienia tej klasy do działania. Metody te mogą być kwalifikowana nazwą klasy (`String`), a nie z wystąpieniem klasy `String`. Na przykład:  
  
 [!code-vb[VbVbalrStrings#45](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#45)]  
  
 W poprzednim przykładzie metoda <xref:System.String.Copy%2A?displayProperty=nameWithType> jest metodą statyczną, która operuje na wyrażeniu, które jest określone, i przypisuje wartość wyniki do `bString`.  
  
#### <a name="instance-methods"></a>Metody wystąpień  
 Metody wystąpień, które różnią się od określonego wystąpienia `String` i muszą być kwalifikowane przy użyciu nazwy wystąpienia. Na przykład:  
  
 [!code-vb[VbVbalrStrings#46](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStrings/VB/Class2.vb#46)]  
  
 W tym przykładzie metoda <xref:System.String.Substring%2A?displayProperty=nameWithType> jest metodą wystąpienia `String` (czyli `aString`). Wykonuje operację na `aString` i przypisuje tę wartość do `bString`.  
  
 Aby uzyskać więcej informacji, zobacz dokumentację klasy <xref:System.String>.  
  
## <a name="see-also"></a>Zobacz także

- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
