---
title: Usuwanie atrybutów z węzła elementu w ramach modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7031d34916c520f52550d215a1a8e62880209c87
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64590035"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Usuwanie atrybutów z węzła elementu w ramach modelu DOM
Istnieje wiele sposobów, aby usunąć atrybuty. Jedna z technik jest je usunąć z kolekcji atrybutów. Aby to zrobić, wykonywane są następujące czynności:  
  
1. Pobierz kolekcję atrybutów z elementu za pomocą `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2. Usuń atrybut z kolekcji atrybutów przy użyciu jednej z trzech metod:  
  
    - Użyj <xref:System.Xml.XmlAttributeCollection.Remove%2A> Aby usunąć określony atrybut.  
  
    - Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> usunąć wszystkie atrybuty z kolekcji i pozostaw elementu żadnych atrybutów.  
  
    - Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> Aby usunąć atrybut z kolekcji atrybutów przy użyciu jego numer indeksu.  
  
 Następujące metody usuwanie atrybutów z węzła elementu.  
  
- Użyj <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> do usunięcia z kolekcji atrybutów.  
  
- Użyj <xref:System.Xml.XmlElement.RemoveAttribute%2A> usunąć jeden atrybut według nazwy z kolekcji.  
  
- Użyj <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> usunąć jeden atrybut przez numer indeksu z kolekcji.  
  
 Co więcej alternatywą jest pobieranie elementu, Pobierz atrybut z kolekcji atrybutów i Usuń węzeł atrybutu bezpośrednio. Aby uzyskać ten atrybut z kolekcji atrybutów, można użyć nazwy `XmlAttribute attr = attrs["attr_name"];`, indeks `XmlAttribute attr = attrs[0];`, lub w pełni kwalifikując nazwę z przestrzenią nazw `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Niezależnie od metody, aby usunąć atrybuty istnieją specjalne ograniczenia na temat usuwania atrybutów, które są zdefiniowane jako domyślne atrybuty w definicji typu dokumentu (DTD). Nie można usunąć domyślnych atrybutów, chyba że zostanie usunięty element, do którego należą. Atrybuty domyślne są zawsze obecne elementy, które mają domyślne atrybutów zadeklarowany. Usunięcie domyślnego atrybutu z <xref:System.Xml.XmlAttributeCollection> lub <xref:System.Xml.XmlElement> wyniki w atrybucie zastąpienie wstawiony <xref:System.Xml.XmlAttributeCollection> elementu zainicjowany do wartości domyślnej, który został zadeklarowany. Jeśli masz element, który został zdefiniowany jako `<book att1="1" att2="2" att3="3"></book>`, można skorzystać z `book` zadeklarowany element z trzech atrybutów domyślnych. Implementacja XML Document Object Model (DOM) gwarantuje, że tak długo, jak to `book` element istnieje, jego atrybuty te trzy domyślne `att1`, `att2`, i `att3`.  
  
 Gdy zostanie wywołana z <xref:System.Xml.XmlAttribute>, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> metody ustawia wartość atrybutu String.Empty, ponieważ atrybut nie może istnieć bez wartości.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
