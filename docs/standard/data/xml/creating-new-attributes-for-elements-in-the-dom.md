---
title: Tworzenie nowych atrybutów dla elementów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 870e800220031338557792fa612d4a3101e79f90
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/10/2018
ms.locfileid: "44271945"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="afcda-102">Tworzenie nowych atrybutów dla elementów w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="afcda-102">Creating New Attributes for Elements in the DOM</span></span>
<span data-ttu-id="afcda-103">Tworzenie nowych atrybutów różni się od tworzenia innych typów węzła, ponieważ atrybutów nie są węzłami, ale są właściwości węzeł elementu i są zawarte w **XmlAttributeCollection** skojarzone z elementem.</span><span class="sxs-lookup"><span data-stu-id="afcda-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="afcda-104">Istnieje wiele sposobów, aby utworzyć atrybut i dołączyć go do elementu:</span><span class="sxs-lookup"><span data-stu-id="afcda-104">There are multiple ways to create an attribute and attach it to an element:</span></span>  
  
-   <span data-ttu-id="afcda-105">Pobierz węzeł elementu i użyć **SetAttribute** Dodawanie atrybutu do kolekcji atrybutu tego elementu.</span><span class="sxs-lookup"><span data-stu-id="afcda-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>  
  
-   <span data-ttu-id="afcda-106">Tworzenie **XmlAttribute** za pomocą węzła **CreateAttribute** metody, Pobierz węzła elementu, a następnie użyj **SetAttributeNode** można dodać węzła do kolekcji atrybutów tego element.</span><span class="sxs-lookup"><span data-stu-id="afcda-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>  
  
 <span data-ttu-id="afcda-107">Poniższy przykład przedstawia sposób dodawania atrybutu do elementu za pomocą **SetAttribute** metody.</span><span class="sxs-lookup"><span data-stu-id="afcda-107">The following example shows how to add an attribute to an element using the **SetAttribute** method.</span></span>  
  
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
  
 <span data-ttu-id="afcda-108">W poniższym przykładzie pokazano nową atrybutu tworzone przy użyciu **CreateAttribute** metody.</span><span class="sxs-lookup"><span data-stu-id="afcda-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="afcda-109">Następnie wyświetla atrybut dodawane do kolekcji atrybut **książki** elementu za pomocą **SetAttributeNode** metody.</span><span class="sxs-lookup"><span data-stu-id="afcda-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>  
  
 <span data-ttu-id="afcda-110">Biorąc pod uwagę następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="afcda-110">Given the following XML:</span></span>  
  
```xml  
<book genre='novel' ISBN='1-861001-57-5'>  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="afcda-111">Utwórz nowy atrybut i wartości:</span><span class="sxs-lookup"><span data-stu-id="afcda-111">create a new attribute and give it a value:</span></span>  
  
```vb  
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")  
   attr.Value = "WorldWide Publishing"  
```  
  
```csharp  
XmlAttribute attr = doc.CreateAttribute("publisher");  
attr.Value = "WorldWide Publishing";  
```  
  
 <span data-ttu-id="afcda-112">i dołączyć go do elementu:</span><span class="sxs-lookup"><span data-stu-id="afcda-112">and attach it to the element:</span></span>  
  
```vb  
doc.DocumentElement.SetAttributeNode(attr)  
```  
  
```csharp  
doc.DocumentElement.SetAttributeNode(attr);  
```  
  
 <span data-ttu-id="afcda-113">**Output**</span><span class="sxs-lookup"><span data-stu-id="afcda-113">**Output**</span></span>  
  
```xml  
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">  
<title>Pride And Prejudice</title>  
</book>  
```  
  
 <span data-ttu-id="afcda-114">Przykładowe pełny kod znajduje się w temacie <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="afcda-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>  
  
 <span data-ttu-id="afcda-115">Można również utworzyć **XmlAttribute** węzła i użyj **InsertBefore** lub **InsertAfter** metody, aby umieścić go w odpowiedniej pozycji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="afcda-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="afcda-116">Jeśli atrybut o tej samej nazwie istnieje już w kolekcji atrybutów istniejących **XmlAttribute** węzeł zostanie usunięty z kolekcji, a nowe **XmlAttribute** wstawić węzła.</span><span class="sxs-lookup"><span data-stu-id="afcda-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="afcda-117">Spowoduje to wykonanie taki sam sposób jak **SetAttribute** metody.</span><span class="sxs-lookup"><span data-stu-id="afcda-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="afcda-118">Te metody przyjmują jako parametru, istniejący węzeł jako punkt odniesienia w celu **InsertBefore** i **InsertAfter**.</span><span class="sxs-lookup"><span data-stu-id="afcda-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="afcda-119">Jeśli nie podasz węzeł odniesienia, wskazując, skąd można wstawić nowy węzeł, wartość domyślna dla **InsertAfter** metoda polega na Wstaw nowy węzeł na początku kolekcji.</span><span class="sxs-lookup"><span data-stu-id="afcda-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="afcda-120">Domyślne położenie **InsertBefore**, jeśli nie podano żadnego węzła odwołanie, znajduje się na końcu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="afcda-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>  
  
 <span data-ttu-id="afcda-121">Jeśli utworzono **XmlNamedNodeMap** atrybutów, można dodać atrybutu przy użyciu nazwy <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="afcda-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span></span> <span data-ttu-id="afcda-122">Aby uzyskać więcej informacji, zobacz [kolekcje węzłów: namednodemaps i NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span><span class="sxs-lookup"><span data-stu-id="afcda-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](../../../../docs/standard/data/xml/node-collections-in-namednodemaps-and-nodelists.md).</span></span>  
  
## <a name="default-attributes"></a><span data-ttu-id="afcda-123">Atrybuty domyślne</span><span class="sxs-lookup"><span data-stu-id="afcda-123">Default Attributes</span></span>  
 <span data-ttu-id="afcda-124">Jeśli utworzysz element, który jest zadeklarowany ma atrybut domyślny, nowy domyślny atrybut o jego wartość domyślna jest tworzone przez XML Document Object Model (DOM) i dołączony do elementu.</span><span class="sxs-lookup"><span data-stu-id="afcda-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="afcda-125">Węzły podrzędne domyślnego atrybutu są również tworzone w tej chwili.</span><span class="sxs-lookup"><span data-stu-id="afcda-125">The child nodes of the default attribute are also created at this time.</span></span>  
  
## <a name="attribute-child-nodes"></a><span data-ttu-id="afcda-126">Węzły podrzędne atrybutu</span><span class="sxs-lookup"><span data-stu-id="afcda-126">Attribute Child Nodes</span></span>  
 <span data-ttu-id="afcda-127">Wartość węzła atrybutu staje się jego węzłów podrzędnych.</span><span class="sxs-lookup"><span data-stu-id="afcda-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="afcda-128">Istnieją tylko dwa typy węzłów prawidłowy element podrzędny: **XmlText** węzłów i **XmlEntityReference** węzłów.</span><span class="sxs-lookup"><span data-stu-id="afcda-128">There are only two types of valid child nodes: **XmlText** nodes, and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="afcda-129">Są węzły podrzędne, w tym sensie, że metody, takie jak **FirstChild** i **LastChild** przetwarzać je jako węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="afcda-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="afcda-130">Wykonywania tego rozróżnienia atrybutu o węzłów podrzędnych jest ważne, podczas próby usunięcia atrybutów i węzłów podrzędnych atrybutu.</span><span class="sxs-lookup"><span data-stu-id="afcda-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="afcda-131">Aby uzyskać więcej informacji, zobacz [usuwanie atrybutów z węzła elementu w modelu DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="afcda-131">For more information, see [Removing Attributes from an Element Node in the DOM](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="afcda-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="afcda-132">See also</span></span>

- [<span data-ttu-id="afcda-133">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="afcda-133">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
