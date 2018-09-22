---
title: Typy węzłów XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 71d03b78-6898-4ce7-b0fc-1282573f31f7
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 623583f16c23b55c16f648fedcd039ca36f73b1f
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46532639"
---
# <a name="types-of-xml-nodes"></a>Typy węzłów XML
Podczas odczytywania dokumentu XML do pamięci jako drzewo węzłów typy węzłów dla węzłów są decyzję, gdy węzły zostaną utworzone. XML Document Object Model (DOM) ma kilka rodzajów typy węzłów, określane przez World Wide Web Consortium (W3C) i na liście w sekcji 1.1.1 strukturę modelu DOM. W poniższej tabeli wymieniono typy węzłów obiektu przypisane do tego typu węzła i krótki opis każdego z nich.  
  
|Typ węzła w modelu DOM|Obiekt|Opis|  
|-------------------|------------|-----------------|  
|dokument|<xref:System.Xml.XmlDocument>|Kontener wszystkich węzłów w drzewie. Jest również znane jako katalog główny dokumentów, które nie zawsze jest taki sam jak element główny.|  
|DocumentFragment|<xref:System.Xml.XmlDocumentFragment>|Pakiet tymczasowe, zawierający co najmniej jeden węzeł bez żadnych strukturę drzewa.|  
|Typ|<xref:System.Xml.XmlDocumentType>|Reprezentuje `<!DOCTYPE…>` węzła.|  
|Obiekt EntityReference|<xref:System.Xml.XmlEntityReference>|Reprezentuje tekst odwołanie do jednostki — rozwinięte.|  
|Element|<xref:System.Xml.XmlElement>|Reprezentuje węzeł elementu.|  
|attr|<xref:System.Xml.XmlAttribute>|Jest atrybutem elementu.|  
|ProcessingInstruction|<xref:System.Xml.XmlProcessingInstruction>|Jest węzeł przetwarzania instrukcji.|  
|Komentarz|<xref:System.Xml.XmlComment>|Węzeł komentarzy.|  
|Tekst|<xref:System.Xml.XmlText>|Tekst należących do elementu lub atrybutu.|  
|CDATASection|<xref:System.Xml.XmlCDataSection>|Reprezentuje CDATA.|  
|Jednostka|<xref:System.Xml.XmlEntity>|Reprezentuje `<!ENTITY…>` deklaracji w pliku XML dokumentu z podzbioru definition (DTD) typu wewnętrznego dokumentu lub w zewnętrznej definicji DTD i jednostki parametru.|  
|Notacja|<xref:System.Xml.XmlNotation>|Reprezentuje notacji zadeklarowanej w DTD.|  
  
 Nawet jeśli atrybut (*attr*) znajduje się w interfejsach podstawowych sekcji 1.2 W3C DOM poziomu 1 jako węzeł, nie uważa się elementem podrzędnym węzła dowolnego elementu.  
  
 W poniższej tabeli przedstawiono typy dodatkowy węzeł nie jest zdefiniowany przez organizację W3C, ale są one dostępne do użycia w modelu obiektów programu Microsoft .NET Framework jako **typ XmlNodeType** wyliczenia. Dlatego jest nie pasującego DOM typu kolumny węzła dla tych typów węzłów.  
  
|Typ węzła|Opis|  
|---------------|-----------------|  
|<xref:System.Xml.XmlDeclaration>|Reprezentuje węzeł deklaracji `<?xml version="1.0"…>`.|  
|<xref:System.Xml.XmlSignificantWhitespace>|Reprezentuje znaczące biały znak, który jest biały znak w zawartości mieszanej.|  
|<xref:System.Xml.XmlWhitespace>|Reprezentuje biały znak w zawartości elementu.|  
|EndElement|Zwracane, jeśli **XmlReader** pobiera-to-end elementu.<br /><br /> Przykładowy kod XML:  **\< /item >**<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNodeType>.|  
|EndEntity|Zwracane, jeśli **XmlReader** pobiera w celu zastąpienia jednostki w wyniku wywołania <xref:System.Xml.XmlReader.ResolveEntity%2A>. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNodeType>.|  
  
 Aby wyświetlić przykładowy kod odczytuje w formacie XML, który używa konstrukcji przypadków w ramach typów węzłów do drukowania informacji na temat węzła i jego zawartości, zobacz <xref:System.Xml.XmlSignificantWhitespace.NodeType%2A>.  
  
 Aby uzyskać więcej informacji na temat hierarchii obiektów na typy węzłów i ich nazwy obiektów równoważnych, zobacz [hierarchii XML Document Object Model (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom-hierarchy.md). Aby uzyskać więcej informacji na temat obiektów utworzonych w węźle drzewa, zobacz [mapowanie hierarchii obiektów na dane XML](../../../../docs/standard/data/xml/mapping-the-object-hierarchy-to-xml-data.md).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
