---
title: Wstępne Atomizacja XName obiektów (LINQ do XML) (C#)
ms.date: 07/20/2015
ms.assetid: e84fbbe7-f072-4771-bfbb-059d18e1ad15
ms.openlocfilehash: 8d793dcdfd2669fa96c92be0e0e3c3ebb8f38d0e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-c"></a><span data-ttu-id="f49d7-102">Wstępne Atomizacja XName obiektów (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f49d7-102">Pre-Atomization of XName Objects (LINQ to XML) (C#)</span></span>
<span data-ttu-id="f49d7-103">Jednym ze sposobów poprawy wydajności w składniku LINQ to XML ma wstępnie rozproszyć <xref:System.Xml.Linq.XName> obiektów.</span><span class="sxs-lookup"><span data-stu-id="f49d7-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="f49d7-104">Wstępne Atomizacja oznacza, że można przypisać ciąg <xref:System.Xml.Linq.XName> obiekt przed utworzeniem drzewa XML za pomocą konstruktorów <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute> klasy.</span><span class="sxs-lookup"><span data-stu-id="f49d7-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="f49d7-105">Następnie, zamiast przekazywanie ciąg konstruktora, który użyć niejawna konwersja z ciągu na <xref:System.Xml.Linq.XName>, należy przekazać zainicjowane <xref:System.Xml.Linq.XName> obiektu.</span><span class="sxs-lookup"><span data-stu-id="f49d7-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="f49d7-106">Poprawia to wydajność, podczas tworzenia dużych drzewa XML, w którym są powtarzane konkretne nazwy.</span><span class="sxs-lookup"><span data-stu-id="f49d7-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="f49d7-107">W tym celu należy zadeklarować i zainicjuj <xref:System.Xml.Linq.XName> obiekty przed skonstruuj drzewo XML, a następnie użyć <xref:System.Xml.Linq.XName> obiektów zamiast określania ciągów dla nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="f49d7-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="f49d7-108">Ta technika może spowodować znaczący wzrost wydajności w przypadku tworzenia dużą liczbę elementów (lub atrybutów) o takiej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="f49d7-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="f49d7-109">Należy przetestować przed Atomizacja z danego scenariusza zdecydować, czy należy z niej korzystać.</span><span class="sxs-lookup"><span data-stu-id="f49d7-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f49d7-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="f49d7-110">Example</span></span>  
 <span data-ttu-id="f49d7-111">W poniższym przykładzie pokazano to.</span><span class="sxs-lookup"><span data-stu-id="f49d7-111">The following example demonstrates this.</span></span>  
  
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
  
 <span data-ttu-id="f49d7-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f49d7-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="f49d7-113">W poniższym przykładzie przedstawiono tę samą metodę, gdy dokument XML jest w przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="f49d7-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
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
  
 <span data-ttu-id="f49d7-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="f49d7-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="f49d7-115">Poniższy przykład przypomina więcej co prawdopodobnie wystąpią w świecie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="f49d7-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="f49d7-116">W tym przykładzie zawartość elementu jest dostarczana przez kwerendę:</span><span class="sxs-lookup"><span data-stu-id="f49d7-116">In this example, the content of the element is supplied by a query:</span></span>  
  
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
  
 <span data-ttu-id="f49d7-117">Poprzedni przykład wykonuje lepszą wydajność niż poniższy przykład, w którym nazwy nie są wstępnie atomized:</span><span class="sxs-lookup"><span data-stu-id="f49d7-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f49d7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f49d7-118">See Also</span></span>  
 [<span data-ttu-id="f49d7-119">Wydajność (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f49d7-119">Performance (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/performance-linq-to-xml.md)  
 [<span data-ttu-id="f49d7-120">Atomized XName i XNamespace obiektów (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="f49d7-120">Atomized XName and XNamespace Objects (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
