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
ms.openlocfilehash: d6a91de4e279816bafd29f46bb4f5422cbd934ff
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400192"
---
# <a name="xml-element-literal-visual-basic"></a>Literał elementu XML (Visual Basic)

Literał reprezentujący <xref:System.Xml.Linq.XElement> obiekt.

## <a name="syntax"></a>Składnia

```xml
<name [ attributeList ] />
-or-
<name [ attributeList ] > [ elementContents ] </[ name ]>
```

## <a name="parts"></a>Części

- `<`

  Wymagany. Otwiera tag elementu początkowego.

- `name`

  Wymagany. Nazwa elementu. Jest to jeden z następujących formatów:

  - Tekst literału dla nazwy elementu w formularzu `[ePrefix:]eName` , gdzie:

    |Część|Opis|
    |---|---|
    |`ePrefix`|Opcjonalny. Prefiks przestrzeni nazw XML dla elementu. Musi to być globalna przestrzeń nazw XML zdefiniowana za pomocą `Imports` instrukcji w pliku lub na poziomie projektu lub lokalnego obszaru nazw XML zdefiniowanego w tym elemencie lub elemencie nadrzędnym.|
    |`eName`|Wymagany. Nazwa elementu. Jest to jeden z następujących formatów:<br /><br /> -Literal Text. Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Osadzone wyrażenie formularza `<%= eNameExp %>` . Typ `eNameExp` musi być `String` lub typem, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName> .|

  - Wyrażenie osadzone formularza `<%= nameExp %>` . Typ elementu `nameExp` musi być `String` lub typem niejawnie konwertowanym na <xref:System.Xml.Linq.XName> . Wyrażenie osadzone jest niedozwolone w tagu zamykającym elementu.

- `attributeList`

  Opcjonalny. Lista atrybutów zadeklarowanych w literale.

  `attribute [ attribute ... ]`

  Każda `attribute` z nich ma jedną z następujących składni:

  - Przypisanie atrybutu w formularzu `[aPrefix:]aName=aValue` , gdzie:

    |Część|Opis|
    |---|---|
    |`aPrefix`|Opcjonalny. Prefiks przestrzeni nazw XML dla atrybutu. Musi być globalną przestrzenią nazw XML zdefiniowaną za pomocą `Imports` instrukcji lub lokalną przestrzenią nazw XML, która jest zdefiniowana w tym elemencie lub elemencie nadrzędnym.|
    |`aName`|Wymagany. Nazwa atrybutu. Jest to jeden z następujących formatów:<br /><br /> -Literal Text. Zobacz [nazwy zadeklarowanych elementów i atrybutów XML](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />-Osadzone wyrażenie formularza `<%= aNameExp %>` . Typ `aNameExp` musi być `String` lub typem, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName> .|
    |`aValue`|Opcjonalny. Wartość atrybutu. Jest to jeden z następujących formatów:<br /><br /> -Literalny tekst ujęty w cudzysłów.<br />-Osadzone wyrażenie formularza `<%= aValueExp %>` . Dozwolony jest dowolny typ.|

  - Wyrażenie osadzone formularza `<%= aExp %>` .

- `/>`

  Opcjonalny. Wskazuje, że element jest pusty, bez zawartości.

- `>`

  Wymagany. Zamyka tag początkowego lub pustego elementu.

- `elementContents`

  Opcjonalny. Zawartość elementu.

  `content [ content ... ]`

  Każdy `content` z nich może być jednym z następujących:

  - Tekst literału. Całe białe miejsce w programie `elementContents` jest znaczące, jeśli istnieje dowolny tekst w postaci literału.

  - Wyrażenie osadzone formularza `<%= contentExp %>` .

  - Literal elementu XML.

  - Literał komentarza XML. Zobacz [literał komentarza XML](xml-comment-literal.md).

  - Literał instrukcji przetwarzania XML. Zobacz [literał instrukcji przetwarzania XML](xml-processing-instruction-literal.md).

  - Literał CDATA XML. Zobacz [LITERAŁ CDATA XML](xml-cdata-literal.md).

- `</[name]>`

  Opcjonalny. Reprezentuje tag zamykający elementu. Opcjonalny `name` parametr jest niedozwolony, jeśli jest wynikiem wyrażenia osadzonego.

## <a name="return-value"></a>Wartość zwracana

Obiekt <xref:System.Xml.Linq.XElement>.

## <a name="remarks"></a>Uwagi

Można użyć składni literału elementu XML do tworzenia <xref:System.Xml.Linq.XElement> obiektów w kodzie.

> [!NOTE]
> Literał XML może obejmować wiele wierszy bez używania znaków kontynuacji wiersza. Ta funkcja umożliwia skopiowanie zawartości z dokumentu XML i wklejenie jej bezpośrednio do programu Visual Basic.

Osadzone wyrażenia formularza `<%= exp %>` umożliwiają dodawanie dynamicznych informacji do literału elementu XML. Aby uzyskać więcej informacji, zobacz [Embedded Expressions in XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md).

Kompilator Visual Basic konwertuje literał elementu XML na wywołania <xref:System.Xml.Linq.XElement.%23ctor%2A> konstruktora i, jeśli jest wymagany, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> Konstruktor.

## <a name="xml-namespaces"></a>Przestrzenie nazw XML

Prefiksy przestrzeni nazw XML są przydatne, gdy trzeba utworzyć literały XML z elementami z tego samego obszaru nazw wiele razy w kodzie. Można użyć globalnych prefiksów przestrzeni nazw XML, które można zdefiniować przy użyciu `Imports` instrukcji lub lokalnych prefiksów, które można zdefiniować przy użyciu `xmlns:xmlPrefix="xmlNamespace"` składni atrybutu. Aby uzyskać więcej informacji, zobacz [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md).

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

Zwróć uwagę, że kompilator przekonwertował prefiks globalnej przestrzeni nazw XML na definicję prefiksu dla przestrzeni nazw XML. \<ns:middle>Element ponownie definiuje prefiks przestrzeni nazw XML dla \<ns:inner1> elementu. Jednak \<ns:inner2> element używa przestrzeni nazw zdefiniowanej przez `Imports` instrukcję.

## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Linq.XElement>
- [Nazwy deklarowanych elementów XML oraz atrybuty](../../programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Literał komentarza XML](xml-comment-literal.md)
- [Literał CDATA XML](xml-cdata-literal.md)
- [Literały XML](index.md)
- [Tworzenie XML w Visual Basic](../../programming-guide/language-features/xml/creating-xml.md)
- [Wyrażenia osadzone w XML](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports — Instrukcja (przestrzeń nazw XML)](../statements/imports-statement-xml-namespace.md)
