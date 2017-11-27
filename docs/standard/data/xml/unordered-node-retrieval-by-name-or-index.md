---
title: "Pobieranie węzła nieuporządkowaną przez nazwę lub indeks"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a8bea8f373dced08fd7a2a828255a593533df9d7
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="ec924-102">Pobieranie węzła nieuporządkowaną przez nazwę lub indeks</span><span class="sxs-lookup"><span data-stu-id="ec924-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="ec924-103">**XmlNamedNodeMap** jest opisany w sieci World Wide Web konsorcjum W3C specyfikacji jako NamedNodeMap i jest wymagany do obsługi nieuporządkowaną zestaw określonych węzłów z możliwością węzłów odwołanie przez ich nazwę lub indeks.</span><span class="sxs-lookup"><span data-stu-id="ec924-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="ec924-104">Jedynym sposobem, musisz mieć dostęp do **XmlNamedNodeMap** jest, gdy **XmlNamedNodeMap** jest zwracany za pomocą metody lub właściwości.</span><span class="sxs-lookup"><span data-stu-id="ec924-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="ec924-105">Istnieją trzy metody lub właściwości, które zwracają **XmlNamedNodeMap**:</span><span class="sxs-lookup"><span data-stu-id="ec924-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
-   <span data-ttu-id="ec924-106">XmlElement.Attributes</span><span class="sxs-lookup"><span data-stu-id="ec924-106">XmlElement.Attributes</span></span>  
  
-   <span data-ttu-id="ec924-107">XmlDocumentType.Entities</span><span class="sxs-lookup"><span data-stu-id="ec924-107">XmlDocumentType.Entities</span></span>  
  
-   <span data-ttu-id="ec924-108">XmlDocumentType.Notations</span><span class="sxs-lookup"><span data-stu-id="ec924-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="ec924-109">Na przykład **XmlDocumentType.Entities** właściwości pobiera kolekcję **XmlEntity** węzłów zadeklarowany w deklaracji typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ec924-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="ec924-110">Ta kolekcja jest zwracana jako **XmlNamedNodeMap**, i można wykonać iterację kolekcji przy użyciu **liczba** właściwości i wyświetlenia informacji jednostki.</span><span class="sxs-lookup"><span data-stu-id="ec924-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="ec924-111">Na przykład iteracji **XmlNamedNodeMap**, zobacz <xref:System.Xml.XmlDocumentType.Entities%2A>.</span><span class="sxs-lookup"><span data-stu-id="ec924-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="ec924-112">**XmlAttributeCollection** jest pochodną **XmlNamedNodeMap** i tylko atrybuty są można modyfikować, gdy notacji i jednostki są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="ec924-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="ec924-113">Przy użyciu **XmlNamedNodeMap** dla atrybutów, można uzyskać węzłów dla tych atrybutów, na podstawie ich nazw XML.</span><span class="sxs-lookup"><span data-stu-id="ec924-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="ec924-114">Zapewnia to łatwa metoda manipulowania kolekcję atrybutów w węźle elementu.</span><span class="sxs-lookup"><span data-stu-id="ec924-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="ec924-115">Może to być contrasted bezpośrednio z **XmlNodeList**, który też implementuje **IEnumerable** interfejsu, ale akcesora indeksu, a nie w ciągu.</span><span class="sxs-lookup"><span data-stu-id="ec924-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="ec924-116">**RemoveNamedItem** i **SetNamedItem** metody są używane tylko przed **XmlAttributeCollection**.</span><span class="sxs-lookup"><span data-stu-id="ec924-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="ec924-117">Dodawanie lub usuwanie z kolekcji atrybutów, czy za pomocą **AttributeCollection** lub **XmlNamedNodeMap** implementacji, modyfikuje kolekcji atrybutów w elemencie.</span><span class="sxs-lookup"><span data-stu-id="ec924-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="ec924-118">Poniższy przykład kodu pokazuje, jak przenieść atrybutu i utworzyć nowy atrybut.</span><span class="sxs-lookup"><span data-stu-id="ec924-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
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
  
 <span data-ttu-id="ec924-119">Aby wyświetlić przykład dodatkowy kod, który zawiera atrybut usuwana z **AttributeCollection**, zobacz [metody XmlNamedNodeMap.RemoveNamedItem](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span><span class="sxs-lookup"><span data-stu-id="ec924-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](Overload:System.Xml.XmlNamedNodeMap.RemoveNamedItem).</span></span> <span data-ttu-id="ec924-120">Aby uzyskać więcej informacji na temat właściwości i metody, zobacz [członków XmlNamedNodeMap](AllMembers.T:System.Xml.XmlNamedNodeMap).</span><span class="sxs-lookup"><span data-stu-id="ec924-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](AllMembers.T:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ec924-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec924-121">See Also</span></span>  
 [<span data-ttu-id="ec924-122">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="ec924-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
