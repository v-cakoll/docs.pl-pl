---
title: Właściwości osi elementu podrzędnego XML
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
ms.openlocfilehash: 90dc22d12be5566fa1ee40f6b0e48eff8088e67b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400269"
---
# <a name="xml-child-axis-property-visual-basic"></a>Właściwości osi elementu podrzędnego XML (Visual Basic)
Zapewnia dostęp do elementów podrzędnych jednego z następujących: <xref:System.Xml.Linq.XElement> obiektu, <xref:System.Xml.Linq.XDocument> obiektu, kolekcji <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.  
  
## <a name="syntax"></a>Składnia  
  
```vb  
object.<child>  
```  
  
## <a name="parts"></a>Części  
  
|Termin|Definicja|  
|---|---|  
|`object`|Wymagany. <xref:System.Xml.Linq.XElement>Obiekt, <xref:System.Xml.Linq.XDocument> obiekt, kolekcja <xref:System.Xml.Linq.XElement> obiektów lub kolekcja <xref:System.Xml.Linq.XDocument> obiektów.|  
|. <|Wymagany. Wskazuje początek właściwości osi podrzędnej.|  
|`child`|Wymagany. Nazwa węzłów podrzędnych do uzyskania dostępu do formularza `[prefix:]name` .<br /><br /> -   `Prefix`Obowiązkowe. Prefiks przestrzeni nazw XML dla węzła podrzędnego. Musi być globalną przestrzenią nazw XML zdefiniowaną za pomocą `Imports` instrukcji.<br />-   `Name`Potrzeb. Nazwa lokalnego węzła podrzędnego. Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|  
|>|Wymagany. Oznacza koniec właściwości osi podrzędnej.|  
  
## <a name="return-value"></a>Wartość zwracana  
 Kolekcja obiektów <xref:System.Xml.Linq.XElement>.  
  
## <a name="remarks"></a>Uwagi  
 Można użyć właściwości osi elementu podrzędnego XML, aby uzyskać dostęp do węzłów podrzędnych przy użyciu nazwy <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektu lub z kolekcji <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> obiektów. Użyj właściwości XML, `Value` Aby uzyskać dostęp do wartości pierwszego węzła podrzędnego w zwróconej kolekcji. Aby uzyskać więcej informacji, zobacz [Właściwość wartości XML](xml-value-property.md).  
  
 Kompilator Visual Basic konwertuje właściwości osi podrzędnej na wywołania <xref:System.Xml.Linq.XContainer.Elements%2A> metody.  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Nazwa we właściwości osi podrzędnej może używać tylko prefiksów przestrzeni nazw XML zadeklarowanych globalnie z `Imports` instrukcją. Nie może używać prefiksów przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md).  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z `contact` obiektu.  
  
 [!code-vb[VbXMLSamples#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#17)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak uzyskać dostęp do węzłów podrzędnych o nazwie `phone` z kolekcji zwróconej przez `contact` Właściwość osi elementu podrzędnego `contacts` obiektu.  
  
 [!code-vb[VbXMLSamples#18](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples7.vb#18)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Home Phone = 206-555-0144`  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name` .  
  
 [!code-vb[VbXMLSamples#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples8.vb#19)]  
  
 Ten kod wyświetla następujący tekst:  
  
 `Patrick Hines`  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement>
- [Właściwości osi XML](index.md)
- [Literały XML](../xml-literals/index.md)
- [Tworzenie XML w Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Nazwy deklarowanych elementów XML oraz atrybuty](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
