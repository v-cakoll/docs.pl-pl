---
title: Jak kontrolować typ projekcji (C#)
description: Dowiedz się, jak kontrolować typ projekcji w LINQ w języku C#, aby tworzyć Kolekcje typów innych niż IEnumerable <T> of XElement.
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 32b019b5e1574e7160b4dce5fb0322caa3c1ca71
ms.sourcegitcommit: 04022ca5d00b2074e1b1ffdbd76bec4950697c4c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2020
ms.locfileid: "87103348"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Jak kontrolować typ projekcji (C#)
Projekcja to proces przejmowania jednego zestawu danych, filtrowanie go, zmiana jego kształtu, a nawet zmiana jego typu. Większość wyrażeń zapytania wykonuje projekcje. Większość wyrażeń zapytania przedstawionych w tej sekcji szacuje się <xref:System.Collections.Generic.IEnumerable%601> na <xref:System.Xml.Linq.XElement> , ale można kontrolować typ projekcji, aby tworzyć Kolekcje innych typów. W tym temacie pokazano, jak to zrobić.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano nowy typ, `Customer` . Wyrażenie zapytania następnie tworzy wystąpienie nowych `Customer` obiektów w `Select` klauzuli. Powoduje to, że typ wyrażenia zapytania ma być <xref:System.Collections.Generic.IEnumerable%601> `Customer` .  
  
 W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
```csharp  
public class Customer  
{  
    private string customerID;  
    public string CustomerID{ get{return customerID;} set{customerID = value;}}  
  
    private string companyName;  
    public string CompanyName{ get{return companyName;} set{companyName = value;}}  
  
    private string contactName;  
    public string ContactName { get{return contactName;} set{contactName = value;}}  
  
    public Customer(string customerID, string companyName, string contactName)  
    {  
        CustomerID = customerID;  
        CompanyName = companyName;  
        ContactName = contactName;  
    }  
  
    public override string ToString()  
    {  
        return $"{this.customerID}:{this.companyName}:{this.contactName}";
    }  
}  
  
class Program  
{  
    static void Main(string[] args)  
    {  
        XElement custOrd = XElement.Load("CustomersOrders.xml");  
        IEnumerable<Customer> custList =  
            from el in custOrd.Element("Customers").Elements("Customer")  
            select new Customer(  
                (string)el.Attribute("CustomerID"),  
                (string)el.Element("CompanyName"),  
                (string)el.Element("ContactName")  
            );  
        foreach (Customer cust in custList)  
            Console.WriteLine(cust);  
    }  
}  
```  
  
 Ten kod spowoduje wygenerowanie następujących danych wyjściowych:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable.Select%2A>
