---
title: Usuwanie atrybutów z węzła elementu w ramach modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: bb18e712d5ed2cd06c7ae0e867b19ca8a9ad2513
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75710352"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Usuwanie atrybutów z węzła elementu w ramach modelu DOM
Istnieje wiele sposobów usuwania atrybutów. Jedną z technik jest usunięcie ich z kolekcji atrybutów. W tym celu należy wykonać następujące czynności:  
  
1. Pobierz kolekcję atrybutów z elementu przy użyciu `XmlAttributeCollection attrs = elem.Attributes;`.  
  
2. Usuń atrybut z kolekcji atrybutów przy użyciu jednej z trzech metod:  
  
    - Użyj <xref:System.Xml.XmlAttributeCollection.Remove%2A>, aby usunąć określony atrybut.  
  
    - Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A>, aby usunąć wszystkie atrybuty z kolekcji i pozostawić element bez atrybutów.  
  
    - Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A>, aby usunąć atrybut z kolekcji atrybutów przy użyciu numeru indeksu.  
  
 Poniższe metody usuwają atrybuty z węzła elementu.  
  
- Użyj <xref:System.Xml.XmlElement.RemoveAllAttributes%2A>, aby usunąć kolekcję atrybutów.  
  
- Użyj <xref:System.Xml.XmlElement.RemoveAttribute%2A>, aby usunąć pojedynczy atrybut według nazwy z kolekcji.  
  
- Użyj <xref:System.Xml.XmlElement.RemoveAttributeAt%2A>, aby usunąć pojedynczy atrybut według numeru indeksu z kolekcji.  
  
 Jedną z alternatywnych metod jest pobranie elementu, pobranie atrybutu z kolekcji atrybutów i bezpośrednie usunięcie węzła atrybutu. Aby uzyskać atrybut z kolekcji atrybutów, można użyć nazwy, `XmlAttribute attr = attrs["attr_name"];`, `XmlAttribute attr = attrs[0];`indeksu lub w pełni kwalifikującej się nazwy z przestrzenią nazw `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]`.  
  
 Niezależnie od metody używanej do usuwania atrybutów istnieją specjalne ograniczenia dotyczące usuwania atrybutów, które są zdefiniowane jako atrybuty domyślne w definicji typu dokumentu (DTD). Atrybutów domyślnych nie można usunąć, chyba że element, do którego należą, jest usuwany. Atrybuty domyślne są zawsze obecne dla elementów, które mają zadeklarowane atrybuty domyślne. Usunięcie atrybutu domyślnego z <xref:System.Xml.XmlAttributeCollection> lub z <xref:System.Xml.XmlElement> powoduje, że atrybut zastępczy został wstawiony do <xref:System.Xml.XmlAttributeCollection> elementu, został zainicjowany do wartości domyślnej, która została zadeklarowana. Jeśli masz element zdefiniowany jako `<book att1="1" att2="2" att3="3"></book>`, wówczas masz element `book` z trzema zadeklarowanymi atrybutami domyślnymi. Implementacja XML Document Object Model (DOM) gwarantuje, że o ile ten element `book` istnieje, ma te trzy atrybuty domyślne `att1`, `att2`i `att3`.  
  
 Gdy wywoływana przy użyciu <xref:System.Xml.XmlAttribute>, Metoda <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> ustawia wartość atrybutu na String. Empty, ponieważ atrybut nie może istnieć bez wartości.  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
