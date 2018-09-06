---
title: Relacje i ograniczenia schematu XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: bcb6e257a40040701612b73768a98e056bccd6c5
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43785615"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="a1db9-102">Relacje i ograniczenia schematu XML</span><span class="sxs-lookup"><span data-stu-id="a1db9-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="a1db9-103">W schemacie języka (XSD) definicji schematu XML można określić ograniczenia (unikatowe, klucza i ograniczeń keyref) i relacji (przy użyciu **msdata:Relationship** adnotacji).</span><span class="sxs-lookup"><span data-stu-id="a1db9-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="a1db9-104">W tym temacie wyjaśniono, jak interpretować ograniczenia i relacji określony w schemacie XML do generowania <xref:System.Data.DataSet>.</span><span class="sxs-lookup"><span data-stu-id="a1db9-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="a1db9-105">Ogólnie rzecz biorąc, w schematu XML, należy określić **msdata:Relationship** adnotacji, jeśli chcesz wygenerować tylko relacje w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="a1db9-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="a1db9-106">Aby uzyskać więcej informacji, zobacz [Generowanie relacji elementu DataSet ze schematu XML (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="a1db9-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="a1db9-107">Określ ograniczenia (unikatowe, klucza i keyref) Jeśli chcesz wygenerować ograniczeń **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="a1db9-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="a1db9-108">Należy pamiętać, że ograniczenia klucza i keyref również są używane do generowania relacji, zgodnie z opisem w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="a1db9-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="a1db9-109">Generowanie relacji z kluczem i ograniczeń keyref</span><span class="sxs-lookup"><span data-stu-id="a1db9-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="a1db9-110">Zamiast określania **msdata:Relationship** adnotacji, można określić klucz i keyref ograniczeń, które są używane w procesie mapowanie schematu XML do generowania nie tylko ograniczenia, ale także relacji w  **Zestaw danych**.</span><span class="sxs-lookup"><span data-stu-id="a1db9-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="a1db9-111">Jednak w przypadku określenia `msdata:ConstraintOnly="true"` w **keyref** elementu **DataSet** będzie zawierać wyłącznie ograniczeń i nie zostaną uwzględnione w relacji.</span><span class="sxs-lookup"><span data-stu-id="a1db9-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="a1db9-112">W poniższym przykładzie przedstawiono schematu XML, który zawiera **kolejności** i **OrderDetail** elementy, które nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="a1db9-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="a1db9-113">Schemat określa również ograniczeń keyref i kluczy.</span><span class="sxs-lookup"><span data-stu-id="a1db9-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="a1db9-114">**DataSet** , jest generowany podczas schematu XML zawiera proces mapowania **kolejności** i **OrderDetail** tabel.</span><span class="sxs-lookup"><span data-stu-id="a1db9-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="a1db9-115">Ponadto **DataSet** zawiera relacje i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="a1db9-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="a1db9-116">Poniższy kod przedstawia te relacje i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="a1db9-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="a1db9-117">Należy zauważyć, że nie określono schematu **msdata:Relationship** adnotacji; zamiast tego ograniczenia klucza i keyref są używane do generowania relacji.</span><span class="sxs-lookup"><span data-stu-id="a1db9-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
```  
....ConstraintName: OrderNumberKey  
....Type: UniqueConstraint  
....Table: Order  
....Columns: OrderNumber  
....IsPrimaryKey: False  
  
....ConstraintName: OrderNoRef  
....Type: ForeignKeyConstraint  
....Table: OrderDetail  
....Columns: OrderNo  
....RelatedTable: Order  
....RelatedColumns: OrderNumber  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
```  
  
 <span data-ttu-id="a1db9-118">W poprzednim przykładzie schematu **kolejności** i **OrderDetail** elementy nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="a1db9-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="a1db9-119">W poniższym przykładzie schematu tych elementów jest zagnieżdżanych.</span><span class="sxs-lookup"><span data-stu-id="a1db9-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="a1db9-120">Jednak nie **msdata:Relationship** adnotacja jest określona; w związku z tym, przyjmowana jest niejawnych relacji.</span><span class="sxs-lookup"><span data-stu-id="a1db9-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="a1db9-121">Aby uzyskać więcej informacji, zobacz [mapy niejawnych relacji między zagnieżdżone elementy schematu](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="a1db9-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="a1db9-122">Schemat określa również ograniczeń keyref i kluczy.</span><span class="sxs-lookup"><span data-stu-id="a1db9-122">The schema also specifies key and keyref constraints.</span></span>  
  
```xml  
<xs:schema id="MyDataSet" xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
  
      <xs:element name="Order">  
        <xs:complexType>  
          <xs:sequence>  
            <xs:element name="OrderNumber" type="xs:integer" />  
            <xs:element name="EmpNumber" type="xs:integer" />  
  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:integer" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
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
  
 <span data-ttu-id="a1db9-123">**DataSet** wyniku procesu mapowania schematu XML zawiera dwie tabele:</span><span class="sxs-lookup"><span data-stu-id="a1db9-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="a1db9-124">**DataSet** obejmuje również dwie relacje (jedną na podstawie **msdata:relationship** adnotacji, a drugi na podstawie klucza i keyref ograniczeń) i różnych ograniczeń.</span><span class="sxs-lookup"><span data-stu-id="a1db9-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="a1db9-125">Poniższy przykład pokazuje, relacje i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="a1db9-125">The following example shows the relations and constraints.</span></span>  
  
```  
..RelationName: Order_OrderDetail  
..ParentTable: Order  
..ParentColumns: Order_Id  
..ChildTable: OrderDetail  
..ChildColumns: Order_Id  
..ParentKeyConstraint: Constraint1  
..ChildKeyConstraint: Order_OrderDetail  
..Nested: True  
  
..RelationName: OrderNoRef  
..ParentTable: Order  
..ParentColumns: OrderNumber  
..ChildTable: OrderDetail  
..ChildColumns: OrderNo  
..ParentKeyConstraint: OrderNumberKey  
..ChildKeyConstraint: OrderNoRef  
..Nested: False  
  
..ConstraintName: OrderNumberKey  
..Type: UniqueConstraint  
..Table: Order  
..Columns: OrderNumber  
..IsPrimaryKey: False  
  
..ConstraintName: Constraint1  
..Type: UniqueConstraint  
..Table: Order  
..Columns: Order_Id  
..IsPrimaryKey: True  
  
..ConstraintName: Order_OrderDetail  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: Order_Id  
..RelatedTable: Order  
..RelatedColumns: Order_Id  
  
..ConstraintName: OrderNoRef  
..Type: ForeignKeyConstraint  
..Table: OrderDetail  
..Columns: OrderNo  
..RelatedTable: Order  
..RelatedColumns: OrderNumber  
```  
  
 <span data-ttu-id="a1db9-126">Jeśli zawiera ograniczenie keyref odwołujące się do tabeli zagnieżdżonej **msdata:IsNested = "true"** adnotacji, **DataSet** spowoduje utworzenie jednego relację zagnieżdżonych, która opiera się na ograniczenie keyref i powiązane ograniczenia unique key.</span><span class="sxs-lookup"><span data-stu-id="a1db9-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a1db9-127">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a1db9-127">See Also</span></span>  
 [<span data-ttu-id="a1db9-128">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="a1db9-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 [<span data-ttu-id="a1db9-129">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="a1db9-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
