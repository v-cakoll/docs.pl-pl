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
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a>Instrukcje: kwalifikowanie elementu XML i nazw atrybutów XML

Obszary nazw XML zawartych wystąpienia <xref:System.Xml.Serialization.XmlSerializerNamespaces> klasy musi być zgodna ze specyfikacją World Wide Web Consortium (W3C) o nazwie [przestrzeni nazw w kodzie XML](https://www.w3.org/TR/REC-xml-names/).

Obszary nazw XML umożliwiają uprawniających nazwy elementów XML i atrybutów XML w dokumentach XML. Kwalifikowana nazwa składa się z prefiksu i lokalna nazwa, rozdzielone średnikiem. Prefiks, który działa tylko jako symbolu zastępczego; jest mapowany do identyfikatora URI, który określa obszar nazw. Kombinacja powszechnie zarządzanych nazw identyfikatora URI i lokalna nazwa tworzy nazwę, która może być unikatowym.

Utworzenie wystąpienia `XmlSerializerNamespaces` i Dodawanie obiektu pary nazw, można określić prefiksy używane w dokumencie XML.

## <a name="to-create-qualified-names-in-an-xml-document"></a>Aby utworzyć kwalifikowane nazwy w dokumencie XML

1. Utworzenie wystąpienia `XmlSerializerNamespaces` klasy.

2. Dodaj wszystkie prefiksy i pary nazw do `XmlSerializerNamespaces`.

3. Zastosuj odpowiedni `System.Xml.Serialization` atrybut do każdej składowej lub klasy, które <xref:System.Xml.Serialization.XmlSerializer> ma serializować do dokumentu XML.

    Dostępne są następujące atrybuty: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, i <xref:System.Xml.Serialization.XmlTypeAttribute>.

4. Ustaw `Namespace` właściwości każdego atrybutu do jednej z tych wartości nazw z `XmlSerializerNamespaces`.

5. Przekaż `XmlSerializerNamespaces` do `Serialize` metody `XmlSerializer`.

## <a name="example"></a>Przykład

Poniższy przykład tworzy `XmlSerializerNamespaces`, i dodaje dwie pary prefiksu i obszaru nazw do obiektu. Tworzy kod `XmlSerializer` używany do serializacji wystąpienia `Books` klasy. Wywołania kodu `Serialize` metody z `XmlSerializerNamespaces`, umożliwiając XML zawiera prefiksem obszary nazw.

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

## <a name="see-also"></a>Zobacz także

- <xref:System.Xml.Serialization.XmlSerializer>
- [Narzędzie definicji schematu XML i serializacja XML](the-xml-schema-definition-tool-and-xml-serialization.md)
- [Wprowadzenie do serializacji XML](introducing-xml-serialization.md)
- [Klasy XmlSerializer](xref:System.Xml.Serialization.XmlSerializer)
- [Atrybuty kontrolujące serializację XML](attributes-that-control-xml-serialization.md)
- [Instrukcje: Określ nazwę elementu alternatywny Stream XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacji obiektu](how-to-deserialize-an-object.md)
