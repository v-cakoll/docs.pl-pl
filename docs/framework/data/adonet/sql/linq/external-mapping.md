---
title: Mapowanie zewnętrzne
ms.date: 03/30/2017
ms.assetid: 076606b8-d889-4ba0-b5da-ae577b146f23
ms.openlocfilehash: 4b493279307f61847b72048c5bfa9dc14a38fe29
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218683"
---
# <a name="external-mapping"></a>Mapowanie zewnętrzne
[!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] obsługuje *mapowanie zewnętrzne*, za pomocą którego używasz oddzielnego pliku XML, aby określić mapowanie między modelu danych, bazy danych i modelu obiektu procesu. Korzyści wynikające z używania pliku mapowanie zewnętrzne są następujące:  
  
-   Poza swój kod aplikacji, należy dysponować mapowania kodu. Takie podejście zmniejsza nieładu w kodzie aplikacji.  
  
-   Można traktować plik mapowania zewnętrznych podobny do tego pliku konfiguracji. Na przykład należy zaktualizować, jak aplikacja zachowuje się po wysyłania plików binarnych, po prostu zastępowaniu pliku mapowania zewnętrznych.  
  
## <a name="requirements"></a>Wymagania  
 Plik mapowania musi być plikiem formatu XML, a plik musi przeprowadzić walidacji względem [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] pliku (XSD) definicji schematu.  
  
 Mają zastosowanie następujące zasady:  
  
-   Plik mapowania musi być plikiem XML.  
  
-   Plik mapowania XML musi być prawidłowy względem pliku definicji schematu XML. Aby uzyskać więcej informacji, zobacz [jak: Weryfikacja DBML i zewnętrznych plików mapowania](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).  
  
-   Mapowanie zewnętrzne zastępuje mapowanie oparte na atrybutach. Oznacza to, kiedy używasz mapowanie zewnętrzne źródło do utworzenia <xref:System.Data.Linq.DataContext>, <xref:System.Data.Linq.DataContext> ignoruje wszystkie atrybuty mapowania, które zostały utworzone w klasach. To zachowanie ma wartość true, czy klasa znajduje się w pliku mapowania zewnętrznych.  
  
-   [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] nie obsługuje użycie hybrydowego dwa podejścia mapowanie (oparte na atrybutach i zewnętrznych).  
  
## <a name="xml-schema-definition-file"></a>Plik definicji schematu XML  
 Mapowanie zewnętrzne w [!INCLUDE[vbtecdlinq](../../../../../../includes/vbtecdlinq-md.md)] musi być prawidłowy względem następujących definicji schematu XML.  
  
 Rozróżnia ten plik definicji schematu z pliku definicji schematu, który służy do sprawdzania poprawności za pomocą pliku DBML. Aby uzyskać więcej informacji, zobacz [generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)).  
  
> [!NOTE]
>  Użytkowników usługi Visual Studio również znaleźć tego pliku XSD w oknie dialogowym schematów XML jako "LinqToSqlMapping.xsd". Aby użyć tego pliku poprawnie dotyczące weryfikacji pliku mapowania zewnętrznych, zobacz [jak: Weryfikacja DBML i zewnętrznych plików mapowania](../../../../../../docs/framework/data/adonet/sql/linq/how-to-validate-dbml-and-external-mapping-files.md).  
  
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
  
## <a name="see-also"></a>Zobacz także

- [Generowanie kodu w składniku LINQ to SQL](../../../../../../docs/framework/data/adonet/sql/linq/code-generation-in-linq-to-sql.md)
- [Dokumentacja](../../../../../../docs/framework/data/adonet/sql/linq/reference.md)
- [Instrukcje: Generowanie modelu obiektu jako zewnętrznego pliku](../../../../../../docs/framework/data/adonet/sql/linq/how-to-generate-the-object-model-as-an-external-file.md)
