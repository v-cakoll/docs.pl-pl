---
title: Kopiowanie istniejących węzłów z jednego dokumentu do innego
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 3caa78c1-3448-4b7b-b83c-228ee857635e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: e08c86ebdd71746520085844de5743692e84640e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965928"
---
# <a name="copying-existing-nodes-from-one-document-to-another"></a>Kopiowanie istniejących węzłów z jednego dokumentu do innego
Metoda **ImportNode** jest mechanizmem, za pomocą którego jest kopiowany węzeł lub całe poddrzewo węzła z jednego **dokumentu XmlDocument** do innego. Węzeł zwrócony z wywołania to kopia węzła z dokumentu źródłowego, w tym wartości atrybutów, nazwa węzła, typ węzła i wszystkie atrybuty powiązane z przestrzenią nazw, takie jak prefiks, nazwa lokalna i przestrzeń nazw Uniform Resource Identifier (URI). Dokument źródłowy nie jest zmieniany. Po zaimportowaniu węzła nadal trzeba dodać go do drzewa przy użyciu jednej z metod używanych do wstawiania węzłów.  
  
 Gdy węzeł zostanie dołączony do nowego dokumentu, nowy dokument jest właścicielem węzła. Przyczyną jest to, że każdy węzeł, gdy został utworzony, ma dokument będącego właścicielem, nawet jeśli węzły są tworzone w oddzielnych fragmentach dokumentu. Jest to wymaganie Document Object Model XML (DOM) i jest wymuszane przez projekt tworzenia fabryki w klasie XmlDocument . Na przykład, **CreateElement**, jest jedynym sposobem tworzenia nowych węzłów.  
  
 W zależności od typu węzła zaimportowanego węzła i wartości parametru głębokiego, dodatkowe informacje są kopiowane stosownie do potrzeb. Ta metoda próbuje zdublować zachowanie w przypadku, gdy fragment kodu XML lub HTML został skopiowany z jednego dokumentu do drugiego, a księgowanie dla faktu, że dla języka XML, dwa dokumenty mogą mieć różne definicje typu dokumentu (DTD).  
  
 W poniższej tabeli opisano określone zachowanie dla każdego typu węzła, który można zaimportować.  
  
|Typ węzła|parametr głębokiego ma wartość true|parametr głębokiego ma wartość false|  
|---------------|------------------------------|-------------------------------|  
|XmlAttribute|Wartość jest równa true dla elementu XmlAttribute. <xref:System.Xml.XmlAttribute.Specified%2A> Elementy podrzędne źródłowego elementu **XmlAttribute** są zaimportowane cyklicznie, a utworzone węzły w celu utworzenia odpowiedniego poddrzewa.|Parametr *głębokiego* nie ma zastosowania do węzłów **XmlAttribute** , ponieważ zawsze są one umieszczane w węzłach podrzędnych podczas importowania.|  
|XmlCDataSection|Kopiuje węzeł, w tym jego dane.|Kopiuje węzeł, w tym jego dane.|  
|XmlComment|Kopiuje węzeł, w tym jego dane.|Kopiuje węzeł, w tym jego dane.|  
|XmlDocumentFragment|Elementy podrzędne węzła źródłowego są zaimportowane cyklicznie, a utworzone węzły w celu utworzenia odpowiedniego poddrzewa.|Zostanie utworzony pusty **XmlDocumentFragment** .|  
|Element XmlDocumentType|Kopiuje węzeł, w tym jego dane. *|Kopiuje węzeł, w tym jego dane. *|  
|XmlElement|Elementy podrzędne elementu źródłowego są zaimportowane cyklicznie, a utworzone węzły w celu utworzenia odpowiedniego poddrzewa. **Uwaga:**  Atrybuty domyślne nie są kopiowane. Jeśli dokument importowany do definiuje atrybuty domyślne dla tej nazwy elementu, są one przypisane.|Wybrane węzły atrybutów elementu źródłowego są importowane, a wygenerowane węzły **XmlAttribute** są dołączone do nowego elementu. Węzły podrzędne nie są kopiowane. **Uwaga:**  Atrybuty domyślne nie są kopiowane. Jeśli dokument importowany do definiuje atrybuty domyślne dla tej nazwy elementu, są one przypisane.|  
|XmlEntityReference|Ponieważ dokumenty źródłowe i docelowe mogą mieć różne jednostki, ta metoda kopiuje tylko węzeł XmlEntityReference . Tekst zastępczy nie jest uwzględniany. Jeśli dokument docelowy ma zdefiniowaną jednostkę, jego wartość jest przypisana.|Ponieważ dokumenty źródłowe i docelowe mogą mieć różne jednostki, ta metoda kopiuje tylko węzeł XmlEntityReference . Tekst zastępczy nie jest uwzględniany. Jeśli dokument docelowy ma zdefiniowaną jednostkę, jego wartość jest przypisana.|  
|XmlProcessingInstruction|Kopiuje wartość docelową i dane z importowanego węzła.|Kopiuje wartość docelową i dane z importowanego węzła.|  
|XmlText|Kopiuje węzeł, w tym jego dane.|Kopiuje węzeł, w tym jego dane.|  
|XmlSignificantWhitespace|Kopiuje węzeł, w tym jego dane.|Kopiuje węzeł, w tym jego dane.|  
|XmlWhitespace|Kopiuje węzeł, w tym jego dane.|Kopiuje węzeł, w tym jego dane.|  
|XmlDeclaration|Kopiuje wartość docelową i dane z importowanego węzła.|Kopiuje wartość docelową i dane z importowanego węzła.|  
|Wszystkie inne typy węzłów|Nie można zaimportować tych typów węzłów.|Nie można zaimportować tych typów węzłów.|  
  
> [!NOTE]
> Chociaż węzły DocumentType można zaimportować, dokument może mieć tylko jeden DocumentType. Dlatego po zaimportowaniu typu dokumentu przed wstawieniem go do drzewa musisz upewnić się, że dokument nie zawiera żadnego typu dokumentu. Aby uzyskać informacje na temat usuwania węzłów, zobacz [usuwanie węzłów, zawartości i wartości z dokumentu XML](../../../../docs/standard/data/xml/removing-nodes-content-and-values-from-an-xml-document.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
