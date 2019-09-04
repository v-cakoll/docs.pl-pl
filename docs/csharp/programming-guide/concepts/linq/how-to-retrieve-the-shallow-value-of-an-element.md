---
title: 'Instrukcje: Pobieranie skróconej wartości elementu (C#)'
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 662c20cf2b17b9f93e00f0fd3c5cf925b5274de5
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2019
ms.locfileid: "70253369"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="9167a-102">Instrukcje: Pobieranie skróconej wartości elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="9167a-102">How to: Retrieve the Shallow Value of an Element (C#)</span></span>
<span data-ttu-id="9167a-103">W tym temacie pokazano, jak uzyskać skróconą wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="9167a-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="9167a-104">Wartość płytki to wartość tylko określonego elementu, a nie wartość Szczegółowa, która obejmuje wartości wszystkich elementów potomnych połączonych w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="9167a-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="9167a-105">Po pobraniu wartości elementu przy użyciu funkcji rzutowania lub <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości, pobierana jest wartość Szczegółowa.</span><span class="sxs-lookup"><span data-stu-id="9167a-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="9167a-106">Aby pobrać wartość płytki, można użyć `ShallowValue` metody rozszerzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="9167a-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="9167a-107">Pobieranie skróconej wartości jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="9167a-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="9167a-108">Poniższy przykład deklaruje metodę rozszerzenia, która pobiera płytki wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="9167a-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="9167a-109">Następnie używa metody rozszerzającej w zapytaniu, aby wyświetlić listę wszystkich elementów, które zawierają obliczoną wartość.</span><span class="sxs-lookup"><span data-stu-id="9167a-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9167a-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="9167a-110">Example</span></span>  
 <span data-ttu-id="9167a-111">Następujący plik tekstowy, Report. XML, jest źródłem dla tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="9167a-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
```csharp  
public static class MyExtensions  
{  
    public static string ShallowValue(this XElement xe)  
    {  
        return xe  
               .Nodes()  
               .OfType<XText>()  
               .Aggregate(new StringBuilder(),  
                          (s, c) => s.Append(c),  
                          s => s.ToString());  
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement root = XElement.Load("Report.xml");  
  
        IEnumerable<XElement> query = from el in root.Descendants()  
                                      where el.ShallowValue().StartsWith("=")  
                                      select el;  
  
        foreach (var q in query)  
        {  
            Console.WriteLine("{0}{1}{2}",  
                q.Name.ToString().PadRight(8),  
                q.Attribute("Name").ToString().PadRight(20),  
                q.ShallowValue());  
        }  
    }  
}  
```  
  
 <span data-ttu-id="9167a-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="9167a-112">This example produces the following output:</span></span>  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="9167a-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9167a-113">See also</span></span>

- [<span data-ttu-id="9167a-114">Osie LINQ to XML (C#)</span><span class="sxs-lookup"><span data-stu-id="9167a-114">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
