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
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="1ccc0-102">Jak kontrolować typ projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="1ccc0-102">How to control the type of a projection (C#)</span></span>
<span data-ttu-id="1ccc0-103">Projekcja to proces przyjmowania jednego zestawu danych, filtrowania go, zmiany jego kształtu, a nawet zmiany jego typu.</span><span class="sxs-lookup"><span data-stu-id="1ccc0-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="1ccc0-104">Większość wyrażeń zapytań wykonuje projekcje.</span><span class="sxs-lookup"><span data-stu-id="1ccc0-104">Most query expressions perform projections.</span></span> <span data-ttu-id="1ccc0-105">Większość wyrażeń kwerendy przedstawionych <xref:System.Collections.Generic.IEnumerable%601> <xref:System.Xml.Linq.XElement>w tej sekcji ocenia , ale można kontrolować typ projekcji, aby utworzyć kolekcje innych typów.</span><span class="sxs-lookup"><span data-stu-id="1ccc0-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="1ccc0-106">W tym temacie pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="1ccc0-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ccc0-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="1ccc0-107">Example</span></span>  
 <span data-ttu-id="1ccc0-108">Poniższy przykład definiuje nowy typ `Customer`.</span><span class="sxs-lookup"><span data-stu-id="1ccc0-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="1ccc0-109">Wyrażenie kwerendy następnie tworzy `Customer` nowe obiekty `Select` w klauzuli.</span><span class="sxs-lookup"><span data-stu-id="1ccc0-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="1ccc0-110">Powoduje to, że typ wyrażenia <xref:System.Collections.Generic.IEnumerable%601> `Customer`kwerendy ma być .</span><span class="sxs-lookup"><span data-stu-id="1ccc0-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="1ccc0-111">W tym przykładzie użyto następującego dokumentu XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ do XML).](./sample-xml-file-customers-and-orders-linq-to-xml-2.md)</span><span class="sxs-lookup"><span data-stu-id="1ccc0-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="1ccc0-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="1ccc0-112">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ccc0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1ccc0-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
