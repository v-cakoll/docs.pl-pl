---
title: 'Instrukcje: Pobierz pojedynczy atrybut (LINQ to XML) (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 11b938d7-c011-4048-900e-8b9183c41c94
ms.openlocfilehash: 635644783153765d61aff3c00fe16860642c29f1
ms.sourcegitcommit: eb9ff6f364cde6f11322e03800d8f5ce302f3c73
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/01/2019
ms.locfileid: "68710527"
---
# <a name="how-to-retrieve-a-single-attribute-linq-to-xml-visual-basic"></a><span data-ttu-id="7758b-102">Instrukcje: Pobierz pojedynczy atrybut (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7758b-102">How to: Retrieve a Single Attribute (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="7758b-103">W tym temacie wyjaśniono, jak pobrać pojedynczy atrybut elementu, pod nazwą atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7758b-103">This topic explains how to retrieve a single attribute of an element, given the attribute name.</span></span> <span data-ttu-id="7758b-104">Jest to przydatne w przypadku pisania wyrażeń zapytania, gdzie chcesz znaleźć element, który ma określony atrybut.</span><span class="sxs-lookup"><span data-stu-id="7758b-104">This is useful for writing query expressions where you want to find an element that has a particular attribute.</span></span>  
  
 <span data-ttu-id="7758b-105"><xref:System.Xml.Linq.XElement.Attribute%2A> Metoda klasy<xref:System.Xml.Linq.XElement> zwraca z<xref:System.Xml.Linq.XAttribute> określoną nazwą.</span><span class="sxs-lookup"><span data-stu-id="7758b-105">The <xref:System.Xml.Linq.XElement.Attribute%2A> method of the <xref:System.Xml.Linq.XElement> class returns the <xref:System.Xml.Linq.XAttribute> with the specified name.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7758b-106">Przykład</span><span class="sxs-lookup"><span data-stu-id="7758b-106">Example</span></span>  
 <span data-ttu-id="7758b-107">W poniższym przykładzie zastosowano <xref:System.Xml.Linq.XElement.Attribute%2A> metodę.</span><span class="sxs-lookup"><span data-stu-id="7758b-107">The following example uses the <xref:System.Xml.Linq.XElement.Attribute%2A> method.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList = From el In cust...<Phone>  
For Each e As XElement In elList  
    Console.WriteLine(e.@type)  
Next  
```  
  
 <span data-ttu-id="7758b-108">Ten przykład umożliwia znalezienie wszystkich elementów podrzędnych w drzewie o nazwie `Phone`, a następnie znalezienie atrybutu o nazwie `type`.</span><span class="sxs-lookup"><span data-stu-id="7758b-108">This example finds all the descendants in the tree named `Phone`, and then finds the attribute named `type`.</span></span>  
  
 <span data-ttu-id="7758b-109">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7758b-109">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="example"></a><span data-ttu-id="7758b-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="7758b-110">Example</span></span>  
 <span data-ttu-id="7758b-111">Jeśli chcesz pobrać wartość atrybutu, możesz go rzutować, tak jak w przypadku <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="7758b-111">If you want to retrieve the value of the attribute, you can cast it, just as you do for with <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="7758b-112">Poniższy przykład ilustruje to.</span><span class="sxs-lookup"><span data-stu-id="7758b-112">The following example demonstrates this.</span></span>  
  
```vb  
Dim cust As XElement = <PhoneNumbers>  
                           <Phone type="home">555-555-5555</Phone>  
                           <Phone type="work">555-555-6666</Phone>  
                       </PhoneNumbers>  
Dim elList As IEnumerable(Of XElement) = _  
    From el In cust...<Phone> _  
    Select el  
For Each el As XElement In elList  
    Console.WriteLine(el.@type)  
Next  
```  
  
 <span data-ttu-id="7758b-113">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7758b-113">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
 [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]<span data-ttu-id="7758b-114">zapewnia jawne Operatory rzutowania dla <xref:System.Xml.Linq.XAttribute> klasy do `string` `int` `bool?` `bool` `int?`,, ,,`long?`,, ,,,`uint?` `uint` `long` `ulong`, `ulong?` ,`float?` ,,`TimeSpan`, ,`decimal?`, ,,`TimeSpan?`,, ,`GUID`i `float` `double` `DateTime` `double?` `decimal` `DateTime?`  `GUID?`.</span><span class="sxs-lookup"><span data-stu-id="7758b-114">provides explicit cast operators for the <xref:System.Xml.Linq.XAttribute> class to `string`, `bool`, `bool?`, `int`, `int?`, `uint`, `uint?`, `long`, `long?`, `ulong`, `ulong?`, `float`, `float?`, `double`, `double?`, `decimal`, `decimal?`, `DateTime`, `DateTime?`, `TimeSpan`, `TimeSpan?`, `GUID`, and `GUID?`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7758b-115">Przykład</span><span class="sxs-lookup"><span data-stu-id="7758b-115">Example</span></span>  
 <span data-ttu-id="7758b-116">Poniższy przykład pokazuje ten sam kod dla atrybutu, który znajduje się w przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="7758b-116">The following example shows the same code for an attribute that is in a namespace.</span></span> <span data-ttu-id="7758b-117">Aby uzyskać więcej informacji, zobacz temat [przestrzenie nazw — omówienie (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="7758b-117">For more information, see [Namespaces Overview (LINQ to XML) (Visual Basic)](namespaces-overview-linq-to-xml.md).</span></span>  
  
```vb  
Imports <xmlns:aw="http://www.adventure-works.com">  
  
Module Module1  
    Sub Main()  
        Dim cust As XElement = _  
            <aw:PhoneNumbers>  
                <aw:Phone aw:type="home">555-555-5555</aw:Phone>  
                <aw:Phone aw:type="work">555-555-6666</aw:Phone>  
            </aw:PhoneNumbers>  
        Dim elList As IEnumerable(Of XElement) = _  
            From el In cust...<aw:Phone> _  
            Select el  
        For Each el As XElement In elList  
            Console.WriteLine(el.@aw:type)  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="7758b-118">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="7758b-118">This code produces the following output:</span></span>  
  
```  
home  
work  
```  
  
## <a name="see-also"></a><span data-ttu-id="7758b-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="7758b-119">See also</span></span>

- [<span data-ttu-id="7758b-120">Osie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7758b-120">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
