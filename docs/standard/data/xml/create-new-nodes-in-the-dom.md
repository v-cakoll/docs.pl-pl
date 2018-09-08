---
title: Tworzenie nowych węzłów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 390ffa1dd9f2e76372b0e4fcbf2916918b64d748
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44134729"
---
# <a name="create-new-nodes-in-the-dom"></a>Tworzenie nowych węzłów w modelu DOM
<xref:System.Xml.XmlDocument> Ma metody create, dla wszystkich typów węzłów. Podaj metody o nazwie, gdy jest to wymagane, a zawartość lub inne parametry te węzły, które mają zawartość (na przykład węzeł tekstowy) i węzeł jest tworzony. Dostępne są następujące metody: te, które wymagają nazwy i kilka innych parametrów, wprowadzić, aby utworzyć odpowiedni węzeł.  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 Inne typy węzłów mają wymagania więcej niż tylko dostarczanie danych do parametrów.  
  
 Aby uzyskać informacji na temat atrybutów, zobacz [tworzenie nowych atrybutów dla elementów w modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md). Aby uzyskać informacji na temat sprawdzania poprawności nazwy elementów i atrybutów, zobacz [— Element XML i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md). W celu tworzenia odwołań do jednostek, zobacz [odwołania do tworzenia nowych jednostek](../../../../docs/standard/data/xml/creating-new-entity-references.md). Aby uzyskać informacji na temat skutków rozszerzenie odwołań do jednostek w przestrzeni nazw, zobacz [Namespace wpływ na rozwijanie odwołań do jednostek dla nowych węzłów zawierających elementy i atrybuty](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).  
  
 Po utworzeniu nowych węzłów, istnieje kilka różnych metod wstawić je do drzewa. W tabeli wymieniono metody, gdzie nowy węzeł jest widoczny w XML Document Object Model (DOM) opis.  
  
|Metoda|Położenie węzłów|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|Wstawione przed węzłem odniesienia. Na przykład, aby wstawić nowy węzeł w pozycji 5:<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertBefore%2A> metody.|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|Wstawiona po węzła odniesienia. Na przykład:<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertAfter%2A> metody.|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|Dodaje węzeł do końca listy węzłów podrzędnych dla danego węzła. Jeśli węzeł dodawany jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragment dokumentu zostaną przeniesione do listy podrzędny tego węzła. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.AppendChild%2A> metody.|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|Dodaje węzeł na początku listy węzłów podrzędnych danego węzła. Jeśli węzeł dodawany jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragment dokumentu zostaną przeniesione do listy podrzędny tego węzła. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.PrependChild%2A> metody.|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|Dołącza <xref:System.Xml.XmlAttribute> węzła w końcu Kolekcja atrybutów skojarzona z elementem. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlAttributeCollection.Append%2A> metody.|  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
