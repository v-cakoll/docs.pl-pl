---
title: Literał elementu XML (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
ms.openlocfilehash: 7bd47d2461ba86dfbd1d5ff5993382914116f9ba
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "58842255"
---
# <a name="xml-element-literal-visual-basic"></a>Literał elementu XML (Visual Basic)

Literał, która reprezentuje <xref:System.Xml.Linq.XElement> obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```xml  
<name [ attributeList ] />  
-or-  
<name [ attributeList ] > [ elementContents ] </[ name ]>  
```  
  
## <a name="parts"></a>Części  
  
-   `<`  
  
     Wymagana. Zostanie otwarty początkowego tagu elementu.  
  
-   `name`  
  
     Wymagana. Nazwa elementu. Format jest jedną z następujących czynności:  
  
    -   Tekst dosłowny dla nazwy elementu, w postaci `[ePrefix:]eName`, gdzie:  
  
        |Część|Opis|  
        |---|---|  
        |`ePrefix`|Opcjonalna. Prefiks przestrzeni nazw XML dla elementu. Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana za pomocą `Imports` instrukcja w pliku lub na poziomie projektu lub lokalną przestrzeń nazw XML, który jest zdefiniowany w tym elemencie lub elementu nadrzędnego.|  
        |`eName`|Wymagana. Nazwa elementu. Format jest jedną z następujących czynności:<br /><br /> -Literał tekstowy. Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />— Osadzone wyrażenie w formie `<%= eNameExp %>`. Typ `eNameExp` musi być `String` lub typ, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName>.|  
  
    -   Osadzone wyrażenie w formie `<%= nameExp %>`. Typ `nameExp` musi być `String` lub niejawnie konwertowane na typ <xref:System.Xml.Linq.XName>. Wyrażenia osadzone nie jest dozwolona w tagu zamykającego elementu.  
  
-   `attributeList`  
  
     Opcjonalna. Lista atrybutów zadeklarowany w literału.  
  
     `attribute [ attribute ... ]`  
  
     Każdy `attribute` ma jedną z poniższych składni:  
  
    -   Atrybut przypisania formularza `[aPrefix:]aName=aValue`, gdzie:  
  
        |Część|Opis|  
        |---|---|  
        |`aPrefix`|Opcjonalna. Prefiks przestrzeni nazw XML dla atrybutu. Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana za pomocą `Imports` instrukcji lub lokalną przestrzeń nazw XML, który jest zdefiniowany w tym elemencie lub elementu nadrzędnego.|  
        |`aName`|Wymagana. Nazwa atrybutu. Format jest jedną z następujących czynności:<br /><br /> -Literał tekstowy. Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />— Osadzone wyrażenie w formie `<%= aNameExp %>`. Typ `aNameExp` musi być `String` lub typ, który jest niejawnie konwertowany na <xref:System.Xml.Linq.XName>.|  
        |`aValue`|Opcjonalna. Wartość atrybutu. Format jest jedną z następujących czynności:<br /><br /> — Tekst literał ujęta w znaki cudzysłowu.<br />— Osadzone wyrażenie w formie `<%= aValueExp %>`. Dowolny typ jest dozwolone.|  
  
    -   Osadzone wyrażenie w formie `<%= aExp %>`.  
  
-   `/>`  
  
     Opcjonalna. Wskazuje, że element jest elementem pustym, bez zawartości.  
  
-   `>`  
  
     Wymagana. Kończy się tagu elementu zaczynające się lub jest pusty.  
  
-   `elementContents`  
  
     Opcjonalna. Zawartość elementu.  
  
     `content [ content ... ]`  
  
     Każdy `content` może być jedną z następujących czynności:  
  
    -   Literał tekstowy. Wszystkie biały znak w `elementContents` staje się istotne, jeśli dowolny tekst literału.  
  
    -   Osadzone wyrażenie w formie `<%= contentExp %>`.  
  
    -   Literał elementu XML.  
  
    -   Literał komentarza XML. Zobacz [literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).  
  
    -   Literał instrukcji przetwarzania XML. Zobacz [literał instrukcji przetwarzania XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).  
  
    -   Literał CDATA XML. Zobacz [literał XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).  
  
-   `</[name]>`  
  
     Opcjonalna. Reprezentuje tag zamykający dla elementu. Opcjonalny `name` parametr nie jest dozwolona, gdy jest wynikiem wyrażenia osadzone.  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XElement> Obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Składnia literał elementu XML służy do tworzenia <xref:System.Xml.Linq.XElement> obiektów w kodzie.  
  
> [!NOTE]
>  Literał XML może obejmować wiele wierszy, bez używania znaków kontynuacji wiersza. Ta funkcja pozwala na kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio w programie Visual Basic.  
  
 Osadzone wyrażenia formularza `<%= exp %>` umożliwiają dodawanie informacji dynamicznych do literał elementu XML. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 Kompilator Visual Basic konwertuje literał elementu XML do wywołania <xref:System.Xml.Linq.XElement.%23ctor%2A> Konstruktor i, jeśli jest to konieczne, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktora.  
  
## <a name="xml-namespaces"></a>Obszary nazw XML  
 Prefiksy przestrzeni nazw XML są przydatne, gdy trzeba utworzyć literałów XML przy użyciu tej samej przestrzeni nazw wiele razy w kodzie elementów. Możesz użyć globalne prefiksy przestrzeni nazw XML, które definiują przy użyciu `Imports` instrukcji lub lokalnej prefiksy, które definiują przy użyciu `xmlns:xmlPrefix="xmlNamespace"` atrybutu składni. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
 Zgodnie z regułami zakresu dla przestrzeni nazw XML lokalnej prefiksy mają pierwszeństwo przed globalne prefiksy. Jednak jeśli literał XML definiuje obszar nazw XML, przestrzeń nazw nie jest dostępne dla wyrażeń, które są wyświetlane w wyrażeniu osadzonych. Wyrażenia osadzone mogą uzyskiwać dostęp tylko globalnej przestrzeni nazw XML.  
  
 Kompilator Visual Basic konwertuje każdy globalnej przestrzeni nazw XML, używany przez literał XML w jednej definicji lokalną przestrzeń nazw w wygenerowanym kodzie. Globalnej przestrzeni nazw XML, które nie są używane, nie są wyświetlane w wygenerowanym kodzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak utworzyć prosty element XML, który ma dwa pustych elementów zagnieżdżonych.  
  
 [!code-vb[VbXMLSamples#20](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#20)]  
  
 W przykładzie wyświetlono następujący tekst. Należy zauważyć, że literału zachowuje strukturę pustych elementów.  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład pokazuje, jak za pomocą wyrażenia osadzone nazwy elementu i utworzyć atrybuty.  
  
 [!code-vb[VbXMLSamples#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples9.vb#21)]  
  
 Ten kod wyświetla następujący tekst:  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiksu przestrzeni nazw, aby utworzyć literał XML i wyświetla formularz końcowego elementu.  
  
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
  
 Należy zauważyć, że kompilator konwertowane prefiks globalnej przestrzeni nazw XML na definicję prefiksu przestrzeni nazw XML. \<Ns:middle > element redefiniuje prefiks przestrzeni nazw XML dla \<ns:inner1 > element. Jednak \<ns:inner2 > element korzysta z przestrzenią nazw zdefiniowaną przez `Imports` instrukcji.  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Linq.XElement>
- [Nazwy deklarowanych elementów i atrybutów XML](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)
- [Literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [Literał CDATA XML](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)
- [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)
- [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [Wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
- [Imports, instrukcja (przestrzeń nazw XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
