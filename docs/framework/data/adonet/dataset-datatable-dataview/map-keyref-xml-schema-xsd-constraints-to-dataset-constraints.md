---
title: Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 93f766003326fd41357581196015fd58c71d7508
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73040367"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="1bcd2-102">Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="1bcd2-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="1bcd2-103">Element **keyref** umożliwia ustanowienie linków między elementami w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="1bcd2-104">Jest to podobne do relacji klucza obcego w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="1bcd2-105">Jeśli schemat określa element **keyref** , element jest konwertowany podczas procesu mapowania schematu do odpowiedniego ograniczenia klucza obcego w kolumnach w tabelach <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="1bcd2-106">Domyślnie element **keyref** również generuje relację z właściwościami **Parent**, **Child**, **ParentColumn**i **ChildColumn** określonymi w relacji.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="1bcd2-107">Poniższa tabela zawiera opis atrybutów **msdata** , które można określić w elemencie **keyref** .</span><span class="sxs-lookup"><span data-stu-id="1bcd2-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="1bcd2-108">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="1bcd2-108">Attribute name</span></span>|<span data-ttu-id="1bcd2-109">Opis</span><span class="sxs-lookup"><span data-stu-id="1bcd2-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="1bcd2-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="1bcd2-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="1bcd2-111">Jeśli **ConstraintOnly = "true"** jest określony w elemencie **keyref** w schemacie, zostanie utworzone ograniczenie, ale nie jest tworzone żadne powiązanie.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="1bcd2-112">Jeśli ten atrybut nie jest określony (lub jest ustawiony na **wartość false**), zarówno ograniczenie, jak i relacja są tworzone w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="1bcd2-113">**msdata: ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="1bcd2-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="1bcd2-114">Jeśli określono atrybut **ConstraintName** , jego wartość jest używana jako nazwa ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="1bcd2-115">W przeciwnym razie atrybut **name** elementu **keyref** w schemacie zawiera nazwę ograniczenia w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="1bcd2-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="1bcd2-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="1bcd2-117">Jeśli atrybut **UpdateRule** jest określony w elemencie **keyref** w schemacie, jego wartość jest przypisywana do właściwości ograniczenia **UpdateRule** w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="1bcd2-118">W przeciwnym razie Właściwość **UpdateRule** jest ustawiona na **Kaskada**.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="1bcd2-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="1bcd2-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="1bcd2-120">Jeśli atrybut **DeleteRule** jest określony w elemencie **keyref** w schemacie, jego wartość jest przypisywana do właściwości ograniczenia **DeleteRule** w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="1bcd2-121">W przeciwnym razie Właściwość **DeleteRule** jest ustawiona na **Kaskada**.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="1bcd2-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="1bcd2-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="1bcd2-123">Jeśli atrybut **AcceptRejectRule** jest określony w elemencie **keyref** w schemacie, jego wartość jest przypisywana do właściwości ograniczenia **AcceptRejectRule** w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="1bcd2-124">W przeciwnym razie Właściwość **AcceptRejectRule** ma wartość **none**.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="1bcd2-125">Poniższy przykład zawiera schemat, który określa relacje **Key** i **keyref** między elementem podrzędnym **OrderNumber** elementu **Order** i elementem podrzędnym **OrderNo** **OrderDetail** postaci.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="1bcd2-126">W przykładzie element podrzędny **OrderNumber** elementu **OrderDetail** odwołuje się do elementu podrzędnego klucza **OrderNo** elementu **Order** .</span><span class="sxs-lookup"><span data-stu-id="1bcd2-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
      <xs:element name="OrderDetail">  
       <xs:complexType>  
         <xs:sequence>  
           <xs:element name="OrderNo" type="xs:integer" />  
           <xs:element name="ItemNo" type="xs:string" />  
         </xs:sequence>  
       </xs:complexType>  
      </xs:element>  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
          </xs:sequence>  
        </xs:complexType>  
      </xs:element>  
    </xs:choice>  
  </xs:complexType>  
  
  <xs:key name="OrderNumberKey"  >  
    <xs:selector xpath=".//Order" />  
    <xs:field xpath="OrderNumber" />  
  </xs:key>  
  
  <xs:keyref name="OrderNoRef" refer="OrderNumberKey">  
    <xs:selector xpath=".//OrderDetail" />  
    <xs:field xpath="OrderNo" />  
  </xs:keyref>  
 </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="1bcd2-127">Proces mapowania schematu języka definicji schematu XML (XSD) generuje następujący **zestaw danych** z dwiema tabelami:</span><span class="sxs-lookup"><span data-stu-id="1bcd2-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```text  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="1bcd2-128">Ponadto **zestaw danych** definiuje następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="1bcd2-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
- <span data-ttu-id="1bcd2-129">Unikatowe ograniczenie tabeli **Order** .</span><span class="sxs-lookup"><span data-stu-id="1bcd2-129">A unique constraint on the **Order** table.</span></span>  
  
    ```text
              Table: Order  
    Columns: OrderNumber
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
- <span data-ttu-id="1bcd2-130">Relacja między tabelami **Order** i **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="1bcd2-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="1bcd2-131">Właściwość **zagnieżdżona** jest ustawiona na **false** , ponieważ dwa elementy nie są zagnieżdżone w schemacie.</span><span class="sxs-lookup"><span data-stu-id="1bcd2-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```text
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
- <span data-ttu-id="1bcd2-132">Ograniczenie klucza obcego w tabeli **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="1bcd2-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo
    RelatedTable: Order  
    RelatedColumns: OrderNumber
    ```  
  
## <a name="see-also"></a><span data-ttu-id="1bcd2-133">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1bcd2-133">See also</span></span>

- [<span data-ttu-id="1bcd2-134">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="1bcd2-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="1bcd2-135">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="1bcd2-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="1bcd2-136">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="1bcd2-136">ADO.NET Overview</span></span>](../ado-net-overview.md)
