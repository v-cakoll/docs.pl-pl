---
title: Właściwości osi elementu podrzędnego XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Baisc]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 6040401ce3e98c835677be3c4cc7698013348f37
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44128998"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Właściwości osi elementu podrzędnego XML (Visual Basic)
Zapewnia dostęp do obiektów podrzędnych z następujących czynności: <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> object, zbiór <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a>Części  
 `object`  
 Wymagane. <xref:System.Xml.Linq.XElement> Obiektu <xref:System.Xml.Linq.XDocument> object, zbiór <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.  
  
 ...<  
 Wymagane. Oznacza początek właściwości osi elementu podrzędnego.  
  
 `descendant`  
 Wymagane. Nazwy węzłów podrzędnych dostępu, w postaci [`prefix``:`]`name`.  
  
|Część|Opis|  
|----------|-----------------|  
|`prefix`|Opcjonalna. Prefiks przestrzeni nazw XML dla elementów podrzędnych węzła. Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana za pomocą `Imports` instrukcji.|  
|`name`|Wymagane. Lokalna nazwa elementu podrzędnego węzła. Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Wymagane. Oznacza koniec właściwości osi elementu podrzędnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja <xref:System.Xml.Linq.XElement> obiektów.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości osi descendant XML umożliwia dostęp do węzłów podrzędnych za pomocą nazwy z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektu, lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów. Użyj pliku XML `Value` właściwość, aby uzyskać dostęp do wartości pierwszego elementu podrzędnego węzła w zwrócona kolekcja. Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Kompilator Visual Basic konwertuje właściwości osi elementu podrzędnego do wywołania <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.  
  
## <a name="xml-namespaces"></a>Obszary nazw XML  
 Nazwa właściwości osi elementu podrzędnego można użyć tylko obszary nazw XML globalnie zadeklarowane za pomocą `Imports` instrukcji. Nie może używać przestrzeni nazw XML zadeklarowany lokalnie w literałach — element XML. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać dostęp do wartości pierwszego elementu podrzędnego węzła o nazwie `name` i wartości wszystkich podrzędnych węzłów o nazwie `phone` z `contacts` obiektu.  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostęp do wartości pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
