---
title: Usuwanie atrybutów z węzłem elementu w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 758ce84390c9ba47e3eb56e1feb293a4cf0408a1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33570571"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Usuwanie atrybutów z węzłem elementu w modelu DOM
Istnieje wiele sposobów, aby usunąć atrybuty. Jeden technika jest je usunąć z kolekcji atrybutów. Aby to zrobić, są wykonywane następujące czynności:  
  
1.  Pobierz kolekcję atrybutów z przy użyciu elementu `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2.  Usuń atrybut z kolekcji atrybutów przy użyciu jednej z trzech metod:  
  
    -   Użyj <xref:System.Xml.XmlAttributeCollection.Remove%2A> Aby usunąć określony atrybut.  
  
    -   Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> Aby usunąć wszystkie atrybuty z kolekcji i pozostawić element bez atrybutów.  
  
    -   Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> można usunąć atrybutu z kolekcji atrybutów przy użyciu numeru indeksu.  
  
 Następujące metody usuwanie atrybutów z węzeł elementu.  
  
-   Użyj <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> można usunąć kolekcji atrybutów.  
  
-   Użyj <xref:System.Xml.XmlElement.RemoveAttribute%2A> usunąć jeden atrybut o nazwie z kolekcji.  
  
-   Użyj <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> usunięcie jeden atrybut, a numer indeksu z kolekcji.  
  
 Co więcej alternatywą jest uzyskać elementu, pobrać atrybutu z kolekcji atrybutów i usunąć węzła atrybutu bezpośrednio. Aby uzyskać ten atrybut z kolekcji atrybutów, można użyć nazwy, `XmlAttribute attr = attrs["attr_name"];`, indeks `XmlAttribute attr = attrs[0];`, lub w pełni kwalifikowanie nazw z przestrzeni nazw `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Niezależnie od metody umożliwia usuwanie atrybutów ma ograniczeń specjalnych na usuwanie atrybutów, które są zdefiniowane jako domyślne atrybuty w definicji typu dokumentu (DTD). Nie można usunąć atrybutów domyślnych, chyba że zostanie usunięty element, do którego należą. Domyślne atrybuty zawsze znajdują się dla elementów, które mają atrybuty domyślne zadeklarowany. Usuwanie domyślnego atrybutu z <xref:System.Xml.XmlAttributeCollection> lub <xref:System.Xml.XmlElement> wyniki w atrybucie zastępczy wstawione do <xref:System.Xml.XmlAttributeCollection> elementu zainicjowany do wartości domyślnej, który został zadeklarowany. Jeśli masz zdefiniowany jako element `<book att1="1" att2="2" att3="3"></book>`, a następnie masz `book` zadeklarowany element z trzech atrybutów domyślnych. Implementacja XML modelu DOM (Document Object) gwarantuje, że tak długo, jak to `book` element istnieje, ma następujące trzy domyślne atrybuty `att1`, `att2`, i `att3`.  
  
 Po wywołaniu z <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> metody ustawia wartość atrybutu String.Empty, ponieważ atrybut nie może istnieć bez wartości.  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
