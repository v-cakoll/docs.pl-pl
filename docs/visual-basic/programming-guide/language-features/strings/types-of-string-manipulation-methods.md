---
title: Typy metod manipulowania ciągami w Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- strings [Visual Basic], manipulating [Visual Basic]
- string manipulation
ms.assetid: 905055cd-7f50-48fb-9eed-b0995af1dc1f
ms.openlocfilehash: 11903e067c064f129ecd2df80244edb6741c73be
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33648697"
---
# <a name="types-of-string-manipulation-methods-in-visual-basic"></a>Typy metod manipulowania ciągami w Visual Basic
Istnieje kilka różnych sposobów do analizowania i manipulowania z ciągów. Niektóre metody są częścią języka Visual Basic, a inne są związane z `String` klasy.  
  
## <a name="visual-basic-language-and-the-net-framework"></a>Język Visual Basic i .NET Framework  
 Metody języka Visual Basic są używane jako funkcje związanego z używaniem języka. Mogą one używane, bez kwalifikacji w kodzie. W poniższym przykładzie przedstawiono typowy sposób użycia polecenia manipulowanie ciągami Visual Basic:  
  
 [!code-vb[VbVbalrStrings#44](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_1.vb)]  
  
 W tym przykładzie `Mid` funkcja wykonuje operację bezpośrednio na `aString` i przypisuje wartość do `bString`.  
  
 Aby uzyskać listę metod manipulowania ciągami w Visual Basic, zobacz [manipulowanie ciągami — Podsumowanie](../../../../visual-basic/language-reference/keywords/string-manipulation-summary.md).  
  
### <a name="shared-methods-and-instance-methods"></a>Metody udostępnionego i wystąpienie metody  
 Można również manipulować ciągów z metody `String` klasy. Istnieją dwa typy metod w `String`: *udostępnionego* metod i *wystąpienia* metody.  
  
#### <a name="shared-methods"></a>Metody udostępnionego  
 Udostępnionej metody to metoda, która wynika ze `String` samej klasy i nie wymaga wystąpienia tej klasy do pracy. Te metody mogą być kwalifikowany za pomocą nazwy klasy (`String`), a nie z wystąpieniem `String` klasy. Na przykład:  
  
 [!code-vb[VbVbalrStrings#45](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_2.vb)]  
  
 W powyższym przykładzie <xref:System.String.Copy%2A?displayProperty=nameWithType> metoda jest metodą statyczną, który działa na wyrażeniu go otrzymuje i przypisuje wynikowej wartości do `bString`.  
  
#### <a name="instance-methods"></a>Wystąpienie metody  
 Wystąpienie metody, natomiast wynika z konkretnego wystąpienia `String` i musi być kwalifikowany za pomocą nazwy obiektu. Na przykład:  
  
 [!code-vb[VbVbalrStrings#46](../../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/types-of-string-manipulation-methods_3.vb)]  
  
 W tym przykładzie <xref:System.String.Substring%2A?displayProperty=nameWithType> metoda jest metodą wystąpienia `String` (czyli `aString`). Wykonuje operację na `aString` i przypisuje wartość tego `bString`.  
  
 Aby uzyskać więcej informacji, zobacz dokumentację <xref:System.String> klasy.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie do ciągów w Visual Basic](../../../../visual-basic/programming-guide/language-features/strings/introduction-to-strings.md)
