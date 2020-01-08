---
title: Jak kwalifikować elementy XML i nazwy atrybutów XML
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 383dc7687e67e183b86598857067801c950b0312
ms.sourcegitcommit: 8c99457955fc31785b36b3330c4ab6ce7984a7ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/29/2019
ms.locfileid: "75545092"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="9a9b9-102">Jak kwalifikować elementy XML i nazwy atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="9a9b9-102">How to qualify XML element and XML attribute names</span></span>

<span data-ttu-id="9a9b9-103">Przestrzenie nazw XML zawarte w wystąpieniach klasy <xref:System.Xml.Serialization.XmlSerializerNamespaces> muszą być zgodne ze specyfikacją organizacja World Wide Web Consortium (W3C) o nazwie [przestrzenie nazw w kodzie XML](https://www.w3.org/TR/REC-xml-names/).</span><span class="sxs-lookup"><span data-stu-id="9a9b9-103">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (W3C) specification called [Namespaces in XML](https://www.w3.org/TR/REC-xml-names/).</span></span>

<span data-ttu-id="9a9b9-104">Obszary nazw XML umożliwiają uprawniających nazwy elementów XML i atrybutów XML w dokumentach XML.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-104">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="9a9b9-105">Kwalifikowana nazwa składa się z prefiksu i lokalna nazwa, rozdzielone średnikiem.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-105">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="9a9b9-106">Prefiks działa tylko jako symbol zastępczy; jest on mapowany na identyfikator URI, który określa przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-106">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="9a9b9-107">Kombinacja powszechnie zarządzanych nazw identyfikatora URI i lokalna nazwa tworzy nazwę, która może być unikatowym.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-107">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>

<span data-ttu-id="9a9b9-108">Utworzenie wystąpienia `XmlSerializerNamespaces` i Dodawanie obiektu pary nazw, można określić prefiksy używane w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-108">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>

## <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="9a9b9-109">Aby utworzyć kwalifikowane nazwy w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="9a9b9-109">To create qualified names in an XML document</span></span>

1. <span data-ttu-id="9a9b9-110">Utworzenie wystąpienia `XmlSerializerNamespaces` klasy.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-110">Create an instance of the `XmlSerializerNamespaces` class.</span></span>

2. <span data-ttu-id="9a9b9-111">Dodaj wszystkie prefiksy i pary nazw do `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-111">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>

3. <span data-ttu-id="9a9b9-112">Zastosuj odpowiedni atrybut `System.Xml.Serialization` do każdego elementu członkowskiego lub klasy, które <xref:System.Xml.Serialization.XmlSerializer> ma do serializacji w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-112">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>

    <span data-ttu-id="9a9b9-113">Dostępne są następujące atrybuty: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, i <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-113">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>

4. <span data-ttu-id="9a9b9-114">Ustaw `Namespace` właściwości każdego atrybutu do jednej z tych wartości nazw z `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-114">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>

5. <span data-ttu-id="9a9b9-115">Przekaż `XmlSerializerNamespaces` do `Serialize` metody `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-115">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>

## <a name="example"></a><span data-ttu-id="9a9b9-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="9a9b9-116">Example</span></span>

<span data-ttu-id="9a9b9-117">Poniższy przykład tworzy `XmlSerializerNamespaces`i dodaje dwa pary prefiksów i przestrzeni nazw do obiektu.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-117">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="9a9b9-118">Tworzy kod `XmlSerializer` używany do serializacji wystąpienia `Books` klasy.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-118">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="9a9b9-119">Wywołania kodu `Serialize` metody z `XmlSerializerNamespaces`, umożliwiając XML zawiera prefiksem obszary nazw.</span><span class="sxs-lookup"><span data-stu-id="9a9b9-119">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>

```vb
Imports System.IO
Imports System.Xml
Imports System.Xml.Serialization

Public Module Program

    Public Sub Main()
        SerializeObject("XmlNamespaces.xml")
    End Sub

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
End Module

Public Class Books
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public Book As Book
End Class

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
    <XmlElement([Namespace] := "http://www.cohowinery.com")> _
    Public price As Decimal
End Class
```

```csharp
using System;
using System.IO;
using System.Xml;
using System.Xml.Serialization;

public class Program
{
    public static void Main()
    {
        SerializeObject("XmlNamespaces.xml");
    }
    
    public static void SerializeObject(string filename)
    {
        var mySerializer = new XmlSerializer(typeof(Books));
        // Writing a file requires a TextWriter.
        TextWriter myWriter = new StreamWriter(filename);

        // Creates an XmlSerializerNamespaces and adds two
        // prefix-namespace pairs.
        var myNamespaces = new XmlSerializerNamespaces();
        myNamespaces.Add("books", "http://www.cpandl.com");
        myNamespaces.Add("money", "http://www.cohowinery.com");

        // Creates a Book.
        var myBook = new Book();
        myBook.TITLE = "A Book Title";
        var myPrice = new Price();
        myPrice.price = (decimal) 9.95;
        myPrice.currency = "US Dollar";
        myBook.PRICE = myPrice;
        var myBooks = new Books();
        myBooks.Book = myBook;
        mySerializer.Serialize(myWriter, myBooks, myNamespaces);
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

public class Price
{
    [XmlAttribute(Namespace = "http://www.cpandl.com")]
    public string currency;
    [XmlElement(Namespace = "http://www.cohowinery.com")]
    public decimal price;
}
```

## <a name="see-also"></a><span data-ttu-id="9a9b9-120">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9a9b9-120">See also</span></span>

- <xref:System.Xml.Serialization.XmlSerializer>
- [<span data-ttu-id="9a9b9-121">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="9a9b9-121">The XML Schema Definition Tool and XML Serialization</span></span>](the-xml-schema-definition-tool-and-xml-serialization.md)
- [<span data-ttu-id="9a9b9-122">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="9a9b9-122">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="9a9b9-123">Klasa XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="9a9b9-123">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)
- [<span data-ttu-id="9a9b9-124">Atrybuty kontrolujące serializację XML</span><span class="sxs-lookup"><span data-stu-id="9a9b9-124">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="9a9b9-125">Instrukcje: Określanie alternatywnej nazwy elementu dla strumienia XML</span><span class="sxs-lookup"><span data-stu-id="9a9b9-125">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="9a9b9-126">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="9a9b9-126">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="9a9b9-127">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="9a9b9-127">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
