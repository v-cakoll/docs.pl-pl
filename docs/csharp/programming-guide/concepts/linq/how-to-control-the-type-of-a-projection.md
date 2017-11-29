---
title: 'Porady: kontrolowanie typu projekcji (C#)'
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-csharp
ms.topic: article
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
caps.latest.revision: "3"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 9b7b5b39ca308449b09023bc21446859a728e738
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-control-the-type-of-a-projection-c"></a>Porady: kontrolowanie typu projekcji (C#)
Projekcja to proces biorąc jeden zestaw danych, filtrowania jej zmiana jego kształtu i nawet zmianę jej typu. Wyrażenia zapytań większości wykonać projekcje. Wynikiem obliczania większość wyrażenia zapytań w tej sekcji <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, można jednak sterować typ projekcji, aby utworzyć kolekcje innych typów. W tym temacie pokazano, jak to zrobić.  
  
## <a name="example"></a>Przykład  
 W poniższym przykładzie zdefiniowano nowy typ `Customer`. Wyrażenia zapytania następnie tworzy nowy `Customer` obiekty w `Select` klauzuli. Powoduje to, że typ tego wyrażenia zapytania <xref:System.Collections.Generic.IEnumerable%601> z `Customer`.  
  
 W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).  
  
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
        return String.Format("{0}:{1}:{2}", this.customerID, this.companyName, this.contactName);  
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
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Linq.Enumerable.Select%2A>  
 [Projekcje i przekształcenia (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
