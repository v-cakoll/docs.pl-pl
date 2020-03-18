---
title: Jak kontrolować typ projekcji (C#)
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: cb7c272fbe67c0700b5740691befc483993f4e29
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "74141352"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Jak kontrolować typ projekcji (C#)
Projekcja to proces przyjmowania jednego zestawu danych, filtrowania go, zmiany jego kształtu, a nawet zmiany jego typu. Większość wyrażeń zapytań wykonuje projekcje. Większość wyrażeń kwerendy przedstawionych <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>w tej sekcji ocenia , ale można kontrolować typ projekcji, aby utworzyć kolekcje innych typów. W tym temacie pokazano, jak to zrobić.  
  
## <a name="example"></a>Przykład  
 Poniższy przykład definiuje nowy typ `Customer`. Wyrażenie kwerendy następnie tworzy `Customer` nowe obiekty `Select` w klauzuli. Powoduje to, że typ wyrażenia <xref:System.Collections.Generic.IEnumerable%601> `Customer`kwerendy ma być .  
  
 W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ do XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)  
  
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
  
 Ten kod generuje następujące dane wyjściowe:  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Linq.Enumerable.Select%2A>
