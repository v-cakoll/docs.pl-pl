---
title: Pobieranie nieuporządkowanych węzłów według nazwy lub indeksu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
author: mairaw
ms.author: mairaw
ms.openlocfilehash: da1c9f25052bb2354b435cd28b7ff55d4a754ed1
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/21/2018
ms.locfileid: "46539203"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>Pobieranie nieuporządkowanych węzłów według nazwy lub indeksu
**XmlNamedNodeMap** opisano w specyfikacji World Wide Web Consortium (W3C) jako NamedNodeMap i jest wymagany do obsługi nieuporządkowaną zestaw węzłów z możliwością odwołanie węzły według ich nazwy lub indeksu. Jedynym sposobem, że masz dostęp do **XmlNamedNodeMap** jest, gdy **XmlNamedNodeMap** jest zwracany przez metodę lub właściwość. Istnieją trzy metody lub właściwości, które zwracają **XmlNamedNodeMap**:  
  
-   XmlElement.Attributes  
  
-   XmlDocumentType.Entities  
  
-   XmlDocumentType.Notations  
  
 Na przykład **XmlDocumentType.Entities** właściwości pobiera kolekcję **XmlEntity** węzłów zadeklarowane w deklaracji typu dokumentu. Ta kolekcja jest zwracana jako **XmlNamedNodeMap**, i można wykonać iterację kolekcji przy użyciu **liczba** właściwości i wyświetlanie informacji o jednostkach. Na przykład iteracja **XmlNamedNodeMap**, zobacz <xref:System.Xml.XmlDocumentType.Entities%2A>.  
  
 **XmlAttributeCollection** jest tworzony na podstawie **XmlNamedNodeMap** i można modyfikować, są tylko atrybuty, a jednostki i notacji tylko do odczytu. Za pomocą **XmlNamedNodeMap** dla atrybutów, możesz uzyskać dostęp do węzłów dla tych atrybutów, na podstawie ich nazw XML. Zapewnia to prostą metodę do manipulowania kolekcję atrybutów węzeł elementu. To może być przedstawiane jako przeciwieństwo bezpośrednio **XmlNodeList**, który implementuje również **IEnumerable** interfejsu, ale za pomocą metody dostępu indeksu, a nie w ciągu. **RemoveNamedItem** i **SetNamedItem** metody są używane tylko względem **XmlAttributeCollection**. Dodawanie lub usuwanie z kolekcji atrybutów przeprowadzanych przy użyciu **AttributeCollection** lub **XmlNamedNodeMap** implementacji modyfikuje kolekcji atrybutów w elemencie. Poniższy przykład kodu pokazuje, jak przenieść atrybut i utworzyć nowy atrybut.  
  
```vb  
Imports System  
Imports System.Xml  
  
Class test  
  
    Public Shared Sub Main()  
        Dim doc As New XmlDocument()  
        doc.LoadXml("<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> ")  
  
        ' Get the attributes of node "child2 "  
        Dim ac As XmlAttributeCollection = doc.DocumentElement.ChildNodes(1).Attributes  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
        Dim i As Integer  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Get the 'attr1' from child1.  
        Dim attr As XmlAttribute = doc.DocumentElement.ChildNodes(0).Attributes(0)  
  
        ' Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem(attr)  
  
        ''attr1' will be removed from 'child1' and added to 'child2'.  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
        ' Create a new attribute and add to the collection.  
        Dim attr2 As XmlAttribute = doc.CreateAttribute("attr4")  
        attr2.Value = "val4"  
        ac.SetNamedItem(attr2)  
  
        ' Print out the number of attributes and their names.  
        Console.WriteLine(("Number of Attributes: " + ac.Count))  
  
        For i = 0 To ac.Count - 1  
            Console.WriteLine((i + 1 + ".  Attribute Name: '" + ac(i).Name + "'  Attribute Value:  '" + ac(i).Value + "'"))  
        Next i  
    End Sub 'Main  
End Class 'test  
```  
  
```csharp  
using System;  
using System.Xml;  
class test {  
    public static void Main() {  
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml( "<root> <child1 attr1='val1' attr2='val2'> text1 </child1> <child2 attr3='val3'> text2 </child2> </root> " );  
  
        // Get the attributes of node "child2"  
        XmlAttributeCollection ac = doc.DocumentElement.ChildNodes[1].Attributes;  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );  
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Get the 'attr1' from child1.  
        XmlAttribute attr = doc.DocumentElement.ChildNodes[0].Attributes[0];  
  
        // Add this attribute to the attributecollection "ac".  
        ac.SetNamedItem( attr );  
  
        // 'attr1' will be removed from 'child1' and added to 'child2'.  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );   
  
        // Create a new attribute and add to the collection.  
        XmlAttribute attr2 = doc.CreateAttribute( "attr4" );  
        attr2.Value = "val4";  
        ac.SetNamedItem( attr2 );  
  
        // Print out the number of attributes and their names.  
        Console.WriteLine( "Number of Attributes: "+ac.Count );          
        for( int i = 0; i < ac.Count; i++ )  
            Console.WriteLine( (i+1) + ".  Attribute Name: '" +ac[i].Name+ "'  Attribute Value:  '"+ ac[i].Value +"'" );           
  
    }  
}  
```  
  
 Aby zobaczyć przykład dodatkowy kod zawierającym atrybut usuwany z **AttributeCollection**, zobacz [metoda XmlNamedNodeMap.RemoveNamedItem](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem). Aby uzyskać więcej informacji na temat metody i właściwości, zobacz [członków XmlNamedNodeMap](AllMembers.T:System.Xml.XmlNamedNodeMap).  
  
## <a name="see-also"></a>Zobacz także

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
