---
title: 'Porady: kontrolowanie typu projekcji (C#)'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 67ca04d9f3412def8d8c940c9ed932bf9da3287b
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2018
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="36833-102">Porady: kontrolowanie typu projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="36833-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="36833-103">Projekcja to proces biorąc jeden zestaw danych, filtrowania jej zmiana jego kształtu i nawet zmianę jej typu.</span><span class="sxs-lookup"><span data-stu-id="36833-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="36833-104">Wyrażenia zapytań większości wykonać projekcje.</span><span class="sxs-lookup"><span data-stu-id="36833-104">Most query expressions perform projections.</span></span> <span data-ttu-id="36833-105">Wynikiem obliczania większość wyrażenia zapytań w tej sekcji <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, można jednak sterować typ projekcji, aby utworzyć kolekcje innych typów.</span><span class="sxs-lookup"><span data-stu-id="36833-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="36833-106">W tym temacie pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="36833-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="36833-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="36833-107">Example</span></span>  
 <span data-ttu-id="36833-108">W poniższym przykładzie zdefiniowano nowy typ `Customer`.</span><span class="sxs-lookup"><span data-stu-id="36833-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="36833-109">Wyrażenia zapytania następnie tworzy nowy `Customer` obiekty w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="36833-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="36833-110">Powoduje to, że typ tego wyrażenia zapytania <xref:System.Collections.Generic.IEnumerable%601> z `Customer`.</span><span class="sxs-lookup"><span data-stu-id="36833-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="36833-111">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="36833-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="36833-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="36833-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="36833-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="36833-113">See Also</span></span>  
 <xref:System.Linq.Enumerable.Select%2A>  
 [<span data-ttu-id="36833-114">Projekcje i przekształcenia (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="36833-114">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
