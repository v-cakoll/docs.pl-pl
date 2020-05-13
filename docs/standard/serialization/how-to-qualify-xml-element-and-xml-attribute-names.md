---
title: Jak kwalifikować elementy XML i nazwy atrybutów XML
description: W tym artykule opisano, jak zakwalifikować nazwy elementów XML i atrybutów XML w dokumentach XML.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- qualifying XML names
- qualifying XML elements
- XML namespaces, qualifying elements and names in
ms.assetid: 44719f90-7e15-42e8-a9e2-282287e2b5bf
ms.openlocfilehash: 6c29e03d9ce28e5b0abc68a5d7e8d82f4485ac93
ms.sourcegitcommit: d6bd7903d7d46698e9d89d3725f3bb4876891aa3
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/13/2020
ms.locfileid: "83378412"
---
# <a name="how-to-qualify-xml-element-and-xml-attribute-names"></a>Jak kwalifikować elementy XML i nazwy atrybutów XML

Przestrzenie nazw XML zawarte w wystąpieniach <xref:System.Xml.Serialization.XmlSerializerNamespaces> klasy muszą być zgodne ze specyfikacją organizacja World Wide Web Consortium (W3C) o nazwie [przestrzenie nazw w kodzie XML](https://www.w3.org/TR/REC-xml-names/).

Obszary nazw XML umożliwiają uprawniających nazwy elementów XML i atrybutów XML w dokumentach XML. Kwalifikowana nazwa składa się z prefiksu i lokalna nazwa, rozdzielone średnikiem. Prefiks działa tylko jako symbol zastępczy; jest on mapowany na identyfikator URI, który określa przestrzeń nazw. Kombinacja powszechnie zarządzanych nazw identyfikatora URI i lokalna nazwa tworzy nazwę, która może być unikatowym.

Utworzenie wystąpienia `XmlSerializerNamespaces` i Dodawanie obiektu pary nazw, można określić prefiksy używane w dokumencie XML.

## <a name="to-create-qualified-names-in-an-xml-document"></a>Aby utworzyć kwalifikowane nazwy w dokumencie XML

1. Utworzenie wystąpienia `XmlSerializerNamespaces` klasy.

2. Dodaj wszystkie prefiksy i pary nazw do `XmlSerializerNamespaces`.

3. Zastosuj odpowiedni `System.Xml.Serialization` atrybut do każdego elementu członkowskiego lub klasy, które <xref:System.Xml.Serialization.XmlSerializer> ma zostać zserializowane w dokumencie XML.

    Dostępne są następujące atrybuty: <xref:System.Xml.Serialization.XmlAnyElementAttribute>, <xref:System.Xml.Serialization.XmlArrayAttribute>, <xref:System.Xml.Serialization.XmlArrayItemAttribute>, <xref:System.Xml.Serialization.XmlAttributeAttribute>, <xref:System.Xml.Serialization.XmlElementAttribute>, <xref:System.Xml.Serialization.XmlRootAttribute>, i <xref:System.Xml.Serialization.XmlTypeAttribute>.

4. Ustaw `Namespace` właściwości każdego atrybutu do jednej z tych wartości nazw z `XmlSerializerNamespaces`.

5. Przekaż `XmlSerializerNamespaces` do `Serialize` metody `XmlSerializer`.

## <a name="example"></a>Przykład

Poniższy przykład tworzy `XmlSerializerNamespaces` i dodaje dwa pary prefiksów i przestrzeni nazw do obiektu. Tworzy kod `XmlSerializer` używany do serializacji wystąpienia `Books` klasy. Wywołania kodu `Serialize` metody z `XmlSerializerNamespaces`, umożliwiając XML zawiera prefiksem obszary nazw.

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

## <a name="see-also"></a>Zobacz też

- <xref:System.Xml.Serialization.XmlSerializer>
- [Narzędzie definicji schematu XML i serializacja XML](the-xml-schema-definition-tool-and-xml-serialization.md)
- [Wprowadzenie do serializacji XML](introducing-xml-serialization.md)
- [Klasa XmlSerializer](xref:System.Xml.Serialization.XmlSerializer)
- [Atrybuty kontrolujące serializacji XML](attributes-that-control-xml-serialization.md)
- [Instrukcje: Określanie alternatywnej nazwy elementu dla strumienia XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)
