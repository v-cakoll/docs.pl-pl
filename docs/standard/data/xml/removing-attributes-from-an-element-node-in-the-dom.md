---
title: Usuwanie atrybutów z węzła elementu w ramach modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 7ede6f9e-a3ac-49a4-8488-ab8360a44aa4
ms.openlocfilehash: 0ac8528d52ef09aab99c76aea9378c0188fa66d4
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84292023"
---
# <a name="removing-attributes-from-an-element-node-in-the-dom"></a>Usuwanie atrybutów z węzła elementu w ramach modelu DOM
Istnieje wiele sposobów usuwania atrybutów. Jedną z technik jest usunięcie ich z kolekcji atrybutów. W tym celu należy wykonać następujące czynności:  
  
1. Pobierz kolekcję atrybutów z elementu przy użyciu `XmlAttributeCollection attrs = elem.Attributes;` .  
  
2. Usuń atrybut z kolekcji atrybutów przy użyciu jednej z trzech metod:  
  
    - Służy <xref:System.Xml.XmlAttributeCollection.Remove%2A> do usuwania określonego atrybutu.  
  
    - Użyj, <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> Aby usunąć wszystkie atrybuty z kolekcji i pozostawić element bez atrybutów.  
  
    - Użyj <xref:System.Xml.XmlAttributeCollection.RemoveAt%2A> , aby usunąć atrybut z kolekcji atrybutów przy użyciu jego numeru indeksu.  
  
 Poniższe metody usuwają atrybuty z węzła elementu.  
  
- Służy <xref:System.Xml.XmlElement.RemoveAllAttributes%2A> do usuwania kolekcji atrybutów.  
  
- Użyj, <xref:System.Xml.XmlElement.RemoveAttribute%2A> Aby usunąć pojedynczy atrybut według nazwy z kolekcji.  
  
- Służy <xref:System.Xml.XmlElement.RemoveAttributeAt%2A> do usuwania pojedynczego atrybutu według numeru indeksu z kolekcji.  
  
 Jedną z alternatywnych metod jest pobranie elementu, pobranie atrybutu z kolekcji atrybutów i bezpośrednie usunięcie węzła atrybutu. Aby uzyskać atrybut z kolekcji atrybutów, można użyć nazwy, `XmlAttribute attr = attrs["attr_name"];` indeksu `XmlAttribute attr = attrs[0];` lub przez pełną kwalifikację nazwy z przestrzenią nazw `XmlAttribute attr = attrs["attr_localName", "attr_namespace"]` .  
  
 Niezależnie od metody używanej do usuwania atrybutów istnieją specjalne ograniczenia dotyczące usuwania atrybutów, które są zdefiniowane jako atrybuty domyślne w definicji typu dokumentu (DTD). Atrybutów domyślnych nie można usunąć, chyba że element, do którego należą, jest usuwany. Atrybuty domyślne są zawsze obecne dla elementów, które mają zadeklarowane atrybuty domyślne. Usunięcie atrybutu domyślnego z <xref:System.Xml.XmlAttributeCollection> lub z <xref:System.Xml.XmlElement> wyników w atrybucie zastępczym wstawionym do <xref:System.Xml.XmlAttributeCollection> elementu, który został zainicjowany do wartości domyślnej, która została zadeklarowana. Jeśli masz element zdefiniowany jako, masz `<book att1="1" att2="2" att3="3"></book>` `book` element z trzema zadeklarowanymi atrybutami domyślnymi. Implementacja XML Document Object Model (DOM) gwarantuje, że tak długo, jak ten `book` element istnieje, ma trzy atrybuty domyślne `att1` , `att2` , i `att3` .  
  
 Gdy wywoływana z <xref:System.Xml.XmlAttribute> , <xref:System.Xml.XmlAttributeCollection.RemoveAll%2A> Metoda ustawia wartość atrybutu na String. Empty, ponieważ atrybut nie może istnieć bez wartości.  
  
## <a name="see-also"></a>Zobacz także

- [XML Document Object Model (DOM)](xml-document-object-model-dom.md)
