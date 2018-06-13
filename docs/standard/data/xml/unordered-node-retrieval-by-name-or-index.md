---
title: Pobieranie węzła nieuporządkowaną przez nazwę lub indeks
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 785a609455a35dd87a9593f00b58fd160ac708e9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572944"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a>Pobieranie węzła nieuporządkowaną przez nazwę lub indeks
**XmlNamedNodeMap** jest opisany w sieci World Wide Web konsorcjum W3C specyfikacji jako NamedNodeMap i jest wymagany do obsługi nieuporządkowaną zestaw określonych węzłów z możliwością węzłów odwołanie przez ich nazwę lub indeks. Jedynym sposobem, musisz mieć dostęp do **XmlNamedNodeMap** jest, gdy **XmlNamedNodeMap** jest zwracany za pomocą metody lub właściwości. Istnieją trzy metody lub właściwości, które zwracają **XmlNamedNodeMap**:  
  
-   XmlElement.Attributes  
  
-   XmlDocumentType.Entities  
  
-   XmlDocumentType.Notations  
  
 Na przykład **XmlDocumentType.Entities** właściwości pobiera kolekcję **XmlEntity** węzłów zadeklarowany w deklaracji typu dokumentu. Ta kolekcja jest zwracana jako **XmlNamedNodeMap**, i można wykonać iterację kolekcji przy użyciu **liczba** właściwości i wyświetlenia informacji jednostki. Na przykład iteracji **XmlNamedNodeMap**, zobacz <xref:System.Xml.XmlDocumentType.Entities%2A>.  
  
 **XmlAttributeCollection** jest pochodną **XmlNamedNodeMap** i tylko atrybuty są można modyfikować, gdy notacji i jednostki są tylko do odczytu. Przy użyciu **XmlNamedNodeMap** dla atrybutów, można uzyskać węzłów dla tych atrybutów, na podstawie ich nazw XML. Zapewnia to łatwa metoda manipulowania kolekcję atrybutów w węźle elementu. Może to być contrasted bezpośrednio z **XmlNodeList**, który też implementuje **IEnumerable** interfejsu, ale akcesora indeksu, a nie w ciągu. **RemoveNamedItem** i **SetNamedItem** metody są używane tylko przed **XmlAttributeCollection**. Dodawanie lub usuwanie z kolekcji atrybutów, czy za pomocą **AttributeCollection** lub **XmlNamedNodeMap** implementacji, modyfikuje kolekcji atrybutów w elemencie. Poniższy przykład kodu pokazuje, jak przenieść atrybutu i utworzyć nowy atrybut.  
  
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
  
 Aby wyświetlić przykład dodatkowy kod, który zawiera atrybut usuwana z **AttributeCollection**, zobacz [metody XmlNamedNodeMap.RemoveNamedItem](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem). Aby uzyskać więcej informacji na temat właściwości i metody, zobacz [członków XmlNamedNodeMap](AllMembers.T:System.Xml.XmlNamedNodeMap).  
  
## <a name="see-also"></a>Zobacz też  
 [Model DOM (XML Document Object Model)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
