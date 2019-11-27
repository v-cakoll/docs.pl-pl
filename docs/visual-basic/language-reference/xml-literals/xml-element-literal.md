---
title: Literał elementu XML
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: d6d900ca6868cfffe6b0e5b349321a79c5716c46
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347028"
---
# <a name="xml-element-literal-visual-basic"></a>Literał elementu XML (Visual Basic)

Literał reprezentujący obiekt <xref:System.Xml.Linq.XElement>.

## <a name="syntax"></a>Składnia

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>Części

- `<`

  Wymagana. Otwiera tag elementu początkowego.

- `name`

  Wymagana. Nazwa elementu. Jest to jeden z następujących formatów:

  - Tekst literału dla nazwy elementu w formularzu `[ePrefix:]eName`, gdzie:

    |Części|Opis|
    |---|---|
    |`ePrefix`|Opcjonalna. Prefiks przestrzeni nazw XML dla elementu. Musi być globalną przestrzenią nazw XML, która jest zdefiniowana za pomocą instrukcji `Imports` w pliku lub na poziomie projektu lub w lokalnej przestrzeni nazw XML, która jest zdefiniowana w tym elemencie lub elemencie nadrzędnym.|
    |`eName`|Wymagana. Nazwa elementu. Jest to jeden z następujących formatów:<br /><br /> -Literal Text. Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Osadzone wyrażenie `<%= eNameExp %>`formularza. Typ `eNameExp` musi być `String` lub typem, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName>.|

  - Wyrażenie osadzone `<%= nameExp %>`formularza. Typ `nameExp` musi być `String` lub typem niejawnie konwertowanym na <xref:System.Xml.Linq.XName>. Wyrażenie osadzone jest niedozwolone w tagu zamykającym elementu.

- `attributeList`

  Opcjonalna. Lista atrybutów zadeklarowanych w literale.

  `attribute [ attribute ... ]`

  Każda `attribute` ma jedną z następujących składni:

  - Przypisanie atrybutu w formularzu `[aPrefix:]aName=aValue`, gdzie:

    |Części|Opis|
    |---|---|
    |`aPrefix`|Opcjonalna. Prefiks przestrzeni nazw XML dla atrybutu. Musi to być globalna przestrzeń nazw XML, która jest zdefiniowana za pomocą instrukcji `Imports` lub lokalnego obszaru nazw XML zdefiniowanego w tym elemencie lub elemencie nadrzędnym.|
    |`aName`|Wymagana. Nazwa atrybutu. Jest to jeden z następujących formatów:<br /><br /> -Literal Text. Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Osadzone wyrażenie `<%= aNameExp %>`formularza. Typ `aNameExp` musi być `String` lub typem, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName>.|
    |`aValue`|Opcjonalna. Wartość atrybutu. Jest to jeden z następujących formatów:<br /><br /> -Literalny tekst ujęty w cudzysłów.<br />-Osadzone wyrażenie `<%= aValueExp %>`formularza. Dozwolony jest dowolny typ.|

  - Wyrażenie osadzone `<%= aExp %>`formularza.

- `/>`

  Opcjonalna. Wskazuje, że element jest pusty, bez zawartości.

- `>`

  Wymagana. Zamyka tag początkowego lub pustego elementu.

- `elementContents`

  Opcjonalna. Zawartość elementu.

  `content [ content ... ]`

  Każdy `content` może być jednym z następujących:

  - Tekst literału. Cały biały znak w `elementContents` będzie znaczący, jeśli istnieje dowolny tekst w postaci literału.

  - Wyrażenie osadzone `<%= contentExp %>`formularza.

  - Literal elementu XML.

  - Literał komentarza XML. Zobacz [literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).

  - Literał instrukcji przetwarzania XML. Zobacz [literał instrukcji przetwarzania XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).

  - Literał CDATA XML. Zobacz [LITERAŁ CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).

- `</[name]>`

  Opcjonalna. Reprezentuje tag zamykający elementu. Opcjonalny parametr `name` jest niedozwolony, jeśli jest wynikiem wyrażenia osadzonego.

## <a name="return-value"></a>Wartość zwracana

Obiekt <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Uwagi

Można użyć składni literału elementu XML do tworzenia obiektów <xref:System.Xml.Linq.XElement> w kodzie.

> [!NOTE]
> Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza. Ta funkcja umożliwia skopiowanie zawartości z dokumentu XML i wklejenie jej bezpośrednio do programu Visual Basic.

Osadzone wyrażenia w formularzu `<%= exp %>` umożliwiają dodawanie dynamicznych informacji do literału elementu XML. Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).

Kompilator Visual Basic konwertuje literał elementu XML na wywołania konstruktora <xref:System.Xml.Linq.XElement.%23ctor%2A> i, jeśli jest to wymagane, Konstruktor <xref:System.Xml.Linq.XAttribute.%23ctor%2A>.

## <a name="xml-namespaces"></a>Przestrzenie nazw XML

Prefiksy przestrzeni nazw XML są przydatne, gdy trzeba utworzyć literały XML z elementami z tego samego obszaru nazw wiele razy w kodzie. Można użyć globalnych prefiksów przestrzeni nazw XML, które można zdefiniować przy użyciu instrukcji `Imports` lub lokalnych prefiksów, które można zdefiniować przy użyciu składni atrybutów `xmlns:xmlPrefix="xmlNamespace"`. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).

Zgodnie z regułami określania zakresu dla przestrzeni nazw XML, lokalne prefiksy mają pierwszeństwo przed globalnymi prefiksami. Jeśli jednak literał XML definiuje przestrzeń nazw XML, ta przestrzeń nazw nie jest dostępna dla wyrażeń, które pojawiają się w wyrażeniu osadzonym. Wyrażenie osadzone może uzyskać dostęp tylko do globalnej przestrzeni nazw XML.

Kompilator Visual Basic konwertuje każdą globalną przestrzeń nazw XML, która jest używana przez literał XML w jedną definicję lokalnego obszaru nazw w wygenerowanym kodzie. Globalne obszary nazw XML, które nie są używane, nie są wyświetlane w wygenerowanym kodzie.

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak utworzyć prosty element XML, który ma dwa zagnieżdżone puste elementy.

[!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]

Przykład wyświetla następujący tekst. Zauważ, że literał zachowuje strukturę pustych elementów.

```xml
<outer>
  <inner1></inner1>
  <inner2 />
</outer>
```

## <a name="example"></a>Przykład

Poniższy przykład pokazuje, jak używać osadzonych wyrażeń, aby nazwać element i utworzyć atrybuty.

[!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]

Ten kod wyświetla następujący tekst:

```xml
<book isbn="1234" author="My Author" year="1999" title="My Book" />
```

## <a name="example"></a>Przykład

Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw w celu utworzenia literału XML i wyświetla ostateczną postać elementu.

[!code-vb[VbXMLSamples#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples10.vb#22)]

Ten kod wyświetla następujący tekst:

```xml
<ns:outer xmlns:ns="http://SomeNamespace">
  <ns:middle xmlns:ns="http://NewNamespace">
    <ns:inner1 />
    <inner2 xmlns="http://SomeNamespace" />
  </ns:middle>
</ns:outer>
```

Zwróć uwagę, że kompilator przekonwertował prefiks globalnej przestrzeni nazw XML na definicję prefiksu dla przestrzeni nazw XML. Element \<NS: Middle > ponownie definiuje prefiks przestrzeni nazw XML dla elementu \<NS: inner1 >. Jednak \<NS: inner2 > używa przestrzeni nazw zdefiniowanej przez instrukcję `Imports`.

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Literał CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie kodu XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports, instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
