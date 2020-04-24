---
title: Pobieranie nieuporządkowanych węzłów na podstawie nazwy lub indeksu
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: 2038a90b-92af-4a0a-baaa-08e688d95194
ms.openlocfilehash: 55ea0e31bb8a2863dc0e0eb30f6ca5700c3110b8
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/28/2020
ms.locfileid: "78155740"
---
# <a name="unordered-node-retrieval-by-name-or-index"></a><span data-ttu-id="4060b-102">Pobieranie nieuporządkowanych węzłów na podstawie nazwy lub indeksu</span><span class="sxs-lookup"><span data-stu-id="4060b-102">Unordered Node Retrieval by Name or Index</span></span>
<span data-ttu-id="4060b-103">**XmlNamedNodeMap** jest opisany w specyfikacji organizacja World Wide Web Consortium (W3C) jako NamedNodeMap i jest wymagany do obsługi nieuporządkowanego zestawu węzłów z możliwością odwoływania się do węzłów według ich nazwy lub indeksu.</span><span class="sxs-lookup"><span data-stu-id="4060b-103">The **XmlNamedNodeMap** is described in the World Wide Web Consortium (W3C) specification as the NamedNodeMap and is required to handle an unordered set of nodes with the ability to reference nodes by their name or index.</span></span> <span data-ttu-id="4060b-104">Jedynym sposobem, w jaki masz dostęp do elementu **XmlNamedNodeMap** , jest to, że **XmlNamedNodeMap** jest zwracany przez metodę lub właściwość.</span><span class="sxs-lookup"><span data-stu-id="4060b-104">The only way you have access to an **XmlNamedNodeMap** is when an **XmlNamedNodeMap** is returned through a method or property.</span></span> <span data-ttu-id="4060b-105">Istnieją trzy metody lub właściwości, które zwracają **XmlNamedNodeMap**:</span><span class="sxs-lookup"><span data-stu-id="4060b-105">There are three methods or properties that return an **XmlNamedNodeMap**:</span></span>  
  
- <span data-ttu-id="4060b-106">XmlElement. Attributes</span><span class="sxs-lookup"><span data-stu-id="4060b-106">XmlElement.Attributes</span></span>  
  
- <span data-ttu-id="4060b-107">XmlDocumentType. Entities</span><span class="sxs-lookup"><span data-stu-id="4060b-107">XmlDocumentType.Entities</span></span>  
  
- <span data-ttu-id="4060b-108">XmlDocumentType. Notations</span><span class="sxs-lookup"><span data-stu-id="4060b-108">XmlDocumentType.Notations</span></span>  
  
 <span data-ttu-id="4060b-109">Na przykład właściwość **XmlDocumentType. Entities** Pobiera kolekcję węzłów **XmlEntity** zadeklarowanych w deklaracji typu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="4060b-109">For example, the **XmlDocumentType.Entities** property gets the collection of **XmlEntity** nodes declared in the document type declaration.</span></span> <span data-ttu-id="4060b-110">Ta kolekcja jest zwracana jako **XmlNamedNodeMap**i można wykonać iterację kolekcji przy użyciu właściwości **Count** i wyświetlić informacje o jednostce.</span><span class="sxs-lookup"><span data-stu-id="4060b-110">This collection is returned as an **XmlNamedNodeMap**, and you can iterate through the collection with the use of the **Count** property and display entity information.</span></span> <span data-ttu-id="4060b-111">Przykład iteracji przez **XmlNamedNodeMap**można znaleźć w temacie <xref:System.Xml.XmlDocumentType.Entities%2A>.</span><span class="sxs-lookup"><span data-stu-id="4060b-111">For an example of iterating through an **XmlNamedNodeMap**, see <xref:System.Xml.XmlDocumentType.Entities%2A>.</span></span>  
  
 <span data-ttu-id="4060b-112">**Atrybut XmlAttributeCollection** pochodzi od **XmlNamedNodeMap** i tylko atrybuty można modyfikować, a notacje i jednostki są tylko do odczytu.</span><span class="sxs-lookup"><span data-stu-id="4060b-112">The **XmlAttributeCollection** is derived from **XmlNamedNodeMap** and only attributes are modifiable, while notations and entities are read-only.</span></span> <span data-ttu-id="4060b-113">Korzystając z **XmlNamedNodeMap** dla atrybutów, można uzyskać węzły dla tych atrybutów na podstawie ich nazw XML.</span><span class="sxs-lookup"><span data-stu-id="4060b-113">Using the **XmlNamedNodeMap** for the attributes, you can get nodes for those attributes based on their XML names.</span></span> <span data-ttu-id="4060b-114">Zapewnia to łatwą metodę manipulowania kolekcją atrybutów w węźle elementu.</span><span class="sxs-lookup"><span data-stu-id="4060b-114">This provides an easy method for manipulating the collection of attributes on an element node.</span></span> <span data-ttu-id="4060b-115">Może to być możliwe bezpośrednio przy użyciu **XmlNodeList**, który implementuje interfejs **IEnumerable** , ale z metodą dostępu do indeksu, a nie ciągiem.</span><span class="sxs-lookup"><span data-stu-id="4060b-115">This can be contrasted directly with **XmlNodeList**, which also implements the **IEnumerable** interface, but with an index accessor rather than a string.</span></span> <span data-ttu-id="4060b-116">Metody **RemoveNamedItem** i **SetNamedItem** są używane tylko w odniesieniu do elementu **XmlAttributeCollection**.</span><span class="sxs-lookup"><span data-stu-id="4060b-116">The **RemoveNamedItem** and **SetNamedItem** methods are only used against an **XmlAttributeCollection**.</span></span> <span data-ttu-id="4060b-117">Dodanie lub usunięcie z kolekcji atrybutów, niezależnie od tego, czy jest używana implementacja **atrybutu** lub **XmlNamedNodeMap** , modyfikuje kolekcję atrybutów w elemencie.</span><span class="sxs-lookup"><span data-stu-id="4060b-117">Adding or removing from an attribute collection, whether using the **AttributeCollection** or the **XmlNamedNodeMap** implementation, modifies the attribute collection on the element.</span></span> <span data-ttu-id="4060b-118">Poniższy przykład kodu pokazuje, jak przenieść atrybut i utworzyć nowy atrybut.</span><span class="sxs-lookup"><span data-stu-id="4060b-118">The following code example shows how to move an attribute and create a new attribute.</span></span>  
  
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
  
 <span data-ttu-id="4060b-119">Aby wyświetlić dodatkowy przykład kodu, który pokazuje usuwany atrybut z **atrybutucollection**, zobacz [XmlNamedNodeMap. RemoveNamedItem](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span><span class="sxs-lookup"><span data-stu-id="4060b-119">To see an additional code example which shows an attribute being removed from an **AttributeCollection**, see [XmlNamedNodeMap.RemoveNamedItem Method](xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A).</span></span> <span data-ttu-id="4060b-120">Aby uzyskać więcej informacji na temat metod i właściwości, zobacz [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).</span><span class="sxs-lookup"><span data-stu-id="4060b-120">For more information on the methods and properties, see [XmlNamedNodeMap Members](xref:System.Xml.XmlNamedNodeMap).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4060b-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="4060b-121">See also</span></span>

- [<span data-ttu-id="4060b-122">XML Document Object Model (DOM)</span><span class="sxs-lookup"><span data-stu-id="4060b-122">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
