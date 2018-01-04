---
title: "Typy węzłów XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 0fd196f4aed5d4faa3e703f639b927f001b50174
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="types-of-xml-nodes"></a>Typy węzłów XML
Podczas odczytywania dokumentu XML do pamięci jako drzewo węzłów typy węzłów, węzłom ustalonymi podczas tworzenia węzłów. XML modelu DOM (Document Object) ma kilka rodzajów typy węzłów, określany przez sieci World Wide Web konsorcjum W3C i wymienione w sekcji 1.1.1 strukturę modelu DOM. W poniższej tabeli wymieniono typy węzłów przypisane do tego typu węzła oraz krótki opis każdego obiektu.  
  
|Typ węzła modelu DOM|Obiekt|Opis|  
|-------------------|------------|-----------------|  
|dokument|<xref:System.Xml.XmlDocument>|Kontener wszystkich węzłów w drzewie. Jest nazywana głównego dokumentu, który nie jest zawsze taki sam jak element główny.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Zbiór tymczasowy, zawierający co najmniej jeden węzeł bez żadnych struktury drzewa.|  
|Typ dokumentu|<xref:System.Xml.XmlDocumentType>|Reprezentuje `<!DOCTYPE…>` węzła.|  
|Obiekt EntityReference|<xref:System.Xml.XmlEntityReference>|Reprezentuje tekst odwołanie-rozwinięty jednostki.|  
|Element|<xref:System.Xml.XmlElement>|Reprezentuje węzeł elementu.|  
|Attr|<xref:System.Xml.XmlAttribute>|Jest atrybutem elementu.|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|Jest węzłem instrukcji przetwarzania.|  
|Komentarz|<xref:System.Xml.XmlComment>|Węzeł komentarza.|  
|Tekst|<xref:System.Xml.XmlText>|Tekst należących do elementu lub atrybutu.|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|Reprezentuje CDATA.|  
|Jednostka|<xref:System.Xml.XmlEntity>|Reprezentuje `<!ENTITY…>` deklaracji w kodzie XML dokumentu z podzestawu wewnętrznego dokumentu typu definicji (DTD) lub zewnętrznej definicji DTD i jednostki parametru.|  
|Notacja|<xref:System.Xml.XmlNotation>|Reprezentuje notacji zadeklarowanej w definicji DTD.|  
  
 Nawet jeśli atrybut (*attr*) znajduje się w interfejsach podstawowych sekcji 1.2 W3C DOM poziomu 1 jako węzeł, nie wydaje się elementem podrzędnym węzła dowolnego elementu.  
  
 W poniższej tabeli przedstawiono typy dodatkowego węzła nie jest zdefiniowany przez W3C, jednak będą dostępne do użycia w modelu obiektów programu Microsoft .NET Framework jako **typ XmlNodeType** wyliczenia. Dlatego nie jest brak pasującego modelu DOM węzła kolumny typu dla tych typów węzłów.  
  
|Typ węzła|Opis|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Reprezentuje węzeł deklaracji `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Reprezentuje znaczący biały znak, który jest biały znak w zawartości mieszanej.|  
|<xref:System.Xml.XmlWhitespace>|Reprezentuje biały znak w zawartości elementu.|  
|EndElement|Zwracane, jeśli **XmlReader** pobiera do końca elementu.<br /><br /> Przykład XML:  **\< /elementu >**<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Zwracane, jeśli **XmlReader** pobiera w celu zastąpienia jednostki w wyniku wywołania <xref:System.Xml.XmlReader.ResolveEntity%2A>. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNodeType>.|  
  
 Aby wyświetlić przykładów kodu odczytuje w kodzie XML i używa wielkość konstrukcja na typy węzłów do wydruku informacji na temat węzła i jego zawartości, zobacz <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.  
  
 Więcej informacji o hierarchii obiektów typy węzłów i ich nazwy odpowiadającego mu obiektu, dla [hierarchii XML modelu DOM (Document Object)](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md). Aby uzyskać więcej informacji dotyczących obiektów utworzonych w węźle drzewa, zobacz [mapowania hierarchii obiektów do danych XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
