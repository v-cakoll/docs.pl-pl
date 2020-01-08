---
title: Jak przekształcić kształt drzewa XML (C#)
ms.date: 07/20/2015
ms.assetid: 93c5d426-dea2-4709-a991-60204de42e8f
ms.openlocfilehash: 91f91ed6fea5371fae2ce67a413f4825f37af6c3
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/25/2019
ms.locfileid: "75347303"
---
# <a name="how-to-transform-the-shape-of-an-xml-tree-c"></a><span data-ttu-id="06c15-102">Jak przekształcić kształt drzewa XML (C#)</span><span class="sxs-lookup"><span data-stu-id="06c15-102">How to transform the shape of an XML tree (C#)</span></span>
<span data-ttu-id="06c15-103">*Kształt* dokumentu XML odwołuje się do jego nazw elementów, nazw atrybutów i cech hierarchii.</span><span class="sxs-lookup"><span data-stu-id="06c15-103">The *shape* of an XML document refers to its element names, attribute names, and the characteristics of its hierarchy.</span></span>  
  
 <span data-ttu-id="06c15-104">Czasami trzeba będzie zmienić kształt dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="06c15-104">Sometimes you will have to change the shape of an XML document.</span></span> <span data-ttu-id="06c15-105">Na przykład może być konieczne wysłanie istniejącego dokumentu XML do innego systemu, który wymaga innych nazw elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="06c15-105">For example, you might have to send an existing XML document to another system that requires different element and attribute names.</span></span> <span data-ttu-id="06c15-106">Możesz przejść przez dokument, usunąć i zmienić nazwy elementów zgodnie z potrzebami, ale użycie konstrukcji funkcjonalnej skutkuje bardziej czytelnym i możliwym do utrzymania kodem.</span><span class="sxs-lookup"><span data-stu-id="06c15-106">You could go through the document, deleting and renaming elements as required, but using functional construction results in more readable and maintainable code.</span></span> <span data-ttu-id="06c15-107">Aby uzyskać więcej informacji na temat konstrukcji funkcjonalnej, zobacz [konstrukcja funkcjonalnaC#(LINQ to XML) ()](./functional-construction-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="06c15-107">For more information about functional construction, see [Functional Construction (LINQ to XML) (C#)](./functional-construction-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="06c15-108">Pierwszy przykład zmienia organizację dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="06c15-108">The first example changes the organization of the XML document.</span></span> <span data-ttu-id="06c15-109">Przenosi elementy złożone z jednej lokalizacji w drzewie do innej.</span><span class="sxs-lookup"><span data-stu-id="06c15-109">It moves complex elements from one location in the tree to another.</span></span>  
  
 <span data-ttu-id="06c15-110">Drugi przykład w tym temacie tworzy dokument XML o innym kształcie niż dokument źródłowy.</span><span class="sxs-lookup"><span data-stu-id="06c15-110">The second example in this topic creates an XML document with a different shape than the source document.</span></span> <span data-ttu-id="06c15-111">Zmiany wielkości liter w nazwach elementów, zmiana nazwy niektórych elementów i pozostawienie niektórych elementów z drzewa źródłowego z przekształconego drzewa.</span><span class="sxs-lookup"><span data-stu-id="06c15-111">It changes the casing of the element names, renames some elements, and leaves some elements from the source tree out of the transformed tree.</span></span>  
  
## <a name="example"></a><span data-ttu-id="06c15-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="06c15-112">Example</span></span>  
 <span data-ttu-id="06c15-113">Poniższy kod zmienia kształt pliku XML przy użyciu osadzonych wyrażeń zapytań.</span><span class="sxs-lookup"><span data-stu-id="06c15-113">The following code changes the shape of an XML file using embedded query expressions.</span></span>  
  
 <span data-ttu-id="06c15-114">Źródłowy dokument XML w tym przykładzie zawiera element `Customers` w elemencie `Root`, który zawiera wszystkich klientów.</span><span class="sxs-lookup"><span data-stu-id="06c15-114">The source XML document in this example contains a `Customers` element under the `Root` element that contains all customers.</span></span> <span data-ttu-id="06c15-115">Zawiera również element `Orders` w elemencie `Root`, który zawiera wszystkie zamówienia.</span><span class="sxs-lookup"><span data-stu-id="06c15-115">It also contains an `Orders` element under the `Root` element that contains all orders.</span></span> <span data-ttu-id="06c15-116">Ten przykład tworzy nowe drzewo XML, w którym zamówienia dla każdego klienta znajdują się w `Orders` elementu w ramach elementu `Customer`.</span><span class="sxs-lookup"><span data-stu-id="06c15-116">This example creates a new XML tree in which the orders for each customer are contained in an `Orders` element within the `Customer` element.</span></span> <span data-ttu-id="06c15-117">Oryginalny dokument zawiera również element `CustomerID` w elemencie `Order`; Ten element zostanie usunięty z dokumentu, który można zmienić.</span><span class="sxs-lookup"><span data-stu-id="06c15-117">The original document also contains a `CustomerID` element in the `Order` element; this element will be removed from the re-shaped document.</span></span>  
  
 <span data-ttu-id="06c15-118">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span><span class="sxs-lookup"><span data-stu-id="06c15-118">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](./sample-xml-file-customers-and-orders-linq-to-xml-2.md).</span></span>  
  
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
  
 <span data-ttu-id="06c15-119">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="06c15-119">This code produces the following output:</span></span>  
  
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
  
## <a name="example"></a><span data-ttu-id="06c15-120">Przykład</span><span class="sxs-lookup"><span data-stu-id="06c15-120">Example</span></span>  
 <span data-ttu-id="06c15-121">Ten przykład zmienia nazwę niektórych elementów i konwertuje niektóre atrybuty do elementów.</span><span class="sxs-lookup"><span data-stu-id="06c15-121">This example renames some elements and converts some attributes to elements.</span></span>  
  
 <span data-ttu-id="06c15-122">Kod wywołuje `ConvertAddress`, który zwraca listę obiektów <xref:System.Xml.Linq.XElement>.</span><span class="sxs-lookup"><span data-stu-id="06c15-122">The code calls `ConvertAddress`, which returns a list of <xref:System.Xml.Linq.XElement> objects.</span></span> <span data-ttu-id="06c15-123">Argument metody jest zapytanie, które określa `Address` element złożony, gdzie atrybut `Type` ma wartość `"Shipping"`.</span><span class="sxs-lookup"><span data-stu-id="06c15-123">The argument to the method is a query that determines the `Address` complex element where the `Type` attribute has a value of `"Shipping"`.</span></span>  
  
 <span data-ttu-id="06c15-124">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: typowe zamówienie zakupu (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span><span class="sxs-lookup"><span data-stu-id="06c15-124">This example uses the following XML document: [Sample XML File: Typical Purchase Order (LINQ to XML)](./sample-xml-file-typical-purchase-order-linq-to-xml-1.md).</span></span>  
  
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
  
 <span data-ttu-id="06c15-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="06c15-125">This code produces the following output:</span></span>  
  
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
