---
title: Pobieranie nieuporządkowanych węzłów na podstawie nazwy lub indeksu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 577de6b60e579b37eb54ea69de72f3534f1d23ac
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628907"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>Pobieranie nieuporządkowanych węzłów na podstawie nazwy lub indeksu
**XmlNamedNodeMap** jest opisany w specyfikacji organizacja World Wide Web Consortium (W3C) jako NamedNodeMap i jest wymagany do obsługi nieuporządkowanego zestawu węzłów z możliwością odwoływania się do węzłów według ich nazwy lub indeksu. Jedynym sposobem, w jaki masz dostęp do elementu **XmlNamedNodeMap** , jest to, że **XmlNamedNodeMap** jest zwracany przez metodę lub właściwość. Istnieją trzy metody lub właściwości, które zwracają **XmlNamedNodeMap**:  
  
- XmlElement. Attributes  
  
- XmlDocumentType.Entities  
  
- XmlDocumentType.Notations  
  
 Na przykład właściwość **XmlDocumentType. Entities** Pobiera kolekcję węzłów **XmlEntity** zadeklarowanych w deklaracji typu dokumentu. Ta kolekcja jest zwracana jako **XmlNamedNodeMap**i można wykonać iterację kolekcji przy użyciu właściwości **Count** i wyświetlić informacje o jednostce. Aby zapoznać się z przykładem iteracji przez **XmlNamedNodeMap**, zobacz <xref:System.Xml.XmlDocumentType.Entities%2A>.  
  
 **Atrybut XmlAttributeCollection** pochodzi od **XmlNamedNodeMap** i tylko atrybuty można modyfikować, a notacje i jednostki są tylko do odczytu. Korzystając z **XmlNamedNodeMap** dla atrybutów, można uzyskać węzły dla tych atrybutów na podstawie ich nazw XML. Zapewnia to łatwą metodę manipulowania kolekcją atrybutów w węźle elementu. Może to być możliwe bezpośrednio przy użyciu **XmlNodeList**, który implementuje interfejs **IEnumerable** , ale z metodą dostępu do indeksu, a nie ciągiem. Metody **RemoveNamedItem** i **SetNamedItem** są używane tylko w odniesieniu do elementu **XmlAttributeCollection**. Dodanie lub usunięcie z kolekcji atrybutów, niezależnie od tego, czy jest używana implementacja **atrybutu** lub **XmlNamedNodeMap** , modyfikuje kolekcję atrybutów w elemencie. Poniższy przykład kodu pokazuje, jak przenieść atrybut i utworzyć nowy atrybut.  
  
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
  
 Aby wyświetlić dodatkowy przykład kodu, który pokazuje usuwany atrybut z **atrybutucollection**, zobacz [XmlNamedNodeMap. RemoveNamedItem](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A). Aby uzyskać więcej informacji na temat metod i właściwości, zobacz [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).  
  
## <a name="see-also"></a>Zobacz też

- [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
