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
ms.openlocfilehash: 248f3cf31f686de3af2ea06012aa4a6d4f3f29fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942918"
---
# <a name="xml-cdata-literal-visual-basic"></a>Literał CDATA XML (Visual Basic)
Literał reprezentujący <xref:System.Xml.Linq.XCData> obiekt.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Części  
 `<![CDATA[`  
 Wymagane. Wskazuje początek sekcji CDATA XML.  
  
 `content`  
 Wymagana. Zawartość tekstowa do wyświetlenia w sekcji CDATA XML.  
  
 `]]>`  
 Wymagane. Oznacza koniec sekcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XCData> Obiekt.  
  
## <a name="remarks"></a>Uwagi  
 Sekcje CDATA XML zawierają nieprzetworzony tekst, który powinien być uwzględniony, ale nie jest analizowany, z XML, który zawiera. Sekcja CDATA XML może zawierać dowolny tekst. Obejmuje to zastrzeżone znaki XML. Sekcja CDATA XML zostanie zakończona z sekwencją "]] >". Oznacza to następujące kwestie:  
  
- Nie można użyć wyrażenia osadzonego w literale CDATA XML, ponieważ ogranicznik wyrażenia osadzonego są prawidłową zawartością elementu XML CDATA.  
  
- Sekcje CDATA XML nie mogą być zagnieżdżane `content` , ponieważ nie mogą zawierać wartości "]] >".  
  
 Do zmiennej można przypisać literał XML CDATA lub dodać go do literału elementu XML.  
  
> [!NOTE]
> Literał XML może obejmować wiele wierszy, ale nie używa znaków kontynuacji wiersza. Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał XML CDATA na wywołanie <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy sekcję CDATA, która zawiera tekst "może zawierać literały \<XML >.  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XCData>
- [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
