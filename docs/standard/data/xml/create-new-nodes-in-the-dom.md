---
title: Utwórz nowe węzły w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbc8d6c1055afc1a0799522f341551d04bab4ace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33569307"
---
# <a name="create-new-nodes-in-the-dom"></a>Utwórz nowe węzły w modelu DOM
<xref:System.Xml.XmlDocument> Ma metody create dla wszystkich typów węzłów. Podaj metodę o nazwie, gdy jest to wymagane, a zawartości lub inne parametry dla tych węzłów, które ma zawartość (na przykład węzeł tekstowy) i węzłem, jest tworzona. Dostępne są następujące metody: te, które wymagają nazwy i kilka innych parametrów wprowadzić, aby utworzyć odpowiedni węzeł.  
  
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
  
 Inne typy węzłów mają wymagania więcej niż tylko dostarczania danych do parametrów.  
  
 Aby uzyskać informacje o atrybutach, zobacz [tworzenie nowych atrybutów elementów w modelu DOM](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md). Aby uzyskać informacji o weryfikacji nazwy elementów i atrybutów, zobacz [— Element XML i weryfikacja nazwy atrybutu podczas tworzenia nowych węzłów](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md). Do tworzenia odwołań do jednostek, zobacz [odwołania do tworzenia nowych jednostek](../../../../docs/standard/data/xml/creating-new-entity-references.md). Aby uzyskać informacji na temat wpływu rozszerzenie odwołań do jednostek w przestrzeni nazw, zobacz [Namespace ma to wpływu na jednostki odwołanie do rozszerzenia dla nowych węzłów zawierających elementy i atrybuty](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md).  
  
 Po utworzeniu nowych węzłów, dostępnych jest kilka metod wstawić je do drzewa. W tabeli przedstawiono metody opis gdy nowy węzeł jest dostępny w XML modelu DOM (Document Object).  
  
|Metoda|Rozmieszczenie|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|Dodaje przed węzła odniesienia. Na przykład, aby wstawić nowy węzeł w położeniu 5:<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertBefore%2A> metody.|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|Dodaje po węzła odniesienia. Na przykład:<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.InsertAfter%2A> metody.|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|Dodaje węzeł na końcu listy węzłów podrzędnych dla danego węzła. Jeśli węzeł dodawany jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragment dokumentu zostaną przeniesione do listy podrzędny tego węzła. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.AppendChild%2A> metody.|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|Dodaje węzeł na początku listy węzłów podrzędnych danego węzła. Jeśli węzeł dodawany jest <xref:System.Xml.XmlDocumentFragment>, cała zawartość fragment dokumentu zostaną przeniesione do listy podrzędny tego węzła. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlNode.PrependChild%2A> metody.|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|Dołącza <xref:System.Xml.XmlAttribute> węzła do końca kolekcji atrybutów skojarzona z elementem. Aby uzyskać więcej informacji, zobacz <xref:System.Xml.XmlAttributeCollection.Append%2A> metody.|  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
