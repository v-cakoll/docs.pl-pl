---
title: "Porady: kwalifikują się do elementu XML i nazwach atrybutów XML"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 048bcc587915467f644a2cce695cec352147223a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/23/2017
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a><span data-ttu-id="3b7fb-102">Porady: kwalifikują się do elementu XML i nazwach atrybutów XML</span><span class="sxs-lookup"><span data-stu-id="3b7fb-102">How to: Qualify XML Element and XML Attribute Names</span></span>
[<span data-ttu-id="3b7fb-103">Przykładowy kod</span><span class="sxs-lookup"><span data-stu-id="3b7fb-103">Code Example</span></span>](#cpconworkingwithxmlnamespacesanchor1)  
  
 <span data-ttu-id="3b7fb-104">Obszary nazw XML zawartych wystąpienia <xref:System.Xml.Serialization.XmlSerializerNamespaces> klasy musi być zgodna ze specyfikacją World Wide Web Consortium (www.w3.org) o nazwie "Obszary nazw w języku XML".</span><span class="sxs-lookup"><span data-stu-id="3b7fb-104">XML namespaces contained by instances of the <xref:System.Xml.Serialization.XmlSerializerNamespaces> class must conform to the World Wide Web Consortium (www.w3.org) specification called "Namespaces in XML."</span></span>  
  
 <span data-ttu-id="3b7fb-105">Obszary nazw XML umożliwiają uprawniających nazwy elementów XML i atrybutów XML w dokumentach XML.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-105">XML namespaces provide a method for qualifying the names of XML elements and XML attributes in XML documents.</span></span> <span data-ttu-id="3b7fb-106">Kwalifikowana nazwa składa się z prefiksu i lokalna nazwa, rozdzielone średnikiem.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-106">A qualified name consists of a prefix and a local name, separated by a colon.</span></span> <span data-ttu-id="3b7fb-107">Prefiks działa tylko jako symbol zastępczy; jest mapowany do identyfikatora URI, który określa przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-107">The prefix functions only as a placeholder; it is mapped to a URI that specifies a namespace.</span></span> <span data-ttu-id="3b7fb-108">Kombinacja powszechnie zarządzanych nazw identyfikatora URI i lokalna nazwa tworzy nazwę, która może być unikatowym.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-108">The combination of the universally managed URI namespace and the local name produces a name that is guaranteed to be universally unique.</span></span>  
  
 <span data-ttu-id="3b7fb-109">Utworzenie wystąpienia `XmlSerializerNamespaces` i Dodawanie obiektu pary nazw, można określić prefiksy używane w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-109">By creating an instance of `XmlSerializerNamespaces` and adding the namespace pairs to the object, you can specify the prefixes used in an XML document.</span></span>  
  
### <a name="to-create-qualified-names-in-an-xml-document"></a><span data-ttu-id="3b7fb-110">Aby utworzyć kwalifikowane nazwy w dokumencie XML</span><span class="sxs-lookup"><span data-stu-id="3b7fb-110">To create qualified names in an XML document</span></span>  
  
1.  <span data-ttu-id="3b7fb-111">Utworzenie wystąpienia `XmlSerializerNamespaces` klasy.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-111">Create an instance of the `XmlSerializerNamespaces` class.</span></span>  
  
2.  <span data-ttu-id="3b7fb-112">Dodaj wszystkie prefiksy i pary nazw do `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-112">Add all prefixes and namespace pairs to the `XmlSerializerNamespaces`.</span></span>  
  
3.  <span data-ttu-id="3b7fb-113">Zastosuj odpowiednie `System.Xml.Serialization` atrybut do każdego elementu członkowskiego lub klasy, która <xref:System.Xml.Serialization.XmlSerializer> jest do serializacji w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-113">Apply the appropriate `System.Xml.Serialization` attribute to each member or class that the <xref:System.Xml.Serialization.XmlSerializer> is to serialize into an XML document.</span></span>  
  
     <span data-ttu-id="3b7fb-114">Dostępne są następujące atrybuty: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, i <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-114">The available attributes are: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span>  
  
4.  <span data-ttu-id="3b7fb-115">Ustaw `Namespace` właściwości każdego atrybutu do jednej z tych wartości nazw z `XmlSerializerNamespaces`.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-115">Set the `Namespace` property of each attribute to one of the namespace values from the `XmlSerializerNamespaces`.</span></span>  
  
5.  <span data-ttu-id="3b7fb-116">Przekaż `XmlSerializerNamespaces` do `Serialize` metody `XmlSerializer`.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-116">Pass the `XmlSerializerNamespaces` to the `Serialize` method of the `XmlSerializer`.</span></span>  
  
## <a name="example"></a><span data-ttu-id="3b7fb-117">Przykład</span><span class="sxs-lookup"><span data-stu-id="3b7fb-117">Example</span></span>  
 <span data-ttu-id="3b7fb-118">Poniższy przykład tworzy `XmlSerializerNamespaces`, i dodaje dwie pary prefiksu i przestrzeni nazw do obiektu.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-118">The following example creates an `XmlSerializerNamespaces`, and adds two prefix and namespace pairs to the object.</span></span> <span data-ttu-id="3b7fb-119">Tworzy kod `XmlSerializer` używany do serializacji wystąpienia `Books` klasy.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-119">The code creates an `XmlSerializer` that is used to serialize an instance of the `Books` class.</span></span> <span data-ttu-id="3b7fb-120">Wywołania kodu `Serialize` metody z `XmlSerializerNamespaces`, umożliwiając XML zawiera prefiksem obszary nazw.</span><span class="sxs-lookup"><span data-stu-id="3b7fb-120">The code calls the `Serialize` method with the `XmlSerializerNamespaces`, allowing the XML to contain prefixed namespaces.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="3b7fb-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3b7fb-121">See Also</span></span>  
 <xref:System.Xml.Serialization.XmlSerializer>  
 [<span data-ttu-id="3b7fb-122">Narzędzie definicji schematu XML i serializacja XML</span><span class="sxs-lookup"><span data-stu-id="3b7fb-122">The XML Schema Definition Tool and XML Serialization</span></span>](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md)  
 [<span data-ttu-id="3b7fb-123">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="3b7fb-123">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="3b7fb-124">Klasa XmlSerializer</span><span class="sxs-lookup"><span data-stu-id="3b7fb-124">XmlSerializer Class</span></span>](xref:System.Xml.Serialization.XmlSerializer)  
 [<span data-ttu-id="3b7fb-125">Atrybuty kontrolujące serializację XML</span><span class="sxs-lookup"><span data-stu-id="3b7fb-125">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 [<span data-ttu-id="3b7fb-126">Instrukcje: Określanie alternatywnej nazwy elementu dla strumienia XML</span><span class="sxs-lookup"><span data-stu-id="3b7fb-126">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [<span data-ttu-id="3b7fb-127">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="3b7fb-127">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="3b7fb-128">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="3b7fb-128">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
