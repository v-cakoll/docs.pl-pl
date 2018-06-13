---
title: 'Porady: pobieranie skrócona wartość elementu (C#)'
ms.date: 07/20/2015
ms.assetid: 924a2699-72f6-4be1-aaa6-de62f8ec73b9
ms.openlocfilehash: 47c7cdd118a14070ea3a005bda88b55cc7075185
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325945"
---
# <a name="how-to-retrieve-the-shallow-value-of-an-element-c"></a>Porady: pobieranie skrócona wartość elementu (C#)
W tym temacie pokazano, jak pobrać pobieżną wartości elementu. Skrócona wartość jest wartością tylko określonego elementu zamiast dokładnego wartość, która zawiera wartości wszystkich elementów podrzędnych połączone w jeden ciąg.  
  
 Podczas pobierania wartości elementu przy użyciu albo rzutowanie lub <xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType> właściwości, można pobrać wartości bezpośrednich. Aby pobrać pobieżną wartości, można użyć `ShallowValue` — metoda rozszerzenia, jak pokazano w przykładzie Oto. Pobieranie pobieżną wartości jest przydatne, gdy chcesz wybrać elementy na podstawie ich zawartości.  
  
 Poniższy przykład deklaruje metodę rozszerzenia, która pobiera skrócona wartość elementu. Następnie używa metody rozszerzenia w zapytaniu Aby wyświetlić listę wszystkich elementów, które zawierają obliczonej wartości.  
  
## <a name="example"></a>Przykład  
 Następujący plik tekstowy, Report.xml, jest źródła w ramach tego przykładu.  
  
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
  
```  
Column  Name="CustomerId"   =Customer.CustomerId.Heading  
Column  Name="Name"         =Customer.Name.Heading  
Column  Name="CustomerId"   =Customer.CustomerId  
Column  Name="Name"         =Customer.Name  
```  
  
## <a name="see-also"></a>Zobacz też  
 [LINQ do osi XML (C#)](../../../../csharp/programming-guide/concepts/linq/linq-to-xml-axes.md)
