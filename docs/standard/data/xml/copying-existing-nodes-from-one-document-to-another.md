---
title: "Kopiowanie istniejących węzłów z jednego dokumentu do innego"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 958dccfc184857b0edd12cd1d9afe7b3b468b1e6
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Kopiowanie istniejących węzłów z jednego dokumentu do innego
**ImportNode** metody to mechanizm, za pomocą którego węzeł lub całego węzła poddrzewo zostaną skopiowane z jednego **XmlDocument** na inny. Węzeł zwracana z wywołania jest kopią węzła w dokumencie źródłowym, w tym wartości atrybutów, nazwa węzła typu węzła i wszystkie atrybuty związane z przestrzeni nazw, takie jak prefiks, nazwę lokalną i przestrzeń nazw identyfikatora URI (Uniform Resource). Dokument źródłowy nie zostanie zmieniona. Po zaimportowaniu tego węzła, musisz dodać je do drzewa przy użyciu jednej z metod służy do wstawiania węzłów.  
  
 Gdy węzeł jest dołączony do jego nowy dokument, nowy dokument jest właścicielem tego węzła. Przyczyną jest podczas tworzenia każdego węzła dokument będący właścicielem, nawet jeśli węzły są tworzone w fragmenty innego dokumentu. Jest wymaganie od XML modelu DOM (Document Object) i są wymuszane przez projekt tworzenie fabryki na **XmlDocument** klasy. Na przykład **funkcji CreateElement**, jest to jedyny sposób, aby utworzyć nowe węzły.  
  
 W zależności od typu węzła importowanych węzła i wartość *głębokie* parametru, dodatkowe informacje są kopiowane jako odpowiednie. Ta metoda próbuje duplikatów zachowanie oczekiwane, jeśli fragment XML lub źródła HTML został skopiowany z jednego dokumentu do innego dla faktów, XML, dwa dokumenty może mieć innego dokumentu definicje typów (elementów DTD).  
  
 W poniższej tabeli opisano określone zachowanie dla każdego typu węzła, który można zaimportować.  
  
|Typ węzła|*głębokie* parametr ma wartość true|*głębokie* parametr ma wartość false|  
|---------------|------------------------------|-------------------------------|  
|Element XmlAttribute|<xref:System.Xml.XmlAttribute.Specified%2A> Ustawiono **true** na XmlAttribute. Elementy podrzędne źródła **XmlAttribute** rekursywnie zaimportowane i wynikowy węzły są odbierane do utworzenia odpowiedniego poddrzewa.|*Głębokie* parametru nie ma zastosowania do **XmlAttribute** węzłów, ponieważ zawierają one ich węzłów podrzędnych z nimi po zaimportowaniu.|  
|XmlCDataSection|Kopiuje węzła, w tym jego dane.|Kopiuje węzła, w tym jego dane.|  
|XmlComment|Kopiuje węzła, w tym jego dane.|Kopiuje węzła, w tym jego dane.|  
|XmlDocumentFragment|Elementów podrzędnych węzła źródłowego są rekursywnie zaimportowane i wynikowy węzłów odbierane do utworzenia odpowiedniego poddrzewa.|Pusta **XmlDocumentFragment** jest tworzony.|  
|XmlDocumentType|Kopiuje węzła, w tym jego data.*|Kopiuje węzła, w tym jego data.*|  
|Element XmlElement|Elementy podrzędne elementu źródła są rekursywnie zaimportowane i wynikowy węzłów odbierane do utworzenia odpowiedniego poddrzewa. **Uwaga:** domyślne atrybuty nie są kopiowane. Jeśli importowany do dokumentu definiuje domyślne atrybuty dla tej nazwy elementu, te są przypisane.|Określony atrybut węzły elementu źródłowego zostały zaimportowane i wygenerowany **XmlAttribute** węzły są dołączone do nowego elementu. Węzły podrzędne nie są kopiowane. **Uwaga:** domyślne atrybuty nie są kopiowane. Jeśli importowany do dokumentu definiuje domyślne atrybuty dla tej nazwy elementu, te są przypisane.|  
|XmlEntityReference|Ponieważ dokumenty źródłowy i docelowy mogą mieć jednostek określony inaczej, ta metoda tylko kopiuje **XmlEntityReference** węzła. Tekst zastępczy nie jest włączony. Jeśli plik docelowy ma jednostki zdefiniowane, jego wartość jest przypisany.|Ponieważ dokumenty źródłowy i docelowy mogą mieć jednostek określony inaczej, ta metoda tylko kopiuje **XmlEntityReference** węzła. Tekst zastępczy nie jest włączony. Jeśli plik docelowy ma jednostki zdefiniowane, jego wartość jest przypisany.|  
|XmlProcessingInstruction|Kopiuje wartości docelowej i danych z węzła zaimportowany.|Kopiuje wartości docelowej i danych z węzła zaimportowany.|  
|XmlText|Kopiuje węzła, w tym jego dane.|Kopiuje węzła, w tym jego dane.|  
|XmlSignificantWhitespace|Kopiuje węzła, w tym jego dane.|Kopiuje węzła, w tym jego dane.|  
|XmlWhitespace|Kopiuje węzła, w tym jego dane.|Kopiuje węzła, w tym jego dane.|  
|XmlDeclaration|Kopiuje wartości docelowej i danych z węzła zaimportowany.|Kopiuje wartości docelowej i danych z węzła zaimportowany.|  
|Wszystkie inne typy węzła|Nie można zaimportować typu węzła.|Nie można zaimportować typu węzła.|  
  
> [!NOTE]
>  Mimo że można zaimportować węzłów dokumentu, dokument może mieć tylko jeden typ dokumentu. Dlatego po zaimportowaniu typu dokumentu przed wstawieniem do drzewa, musisz upewnić się, że nie ma dokumentu typu w dokumencie. Aby uzyskać informacje dotyczące usuwania węzłów, zobacz [wartości z dokumentu XML, zawartość i usuwanie węzłów](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
