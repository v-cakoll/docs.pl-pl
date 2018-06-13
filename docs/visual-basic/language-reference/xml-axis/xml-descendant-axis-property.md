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
ms.openlocfilehash: 02bb87235efbdef8a5474fec9799757f75877876
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33604292"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Właściwości osi elementu podrzędnego XML (Visual Basic)
Zapewnia dostęp do następujących obiektów podrzędnych: <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> obiektu, to zbiór <xref:System.Xml.Linq.XElement> obiektów lub zbiór <xref:System.Xml.Linq.XDocument> obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
object...<descendant>  
```  
  
## <a name="parts"></a>Części  
 `object`  
 Wymagana. <xref:System.Xml.Linq.XElement> Obiektu <xref:System.Xml.Linq.XDocument> obiektu, to zbiór <xref:System.Xml.Linq.XElement> obiektów lub zbiór <xref:System.Xml.Linq.XDocument> obiektów.  
  
 ...<  
 Wymagana. Oznacza początek właściwości osi elementu podrzędnego.  
  
 `descendant`  
 Wymagana. Nazwy elementów podrzędnych węzłów do formularza [`prefix``:`]`name`.  
  
|Część|Opis|  
|----------|-----------------|  
|`prefix`|Opcjonalna. Prefiks przestrzeni nazw XML dla elementów podrzędnych węzła. Musi być globalnej przestrzeni nazw XML, który jest zdefiniowany przy użyciu `Imports` instrukcji.|  
|`name`|Wymagana. Lokalna nazwa elementu podrzędnego węzła. Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
  
 \>  
 Wymagana. Oznacza koniec właściwości osi elementu podrzędnego.  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja <xref:System.Xml.Linq.XElement> obiektów.  
  
## <a name="remarks"></a>Uwagi  
 Właściwości osi descendant XML umożliwia dostęp do elementów podrzędnych węzłów, nazwy z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiekt, lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów. Użyj pliku XML `Value` właściwość, aby uzyskać dostęp do wartości pierwszy węzeł elementu podrzędnego w zwracanej kolekcji. Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Kompilator Visual Basic konwertuje właściwości osi elementu podrzędnego wywołań <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Nazwa właściwości osi elementu podrzędnego można użyć tylko obszary nazw XML zadeklarowany globalnie z `Imports` instrukcji. Nie może używać lokalnie zadeklarowane w literałach XML elementu przestrzeni nazw XML. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób uzyskać dostęp do wartości pierwszego elementu podrzędnego węzła o nazwie `name` i wartości wszystkich węzłów elementów podrzędnych o nazwie `phone` z `contacts` obiektu.  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiks przestrzeni nazw do utworzenia literału XML i uzyskać dostęp do wartości pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
 `Name: Patrick Hines`  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
