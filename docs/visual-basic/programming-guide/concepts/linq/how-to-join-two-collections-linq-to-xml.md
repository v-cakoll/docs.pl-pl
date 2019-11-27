---
title: 'Instrukcje: dołączanie dwóch kolekcji (LINQ to XML)'
ms.date: 07/20/2015
ms.assetid: 5a5758d4-906b-4285-908d-5b930db192e6
ms.openlocfilehash: 404a43f52fce141b515da389090c81c57186f2e2
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344533"
---
# <a name="how-to-join-two-collections-linq-to-xml-visual-basic"></a><span data-ttu-id="b77c6-102">Instrukcje: sprzęganie dwóch kolekcji (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b77c6-102">How to: Join Two Collections (LINQ to XML) (Visual Basic)</span></span>
<span data-ttu-id="b77c6-103">Element lub atrybut w dokumencie XML czasami może odwoływać się do innego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="b77c6-103">An element or attribute in an XML document can sometimes refer to another element or attribute.</span></span> <span data-ttu-id="b77c6-104">[Przykładowy plik XML: Customers i Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) dokument XML zawiera listę klientów i listę zamówień.</span><span class="sxs-lookup"><span data-stu-id="b77c6-104">For example, the [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md) XML document contains a list of customers and a list of orders.</span></span> <span data-ttu-id="b77c6-105">Każdy element `Customer` zawiera atrybut `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="b77c6-105">Each `Customer` element contains a `CustomerID` attribute.</span></span> <span data-ttu-id="b77c6-106">Każdy element `Order` zawiera `CustomerID` elementu.</span><span class="sxs-lookup"><span data-stu-id="b77c6-106">Each `Order` element contains a `CustomerID` element.</span></span> <span data-ttu-id="b77c6-107">Element `CustomerID` w każdej kolejności odwołuje się do atrybutu `CustomerID` w kliencie.</span><span class="sxs-lookup"><span data-stu-id="b77c6-107">The `CustomerID` element in each order refers to the `CustomerID` attribute in a customer.</span></span>  
  
 <span data-ttu-id="b77c6-108">[Przykładowy plik XSD tematu: klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) zawierają XSD, których można użyć do zweryfikowania tego dokumentu.</span><span class="sxs-lookup"><span data-stu-id="b77c6-108">The topic [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md) contains an XSD that can be used to validate this document.</span></span> <span data-ttu-id="b77c6-109">Używa `xs:key` i `xs:keyref` funkcji XSD, aby określić, że atrybut `CustomerID` elementu `Customer` jest kluczem i aby ustanowić relację między `CustomerID` elementu w każdym `Order` elementu i atrybut `CustomerID` w każdym `Customer` elementu.</span><span class="sxs-lookup"><span data-stu-id="b77c6-109">It uses the `xs:key` and `xs:keyref` features of XSD to establish that the `CustomerID` attribute of the `Customer` element is a key, and to establish a relationship between the `CustomerID` element in each `Order` element and the `CustomerID` attribute in each `Customer` element.</span></span>  
  
 <span data-ttu-id="b77c6-110">Za pomocą [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)]można wykorzystać tę relację przy użyciu klauzuli `Join`.</span><span class="sxs-lookup"><span data-stu-id="b77c6-110">With [!INCLUDE[sqltecxlinq](~/includes/sqltecxlinq-md.md)], you can take advantage of this relationship by using the `Join` clause.</span></span>  
  
 <span data-ttu-id="b77c6-111">Należy pamiętać, że ponieważ nie ma dostępnego indeksu, takie dołączenie będzie miało niską wydajność środowiska uruchomieniowego.</span><span class="sxs-lookup"><span data-stu-id="b77c6-111">Note that because there is no index available, such joining will have poor runtime performance.</span></span>  
  
 <span data-ttu-id="b77c6-112">Aby uzyskać szczegółowe informacje na temat `Join`, zobacz [operacje join (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span><span class="sxs-lookup"><span data-stu-id="b77c6-112">For more detailed information about `Join`, see [Join Operations (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/join-operations.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="b77c6-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="b77c6-113">Example</span></span>  
 <span data-ttu-id="b77c6-114">Poniższy przykład sprzęga elementy `Customer` do elementów `Order` i generuje nowy dokument XML zawierający element `CompanyName` w zamówieniach.</span><span class="sxs-lookup"><span data-stu-id="b77c6-114">The following example joins the `Customer` elements to the `Order` elements, and generates a new XML document that includes the `CompanyName` element in the orders.</span></span>  
  
 <span data-ttu-id="b77c6-115">Przed wykonaniem zapytania, przykład sprawdza, czy dokument jest zgodny ze schematem w [przykładowym pliku XSD: klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="b77c6-115">Before executing the query, the example validates that the document complies with the schema in [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span> <span data-ttu-id="b77c6-116">Dzięki temu Klauzula join zawsze będzie działała.</span><span class="sxs-lookup"><span data-stu-id="b77c6-116">This ensures that the join clause will always work.</span></span>  
  
 <span data-ttu-id="b77c6-117">To zapytanie najpierw pobiera wszystkie elementy `Customer`, a następnie łączy je z elementami `Order`.</span><span class="sxs-lookup"><span data-stu-id="b77c6-117">This query first retrieves all `Customer` elements, and then joins them to the `Order` elements.</span></span> <span data-ttu-id="b77c6-118">Wybiera tylko zamówienia dla klientów o `CustomerID` większej niż "K".</span><span class="sxs-lookup"><span data-stu-id="b77c6-118">It selects only the orders for customers with a `CustomerID` greater than "K".</span></span> <span data-ttu-id="b77c6-119">Następnie projektuje nowy element `Order` zawierający informacje o klientach w poszczególnych zamówieniach.</span><span class="sxs-lookup"><span data-stu-id="b77c6-119">It then projects a new `Order` element that contains the customer information within each order.</span></span>  
  
 <span data-ttu-id="b77c6-120">W tym przykładzie zastosowano następujący dokument XML: [przykładowy plik XML: Customers i Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span><span class="sxs-lookup"><span data-stu-id="b77c6-120">This example uses the following XML document: [Sample XML File: Customers and Orders (LINQ to XML)](../../../../visual-basic/programming-guide/concepts/linq/sample-xml-file-customers-and-orders-linq-to-xml.md).</span></span>  
  
 <span data-ttu-id="b77c6-121">W tym przykładzie zastosowano następujący schemat XSD: [przykładowy plik XSD: klienci i zamówienia](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span><span class="sxs-lookup"><span data-stu-id="b77c6-121">This example uses the following XSD schema: [Sample XSD File: Customers and Orders](../../../../visual-basic/programming-guide/concepts/linq/sample-xsd-file-customers-and-orders.md).</span></span>  
  
 <span data-ttu-id="b77c6-122">Należy pamiętać, że sprzężenie w ten sposób nie będzie działać prawidłowo.</span><span class="sxs-lookup"><span data-stu-id="b77c6-122">Note that joining in this fashion will not perform very well.</span></span> <span data-ttu-id="b77c6-123">Sprzężenia są wykonywane za pośrednictwem wyszukiwania liniowego.</span><span class="sxs-lookup"><span data-stu-id="b77c6-123">Joins are performed via a linear search.</span></span> <span data-ttu-id="b77c6-124">Brak tabel lub indeksów skrótów, które mogą pomóc w wydajności.</span><span class="sxs-lookup"><span data-stu-id="b77c6-124">There are no hash tables or indexes to help with performance.</span></span>  
  
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
  
 <span data-ttu-id="b77c6-125">Ten kod generuje następujące dane wyjściowe:</span><span class="sxs-lookup"><span data-stu-id="b77c6-125">This code produces the following output:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="b77c6-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="b77c6-126">See also</span></span>

- [<span data-ttu-id="b77c6-127">Zaawansowane techniki zapytań (LINQ to XML) (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b77c6-127">Advanced Query Techniques (LINQ to XML) (Visual Basic)</span></span>](../../../../visual-basic/programming-guide/concepts/linq/advanced-query-techniques-linq-to-xml.md)
