---
title: "Kontrolowanie serializacji XML przy użyciu atrybutów"
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
caps.latest.revision: "4"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: e921402980b1382761dd25d9cbbabda6b2c6a038
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="controlling-xml-serialization-using-attributes"></a><span data-ttu-id="f9f35-102">Kontrolowanie serializacji XML przy użyciu atrybutów</span><span class="sxs-lookup"><span data-stu-id="f9f35-102">Controlling XML Serialization Using Attributes</span></span>
<span data-ttu-id="f9f35-103">Atrybuty można kontrolować serializacji XML obiektu lub utworzyć alternatywny strumień XML z tego samego zestawu klas.</span><span class="sxs-lookup"><span data-stu-id="f9f35-103">Attributes can be used to control the XML serialization of an object or to create an alternate XML stream from the same set of classes.</span></span> <span data-ttu-id="f9f35-104">Aby uzyskać więcej informacji o tworzeniu alternatywnego strumienia XML, zobacz [porady: Określ alternatywną nazwę elementu strumienia XML](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span><span class="sxs-lookup"><span data-stu-id="f9f35-104">For more details about creating an alternate XML stream, see [How to: Specify an Alternate Element Name for an XML Stream](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f9f35-105">Jeśli wygenerowany kod XML musi być zgodna z sekcji 5 konsorcjum World Wide Web (www.w3.org) dokumentu "Prosty obiekt dostępu protokołu (SOAP) 1.1", użyj atrybuty wymienione w [atrybuty że formant zakodowane SOAP serializacji](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="f9f35-105">If the XML generated must conform to section 5 of the World Wide Web Consortium (www.w3.org) document titled "Simple Object Access Protocol (SOAP) 1.1," use the attributes listed in [Attributes That Control Encoded SOAP Serialization](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md).</span></span>  
  
 <span data-ttu-id="f9f35-106">Domyślnie nazwa elementu XML jest określana przez nazwę klasy lub składowej.</span><span class="sxs-lookup"><span data-stu-id="f9f35-106">By default, an XML element name is determined by the class or member name.</span></span> <span data-ttu-id="f9f35-107">Proste klasy o nazwie `Book`, pole o nazwie `ISBN` spowoduje utworzenie tagu XML \<ISBN >, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f9f35-107">In a simple class named `Book`, a field named `ISBN` will produce an XML element tag \<ISBN>, as shown in the following example.</span></span>  
  
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
  
 <span data-ttu-id="f9f35-108">To zachowanie domyślne można zmienić, aby nadać nową nazwę elementu.</span><span class="sxs-lookup"><span data-stu-id="f9f35-108">This default behavior can be changed if you want to give the element a new name.</span></span> <span data-ttu-id="f9f35-109">Poniższy kod pokazuje, jak atrybut umożliwia to przez ustawienie <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> właściwości <xref:System.Xml.Serialization.XmlElementAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f9f35-109">The following code shows how an attribute enables this by setting the <xref:System.Xml.Serialization.XmlElementAttribute.ElementName%2A> property of a <xref:System.Xml.Serialization.XmlElementAttribute>.</span></span>  
  
```vb  
Public Class TaxRates  
   < XmlElement(ElementName = "TaxRate")> _  
    Public ReturnTaxRate As Decimal  
End Class  
```  
  
```csharp  
public class TaxRates{  
    [XmlElement(ElementName = "TaxRate")]  
    public decimal ReturnTaxRate;  
}  
```  
  
 <span data-ttu-id="f9f35-110">Aby uzyskać więcej informacji na temat atrybutów, zobacz [atrybutów](../../../docs/standard/attributes/index.md).</span><span class="sxs-lookup"><span data-stu-id="f9f35-110">For more information about attributes, see [Attributes](../../../docs/standard/attributes/index.md).</span></span> <span data-ttu-id="f9f35-111">Aby uzyskać listę atrybutów, które kontrolują serializacji XML, zobacz [atrybuty który kontroli serializacji XML](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md).</span><span class="sxs-lookup"><span data-stu-id="f9f35-111">For a list of attributes that control XML serialization, see [Attributes That Control XML Serialization](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md).</span></span>  
  
## <a name="controlling-array-serialization"></a><span data-ttu-id="f9f35-112">Kontrolowanie serializacji tablicy</span><span class="sxs-lookup"><span data-stu-id="f9f35-112">Controlling Array Serialization</span></span>  
 <span data-ttu-id="f9f35-113"><xref:System.Xml.Serialization.XmlArrayAttribute> i <xref:System.Xml.Serialization.XmlArrayItemAttribute> atrybuty są przeznaczone do sterowania serializacji tablic.</span><span class="sxs-lookup"><span data-stu-id="f9f35-113">The <xref:System.Xml.Serialization.XmlArrayAttribute> and the <xref:System.Xml.Serialization.XmlArrayItemAttribute> attributes are designed to control the serialization of arrays.</span></span> <span data-ttu-id="f9f35-114">Przy użyciu tych atrybutów, można kontrolować nazwy elementu, nazw i typ danych schematu XML (XSD) (zgodnie z definicją w dokumencie World Wide Web Consortium [www.w3.org] zatytułowany "XML schematu część 2: typy danych").</span><span class="sxs-lookup"><span data-stu-id="f9f35-114">Using these attributes, you can control the element name, namespace, and XML Schema (XSD) data type (as defined in the World Wide Web Consortium [www.w3.org] document titled "XML Schema Part 2: Datatypes").</span></span> <span data-ttu-id="f9f35-115">Można również określić typy, które mogły zostać uwzględnione w tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9f35-115">You can also specify the types that can be included in an array.</span></span>  
  
 <span data-ttu-id="f9f35-116"><xref:System.Xml.Serialization.XmlArrayAttribute> Ustali właściwości otaczającego element XML, który powstaje wtedy, gdy jest serializowana tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9f35-116">The <xref:System.Xml.Serialization.XmlArrayAttribute> will determine the properties of the enclosing XML element that results when an array is serialized.</span></span> <span data-ttu-id="f9f35-117">Na przykład domyślnie poniżej tablicy serializowanie spowoduje — element XML o nazwie `Employees`.</span><span class="sxs-lookup"><span data-stu-id="f9f35-117">For example, by default, serializing the array below will result in an XML element named `Employees`.</span></span> <span data-ttu-id="f9f35-118">`Employees` Element będzie zawierać szereg elementów o nazwie po typ tablicy `Employee`.</span><span class="sxs-lookup"><span data-stu-id="f9f35-118">The `Employees` element will contain a series of elements named after the array type `Employee`.</span></span>  
  
```vb  
Public Class Group  
    Public Employees() As Employee  
End Class  
Public Class Employee  
    Public Name As String  
End Class  
```  
  
```csharp  
public class Group{  
    public Employee[] Employees;  
}  
public class Employee{  
    public string Name;  
}  
```  
  
 <span data-ttu-id="f9f35-119">Zserializowany wystąpienie może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f9f35-119">A serialized instance might resemble the following.</span></span>  
  
```xml  
<Group>  
<Employees>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
</Employees >  
</Group>  
```  
  
 <span data-ttu-id="f9f35-120">Stosując <xref:System.Xml.Serialization.XmlArrayAttribute>, nazwa elementu XML, można zmienić w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f9f35-120">By applying a <xref:System.Xml.Serialization.XmlArrayAttribute>, you can change the name of the XML element, as follows.</span></span>  
  
```vb  
Public Class Group  
    <XmlArray("TeamMembers")> _  
    Public Employees() As Employee  
End Class  
```  
  
```csharp  
public class Group{  
    [XmlArray("TeamMembers")]  
    public Employee[] Employees;  
}  
```  
  
 <span data-ttu-id="f9f35-121">Wynikowy kod XML może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f9f35-121">The resulting XML might resemble the following.</span></span>  
  
```xml  
<Group>  
<TeamMembers>  
    <Employee>  
        <Name>Haley</Name>  
    </Employee>  
</TeamMembers>  
```  
  
 <span data-ttu-id="f9f35-122"><xref:System.Xml.Serialization.XmlArrayItemAttribute>, Z drugiej strony, określa, jak są serializacji elementów znajdujących się w tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9f35-122">The <xref:System.Xml.Serialization.XmlArrayItemAttribute>, on the other hand, controls how the items contained in the array are serialized.</span></span> <span data-ttu-id="f9f35-123">Należy pamiętać, że atrybut jest stosowany do pola zwracanie tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9f35-123">Note that the attribute is applied to the field returning the array.</span></span>  
  
```vb  
Public Class Group  
    <XmlArrayItem("MemberName")> _  
    Public Employee() As Employees  
End Class  
```  
  
```csharp  
public class Group{  
    [XmlArrayItem("MemberName")]  
    public Employee[] Employees;  
}  
```  
  
 <span data-ttu-id="f9f35-124">Wynikowy kod XML może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f9f35-124">The resulting XML might resemble the following.</span></span>  
  
```xml  
<Group>  
<Employees>  
    <MemberName>Haley</MemberName>  
</Employees>  
</Group>  
```  
  
## <a name="serializing-derived-classes"></a><span data-ttu-id="f9f35-125">Klasy pochodne serializacji</span><span class="sxs-lookup"><span data-stu-id="f9f35-125">Serializing Derived Classes</span></span>  
 <span data-ttu-id="f9f35-126">Używanie innego <xref:System.Xml.Serialization.XmlArrayItemAttribute> jest umożliwienie serializacji w klasach pochodnych.</span><span class="sxs-lookup"><span data-stu-id="f9f35-126">Another use of the <xref:System.Xml.Serialization.XmlArrayItemAttribute> is to allow the serialization of derived classes.</span></span> <span data-ttu-id="f9f35-127">Na przykład innej klasy o nazwie `Manager` która pochodzi z `Employee` mogą być dodawane do poprzedniego przykładu.</span><span class="sxs-lookup"><span data-stu-id="f9f35-127">For example, another class named `Manager` that derives from `Employee` can be added to the previous example.</span></span> <span data-ttu-id="f9f35-128">Jeśli nie mają zastosowania <xref:System.Xml.Serialization.XmlArrayItemAttribute>, kod będzie działać w czasie wykonywania, ponieważ typ klasy pochodnej nie zostaną rozpoznane.</span><span class="sxs-lookup"><span data-stu-id="f9f35-128">If you do not apply the <xref:System.Xml.Serialization.XmlArrayItemAttribute>, the code will fail at run time because the derived class type will not be recognized.</span></span> <span data-ttu-id="f9f35-129">Aby rozwiązać ten problem, zastosuj atrybut dwa razy, każde ustawienie czasu <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> właściwości dla każdego typu akceptowalnego (podstawowych i pochodnych).</span><span class="sxs-lookup"><span data-stu-id="f9f35-129">To remedy this, apply the attribute twice, each time setting the <xref:System.Xml.Serialization.XmlArrayItemAttribute.Type%2A> property for each acceptable type (base and derived).</span></span>  
  
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
public class Group{  
    [XmlArrayItem(Type = typeof(Employee)),  
    XmlArrayItem(Type = typeof(Manager))]  
    public Employee[] Employees;  
}  
public class Employee{  
    public string Name;  
}  
public class Manager:Employee{  
    public int Level;  
}  
```  
  
 <span data-ttu-id="f9f35-130">Zserializowany wystąpienie może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f9f35-130">A serialized instance might resemble the following.</span></span>  
  
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
</Employees >  
</Group>  
```  
  
## <a name="serializing-an-array-as-a-sequence-of-elements"></a><span data-ttu-id="f9f35-131">Szeregowanie tablicę jako sekwencję elementów</span><span class="sxs-lookup"><span data-stu-id="f9f35-131">Serializing an Array as a Sequence of Elements</span></span>  
 <span data-ttu-id="f9f35-132">Tablica może serializować płaskiej sekwencję elementów XML, stosując <xref:System.Xml.Serialization.XmlElementAttribute> do pola zwracanie tablicy w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f9f35-132">You can also serialize an array as a flat sequence of XML elements by applying a <xref:System.Xml.Serialization.XmlElementAttribute> to the field returning the array as follows.</span></span>  
  
```vb  
Public Class Group  
    <XmlElement> _  
    Public Employees() As Employee  
End Class  
```  
  
```csharp  
public class Group{  
    [XmlElement]  
    public Employee[] Employees;  
}  
```  
  
 <span data-ttu-id="f9f35-133">Zserializowany wystąpienie może wyglądać w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f9f35-133">A serialized instance might resemble the following.</span></span>  
  
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
  
 <span data-ttu-id="f9f35-134">W inny sposób do odróżniania dwóch strumieni XML jest do generowania PLików dokumentów schematu XML (XSD) z skompilowany kod za pomocą narzędzia definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="f9f35-134">Another way to differentiate the two XML streams is to use the XML Schema Definition tool to generate the XML Schema (XSD) document files from the compiled code.</span></span> <span data-ttu-id="f9f35-135">(Aby uzyskać więcej informacji na temat używania narzędzia, zobacz [narzędzie definicji schematu XML i serializacja XML](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md).) Gdy atrybut nie jest stosowany do pola, schemat opisuje element w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f9f35-135">(For more details on using the tool, see [The XML Schema Definition Tool and XML Serialization](../../../docs/standard/serialization/the-xml-schema-definition-tool-and-xml-serialization.md).) When no attribute is applied to the field, the schema describes the element in the following manner.</span></span>  
  
```xml  
<xs:element minOccurs="0" maxOccurs ="1" name="Employees" type="ArrayOfEmployee" />  
```  
  
 <span data-ttu-id="f9f35-136">Gdy <xref:System.Xml.Serialization.XmlElementAttribute> jest stosowany do pola, wynikowy schematu Opisuje element w następujący sposób.</span><span class="sxs-lookup"><span data-stu-id="f9f35-136">When the <xref:System.Xml.Serialization.XmlElementAttribute> is applied to the field, the resulting schema describes the element as follows.</span></span>  
  
```xml  
<xs:element minOccurs="0" maxOccurs="unbounded" name="Employees" type="Employee" />   
```  
  
## <a name="serializing-an-arraylist"></a><span data-ttu-id="f9f35-137">Serializacji ArrayList</span><span class="sxs-lookup"><span data-stu-id="f9f35-137">Serializing an ArrayList</span></span>  
 <span data-ttu-id="f9f35-138"><xref:System.Collections.ArrayList> Klasy może zawierać kolekcji różnych obiektów.</span><span class="sxs-lookup"><span data-stu-id="f9f35-138">The <xref:System.Collections.ArrayList> class can contain a collection of diverse objects.</span></span> <span data-ttu-id="f9f35-139">Korzystając z tego powodu <xref:System.Collections.ArrayList> , ile skorzystaj z tablicy.</span><span class="sxs-lookup"><span data-stu-id="f9f35-139">You can therefore use a <xref:System.Collections.ArrayList> much as you use an array.</span></span> <span data-ttu-id="f9f35-140">Używaj pola, która zwraca tablicę obiektów określonego typu, jednak można utworzyć pole, które zwraca pojedynczą <xref:System.Collections.ArrayList>.</span><span class="sxs-lookup"><span data-stu-id="f9f35-140">Instead of creating a field that returns an array of typed objects, however, you can create a field that returns a single <xref:System.Collections.ArrayList>.</span></span> <span data-ttu-id="f9f35-141">Jednak, podobnie jak w przypadku tablic, musi powiadomić <xref:System.Xml.Serialization.XmlSerializer> typów obiektów <xref:System.Collections.ArrayList> zawiera.</span><span class="sxs-lookup"><span data-stu-id="f9f35-141">However, as with arrays, you must inform the <xref:System.Xml.Serialization.XmlSerializer> of the types of objects the <xref:System.Collections.ArrayList> contains.</span></span> <span data-ttu-id="f9f35-142">Aby to zrobić, należy przypisać wiele wystąpień <xref:System.Xml.Serialization.XmlElementAttribute> do pola, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f9f35-142">To accomplish this, assign multiple instances of the <xref:System.Xml.Serialization.XmlElementAttribute> to the field, as shown in the following example.</span></span>  
  
```vb  
Public Class Group  
    <XmlElement(Type:=GetType(Employee)), _  
    XmlElement(Type:=GetType(Manager))> _  
    Public Info As ArrayList  
End Class  
```  
  
```csharp  
public class Group{  
    [XmlElement(Type = typeof(Employee)),   
    XmlElement(Type = typeof(Manager))]  
    public ArrayList Info;  
}  
```  
  
## <a name="controlling-serialization-of-classes-using-xmlrootattribute-and-xmltypeattribute"></a><span data-ttu-id="f9f35-143">Kontrolowanie serializacji klas przy użyciu XmlRootAttribute i XmlTypeAttribute</span><span class="sxs-lookup"><span data-stu-id="f9f35-143">Controlling Serialization of Classes Using XmlRootAttribute and XmlTypeAttribute</span></span>  
 <span data-ttu-id="f9f35-144">Istnieją dwa atrybuty, które można zastosować do klasy (i tylko klasę): <xref:System.Xml.Serialization.XmlRootAttribute> i <xref:System.Xml.Serialization.XmlTypeAttribute>.</span><span class="sxs-lookup"><span data-stu-id="f9f35-144">There are two attributes that can be applied to a class (and only a class): <xref:System.Xml.Serialization.XmlRootAttribute> and <xref:System.Xml.Serialization.XmlTypeAttribute>.</span></span> <span data-ttu-id="f9f35-145">Te atrybuty są bardzo podobne.</span><span class="sxs-lookup"><span data-stu-id="f9f35-145">These attributes are very similar.</span></span> <span data-ttu-id="f9f35-146"><xref:System.Xml.Serialization.XmlRootAttribute> Może odnosić się tylko jedna klasa: klasa, że podczas serializacji, reprezentuje dokumentu XML na otwieranie i zamykanie elementu — innymi słowy, element główny.</span><span class="sxs-lookup"><span data-stu-id="f9f35-146">The <xref:System.Xml.Serialization.XmlRootAttribute> can be applied to only one class: the class that, when serialized, represents the XML document's opening and closing element—in other words, the root element.</span></span> <span data-ttu-id="f9f35-147"><xref:System.Xml.Serialization.XmlTypeAttribute>, W drugim ręcznie, mogą być stosowane do każdej klasy, w tym klasy głównym.</span><span class="sxs-lookup"><span data-stu-id="f9f35-147">The <xref:System.Xml.Serialization.XmlTypeAttribute>, on the other hand, can be applied to any class, including the root class.</span></span>  
  
 <span data-ttu-id="f9f35-148">Na przykład w poprzednich przykładach `Group` klasy jest klasy głównym, a jego pola publiczne i właściwości stają się znaleźć w dokumencie XML elementy XML.</span><span class="sxs-lookup"><span data-stu-id="f9f35-148">For example, in the previous examples, the `Group` class is the root class, and all its public fields and properties become the XML elements found in the XML document.</span></span> <span data-ttu-id="f9f35-149">Dlatego może być tylko jeden katalog główny klasy.</span><span class="sxs-lookup"><span data-stu-id="f9f35-149">Therefore, there can be only one root class.</span></span> <span data-ttu-id="f9f35-150">Stosując <xref:System.Xml.Serialization.XmlRootAttribute>, można kontrolować strumień XML wygenerowanych przez <xref:System.Xml.Serialization.XmlSerializer>.</span><span class="sxs-lookup"><span data-stu-id="f9f35-150">By applying the <xref:System.Xml.Serialization.XmlRootAttribute>, you can control the XML stream generated by the <xref:System.Xml.Serialization.XmlSerializer>.</span></span> <span data-ttu-id="f9f35-151">Na przykład można zmienić nazwy elementu i przestrzeń nazw.</span><span class="sxs-lookup"><span data-stu-id="f9f35-151">For example, you can change the element name and namespace.</span></span>  
  
 <span data-ttu-id="f9f35-152"><xref:System.Xml.Serialization.XmlTypeAttribute> Umożliwia sterowanie schemat wygenerowanego kodu XML.</span><span class="sxs-lookup"><span data-stu-id="f9f35-152">The <xref:System.Xml.Serialization.XmlTypeAttribute> allows you to control the schema of the generated XML.</span></span> <span data-ttu-id="f9f35-153">Ta funkcja jest przydatne, gdy należy opublikować schematu za pomocą usługi sieci Web XML.</span><span class="sxs-lookup"><span data-stu-id="f9f35-153">This capability is useful when you need to publish the schema through an XML Web service.</span></span> <span data-ttu-id="f9f35-154">Poniższy przykład dotyczy zarówno <xref:System.Xml.Serialization.XmlTypeAttribute> i <xref:System.Xml.Serialization.XmlRootAttribute> do tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="f9f35-154">The following example applies both the <xref:System.Xml.Serialization.XmlTypeAttribute> and the <xref:System.Xml.Serialization.XmlRootAttribute> to the same class.</span></span>  
  
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
public class Group{  
    public Employee[] Employees;  
}  
```  
  
 <span data-ttu-id="f9f35-155">Jeśli ta klasa jest skompilowana, a narzędzie definicji schematu XML jest używany do generowania jego schematu, czy okażą się następujące XML opisujący `Group`.</span><span class="sxs-lookup"><span data-stu-id="f9f35-155">If this class is compiled, and the XML Schema Definition tool is used to generate its schema, you would find the following XML describing `Group`.</span></span>  
  
```xml  
<xs:element name="NewGroupName" type="NewTypeName">  
```  
  
 <span data-ttu-id="f9f35-156">Z drugiej strony, jeśli zostały do serializacji wystąpienia klasy, tylko `NewGroupName` będzie można znaleźć w dokumencie XML.</span><span class="sxs-lookup"><span data-stu-id="f9f35-156">In contrast, if you were to serialize an instance of the class, only `NewGroupName` would be found in the XML document.</span></span>  
  
```xml  
<NewGroupName>  
    . . .  
</NewGroupName>  
```  
  
## <a name="preventing-serialization-with-the-xmlignoreattribute"></a><span data-ttu-id="f9f35-157">Zapobieganie serializacji z XmlIgnoreAttribute</span><span class="sxs-lookup"><span data-stu-id="f9f35-157">Preventing Serialization with the XmlIgnoreAttribute</span></span>  
 <span data-ttu-id="f9f35-158">Może to być sytuacje, gdy właściwość publiczna lub pola nie jest konieczne serializacji.</span><span class="sxs-lookup"><span data-stu-id="f9f35-158">There might be situations when a public property or field does not need to be serialized.</span></span> <span data-ttu-id="f9f35-159">Na przykład pole lub właściwość może służyć do zawierają metadanych.</span><span class="sxs-lookup"><span data-stu-id="f9f35-159">For example, a field or property could be used to contain metadata.</span></span> <span data-ttu-id="f9f35-160">W takiej sytuacji należy zastosować <xref:System.Xml.Serialization.XmlIgnoreAttribute> pola lub właściwości i <xref:System.Xml.Serialization.XmlSerializer> pominie go.</span><span class="sxs-lookup"><span data-stu-id="f9f35-160">In such cases, apply the <xref:System.Xml.Serialization.XmlIgnoreAttribute> to the field or property and the <xref:System.Xml.Serialization.XmlSerializer> will skip over it.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f9f35-161">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f9f35-161">See Also</span></span>  
 [<span data-ttu-id="f9f35-162">Atrybuty, które kontrolują serializacji XML</span><span class="sxs-lookup"><span data-stu-id="f9f35-162">Attributes That Control XML Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-xml-serialization.md)  
 [<span data-ttu-id="f9f35-163">Atrybuty, które sterowania serializacją użyciu zakodowanego protokołu SOAP</span><span class="sxs-lookup"><span data-stu-id="f9f35-163">Attributes That Control Encoded SOAP Serialization</span></span>](../../../docs/standard/serialization/attributes-that-control-encoded-soap-serialization.md)  
 [<span data-ttu-id="f9f35-164">Wprowadzenie do serializacji XML</span><span class="sxs-lookup"><span data-stu-id="f9f35-164">Introducing XML Serialization</span></span>](../../../docs/standard/serialization/introducing-xml-serialization.md)  
 [<span data-ttu-id="f9f35-165">Przykłady serializacji XML</span><span class="sxs-lookup"><span data-stu-id="f9f35-165">Examples of XML Serialization</span></span>](../../../docs/standard/serialization/examples-of-xml-serialization.md)  
 [<span data-ttu-id="f9f35-166">Porady: Określ nazwę elementu alternatywnego strumienia XML</span><span class="sxs-lookup"><span data-stu-id="f9f35-166">How to: Specify an Alternate Element Name for an XML Stream</span></span>](../../../docs/standard/serialization/how-to-specify-an-alternate-element-name-for-an-xml-stream.md)  
 [<span data-ttu-id="f9f35-167">Porady: szeregowania obiektu</span><span class="sxs-lookup"><span data-stu-id="f9f35-167">How to: Serialize an Object</span></span>](../../../docs/standard/serialization/how-to-serialize-an-object.md)  
 [<span data-ttu-id="f9f35-168">Porady: deserializacji obiektu</span><span class="sxs-lookup"><span data-stu-id="f9f35-168">How to: Deserialize an Object</span></span>](../../../docs/standard/serialization/how-to-deserialize-an-object.md)
