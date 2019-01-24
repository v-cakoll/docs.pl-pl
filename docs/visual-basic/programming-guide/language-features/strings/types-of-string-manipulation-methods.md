---
title: Typy metod manipulowania ciągami w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: fa579303ad268a88269f360bdf626f9590c5d6a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54648498"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Typy metod manipulowania ciągami w Visual Basic
Istnieją różne sposoby analizować ciągów i manipulowania nimi sieci. Niektóre metody są częścią języka Visual Basic, a inne są integralną częścią `String` klasy.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Język Visual Basic i .NET Framework  
 Metody języka Visual Basic są używane jako związane funkcje języka. Mogą one być używane bez kwalifikacji w kodzie. Typowym zastosowaniem polecenia manipulowanie ciągami języka Visual Basic można znaleźć w poniższym przykładzie:  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 W tym przykładzie `Mid` funkcja wykonuje operację bezpośrednie na `aString` i przypisuje wartość do `bString`.  
  
 Aby uzyskać listę metod manipulowania ciągami języka Visual Basic, zobacz [manipulowanie ciągami — Podsumowanie](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Udostępnione metody i metody wystąpienia  
 Można również manipulowania ciągami za pomocą metody `String` klasy. Istnieją dwa typy metod w `String`: *udostępnionego* metod i *wystąpienia* metody.  
  
#### <a name="shared-methods"></a>Udostępnione metody  
 Udostępnione metoda jest metodą, która wynika z `String` samej klasy i nie wymaga wystąpienia tej klasy do pracy. Te metody mogą być kwalifikowana nazwą klasy (`String`), a nie z wystąpieniem `String` klasy. Na przykład:  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 W powyższym przykładzie <xref:System.String.Copy%2A?displayProperty=nameWithType> metoda jest metodą statyczną, który działa na wyrażenie go otrzymuje i przypisuje wartość wynikową do `bString`.  
  
#### <a name="instance-methods"></a>Metody wystąpienia  
 Metody wystąpienia, z kolei wynika z konkretnego wystąpienia `String` i musi być kwalifikowana nazwą wystąpienia. Na przykład:  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 W tym przykładzie <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda jest metodą wystąpienia `String` (czyli `aString`). Wykonuje operację na `aString` i przypisuje wartość do `bString`.  
  
 Aby uzyskać więcej informacji, zobacz dokumentację dla <xref:System.String> klasy.  
  
## <a name="see-also"></a>Zobacz także
- [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
