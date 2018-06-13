---
title: Mapowanie zewnętrznych
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 640dff5555ab346782825c44ded758a681226648
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33365218"
---
# <a name="external-mapping"></a><span data-ttu-id="7cdcd-102">Mapowanie zewnętrznych</span><span class="sxs-lookup"><span data-stu-id="7cdcd-102">External Mapping</span></span>
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7cdcd-103"> obsługuje *zewnętrznych mapowania*, proces, za pomocą której używasz oddzielny plik XML do określenia mapowania między modelu danych, bazy danych i modelu obiektu.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-103"> supports *external mapping*, a process by which you use a separate XML file to specify mapping between the data model of the database and your object model.</span></span> <span data-ttu-id="7cdcd-104">Korzyści wynikające z używania pliku mapowania zewnętrzne są następujące:</span><span class="sxs-lookup"><span data-stu-id="7cdcd-104">Advantages of using an external mapping file include the following:</span></span>  
  
-   <span data-ttu-id="7cdcd-105">Poza kod aplikacji, można zachować mapowania kodu.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-105">You can keep your mapping code out of your application code.</span></span> <span data-ttu-id="7cdcd-106">Takie podejście upraszcza w kodzie aplikacji.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-106">This approach reduces clutter in your application code.</span></span>  
  
-   <span data-ttu-id="7cdcd-107">Można traktować plik mapowania zewnętrznych coś, takich jak plik konfiguracji.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-107">You can treat an external mapping file something like a configuration file.</span></span> <span data-ttu-id="7cdcd-108">Na przykład można zaktualizować zachowania aplikacji po wysyłania plików binarnych przez właśnie zastępowaniu plik mapowania zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-108">For example, you can update how your application behaves after shipping the binaries by just swapping out the external mapping file.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7cdcd-109">Wymagania</span><span class="sxs-lookup"><span data-stu-id="7cdcd-109">Requirements</span></span>  
 <span data-ttu-id="7cdcd-110">Plik mapowania musi być plikiem formatu XML, a plik musi sprawdzania poprawności [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schematu pliku definicji (XSD).</span><span class="sxs-lookup"><span data-stu-id="7cdcd-110">The mapping file must be an XML file, and the file must validate against a [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] schema definition (.xsd) file.</span></span>  
  
 <span data-ttu-id="7cdcd-111">Mają zastosowanie następujące zasady:</span><span class="sxs-lookup"><span data-stu-id="7cdcd-111">The following rules apply:</span></span>  
  
-   <span data-ttu-id="7cdcd-112">Plik mapowania musi być plikiem formatu XML.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-112">The mapping file must be an XML file.</span></span>  
  
-   <span data-ttu-id="7cdcd-113">Plik mapowania XML musi być prawidłowa względem pliku definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-113">The XML mapping file must be valid against the XML schema definition file.</span></span> <span data-ttu-id="7cdcd-114">Aby uzyskać więcej informacji, zobacz [porady: Sprawdzanie poprawności DBML i mapowania plików zewnętrznych](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="7cdcd-114">For more information, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
-   <span data-ttu-id="7cdcd-115">Mapowanie zewnętrznych przesłania mapowania na podstawie atrybutów.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-115">External mapping overrides attribute-based mapping.</span></span> <span data-ttu-id="7cdcd-116">Innymi słowy, jeśli używasz źródła zewnętrznego mapowania do utworzenia <xref:System.Data.Linq.DataContext>, <xref:System.Data.Linq.DataContext> ignoruje wszystkie atrybuty mapowania, które zostały utworzone w klasach.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-116">In other words, when you use an external mapping source to create a <xref:System.Data.Linq.DataContext>, the <xref:System.Data.Linq.DataContext> ignores all mapping attributes you have created on classes.</span></span> <span data-ttu-id="7cdcd-117">To zachowanie jest spełniony, czy klasa znajduje się w pliku mapowania zewnętrznych.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-117">This behavior is true whether the class is included in the external mapping file.</span></span>  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)]<span data-ttu-id="7cdcd-118"> nie obsługuje użycia hybrydowego dwa podejścia mapowania (na podstawie atrybutów i zewnętrznych).</span><span class="sxs-lookup"><span data-stu-id="7cdcd-118"> does not support the hybrid use of the two mapping approaches (attribute-based and external).</span></span>  
  
## <a name="xml-schema-definition-file"></a><span data-ttu-id="7cdcd-119">Plik definicji schematu XML</span><span class="sxs-lookup"><span data-stu-id="7cdcd-119">XML Schema Definition File</span></span>  
 <span data-ttu-id="7cdcd-120">Mapowanie zewnętrznych w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musi być prawidłowa względem następującą definicję schematu XML.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-120">External mapping in [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] must be valid against the following XML schema definition.</span></span>  
  
 <span data-ttu-id="7cdcd-121">Odróżnić ten plik definicji schematu z pliku definicji schematu, który jest używany do sprawdzania poprawności za pomocą pliku DBML.</span><span class="sxs-lookup"><span data-stu-id="7cdcd-121">Distinguish this schema definition file from the schema definition file that is used to validate a DBML file.</span></span> <span data-ttu-id="7cdcd-122">Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span><span class="sxs-lookup"><span data-stu-id="7cdcd-122">For more information, see [Code Generation in LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7cdcd-123">Użytkowników programu Visual Studio będzie również znaleźć tego pliku XSD w oknie dialogowym schematów XML jako "LinqToSqlMapping.xsd".</span><span class="sxs-lookup"><span data-stu-id="7cdcd-123">Visual Studio users will also find this XSD file in the XML Schemas dialog box as "LinqToSqlMapping.xsd".</span></span> <span data-ttu-id="7cdcd-124">Używanie tego pliku poprawnie sprawdzania poprawności pliku mapowania zewnętrznych, zobacz [porady: Sprawdzanie poprawności DBML i plików zewnętrznych mapowania](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span><span class="sxs-lookup"><span data-stu-id="7cdcd-124">To use this file correctly for validating an external mapping file, see [How to: Validate DBML and External Mapping Files](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="7cdcd-125">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7cdcd-125">See Also</span></span>  
 [<span data-ttu-id="7cdcd-126">Generowanie kodu w składniku LINQ to SQL</span><span class="sxs-lookup"><span data-stu-id="7cdcd-126">Code Generation in LINQ to SQL</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)  
 [<span data-ttu-id="7cdcd-127">Dokumentacja</span><span class="sxs-lookup"><span data-stu-id="7cdcd-127">Reference</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)  
 [<span data-ttu-id="7cdcd-128">Instrukcje: Generowanie modelu obiektu jako zewnętrznego pliku</span><span class="sxs-lookup"><span data-stu-id="7cdcd-128">How to: Generate the Object Model as an External File</span></span>](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)
