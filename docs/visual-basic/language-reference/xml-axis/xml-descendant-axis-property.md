---
title: Właściwości osi elementu podrzędnego XML (Visual Basic)
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
ms.openlocfilehash: e2c3e01808d3eeb18f6753a5fc79b8627e7f323b
ms.sourcegitcommit: 1f12db2d852d05bed8c53845f0b5a57a762979c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2019
ms.locfileid: "72582229"
---
# <a name="xml-descendant-axis-property-visual-basic"></a>Właściwości osi elementu podrzędnego XML (Visual Basic)

Zapewnia dostęp do elementów podrzędnych następujących: obiektu <xref:System.Xml.Linq.XElement>, obiektu <xref:System.Xml.Linq.XDocument>, kolekcji obiektów <xref:System.Xml.Linq.XElement> lub kolekcji obiektów <xref:System.Xml.Linq.XDocument>.

## <a name="syntax"></a>Składnia

```vb
object...<descendant>
```

## <a name="parts"></a>Części

Wymagane `object`. Obiekt <xref:System.Xml.Linq.XElement>, obiekt <xref:System.Xml.Linq.XDocument>, kolekcja obiektów <xref:System.Xml.Linq.XElement> lub kolekcja obiektów <xref:System.Xml.Linq.XDocument>.

Wymagane `...<`. Wskazuje początek właściwości osi elementu podrzędnego.

Wymagane `descendant`. Nazwa węzłów podrzędnych, do których można uzyskać dostęp, w postaci [`prefix:]name`.

|Części|Opis|
|----------|-----------------|
|`prefix`|Opcjonalny. Prefiks przestrzeni nazw XML dla węzła podrzędnego. Musi to być globalna przestrzeń nazw XML, która jest definiowana przy użyciu instrukcji `Imports`.|
|`name`|Wymagany. Nazwa lokalna węzła podrzędnego. Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).|

Wymagane `>`. Oznacza koniec właściwości osi elementu podrzędnego.

## <a name="return-value"></a>Wartość zwracana

Kolekcja obiektów <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Uwagi

Aby uzyskać dostęp do węzłów podrzędnych według nazwy z obiektu <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument> lub z kolekcji obiektów <xref:System.Xml.Linq.XElement> lub <xref:System.Xml.Linq.XDocument>, można użyć właściwości osi elementu podrzędnego XML. Użyj właściwości `Value` XML, aby uzyskać dostęp do wartości pierwszego węzła podrzędnego w zwróconej kolekcji. Aby uzyskać więcej informacji, zobacz [Właściwość wartości XML](../../../visual-basic/language-reference/xml-axis/xml-value-property.md).

Kompilator Visual Basic konwertuje właściwości osi elementu podrzędnego na wywołania metody <xref:System.Xml.Linq.XContainer.Descendants%2A>.

## <a name="xml-namespaces"></a>Przestrzenie nazw XML

Nazwa we właściwości osi zależnej może używać tylko przestrzeni nazw XML zadeklarowanych globalnie za pomocą instrukcji `Imports`. Nie można używać przestrzeni nazw XML zadeklarowanych lokalnie w literałach elementu XML. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak uzyskać dostęp do wartości pierwszego węzła podrzędnego o nazwie `name` i wartości wszystkich węzłów podrzędnych o nazwie `phone` z obiektu `contacts`.

[!code-vb[VbXMLSamples#25](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples11.vb#25)]

Ten kod wyświetla następujący tekst:

`Name: Patrick Hines`

`Home Phone = 206-555-0144`

## <a name="example"></a>Przykład

Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i uzyskania dostępu do wartości pierwszego węzła podrzędnego przy użyciu kwalifikowanej nazwy `ns:name`.

[!code-vb[VbXMLSamples#26](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples12.vb#26)]

Ten kod wyświetla następujący tekst:

`Name: Patrick Hines`

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- [Właściwości osi XML](../../../visual-basic/language-reference/xml-axis/index.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
