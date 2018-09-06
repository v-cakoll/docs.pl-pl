---
title: Uzyskiwanie dostępu do atrybutów w modelu DOM
ms.date: 03/30/2017
ms.technology: dotnet-standard
dev_langs:
- csharp
- vb
ms.assetid: ce2df341-a1a4-4e97-8e1b-cd45b8e3e71e
author: mairaw
ms.author: mairaw
ms.openlocfilehash: aeb0a8e80a023568f192e832b1e4a3244fc87455
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/06/2018
ms.locfileid: "43870175"
---
# <a name="accessing-attributes-in-the-dom"></a><span data-ttu-id="8dd5e-102">Uzyskiwanie dostępu do atrybutów w modelu DOM</span><span class="sxs-lookup"><span data-stu-id="8dd5e-102">Accessing Attributes in the DOM</span></span>
<span data-ttu-id="8dd5e-103">Atrybuty to właściwości elementu, nie elementów podrzędnych elementu.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-103">Attributes are properties of the element, not children of the element.</span></span> <span data-ttu-id="8dd5e-104">Ważne jest wykonywania tego rozróżnienia ze względu na metody służące do nawigacji element równorzędny, nadrzędny i węzły podrzędne węzła XML Document Object Model (DOM).</span><span class="sxs-lookup"><span data-stu-id="8dd5e-104">This distinction is important because of the methods used to navigate sibling, parent, and child nodes of the XML Document Object Model (DOM).</span></span> <span data-ttu-id="8dd5e-105">Na przykład **PreviousSibling** i **NextSibling** metod nie są używane do nawigacji z elementu, atrybutu lub między atrybutami.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-105">For example, the **PreviousSibling** and **NextSibling** methods are not used to navigate from an element to an attribute or between attributes.</span></span> <span data-ttu-id="8dd5e-106">Zamiast tego atrybutu jest właściwością elementu i należące do elementu, ma **OwnerElement** właściwości i nie **parentNode** właściwości i ma różnych metod nawigacji.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-106">Instead, an attribute is a property of an element and is owned by an element, has an **OwnerElement** property and not a **parentNode** property, and has distinct methods of navigation.</span></span>  
  
 <span data-ttu-id="8dd5e-107">Jeśli bieżący węzeł jest elementem, użyj **HasAttribute** metodę, aby zobaczyć, czy istnieją jakiekolwiek atrybuty skojarzone z elementem.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-107">When the current node is an element, use the **HasAttribute** method to see if there are any attributes associated with the element.</span></span> <span data-ttu-id="8dd5e-108">Gdy wiadomo, że element ma atrybuty, istnieje kilka metod uzyskania dostępu do atrybutów.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-108">Once it is known that an element has attributes, there are multiple methods for accessing attributes.</span></span> <span data-ttu-id="8dd5e-109">Aby pobrać jeden atrybut z elementu, można użyć **GetAttribute** i **GetAttributeNode** metody **XmlElement** lub możesz uzyskać wszystkie atrybuty do kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-109">To retrieve a single attribute from the element, you can use the **GetAttribute** and **GetAttributeNode** methods of the **XmlElement** or you can obtain all the attributes into a collection.</span></span> <span data-ttu-id="8dd5e-110">Uzyskiwanie kolekcji jest przydatne, jeśli potrzebujesz do iteracji w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-110">Obtaining the collection is useful if you need to iterate over the collection.</span></span> <span data-ttu-id="8dd5e-111">Jeśli chcesz, aby wszystkie atrybuty z elementu, użyj **atrybuty** właściwość elementu, aby pobrać wszystkie atrybuty w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-111">If you want all attributes from the element, use the **Attributes** property of the element to retrieve all the attributes into a collection.</span></span>  
  
## <a name="retrieving-all-attributes-into-a-collection"></a><span data-ttu-id="8dd5e-112">Pobieranie wszystkich atrybutów do kolekcji</span><span class="sxs-lookup"><span data-stu-id="8dd5e-112">Retrieving All Attributes into a Collection</span></span>  
 <span data-ttu-id="8dd5e-113">Jeśli chcesz, aby wszystkie atrybuty węzła elementu to wprowadzane do kolekcji, należy wywołać **XmlElement.Attributes** właściwości.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-113">If you want all the attributes of an element node put into a collection, call the **XmlElement.Attributes** property.</span></span> <span data-ttu-id="8dd5e-114">Spowoduje pobranie **XmlAttributeCollection** zawiera wszystkie atrybuty elementu.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-114">This gets the **XmlAttributeCollection** that contains all the attributes of an element.</span></span> <span data-ttu-id="8dd5e-115">**XmlAttributeCollection** klasa dziedziczy **XmlNamedNode** mapy.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-115">The **XmlAttributeCollection** class inherits from the **XmlNamedNode** map.</span></span> <span data-ttu-id="8dd5e-116">W związku z tym, metody i właściwości dostępne w kolekcji obejmują te, które są dostępne na mapie nazwany węzeł dodatkowo do metod i właściwości specyficzne dla **XmlAttributeCollection** klasy, takie jak **ItemOf**  właściwości lub **Append** metody.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-116">Therefore, the methods and properties available on the collection include those available on a named node map in addition to methods and properties specific to the **XmlAttributeCollection** class, such as the **ItemOf** property or the **Append** method.</span></span> <span data-ttu-id="8dd5e-117">Reprezentuje każdego elementu w kolekcji atrybutów **XmlAttribute** węzła.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-117">Each item in the attribute collection represents an **XmlAttribute** node.</span></span> <span data-ttu-id="8dd5e-118">Aby znaleźć liczby atrybutów w elemencie, Uzyskaj **XmlAttributeCollection**i użyj **liczba** właściwości, aby zobaczyć, ile **XmlAttribute** węzły znajdują się w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-118">To find the number of attributes on an element, get the **XmlAttributeCollection**, and use the **Count** property to see how many **XmlAttribute** nodes are in the collection.</span></span>  
  
 <span data-ttu-id="8dd5e-119">Poniższy przykład kodu pokazuje, jak pobrać atrybut, kolekcji i przy użyciu **liczba** metodę indeksem pętli iteracji nad nim.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-119">The following code example shows how to retrieve an attribute collection and, using the **Count** method for the looping index, iterate over it.</span></span> <span data-ttu-id="8dd5e-120">Następnie kod pokazuje, jak pobieranie pojedynczego atrybutu z kolekcji i wyświetlić jego wartość.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-120">The code then shows how to retrieve a single attribute from the collection and display its value.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.   
        Dim myElement As XmlElement = doc.DocumentElement  
  
        ' Create an attribute collection from the element.  
        Dim attrColl As XmlAttributeCollection = myElement.Attributes  
  
        ' Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...")  
        Dim i As Integer  
        For i = 0 To attrColl.Count - 1  
            Console.Write("{0} = ", attrColl.ItemOf(i).Name)  
            Console.Write("{0}", attrColl.ItemOf(i).Value)  
            Console.WriteLine()  
        Next  
  
        ' Retrieve a single attribute from the collection; specifically, the  
        ' attribute with the name "misc".  
        Dim attr As XmlAttribute = attrColl("misc")  
  
        ' Retrieve the value from that attribute.  
        Dim miscValue As String = attr.InnerXml  
  
        Console.WriteLine("Display the attribute information.")  
        Console.WriteLine(miscValue)  
  
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
        XmlDocument doc = new XmlDocument();  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" +  
                      "<title>The Handmaid's Tale</title>" +  
                      "<price>14.95</price>" +  
                      "</book>");  
  
        // Move to an element.  
        XmlElement myElement = doc.DocumentElement;  
  
        // Create an attribute collection from the element.  
        XmlAttributeCollection attrColl = myElement.Attributes;  
  
        // Show the collection by iterating over it.  
        Console.WriteLine("Display all the attributes in the collection...");  
        for (int i = 0; i < attrColl.Count; i++)  
        {  
            Console.Write("{0} = ", attrColl[i].Name);  
            Console.Write("{0}", attrColl[i].Value);  
            Console.WriteLine();  
        }  
  
        // Retrieve a single attribute from the collection; specifically, the  
        // attribute with the name "misc".  
        XmlAttribute attr = attrColl["misc"];  
  
        // Retrieve the value from that attribute.  
        String miscValue = attr.InnerXml;  
  
        Console.WriteLine("Display the attribute information.");  
        Console.WriteLine(miscValue);  
  
    }  
}  
```  
  
 <span data-ttu-id="8dd5e-121">W tym przykładzie są wyświetlane następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="8dd5e-121">This example displays the following output:</span></span>  
  
 <span data-ttu-id="8dd5e-122">**Output**</span><span class="sxs-lookup"><span data-stu-id="8dd5e-122">**Output**</span></span>  
  
 <span data-ttu-id="8dd5e-123">Wyświetl wszystkie atrybuty w kolekcji.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-123">Display all the attributes in the collection.</span></span>  
  
```  
genre = novel  
ISBN = 1-861001-57-5  
misc = sale item  
Display the attribute information.  
sale item  
```  
  
 <span data-ttu-id="8dd5e-124">Informacje przedstawione w kolekcji atrybutów można pobrać według nazwy lub numer indeksu.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-124">The information in an attribute collection can be retrieved by name or index number.</span></span> <span data-ttu-id="8dd5e-125">W powyższym przykładzie pokazano, jak można pobrać danych według nazwy.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-125">The example above shows how to retrieve data by name.</span></span> <span data-ttu-id="8dd5e-126">Następny przykład pokazuje, jak pobierać dane za pomocą numeru indeksu.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-126">The next example shows how to retrieve data by index number.</span></span>  
  
 <span data-ttu-id="8dd5e-127">Ponieważ **XmlAttributeCollection** jest kolekcją i można przez nazwę lub indeks, w tym przykładzie przedstawiono, zaznaczając pierwszy atrybut z kolekcji, a następnie używając następującego pliku liczony od zera indeks **baseuri.xml**, jako danych wejściowych.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-127">Because the **XmlAttributeCollection** is a collection and can be iterated over by name or index, this example shows selecting the first attribute out of the collection using a zero-based index and using the following file, **baseuri.xml**, as input.</span></span>  
  
### <a name="input"></a><span data-ttu-id="8dd5e-128">Dane wejściowe</span><span class="sxs-lookup"><span data-stu-id="8dd5e-128">Input</span></span>  
  
```xml  
<!-- XML fragment -->  
<book genre="novel">  
  <title>Pride And Prejudice</title>  
</book>  
```  
  
```vb  
Option Explicit On  
Option Strict On  
  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
        ' Create the XmlDocument.  
        Dim doc As New XmlDocument()  
        doc.Load("http://localhost/baseuri.xml")  
  
        ' Display information on the attribute node. The value  
        ' returned for BaseURI is 'http://localhost/baseuri.xml'.  
        Dim attr As XmlAttribute = doc.DocumentElement.Attributes(0)  
        Console.WriteLine("Name of the attribute:  {0}", attr.Name)  
        Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI)  
        Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText)  
    End Sub 'Main   
End Class 'Sample  
```  
  
```csharp  
using System;  
using System.IO;  
using System.Xml;  
  
public class Sample  
{  
  public static void Main()  
  {  
    // Create the XmlDocument.  
    XmlDocument doc = new XmlDocument();  
  
    doc.Load("http://localhost/baseuri.xml");  
  
    // Display information on the attribute node. The value  
    // returned for BaseURI is 'http://localhost/baseuri.xml'.  
    XmlAttribute attr = doc.DocumentElement.Attributes[0];  
    Console.WriteLine("Name of the attribute:  {0}", attr.Name);  
    Console.WriteLine("Base URI of the attribute:  {0}", attr.BaseURI);  
    Console.WriteLine("The value of the attribtue:  {0}", attr.InnerText);  
  }  
}  
```  
  
## <a name="retrieving-an-individual-attribute-node"></a><span data-ttu-id="8dd5e-129">Trwa pobieranie węzłem poszczególne atrybuty</span><span class="sxs-lookup"><span data-stu-id="8dd5e-129">Retrieving an Individual Attribute Node</span></span>  
 <span data-ttu-id="8dd5e-130">Można pobrać węzła jeden atrybut z elementu <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> metoda jest używana.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-130">To retrieve a single attribute node from an element, the <xref:System.Xml.XmlElement.GetAttributeNode%2A?displayProperty=nameWithType> method is used.</span></span> <span data-ttu-id="8dd5e-131">Zwraca obiekt typu **XmlAttribute**.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-131">It returns an object of type **XmlAttribute**.</span></span> <span data-ttu-id="8dd5e-132">Po utworzeniu **XmlAttribute**, wszystkie metody i właściwości dostępnych w <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> klasy są dostępne dla tego obiektu, takie jak wyszukiwanie **OwnerElement**.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-132">Once you have an **XmlAttribute**, all the methods and properties available in the <xref:System.Xml.XmlAttribute?displayProperty=nameWithType> class are available on that object, such as finding the **OwnerElement**.</span></span>  
  
```vb  
Imports System  
Imports System.IO  
Imports System.Xml  
  
Public Class Sample  
  
    Public Shared Sub Main()  
  
        Dim doc As XmlDocument = New XmlDocument()  
        doc.LoadXml("<book genre='novel' ISBN='1-861001-57-5' misc='sale item'>" & _  
               "<title>The Handmaid's Tale</title>" & _  
               "<price>14.95</price>" & _  
               "</book>")  
  
        ' Move to an element.  
        Dim root As XmlElement  
        root = doc.DocumentElement  
  
        ' Get an attribute.  
        Dim attr As XmlAttribute  
        attr = root.GetAttributeNode("ISBN")  
  
        ' Display the value of the attribute.  
        Dim attrValue As String  
        attrValue = attr.InnerXml  
        Console.WriteLine(attrValue)  
  
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
    XmlDocument doc = new XmlDocument();  
     doc.LoadXml("<book genre='novel' ISBN='1-861003-78' misc='sale item'>" +  
                   "<title>The Handmaid's Tale</title>" +  
                   "<price>14.95</price>" +  
                   "</book>");   
  
    // Move to an element.  
     XmlElement root = doc.DocumentElement;  
  
    // Get an attribute.  
     XmlAttribute attr = root.GetAttributeNode("ISBN");  
  
    // Display the value of the attribute.  
     String attrValue = attr.InnerXml;  
     Console.WriteLine(attrValue);  
  
    }  
}  
```  
  
 <span data-ttu-id="8dd5e-133">Możesz również tworzyć jak pokazano w poprzednim przykładzie, gdzie węzeł jeden atrybut jest pobierana z kolekcji atrybutów.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-133">You can also do as shown in the previous example, where a single attribute node is retrieved from the attribute collection.</span></span> <span data-ttu-id="8dd5e-134">Poniższy przykład kodu pokazuje sposób jeden wiersz kodu mogą być zapisywane na pobieranie pojedynczego atrybutu przez numer indeksu z katalogu głównego dokumentu XML drzewa, znanego również jako **elementu DocumentElement** właściwości.</span><span class="sxs-lookup"><span data-stu-id="8dd5e-134">The following code example shows how one line of code can be written to retrieve a single attribute by index number from the root of the XML document tree, also known as the **DocumentElement** property.</span></span>  
  
```  
XmlAttribute attr = doc.DocumentElement.Attributes[0];  
```  
  
## <a name="see-also"></a><span data-ttu-id="8dd5e-135">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8dd5e-135">See also</span></span>

- [<span data-ttu-id="8dd5e-136">Model DOM (XML Document Object Model)</span><span class="sxs-lookup"><span data-stu-id="8dd5e-136">XML Document Object Model (DOM)</span></span>](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
