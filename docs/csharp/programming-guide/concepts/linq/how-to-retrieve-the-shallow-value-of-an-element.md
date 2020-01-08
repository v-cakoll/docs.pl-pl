---
title: Jak pobrać skróconą wartość elementu (C#)
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: b9b69b5a18106f82d13cb54208c2362f8239711e
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347447"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Jak pobrać skróconą wartość elementu (C#)
W tym temacie pokazano, jak uzyskać skróconą wartość elementu. Wartość płytki to wartość tylko określonego elementu, a nie wartość Szczegółowa, która obejmuje wartości wszystkich elementów potomnych połączonych w jeden ciąg.  
  
 Po pobraniu wartości elementu przy użyciu funkcji rzutowania lub właściwości <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> pobierana jest wartość Szczegółowa. Aby pobrać skróconą wartość, można użyć metody rozszerzenia `ShallowValue`, jak pokazano w poniższym przykładzie. Pobieranie skróconej wartości jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.  
  
 Poniższy przykład deklaruje metodę rozszerzenia, która pobiera płytki wartość elementu. Następnie używa metody rozszerzającej w zapytaniu, aby wyświetlić listę wszystkich elementów, które zawierają obliczoną wartość.  
  
## <a name="example"></a>Przykład  
 Następujący plik tekstowy, Report. XML, jest źródłem dla tego przykładu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Osie LINQ to XML (C#)](./linq-to-xml-axes-overview.md)
