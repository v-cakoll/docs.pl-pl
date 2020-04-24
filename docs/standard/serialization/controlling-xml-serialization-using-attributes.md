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
ms.openlocfilehash: e11152dc626b1e3619b9ecbc04d8a237ca9f13d3
ms.sourcegitcommit: 99b153b93bf94d0fecf7c7bcecb58ac424dfa47c
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2020
ms.locfileid: "80248046"
---
# <a name="controlling-xml-serialization-using-attributes"></a><span data-ttu-id="ec316-102">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="ec316-102">Controlling XML Serialization Using Attributes</span></span>

<span data-ttu-id="ec316-103">Atrybuty można kontrolować serializacji XML obiektu lub utworzyć alternatywny strumień XML z tego samego zestawu klas.</span><span class="sxs-lookup"><span data-stu-id="ec316-103">Attributes can be used to control the XML serialization of an object or to create an alternate XML stream from the same set of classes.</span></span> <span data-ttu-id="ec316-104">Aby uzyskać więcej informacji na temat tworzenia alternatywnego strumienia XML, zobacz [How to: Określanie alternatywnej nazwy elementu dla strumienia XML](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span><span class="sxs-lookup"><span data-stu-id="ec316-104">For more details about creating an alternate XML stream, see [How to: Specify an Alternate Element Name for an XML Stream](how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>

> [!NOTE]
> <span data-ttu-id="ec316-105">Jeśli wygenerowany kod XML musi być zgodny z sekcją 5 dokumentu organizacja World Wide Web Consortium (W3C) zatytułowanego [Simple Object Access Protocol (SOAP) 1,1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), użyj atrybutów wymienionych w [atrybutach, które kontrolują zaszyfrowane serializacji SOAP](attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ec316-105">If the XML generated must conform to section 5 of the World Wide Web Consortium (W3C) document titled [Simple Object Access Protocol (SOAP) 1.1](https://www.w3.org/TR/2000/NOTE-SOAP-20000508/), use the attributes listed in [Attributes That Control Encoded SOAP Serialization](attributes-that-control-encoded-soap-serialization.md).</span></span>

<span data-ttu-id="ec316-106">Domyślnie nazwa elementu XML jest określana przez nazwę klasy lub składowej.</span><span class="sxs-lookup"><span data-stu-id="ec316-106">By default, an XML element name is determined by the class or member name.</span></span> <span data-ttu-id="ec316-107">W prostej klasie o `Book`nazwie pole o nazwie `ISBN` będzie generować tag \<elementu XML>, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ec316-107">In a simple class named `Book`, a field named `ISBN` will produce an XML element tag \<ISBN>, as shown in the following example.</span></span>

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

<span data-ttu-id="ec316-108">To zachowanie domyślne można zmienić, aby nadać nową nazwę elementu.</span><span class="sxs-lookup"><span data-stu-id="ec316-108">This default behavior can be changed if you want to give the element a new name.</span></span> <span data-ttu-id="ec316-109">Poniższy kod pokazuje, jak atrybut umożliwia to przez ustawienie <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> właściwości <xref:System.Xml.Serialization.XmlElementAttribute>.</span><span class="sxs-lookup"><span data-stu-id="ec316-109">The following code shows how an attribute enables this by setting the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> property of a <xref:System.Xml.Serialization.XmlElementAttribute>.</span></span>

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

<span data-ttu-id="ec316-110">Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybuty](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="ec316-110">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span> <span data-ttu-id="ec316-111">Aby zapoznać się z listą atrybutów kontrolujących serializacji XML, zobacz atrybuty kontrolujące [serializacji XML](attributes-that-control-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="ec316-111">For a list of attributes that control XML serialization, see [Attributes That Control XML Serialization](attributes-that-control-xml-serialization.md).</span></span>

## <a name="controlling-array-serialization"></a><span data-ttu-id="ec316-112">Kontrolowanie serializacji tablicy</span><span class="sxs-lookup"><span data-stu-id="ec316-112">Controlling Array Serialization</span></span>

<span data-ttu-id="ec316-113"><xref:System.Xml.Serialization.XmlArrayAttribute> i <xref:System.Xml.Serialization.XmlArrayItemAttribute> atrybuty są przeznaczone do sterowania serializacji tablic.</span><span class="sxs-lookup"><span data-stu-id="ec316-113">The <xref:System.Xml.Serialization.XmlArrayAttribute> and the <xref:System.Xml.Serialization.XmlArrayItemAttribute> attributes are designed to control the serialization of arrays.</span></span> <span data-ttu-id="ec316-114">Przy użyciu tych atrybutów, można kontrolować nazwy elementu, nazw i typ danych schematu XML (XSD) (zgodnie z definicją w dokumencie World Wide Web Consortium [www.w3.org] zatytułowany "XML schematu część 2: typy danych").</span><span class="sxs-lookup"><span data-stu-id="ec316-114">Using these attributes, you can control the element name, namespace, and XML Schema (XSD) data type (as defined in the World Wide Web Consortium [www.w3.org] document titled "XML Schema Part 2: Datatypes").</span></span> <span data-ttu-id="ec316-115">Można również określić typy, które mogły zostać uwzględnione w tablicy.</span><span class="sxs-lookup"><span data-stu-id="ec316-115">You can also specify the types that can be included in an array.</span></span>

<span data-ttu-id="ec316-116"><xref:System.Xml.Serialization.XmlArrayAttribute> Ustali właściwości otaczającego element XML, który powstaje wtedy, gdy jest serializowana tablicy.</span><span class="sxs-lookup"><span data-stu-id="ec316-116">The <xref:System.Xml.Serialization.XmlArrayAttribute> will determine the properties of the enclosing XML element that results when an array is serialized.</span></span> <span data-ttu-id="ec316-117">Na przykład domyślnie Serializowanie tablicy poniżej spowoduje wystąpienie elementu XML o nazwie `Employees`.</span><span class="sxs-lookup"><span data-stu-id="ec316-117">For example, by default, serializing the array below will result in an XML element named `Employees`.</span></span> <span data-ttu-id="ec316-118">`Employees` Element będzie zawierać szereg elementów o nazwie po typ tablicy `Employee`.</span><span class="sxs-lookup"><span data-stu-id="ec316-118">The `Employees` element will contain a series of elements named after the array type `Employee`.</span></span>

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

<span data-ttu-id="ec316-119">Zserializowany wystąpienie może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec316-119">A serialized instance might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</Employees>
</Group>
```

<span data-ttu-id="ec316-120">Stosując <xref:System.Xml.Serialization.XmlArrayAttribute>, można zmienić nazwę elementu XML w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec316-120">By applying a <xref:System.Xml.Serialization.XmlArrayAttribute>, you can change the name of the XML element, as follows.</span></span>

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

<span data-ttu-id="ec316-121">Wynikowy kod XML może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec316-121">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<TeamMembers>
    <Employee>
        <Name>Haley</Name>
    </Employee>
</TeamMembers>
</Group>
```

<span data-ttu-id="ec316-122"><xref:System.Xml.Serialization.XmlArrayItemAttribute>, Z drugiej strony, określa, jak są serializacji elementów znajdujących się w tablicy.</span><span class="sxs-lookup"><span data-stu-id="ec316-122">The <xref:System.Xml.Serialization.XmlArrayItemAttribute>, on the other hand, controls how the items contained in the array are serialized.</span></span> <span data-ttu-id="ec316-123">Należy zauważyć, że atrybut jest stosowany do pola zwracającego tablicę.</span><span class="sxs-lookup"><span data-stu-id="ec316-123">Note that the attribute is applied to the field returning the array.</span></span>

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

<span data-ttu-id="ec316-124">Wynikowy kod XML może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec316-124">The resulting XML might resemble the following.</span></span>

```xml
<Group>
<Employees>
    <MemberName>Haley</MemberName>
</Employees>
</Group>
```

## <a name="serializing-derived-classes"></a><span data-ttu-id="ec316-125">Klasy pochodne serializacji</span><span class="sxs-lookup"><span data-stu-id="ec316-125">Serializing Derived Classes</span></span>

<span data-ttu-id="ec316-126">Używanie innego <xref:System.Xml.Serialization.XmlArrayItemAttribute> jest umożliwienie serializacji w klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="ec316-126">Another use of the <xref:System.Xml.Serialization.XmlArrayItemAttribute> is to allow the serialization of derived classes.</span></span> <span data-ttu-id="ec316-127">Na przykład inną klasę o nazwie `Manager` , która pochodzi `Employee` od, można dodać do poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="ec316-127">For example, another class named `Manager` that derives from `Employee` can be added to the previous example.</span></span> <span data-ttu-id="ec316-128">Jeśli nie zastosowano <xref:System.Xml.Serialization.XmlArrayItemAttribute>, kod zakończy się niepowodzeniem w czasie wykonywania, ponieważ typ klasy pochodnej nie zostanie rozpoznany.</span><span class="sxs-lookup"><span data-stu-id="ec316-128">If you do not apply the <xref:System.Xml.Serialization.XmlArrayItemAttribute>, the code will fail at run time because the derived class type will not be recognized.</span></span> <span data-ttu-id="ec316-129">Aby rozwiązać ten stan, zastosuj atrybut dwa razy, za każdym razem <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> , gdy ustawia właściwość dla każdego akceptowalnego typu (podstawowa i pochodna).</span><span class="sxs-lookup"><span data-stu-id="ec316-129">To remedy this, apply the attribute twice, each time setting the <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> property for each acceptable type (base and derived).</span></span>

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

<span data-ttu-id="ec316-130">Zserializowany wystąpienie może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec316-130">A serialized instance might resemble the following.</span></span>

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

## <a name="serializing-an-array-as-a-sequence-of-elements"></a><span data-ttu-id="ec316-131">Szeregowanie tablicę jako sekwencję elementów</span><span class="sxs-lookup"><span data-stu-id="ec316-131">Serializing an Array as a Sequence of Elements</span></span>

<span data-ttu-id="ec316-132">Można również serializować tablicę jako płaską sekwencję elementów XML, stosując <xref:System.Xml.Serialization.XmlElementAttribute> do pola zwracającego tablicę w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec316-132">You can also serialize an array as a flat sequence of XML elements by applying a <xref:System.Xml.Serialization.XmlElementAttribute> to the field returning the array as follows.</span></span>

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

<span data-ttu-id="ec316-133">Zserializowany wystąpienie może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec316-133">A serialized instance might resemble the following.</span></span>

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

<span data-ttu-id="ec316-134">W inny sposób do odróżniania dwóch strumieni XML jest do generowania PLików dokumentów schematu XML (XSD) z skompilowany kod za pomocą narzędzia definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="ec316-134">Another way to differentiate the two XML streams is to use the XML Schema Definition tool to generate the XML Schema (XSD) document files from the compiled code.</span></span> <span data-ttu-id="ec316-135">(Aby uzyskać więcej informacji na temat korzystania z tego narzędzia, zobacz [narzędzie definicji schematu XML i SERIALIZACJA XML](the-xml-schema-definition-tool-and-xml-serialization.md)). Gdy żaden atrybut nie jest stosowany do pola, schemat opisuje element w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec316-135">(For more details on using the tool, see [The XML Schema Definition Tool and XML Serialization](the-xml-schema-definition-tool-and-xml-serialization.md).) When no attribute is applied to the field, the schema describes the element in the following manner.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />
```

<span data-ttu-id="ec316-136">Gdy <xref:System.Xml.Serialization.XmlElementAttribute> zostanie zastosowany do pola, w efekcie schemat zawiera opis elementu w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="ec316-136">When the <xref:System.Xml.Serialization.XmlElementAttribute> is applied to the field, the resulting schema describes the element as follows.</span></span>

```xml
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />
```

## <a name="serializing-an-arraylist"></a><span data-ttu-id="ec316-137">Serializacji ArrayList</span><span class="sxs-lookup"><span data-stu-id="ec316-137">Serializing an ArrayList</span></span>

<span data-ttu-id="ec316-138"><xref:System.Collections.ArrayList> Klasy może zawierać kolekcji różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="ec316-138">The <xref:System.Collections.ArrayList> class can contain a collection of diverse objects.</span></span> <span data-ttu-id="ec316-139">Korzystając z tego powodu <xref:System.Collections.ArrayList> , ile skorzystaj z tablicy.</span><span class="sxs-lookup"><span data-stu-id="ec316-139">You can therefore use a <xref:System.Collections.ArrayList> much as you use an array.</span></span> <span data-ttu-id="ec316-140">Używaj pola, która zwraca tablicę obiektów określonego typu, jednak można utworzyć pole, które zwraca pojedynczą <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="ec316-140">Instead of creating a field that returns an array of typed objects, however, you can create a field that returns a single <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="ec316-141">Jednak, podobnie jak w przypadku tablic, musi powiadomić <xref:System.Xml.Serialization.XmlSerializer> typów obiektów <xref:System.Collections.ArrayList> zawiera.</span><span class="sxs-lookup"><span data-stu-id="ec316-141">However, as with arrays, you must inform the <xref:System.Xml.Serialization.XmlSerializer> of the types of objects the <xref:System.Collections.ArrayList> contains.</span></span> <span data-ttu-id="ec316-142">Aby to osiągnąć, należy przypisać wiele wystąpień <xref:System.Xml.Serialization.XmlElementAttribute> do pola, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="ec316-142">To accomplish this, assign multiple instances of the <xref:System.Xml.Serialization.XmlElementAttribute> to the field, as shown in the following example.</span></span>

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

## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a><span data-ttu-id="ec316-143">Kontrolowanie serializacji klas przy użyciu XmlRootAttribute i XmlTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="ec316-143">Controlling Serialization of Classes Using XmlRootAttribute and XmlTypeAttribute</span></span>

<span data-ttu-id="ec316-144">Istnieją dwa atrybuty, które można zastosować do klasy (i tylko klasy): <xref:System.Xml.Serialization.XmlRootAttribute> i. <xref:System.Xml.Serialization.XmlTypeAttribute></span><span class="sxs-lookup"><span data-stu-id="ec316-144">There are two attributes that can be applied to a class (and only a class): <xref:System.Xml.Serialization.XmlRootAttribute> and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span> <span data-ttu-id="ec316-145">Te atrybuty są bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="ec316-145">These attributes are very similar.</span></span> <span data-ttu-id="ec316-146"><xref:System.Xml.Serialization.XmlRootAttribute> Może być stosowana tylko do jednej klasy: Klasa, która, gdy jest serializowana, reprezentuje element otwierający i zamykający dokumentu XML — innymi słowy, element główny.</span><span class="sxs-lookup"><span data-stu-id="ec316-146">The <xref:System.Xml.Serialization.XmlRootAttribute> can be applied to only one class: the class that, when serialized, represents the XML document's opening and closing element—in other words, the root element.</span></span> <span data-ttu-id="ec316-147"><xref:System.Xml.Serialization.XmlTypeAttribute>, Z drugiej strony, można zastosować do dowolnej klasy, w tym klasy głównej.</span><span class="sxs-lookup"><span data-stu-id="ec316-147">The <xref:System.Xml.Serialization.XmlTypeAttribute>, on the other hand, can be applied to any class, including the root class.</span></span>

<span data-ttu-id="ec316-148">Na przykład w poprzednich przykładach `Group` Klasa jest klasą główną, a wszystkie jej pola publiczne i właściwości stają się elementami XML, które znajdują się w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="ec316-148">For example, in the previous examples, the `Group` class is the root class, and all its public fields and properties become the XML elements found in the XML document.</span></span> <span data-ttu-id="ec316-149">Dlatego może być tylko jeden katalog główny klasy.</span><span class="sxs-lookup"><span data-stu-id="ec316-149">Therefore, there can be only one root class.</span></span> <span data-ttu-id="ec316-150">Stosując <xref:System.Xml.Serialization.XmlRootAttribute>, można kontrolować strumień XML generowany przez <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="ec316-150">By applying the <xref:System.Xml.Serialization.XmlRootAttribute>, you can control the XML stream generated by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="ec316-151">Można na przykład zmienić nazwę elementu i przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="ec316-151">For example, you can change the element name and namespace.</span></span>

<span data-ttu-id="ec316-152"><xref:System.Xml.Serialization.XmlTypeAttribute> Umożliwia sterowanie schemat wygenerowanego kodu XML.</span><span class="sxs-lookup"><span data-stu-id="ec316-152">The <xref:System.Xml.Serialization.XmlTypeAttribute> allows you to control the schema of the generated XML.</span></span> <span data-ttu-id="ec316-153">Ta funkcja jest przydatne, gdy należy opublikować schematu za pomocą usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="ec316-153">This capability is useful when you need to publish the schema through an XML Web service.</span></span> <span data-ttu-id="ec316-154">W poniższym przykładzie zastosowano zarówno <xref:System.Xml.Serialization.XmlTypeAttribute> , jak <xref:System.Xml.Serialization.XmlRootAttribute> i do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="ec316-154">The following example applies both the <xref:System.Xml.Serialization.XmlTypeAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the same class.</span></span>

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

<span data-ttu-id="ec316-155">Jeśli ta klasa jest skompilowana, a narzędzie definicji schematu XML jest używany do generowania jego schematu, czy okażą się następujące XML opisujący `Group`.</span><span class="sxs-lookup"><span data-stu-id="ec316-155">If this class is compiled, and the XML Schema Definition tool is used to generate its schema, you would find the following XML describing `Group`.</span></span>

```xml
<xs:element name="NewGroupName" type="NewTypeName" />
```

<span data-ttu-id="ec316-156">Z drugiej strony, jeśli zostały do serializacji wystąpienia klasy, tylko `NewGroupName` będzie można znaleźć w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="ec316-156">In contrast, if you were to serialize an instance of the class, only `NewGroupName` would be found in the XML document.</span></span>

```xml
<NewGroupName>
    . . .
</NewGroupName>
```

## <a name="preventing-serialization-with-the-xmlignoreattribute"></a><span data-ttu-id="ec316-157">Zapobieganie serializacji z XmlIgnoreAttribute</span><span class="sxs-lookup"><span data-stu-id="ec316-157">Preventing Serialization with the XmlIgnoreAttribute</span></span>

<span data-ttu-id="ec316-158">Może to być sytuacje, gdy właściwość publiczna lub pola nie jest konieczne serializacji.</span><span class="sxs-lookup"><span data-stu-id="ec316-158">There might be situations when a public property or field does not need to be serialized.</span></span> <span data-ttu-id="ec316-159">Na przykład pole lub właściwość może służyć do przechowywania metadanych.</span><span class="sxs-lookup"><span data-stu-id="ec316-159">For example, a field or property could be used to contain metadata.</span></span> <span data-ttu-id="ec316-160">W takich przypadkach należy zastosować <xref:System.Xml.Serialization.XmlIgnoreAttribute> do pola lub właściwości, a <xref:System.Xml.Serialization.XmlSerializer> następnie pomijać je.</span><span class="sxs-lookup"><span data-stu-id="ec316-160">In such cases, apply the <xref:System.Xml.Serialization.XmlIgnoreAttribute> to the field or property and the <xref:System.Xml.Serialization.XmlSerializer> will skip over it.</span></span>

## <a name="see-also"></a><span data-ttu-id="ec316-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ec316-161">See also</span></span>

- [<span data-ttu-id="ec316-162">Atrybuty kontrolujące serializacji XML</span><span class="sxs-lookup"><span data-stu-id="ec316-162">Attributes That Control XML Serialization</span></span>](attributes-that-control-xml-serialization.md)
- [<span data-ttu-id="ec316-163">Atrybuty kontrolujące zakodowaną serializację protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="ec316-163">Attributes That Control Encoded SOAP Serialization</span></span>](attributes-that-control-encoded-soap-serialization.md)
- [<span data-ttu-id="ec316-164">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="ec316-164">Introducing XML Serialization</span></span>](introducing-xml-serialization.md)
- [<span data-ttu-id="ec316-165">Przykłady serializacji XML</span><span class="sxs-lookup"><span data-stu-id="ec316-165">Examples of XML Serialization</span></span>](examples-of-xml-serialization.md)
- [<span data-ttu-id="ec316-166">Instrukcje: Określanie alternatywnej nazwy elementu dla strumienia XML</span><span class="sxs-lookup"><span data-stu-id="ec316-166">How to: Specify an Alternate Element Name for an XML Stream</span></span>](how-to-specify-an-alternate-element-name-for-an-xml-stream.md)
- [<span data-ttu-id="ec316-167">Instrukcje: Serializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="ec316-167">How to: Serialize an Object</span></span>](how-to-serialize-an-object.md)
- [<span data-ttu-id="ec316-168">Instrukcje: Deserializacja obiektu</span><span class="sxs-lookup"><span data-stu-id="ec316-168">How to: Deserialize an Object</span></span>](how-to-deserialize-an-object.md)
