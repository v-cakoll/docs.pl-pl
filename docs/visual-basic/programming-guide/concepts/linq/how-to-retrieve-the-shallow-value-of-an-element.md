---
title: 'Instrukcje: pobieranie płytkiej wartości elementu'
ms.date: 07/20/2015
ms.assetid: 730a6670-fb8c-41fc-8a1b-eb97a837e432
ms.openlocfilehash: 24e6b128481f56941f0a61da9766f02813a46e97
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397820"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-visual-basic"></a><span data-ttu-id="05dd9-102">Instrukcje: pobieranie płytki wartości elementu (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05dd9-102">How to: Retrieve the Shallow Value of an Element (Visual Basic)</span></span>

<span data-ttu-id="05dd9-103">W tym temacie pokazano, jak uzyskać skróconą wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="05dd9-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="05dd9-104">Wartość płytki to wartość tylko określonego elementu, a nie wartość Szczegółowa, która obejmuje wartości wszystkich elementów potomnych połączonych w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="05dd9-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>

<span data-ttu-id="05dd9-105">Po pobraniu wartości elementu przy użyciu funkcji rzutowania lub <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości, pobierana jest wartość Szczegółowa.</span><span class="sxs-lookup"><span data-stu-id="05dd9-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="05dd9-106">Aby pobrać wartość płytki, można użyć `ShallowValue` metody rozszerzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="05dd9-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="05dd9-107">Pobieranie skróconej wartości jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="05dd9-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>

<span data-ttu-id="05dd9-108">Poniższy przykład deklaruje metodę rozszerzenia, która pobiera płytki wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="05dd9-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="05dd9-109">Następnie używa metody rozszerzającej w zapytaniu, aby wyświetlić listę wszystkich elementów, które zawierają obliczoną wartość.</span><span class="sxs-lookup"><span data-stu-id="05dd9-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>

## <a name="example"></a><span data-ttu-id="05dd9-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="05dd9-110">Example</span></span>

<span data-ttu-id="05dd9-111">Następujący plik tekstowy, Report. XML, jest źródłem dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="05dd9-111">The following text file, Report.xml, is the source for this example.</span></span>

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

<span data-ttu-id="05dd9-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="05dd9-112">This example produces the following output:</span></span>

```console
Column  Name="CustomerId"   =Customer.CustomerId.Heading
Column  Name="Name"         =Customer.Name.Heading
Column  Name="CustomerId"   =Customer.CustomerId
Column  Name="Name"         =Customer.Name
```

## <a name="see-also"></a><span data-ttu-id="05dd9-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="05dd9-113">See also</span></span>

- [<span data-ttu-id="05dd9-114">Osie LINQ to XML (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="05dd9-114">LINQ to XML Axes (Visual Basic)</span></span>](linq-to-xml-axes.md)
