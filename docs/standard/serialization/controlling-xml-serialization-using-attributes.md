---
title: Kontrolowanie serializacji XML przy użyciu atrybutów
description: Atrybuty można kontrolować serializacji XML obiektu lub utworzyć alternatywny strumień XML z tego samego zestawu klas.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- classes, serializing
- XML serialization, examples
- derived classes, serializing
- arrays, serializing
- XML serialization, attributes
- preventing serialization
- attributes [.NET Framework], XML serialization
- serialization, examples
- serialization, attributes
ms.assetid: 47d4c39d-30e1-4c7b-8a2e-301325390647
ms.openlocfilehash: 79c5541b4c384e91fbec8c8f1b2130887e79a252
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84289684"
---
# <a name="controlling-xml-serialization-using-attributes"></a>Kontrolowanie serializacji XML przy użyciu atrybutów

Atrybuty można kontrolować serializacji XML obiektu lub utworzyć alternatywny strumień XML z tego samego zestawu klas. Aby uzyskać więcej informacji na temat tworzenia alternatywnego strumienia XML, zobacz [How to: Określanie alternatywnej nazwy elementu dla strumienia XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).

> [!NOTE]
> Jeśli wygenerowany kod XML musi być zgodny z sekcją 5 dokumentu organizacja World Wide Web Consortium (W3C) zatytułowanego [Simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), użyj atrybutów wymienionych w [atrybutach, które kontrolują zaszyfrowane serializacji SOAP](attributes-that-control-encoded-soap-serialization.md).

Domyślnie nazwa elementu XML jest określana przez nazwę klasy lub składowej. W prostej klasie o nazwie `Book` pole o nazwie `ISBN` utworzy tag elementu XML \<ISBN> , jak pokazano w poniższym przykładzie.

```vb
Public Class Book
    Public ISBN As String
End Class
' When an instance of the Book class is serialized, it might
' produce this XML:
' <ISBN>1234567890</ISBN>.
```

```csharp
public class Book
{
    public string ISBN;
}
// When an instance of the Book class is serialized, it might
// produce this XML:
// <ISBN>1234567890</ISBN>.
```

To zachowanie domyślne można zmienić, aby nadać nową nazwę elementu. Poniższy kod pokazuje, jak atrybut umożliwia to przez ustawienie <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> właściwości <xref:System.Xml.Serialization.XmlElementAttribute>.

```vb
Public Class TaxRates
   < XmlElement(ElementName = "TaxRate")> _
    Public ReturnTaxRate As Decimal
End Class
```

```csharp
public class TaxRates {
    [XmlElement(ElementName = "TaxRate")]
    public decimal ReturnTaxRate;
}
```

Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty](../attributes/index.md). Aby zapoznać się z listą atrybutów kontrolujących serializacji XML, zobacz atrybuty kontrolujące [serializacji XML](attributes-that-control-xml-serialization.md).

## <a name="controlling-array-serialization"></a>Kontrolowanie serializacji tablicy

<xref:System.Xml.Serialization.XmlArrayAttribute> i <xref:System.Xml.Serialization.XmlArrayItemAttribute> atrybuty są przeznaczone do sterowania serializacji tablic. Przy użyciu tych atrybutów, można kontrolować nazwy elementu, nazw i typ danych schematu XML (XSD) (zgodnie z definicją w dokumencie World Wide Web Consortium [www.w3.org] zatytułowany "XML schematu część 2: typy danych"). Można również określić typy, które mogły zostać uwzględnione w tablicy.

<xref:System.Xml.Serialization.XmlArrayAttribute> Ustali właściwości otaczającego element XML, który powstaje wtedy, gdy jest serializowana tablicy. Na przykład domyślnie Serializowanie tablicy poniżej spowoduje wystąpienie elementu XML o nazwie `Employees` . `Employees` Element będzie zawierać szereg elementów o nazwie po typ tablicy `Employee`.

```vb
Public Class Group
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
```

```csharp
public class Group {
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
```

Zserializowany wystąpienie może wyglądać w następujący sposób.

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

Stosując <xref:System.Xml.Serialization.XmlArrayAttribute> , można zmienić nazwę elementu XML w następujący sposób.

```vb
Public Class Group
    <XmlArray("TeamMembers")> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlArray("TeamMembers")]
    public Employee[] Employees;
}
```

Wynikowy kod XML może wyglądać w następujący sposób.

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

<xref:System.Xml.Serialization.XmlArrayItemAttribute>, Z drugiej strony, określa, jak są serializacji elementów znajdujących się w tablicy. Należy zauważyć, że atrybut jest stosowany do pola zwracającego tablicę.

```vb
Public Class Group
    <XmlArrayItem("MemberName")> _
    Public Employee() As Employees
End Class
```

```csharp
public class Group {
    [XmlArrayItem("MemberName")]
    public Employee[] Employees;
}
```

Wynikowy kod XML może wyglądać w następujący sposób.

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a>Klasy pochodne serializacji

Używanie innego <xref:System.Xml.Serialization.XmlArrayItemAttribute> jest umożliwienie serializacji w klasach pochodnych. Na przykład inną klasę o nazwie `Manager` , która pochodzi od, `Employee` można dodać do poprzedniego przykładu. Jeśli nie zastosowano <xref:System.Xml.Serialization.XmlArrayItemAttribute> , kod zakończy się niepowodzeniem w czasie wykonywania, ponieważ typ klasy pochodnej nie zostanie rozpoznany. Aby rozwiązać ten stan, zastosuj atrybut dwa razy, za każdym razem, gdy ustawia <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> Właściwość dla każdego akceptowalnego typu (podstawowa i pochodna).

```vb
Public Class Group
    <XmlArrayItem(Type:=GetType(Employee)), _
    XmlArrayItem(Type:=GetType(Manager))> _
    Public Employees() As Employee
End Class
Public Class Employee
    Public Name As String
End Class
Public Class Manager
Inherits Employee
    Public Level As Integer
End Class
```

```csharp
public class Group {
    [XmlArrayItem(Type = typeof(Employee)),
    XmlArrayItem(Type = typeof(Manager))]
    public Employee[] Employees;
}
public class Employee {
    public string Name;
}
public class Manager:Employee {
    public int Level;
}
```

Zserializowany wystąpienie może wyglądać w następujący sposób.

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
    <Employee xsi:type = "Manager">
        <Name>Ann</Name>
        <Level>3</Level>
    </Employee>
</Employees>
</Group>
```

## <a name="serializing-an-array-as-a-sequence-of-elements"></a>Szeregowanie tablicę jako sekwencję elementów

Można również serializować tablicę jako płaską sekwencję elementów XML, stosując <xref:System.Xml.Serialization.XmlElementAttribute> do pola zwracającego tablicę w następujący sposób.

```vb
Public Class Group
    <XmlElement> _
    Public Employees() As Employee
End Class
```

```csharp
public class Group {
    [XmlElement]
    public Employee[] Employees;
}
```

Zserializowany wystąpienie może wyglądać w następujący sposób.

```xml
<Group>
<Employees>
    <Name>Haley</Name>
</Employees>
<Employees>
    <Name>Noriko</Name>
</Employees>
<Employees>
    <Name>Marco</Name>
</Employees>
</Group>
```

W inny sposób do odróżniania dwóch strumieni XML jest do generowania PLików dokumentów schematu XML (XSD) z skompilowany kod za pomocą narzędzia definicji schematu XML. (Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [narzędzie definicji schematu XML i SERIALIZACJA XML](the-xml-schema-definition-tool-and-xml-serialization.md)). Gdy żaden atrybut nie jest stosowany do pola, schemat opisuje element w następujący sposób.

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

Gdy <xref:System.Xml.Serialization.XmlElementAttribute> zostanie zastosowany do pola, w efekcie schemat zawiera opis elementu w następujący sposób.

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />
```

## <a name="serializing-an-arraylist"></a>Serializacji ArrayList

<xref:System.Collections.ArrayList> Klasy może zawierać kolekcji różnych obiektów. Korzystając z tego powodu <xref:System.Collections.ArrayList> , ile skorzystaj z tablicy. Używaj pola, która zwraca tablicę obiektów określonego typu, jednak można utworzyć pole, które zwraca pojedynczą <xref:System.Collections.ArrayList>. Jednak, podobnie jak w przypadku tablic, musi powiadomić <xref:System.Xml.Serialization.XmlSerializer> typów obiektów <xref:System.Collections.ArrayList> zawiera. Aby to osiągnąć, należy przypisać wiele wystąpień <xref:System.Xml.Serialization.XmlElementAttribute> do pola, jak pokazano w poniższym przykładzie.

```vb
Public Class Group
    <XmlElement(Type:=GetType(Employee)), _
    XmlElement(Type:=GetType(Manager))> _
    Public Info As ArrayList
End Class
```

```csharp
public class Group {
    [XmlElement(Type = typeof(Employee)),
    XmlElement(Type = typeof(Manager))]
    public ArrayList Info;
}
```

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a>Kontrolowanie serializacji klas przy użyciu XmlRootAttribute i XmlTypeAttribute

Istnieją dwa atrybuty, które można zastosować do klasy (i tylko klasy): <xref:System.Xml.Serialization.XmlRootAttribute> i <xref:System.Xml.Serialization.XmlTypeAttribute> . Te atrybuty są bardzo podobne. <xref:System.Xml.Serialization.XmlRootAttribute>Może być stosowana tylko do jednej klasy: Klasa, która, gdy jest serializowana, reprezentuje element otwierający i zamykający dokumentu XML — innymi słowy, element główny. <xref:System.Xml.Serialization.XmlTypeAttribute>, Z drugiej strony, można zastosować do dowolnej klasy, w tym klasy głównej.

Na przykład w poprzednich przykładach `Group` Klasa jest klasą główną, a wszystkie jej pola publiczne i właściwości stają się elementami XML, które znajdują się w dokumencie XML. Dlatego może być tylko jeden katalog główny klasy. Stosując, można <xref:System.Xml.Serialization.XmlRootAttribute> kontrolować strumień XML generowany przez <xref:System.Xml.Serialization.XmlSerializer> . Można na przykład zmienić nazwę elementu i przestrzeń nazw.

<xref:System.Xml.Serialization.XmlTypeAttribute> Umożliwia sterowanie schemat wygenerowanego kodu XML. Ta funkcja jest przydatne, gdy należy opublikować schematu za pomocą usługi sieci Web XML. W poniższym przykładzie zastosowano zarówno, <xref:System.Xml.Serialization.XmlTypeAttribute> jak i <xref:System.Xml.Serialization.XmlRootAttribute> do tej samej klasy.

```vb
<XmlRoot("NewGroupName"), _
XmlType("NewTypeName")> _
Public Class Group
    Public Employees() As Employee
End Class
```

```csharp
[XmlRoot("NewGroupName")]
[XmlType("NewTypeName")]
public class Group {
    public Employee[] Employees;
}
```

Jeśli ta klasa jest skompilowana, a narzędzie definicji schematu XML jest używany do generowania jego schematu, czy okażą się następujące XML opisujący `Group`.

```xml
<xs:element name="NewGroupName" type="NewTypeName" />
```

Z drugiej strony, jeśli zostały do serializacji wystąpienia klasy, tylko `NewGroupName` będzie można znaleźć w dokumencie XML.

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a>Zapobieganie serializacji z XmlIgnoreAttribute

Może to być sytuacje, gdy właściwość publiczna lub pola nie jest konieczne serializacji. Na przykład pole lub właściwość może służyć do przechowywania metadanych. W takich przypadkach należy zastosować <xref:System.Xml.Serialization.XmlIgnoreAttribute> do pola lub właściwości, a następnie <xref:System.Xml.Serialization.XmlSerializer> pomijać je.

## <a name="see-also"></a>Zobacz także

- [Atrybuty kontrolujące serializacji XML](attributes-that-control-xml-serialization.md)
- [Atrybuty kontrolujące zakodowaną serializację protokołu SOAP](attributes-that-control-encoded-soap-serialization.md)
- [Wprowadzenie do serializacji XML](introducing-xml-serialization.md)
- [Przykłady serializacji XML](examples-of-xml-serialization.md)
- [Instrukcje: Określanie alternatywnej nazwy elementu dla strumienia XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)
