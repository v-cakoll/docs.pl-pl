---
title: Hierarchia Model (DOM) obiektu dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: ef2b5b200f95cdfac9b08a33c328c1dfb797e59e
ms.sourcegitcommit: f513a91160b3fec289dd06646d0d6f81f8fcf910
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/18/2018
ms.locfileid: "46008960"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarchia Model (DOM) obiektu dokumentu XML
Na poniższej ilustracji przedstawiono hierarchii klas dla XML Document Object Model (DOM), za pomocą sieci World Wide Web Consortium (W3C) nadaj nazwę w nawiasach wraz z nazwą klasy, gdzie jest to stosowne.  
  
 ![Model obiektu dokumentu XML &#40;DOM&#41; hierarchii](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hierarchia XML modelu DOM (Document Object)  
  
 Następujące klasy nie dziedziczą **XmlNode**:  
  
-   **XmlImplementation**  
  
-   **XmlNamedNodeMap**  
  
-   **XmlNodeList**  
  
-   **Klasy XmlNodeChangedEventArgs**  
  
 **XmlImplementation** klasa jest używana w celu utworzenia dokumentu XML. Aby uzyskać więcej informacji, zobacz [Tworzenie dokumentu XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 **XmlNamedNodeMap** klasa obsługuje nieuporządkowaną zestaw węzłów. Aby uzyskać więcej informacji, zobacz [nieuporządkowaną pobierania węzła przez nazwę lub indeks](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 **XmlNodeList** klasa obsługuje uporządkowane listy węzłów. Aby uzyskać więcej informacji, zobacz [uporządkowane pobierania węzła za pomocą indeksu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 **Klasy XmlNodeChangedEventArgs** klasa obsługuje programy obsługi zdarzeń zarejestrowane na **XmlDocument**. Aby uzyskać więcej informacji, zobacz [zdarzenie obsługi w dokumencie XML przy użyciu klasy XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 **XmlLinkedNode** klasa dziedziczy **XmlNode**. Jego celem jest zastąpienie dwie metody z **XmlNode**: **PreviousSibling** i **NextSibling** metody. Te przesłonięte metody są dziedziczone i używane przez **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, i **XmlProcessingInstruction**, służą do klas, które mają elementy równorzędne poprzedni i dalej.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
