---
title: Tworzenie nowych węzłów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
ms.openlocfilehash: f48990286405baee347becef87d0511cd42e9e77
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711002"
---
# <a name="create-new-nodes-in-the-dom"></a>Tworzenie nowych węzłów w modelu DOM
<xref:System.Xml.XmlDocument> ma metodę Create dla wszystkich typów węzłów. Podaj metodę o nazwie, gdy jest to wymagane, oraz zawartość lub inne parametry dla tych węzłów, które mają zawartość (na przykład węzeł tekstowy) i węzeł jest tworzony. Poniższe metody to te, które wymagają nazwy i kilku innych parametrów wypełnionych w celu utworzenia odpowiedniego węzła.  
  
- <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
- <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
- <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
- <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
- <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
- <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
- <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
- <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 Inne typy węzłów mają więcej wymagań niż tylko dostarczanie danych do parametrów.  
  
 Aby uzyskać informacje na temat atrybutów, zobacz [Tworzenie nowych atrybutów dla elementów w modelu dom](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md). Aby uzyskać informacje na temat walidacji nazw elementów i atrybutów, zobacz [Weryfikacja nazwy elementu i atrybutu XML podczas tworzenia nowych węzłów](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md). Aby uzyskać informacje na temat tworzenia odwołań do jednostek, zobacz [Tworzenie nowych odwołań do jednostek](../../../../docs/standard/data/xml/creating-new-entity-references.md). Aby uzyskać informacje na temat sposobu, w jaki przestrzenie nazw wpływają na rozszerzanie odwołań do jednostek, zobacz [przestrzeń nazw ma wpływ na rozszerzanie odwołania do jednostek dla nowych węzłów zawierających elementy i atrybuty](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).  
  
 Po utworzeniu nowych węzłów dostępne są kilka metod wstawienia ich do drzewa. W tabeli wymieniono metody z opisem, gdzie nowy węzeł pojawia się w Document Object Model XML (DOM).  
  
|Metoda|Położenie węzła|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|Wstawiono przed węzłem referencyjnym. Na przykład, aby wstawić nowy węzeł w pozycji 5:<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> Aby uzyskać więcej informacji, zobacz metodę <xref:System.Xml.XmlNode.InsertBefore%2A>.|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|Wstawiono po węźle odwołania. Na przykład:<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> Aby uzyskać więcej informacji, zobacz metodę <xref:System.Xml.XmlNode.InsertAfter%2A>.|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|Dodaje węzeł na końcu listy węzłów podrzędnych dla danego węzła. Jeśli dodawany węzeł jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragmentu dokumentu zostanie przeniesiona na listę podrzędną tego węzła. Aby uzyskać więcej informacji, zobacz metodę <xref:System.Xml.XmlNode.AppendChild%2A>.|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|Dodaje węzeł na początku listy węzłów podrzędnych danego węzła. Jeśli dodawany węzeł jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragmentu dokumentu zostanie przeniesiona na listę podrzędną tego węzła. Aby uzyskać więcej informacji, zobacz metodę <xref:System.Xml.XmlNode.PrependChild%2A>.|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|Dołącza węzeł <xref:System.Xml.XmlAttribute> do końca kolekcji atrybutów skojarzonej z elementem. Aby uzyskać więcej informacji, zobacz metodę <xref:System.Xml.XmlAttributeCollection.Append%2A>.|  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
