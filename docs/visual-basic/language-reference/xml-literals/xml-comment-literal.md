---
title: Literał komentarza XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 60c354215c627683fd6c69d9ca66fc115c26ccda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603941"
---
# <a name="xml-comment-literal-visual-basic"></a>Literał komentarza XML (Visual Basic)
Literał reprezentujący <xref:System.Xml.Linq.XComment> obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`<!--`|Wymagana. Oznacza początek komentarza XML.|  
|`content`|Wymagana. Tekst wyświetlany w komentarzu XML. Nie może zawierać szereg dwa łączniki (-) lub kończyć się łącznikiem sąsiadujące tagu zamykającego.|  
|`-->`|Wymagana. Oznacza koniec komentarza XML.|  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XComment> Obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Literały komentarza XML nie zawierają zawartości dokumentu; zawierają informacje o dokumentu. W sekcji komentarza XML kończy sekwencji "-->". Oznacza to następujące kwestie:  
  
-   Nie można użyć wyrażenia osadzonego w komentarzu XML literału, ponieważ ogranicznika wyrażenia osadzonego to prawidłowa zawartość komentarza XML.  
  
-   Sekcje komentarza XML nie mogą być zagnieżdżone, ponieważ `content` nie może zawierać wartości "-->".  
  
 Literał komentarza XML można przypisać do zmiennej lub można objąć literał elementu XML.  
  
> [!NOTE]
>  Literał XML może obejmować wiele wierszy bez użycia znaki kontynuacji wiersza. Ta funkcja umożliwia kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał komentarza XML na wywołanie <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy komentarz XML, który zawiera tekst "Jest komentarz".  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XComment>  
 [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
