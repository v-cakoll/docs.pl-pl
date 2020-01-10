---
title: Tworzenie nowych atrybutów dla elementów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: dd6dc920-b011-418a-b3db-f1580a7d9251
ms.openlocfilehash: 79a3390933256ed862d35c90db0aab2177cdfc41
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75711015"
---
# <a name="creating-new-attributes-for-elements-in-the-dom"></a><span data-ttu-id="571d1-102">Tworzenie nowych atrybutów dla elementów w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="571d1-102">Creating New Attributes for Elements in the DOM</span></span>

<span data-ttu-id="571d1-103">Tworzenie nowych atrybutów jest inne niż tworzenie innych typów węzłów, ponieważ atrybuty nie są węzłami, ale są właściwościami węzła elementu i są zawarte w **XmlAttributeCollection** skojarzonym z elementem.</span><span class="sxs-lookup"><span data-stu-id="571d1-103">Creating new attributes is different than creating other node types, because attributes are not nodes, but are properties of an element node and are contained in an **XmlAttributeCollection** associated with the element.</span></span> <span data-ttu-id="571d1-104">Istnieje wiele sposobów utworzenia atrybutu i dołączenia go do elementu:</span><span class="sxs-lookup"><span data-stu-id="571d1-104">There are multiple ways to create an attribute and attach it to an element:</span></span>

- <span data-ttu-id="571d1-105">Pobierz węzeł elementu i Użyj **Właściwości SetAttribute** , aby dodać atrybut do kolekcji atrybutów tego elementu.</span><span class="sxs-lookup"><span data-stu-id="571d1-105">Get the element node and use **SetAttribute** to add an attribute to the attribute collection of that element.</span></span>

- <span data-ttu-id="571d1-106">Utwórz węzeł **XmlAttribute** przy użyciu metody **CreateAttribute** , Pobierz węzeł elementu, a następnie użyj **SetAttributeNode** , aby dodać węzeł do kolekcji atrybutów tego elementu.</span><span class="sxs-lookup"><span data-stu-id="571d1-106">Create an **XmlAttribute** node using the **CreateAttribute** method, get the element node, then use **SetAttributeNode** to add the node to the attribute collection of that element.</span></span>

<span data-ttu-id="571d1-107">Poniższy przykład pokazuje, jak dodać atrybut do elementu przy użyciu metody **SetAttribute** :</span><span class="sxs-lookup"><span data-stu-id="571d1-107">The following example shows how to add an attribute to an element using the **SetAttribute** method:</span></span>

```vb
Imports System.IO
Imports System.Xml

Public Class Sample

    Public Shared Sub Main()

        Dim doc As New XmlDocument()
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" & _
                    "<title>Pride And Prejudice</title>" & _
                    "</book>")
        Dim root As XmlElement = doc.DocumentElement

        ' Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel")

        Console.WriteLine("Display the modified XML...")
        Console.WriteLine(doc.InnerXml)
    End Sub
End Class
```  
  
```csharp
using System;
using System.IO;
using System.Xml;

public class Sample
{
    public static void Main()
    {
        var doc = new XmlDocument();
        doc.LoadXml("<book xmlns:bk='urn:samples' bk:ISBN='1-861001-57-5'>" +
                    "<title>Pride And Prejudice</title>" +
                    "</book>");
        XmlElement root = doc.DocumentElement;

        // Add a new attribute.
        root.SetAttribute("genre", "urn:samples", "novel");

        Console.WriteLine("Display the modified XML...");
        Console.WriteLine(doc.InnerXml);
    }
}
```

<span data-ttu-id="571d1-108">Poniższy przykład przedstawia nowy atrybut tworzony przy użyciu metody **CreateAttribute** .</span><span class="sxs-lookup"><span data-stu-id="571d1-108">The following example shows a new attribute being created using the **CreateAttribute** method.</span></span> <span data-ttu-id="571d1-109">Następnie pokazuje atrybut dodany do kolekcji atrybutów elementu **Book** przy użyciu metody **SetAttributeNode** .</span><span class="sxs-lookup"><span data-stu-id="571d1-109">It then shows the attribute added to the attribute collection of the **book** element using the **SetAttributeNode** method.</span></span>

<span data-ttu-id="571d1-110">Uwzględniając następujący kod XML:</span><span class="sxs-lookup"><span data-stu-id="571d1-110">Given the following XML:</span></span>
  
```xml
<book genre='novel' ISBN='1-861001-57-5'>
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="571d1-111">Utwórz nowy atrybut i nadaj mu wartość:</span><span class="sxs-lookup"><span data-stu-id="571d1-111">create a new attribute and give it a value:</span></span>

```vb
Dim attr As XmlAttribute = doc.CreateAttribute("publisher")
attr.Value = "WorldWide Publishing"
```

```csharp
XmlAttribute attr = doc.CreateAttribute("publisher");
attr.Value = "WorldWide Publishing";
```

<span data-ttu-id="571d1-112">i Dołącz do elementu:</span><span class="sxs-lookup"><span data-stu-id="571d1-112">and attach it to the element:</span></span>

```vb
doc.DocumentElement.SetAttributeNode(attr)
```

```csharp
doc.DocumentElement.SetAttributeNode(attr);
```

<span data-ttu-id="571d1-113">**Output**</span><span class="sxs-lookup"><span data-stu-id="571d1-113">**Output**</span></span>

```xml
<book genre="novel" ISBN="1-861001-57-5" publisher="WorldWide Publishing">
<title>Pride And Prejudice</title>
</book>
```

<span data-ttu-id="571d1-114">Pełny przykładowy kod można znaleźć w <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span><span class="sxs-lookup"><span data-stu-id="571d1-114">The full code sample can be found at <xref:System.Xml.XmlDocument.CreateAttribute%2A>.</span></span>

<span data-ttu-id="571d1-115">Można również utworzyć węzeł **XmlAttribute** i użyć metod **InsertBefore** lub **InsertAfter** , aby umieścić go w odpowiedniej pozycji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="571d1-115">You can also create an **XmlAttribute** node and use the **InsertBefore** or **InsertAfter** methods to place it in the appropriate position in the collection.</span></span> <span data-ttu-id="571d1-116">Jeśli atrybut o tej samej nazwie już istnieje w kolekcji atrybutów, istniejący węzeł **XmlAttribute** zostanie usunięty z kolekcji, a nowy węzeł **XmlAttribute** zostanie wstawiony.</span><span class="sxs-lookup"><span data-stu-id="571d1-116">If an attribute with the same name is already present in the attribute collection, the existing **XmlAttribute** node is removed from the collection and the new **XmlAttribute** node is inserted.</span></span> <span data-ttu-id="571d1-117">Jest to tak samo samo jak Metoda **SetAttribute** .</span><span class="sxs-lookup"><span data-stu-id="571d1-117">This performs the same way as the **SetAttribute** method.</span></span> <span data-ttu-id="571d1-118">Metody te przyjmują jako parametr, istniejący węzeł jako punkt odniesienia do wykonania **InsertBefore** i **InsertAfter**.</span><span class="sxs-lookup"><span data-stu-id="571d1-118">These methods take, as a parameter, an existing node as a reference point to do the **InsertBefore** and **InsertAfter**.</span></span> <span data-ttu-id="571d1-119">Jeśli nie podasz węzła referencyjnego wskazującego, gdzie wstawić nowy węzeł, wartość domyślna dla metody **InsertAfter** polega na wstawieniu nowego węzła na początku kolekcji.</span><span class="sxs-lookup"><span data-stu-id="571d1-119">If you do not provide a reference node indicating where to insert the new node, the default for the **InsertAfter** method is to insert the new node at the beginning of the collection.</span></span> <span data-ttu-id="571d1-120">Domyślna pozycja **InsertBefore**, jeśli nie podano węzła odwołania, znajduje się na końcu kolekcji.</span><span class="sxs-lookup"><span data-stu-id="571d1-120">The default position for the **InsertBefore**, if no reference node is provided, is at the end of the collection.</span></span>

<span data-ttu-id="571d1-121">Jeśli utworzono **XmlNamedNodeMap** atrybutów, można dodać atrybut według nazwy przy użyciu metody <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A>.</span><span class="sxs-lookup"><span data-stu-id="571d1-121">If you created an **XmlNamedNodeMap** of attributes, you can add an attribute by name using the <xref:System.Xml.XmlNamedNodeMap.SetNamedItem%2A> method.</span></span> <span data-ttu-id="571d1-122">Aby uzyskać więcej informacji, zobacz [kolekcje węzłów w NamedNodeMaps i aktualizacja](node-collections-in-namednodemaps-and-nodelists.md).</span><span class="sxs-lookup"><span data-stu-id="571d1-122">For more information, see [Node Collections in NamedNodeMaps and NodeLists](node-collections-in-namednodemaps-and-nodelists.md).</span></span>

## <a name="default-attributes"></a><span data-ttu-id="571d1-123">Atrybuty domyślne</span><span class="sxs-lookup"><span data-stu-id="571d1-123">Default attributes</span></span>

<span data-ttu-id="571d1-124">Jeśli utworzysz element, który jest zadeklarowany jako mający atrybut domyślny, wówczas nowy domyślny atrybut z jego wartością domyślną jest tworzony przez XML Document Object Model (DOM) i dołączony do elementu.</span><span class="sxs-lookup"><span data-stu-id="571d1-124">If you create an element that is declared to have a default attribute, then a new default attribute with its default value is created by the XML Document Object Model (DOM) and attached to the element.</span></span> <span data-ttu-id="571d1-125">Węzły podrzędne atrybutu domyślnego są również tworzone w tym momencie.</span><span class="sxs-lookup"><span data-stu-id="571d1-125">The child nodes of the default attribute are also created at this time.</span></span>

## <a name="attribute-child-nodes"></a><span data-ttu-id="571d1-126">Węzły podrzędne atrybutu</span><span class="sxs-lookup"><span data-stu-id="571d1-126">Attribute child nodes</span></span>

<span data-ttu-id="571d1-127">Wartość węzła atrybutu staną się węzłami podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="571d1-127">The value of an attribute node becomes its child nodes.</span></span> <span data-ttu-id="571d1-128">Istnieją tylko dwa typy prawidłowych węzłów podrzędnych: węzły **XmlText** i **XmlEntityReference** .</span><span class="sxs-lookup"><span data-stu-id="571d1-128">There are only two types of valid child nodes: **XmlText** nodes and **XmlEntityReference** nodes.</span></span> <span data-ttu-id="571d1-129">Są to węzły podrzędne w sensie, że metody, takie jak **FirstChild** i **LastChild** , przetwarzają je jako węzły podrzędne.</span><span class="sxs-lookup"><span data-stu-id="571d1-129">These are child nodes in the sense that methods such as **FirstChild** and **LastChild** process them as child nodes.</span></span> <span data-ttu-id="571d1-130">Takie rozróżnienie atrybutu z węzłami podrzędnymi jest ważne przy próbie usunięcia atrybutów lub węzłów podrzędnych atrybutu.</span><span class="sxs-lookup"><span data-stu-id="571d1-130">This distinction of an attribute having child nodes is important when trying to remove attributes or attribute child nodes.</span></span> <span data-ttu-id="571d1-131">Aby uzyskać więcej informacji, zobacz [usuwanie atrybutów z węzła elementu w modelu dom](removing-attributes-from-an-element-node-in-the-dom.md).</span><span class="sxs-lookup"><span data-stu-id="571d1-131">For more information, see [Removing Attributes from an Element Node in the DOM](removing-attributes-from-an-element-node-in-the-dom.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="571d1-132">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="571d1-132">See also</span></span>

- [<span data-ttu-id="571d1-133">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="571d1-133">XML Document Object Model (DOM)</span></span>](xml-document-object-model-dom.md)
