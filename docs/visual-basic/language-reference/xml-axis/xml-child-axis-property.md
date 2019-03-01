---
title: Właściwości osi elementu podrzędnego XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyChildAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML axis [Visual Basic], child
- child axis property [Visual Basic]
- XML child axis property [Visual Basic]
- XML [Visual Basic], accessing
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
ms.openlocfilehash: f8c0ab8f52e5819f799d21f7e23eb83684144605
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964453"
---
# <a name="xml-child-axis-property-visual-basic"></a>Właściwości osi elementu podrzędnego XML (Visual Basic)
Zapewnia dostęp do elementów podrzędnych w jednej z następujących czynności: <xref:System.Xml.Linq.XElement> obiektu <xref:System.Xml.Linq.XDocument> object, zbiór <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```  
object.<child>  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`object`|Wymagana. <xref:System.Xml.Linq.XElement> Obiektu <xref:System.Xml.Linq.XDocument> object, zbiór <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.|  
|.<|Wymagana. Oznacza początek właściwości osi elementu podrzędnego.|  
|`child`|Wymagana. Nazwy węzłów podrzędnych, aby uzyskać dostęp, w postaci [`prefix:]name`.<br /><br /> -   `Prefix` — Opcjonalne. Prefiks przestrzeni nazw XML dla węzła podrzędnego. Musi być globalnej przestrzeni nazw XML zdefiniowana z `Imports` instrukcji.<br />-   `Name` — Wymagane. Nazwa węzła podrzędnego lokalnego. Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Wymagana. Oznacza koniec właściwości osi elementu podrzędnego.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja <xref:System.Xml.Linq.XElement> obiektów.  
  
## <a name="remarks"></a>Uwagi  
 Umożliwia właściwości osi elementu podrzędnego XML access węzłów podrzędnych za pomocą nazwy z <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektu, lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów. Użyj pliku XML `Value` właściwość, aby uzyskać dostęp do wartości pierwszy węzeł podrzędny w zwrócona kolekcja. Aby uzyskać więcej informacji, zobacz [właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).  
  
 Kompilator Visual Basic konwertuje właściwości osi podrzędnej wywołania <xref:System.Xml.Linq.XContainer.Elements%2A> metody.  
  
## <a name="xml-namespaces"></a>Obszary nazw XML  
 Nazwa w właściwości osi elementu podrzędnego można użyć tylko takie prefiksy przestrzeni nazw XML, globalnie zadeklarowane za pomocą `Imports` instrukcji. Nie można go używać prefiksy przestrzeni nazw XML zadeklarowany lokalnie w literałach — element XML. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z `contact` obiektu.  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` w kolekcji zwróconej przez `contact` właściwości osi elementu podrzędnego z `contacts` obiektu.  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw tworzenie literałów XML i dostępem pierwszy węzeł podrzędny o nazwie kwalifikowanej `ns:name`.  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Xml.Linq.XElement>
- [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
