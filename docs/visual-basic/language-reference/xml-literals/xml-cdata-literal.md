---
title: Literał CDATA XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 999531d8146748fe491255663f0d2d17d056bcd4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603837"
---
# <a name="xml-cdata-literal-visual-basic"></a>Literał CDATA XML (Visual Basic)
Literał reprezentujący <xref:System.Xml.Linq.XCData> obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Części  
 `<![CDATA[`  
 Wymagana. Oznacza początek sekcji XML CDATA.  
  
 `content`  
 Wymagana. Zawartość tekstowa pojawią się w sekcji XML CDATA.  
  
 `]]>`  
 Wymagana. Oznacza koniec sekcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XCData> Obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Sekcji XML CDATA zawiera pierwotne tekst, który powinny być włączone, lecz nie przeanalizować, XML, który go zawiera. Sekcja XML CDATA mogą zawierać dowolny tekst. W tym zarezerwowanych znaków XML. W sekcji XML CDATA kończy sekwencja "]] >". Oznacza to następujące kwestie:  
  
-   Nie można użyć wyrażenia osadzonego w literał CDATA XML, ponieważ prawidłowa zawartość XML CDATA są ograniczniki wyrażenia osadzonego.  
  
-   Nie można zagnieździć sekcji XML CDATA, ponieważ `content` nie może zawierać wartości "]] >".  
  
 Można przypisać literał CDATA XML do zmiennej lub objąć literał elementu XML.  
  
> [!NOTE]
>  Literał XML może obejmować wiele wierszy, ale nie są używane znaki kontynuacji wiersza. Pozwala na kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał CDATA XML do wywołania <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy sekcji CDATA, która zawiera tekst "może zawierać literału \<XML > tagi".  
  
 [!code-vb[VbXMLSamples#23](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XCData>  
 [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
