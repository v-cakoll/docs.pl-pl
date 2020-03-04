---
title: Zarządzanie przestrzeniami nazw w dokumencie XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 682643fc-b848-4e42-8c0d-50deeaeb5f2a
ms.openlocfilehash: 7b219788895ab2f89fa285c2e1b7de62639bfcf9
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78160043"
---
# <a name="managing-namespaces-in-an-xml-document"></a>Zarządzanie przestrzeniami nazw w dokumencie XML
Przestrzenie nazw XML kojarzą nazwy elementów i atrybutów w dokumencie XML z niestandardowymi i wstępnie zdefiniowanymi identyfikatorami URI. Aby utworzyć te skojarzenia, należy zdefiniować prefiksy dla identyfikatorów URI przestrzeni nazw, a następnie użyć tych prefiksów do kwalifikowania nazw elementów i atrybutów w danych XML. Przestrzenie nazw uniemożliwiają kolizje nazw elementów i atrybutów, a elementy i atrybuty o tej samej nazwie mogą być obsługiwane i sprawdzane inaczej.  
  
<a name="declare"></a>
## <a name="declaring-namespaces"></a>Deklarowanie przestrzeni nazw  
 Aby zadeklarować przestrzeń nazw w elemencie, należy użyć atrybutu `xmlns:`:  
  
 `xmlns:<name>=<"uri">`  
  
 gdzie `<name>` jest prefiks przestrzeni nazw, a `<"uri">` jest identyfikatorem URI, który identyfikuje przestrzeń nazw. Po zadeklarowaniu prefiksu można go użyć do kwalifikowania elementów i atrybutów w dokumencie XML i kojarzenia ich z identyfikatorem URI przestrzeni nazw. Ponieważ prefiks przestrzeni nazw jest używany w całym dokumencie, powinien mieć krótki czas.  
  
 Ten przykład definiuje dwa elementy `BOOK`. Pierwszy element jest kwalifikowana za pomocą prefiksu, `mybook`, a drugi element jest kwalifikowana przez prefiks, `bb`. Każdy prefiks jest skojarzony z innym identyfikatorem URI przestrzeni nazw:  
  
```xml  
<mybook:BOOK xmlns:mybook="http://www.contoso.com/books.dtd">  
<bb:BOOK xmlns:bb="urn:blueyonderairlines">  
```  
  
 Aby wyrównać, że element jest częścią określonego obszaru nazw, Dodaj do niego prefiks przestrzeni nazw. Na przykład jeśli element `Author` należy do przestrzeni nazw `mybook`, zostanie zadeklarowany jako `<mybook:Author>`.  
  
<a name="scope"></a>
## <a name="declaration-scope"></a>Zakres deklaracji  
 Przestrzeń nazw zaczyna się od jej punktu deklaracji do końca elementu, w którym został zadeklarowany. W tym przykładzie przestrzeń nazw zdefiniowana w `BOOK` elementu nie ma zastosowania do elementów spoza elementu `BOOK`, takich jak `Publisher` elementu:  
  
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
  
 Przestrzeń nazw musi być zadeklarowana, zanim będzie można jej użyć, ale nie musi być wyświetlana u góry dokumentu XML.  
  
 W przypadku używania wielu przestrzeni nazw w dokumencie XML, można zdefiniować jeden obszar nazw jako domyślną przestrzeń nazw, aby utworzyć przejrzysty dokument szukania. Domyślna przestrzeń nazw jest zadeklarowana w elemencie głównym i ma zastosowanie do wszystkich niekwalifikowanych elementów w dokumencie. Domyślne przestrzenie nazw mają zastosowanie tylko do elementów, a nie do atrybutów.  
  
 Aby użyć domyślnej przestrzeni nazw, Pomiń prefiks i dwukropek z deklaracji w elemencie:  
  
```xml  
<BOOK xmlns="http://www.contoso.com/books.dtd">  
```  
  
## <a name="managing-namespaces"></a>Zarządzanie przestrzeniami nazw  
 Klasa <xref:System.Xml.XmlNamespaceManager> przechowuje kolekcję identyfikatorów URI przestrzeni nazw i ich prefiksów, a następnie umożliwia wyszukiwanie, Dodawanie i usuwanie przestrzeni nazw z tej kolekcji. W niektórych kontekstach Ta klasa jest wymagana w celu uzyskania lepszej wydajności przetwarzania kodu XML. Na przykład Klasa <xref:System.Xml.Xsl.XsltContext> używa <xref:System.Xml.XmlNamespaceManager> do obsługi XPath.  
  
 Menedżer przestrzeni nazw nie wykonuje żadnych walidacji w przestrzeniach nazw, ale zakłada, że prefiksy i przestrzenie nazw zostały już zweryfikowane i są zgodne ze specyfikacją [przestrzeni nazw W3C](https://www.w3.org/TR/REC-xml-names/) .  
  
> [!NOTE]
> LINQ TO XML in [C#](../../../csharp/programming-guide/concepts/linq/linq-to-xml-overview.md) i [Visual Basic](../../../visual-basic/programming-guide/concepts/linq/linq-to-xml.md) nie używać <xref:System.Xml.XmlNamespaceManager> do zarządzania przestrzeniami nazw. Zobacz [Praca z przestrzeniami nazwC#XML ()](../../../csharp/programming-guide/concepts/linq/namespaces-overview-linq-to-xml.md) i [Praca z przestrzeniami nazw XML (Visual Basic)](../../../visual-basic/programming-guide/concepts/linq/working-with-xml-namespaces.md) w dokumentacji LINQ, aby uzyskać informacje na temat zarządzania przestrzeniami nazw przy użyciu LINQ to XML.  
  
 Poniżej przedstawiono niektóre zadania zarządzania i wyszukiwania, które można wykonać za pomocą klasy <xref:System.Xml.XmlNamespaceManager>. Aby uzyskać więcej informacji i przykładów, postępuj zgodnie z linkami do strony odniesienia dla każdej metody lub właściwości.  
  
|Do|Użycie|  
|--------|---------|  
|Dodawanie przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.AddNamespace%2A>, Metoda|  
|Usuwanie przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.RemoveNamespace%2A>, Metoda|  
|Znajdź identyfikator URI dla domyślnej przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.DefaultNamespace%2A> Właściwość|  
|Znajdź identyfikator URI dla prefiksu przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.LookupNamespace%2A>, Metoda|  
|Znajdź prefiks dla identyfikatora URI przestrzeni nazw|<xref:System.Xml.XmlNamespaceManager.LookupPrefix%2A>, Metoda|  
|Pobierz listę przestrzeni nazw w bieżącym węźle|<xref:System.Xml.XmlNamespaceManager.GetNamespacesInScope%2A>, Metoda|  
|Określanie zakresu przestrzeni nazw|Metody <xref:System.Xml.XmlNamespaceManager.PushScope%2A> i <xref:System.Xml.XmlNamespaceManager.PopScope%2A>|  
|Sprawdź, czy prefiks jest zdefiniowany w bieżącym zakresie|<xref:System.Xml.XmlNamespaceManager.HasNamespace%2A>, Metoda|  
|Pobierz tabelę nazw służącą do wyszukiwania prefiksów i identyfikatorów URI|<xref:System.Xml.XmlNamespaceManager.NameTable%2A> Właściwość|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XmlNamespaceManager>
- [Dokumenty i dane XML](../../../../docs/standard/data/xml/index.md)
