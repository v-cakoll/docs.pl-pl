---
title: Hierarchia modelu (DOM) obiektu dokumentu XML
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
caps.latest.revision: "3"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 4d2ffaa994ce3c9b02ed0937967845be1b803f6d
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarchia modelu (DOM) obiektu dokumentu XML
Na poniższej ilustracji przedstawiono hierarchii klas dla XML modelu DOM (Document Object), z sieci World Wide Web konsorcjum W3C nazwę w nawiasy okrągłe oraz nazwę klasy, gdzie jest to potrzebne.  
  
 ![Modelu obiektu dokumentu XML &#40; DOM &#41; Hierarchia](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
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
