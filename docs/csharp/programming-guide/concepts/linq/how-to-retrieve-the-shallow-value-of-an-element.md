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
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Jak pobrać wartość płytkie elementu (C#)
W tym temacie pokazano, jak uzyskać wartość płytkie elementu. Wartość płytka jest wartością tylko określonego elementu, w przeciwieństwie do wartości głębokiej, która zawiera wartości wszystkich elementów potomka połączonych w jeden ciąg.  
  
 Podczas pobierania wartości elementu przy użyciu <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> rzutowania lub właściwości, można pobrać wartość głęboką. Aby pobrać wartość płytkie, `ShallowValue` można użyć metody rozszerzenia, jak pokazano w poniższym przykładzie. Pobieranie wartości płytkiej jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.  
  
 W poniższym przykładzie deklaruje metodę rozszerzenia, która pobiera wartość płytkie elementu. Następnie używa metody rozszerzenia w kwerendzie, aby wyświetlić listę wszystkich elementów, które zawierają wartość obliczeniową.  
  
## <a name="example"></a>Przykład  
 Poniższy plik tekstowy Report.xml jest źródłem tego przykładu.  
  
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
  
 Ten przykład generuje następujące wyniki:  
  
```output  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Zobacz też

- [LINQ do osi XML (C#)](./linq-to-xml-axes-overview.md)
