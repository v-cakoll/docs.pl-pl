---
title: 'Instrukcje: łączenie dwóch kolekcji (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: dc3cfd19d990fa81e00f4781cb15bf07eb9a80ea
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398054"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="a726f-102">Instrukcje: sprzęganie dwóch kolekcji (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a726f-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="a726f-103">Element lub atrybut w dokumencie XML czasami może odwoływać się do innego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="a726f-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="a726f-104">[Przykładowy plik XML: Customers i Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) dokument XML zawiera listę klientów i listę zamówień.</span><span class="sxs-lookup"><span data-stu-id="a726f-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="a726f-105">Każdy `Customer` element zawiera `CustomerID` atrybut.</span><span class="sxs-lookup"><span data-stu-id="a726f-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="a726f-106">Każdy `Order` element zawiera `CustomerID` element.</span><span class="sxs-lookup"><span data-stu-id="a726f-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="a726f-107">`CustomerID`Element w każdym porządku odwołuje się do `CustomerID` atrybutu w kliencie.</span><span class="sxs-lookup"><span data-stu-id="a726f-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="a726f-108">[Przykładowy plik XSD tematu: klienci i zamówienia](sample-xsd-file-customers-and-orders.md) zawierają XSD, których można użyć do zweryfikowania tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="a726f-108">The topic [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="a726f-109">Używa `xs:key` i `xs:keyref` funkcji XSD, aby określić, że `CustomerID` atrybut `Customer` elementu jest kluczem i aby ustanowić relację między `CustomerID` elementem w każdym `Order` elemencie a `CustomerID` atrybutem w każdym `Customer` elemencie.</span><span class="sxs-lookup"><span data-stu-id="a726f-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="a726f-110">Za pomocą programu [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)] można korzystać z tej relacji przy użyciu `Join` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a726f-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="a726f-111">Należy pamiętać, że ponieważ nie ma dostępnego indeksu, takie dołączenie będzie miało niską wydajność środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="a726f-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="a726f-112">Aby uzyskać bardziej szczegółowe informacje na temat `Join` , zobacz [operacje Join (Visual Basic)](join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="a726f-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a726f-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a726f-113">Example</span></span>  
 <span data-ttu-id="a726f-114">Poniższy przykład sprzęga `Customer` elementy do `Order` elementów i generuje nowy dokument XML, który zawiera `CompanyName` element w zamówieniach.</span><span class="sxs-lookup"><span data-stu-id="a726f-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="a726f-115">Przed wykonaniem zapytania, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: klienci i zamówienia](sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="a726f-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="a726f-116">Dzięki temu Klauzula join zawsze będzie działała.</span><span class="sxs-lookup"><span data-stu-id="a726f-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="a726f-117">To zapytanie najpierw pobiera wszystkie `Customer` elementy, a następnie łączy je z `Order` elementami.</span><span class="sxs-lookup"><span data-stu-id="a726f-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="a726f-118">Wybiera tylko zamówienia dla klientów o `CustomerID` większej niż "K".</span><span class="sxs-lookup"><span data-stu-id="a726f-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="a726f-119">Następnie projektuje nowy `Order` element, który zawiera informacje o kliencie w ramach poszczególnych zamówień.</span><span class="sxs-lookup"><span data-stu-id="a726f-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="a726f-120">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="a726f-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="a726f-121">W tym przykładzie zastosowano następujący schemat XSD: [przykładowy plik XSD: klienci i zamówienia](sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="a726f-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="a726f-122">Należy pamiętać, że sprzężenie w ten sposób nie będzie działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="a726f-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="a726f-123">Sprzężenia są wykonywane za pośrednictwem wyszukiwania liniowego.</span><span class="sxs-lookup"><span data-stu-id="a726f-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="a726f-124">Brak tabel lub indeksów skrótów, które mogą pomóc w wydajności.</span><span class="sxs-lookup"><span data-stu-id="a726f-124">There are no hash tables or indexes to help with performance.</span></span>  
  
```vb  
Public Class Program  
    Public Shared errors As Boolean = False  
  
    Public Shared Function LamValidEvent(ByVal o As Object, _  
                 ByVal e As ValidationEventArgs) As Boolean  
        Console.WriteLine("{0}", e.Message)  
        errors = True  
    End Function  
  
    Shared Sub Main()  
        Dim schemas As New XmlSchemaSet()  
        schemas.Add("", "CustomersOrders.xsd")  
  
        Console.Write("Attempting to validate, ")  
        Dim custOrdDoc As XDocument = XDocument.Load("CustomersOrders.xml")  
  
        custOrdDoc.Validate(schemas, Function(o, e) LamValidEvent(0, e))  
        If errors Then  
            Console.WriteLine("custOrdDoc did not validate")  
        Else  
            Console.WriteLine("custOrdDoc validated")  
        End If  
  
        If Not errors Then  
            'Join customers and orders, and create a new XML document with  
            ' a different shape.  
            'The new document contains orders only for customers with a  
            ' CustomerID > 'K'.  
            Dim custOrd As XElement = custOrdDoc.<Root>.FirstOrDefault  
            Dim newCustOrd As XElement = _  
                <Root>  
                    <%= From c In custOrd.<Customers>.<Customer> _  
                        Join o In custOrd.<Orders>.<Order> _  
                        On c.@CustomerID Equals o.<CustomerID>.Value _  
                        Where c.@CustomerID.CompareTo("K") > 0 _  
                        Select _  
                        <Order>  
                            <CustomerID><%= c.@CustomerID %></CustomerID>  
                            <%= c.<CompanyName> %>  
                            <%= c.<ContactName> %>  
                            <%= o.<EmployeeID> %>  
                            <%= o.<OrderDate> %>  
                        </Order> _  
                    %>  
                </Root>  
            Console.WriteLine(newCustOrd)  
        End If  
    End Sub  
End Class  
```  
  
 <span data-ttu-id="a726f-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="a726f-125">This code produces the following output:</span></span>  
  
```console
Attempting to validate, custOrdDoc validated  
<Root>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-03-21T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LAZYK</CustomerID>  
    <CompanyName>Lazy K Kountry Store</CompanyName>  
    <ContactName>John Steel</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-05-22T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>1</EmployeeID>  
    <OrderDate>1997-06-25T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>8</EmployeeID>  
    <OrderDate>1997-10-27T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>6</EmployeeID>  
    <OrderDate>1997-11-10T00:00:00</OrderDate>  
  </Order>  
  <Order>  
    <CustomerID>LETSS</CustomerID>  
    <CompanyName>Let's Stop N Shop</CompanyName>  
    <ContactName>Jaime Yorres</ContactName>  
    <EmployeeID>4</EmployeeID>  
    <OrderDate>1998-02-12T00:00:00</OrderDate>  
  </Order>  
</Root>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a726f-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a726f-126">See also</span></span>

- [<span data-ttu-id="a726f-127">Zaawansowane techniki zapytań (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="a726f-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](advanced-query-techniques-linq-to-xml.md)
