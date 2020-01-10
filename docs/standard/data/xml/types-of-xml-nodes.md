---
title: Typy węzłów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
ms.openlocfilehash: 83b8c09323e73a9b3ba7dea8d272d7d41d03add1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710092"
---
# <a name="types-of-xml-nodes"></a>Typy węzłów XML
Gdy dokument XML jest odczytywany do pamięci jako drzewo węzłów, podczas tworzenia węzłów są podejmowane decyzje dotyczące typów węzłów. Document Object Model XML (DOM) zawiera kilka rodzajów typów węzłów, określonych przez organizacja World Wide Web Consortium (W3C) i wymienionych w sekcji 1.1.1 model struktury DOM. Poniższa tabela zawiera listę typów węzłów, obiekt przypisany do tego typu węzła i Krótki opis każdego z nich.  
  
|Typ węzła DOM|Obiekt|Opis|  
|-------------------|------------|-----------------|  
|dokument|<xref:System.Xml.XmlDocument>|Kontener wszystkich węzłów w drzewie. Jest on również znany jako katalog główny dokumentu, który nie zawsze jest taki sam jak element główny.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Tymczasowy zbiór zawierający co najmniej jeden węzeł bez struktury drzewa.|  
|DocumentType|<xref:System.Xml.XmlDocumentType>|Reprezentuje węzeł `<!DOCTYPE…>`.|  
|Odwołanie do jednostki|<xref:System.Xml.XmlEntityReference>|Reprezentuje tekst odwołania do nierozwiniętej jednostki.|  
|Element|<xref:System.Xml.XmlElement>|Reprezentuje węzeł elementu.|  
|Atrybut|<xref:System.Xml.XmlAttribute>|Jest atrybutem elementu.|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|Jest węzłem przetwarzania instrukcji.|  
|Komentarz|<xref:System.Xml.XmlComment>|Węzeł komentarza.|  
|Tekst|<xref:System.Xml.XmlText>|Tekst należący do elementu lub atrybutu.|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|Reprezentuje CDATA.|  
|Jednostka|<xref:System.Xml.XmlEntity>|Reprezentuje deklaracje `<!ENTITY…>` w dokumencie XML, z podzestawu wewnętrznej definicji typu dokumentu (DTD) lub z zewnętrznych elementów DTD i jednostek parametrów.|  
|Notacja|<xref:System.Xml.XmlNotation>|Reprezentuje notację zadeklarowaną w DTD.|  
  
 Chociaż atrybut (*ATTR*) znajduje się w sekcji W3C dom Level 1 sekcja 1,2 interfejsy podstawowe jako węzeł, nie jest traktowany jako element podrzędny żadnego węzła elementu.  
  
 W poniższej tabeli przedstawiono dodatkowe typy węzłów, które nie są zdefiniowane przez konsorcjum W3C, ale są one dostępne do użycia w modelu obiektów programu Microsoft .NET Framework jako wyliczenia **XmlNodeType** . W związku z tym nie ma żadnej pasującej kolumny typu węzła DOM dla tych typów węzłów.  
  
|Typ węzła|Opis|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Reprezentuje węzeł deklaracji `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Reprezentuje znaczący biały znak, który jest białym znakiem w zawartości mieszanej.|  
|<xref:System.Xml.XmlWhitespace>|Reprezentuje biały znak w zawartości elementu.|  
|EndElement|Zwracany, gdy element **XmlReader** otrzymuje koniec elementu.<br /><br /> Przykład XML: **\</item >**<br /><br /> Aby uzyskać więcej informacji, zobacz temat <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Zwracany, gdy element **XmlReader** jest pobierany na koniec zamiany jednostki w wyniku wywołania <xref:System.Xml.XmlReader.ResolveEntity%2A>. Aby uzyskać więcej informacji, zobacz temat <xref:System.Xml.XmlNodeType>.|  
  
 Aby wyświetlić przykład kodu, który odczytuje w języku XML i używa konstrukcji case w typach węzłów do drukowania informacji o węźle i jego zawartości, zobacz <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.  
  
 Aby uzyskać więcej informacji na temat hierarchii obiektów typów węzłów i ich równoważnej nazwy obiektu, zobacz [Hierarchia XML Document Object Model (dom)](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md). Aby uzyskać więcej informacji na temat obiektów utworzonych w drzewie węzłów, zobacz [Mapowanie hierarchii obiektów na dane XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
