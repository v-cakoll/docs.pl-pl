---
title: 'Porady: pobieranie skrócona wartość elementu (Visual Basic)'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 228afa6cd4bf0599bf7bd63afff17014799ef1b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="3a4e2-102">Porady: pobieranie skrócona wartość elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a4e2-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>
<span data-ttu-id="3a4e2-103">W tym temacie pokazano, jak pobrać pobieżną wartości elementu.</span><span class="sxs-lookup"><span data-stu-id="3a4e2-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="3a4e2-104">Skrócona wartość jest wartością tylko określonego elementu zamiast dokładnego wartość, która zawiera wartości wszystkich elementów podrzędnych połączone w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="3a4e2-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="3a4e2-105">Podczas pobierania wartości elementu przy użyciu albo rzutowanie lub <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości, można pobrać wartości bezpośrednich.</span><span class="sxs-lookup"><span data-stu-id="3a4e2-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="3a4e2-106">Aby pobrać pobieżną wartości, można użyć `ShallowValue` — metoda rozszerzenia, jak pokazano w przykładzie Oto.</span><span class="sxs-lookup"><span data-stu-id="3a4e2-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="3a4e2-107">Pobieranie pobieżną wartości jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="3a4e2-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="3a4e2-108">Poniższy przykład deklaruje metodę rozszerzenia, która pobiera skrócona wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="3a4e2-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="3a4e2-109">Następnie używa metody rozszerzenia w zapytaniu Aby wyświetlić listę wszystkich elementów, które zawierają obliczonej wartości.</span><span class="sxs-lookup"><span data-stu-id="3a4e2-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3a4e2-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="3a4e2-110">Example</span></span>  
 <span data-ttu-id="3a4e2-111">Następujący plik tekstowy, Report.xml, jest źródła w ramach tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="3a4e2-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="3a4e2-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="3a4e2-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="3a4e2-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3a4e2-113">See Also</span></span>  
 [<span data-ttu-id="3a4e2-114">LINQ do osi XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="3a4e2-114">LINQ to XML Axes (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/linq-to-xml-axes.md)
