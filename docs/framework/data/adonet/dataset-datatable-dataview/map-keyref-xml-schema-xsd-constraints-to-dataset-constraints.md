---
title: Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 5b634fea-cc1e-4f6b-9454-10858105b1c8
ms.openlocfilehash: 86bc1961fb23b0b2f98a2849eaabd4eecd65cd64
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43777551"
---
# <a name="map-keyref-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="af9f4-102">Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="af9f4-102">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="af9f4-103">**Keyref** element umożliwia ustanowienie łączy między elementami w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="af9f4-103">The **keyref** element allows you to establish links between elements within a document.</span></span> <span data-ttu-id="af9f4-104">Jest to podobne do relacji klucza obcego w relacyjnej bazie danych.</span><span class="sxs-lookup"><span data-stu-id="af9f4-104">This is similar to a foreign key relationship in a relational database.</span></span> <span data-ttu-id="af9f4-105">Jeśli schemat określa **keyref** elementu, element jest konwertowany podczas procesu mapowania schematu do odpowiedniego ograniczenia klucza obcego dla kolumn w tabelach <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="af9f4-105">If a schema specifies the **keyref** element, the element is converted during the schema mapping process to a corresponding foreign key constraint on the columns in the tables of the <xref:System.Data.DataSet>.</span></span> <span data-ttu-id="af9f4-106">Domyślnie **keyref** element generuje również relacji z **ParentTable**, **ChildTable**, **ParentColumn**i  **ChildColumn** właściwości określone w relacji.</span><span class="sxs-lookup"><span data-stu-id="af9f4-106">By default, the **keyref** element also generates a relation, with the **ParentTable**, **ChildTable**, **ParentColumn**, and **ChildColumn** properties specified on the relation.</span></span>  
  
 <span data-ttu-id="af9f4-107">W poniższej tabeli przedstawiono **msdata** atrybuty, które można określić w **keyref** elementu.</span><span class="sxs-lookup"><span data-stu-id="af9f4-107">The following table outlines the **msdata** attributes you can specify in the **keyref** element.</span></span>  
  
|<span data-ttu-id="af9f4-108">Nazwa atrybutu</span><span class="sxs-lookup"><span data-stu-id="af9f4-108">Attribute name</span></span>|<span data-ttu-id="af9f4-109">Opis</span><span class="sxs-lookup"><span data-stu-id="af9f4-109">Description</span></span>|  
|--------------------|-----------------|  
|<span data-ttu-id="af9f4-110">**msdata:ConstraintOnly**</span><span class="sxs-lookup"><span data-stu-id="af9f4-110">**msdata:ConstraintOnly**</span></span>|<span data-ttu-id="af9f4-111">Jeśli **ConstraintOnly = "true"** jest określona w **keyref** elementu w schemacie, ograniczenie zostanie utworzony, ale żadna relacja jest tworzony.</span><span class="sxs-lookup"><span data-stu-id="af9f4-111">If **ConstraintOnly="true"** is specified on the **keyref** element in the schema, a constraint is created, but no relation is created.</span></span> <span data-ttu-id="af9f4-112">Jeśli ten atrybut nie jest określony (lub jest ustawiona na **False**), ograniczenia i relacji, które są tworzone w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="af9f4-112">If this attribute is not specified (or is set to **False**), both the constraint and the relation are created in the **DataSet**.</span></span>|  
|<span data-ttu-id="af9f4-113">**msdata:ConstraintName**</span><span class="sxs-lookup"><span data-stu-id="af9f4-113">**msdata:ConstraintName**</span></span>|<span data-ttu-id="af9f4-114">Jeśli **ConstraintName** atrybut jest określony, jego wartość jest używana jako nazwa ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="af9f4-114">If the **ConstraintName** attribute is specified, its value is used as the name of the constraint.</span></span> <span data-ttu-id="af9f4-115">W przeciwnym razie **nazwa** atrybutu **keyref** elementu w schemacie zawiera nazwę ograniczenia w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="af9f4-115">Otherwise, the **name** attribute of the **keyref** element in the schema provides the constraint name in the **DataSet**.</span></span>|  
|<span data-ttu-id="af9f4-116">**msdata:UpdateRule**</span><span class="sxs-lookup"><span data-stu-id="af9f4-116">**msdata:UpdateRule**</span></span>|<span data-ttu-id="af9f4-117">Jeśli **elementu UpdateRule** atrybut jest określony w **keyref** elementu w schemacie, jego wartość jest przypisywana do **elementu UpdateRule** właściwości ograniczenia w  **Zestaw danych**.</span><span class="sxs-lookup"><span data-stu-id="af9f4-117">If the **UpdateRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **UpdateRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="af9f4-118">W przeciwnym razie **elementu UpdateRule** właściwość jest ustawiona na **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="af9f4-118">Otherwise the **UpdateRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="af9f4-119">**msdata:DeleteRule**</span><span class="sxs-lookup"><span data-stu-id="af9f4-119">**msdata:DeleteRule**</span></span>|<span data-ttu-id="af9f4-120">Jeśli **DeleteRule** atrybut jest określony w **keyref** elementu w schemacie, jego wartość jest przypisywana do **DeleteRule** właściwości ograniczenia w  **Zestaw danych**.</span><span class="sxs-lookup"><span data-stu-id="af9f4-120">If the **DeleteRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **DeleteRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="af9f4-121">W przeciwnym razie **DeleteRule** właściwość jest ustawiona na **Cascade**.</span><span class="sxs-lookup"><span data-stu-id="af9f4-121">Otherwise the **DeleteRule** property is set to **Cascade**.</span></span>|  
|<span data-ttu-id="af9f4-122">**msdata:AcceptRejectRule**</span><span class="sxs-lookup"><span data-stu-id="af9f4-122">**msdata:AcceptRejectRule**</span></span>|<span data-ttu-id="af9f4-123">Jeśli **AcceptRejectRule** atrybut jest określony w **keyref** elementu w schemacie, jego wartość jest przypisywana do **AcceptRejectRule** ograniczenia właściwości  **Zestaw danych**.</span><span class="sxs-lookup"><span data-stu-id="af9f4-123">If the **AcceptRejectRule** attribute is specified in the **keyref** element in the schema, its value is assigned to the **AcceptRejectRule** constraint property in the **DataSet**.</span></span> <span data-ttu-id="af9f4-124">W przeciwnym razie **AcceptRejectRule** właściwość jest ustawiona na **Brak**.</span><span class="sxs-lookup"><span data-stu-id="af9f4-124">Otherwise the **AcceptRejectRule** property is set to **None**.</span></span>|  
  
 <span data-ttu-id="af9f4-125">Poniższy przykład zawiera schemat, który określa **klucz** i **keyref** relacje między **OrderNumber** element podrzędny elementu **zamówienia**  elementu i **OrderNo** element podrzędny elementu **OrderDetail** elementu.</span><span class="sxs-lookup"><span data-stu-id="af9f4-125">The following example contains a schema that specifies the **key** and **keyref** relationships between the **OrderNumber** child element of the **Order** element and the **OrderNo** child element of the **OrderDetail** element.</span></span>  
  
 <span data-ttu-id="af9f4-126">W tym przykładzie **OrderNumber** element podrzędny elementu **OrderDetail** element odwołuje się do **OrderNo** element podrzędny klucza **kolejności**elementu.</span><span class="sxs-lookup"><span data-stu-id="af9f4-126">In the example, the **OrderNumber** child element of the **OrderDetail** element refers to the **OrderNo** key child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="af9f4-127">Proces mapowania schematu języka (XSD) definicji schematu XML generuje następujące **DataSet** z dwoma tabelami:</span><span class="sxs-lookup"><span data-stu-id="af9f4-127">The XML Schema definition language (XSD) schema mapping process produces the following **DataSet** with two tables:</span></span>  
  
```  
OrderDetail(OrderNo, ItemNo) and  
Order(OrderNumber, EmpNumber)  
```  
  
 <span data-ttu-id="af9f4-128">Ponadto **DataSet** definiuje następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="af9f4-128">In addition, the **DataSet** defines the following constraints:</span></span>  
  
-   <span data-ttu-id="af9f4-129">Ograniczenia unique wobec **kolejności** tabeli.</span><span class="sxs-lookup"><span data-stu-id="af9f4-129">A unique constraint on the **Order** table.</span></span>  
  
    ```  
              Table: Order  
    Columns: OrderNumber   
    ConstraintName: OrderNumberKey  
    Type: UniqueConstraint  
    IsPrimaryKey: False  
    ```  
  
-   <span data-ttu-id="af9f4-130">Relacja między **kolejności** i **OrderDetail** tabel.</span><span class="sxs-lookup"><span data-stu-id="af9f4-130">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="af9f4-131">**Zagnieżdżone** właściwość jest ustawiona na **False** ponieważ dwa elementy nie są zagnieżdżone w schemacie.</span><span class="sxs-lookup"><span data-stu-id="af9f4-131">The **Nested** property is set to **False** because the two elements are not nested in the schema.</span></span>  
  
    ```  
              ParentTable: Order  
    ParentColumns: OrderNumber   
    ChildTable: OrderDetail  
    ChildColumns: OrderNo   
    ParentKeyConstraint: OrderNumberKey  
    ChildKeyConstraint: OrderNoRef  
    RelationName: OrderNoRef  
    Nested: False  
    ```  
  
-   <span data-ttu-id="af9f4-132">Ograniczenie klucza obcego w **OrderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="af9f4-132">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
              ConstraintName: OrderNoRef  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: OrderNo   
    RelatedTable: Order  
    RelatedColumns: OrderNumber   
    ```  
  
## <a name="see-also"></a><span data-ttu-id="af9f4-133">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="af9f4-133">See Also</span></span>  
 [<span data-ttu-id="af9f4-134">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="af9f4-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="af9f4-135">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="af9f4-135">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="af9f4-136">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="af9f4-136">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
