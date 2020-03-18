---
title: Jak pobrać wartość płytkie elementu (C#)
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: b9b69b5a18106f82d13cb54208c2362f8239711e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75347447"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="91e57-102">Jak pobrać wartość płytkie elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="91e57-102">How to retrieve the shallow value of an element (C#)</span></span>
<span data-ttu-id="91e57-103">W tym temacie pokazano, jak uzyskać wartość płytkie elementu.</span><span class="sxs-lookup"><span data-stu-id="91e57-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="91e57-104">Wartość płytka jest wartością tylko określonego elementu, w przeciwieństwie do wartości głębokiej, która zawiera wartości wszystkich elementów potomka połączonych w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="91e57-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="91e57-105">Podczas pobierania wartości elementu przy użyciu <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> rzutowania lub właściwości, można pobrać wartość głęboką.</span><span class="sxs-lookup"><span data-stu-id="91e57-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="91e57-106">Aby pobrać wartość płytkie, `ShallowValue` można użyć metody rozszerzenia, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="91e57-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the following example.</span></span> <span data-ttu-id="91e57-107">Pobieranie wartości płytkiej jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="91e57-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="91e57-108">W poniższym przykładzie deklaruje metodę rozszerzenia, która pobiera wartość płytkie elementu.</span><span class="sxs-lookup"><span data-stu-id="91e57-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="91e57-109">Następnie używa metody rozszerzenia w kwerendzie, aby wyświetlić listę wszystkich elementów, które zawierają wartość obliczeniową.</span><span class="sxs-lookup"><span data-stu-id="91e57-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="91e57-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="91e57-110">Example</span></span>  
 <span data-ttu-id="91e57-111">Poniższy plik tekstowy Report.xml jest źródłem tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="91e57-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="91e57-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="91e57-112">This example produces the following output:</span></span>  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="91e57-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="91e57-113">See also</span></span>

- [<span data-ttu-id="91e57-114">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="91e57-114">LINQ to XML Axes (C#)</span></span>](./linq-to-xml-axes-overview.md)
