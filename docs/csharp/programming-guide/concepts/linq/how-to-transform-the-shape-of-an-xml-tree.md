---
title: 'Porady: Przekształcanie kształtu drzewo XML (C#)'
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 2c1f5728781a89caa813c2e3cbd822ae711a77e4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="0a956-102">Porady: Przekształcanie kształtu drzewo XML (C#)</span><span class="sxs-lookup"><span data-stu-id="0a956-102">How to: Transform the Shape of an XML Tree (C#)</span></span>
<span data-ttu-id="0a956-103">*Kształtu* XML dokumentu odwołuje się do nazwy elementu, nazw atrybutów i cechy jej hierarchii.</span><span class="sxs-lookup"><span data-stu-id="0a956-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="0a956-104">Czasami trzeba będzie zmienić kształt dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0a956-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="0a956-105">Może być konieczne na przykład wysłać istniejący dokument XML do innego systemu, który wymaga innego elementu i nazwach atrybutów.</span><span class="sxs-lookup"><span data-stu-id="0a956-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="0a956-106">W dokumencie, można przejść, usuwanie i zmiana nazwy elementów jako wymagana, ale przy użyciu konstrukcji funkcjonalności wyniki w bardziej czytelnym i łatwy w obsłudze kodu.</span><span class="sxs-lookup"><span data-stu-id="0a956-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="0a956-107">Aby uzyskać więcej informacji na temat konstrukcji funkcjonalności, zobacz [funkcjonalności konstrukcji (LINQ do XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="0a956-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="0a956-108">Pierwszym przykładzie zmienia organizacji dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="0a956-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="0a956-109">Powoduje przeniesienie złożonych elementów z jednej lokalizacji w drzewie do innego.</span><span class="sxs-lookup"><span data-stu-id="0a956-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="0a956-110">Drugi przykład w tym temacie tworzy dokument XML z kształtem innego niż dokumentu źródłowego.</span><span class="sxs-lookup"><span data-stu-id="0a956-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="0a956-111">Go zmiany wielkości liter nazwy elementów, zmienia nazwę niektóre elementy i pozostawia niektóre elementy z drzewa źródła poza przekształcone drzewa.</span><span class="sxs-lookup"><span data-stu-id="0a956-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a956-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a956-112">Example</span></span>  
 <span data-ttu-id="0a956-113">Poniższy kod zmienia kształt plik XML przy użyciu wyrażenia osadzonego zapytania.</span><span class="sxs-lookup"><span data-stu-id="0a956-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="0a956-114">Dokument XML źródła, w tym przykładzie zawiera `Customers` elementu w obszarze `Root` element, który zawiera wszystkich klientów.</span><span class="sxs-lookup"><span data-stu-id="0a956-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="0a956-115">Zawiera także `Orders` elementu w obszarze `Root` element, który zawiera wszystkie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="0a956-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="0a956-116">Nowe drzewo XML, w którym zamówień dla każdego klienta są zawarte w tym przykładzie jest tworzony `Orders` w elemencie `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="0a956-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="0a956-117">Zawiera także oryginalnego dokumentu `CustomerID` element `Order` elementu; spowoduje to element można usunąć z ponownie kształcie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="0a956-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="0a956-118">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: Klienci i zamówienia (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="0a956-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
```csharp  
XElement co = XElement.Load("CustomersOrders.xml");  
XElement newCustOrd =  
    new XElement("Root",  
        from cust in co.Element("Customers").Elements("Customer")  
        select new XElement("Customer",  
            cust.Attributes(),  
            cust.Elements(),  
            new XElement("Orders",  
                from ord in co.Element("Orders").Elements("Order")  
                where (string)ord.Element("CustomerID") == (string)cust.Attribute("CustomerID")  
                select new XElement("Order",  
                    ord.Attributes(),  
                    ord.Element("EmployeeID"),  
                    ord.Element("OrderDate"),  
                    ord.Element("RequiredDate"),  
                    ord.Element("ShipInfo")  
                )  
            )  
        )  
    );  
Console.WriteLine(newCustOrd);  
```  
  
 <span data-ttu-id="0a956-119">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0a956-119">This code produces the following output:</span></span>  
  
```xml  
<Root>  
  <Customer CustomerID="GREAL">  
    <CompanyName>Great Lakes Food Market</CompanyName>  
    <ContactName>Howard Snyder</ContactName>  
    <ContactTitle>Marketing Manager</ContactTitle>  
    <Phone>(503) 555-7555</Phone>  
    <FullAddress>  
      <Address>2732 Baker Blvd.</Address>  
      <City>Eugene</City>  
      <Region>OR</Region>  
      <PostalCode>97403</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  <Customer CustomerID="HUNGC">  
    <CompanyName>Hungry Coyote Import Store</CompanyName>  
    <ContactName>Yoshi Latimer</ContactName>  
    <ContactTitle>Sales Representative</ContactTitle>  
    <Phone>(503) 555-6874</Phone>  
    <Fax>(503) 555-2376</Fax>  
    <FullAddress>  
      <Address>City Center Plaza 516 Main St.</Address>  
      <City>Elgin</City>  
      <Region>OR</Region>  
      <PostalCode>97827</PostalCode>  
      <Country>USA</Country>  
    </FullAddress>  
    <Orders />  
  </Customer>  
  . . .  
```  
  
## <a name="example"></a><span data-ttu-id="0a956-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="0a956-120">Example</span></span>  
 <span data-ttu-id="0a956-121">W tym przykładzie zmienia nazwę niektóre elementy i konwertuje niektóre atrybuty elementów.</span><span class="sxs-lookup"><span data-stu-id="0a956-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="0a956-122">Kod wywołuje `ConvertAddress`, które zwraca listę <xref:System.Xml.Linq.XElement> obiektów.</span><span class="sxs-lookup"><span data-stu-id="0a956-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="0a956-123">Argument do metody jest kwerendę, która określa `Address` złożonego elementu gdzie `Type` atrybut ma wartość `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="0a956-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="0a956-124">W tym przykładzie użyto następujących dokumentu XML: [przykładowego pliku XML: typowe zamówienia zakupu (LINQ do XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="0a956-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](../../../../csharp/programming-guide/concepts/linq/sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
```csharp  
static IEnumerable<XElement> ConvertAddress(XElement add)  
{  
    List<XElement> fragment = new List<XElement>() {  
        new XElement("NAME", (string)add.Element("Name")),  
        new XElement("STREET", (string)add.Element("Street")),  
        new XElement("CITY", (string)add.Element("City")),  
        new XElement("ST", (string)add.Element("State")),  
        new XElement("POSTALCODE", (string)add.Element("Zip")),  
        new XElement("COUNTRY", (string)add.Element("Country"))  
    };  
    return fragment;  
}  
  
static void Main(string[] args)  
{  
    XElement po = XElement.Load("PurchaseOrder.xml");  
    XElement newPo = new XElement("PO",  
        new XElement("ID", (string)po.Attribute("PurchaseOrderNumber")),  
        new XElement("DATE", (DateTime)po.Attribute("OrderDate")),  
        ConvertAddress(  
            (from el in po.Elements("Address")  
            where (string)el.Attribute("Type") == "Shipping"  
            select el)  
            .First()  
        )  
    );  
    Console.WriteLine(newPo);  
}  
```  
  
 <span data-ttu-id="0a956-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="0a956-125">This code produces the following output:</span></span>  
  
```xml  
<PO>  
  <ID>99503</ID>  
  <DATE>1999-10-20T00:00:00</DATE>  
  <NAME>Ellen Adams</NAME>  
  <STREET>123 Maple Street</STREET>  
  <CITY>Mill Valley</CITY>  
  <ST>CA</ST>  
  <POSTALCODE>10999</POSTALCODE>  
  <COUNTRY>USA</COUNTRY>  
</PO>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a956-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0a956-126">See Also</span></span>  
 [<span data-ttu-id="0a956-127">Projekcje i przekształcenia (LINQ do XML) (C#)</span><span class="sxs-lookup"><span data-stu-id="0a956-127">Projections and Transformations (LINQ to XML) (C#)</span></span>](../../../../csharp/programming-guide/concepts/linq/projections-and-transformations-linq-to-xml.md)
