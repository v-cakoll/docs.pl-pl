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
ms.openlocfilehash: 149bbac6d301a9c2f166d05698e3780171126cb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938648"
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
|`content`|Wymagana. Tekst wyświetlany w komentarzu XML. Nie może zawierać szereg dwa łączniki (-) ani kończyć się łącznikiem przylegające do tagu zamykającego.|  
|`-->`|Wymagana. Oznacza koniec komentarza XML.|  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XComment> Obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Literały komentarza XML nie zawierają treści dokumentu; zawierają informacje o tym dokumencie. Sekcja komentarz XML kończy się za pomocą sekwencji "-->". Oznacza to następujące kwestie:  
  
- Nie można użyć wyrażenia osadzone w komentarzu XML literału, ponieważ ograniczniki osadzone wyrażenia są prawidłowa zawartość komentarza XML.  
  
- Sekcje komentarza XML nie mogą być zagnieżdżone, ponieważ `content` nie może zawierać wartość "-->".  
  
 Literał komentarza XML można przypisać do zmiennej lub literał elementu XML można dołączyć go.  
  
> [!NOTE]
>  Literał XML może obejmować wiele wierszy, bez używania znaków kontynuacji wiersza. Ta funkcja pozwala na kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał komentarza XML do wywołania <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy zawierający tekst komentarza XML "To jest komentarz".  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XComment>
- [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
