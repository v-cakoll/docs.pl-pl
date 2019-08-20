---
title: Przedrozproszenie obiektów XName (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 2fd754a352bd2988e52ec9c67a9915a8e587b107
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69591493"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="86e87-102">Przedrozproszenie obiektów XName (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="86e87-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="86e87-103">Jednym ze sposobów poprawy wydajności LINQ to XML jest wyodrębnić <xref:System.Xml.Linq.XName> obiektów.</span><span class="sxs-lookup"><span data-stu-id="86e87-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="86e87-104">Rozproszenie oznacza przypisanie ciągu do <xref:System.Xml.Linq.XName> obiektu przed utworzeniem drzewa XML przy użyciu konstruktorów <xref:System.Xml.Linq.XElement> klas i <xref:System.Xml.Linq.XAttribute> .</span><span class="sxs-lookup"><span data-stu-id="86e87-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="86e87-105">Następnie zamiast przekazywania ciągu do konstruktora, który mógłby użyć niejawnej konwersji z ciągu na <xref:System.Xml.Linq.XName>, należy przekazać zainicjowany <xref:System.Xml.Linq.XName> obiekt.</span><span class="sxs-lookup"><span data-stu-id="86e87-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="86e87-106">Zwiększa to wydajność podczas tworzenia dużego drzewa XML, w którym określone nazwy są powtarzane.</span><span class="sxs-lookup"><span data-stu-id="86e87-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="86e87-107">W tym celu należy zadeklarować i zainicjować <xref:System.Xml.Linq.XName> obiekty przed rozpoczęciem tworzenia drzewa XML, a następnie <xref:System.Xml.Linq.XName> użyć obiektów zamiast określania ciągów nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="86e87-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="86e87-108">Ta technika może przynieść znaczący wzrost wydajności w przypadku tworzenia dużej liczby elementów (lub atrybutów) o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="86e87-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="86e87-109">Należy przetestować rozproszenie z Twoim scenariuszem, aby zdecydować, czy należy z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="86e87-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="86e87-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="86e87-110">Example</span></span>  
 <span data-ttu-id="86e87-111">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="86e87-111">The following example demonstrates this.</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="86e87-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="86e87-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="86e87-113">Poniższy przykład pokazuje tę samą technikę, w której dokument XML znajduje się w przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="86e87-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```csharp  
XNamespace aw = "http://www.adventure-works.com";  
XName Root = aw + "Root";  
XName Data = aw + "Data";  
XName ID = "ID";  
  
XElement root = new XElement(Root,  
    new XAttribute(XNamespace.Xmlns + "aw", aw),  
    new XElement(Data,  
        new XAttribute(ID, "1"),  
        "4,100,000"),  
    new XElement(Data,  
        new XAttribute(ID, "2"),  
        "3,700,000"),  
    new XElement(Data,  
        new XAttribute(ID, "3"),  
        "1,150,000")  
);  
  
Console.WriteLine(root);  
```  
  
 <span data-ttu-id="86e87-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="86e87-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="86e87-115">Poniższy przykład jest bardziej podobny do tego, co prawdopodobnie napotkasz w świecie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="86e87-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="86e87-116">W tym przykładzie zawartość elementu jest dostarczana przez zapytanie:</span><span class="sxs-lookup"><span data-stu-id="86e87-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```csharp  
XName Root = "Root";  
XName Data = "Data";  
XName ID = "ID";  
  
DateTime t1 = DateTime.Now;  
XElement root = new XElement(Root,  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement(Data,  
        new XAttribute(ID, i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
 <span data-ttu-id="86e87-117">Poprzedni przykład wykonuje lepsze niż Poniższy przykład, w którym nazwy nie są wstępnie atomne:</span><span class="sxs-lookup"><span data-stu-id="86e87-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```csharp  
DateTime t1 = DateTime.Now;  
XElement root = new XElement("Root",  
    from i in System.Linq.Enumerable.Range(1, 100000)  
    select new XElement("Data",  
        new XAttribute("ID", i),  
        i * 5)  
);  
DateTime t2 = DateTime.Now;  
  
Console.WriteLine("Time to construct:{0}", t2 - t1);  
```  
  
## <a name="see-also"></a><span data-ttu-id="86e87-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="86e87-118">See also</span></span>

- [<span data-ttu-id="86e87-119">Atomed XName and XNamespace Objects (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="86e87-119">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](./atomized-xname-and-xnamespace-objects-linq-to-xml.md)
