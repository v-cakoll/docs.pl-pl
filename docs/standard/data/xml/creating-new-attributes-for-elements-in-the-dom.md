---
title: "Tworzenie nowych atrybutów dla elementów w modelu DOM"
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
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
caps.latest.revision: "4"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 6970ffc38e900c9b47c58c8ae4b81b9551f5589b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="a33d4-102">Tworzenie nowych atrybutów dla elementów w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="a33d4-102">Creating New Attributes for Elements in the DOM</span></span>
<span data-ttu-id="a33d4-103">Tworzenie nowych atrybutów różni się od tworzenia innych typów węzła, ponieważ atrybuty nie są węzłami, ale są właściwości węzeł elementu i są zawarte w **XmlAttributeCollection** skojarzone z elementem.</span><span class="sxs-lookup"><span data-stu-id="a33d4-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="a33d4-104">Istnieje wiele sposobów tworzenia atrybutu i dołączenie go do elementu:</span><span class="sxs-lookup"><span data-stu-id="a33d4-104">There are multiple ways to create an attribute and attach it to an element:</span></span>  
  
-   <span data-ttu-id="a33d4-105">Pobierz węzeł elementu i użyj **SetAttribute** można dodać atrybutu do kolekcji atrybutów tego elementu.</span><span class="sxs-lookup"><span data-stu-id="a33d4-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>  
  
-   <span data-ttu-id="a33d4-106">Utwórz **XmlAttribute** za pomocą węzła **CreateAttribute** metody, Pobierz węzeł elementu, a następnie użyj **SetAttributeNode** można dodać węzła do tej kolekcji atrybutów element.</span><span class="sxs-lookup"><span data-stu-id="a33d4-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>  
  
 <span data-ttu-id="a33d4-107">Poniższy przykład pokazuje, jak dodać atrybutu do elementu przy użyciu **SetAttribute** metody.</span><span class="sxs-lookup"><span data-stu-id="a33d4-107">The following example shows how to add an attribute to an element using the **SetAttribute** method.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
public class Sample  
  
  public shared sub Main()  
  
  Dim doc as XmlDocument = new XmlDocument()  
  doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _  
              "<title>Pride And Prejudice</title>" & _  
              "</book>")  
  Dim root as XmlElement = doc.DocumentElement  
  
  'Add a new attribute.  
  root.SetAttribute("genre", "urn:samples", "novel")  
  
  Console.WriteLine("Display the modified XML...")  
  Console.WriteLine(doc.InnerXml)  
  
  end sub  
end class  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    XmlDocument doc = new XmlDocument();  
    doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +  
                "<title>Pride And Prejudice</title>" +  
                "</book>");  
    XmlElement root = doc.DocumentElement;  
  
    // Add a new attribute.  
    root.SetAttribute("genre", "urn:samples", "novel");  
  
    Console.WriteLine("Display the modified XML...");  
    Console.WriteLine(doc.InnerXml);  
  }  
```  
  
 <span data-ttu-id="a33d4-108">W poniższym przykładzie przedstawiono nowy atrybut tworzone przy użyciu **CreateAttribute** metody.</span><span class="sxs-lookup"><span data-stu-id="a33d4-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="a33d4-109">Następnie pokaże atrybut, który został dodany do kolekcji atrybut **książki** przy użyciu elementu **SetAttributeNode** metody.</span><span class="sxs-lookup"><span data-stu-id="a33d4-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>  
  
 <span data-ttu-id="a33d4-110">Podane następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="a33d4-110">Given the following XML:</span></span>  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="a33d4-111">Utwórz nowy atrybut i nadaj mu wartość:</span><span class="sxs-lookup"><span data-stu-id="a33d4-111">create a new attribute and give it a value:</span></span>  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 <span data-ttu-id="a33d4-112">i dołącz je do elementu:</span><span class="sxs-lookup"><span data-stu-id="a33d4-112">and attach it to the element:</span></span>  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 <span data-ttu-id="a33d4-113">**Dane wyjściowe**</span><span class="sxs-lookup"><span data-stu-id="a33d4-113">**Output**</span></span>  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="a33d4-114">Kodu pełny przykład można znaleźć w folderze <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="a33d4-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>  
  
 <span data-ttu-id="a33d4-115">Można również utworzyć **XmlAttribute** węzeł i użyj **InsertBefore** lub **InsertAfter** metody umieszczony w odpowiedniej pozycji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a33d4-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="a33d4-116">Jeśli atrybut o takiej samej nazwie jest już obecny w kolekcji atrybutów, istniejące **XmlAttribute** węzeł zostanie usunięty z kolekcji i nowych **XmlAttribute** wstawić węzła.</span><span class="sxs-lookup"><span data-stu-id="a33d4-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="a33d4-117">Wykonuje ten sam sposób jak **SetAttribute** metody.</span><span class="sxs-lookup"><span data-stu-id="a33d4-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="a33d4-118">Te metody przyjmują jako parametr istniejący węzeł jako punkt odniesienia w celu **InsertBefore** i **InsertAfter**.</span><span class="sxs-lookup"><span data-stu-id="a33d4-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="a33d4-119">Jeśli nie podasz węzeł odniesienia, wskazując miejsca do wstawienia nowego węzła, wartością domyślną **InsertAfter** metodą jest Wstaw nowy węzeł na początku kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a33d4-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="a33d4-120">To domyślne położenie dla **InsertBefore**, jeśli żaden węzeł odniesienia jest dostępne, znajduje się na końcu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="a33d4-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>  
  
 <span data-ttu-id="a33d4-121">Jeśli utworzono **XmlNamedNodeMap** atrybutów, można dodać atrybutu przy użyciu nazwy <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="a33d4-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span></span> <span data-ttu-id="a33d4-122">Aby uzyskać więcej informacji, zobacz [węzła kolekcje NamedNodeMaps i NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span><span class="sxs-lookup"><span data-stu-id="a33d4-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span></span>  
  
## <a name="default-attributes"></a><span data-ttu-id="a33d4-123">Domyślne atrybuty</span><span class="sxs-lookup"><span data-stu-id="a33d4-123">Default Attributes</span></span>  
 <span data-ttu-id="a33d4-124">Jeśli utworzysz element, który jest zadeklarowana, aby mieć domyślnego atrybutu nowy atrybut domyślny z wartością domyślną jest tworzone przez XML modelu DOM (Document Object) i dołączony do elementu.</span><span class="sxs-lookup"><span data-stu-id="a33d4-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="a33d4-125">Węzły podrzędne domyślny atrybut również są tworzone w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="a33d4-125">The child nodes of the default attribute are also created at this time.</span></span>  
  
## <a name="attribute-child-nodes"></a><span data-ttu-id="a33d4-126">Węzły podrzędne atrybutu</span><span class="sxs-lookup"><span data-stu-id="a33d4-126">Attribute Child Nodes</span></span>  
 <span data-ttu-id="a33d4-127">Wartość węzła atrybutu staje się węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="a33d4-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="a33d4-128">Istnieją tylko dwa typy węzłów prawidłowy element podrzędny: **XmlText** węzłów i **XmlEntityReference** węzłów.</span><span class="sxs-lookup"><span data-stu-id="a33d4-128">There are only two types of valid child nodes: **XmlText** nodes, and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="a33d4-129">Są to węzłów podrzędnych w tym sensie, że metod, takich jak **FirstChild** i **LastChild** ich przetworzyć jako węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="a33d4-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="a33d4-130">Podczas próby usunięcia atrybuty lub atrybut węzły podrzędne, ważne jest tej różnicy atrybutu o węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="a33d4-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="a33d4-131">Aby uzyskać więcej informacji, zobacz [usuwanie atrybutów z węzłem elementu w modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="a33d4-131">For more information, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a33d4-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a33d4-132">See Also</span></span>  
 [<span data-ttu-id="a33d4-133">Modelu obiektu dokumentu XML modelu DOM)</span><span class="sxs-lookup"><span data-stu-id="a33d4-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
