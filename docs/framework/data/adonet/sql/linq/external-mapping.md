---
title: Mapowanie zewnętrzne
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: ba5af75ae34b233354fec6e9074f3cc96d924c7f
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/07/2019
ms.locfileid: "72003046"
---
# <a name="external-mapping"></a>Mapowanie zewnętrzne
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje *Mapowanie zewnętrzne*, proces, za pomocą którego można określić mapowanie między modelem danych bazy danych i modelem obiektu. Zalety korzystania z zewnętrznego pliku mapowania są następujące:  
  
- Kod mapowania można zachować poza kodem aplikacji. Takie podejście zmniejsza czytelność kodu aplikacji.  
  
- Plik mapowania zewnętrznego można traktować jako plik konfiguracji. Można na przykład zaktualizować działanie aplikacji po dostarczeniu plików binarnych przez zamienienie pliku mapowania zewnętrznego.  
  
## <a name="requirements"></a>Wymagania  
 Plik mapowania musi być plikiem XML, a plik musi być sprawdzony przy użyciu pliku definicji schematu [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] (XSD).  
  
 Mają zastosowanie następujące zasady:  
  
- Plik mapowania musi być plikiem XML.  
  
- Plik mapowania XML musi być prawidłowy względem pliku definicji schematu XML. Aby uzyskać więcej informacji, zobacz [jak: sprawdzanie poprawności DBML i plików mapowania zewnętrznego](how-to-validate-dbml-and-external-mapping-files.md).  
  
- Mapowanie zewnętrzne zastępuje mapowanie oparte na atrybutach. Innymi słowy, jeśli używasz zewnętrznego źródła mapowania do tworzenia <xref:System.Data.Linq.DataContext>, <xref:System.Data.Linq.DataContext> ignoruje wszystkie atrybuty mapowania utworzone dla klas. To zachowanie jest prawdziwe, niezależnie od tego, czy Klasa jest uwzględniona w zewnętrznym pliku mapowania.  
  
- [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje użycia hybrydowego dwóch metod mapowania (opartych na atrybutach i zewnętrznych).  
  
## <a name="xml-schema-definition-file"></a>Plik definicji schematu XML  
 Mapowanie zewnętrzne w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musi być prawidłowe względem następującej definicji schematu XML.  
  
 Odróżnij ten plik definicji schematu od pliku definicji schematu, który jest używany do walidacji pliku DBML. Aby uzyskać więcej informacji, zobacz [generowanie kodu w LINQ to SQL](code-generation-in-linq-to-sql.md)).  
  
> [!NOTE]
> Użytkownicy programu Visual Studio również znajdą ten plik XSD w oknie dialogowym schematy XML jako "LinqToSqlMapping. xsd". Aby prawidłowo użyć tego pliku do walidacji pliku mapowania zewnętrznego, zobacz [How to: Validate DBML and External Mapping Files](how-to-validate-dbml-and-external-mapping-files.md).  
  
```xml  
<?xml version="1.0" encoding="utf-16"?>  
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
  
## <a name="see-also"></a>Zobacz także

- [Generowanie kodu w składniku LINQ to SQL](code-generation-in-linq-to-sql.md)
- [Tematy pomocy](reference.md)
- [Instrukcje: Generowanie modelu obiektu jako zewnętrznego pliku](how-to-generate-the-object-model-as-an-external-file.md)
