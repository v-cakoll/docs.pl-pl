---
title: "Porady: pobieranie skrócona wartość elementu (C#)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 5dcbe3faa457a4880a85f5827d0e5c4808b6a44b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a><span data-ttu-id="54399-102">Porady: pobieranie skrócona wartość elementu (C#)</span><span class="sxs-lookup"><span data-stu-id="54399-102">How to: Retrieve the Shallow Value of an Element (C#)</span></span>
<span data-ttu-id="54399-103">W tym temacie pokazano, jak pobrać pobieżną wartości elementu.</span><span class="sxs-lookup"><span data-stu-id="54399-103">This topic shows how to get the shallow value of an element.</span></span> <span data-ttu-id="54399-104">Skrócona wartość jest wartością tylko określonego elementu zamiast dokładnego wartość, która zawiera wartości wszystkich elementów podrzędnych połączone w jeden ciąg.</span><span class="sxs-lookup"><span data-stu-id="54399-104">The shallow value is the value of the specific element only, as opposed to the deep value, which includes the values of all descendent elements concatenated into a single string.</span></span>  
  
 <span data-ttu-id="54399-105">Podczas pobierania wartości elementu przy użyciu albo rzutowanie lub <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości, można pobrać wartości bezpośrednich.</span><span class="sxs-lookup"><span data-stu-id="54399-105">When you retrieve an element value by using either casting or the <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> property, you retrieve the deep value.</span></span> <span data-ttu-id="54399-106">Aby pobrać pobieżną wartości, można użyć `ShallowValue` — metoda rozszerzenia, jak pokazano w przykładzie Oto.</span><span class="sxs-lookup"><span data-stu-id="54399-106">To retrieve the shallow value, you can use the `ShallowValue` extension method, as shown in the follwing example.</span></span> <span data-ttu-id="54399-107">Pobieranie pobieżną wartości jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.</span><span class="sxs-lookup"><span data-stu-id="54399-107">Retrieving the shallow value is useful when you want to select elements based on their content.</span></span>  
  
 <span data-ttu-id="54399-108">Poniższy przykład deklaruje metodę rozszerzenia, która pobiera skrócona wartość elementu.</span><span class="sxs-lookup"><span data-stu-id="54399-108">The following example declares an extension method that retrieves the shallow value of an element.</span></span> <span data-ttu-id="54399-109">Następnie używa metody rozszerzenia w zapytaniu Aby wyświetlić listę wszystkich elementów, które zawierają obliczonej wartości.</span><span class="sxs-lookup"><span data-stu-id="54399-109">It then uses the extension method in a query to list all elements that contain a calculated value.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54399-110">Przykład</span><span class="sxs-lookup"><span data-stu-id="54399-110">Example</span></span>  
 <span data-ttu-id="54399-111">Następujący plik tekstowy, Report.xml, jest źródła w ramach tego przykładu.</span><span class="sxs-lookup"><span data-stu-id="54399-111">The following text file, Report.xml, is the source for this example.</span></span>  
  
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
  
 <span data-ttu-id="54399-112">Ten przykład generuje następujące wyniki:</span><span class="sxs-lookup"><span data-stu-id="54399-112">This example produces the following output:</span></span>  
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a><span data-ttu-id="54399-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="54399-113">See Also</span></span>  
 [<span data-ttu-id="54399-114">LINQ do osi XML (C#)</span><span class="sxs-lookup"><span data-stu-id="54399-114">LINQ to XML Axes (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
