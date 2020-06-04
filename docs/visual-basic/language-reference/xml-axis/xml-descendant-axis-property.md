---
title: Właściwości osi obiektu podrzędnego XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlPropertyDescendantsAxis
helpviewer_keywords:
- Visual Basic code, accessing XML
- XML descendant axis property [Visual Basic]
- descendant axis property [Visual Basic]
- XML axis [Visual Basic], descendant
- XML [Visual Basic], accessing
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
ms.openlocfilehash: 52544619171dbc7034baeb5feb61395d81096387
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400256"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Właściwości osi elementu podrzędnego XML (Visual Basic)

Zapewnia dostęp do elementów podrzędnych następujących obiektów: <xref:System.Xml.Linq.XElement> obiektu, <xref:System.Xml.Linq.XDocument> obiektu, kolekcji <xref:System.Xml.Linq.XElement> obiektów lub kolekcji <xref:System.Xml.Linq.XDocument> obiektów.

## <a name="syntax"></a>Składnia

```vb
object...<descendant>
```

## <a name="parts"></a>Części

`object`Wymagane. <xref:System.Xml.Linq.XElement>Obiekt, <xref:System.Xml.Linq.XDocument> obiekt, kolekcja <xref:System.Xml.Linq.XElement> obiektów lub kolekcja <xref:System.Xml.Linq.XDocument> obiektów.

`...<`Wymagane. Wskazuje początek właściwości osi elementu podrzędnego.

`descendant`Wymagane. Nazwa węzłów podrzędnych do uzyskania dostępu do formularza [ `prefix:]name` .

|Część|Opis|
|----------|-----------------|
|`prefix`|Opcjonalny. Prefiks przestrzeni nazw XML dla węzła podrzędnego. Musi to być globalna przestrzeń nazw XML, która jest definiowana przy użyciu `Imports` instrukcji.|
|`name`|Wymagany. Nazwa lokalna węzła podrzędnego. Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

`>`Wymagane. Oznacza koniec właściwości osi elementu podrzędnego.

## <a name="return-value"></a>Wartość zwracana

Kolekcja obiektów <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Uwagi

Aby uzyskać dostęp do węzłów podrzędnych według nazwy <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> z kolekcji <xref:System.Xml.Linq.XElement> lub obiektów, można użyć właściwości osi elementu podrzędnego XML <xref:System.Xml.Linq.XDocument> . Użyj właściwości XML, `Value` Aby uzyskać dostęp do wartości pierwszego węzła podrzędnego w zwróconej kolekcji. Aby uzyskać więcej informacji, zobacz [Właściwość wartości XML](xml-value-property.md).

Kompilator Visual Basic konwertuje właściwości osi elementu podrzędnego na wywołania <xref:System.Xml.Linq.XContainer.Descendants%2A> metody.

## <a name="xml-namespaces"></a>Przestrzenie nazw XML

Nazwa we właściwości osi podrzędnej może używać tylko przestrzeni nazw XML zadeklarowanych globalnie z `Imports` instrukcją. Nie można używać przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak uzyskać dostęp do wartości pierwszego węzła podrzędnego o nazwie `name` i wartości wszystkich węzłów podrzędnych o nazwie `phone` z `contacts` obiektu.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Ten kod wyświetla następujący tekst:

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Przykład

Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do wartości pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name` .

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Ten kod wyświetla następujący tekst:

`Name: Patrick Hines`

## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement>
- [Właściwości osi XML](index.md)
- [Literały XML](../xml-literals/index.md)
- [Tworzenie XML w Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Nazwy deklarowanych elementów XML oraz atrybuty](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
