---
title: Relacje i ograniczenia schematu XML
ms.date: 03/30/2017
ms.assetid: 165bc2bc-60a1-40e0-9b89-7c68ef979079
ms.openlocfilehash: 76af1c2e9d85d18a68b8c0a947dfba3b3291326c
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70784188"
---
# <a name="xml-schema-constraints-and-relationships"></a><span data-ttu-id="8ca32-102">Relacje i ograniczenia schematu XML</span><span class="sxs-lookup"><span data-stu-id="8ca32-102">XML Schema Constraints and Relationships</span></span>
<span data-ttu-id="8ca32-103">W schemacie języka definicji schematu XML (XSD) można określić ograniczenia (ograniczenia UNIQUE, Key i keyref) oraz relacje (przy użyciu adnotacji **msdata: Relationship** ).</span><span class="sxs-lookup"><span data-stu-id="8ca32-103">In an XML Schema definition language (XSD) schema, you can specify constraints (unique, key, and keyref constraints) and relationships (using the **msdata:Relationship** annotation).</span></span> <span data-ttu-id="8ca32-104">W tym temacie wyjaśniono, jak są interpretowane ograniczenia i relacje określone w schemacie XML <xref:System.Data.DataSet>w celu wygenerowania.</span><span class="sxs-lookup"><span data-stu-id="8ca32-104">This topic explains how the constraints and relationships specified in an XML Schema are interpreted to generate the <xref:System.Data.DataSet>.</span></span>  
  
 <span data-ttu-id="8ca32-105">Ogólnie rzecz biorąc, w schemacie XML należy określić adnotację **msdata: Relationship** , jeśli chcesz wygenerować tylko relacje w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="8ca32-105">In general, in an XML Schema, you specify the **msdata:Relationship** annotation if you want to generate only relationships in the **DataSet**.</span></span> <span data-ttu-id="8ca32-106">Aby uzyskać więcej informacji, zobacz [generowanie relacji zestawu danych z schematu XML (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span><span class="sxs-lookup"><span data-stu-id="8ca32-106">For more information, see [Generating DataSet Relations from XML Schema (XSD)](generating-dataset-relations-from-xml-schema-xsd.md).</span></span> <span data-ttu-id="8ca32-107">Należy określić ograniczenia (unikatowy, klucz i keyref), jeśli chcesz wygenerować ograniczenia w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="8ca32-107">You specify constraints (unique, key, and keyref) if you want to generate constraints in the **DataSet**.</span></span> <span data-ttu-id="8ca32-108">Należy zauważyć, że ograniczenia Key i keyref są również używane do generowania relacji, jak wyjaśniono w dalszej części tego tematu.</span><span class="sxs-lookup"><span data-stu-id="8ca32-108">Note that the key and keyref constraints are also used to generate relationships, as explained later in this topic.</span></span>  
  
## <a name="generating-a-relationship-from-key-and-keyref-constraints"></a><span data-ttu-id="8ca32-109">Generowanie relacji z ograniczeniami Key i keyref</span><span class="sxs-lookup"><span data-stu-id="8ca32-109">Generating a Relationship from key and keyref Constraints</span></span>  
 <span data-ttu-id="8ca32-110">Zamiast określania adnotacji **msdata: Relationship** , można określić ograniczenia Key i keyref, które są używane podczas procesu mapowania schematu XML do generowania nie tylko ograniczenia, ale również relacji w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="8ca32-110">Instead of specifying the **msdata:Relationship** annotation, you can specify key and keyref constraints, which are used during the XML Schema mapping process to generate not only the constraints but also the relationship in the **DataSet**.</span></span> <span data-ttu-id="8ca32-111">Jeśli jednak określisz `msdata:ConstraintOnly="true"` w elemencie **keyref** , **zestaw danych** będzie zawierać tylko ograniczenia i nie będzie uwzględniać relacji.</span><span class="sxs-lookup"><span data-stu-id="8ca32-111">However, if you specify `msdata:ConstraintOnly="true"` in the **keyref** element, the **DataSet** will include only the constraints and will not include the relationship.</span></span>  
  
 <span data-ttu-id="8ca32-112">W poniższym przykładzie przedstawiono schemat XML, który zawiera elementy **Order** i **OrderDetail** , które nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="8ca32-112">The following example shows an XML Schema that includes **Order** and **OrderDetail** elements, which are not nested.</span></span> <span data-ttu-id="8ca32-113">Schemat określa również ograniczenia klucza i elementu keyref.</span><span class="sxs-lookup"><span data-stu-id="8ca32-113">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="8ca32-114">**Zestaw danych** , który jest generowany podczas procesu mapowania schematu XML, zawiera tabele **Order** i **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="8ca32-114">The **DataSet** that is generated during the XML Schema mapping process includes the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="8ca32-115">Ponadto **zestaw danych** zawiera relacje i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8ca32-115">In addition, the **DataSet** includes relationships and constraints.</span></span> <span data-ttu-id="8ca32-116">W poniższym przykładzie przedstawiono relacje i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8ca32-116">The following example shows these relationships and constraints.</span></span> <span data-ttu-id="8ca32-117">Należy zauważyć, że schemat nie określa adnotacji **msdata: Relationship** ; Zamiast tego ograniczenia Key i keyref są używane do generowania relacji.</span><span class="sxs-lookup"><span data-stu-id="8ca32-117">Note that the schema does not specify the **msdata:Relationship** annotation; instead, the key and keyref constraints are used to generate the relation.</span></span>  
  
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
  
 <span data-ttu-id="8ca32-118">W poprzednim przykładzie schematu elementy **Order** i **OrderDetail** nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="8ca32-118">In the previous schema example, the **Order** and **OrderDetail** elements are not nested.</span></span> <span data-ttu-id="8ca32-119">W poniższym przykładzie schematu te elementy są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="8ca32-119">In the following schema example, these elements are nested.</span></span> <span data-ttu-id="8ca32-120">Jednak nie **msdata:** adnotacja relacji jest określona; w związku z tym założono niejawną relację.</span><span class="sxs-lookup"><span data-stu-id="8ca32-120">However, no **msdata:Relationship** annotation is specified; therefore, an implicit relation is assumed.</span></span> <span data-ttu-id="8ca32-121">Aby uzyskać więcej informacji, zobacz [Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu](map-implicit-relations-between-nested-schema-elements.md).</span><span class="sxs-lookup"><span data-stu-id="8ca32-121">For more information, see [Map Implicit Relations Between Nested Schema Elements](map-implicit-relations-between-nested-schema-elements.md).</span></span> <span data-ttu-id="8ca32-122">Schemat określa również ograniczenia klucza i elementu keyref.</span><span class="sxs-lookup"><span data-stu-id="8ca32-122">The schema also specifies key and keyref constraints.</span></span>  
  
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
  
 <span data-ttu-id="8ca32-123">**Zestaw danych** wynikający z procesu mapowania schematu XML obejmuje dwie tabele:</span><span class="sxs-lookup"><span data-stu-id="8ca32-123">The **DataSet** resulting from the XML Schema mapping process includes two tables:</span></span>  
  
```  
Order(OrderNumber, EmpNumber, Order_Id)  
OrderDetail(OrderNumber, ItemNumber, Order_Id)  
```  
  
 <span data-ttu-id="8ca32-124">**Zestaw danych** zawiera również dwie relacje (jedna oparta na **msdata:** adnotacja relacji i inne na podstawie ograniczeń klucza i elementu keyref) i różne ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8ca32-124">The **DataSet** also includes the two relationships (one based on the **msdata:relationship** annotation and the other based on the key and keyref constraints) and various constraints.</span></span> <span data-ttu-id="8ca32-125">W poniższym przykładzie przedstawiono relacje i ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="8ca32-125">The following example shows the relations and constraints.</span></span>  
  
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
  
 <span data-ttu-id="8ca32-126">Jeśli ograniczenie elementu keyref odwołujące się do zagnieżdżonej tabeli zawiera adnotację **msdata: Isnested = "true"** , **zestaw danych** utworzy pojedynczą relację zagnieżdżoną opartą na ograniczeniu keyref i powiązanym ograniczeniu UNIQUE/Key.</span><span class="sxs-lookup"><span data-stu-id="8ca32-126">If a keyref constraint referring to a nested table contains the **msdata:IsNested="true"** annotation, the **DataSet** will create a single nested relationship that is based on the keyref constraint and the related unique/key constraint.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8ca32-127">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="8ca32-127">See also</span></span>

- [<span data-ttu-id="8ca32-128">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="8ca32-128">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)
- [<span data-ttu-id="8ca32-129">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="8ca32-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
