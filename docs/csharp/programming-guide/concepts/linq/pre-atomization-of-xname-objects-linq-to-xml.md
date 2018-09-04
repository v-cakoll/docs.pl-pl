---
title: Wstępne rozproszenie obiektów XName (LINQ to XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 6a1f3ea5e0b53fe488c13ebd273cce436d7c685b
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43516219"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="c4b4c-102">Wstępne rozproszenie obiektów XName (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c4b4c-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="c4b4c-103">Jednym ze sposobów, aby zwiększyć wydajność w składniku LINQ to XML jest wstępnie wyodrębnić <xref:System.Xml.Linq.XName> obiektów.</span><span class="sxs-lookup"><span data-stu-id="c4b4c-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="c4b4c-104">Wstępne rozproszenie oznacza, że możesz przypisać ciąg <xref:System.Xml.Linq.XName> obiekt przed przystąpieniem do tworzenia drzewa XML za pomocą konstruktorów z <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="c4b4c-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="c4b4c-105">Następnie, zamiast przekazywać ciąg do konstruktora, który użyć niejawna konwersja ciągu na <xref:System.Xml.Linq.XName>, należy przekazać zainicjowanej <xref:System.Xml.Linq.XName> obiektu.</span><span class="sxs-lookup"><span data-stu-id="c4b4c-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="c4b4c-106">Poprawia to wydajność, podczas tworzenia dużych drzewa XML, w którym są powtarzane określonej nazwy.</span><span class="sxs-lookup"><span data-stu-id="c4b4c-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="c4b4c-107">Aby to zrobić, możesz zadeklarować i zainicjować <xref:System.Xml.Linq.XName> obiektów przed konstruowania drzewa XML, a następnie użyj <xref:System.Xml.Linq.XName> obiektów zamiast określania ciągów nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="c4b4c-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="c4b4c-108">Ta technika może przynieść znaczący wzrost wydajności w przypadku tworzenia dużej liczby elementów (lub atrybutów) o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="c4b4c-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="c4b4c-109">Wstępne rozproszenie należy przetestować przy użyciu danego scenariusza, aby zdecydować, czy należy jej używać.</span><span class="sxs-lookup"><span data-stu-id="c4b4c-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4b4c-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="c4b4c-110">Example</span></span>  
 <span data-ttu-id="c4b4c-111">Poniższy przykład przedstawia to.</span><span class="sxs-lookup"><span data-stu-id="c4b4c-111">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="c4b4c-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c4b4c-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="c4b4c-113">Poniższy przykład pokazuje tę samą technikę, w którym dokument XML jest w przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="c4b4c-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
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
  
 <span data-ttu-id="c4b4c-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="c4b4c-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="c4b4c-115">Poniższy przykład jest bardziej przypominające, co prawdopodobnie wystąpi w świecie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="c4b4c-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="c4b4c-116">W tym przykładzie zawartość elementu jest dostarczana przez kwerendę:</span><span class="sxs-lookup"><span data-stu-id="c4b4c-116">In this example, the content of the element is supplied by a query:</span></span>  
  
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
  
 <span data-ttu-id="c4b4c-117">Poprzedni przykład działa lepiej niż poniższy przykład, w których nazwy są nie wstępnie rozproszone obiekty:</span><span class="sxs-lookup"><span data-stu-id="c4b4c-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="c4b4c-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c4b4c-118">See Also</span></span>

- [<span data-ttu-id="c4b4c-119">Wydajność (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c4b4c-119">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)  
- [<span data-ttu-id="c4b4c-120">Rozproszone obiekty XName i Xnamespace (LINQ to XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="c4b4c-120">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
