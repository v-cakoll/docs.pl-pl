---
title: LINQ to XML dla użytkowników metody XPath
ms.date: 07/20/2015
ms.assetid: 0e64911c-a7cc-4c20-b927-ca99078b5656
ms.openlocfilehash: 7942d33831644875f390e9128965fe1c36433808
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84368793"
---
# <a name="linq-to-xml-for-xpath-users-visual-basic"></a>LINQ to XML dla użytkowników XPath (Visual Basic)

W tym zestawie tematów przedstawiono liczbę wyrażeń XPath i ich [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] odpowiedników.  
  
 We wszystkich przykładach użyto funkcji XPath w programie [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] , która jest udostępniana przez metody rozszerzające w <xref:System.Xml.XPath.Extensions?displayProperty=nameWithType> . Przykłady wykonują zarówno wyrażenie XPath, jak i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] wyrażenie. Każdy przykład porównuje wyniki obu zapytań, sprawdzając, czy wyrażenie XPath jest funkcjonalnie równoważne z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] kwerendą. Ponieważ oba typy zapytań zwracają węzły z tego samego drzewa XML, porównanie wyników zapytania jest tworzone przy użyciu tożsamości referencyjnej.  
  
## <a name="in-this-section"></a>W tej sekcji  
  
|Temat|Opis|  
|-----------|-----------------|  
|[Porównanie metody XPath i LINQ to XML](../../../../csharp/programming-guide/concepts/linq/comparison-of-xpath-and-linq-to-xml.md)|Zawiera omówienie podobieństw i różnic między XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .|  
|[Instrukcje: Znajdowanie elementu podrzędnego (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-child-element-xpath-linq-to-xml.md)|Porównuje oś elementu podrzędnego XPath z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Element%2A> metodą.<br /><br /> Skojarzone wyrażenie XPath: `"DeliveryNotes"` .|  
|[Instrukcje: Znajdowanie listy elementów podrzędnych (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-list-of-child-elements-xpath-linq-to-xml.md)|Porównuje oś elementów podrzędnych XPath z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XContainer.Elements%2A> osią.<br /><br /> Skojarzone wyrażenie XPath:`"./*"`|  
|[Instrukcje: wyszukiwanie elementu głównego (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-root-element-xpath-linq-to-xml.md)|Porównuje sposób pobierania elementu głównego za pomocą wyrażenia XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"/PurchaseOrders"`|  
|[Instrukcje: Znajdowanie elementów potomnych (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendant-elements-xpath-linq-to-xml.md)|Porównuje sposób pobierania elementów potomnych o określonej nazwie przy użyciu XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"//Name"`|  
|[Instrukcje: filtrowanie atrybutu (XPath-LINQ to XML) (Visual Basic)](how-to-filter-on-an-attribute-xpath-linq-to-xml.md)|Porównuje sposób pobierania elementów potomnych o określonej nazwie i z atrybutem o określonej wartości za pomocą wyrażenia XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"./Address[@Type='Shipping']"`|  
|[Instrukcje: Znajdowanie powiązanych elementów (XPath-LINQ to XML) (Visual Basic)](how-to-find-related-elements-xpath-linq-to-xml.md)|Porównuje, jak uzyskać element, wybierając atrybut, który jest określany przez wartość innego elementu z wyrażeniem XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"./Customer[@CustomerID=/Root/Orders/Order[12]/CustomerID]"`|  
|[Instrukcje: Znajdowanie elementów w przestrzeni nazw (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-in-a-namespace.md)|Porównuje użycie <xref:System.Xml.XmlNamespaceManager> klasy XPath z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] <xref:System.Xml.Linq.XName.Namespace%2A> właściwością <xref:System.Xml.Linq.XName> klasy do pracy z przestrzeniami nazw XML.<br /><br /> Skojarzone wyrażenie XPath:`"./aw:*"`|  
|[Instrukcje: Znajdowanie poprzedzających elementów równorzędnych (XPath-LINQ to XML) (Visual Basic)](how-to-find-preceding-siblings-xpath-linq-to-xml.md)|Porównuje `preceding-sibling` oś XPath z [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] osią podrzędną <xref:System.Xml.Linq.XNode.ElementsBeforeSelf%2A?displayProperty=nameWithType> .<br /><br /> Skojarzone wyrażenie XPath:`"preceding-sibling::*"`|  
|[Instrukcje: Znajdowanie elementów potomnych elementu podrzędnego (XPath-LINQ to XML) (Visual Basic)](how-to-find-descendants-of-a-child-element-xpath-linq-to-xml.md)|Porównuje sposób pobierania elementów potomnych elementu podrzędnego o określonej nazwie z wyrażeniem XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"./Paragraph//Text/text()"`|  
|[Instrukcje: Znajdowanie Unii dwóch ścieżek lokalizacji (XPath-LINQ to XML) (Visual Basic)](how-to-find-a-union-of-two-location-paths-xpath.md)|Porównuje użycie operatora Union, <code>&#124;</code> w języku XPath ze <xref:System.Linq.Enumerable.Concat%2A> standardowym operatorem zapytania w [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:<code>"//Category&#124;//Price"</code>|  
|[Instrukcje: Znajdowanie węzłów elementów równorzędnych (XPath-LINQ to XML) (Visual Basic)](how-to-find-sibling-nodes-xpath-linq-to-xml.md)|Porównuje sposób znajdowania wszystkich elementów równorzędnych węzła, które mają określoną nazwę z wyrażeniami XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"../Book"`|  
|[Instrukcje: Znajdowanie atrybutu elementu nadrzędnego (XPath-LINQ to XML) (Visual Basic)](how-to-find-an-attribute-of-the-parent-xpath-linq-to-xml.md)|Porównuje sposób przejścia do elementu nadrzędnego i znajdowania skojarzonego atrybutu przy użyciu XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"../@id"`|  
|[Instrukcje: Znajdowanie atrybutów elementów równorzędnych o określonej nazwie (XPath-LINQ to XML) (Visual Basic)](how-to-find-attributes-of-siblings-with-a-specific-name.md)|Porównuje sposób znajdowania określonych atrybutów elementów równorzędnych węzła kontekstu z wyrażeniami XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"../Book/@id"`|  
|[Instrukcje: Znajdowanie elementów z określonym atrybutem (XPath-LINQ to XML) (Visual Basic)](how-to-find-elements-with-a-specific-attribute.md)|Porównuje, jak znaleźć elementy Al zawierające określony atrybut przy użyciu XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"./*[@Select]"`|  
|[Instrukcje: Znajdowanie elementów podrzędnych na podstawie pozycji (XPath-LINQ to XML) (Visual Basic)](how-to-find-child-elements-based-on-position.md)|Porównuje sposób znajdowania elementu na podstawie jego położenia względnego przy użyciu XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"Test[position() >= 2 and position() <= 4]"`|  
|[Instrukcje: wyszukiwanie bezpośrednio poprzedzającego elementu równorzędnego (XPath-LINQ to XML) (Visual Basic)](how-to-find-the-immediate-preceding-sibling-xpath-linq-to-xml.md)|Porównuje sposób znajdowania bezpośrednio poprzedzającego elementu równorzędnego węzła przy użyciu XPath i [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] .<br /><br /> Skojarzone wyrażenie XPath:`"preceding-sibling::*[1]"`|  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.XPath?displayProperty=nameWithType>
- [Wykonywanie zapytania dotyczącego drzew XML (Visual Basic)](querying-xml-trees.md)
- [Przetwarzanie danych XML przy użyciu modelu danych XPath](../../../../standard/data/xml/process-xml-data-using-the-xpath-data-model.md)
