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
ms.openlocfilehash: 93c1346e54106b93f3932a494dea85d082ec994d
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400218"
---
# <a name="xml-comment-literal-visual-basic"></a>Literał komentarza XML (Visual Basic)
Literał reprezentujący <xref:System.Xml.Linq.XComment> obiekt.  
  
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
  
- Sekcje komentarza XML nie mogą być zagnieżdżane, ponieważ `content` nie mogą zawierać wartości "-->".  
  
 Do zmiennej można przypisać literał komentarza XML lub dodać go do literału elementu XML.  
  
> [!NOTE]
> Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza. Ta funkcja umożliwia skopiowanie zawartości z dokumentu XML i wklejenie jej bezpośrednio do programu Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał komentarza XML na wywołanie <xref:System.Xml.Linq.XComment.%23ctor%2A> konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy komentarz XML zawierający tekst "to jest komentarz".  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XComment>
- [Literał elementu XML](xml-element-literal.md)
- [Literały XML](index.md)
- [Tworzenie XML w Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
