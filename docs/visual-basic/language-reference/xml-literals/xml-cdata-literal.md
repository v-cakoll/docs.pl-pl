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
ms.openlocfilehash: 889ec7f93d0503edac51652dda217c6a9f654f9b
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64621432"
---
# <a name="xml-cdata-literal-visual-basic"></a>Literał CDATA XML (Visual Basic)
Literał reprezentujący <xref:System.Xml.Linq.XCData> obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>Części  
 `<![CDATA[`  
 Wymagana. Oznacza początek sekcja XML CDATA.  
  
 `content`  
 Wymagana. Zawartość tekstowa pojawią się w sekcji XML CDATA.  
  
 `]]>`  
 Wymagana. Oznacza koniec sekcji.  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XCData> Obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Sekcje XML CDATA zawierają nieprzetworzony tekst, które powinny być włączone, lecz nie analizować za pomocą XML, który go zawiera. Sekcja XML CDATA może zawierać dowolny tekst. Obejmuje to zarezerwowanych znaków XML. Sekcja XML CDATA kończy się wraz z sekwencji "]] >". Oznacza to następujące kwestie:  
  
- Nie można użyć wyrażenia osadzone w literał CDATA XML, ponieważ ograniczniki osadzone wyrażenia są prawidłowa zawartość XML CDATA.  
  
- Nie można zagnieżdżać sekcji XML CDATA, ponieważ `content` nie może zawierać wartość "]] >".  
  
 Możesz przypisać literał CDATA XML do zmiennej lub ją dołączyć literał elementu XML.  
  
> [!NOTE]
>  Literał XML może obejmować wiele wierszy, ale nie mogą używać znaków kontynuacji wiersza. Dzięki temu można skopiować zawartość z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.  
  
 Kompilator Visual Basic konwertuje literał CDATA XML do wywołania <xref:System.Xml.Linq.XCData.%23ctor%2A> konstruktora.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład obejmuje tworzenie sekcji CDATA, która zawiera tekst "może zawierać literału \<XML > tagi".  
  
 [!code-vb[VbXMLSamples#23](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#23)]  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XCData>
- [Literał elementu XML](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
