---
title: Zarządzanie przestrzeniami nazw w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4b0ace73d81783852242a52bec006b0ad2edaadd
ms.sourcegitcommit: bd28ff1e312eaba9718c4f7ea272c2d4781a7cac
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2019
ms.locfileid: "56836139"
---
# <a name="managing-namespaces-in-an-xml-document"></a>Zarządzanie przestrzeniami nazw w dokumencie XML
Obszary nazw XML skojarzyć nazw elementów i atrybutów w dokumencie XML przy użyciu wstępnie zdefiniowanych i niestandardowych identyfikatorów URI. Aby utworzyć te skojarzenia, zdefiniuj prefiksów identyfikatorów URI przestrzeni nazw, a używać tych prefiksów do kwalifikowania nazwy elementów i atrybutów w danych XML. Przestrzenie nazw zapobiec kolizjom nazw elementów i atrybutów i umożliwić elementów i atrybutów o tej samej nazwie i obsługi sprawdzania poprawności w różny sposób.  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a>Deklarowanie przestrzeni nazw  
 Aby zadeklarować przestrzeni nazw w elemencie, należy użyć `xmlns:` atrybutu:  
  
 `xmlns:<name>=<"uri">`  
  
 gdzie `<name>` jest prefiks przestrzeni nazw i `<"uri">` jest identyfikator URI, który identyfikuje przestrzeni nazw. Po zadeklarowaniu prefiks służy do kwalifikowania elementów i atrybutów w dokumencie XML i skojarzyć je z identyfikatora URI obszaru nazw. Ponieważ prefiks przestrzeni nazw są używane w całym dokumencie, powinno być krótki długości.  
  
 W tym przykładzie definiuje dwa `BOOK` elementów. Pierwszy element kwalifikuje się według prefiksu, `mybook`, a drugi element kwalifikuje się według prefiksu, `bb`. Prefiksu dla każdego jest skojarzona z innej przestrzeni nazw identyfikatora URI:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 Oznaczającego, czy element jest częścią określonego obszaru nazw, należy dodać do niej prefiks przestrzeni nazw. Na przykład jeśli `Author` element należy do `mybook` przestrzeni nazw jest zadeklarowana jako `<mybook:Author>`.  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a>Zakresem deklaracji  
 Przestrzeń nazw jest efektywne w punkcie deklaracji, aż do zakończenia tego elementu został zadeklarowany w. W tym przykładzie przestrzeń nazw zdefiniowana w `BOOK` element nie ma zastosowania do elementów poza `BOOK` element, taki jak `Publisher` elementu:  
  
```xml  
<Author>Joe Smith</Author>  
<BOOK xmlns:book="http://www.contoso.com">  
    <title>My Wonderful Day</title>  
      <price>$3.95</price>  
</BOOK>  
<Publisher>  
    <Name>MSPress</Name>  
</Publisher>  
```  
  
 Przestrzeń nazw musi być zadeklarowana przed użyciem, ale nie ma być wyświetlany w górnej części dokumentu XML.  
  
 Gdy używasz wiele przestrzeni nazw w dokumencie XML, można zdefiniować jedną przestrzeń nazw jako domyślny obszar nazw, można utworzyć czyszcząca wyglądających dokumentu. Domyślny obszar nazw jest zadeklarowany w elemencie głównym i ma zastosowanie do wszystkich elementów niekwalifikowanej w dokumencie. Domyślne obszary nazw dotyczą tylko elementów nie do atrybutów.  
  
 Aby użyć domyślnej przestrzeni nazw, Pomiń prefiks i dwukropek, od deklaracji dla elementu:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a>Zarządzanie przestrzeniami nazw  
 <xref:System.Xml.XmlNamespaceManager> Klasa przechowuje kolekcję URI przestrzeni nazw i prefiksy i pozwalają, dodawania i usuwania przestrzeni nazw z tej kolekcji. W niektórych kontekstach ta klasa jest wymagana w celu zapewnienia lepszej wydajności przetwarzania XML. Na przykład <xref:System.Xml.Xsl.XsltContext> klasy używa <xref:System.Xml.XmlNamespaceManager> obsługę języka XPath.  
  
 Menedżer przestrzeni nazw nie wykonuje żadnych sprawdzania poprawności w przypadku przestrzeni nazw, ale założono, że prefiksy i przestrzenie nazw już zweryfikowana i są zgodne z [przestrzenie nazw W3C](https://www.w3.org/TR/REC-xml-names/) specyfikacji.  
  
> [!NOTE]
> [LINQ to XML (C#)](../../../csharp/programming-guide/concepts/linq/linq-to-xml.md) i [LINQ to XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) nie używaj <xref:System.Xml.XmlNamespaceManager> do zarządzania przestrzeniami nazw. Zobacz [Praca z przestrzeniami nazw XML (C#)](../../../csharp/programming-guide/concepts/linq/working-with-xml-namespaces.md) i [Praca z przestrzeniami nazw XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) w dokumentacji programu LINQ, informacje o zarządzaniu przestrzeni nazw w przypadku korzystania z LINQ to XML.  
  
 Poniżej przedstawiono niektóre z zadań zarządzania i wyszukiwania, można wykonywać za pomocą <xref:System.Xml.XmlNamespaceManager> klasy. Aby uzyskać więcej informacji i przykładów skorzystaj z linków na stronie dokumentacji każda metoda lub właściwość.  
  
|Zadanie|Zastosowanie|  
|--------|---------|  
|Dodawanie przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.AddNamespace%2A> — Metoda|  
|Usuwanie przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A> — Metoda|  
|Znajdź identyfikator URI dla domyślnej przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Właściwość|  
|Znajdź identyfikator URI dla prefiksu przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A> — Metoda|  
|Znajdź prefiks dla identyfikatora URI obszaru nazw|<xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A> — Metoda|  
|Pobierz listę przestrzeni nazw w bieżącym węźle|<xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A> — Metoda|  
|Określanie zakresu przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.PushScope%2A> i <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody|  
|Sprawdź, czy prefiks, który jest zdefiniowany w bieżącym zakresie|<xref:System.Xml.XmlNamespaceManager.HasNamespace%2A> — Metoda|  
|Pobierz tabelę nazw używany do wyszukiwania prefiksy i identyfikatory URI|<xref:System.Xml.XmlNamespaceManager.NameTable%2A> Właściwość|  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.XmlNamespaceManager>
- [Dokumenty i dane XML](../../../../docs/standard/data/xml/index.md)
