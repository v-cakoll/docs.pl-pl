---
title: Wstępne rozproszenie obiektów XName (LINQ to XML)
ms.date: 07/20/2015
ms.assetid: 06ea104b-f44c-4bb2-9c34-889ae025c80d
ms.openlocfilehash: a87a37c5fe2fc29ca980c77d9c775b2b1e909cc1
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74353116"
---
# <a name="pre-atomization-of-xname-objects-linq-to-xml-visual-basic"></a><span data-ttu-id="25fa2-102">Rozproszenie obiektów XName (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25fa2-102">Pre-Atomization of XName Objects (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="25fa2-103">Jednym ze sposobów poprawy wydajności LINQ to XML jest wyodrębnić <xref:System.Xml.Linq.XName> obiektów.</span><span class="sxs-lookup"><span data-stu-id="25fa2-103">One way to improve performance in LINQ to XML is to pre-atomize <xref:System.Xml.Linq.XName> objects.</span></span> <span data-ttu-id="25fa2-104">Rozproszenie oznacza przypisanie ciągu do obiektu <xref:System.Xml.Linq.XName> przed utworzeniem drzewa XML przy użyciu konstruktorów klas <xref:System.Xml.Linq.XElement> i <xref:System.Xml.Linq.XAttribute>.</span><span class="sxs-lookup"><span data-stu-id="25fa2-104">Pre-atomization means that you assign a string to an <xref:System.Xml.Linq.XName> object before you create the XML tree by using the constructors of the <xref:System.Xml.Linq.XElement> and  <xref:System.Xml.Linq.XAttribute> classes.</span></span> <span data-ttu-id="25fa2-105">Następnie zamiast przekazywania ciągu do konstruktora, który mógłby użyć niejawnej konwersji z ciągu na <xref:System.Xml.Linq.XName>, zostanie przekazany zainicjowany <xref:System.Xml.Linq.XName> obiekt.</span><span class="sxs-lookup"><span data-stu-id="25fa2-105">Then, instead of passing a string to the constructor, which would use the implicit conversion from string to <xref:System.Xml.Linq.XName>, you pass the initialized <xref:System.Xml.Linq.XName> object.</span></span>  
  
 <span data-ttu-id="25fa2-106">Zwiększa to wydajność podczas tworzenia dużego drzewa XML, w którym określone nazwy są powtarzane.</span><span class="sxs-lookup"><span data-stu-id="25fa2-106">This improves performance when you create a large XML tree in which specific names are repeated.</span></span> <span data-ttu-id="25fa2-107">W tym celu należy zadeklarować i zainicjować <xref:System.Xml.Linq.XName> obiektów przed rozpoczęciem tworzenia drzewa XML, a następnie użyć obiektów <xref:System.Xml.Linq.XName> zamiast określania ciągów nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="25fa2-107">To do this, you declare and initialize <xref:System.Xml.Linq.XName> objects before you construct the XML tree, and then use the <xref:System.Xml.Linq.XName> objects instead of specifying strings for the element and attribute names.</span></span> <span data-ttu-id="25fa2-108">Ta technika może przynieść znaczący wzrost wydajności w przypadku tworzenia dużej liczby elementów (lub atrybutów) o tej samej nazwie.</span><span class="sxs-lookup"><span data-stu-id="25fa2-108">This technique can yield significant performance gains if you are creating a large number of elements (or attributes) with the same name.</span></span>  
  
 <span data-ttu-id="25fa2-109">Należy przetestować rozproszenie z Twoim scenariuszem, aby zdecydować, czy należy z niego korzystać.</span><span class="sxs-lookup"><span data-stu-id="25fa2-109">You should test pre-atomization with your scenario to decide if you should use it.</span></span>  
  
## <a name="example"></a><span data-ttu-id="25fa2-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="25fa2-110">Example</span></span>  
 <span data-ttu-id="25fa2-111">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="25fa2-111">The following example demonstrates this.</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="25fa2-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="25fa2-112">This example produces the following output:</span></span>  
  
```xml  
<Root>  
  <Data ID="1">4,100,000</Data>  
  <Data ID="2">3,700,000</Data>  
  <Data ID="3">1,150,000</Data>  
</Root>  
```  
  
 <span data-ttu-id="25fa2-113">Poniższy przykład pokazuje tę samą technikę, w której dokument XML znajduje się w przestrzeni nazw:</span><span class="sxs-lookup"><span data-stu-id="25fa2-113">The following example shows the same technique where the XML document is in a namespace:</span></span>  
  
```vb  
Dim aw As XNamespace = "http://www.adventure-works.com"  
Dim Root__1 As XName = aw + "Root"  
Dim Data As XName = aw + "Data"  
Dim ID As XName = "ID"  
  
Dim root__2 As New XElement(Root__1, New XAttribute(XNamespace.Xmlns + "aw", aw), New XElement(Data, New XAttribute(ID, "1"), "4,100,000"), New XElement(Data, New XAttribute(ID, "2"), "3,700,000"), New XElement(Data, New XAttribute(ID, "3"), "1,150,000"))  
  
Console.WriteLine(root__2)  
```  
  
 <span data-ttu-id="25fa2-114">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="25fa2-114">This example produces the following output:</span></span>  
  
```xml  
<aw:Root xmlns:aw="http://www.adventure-works.com">  
  <aw:Data ID="1">4,100,000</aw:Data>  
  <aw:Data ID="2">3,700,000</aw:Data>  
  <aw:Data ID="3">1,150,000</aw:Data>  
</aw:Root>  
```  
  
 <span data-ttu-id="25fa2-115">Poniższy przykład jest bardziej podobny do tego, co prawdopodobnie napotkasz w świecie rzeczywistym.</span><span class="sxs-lookup"><span data-stu-id="25fa2-115">The following example is more similar to what you will likely encounter in the real world.</span></span> <span data-ttu-id="25fa2-116">W tym przykładzie zawartość elementu jest dostarczana przez zapytanie:</span><span class="sxs-lookup"><span data-stu-id="25fa2-116">In this example, the content of the element is supplied by a query:</span></span>  
  
```vb  
Dim Root__1 As XName = "Root"  
Dim Data As XName = "Data"  
Dim ID As XName = "ID"  
  
Dim t1 As DateTime = DateTime.Now  
Dim root__2 As New XElement(Root__1, From i In System.Linq.Enumerable.Range(1, 100000)New XElement(Data, New XAttribute(ID, i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
 <span data-ttu-id="25fa2-117">Poprzedni przykład wykonuje lepsze niż Poniższy przykład, w którym nazwy nie są wstępnie atomne:</span><span class="sxs-lookup"><span data-stu-id="25fa2-117">The previous example performs better than the following example, in which names are not pre-atomized:</span></span>  
  
```vb  
Dim t1 As DateTime = DateTime.Now  
Dim root As New XElement("Root", From i In System.Linq.Enumerable.Range(1, 100000)New XElement("Data", New XAttribute("ID", i), i * 5))  
Dim t2 As DateTime = DateTime.Now  
  
Console.WriteLine("Time to construct:{0}", t2 - t1)  
```  
  
## <a name="see-also"></a><span data-ttu-id="25fa2-118">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="25fa2-118">See also</span></span>

- [<span data-ttu-id="25fa2-119">Wydajność (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25fa2-119">Performance (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/performance-linq-to-xml.md)
- [<span data-ttu-id="25fa2-120">Atomed XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="25fa2-120">Atomized XName and XNamespace Objects (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/atomized-xname-and-xnamespace-objects-linq-to-xml.md)
