---
title: Kopiowanie istniejących węzłów z jednego dokumentu do innego
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 744c97e8728d0a65bff8e7bb7a7dbb298afe1800
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "44036372"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Kopiowanie istniejących węzłów z jednego dokumentu do innego
**ImportNode** metoda to mechanizm, za pomocą którego węzła lub poddrzewo w całym węźle jest kopiowany z jednego **XmlDocument** do innego. Węzeł zwracana z wywołania jest kopią węzeł w dokumencie źródłowym, w tym wartości atrybutów, nazwa węzła, typ węzła i wszystkich atrybutów związane z przestrzeni nazw, takie jak prefiks, lokalna nazwa i identyfikator (URI nazw). Dokument źródłowy nie jest zmieniany. Po zaimportowaniu węzeł nadal trzeba dodać je do drzewa za pomocą jednej z metod służy do wstawiania węzłów.  
  
 Gdy węzeł jest dołączony do jej nowy dokument, nowy dokument jest właścicielem węzła. Przyczyną jest to, czy każdy węzeł podczas tworzenia ma będącej właścicielem dokumentu, nawet jeśli węzły są tworzone we fragmentach oddzielny dokument. To jest to wymagane XML Document Object Model (DOM) i są wymuszane przez projekt tworzenia fabryki na **XmlDocument** klasy. Na przykład **CreateElement**, jest to jedyny sposób, aby utworzyć nowe węzły.  
  
 W zależności od typu węzła importowanych węzła i wartość *głębokiego* parametru, dodatkowe informacje są kopiowane odpowiednio. Ta metoda próbuje duplikatów zachowanie oczekiwane, jeśli fragment kodu XML lub źródła HTML został skopiowany z jednego dokumentu do innego, księgowość fakt, że dla formatu XML dwa dokumenty może mieć definicji typu z innego dokumentu (pliki DTD).  
  
 W poniższej tabeli opisano określone zachowanie dla każdego typu węzła, który można zaimportować.  
  
|Typ węzła|*głębokie* parametr ma wartość true|*głębokie* parametr ma wartość false|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A> Ustawiono **true** na XmlAttribute. Elementy podrzędne źródło **XmlAttribute** rekursywnie zaimportowany i wynikowy węzły są odbierane w celu utworzenia odpowiedniego poddrzewo.|*Głębokiego* parametru nie ma zastosowania do **XmlAttribute** węzłów, ponieważ zawierają one ich węzłów podrzędnych z nimi po zaimportowaniu.|  
|XmlCDataSection|Kopiuje węzła, w tym jego danych.|Kopiuje węzła, w tym jego danych.|  
|XmlComment|Kopiuje węzła, w tym jego danych.|Kopiuje węzła, w tym jego danych.|  
|XmlDocumentFragment|Elementy podrzędne węzła źródłowego są rekursywnie zaimportowany i wynikowy węzły ponownie w celu utworzenia odpowiednich poddrzewa.|Pusta **XmlDocumentFragment** zostanie utworzony.|  
|XmlDocumentType|Kopiuje węzła, w tym jego data.*|Kopiuje węzła, w tym jego data.*|  
|XmlElement|Elementy podrzędne elementu źródłowego są rekursywnie zaimportowany i wynikowy węzły ponownie w celu utworzenia odpowiednich poddrzewa. **Uwaga:** atrybuty domyślne nie są kopiowane. Jeśli dokument, zostaną zaimportowane do definiuje atrybutów domyślnych dla tej nazwy elementu, te są przypisywane.|Określony atrybut węzłów elementu źródłowego są importowane i generowane **XmlAttribute** węzły są dołączone do nowego elementu. Węzły podrzędne nie są kopiowane. **Uwaga:** atrybuty domyślne nie są kopiowane. Jeśli dokument, zostaną zaimportowane do definiuje atrybutów domyślnych dla tej nazwy elementu, te są przypisywane.|  
|XmlEntityReference|Ponieważ dokumentów źródłowych i docelowych może mieć jednostki zdefiniowanych inaczej, ta metoda tylko kopiuje **XmlEntityReference** węzła. Tekst zastępczy nie jest włączony. Jeśli plik docelowy zawiera jednostki zdefiniowane, jego wartość zostanie przypisany.|Ponieważ dokumentów źródłowych i docelowych może mieć jednostki zdefiniowanych inaczej, ta metoda tylko kopiuje **XmlEntityReference** węzła. Tekst zastępczy nie jest włączony. Jeśli plik docelowy zawiera jednostki zdefiniowane, jego wartość zostanie przypisany.|  
|XmlProcessingInstruction|Kopiuje wartości docelowej i danych z zaimportowanych węzła.|Kopiuje wartości docelowej i danych z zaimportowanych węzła.|  
|XmlText|Kopiuje węzła, w tym jego danych.|Kopiuje węzła, w tym jego danych.|  
|XmlSignificantWhitespace|Kopiuje węzła, w tym jego danych.|Kopiuje węzła, w tym jego danych.|  
|XmlWhitespace|Kopiuje węzła, w tym jego danych.|Kopiuje węzła, w tym jego danych.|  
|XmlDeclaration|Kopiuje wartości docelowej i danych z zaimportowanych węzła.|Kopiuje wartości docelowej i danych z zaimportowanych węzła.|  
|Inne typy węzłów|Nie można zaimportować te typy węzłów.|Nie można zaimportować te typy węzłów.|  
  
> [!NOTE]
>  Mimo że można zaimportować węzłów typu dokumentu, dokument może mieć tylko jeden typ. Po zaimportowaniu typ dokumentu przed wstawieniem do drzewa, musisz upewnić się, że istnieje więc żaden typ dokumentu w dokumencie. Aby uzyskać informacje na temat usuwania węzłów, zobacz [usuwanie węzłów, zawartości i wartości z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
