---
title: Literał komentarza XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 8d9db66aabe344bd5c8f9a92ac8618b7bc1abb43
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349398"
---
# <a name="xml-comment-literal-visual-basic"></a>Literał komentarza XML (Visual Basic)
Literał reprezentujący obiekt <xref:System.Xml.Linq.XComment>.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`<!--`|Wymagany. Oznacza początek komentarza XML.|  
|`content`|Wymagany. Tekst, który ma być wyświetlany w komentarzu XML. Nie może zawierać serii dwóch łączników (--) ani kończyć się łącznikiem przylegającym do taga zamykającego.|  
|`-->`|Wymagany. Oznacza koniec komentarza XML.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt <xref:System.Xml.Linq.XComment>.  
  
## <a name="remarks"></a>Uwagi  
 Literały komentarza XML nie zawierają zawartości dokumentu; zawierają one informacje o dokumencie. Sekcja komentarza XML jest zakończona sekwencją "-->". Oznacza to następujące kwestie:  
  
- Nie można użyć wyrażenia osadzonego w literale komentarza XML, ponieważ ogranicznik wyrażenia osadzonego są prawidłową zawartością komentarza XML.  
  
- Sekcje komentarza XML nie mogą być zagnieżdżane, ponieważ `content` nie może zawierać wartości "-->".  
  
 Do zmiennej można przypisać literał komentarza XML lub dodać go do literału elementu XML.  
  
> [!NOTE]
> Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza. Ta funkcja umożliwia skopiowanie zawartości z dokumentu XML i wklejenie jej bezpośrednio do programu Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał komentarza XML na wywołanie konstruktora <xref:System.Xml.Linq.XComment.%23ctor%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy komentarz XML zawierający tekst "to jest komentarz".  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XComment>
- [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
