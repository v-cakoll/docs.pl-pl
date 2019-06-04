---
title: 'Instrukcje: Kontrolowanie typu projekcji (C#)'
ms.date: 07/20/2015
ms.assetid: e4db6b7e-4cc9-4c8f-af85-94acf32aa348
ms.openlocfilehash: 45f60934d6dcac5d2c0fa46409a773d8cdc8b6a2
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66487438"
---
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="65294-102">Instrukcje: Kontrolowanie typu projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="65294-102">How to: Control the Type of a Projection (C#)</span></span>
<span data-ttu-id="65294-103">Projekcja polega na wykonanie jeden zestaw danych, jego filtrowania, zmiana jego kształtu i nawet zmianę jego typu.</span><span class="sxs-lookup"><span data-stu-id="65294-103">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="65294-104">Wyrażenia zapytań większości przeprowadzić projekcji.</span><span class="sxs-lookup"><span data-stu-id="65294-104">Most query expressions perform projections.</span></span> <span data-ttu-id="65294-105">Większość wyrażeń zapytania, przedstawione w tej sekcji zwrócić <xref:System.Collections.Generic.IEnumerable%601> z <xref:System.Xml.Linq.XElement>, można jednak sterować typ projekcji tworzyć kolekcje innych typów.</span><span class="sxs-lookup"><span data-stu-id="65294-105">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="65294-106">W tym temacie pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="65294-106">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="65294-107">Przykład</span><span class="sxs-lookup"><span data-stu-id="65294-107">Example</span></span>  
 <span data-ttu-id="65294-108">W poniższym przykładzie zdefiniowano nowy typ `Customer`.</span><span class="sxs-lookup"><span data-stu-id="65294-108">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="65294-109">Następnie wyrażenie zapytania tworzy nowe wystąpienie `Customer` obiekty w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="65294-109">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="65294-110">Powoduje to, że typ wyrażenia zapytania jako <xref:System.Collections.Generic.IEnumerable%601> z `Customer`.</span><span class="sxs-lookup"><span data-stu-id="65294-110">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="65294-111">W tym przykładzie użyto następujący dokument XML: [Przykładowy plik XML: Klienci i zamówienia (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="65294-111">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="65294-112">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="65294-112">This code produces the following output:</span></span>  
  
```  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="65294-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="65294-113">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
