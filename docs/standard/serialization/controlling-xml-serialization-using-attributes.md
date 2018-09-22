---
title: Kontrolowanie serializacji XML przy użyciu atrybutów
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
ms.openlocfilehash: 28c7ebe1de3adb92e531597027e4b8bb7a63294c
ms.sourcegitcommit: ad99773e5e45068ce03b99518008397e1299e0d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/22/2018
ms.locfileid: "46580632"
---
# <a name="controlling-xml-serialization-using-attributes"></a>Kontrolowanie serializacji XML przy użyciu atrybutów

Atrybuty można kontrolować serializacji XML obiektu lub utworzyć alternatywny strumień XML z tego samego zestawu klas. Aby uzyskać więcej informacji na temat tworzenia alternatywne strumień XML, zobacz [jak: Określ alternatywną nazwę elementu XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).

> [!NOTE]
> Jeśli wygenerowany kod XML musi być zgodna z części 5 dokumentu World Wide Web Consortium (W3C) [proste obiektu dostępu protokołu (protokołu SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), użyj atrybutów na liście [atrybuty czy kontroli kodowany protokołu SOAP Serializacja](attributes-that-control-encoded-soap-serialization.md).

Domyślnie nazwa elementu XML jest określana przez nazwę klasy lub składowej. W klasie proste o nazwie `Book`, pole o nazwie `ISBN` dadzą tag elementu XML \<ISBN >, jak pokazano w poniższym przykładzie.

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

Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty](../../../docs/standard/attributes/index.md). Aby uzyskać listę atrybutów, które kontrolują serializacji XML, zobacz [atrybutów, sterowania serializacji XML](attributes-that-control-xml-serialization.md).

## <a name="controlling-array-serialization"></a>Kontrolowanie serializacji tablicy

<xref:System.Xml.Serialization.XmlArrayAttribute> i <xref:System.Xml.Serialization.XmlArrayItemAttribute> atrybuty są przeznaczone do sterowania serializacji tablic. Przy użyciu tych atrybutów, można kontrolować nazwy elementu, nazw i typ danych schematu XML (XSD) (zgodnie z definicją w dokumencie World Wide Web Consortium [www.w3.org] zatytułowany "XML schematu część 2: typy danych"). Można również określić typy, które mogły zostać uwzględnione w tablicy.

<xref:System.Xml.Serialization.XmlArrayAttribute> Ustali właściwości otaczającego element XML, który powstaje wtedy, gdy jest serializowana tablicy. Na przykład domyślnie serializację tablicy poniżej spowoduje element XML o nazwie `Employees`. `Employees` Element będzie zawierać szereg elementów o nazwie po typ tablicy `Employee`.

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

Stosując <xref:System.Xml.Serialization.XmlArrayAttribute>, nazwa elementu XML, można zmienić w następujący sposób.

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

<xref:System.Xml.Serialization.XmlArrayItemAttribute>, Z drugiej strony, określa, jak są serializacji elementów znajdujących się w tablicy. Należy pamiętać, że jest stosowany do pola zwrócenie wartości tablicy.

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

Używanie innego <xref:System.Xml.Serialization.XmlArrayItemAttribute> jest umożliwienie serializacji w klasach pochodnych. Na przykład inną klasę o nazwie `Manager` który pochodzi od klasy `Employee` mogą być dodawane do poprzedniego przykładu. Jeśli nie zastosujesz <xref:System.Xml.Serialization.XmlArrayItemAttribute>, kod będzie działać w czasie wykonywania, ponieważ nie zostanie rozpoznany typ klasy pochodnej. Aby rozwiązać ten problem, zastosuj atrybut dwa razy, każde ustawienie czasu <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> właściwości dla każdego typu dopuszczalnych (podstawową i pochodnej).

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
    <Employee>
</Employees>
</Group>
```

## <a name="serializing-an-array-as-a-sequence-of-elements"></a>Szeregowanie tablicę jako sekwencję elementów

Tablica może serializować jako prosty sekwencję elementów XML, stosując <xref:System.Xml.Serialization.XmlElementAttribute> do pola zwrócenie wartości tablicy w następujący sposób.

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

W inny sposób do odróżniania dwóch strumieni XML jest do generowania PLików dokumentów schematu XML (XSD) z skompilowany kod za pomocą narzędzia definicji schematu XML. (Aby uzyskać więcej informacji na temat korzystania z narzędzia, zobacz [narzędzie definicji schematu XML i serializacja XML](the-xml-schema-definition-tool-and-xml-serialization.md).) Gdy atrybut nie jest stosowane do pola, schemat opisuje elementu w następujący sposób.

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

Gdy <xref:System.Xml.Serialization.XmlElementAttribute> jest stosowany do pola, wynikowe schemat opisuje elementu w następujący sposób.

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" /> 
```

## <a name="serializing-an-arraylist"></a>Serializacji ArrayList

<xref:System.Collections.ArrayList> Klasy może zawierać kolekcji różnych obiektów. Korzystając z tego powodu <xref:System.Collections.ArrayList> , ile skorzystaj z tablicy. Używaj pola, która zwraca tablicę obiektów określonego typu, jednak można utworzyć pole, które zwraca pojedynczą <xref:System.Collections.ArrayList>. Jednak, podobnie jak w przypadku tablic, musi powiadomić <xref:System.Xml.Serialization.XmlSerializer> typów obiektów <xref:System.Collections.ArrayList> zawiera. W tym celu należy przypisać wiele wystąpień <xref:System.Xml.Serialization.XmlElementAttribute> do pola, jak pokazano w poniższym przykładzie.

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

Istnieją dwa atrybuty, które mogą być stosowane do klasy (i tylko klasę): <xref:System.Xml.Serialization.XmlRootAttribute> i <xref:System.Xml.Serialization.XmlTypeAttribute>. Te atrybuty są bardzo podobne. <xref:System.Xml.Serialization.XmlRootAttribute> Można zastosować do tylko jednej klasy: klasy, że po serializacji, reprezentuje dokumentu XML na otwieranie i zamykanie elementu — innymi słowy, element główny. <xref:System.Xml.Serialization.XmlTypeAttribute>, Z drugiej strony, można zastosować do każdej klasy, łącznie z klasy głównego.

Na przykład w poprzednich przykładach `Group` klasy jest klasą głównego i wszystkich jego publiczny pola i właściwości stają się elementy XML znalezione w dokumencie XML. Dlatego może być tylko jeden katalog główny klasy. Stosując <xref:System.Xml.Serialization.XmlRootAttribute>, można kontrolować strumień XML generowanych przez <xref:System.Xml.Serialization.XmlSerializer>. Na przykład można zmienić nazwy elementu i przestrzeni nazw.

<xref:System.Xml.Serialization.XmlTypeAttribute> Umożliwia sterowanie schemat wygenerowanego kodu XML. Ta funkcja jest przydatne, gdy należy opublikować schematu za pomocą usługi sieci Web XML. Następujący przykład dotyczy zarówno <xref:System.Xml.Serialization.XmlTypeAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do tej samej klasy.

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
<xs:element name="NewGroupName" type="NewTypeName">
```

Z drugiej strony, jeśli zostały do serializacji wystąpienia klasy, tylko `NewGroupName` będzie można znaleźć w dokumencie XML.

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a>Zapobieganie serializacji z XmlIgnoreAttribute

Może to być sytuacje, gdy właściwość publiczna lub pola nie jest konieczne serializacji. Na przykład pole lub właściwość może służyć do zawiera metadanych. W takiej sytuacji należy zastosować <xref:System.Xml.Serialization.XmlIgnoreAttribute> pola lub właściwości i <xref:System.Xml.Serialization.XmlSerializer> pozwoli na pominięcie nad nim.

## <a name="see-also"></a>Zobacz także

- [Atrybuty kontrolujące serializację XML](attributes-that-control-xml-serialization.md)  
- [Atrybuty kontrolujące zakodowaną serializację SOAP](attributes-that-control-encoded-soap-serialization.md)  
- [Wprowadzenie do serializacji XML](introducing-xml-serialization.md)  
- [Przykłady serializacji XML](examples-of-xml-serialization.md)  
- [Instrukcje: Określanie alternatywnej nazwy elementu dla strumienia XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
- [Instrukcje: Serializacja obiektu](how-to-serialize-an-object.md)  
- [Instrukcje: Deserializacja obiektu](how-to-deserialize-an-object.md)  
