---
title: 'Instrukcje: Pobieranie płytkiej wartości elementu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: a861acafe3b9561b1237e6b6449374374c723805
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54505802"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="6abd6-102">Instrukcje: Pobieranie płytkiej wartości elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6abd6-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>
<span data-ttu-id="6abd6-103">W tym temacie przedstawiono sposób pobieranie płytkiej wartości elementu.</span><span class="sxs-lookup"><span data-stu-id="6abd6-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="6abd6-104">Płytkiej wartości jest wartość określonego elementu, w przeciwieństwie do głębokiego wartość, która zawiera wartości wszystkie elementy potomne połączonych w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="6abd6-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="6abd6-105">Podczas pobierania wartości elementu przy użyciu obu rzutowania lub <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości pobrania głębokiego wartości.</span><span class="sxs-lookup"><span data-stu-id="6abd6-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="6abd6-106">Aby pobieranie płytkiej wartości, można użyć `ShallowValue` metodę rozszerzenia, jak pokazano w przykładzie follwing.</span><span class="sxs-lookup"><span data-stu-id="6abd6-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="6abd6-107">Trwa pobieranie płytkiej wartości jest przydatne w przypadku, gdy chcesz wybrać elementy, na podstawie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="6abd6-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="6abd6-108">Poniższy przykład deklaruje metodę rozszerzenia, która pobiera płytkiej wartości elementu.</span><span class="sxs-lookup"><span data-stu-id="6abd6-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="6abd6-109">Następnie używa metody rozszerzenia w zapytaniu, aby wyświetlić listę wszystkich elementów, które zawierają obliczoną wartość.</span><span class="sxs-lookup"><span data-stu-id="6abd6-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6abd6-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="6abd6-110">Example</span></span>  
 <span data-ttu-id="6abd6-111">W następującym pliku tekstowym Report.xml, jest źródłem w tym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6abd6-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>  
<Report>  
  <Section>  
    <Heading>  
      <Column Name="CustomerId">=Customer.CustomerId.Heading</Column>  
      <Column Name="Name">=Customer.Name.Heading</Column>  
    </Heading>  
    <Detail>  
      <Column Name="CustomerId">=Customer.CustomerId</Column>  
      <Column Name="Name">=Customer.Name</Column>  
    </Detail>  
  </Section>  
</Report>  
```  
  
```vb  
Module Module1  
    <System.Runtime.CompilerServices.Extension()> _  
    Public Function ShallowValue(ByVal xe As XElement)  
        Return xe _  
               .Nodes() _  
               .OfType(Of XText)() _  
               .Aggregate(New StringBuilder(), _  
                              Function(s, c) s.Append(c), _  
                              Function(s) s.ToString())  
    End Function  
  
    Sub Main()  
        Dim root As XElement = XElement.Load("Report.xml")  
  
        Dim query As IEnumerable(Of XElement) = _  
            From el In root.Descendants() _  
            Where (el.ShallowValue().StartsWith("=")) _  
            Select el  
  
        For Each q As XElement In query  
            Console.WriteLine("{0}{1}{2}", _  
                q.Name.ToString().PadRight(8), _  
                q.Attribute("Name").ToString().PadRight(20), _  
                q.ShallowValue())  
        Next  
    End Sub  
End Module  
```  
  
 <span data-ttu-id="6abd6-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="6abd6-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="6abd6-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6abd6-113">See also</span></span>
- [<span data-ttu-id="6abd6-114">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6abd6-114">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
