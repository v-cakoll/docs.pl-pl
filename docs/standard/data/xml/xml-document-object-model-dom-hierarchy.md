---
title: Hierarchia modelu DOM (XML Document Object Model)
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 9d187d4f-c76e-4223-a670-cc290783ce47
ms.openlocfilehash: 1193d7631816fe9fbf7aa1984d79ef8e61d5da80
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709975"
---
# <a name="xml-document-object-model-dom-hierarchy"></a>Hierarchia modelu DOM (XML Document Object Model)
Na poniższej ilustracji przedstawiono hierarchię klas dla Document Object Model XML (DOM), z nazwą organizacja World Wide Web Consortium (W3C) w nawiasie wraz z nazwą klasy, w której ma zastosowanie.  
  
 ![Hierarchia &#40;dom&#41; Document Object Model XML](../../../../docs/standard/data/xml/media/dom-class-hierarchy.gif "Dom_class_hierarchy")  
Hierarchia XML Document Object Model (DOM)  
  
 Następujące klasy nie dziedziczą z **XmlNode**:  
  
- **XmlImplementation**  
  
- **XmlNamedNodeMap**  
  
- **XmlNodeList**  
  
- **XmlNodeChangedEventArgs**  
  
 Klasa **XmlImplementation** służy do tworzenia dokumentu XML. Aby uzyskać więcej informacji, zobacz [Tworzenie dokumentów XML](../../../../docs/standard/data/xml/xml-document-creation.md).  
  
 Klasa **XmlNamedNodeMap** obsługuje nieuporządkowany zestaw węzłów. Aby uzyskać więcej informacji, zobacz [nieuporządkowane pobieranie węzłów według nazwy lub indeksu](../../../../docs/standard/data/xml/unordered-node-retrieval-by-name-or-index.md).  
  
 Klasa **XmlNodeList** obsługuje uporządkowaną listę węzłów. Aby uzyskać więcej informacji, zobacz [uporządkowane pobieranie węzłów według indeksu](../../../../docs/standard/data/xml/ordered-node-retrieval-by-index.md).  
  
 Klasa **XmlNodeChangedEventArgs** obsługuje programy obsługi zdarzeń zarejestrowane w **dokumencie XmlDocument**. Aby uzyskać więcej informacji, zobacz [Obsługa zdarzeń w dokumencie XML przy użyciu XmlNodeChangedEventArgs](../../../../docs/standard/data/xml/event-handling-in-an-xml-document-using-the-xmlnodechangedeventargs.md).  
  
 Klasa **XmlLinkedNode** dziedziczy z klasy **XmlNode**. Celem jest przesłonięcie dwóch metod z klasy **XmlNode**: metod **PreviousSibling** i **NextSibling** . Te zastąpione metody są następnie dziedziczone i używane przez **XmlCharacterData**, **xmldeklaracji**, **XmlDocumentType**, **XmlElement**, **XmlEntityReference**i **XmlProcessingInstruction**, które są klasami, które mają poprzednie i następne elementy równorzędne.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
