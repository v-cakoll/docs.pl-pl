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
# <a name="how-to-control-the-type-of-a-projection-c"></a><span data-ttu-id="8e242-103">Jak kontrolować typ projekcji (C#)</span><span class="sxs-lookup"><span data-stu-id="8e242-103">How to control the type of a projection (C#)</span></span>
<span data-ttu-id="8e242-104">Projekcja to proces przejmowania jednego zestawu danych, filtrowanie go, zmiana jego kształtu, a nawet zmiana jego typu.</span><span class="sxs-lookup"><span data-stu-id="8e242-104">Projection is the process of taking one set of data, filtering it, changing its shape, and even changing its type.</span></span> <span data-ttu-id="8e242-105">Większość wyrażeń zapytania wykonuje projekcje.</span><span class="sxs-lookup"><span data-stu-id="8e242-105">Most query expressions perform projections.</span></span> <span data-ttu-id="8e242-106">Większość wyrażeń zapytania przedstawionych w tej sekcji szacuje się <xref:System.Collections.Generic.IEnumerable%601> na <xref:System.Xml.Linq.XElement> , ale można kontrolować typ projekcji, aby tworzyć Kolekcje innych typów.</span><span class="sxs-lookup"><span data-stu-id="8e242-106">Most of the query expressions shown in this section evaluate to <xref:System.Collections.Generic.IEnumerable%601> of <xref:System.Xml.Linq.XElement>, but you can control the type of the projection to create collections of other types.</span></span> <span data-ttu-id="8e242-107">W tym temacie pokazano, jak to zrobić.</span><span class="sxs-lookup"><span data-stu-id="8e242-107">This topic shows how to do this.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8e242-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="8e242-108">Example</span></span>  
 <span data-ttu-id="8e242-109">W poniższym przykładzie zdefiniowano nowy typ, `Customer` .</span><span class="sxs-lookup"><span data-stu-id="8e242-109">The following example defines a new type, `Customer`.</span></span> <span data-ttu-id="8e242-110">Wyrażenie zapytania następnie tworzy wystąpienie nowych `Customer` obiektów w `Select` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="8e242-110">The query expression then instantiates new `Customer` objects in the `Select` clause.</span></span> <span data-ttu-id="8e242-111">Powoduje to, że typ wyrażenia zapytania ma być <xref:System.Collections.Generic.IEnumerable%601> `Customer` .</span><span class="sxs-lookup"><span data-stu-id="8e242-111">This causes the type of the query expression to be <xref:System.Collections.Generic.IEnumerable%601> of `Customer`.</span></span>  
  
 <span data-ttu-id="8e242-112">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="8e242-112">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="8e242-113">Ten kod spowoduje wygenerowanie następujących danych wyjściowych:</span><span class="sxs-lookup"><span data-stu-id="8e242-113">This code produces the following output:</span></span>  
  
```output  
GREAL:Great Lakes Food Market:Howard Snyder  
HUNGC:Hungry Coyote Import Store:Yoshi Latimer  
LAZYK:Lazy K Kountry Store:John Steel  
LETSS:Let's Stop N Shop:Jaime Yorres  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e242-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="8e242-114">See also</span></span>

- <xref:System.Linq.Enumerable.Select%2A>
