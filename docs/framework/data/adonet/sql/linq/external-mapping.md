---
title: Mapowanie zewnętrzne
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 70372473eb2de5d3c4751e237e7beb66315b690e
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950328"
---
# <a name="external-mapping"></a><span data-ttu-id="0aace-102">Mapowanie zewnętrzne</span><span class="sxs-lookup"><span data-stu-id="0aace-102">External Mapping</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0aace-103">obsługuje *Mapowanie zewnętrzne*, proces, za pomocą którego używany jest osobny plik XML do określenia mapowania między modelem danych bazy danych i modelem obiektu.</span><span class="sxs-lookup"><span data-stu-id="0aace-103">supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="0aace-104">Zalety korzystania z zewnętrznego pliku mapowania są następujące:</span><span class="sxs-lookup"><span data-stu-id="0aace-104">Advantages of using an external mapping file include the following:</span></span>  
  
- <span data-ttu-id="0aace-105">Kod mapowania można zachować poza kodem aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0aace-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="0aace-106">Takie podejście zmniejsza czytelność kodu aplikacji.</span><span class="sxs-lookup"><span data-stu-id="0aace-106">This approach reduces clutter in your application code.</span></span>  
  
- <span data-ttu-id="0aace-107">Plik mapowania zewnętrznego można traktować jako plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="0aace-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="0aace-108">Można na przykład zaktualizować działanie aplikacji po dostarczeniu plików binarnych przez zamienienie pliku mapowania zewnętrznego.</span><span class="sxs-lookup"><span data-stu-id="0aace-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="0aace-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="0aace-109">Requirements</span></span>  
 <span data-ttu-id="0aace-110">Plik mapowania musi być plikiem XML, a plik musi być zweryfikowany względem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pliku definicji schematu (XSD).</span><span class="sxs-lookup"><span data-stu-id="0aace-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="0aace-111">Mają zastosowanie następujące zasady:</span><span class="sxs-lookup"><span data-stu-id="0aace-111">The following rules apply:</span></span>  
  
- <span data-ttu-id="0aace-112">Plik mapowania musi być plikiem XML.</span><span class="sxs-lookup"><span data-stu-id="0aace-112">The mapping file must be an XML file.</span></span>  
  
- <span data-ttu-id="0aace-113">Plik mapowania XML musi być prawidłowy względem pliku definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="0aace-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="0aace-114">Aby uzyskać więcej informacji, zobacz [jak: Sprawdź poprawność DBML i](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)zewnętrznych plików mapowania.</span><span class="sxs-lookup"><span data-stu-id="0aace-114">For more information, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
- <span data-ttu-id="0aace-115">Mapowanie zewnętrzne zastępuje mapowanie oparte na atrybutach.</span><span class="sxs-lookup"><span data-stu-id="0aace-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="0aace-116">Innymi słowy, jeśli używasz zewnętrznego źródła mapowania do tworzenia <xref:System.Data.Linq.DataContext> <xref:System.Data.Linq.DataContext> , ignoruje wszystkie atrybuty mapowania, które zostały utworzone dla klas.</span><span class="sxs-lookup"><span data-stu-id="0aace-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="0aace-117">To zachowanie jest prawdziwe, niezależnie od tego, czy Klasa jest uwzględniona w zewnętrznym pliku mapowania.</span><span class="sxs-lookup"><span data-stu-id="0aace-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="0aace-118">nie obsługuje użycia hybrydowego dwóch metod mapowania (opartych na atrybutach i zewnętrznych).</span><span class="sxs-lookup"><span data-stu-id="0aace-118">does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="0aace-119">Plik definicji schematu XML</span><span class="sxs-lookup"><span data-stu-id="0aace-119">XML Schema Definition File</span></span>  
 <span data-ttu-id="0aace-120">Mapowanie zewnętrzne w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] programie musi być prawidłowe względem następującej definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="0aace-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="0aace-121">Odróżnij ten plik definicji schematu od pliku definicji schematu, który jest używany do walidacji pliku DBML.</span><span class="sxs-lookup"><span data-stu-id="0aace-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="0aace-122">Aby uzyskać więcej informacji, zobacz [generowanie kodu w LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="0aace-122">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="0aace-123">Użytkownicy programu Visual Studio również znajdą ten plik XSD w oknie dialogowym schematy XML jako "LinqToSqlMapping. xsd".</span><span class="sxs-lookup"><span data-stu-id="0aace-123">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="0aace-124">Aby prawidłowo użyć tego pliku do walidacji pliku mapowania zewnętrznego, zobacz [How to: Sprawdź poprawność DBML i](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md)zewnętrznych plików mapowania.</span><span class="sxs-lookup"><span data-stu-id="0aace-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
```  
?<?xml version="1.0" encoding="utf-16"?>  
<xs:schema xmlns:xs="http://www.w3.org/2001/XMLSchema" targetNamespace="http://schemas.microsoft.com/linqtosql/mapping/2007" xmlns="http://schemas.microsoft.com/linqtosql/mapping/2007"  
elementFormDefault="qualified" >  
  <xs:element name="Database" type="Database" />  
  <xs:complexType name="Database">  
    <xs:sequence>  
      <xs:element name="Table" type="Table" minOccurs="0" maxOccurs="unbounded" />  
      <xs:element name="Function" type="Function" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Provider" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Table">  
    <xs:sequence>  
      <xs:element name="Type" type="Type" minOccurs="1" maxOccurs="1" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Type">  
    <xs:sequence>  
      <xs:choice minOccurs="0" maxOccurs="unbounded">  
        <xs:element name="Column" type="Column" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Association" type="Association" minOccurs="0" maxOccurs="unbounded" />  
      </xs:choice>  
      <xs:element name="Type" type="Type" minOccurs="0" maxOccurs="unbounded" />  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="required" />  
    <xs:attribute name="InheritanceCode" type="xs:string" use="optional" />  
    <xs:attribute name="IsInheritanceDefault" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Column">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="IsPrimaryKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsDbGenerated" type="xs:boolean" use="optional" />  
    <xs:attribute name="CanBeNull" type="xs:boolean" use="optional" />  
    <xs:attribute name="UpdateCheck" type="UpdateCheck" use="optional" />  
    <xs:attribute name="IsDiscriminator" type="xs:boolean" use="optional" />  
    <xs:attribute name="Expression" type="xs:string" use="optional" />  
    <xs:attribute name="IsVersion" type="xs:boolean" use="optional" />  
    <xs:attribute name="AutoSync" type="AutoSync" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Association">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Member" type="xs:string" use="required" />  
    <xs:attribute name="Storage" type="xs:string" use="optional" />  
    <xs:attribute name="ThisKey" type="xs:string" use="optional" />  
    <xs:attribute name="OtherKey" type="xs:string" use="optional" />  
    <xs:attribute name="IsForeignKey" type="xs:boolean" use="optional" />  
    <xs:attribute name="IsUnique" type="xs:boolean" use="optional" />  
    <xs:attribute name="DeleteRule" type="xs:string" use="optional" />  
    <xs:attribute name="DeleteOnNull" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Function">  
    <xs:sequence>  
      <xs:element name="Parameter" type="Parameter" minOccurs="0" maxOccurs="unbounded" />  
      <xs:choice>  
        <xs:element name="ElementType" type="Type" minOccurs="0" maxOccurs="unbounded" />  
        <xs:element name="Return" type="Return" minOccurs="0" maxOccurs="1" />  
      </xs:choice>  
    </xs:sequence>  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Method" type="xs:string" use="required" />  
    <xs:attribute name="IsComposable" type="xs:boolean" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Parameter">  
    <xs:attribute name="Name" type="xs:string" use="optional" />  
    <xs:attribute name="Parameter" type="xs:string" use="required" />  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
    <xs:attribute name="Direction" type="ParameterDirection" use="optional" />  
  </xs:complexType>  
  <xs:complexType name="Return">  
    <xs:attribute name="DbType" type="xs:string" use="optional" />  
  </xs:complexType>  
  <xs:simpleType name="UpdateCheck">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="WhenChanged" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="ParameterDirection">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="In" />  
      <xs:enumeration value="Out" />  
      <xs:enumeration value="InOut" />  
    </xs:restriction>  
  </xs:simpleType>  
  <xs:simpleType name="AutoSync">  
    <xs:restriction base="xs:string">  
      <xs:enumeration value="Never" />  
      <xs:enumeration value="OnInsert" />  
      <xs:enumeration value="OnUpdate" />  
      <xs:enumeration value="Always" />  
      <xs:enumeration value="Default" />  
    </xs:restriction>  
  </xs:simpleType>  
</xs:schema>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0aace-125">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="0aace-125">See also</span></span>

- [<span data-ttu-id="0aace-126">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="0aace-126">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [<span data-ttu-id="0aace-127">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="0aace-127">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [<span data-ttu-id="0aace-128">Instrukcje: Generuj model obiektów jako plik zewnętrzny</span><span class="sxs-lookup"><span data-stu-id="0aace-128">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)
