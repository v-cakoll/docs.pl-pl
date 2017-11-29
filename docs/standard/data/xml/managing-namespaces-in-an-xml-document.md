---
title: "Zarządzanie przestrzeni nazw w dokumencie XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: e9761afe8b56e15edba6e0319cce9a02501a6bb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="managing-namespaces-in-an-xml-document"></a>Zarządzanie przestrzeni nazw w dokumencie XML
Przestrzenie nazw XML skojarzenia elementu oraz nazwy atrybutów w dokumencie XML z wstępnie zdefiniowanych i niestandardowych identyfikatorów URI. Aby utworzyć skojarzenia, zdefiniuj prefiksów identyfikatorów URI przestrzeni nazw i używać tych prefiksów na kwalifikować się nazw elementów i atrybutów w danych XML. Przestrzenie nazw uniknąć konfliktów nazw elementów i atrybutów, a następnie włącz elementów i atrybutów o tej samej nazwie, można go obsłużyć ani zweryfikowany inaczej.  
  
<a name="declare"></a>   
## <a name="declaring-namespaces"></a>Deklarowanie przestrzeni nazw  
 Deklarowanie przestrzeni nazw dla elementu, należy użyć `xmlns:` atrybutu:  
  
 `xmlns:<name>=<"uri">`  
  
 gdzie `<name>` jest prefiks przestrzeni nazw i `<"uri">` jest identyfikator URI, który identyfikuje przestrzeni nazw. Po deklaracji prefiksu służy ona do uprawnione elementów i atrybutów w dokumencie XML i skojarzyć je z identyfikatorem URI przestrzeni nazw. Ponieważ prefiks przestrzeni nazw jest używana w całym dokumencie, należy go krótkich długości.  
  
 W tym przykładzie definiuje dwie `BOOK` elementów. Pierwszy element elementu kwalifikuje się według prefiksu, `mybook`, a drugi element kwalifikuje się według prefiksu, `bb`. Każdy prefiks jest skojarzona z inną przestrzeń nazw identyfikatora URI:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 Aby wskazują, że element jest częścią określonego obszaru nazw, Dodaj prefiks przestrzeni nazw do niego. Na przykład jeśli `Author` element należy do `mybook` przestrzeni nazw jest zadeklarowana jako `<mybook:Author>`.  
  
<a name="scope"></a>   
## <a name="declaration-scope"></a>Zakresu deklaracji  
 Przestrzeń nazw ma zastosowanie w punkcie deklaracji aż do zakończenia elementu został zadeklarowany w. W tym przykładzie przestrzeń nazw zdefiniowana w `BOOK` element nie ma zastosowania do elementów poza `BOOK` element, taki jak `Publisher` elementu:  
  
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
  
 Użycie kilku obszarów nazw w dokumencie XML, można zdefiniować jako domyślna przestrzeń nazw, można utworzyć dokumentu czyszcząca wyglądającej jednej przestrzeni nazw. Domyślna przestrzeń nazw jest zadeklarowana w elemencie głównym i ma zastosowanie do wszystkich elementów niekwalifikowane w dokumencie. Domyślne obszary nazw dotyczą tylko elementy nie atrybutów.  
  
 Aby użyć domyślnej przestrzeni nazw, Pomiń prefiks i dwukropka z deklaracją elementu:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a>Zarządzanie przestrzenie nazw  
 <xref:System.Xml.XmlNamespaceManager> Klasy przechowuje zbiór URI przestrzeni nazw i prefiksy oraz umożliwia wyszukiwania, dodawanie i usuwanie przestrzeni nazw z tej kolekcji. W niektórych kontekstach ta klasa jest wymagane w celu zapewnienia lepszej wydajności przetwarzania XML. Na przykład <xref:System.Xml.Xsl.XsltContext> klasy używa <xref:System.Xml.XmlNamespaceManager> obsługę języka XPath.  
  
 Menedżer przestrzeni nazw nie sprawdzają poprawność wszystkie przestrzenie nazw, ale założono, że prefiksy i przestrzenie nazw już została zweryfikowana i jest zgodny ze [przestrzenie nazw W3C](http://www.w3.org/TR/REC-xml-names/) specyfikacji.  
  
> [!NOTE]
>  [LINQ do XML](http://msdn.microsoft.com/library/f0fe21e9-ee43-4a55-b91a-0800e5782c13) nie używa <xref:System.Xml.XmlNamespaceManager> do zarządzania obszarami nazw. Zobacz [Praca z przestrzeni nazw XML](http://msdn.microsoft.com/library/e3003209-3234-45be-a832-47feb7927430) w dokumentacji LINQ informacji o zarządzaniu przestrzeni nazw w przypadku korzystania z LINQ do XML.  
  
 Poniżej przedstawiono niektóre zadania zarządzania i wyszukiwania można wykonywać za pomocą <xref:System.Xml.XmlNamespaceManager> klasy. Aby uzyskać dodatkowe informacje i przykłady skorzystaj z łączy na stronie dla każdej metody lub właściwości.  
  
|Do|Zastosowanie|  
|--------|---------|  
|Dodawanie przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.AddNamespace%2A>— Metoda|  
|Usuń przestrzeń nazw|<xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A>— Metoda|  
|Znajdź identyfikator URI dla domyślnej przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A>Właściwość|  
|Znajdź identyfikator URI dla prefiksu przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A>— Metoda|  
|Znajdź prefiks dla identyfikatora URI przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A>— Metoda|  
|Pobierz listę przestrzeni nazw w bieżącym węźle|<xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A>— Metoda|  
|Zakres przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.PushScope%2A>i <xref:System.Xml.XmlNamespaceManager.PopScope%2A> metody|  
|Sprawdź, czy prefiks jest zdefiniowana w bieżącym zakresie|<xref:System.Xml.XmlNamespaceManager.HasNamespace%2A>— Metoda|  
|Pobierz tabelę nazwę używaną do odszukania prefiksy oraz identyfikatorów URI|<xref:System.Xml.XmlNamespaceManager.NameTable%2A>Właściwość|  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Xml.XmlNamespaceManager>  
 [Dokumenty XML i dane](../../../../docs/standard/data/xml/index.md)
