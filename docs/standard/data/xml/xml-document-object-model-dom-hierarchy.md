---
title: Hierarchia modelu (DOM) obiektu dokumentu XML
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b5b4ca249928200ddfc9dcd133ac673261046fb2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarchia modelu (DOM) obiektu dokumentu XML
Na poniższej ilustracji przedstawiono hierarchii klas dla XML modelu DOM (Document Object), z sieci World Wide Web konsorcjum W3C nazwę w nawiasy okrągłe oraz nazwę klasy, gdzie jest to potrzebne.  
  
 ![Modelu obiektu dokumentu XML &#40;DOM&#41; hierarchii](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hierarchia XML modelu DOM (Document Object)  
  
 Następujące klasy nie dziedziczą **XmlNode**:  
  
-   **XmlImplementation**  
  
-   **XmlNamedNodeMap**  
  
-   **XmlNodeList**  
  
-   **XmlNodeChangedEventArgs**  
  
 **XmlImplementation** klasa jest używana do tworzenia dokumentu XML. Aby uzyskać więcej informacji, zobacz [utworzenie dokumentu XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 **XmlNamedNodeMap** klasa obsługuje nieuporządkowaną zestaw węzłów. Aby uzyskać więcej informacji, zobacz [nieuporządkowaną pobierania węzła przez nazwę lub indeks](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 **XmlNodeList** klasa obsługuje uporządkowaną listę węzłów. Aby uzyskać więcej informacji, zobacz [uporządkowane pobierania węzła przez indeks](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 **XmlNodeChangedEventArgs** klasa obsługuje procedury obsługi zdarzeń zarejestrowane na **XmlDocument**. Aby uzyskać więcej informacji, zobacz [obsługi zdarzeń w dokumencie XML przy użyciu XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 **XmlLinkedNode** klasa dziedziczy **XmlNode**. Jego celem jest zastąpienie dwie metody z **XmlNode**: **parametr PreviousSibling** i **NextSibling** metody. Te przesłoniętej metody są dziedziczone i używane przez **XmlCharacterData**, **XmlDeclaration**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**, i **XmlProcessingInstruction**, które są klasy, które mają poprzedniego i następnego elementów równorzędnych.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
