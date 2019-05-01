---
title: 'Instrukcje: kwalifikowanie elementu XML i nazw atrybutów XML'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 04e9dd3c135c516fa5554b9b547306337fb6a668
ms.sourcegitcommit: 89fcad7e816c12eb1299128481183f01c73f2c07
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/24/2019
ms.locfileid: "63807817"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="cf14c-102">Instrukcje: kwalifikowanie elementu XML i nazw atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="cf14c-102">How to: Qualify XML Element and XML Attribute Names</span></span>

<span data-ttu-id="cf14c-103">Obszary nazw XML zawartych wystąpienia <xref:System.Xml.Serialization.XmlSerializerNamespaces> klasy musi być zgodna ze specyfikacją World Wide Web Consortium (W3C) o nazwie [przestrzeni nazw w kodzie XML](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="cf14c-103">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="cf14c-104">Obszary nazw XML umożliwiają uprawniających nazwy elementów XML i atrybutów XML w dokumentach XML.</span><span class="sxs-lookup"><span data-stu-id="cf14c-104">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="cf14c-105">Kwalifikowana nazwa składa się z prefiksu i lokalna nazwa, rozdzielone średnikiem.</span><span class="sxs-lookup"><span data-stu-id="cf14c-105">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="cf14c-106">Prefiks, który działa tylko jako symbolu zastępczego; jest mapowany do identyfikatora URI, który określa obszar nazw.</span><span class="sxs-lookup"><span data-stu-id="cf14c-106">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="cf14c-107">Kombinacja powszechnie zarządzanych nazw identyfikatora URI i lokalna nazwa tworzy nazwę, która może być unikatowym.</span><span class="sxs-lookup"><span data-stu-id="cf14c-107">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="cf14c-108">Utworzenie wystąpienia `XmlSerializerNamespaces` i Dodawanie obiektu pary nazw, można określić prefiksy używane w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="cf14c-108">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="cf14c-109">Aby utworzyć kwalifikowane nazwy w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="cf14c-109">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="cf14c-110">Utworzenie wystąpienia `XmlSerializerNamespaces` klasy.</span><span class="sxs-lookup"><span data-stu-id="cf14c-110">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="cf14c-111">Dodaj wszystkie prefiksy i pary nazw do `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="cf14c-111">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="cf14c-112">Zastosuj odpowiedni `System.Xml.Serialization` atrybut do każdej składowej lub klasy, które <xref:System.Xml.Serialization.XmlSerializer> ma serializować do dokumentu XML.</span><span class="sxs-lookup"><span data-stu-id="cf14c-112">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

    <span data-ttu-id="cf14c-113">Dostępne są następujące atrybuty: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, i <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="cf14c-113">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="cf14c-114">Ustaw `Namespace` właściwości każdego atrybutu do jednej z tych wartości nazw z `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="cf14c-114">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="cf14c-115">Przekaż `XmlSerializerNamespaces` do `Serialize` metody `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="cf14c-115">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="cf14c-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="cf14c-116">Example</span></span>

<span data-ttu-id="cf14c-117">Poniższy przykład tworzy `XmlSerializerNamespaces`, i dodaje dwie pary prefiksu i obszaru nazw do obiektu.</span><span class="sxs-lookup"><span data-stu-id="cf14c-117">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="cf14c-118">Tworzy kod `XmlSerializer` używany do serializacji wystąpienia `Books` klasy.</span><span class="sxs-lookup"><span data-stu-id="cf14c-118">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="cf14c-119">Wywołania kodu `Serialize` metody z `XmlSerializerNamespaces`, umożliwiając XML zawiera prefiksem obszary nazw.</span><span class="sxs-lookup"><span data-stu-id="cf14c-119">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

```vb
Option Explicit
public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}

Option Strict

Imports System
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Class Run

    Public Shared Sub Main()
        Dim test As New Run()
        test.SerializeObject("XmlNamespaces.xml")
    End Sub 'Main

    Public Sub SerializeObject(filename As String)
        Dim mySerializer As New XmlSerializer(GetType(Books))
        ' Writing a file requires a TextWriter.
        Dim myWriter As New StreamWriter(filename)

        ' Creates an XmlSerializerNamespaces and adds two
        ' prefix-namespace pairs.
        Dim myNamespaces As New XmlSerializerNamespaces()
        myNamespaces.Add("books", "http://www.cpandl.com")
        myNamespaces.Add("money", "http://www.cohowinery.com")

        ' Creates a Book.
        Dim myBook As New Book()
        myBook.TITLE = "A Book Title"
        Dim myPrice As New Price()
        myPrice.price = CDec(9.95)
        myPrice.currency = "US Dollar"
        myBook.PRICE = myPrice
        Dim myBooks As New Books()
        myBooks.Book = myBook
        mySerializer.Serialize(myWriter, myBooks, myNamespaces)
        myWriter.Close()
    End Sub
End Class

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class 'Books

<XmlType([Namespace] := "http://www.cpandl.com")> _
Public Class Book

    <XmlElement([Namespace] := "http://www.cpandl.com")> _
    Public TITLE As String
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public PRICE As Price
End Class

Public Class Price
    <XmlAttribute([Namespace] := "http://www.cpandl.com")> _
    Public currency As String
    Public <XmlElement([Namespace] := "http://www.cohowinery.com")> _
        price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Run
{
    public static void Main()
    {
        Run test = new Run();
        test.SerializeObject("XmlNamespaces.xml");
    }
    public void SerializeObject(string filename)
    {
        XmlSerializer mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        XmlSerializerNamespaces myNamespaces =
        new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        Book myBook = new Book();
        myBook.TITLE = "A Book Title";
        Price myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        Books myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter,myBooks,myNamespaces);
        myWriter.Close();
    }
}

public class Books
{
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public Book Book;
}

[XmlType(Namespace ="http://www.cpandl.com")]
public class Book
{
    [XmlElement(Namespace = "http://www.cpandl.com")]
    public string TITLE;
    [XmlElement(Namespace ="http://www.cohowinery.com")]
    public Price PRICE;
}
```

## <a name="see-also"></a><span data-ttu-id="cf14c-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cf14c-120">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="cf14c-121">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="cf14c-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="cf14c-122">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="cf14c-122">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="cf14c-123">Klasy XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="cf14c-123">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="cf14c-124">Atrybuty kontrolujące serializację XML</span><span class="sxs-lookup"><span data-stu-id="cf14c-124">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="cf14c-125">Instrukcje: Określ nazwę elementu alternatywny Stream XML</span><span class="sxs-lookup"><span data-stu-id="cf14c-125">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="cf14c-126">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="cf14c-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="cf14c-127">Instrukcje: Deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="cf14c-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
