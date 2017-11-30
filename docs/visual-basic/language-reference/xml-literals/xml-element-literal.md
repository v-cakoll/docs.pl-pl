---
title: "Literał elementu XML (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.XmlLiteralElement
helpviewer_keywords:
- XML element literal [Visual Basic]
- element literal [Visual Basic]
- XML literals [Visual Basic], element
ms.assetid: 95039642-7893-48b7-b23f-45a6c55d8f67
caps.latest.revision: "32"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: de5825a6af1dd1b93c3c85651125cf817dc564f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
  
     Wymagany. Otwiera początkowego tagu elementu.  
  
-   `name`  
  
     Wymagany. Nazwa elementu. Format jest jedną z następujących czynności:  
  
    -   Literały tekstowe dla nazwy elementu w postaci `[ePrefix:]eName`, gdzie:  
  
        |Część|Opis|  
        |---|---|  
        |`ePrefix`|Opcjonalny. Prefiks przestrzeni nazw XML dla elementu. Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana z `Imports` instrukcji w pliku lub na poziomie projektu lub lokalnej przestrzeni nazw XML, który jest zdefiniowany w tym elemencie lub elementu nadrzędnego.|  
        |`eName`|Wymagany. Nazwa elementu. Format jest jedną z następujących czynności:<br /><br /> — Tekst literału. Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />— Osadzone wyrażenie w postaci `<%= eNameExp %>`. Typ `eNameExp` musi być `String` lub typu, który jest niejawnie przekonwertować <xref:System.Xml.Linq.XName>.|  
  
    -   Osadzone wyrażenie w postaci `<%= nameExp %>`. Typ `nameExp` musi być `String` lub umożliwiają niejawnej konwersji na typ <xref:System.Xml.Linq.XName>. Wyrażenie osadzone nie jest dozwolona w tagu zamykającego elementu.  
  
-   `attributeList`  
  
     Opcjonalny. Lista atrybutów zadeklarowany w literału.  
  
     `attribute [ attribute ... ]`  
  
     Każdy `attribute` ma następujące parametry:  
  
    -   Atrybut przypisania w postaci `[aPrefix:]aName=aValue`, gdzie:  
  
        |Część|Opis|  
        |---|---|  
        |`aPrefix`|Opcjonalny. Prefiks przestrzeni nazw XML dla atrybutu. Musi być globalnej przestrzeni nazw XML, która jest zdefiniowana z `Imports` instrukcji lub lokalnej przestrzeni nazw XML, który jest zdefiniowany w tym elemencie lub elementu nadrzędnego.|  
        |`aName`|Wymagany. Nazwa atrybutu. Format jest jedną z następujących czynności:<br /><br /> — Tekst literału. Zobacz [nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md).<br />— Osadzone wyrażenie w postaci `<%= aNameExp %>`. Typ `aNameExp` musi być `String` lub typu, który jest niejawnie przekonwertować <xref:System.Xml.Linq.XName>.|  
        |`aValue`|Opcjonalny. Wartość atrybutu. Format jest jedną z następujących czynności:<br /><br /> — Tekst literału ujęty w cudzysłów.<br />— Osadzone wyrażenie w postaci `<%= aValueExp %>`. Dowolny typ jest dozwolone.|  
  
    -   Osadzone wyrażenie w postaci `<%= aExp %>`.  
  
-   `/>`  
  
     Opcjonalny. Wskazuje, czy element jest elementem pustym, bez zawartości.  
  
-   `>`  
  
     Wymagany. Kończy się tagu elementu początkowy lub jest pusty.  
  
-   `elementContents`  
  
     Opcjonalny. Zawartość elementu.  
  
     `content [ content ... ]`  
  
     Każdy `content` może być jedną z następujących czynności:  
  
    -   Literały tekstowe. Wszystkie biały znak w `elementContents` staje się istotne, jeśli ma żadnych literału tekstu.  
  
    -   Osadzone wyrażenie w postaci `<%= contentExp %>`.  
  
    -   Literał elementu XML.  
  
    -   Literał komentarza XML. Zobacz [literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md).  
  
    -   Literał instrukcji przetwarzania XML. Zobacz [literał instrukcji przetwarzającej kod XML](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md).  
  
    -   Literał CDATA XML. Zobacz [literał XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md).  
  
-   `</[name]>`  
  
     Opcjonalny. Reprezentuje tag zamykający dla elementu. Opcjonalny `name` parametru nie jest dozwolona, gdy jest to wynik wyrażenia osadzonego.  
  
## <a name="return-value"></a>Wartość zwracana  
 <xref:System.Xml.Linq.XElement> Obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Składnia literał elementu XML umożliwia utworzenie <xref:System.Xml.Linq.XElement> obiektów w kodzie.  
  
> [!NOTE]
>  Literał XML może obejmować wiele wierszy bez użycia znaki kontynuacji wiersza. Ta funkcja umożliwia kopiowanie zawartości z dokumentu XML i wklej go bezpośrednio do [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] program.  
  
 Osadzone wyrażenia w postaci `<%= exp %>` umożliwiają dodanie informacji dynamicznych na literał elementu XML. Aby uzyskać więcej informacji, zobacz [wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md).  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje literał elementu XML do wywołania <xref:System.Xml.Linq.XElement.%23ctor%2A> Konstruktor i, jeśli jest to wymagane, <xref:System.Xml.Linq.XAttribute.%23ctor%2A> konstruktora.  
  
## <a name="xml-namespaces"></a>Przestrzenie nazw XML  
 Prefiksy przestrzeni nazw XML są przydatne, gdy trzeba utworzyć literałów XML z elementami z tego samego obszaru nazw wiele razy w kodzie. Można użyć globalne prefiksy przestrzeni nazw XML, które definiują przy użyciu `Imports` instrukcji lub lokalnego prefiksy, które definiują przy użyciu `xmlns:xmlPrefix="xmlNamespace"` atrybutu składni. Aby uzyskać więcej informacji, zobacz [Importy — instrukcja (XML Namespace)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md).  
  
 Zgodnie z regułami zakresu dla obszarów nazw XML prefiksy lokalnego mają pierwszeństwo przed prefiksy globalnego. Jednak jeśli literał XML definiuje obszar nazw XML, tej przestrzeni nazw nie jest dostępny do wyrażeń, które są widoczne w wyrażenia osadzonego. Wyrażenia osadzonego mogą uzyskiwać dostęp tylko globalnej przestrzeni nazw XML.  
  
 [!INCLUDE[vbprvb](~/includes/vbprvb-md.md)] Kompilatora konwertuje każdego globalnej przestrzeni nazw XML, używany przez literał XML w jednej definicji lokalną przestrzeń nazw w wygenerowanym kodzie. Globalne przestrzenie nazw XML, które nie są używane, nie są wyświetlane w wygenerowanym kodzie.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia sposób tworzenia prostego elementu XML, która ma dwa puste elementy zagnieżdżone.  
  
 [!code-vb[VbXMLSamples#20](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_1.vb)]  
  
 W przykładzie przedstawiono następujący tekst. Zwróć uwagę, że literał zachowa struktury elementów pustych.  
  
```xml  
<outer>  
  <inner1></inner1>  
  <inner2 />  
</outer>  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład przedstawia użycie wyrażenia osadzone nadać nazwy elementu i utworzyć atrybuty.  
  
 [!code-vb[VbXMLSamples#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_2.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
```xml  
<book isbn="1234" author="My Author" year="1999" title="My Book" />  
```  
  
## <a name="example"></a>Przykład  
 Poniższy przykład deklaruje `ns` jako prefiks przestrzeni nazw XML. Następnie używa prefiks przestrzeni nazw w celu utworzenia literału XML i wyświetla formularz końcowego elementu.  
  
 [!code-vb[VbXMLSamples#22](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-element-literal_3.vb)]  
  
 Ten kod zawiera następujący tekst:  
  
```xml  
<ns:outer xmlns:ns="http://SomeNamespace">  
  <ns:middle xmlns:ns="http://NewNamespace">  
    <ns:inner1 />  
    <inner2 xmlns="http://SomeNamespace" />  
  </ns:middle>  
</ns:outer>  
```  
  
 Zwróć uwagę, że kompilator przekształcone prefiks globalnej przestrzeni nazw XML definicję prefiksu dla przestrzeni nazw XML. \<Ns:middle > prefiks przestrzeni nazw XML dla ponownie definiuje element \<ns:inner1 > elementu. Jednak \<ns:inner2 > element używa przestrzeń nazw zdefiniowana przez `Imports` instrukcji.  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.Linq.XElement>  
 [Nazwy deklarowanych elementów XML oraz atrybuty](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)  
 [Literał komentarza XML](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)  
 [Literał XML CDATA](../../../visual-basic/language-reference/xml-literals/xml-cdata-literal.md)  
 [Literały XML](../../../visual-basic/language-reference/xml-literals/index.md)  
 [Tworzenie XML w Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)  
 [Wyrażenia osadzone w XML](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)  
 [Imports — instrukcja (Namespace XML)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)
