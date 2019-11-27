---
title: Literał CDATA XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralCdata
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
ms.openlocfilehash: 72e899e7bd30f2edf0e88207bb3b75bdf36fa11c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349435"
---
# <a name="xml-cdata-literal-visual-basic"></a>Literał CDATA XML (Visual Basic)
Literał reprezentujący obiekt <xref:System.Xml.Linq.XCData>.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Części  
 `<![CDATA[`  
 Wymagana. Wskazuje początek sekcji CDATA XML.  
  
 `content`  
 Wymagana. Zawartość tekstowa do wyświetlenia w sekcji CDATA XML.  
  
 `]]>`  
 Wymagana. Oznacza koniec sekcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 Obiekt <xref:System.Xml.Linq.XCData>.  
  
## <a name="remarks"></a>Uwagi  
 Sekcje CDATA XML zawierają nieprzetworzony tekst, który powinien być uwzględniony, ale nie jest analizowany, z XML, który zawiera. Sekcja CDATA XML może zawierać dowolny tekst. Obejmuje to zastrzeżone znaki XML. Sekcja CDATA XML zostanie zakończona z sekwencją "]] >". Oznacza to następujące kwestie:  
  
- Nie można użyć wyrażenia osadzonego w literale CDATA XML, ponieważ ogranicznik wyrażenia osadzonego są prawidłową zawartością elementu XML CDATA.  
  
- Sekcje CDATA XML nie mogą być zagnieżdżane, ponieważ `content` nie może zawierać wartości "]] >".  
  
 Do zmiennej można przypisać literał XML CDATA lub dodać go do literału elementu XML.  
  
> [!NOTE]
> Literał XML może obejmować wiele wierszy, ale nie używa znaków kontynuacji wiersza. Dzięki temu można skopiować zawartość z dokumentu XML i wkleić ją bezpośrednio do programu Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał XML CDATA na wywołanie konstruktora <xref:System.Xml.Linq.XCData.%23ctor%2A>.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład tworzy sekcję CDATA, która zawiera tekst "może zawierać literał \<tagi XML >".  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XCData>
- [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
