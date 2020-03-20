---
title: Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: dc5b81fd06f2860283c8c5fa028af4b945e2b1e9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79150966"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="19807-102">Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu</span><span class="sxs-lookup"><span data-stu-id="19807-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="19807-103">Schemat języka XM (XSD) może mieć złożone typy zagnieżdżone wewnątrz siebie.</span><span class="sxs-lookup"><span data-stu-id="19807-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="19807-104">W takim przypadku proces mapowania stosuje mapowanie domyślne i tworzy następujące elementy w: <xref:System.Data.DataSet></span><span class="sxs-lookup"><span data-stu-id="19807-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="19807-105">Jedna tabela dla każdego z typów złożonych (nadrzędny i podrzędny).</span><span class="sxs-lookup"><span data-stu-id="19807-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="19807-106">Jeśli w chyłce element nadrzędny nie istnieje żadne unikatowe ograniczenie, jedna dodatkowa kolumna klucza podstawowego na definicję tabeli o nazwie *TableName*_Id gdzie *Nazwa tabeli* jest nazwą tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="19807-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="19807-107">Ograniczenie klucza podstawowego w tabeli nadrzędnej identyfikujące dodatkową kolumnę jako klucz podstawowy (przez ustawienie właściwości **IsPrimaryKey** na **True).**</span><span class="sxs-lookup"><span data-stu-id="19807-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="19807-108">Ograniczenie nosi nazwę\# \# Ograniczenie, gdzie jest 1, 2, 3 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="19807-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="19807-109">Na przykład domyślną nazwą pierwszego ograniczenia jest Constraint1.</span><span class="sxs-lookup"><span data-stu-id="19807-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="19807-110">Ograniczenie klucza obcego w tabeli podrzędnej identyfikujące dodatkową kolumnę jako klucz obcy odnoszący się do klucza podstawowego tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="19807-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="19807-111">Ograniczenie nosi nazwę *ParentTable_ChildTable* gdzie *Tabela nadrzędna* jest nazwą tabeli nadrzędnej, a *Tabela podrzędna* jest nazwą tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="19807-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="19807-112">Relacja danych między tabelami nadrzędnymi i podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="19807-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="19807-113">W poniższym przykładzie pokazano schemat, w którym **OrderDetail** jest elementem podrzędnym **Order**.</span><span class="sxs-lookup"><span data-stu-id="19807-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
            <xs:element name="OrderNumber" type="xs:string" />  
            <xs:element name="EmpNumber" type="xs:string" />  
            <xs:element name="OrderDetail">  
              <xs:complexType>  
                <xs:sequence>  
                  <xs:element name="OrderNo" type="xs:string" />  
                  <xs:element name="ItemNo" type="xs:string" />  
                </xs:sequence>  
              </xs:complexType>  
            </xs:element>  
          </xs:sequence>  
         </xs:complexType>  
       </xs:element>  
     </xs:choice>  
   </xs:complexType>  
  </xs:element>  
</xs:schema>  
```  
  
 <span data-ttu-id="19807-114">Proces mapowania schematu XML tworzy w **zestawie danych**następujące elementy:</span><span class="sxs-lookup"><span data-stu-id="19807-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="19807-115">**Zamówienie** i **orderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="19807-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```text  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="19807-116">Unikatowe ograniczenie w tabeli **Kolejność.**</span><span class="sxs-lookup"><span data-stu-id="19807-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="19807-117">Należy zauważyć, że **właściwość IsPrimaryKey** jest ustawiona na **True**.</span><span class="sxs-lookup"><span data-stu-id="19807-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```text  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="19807-118">Ograniczenie klucza obcego w tabeli **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="19807-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```text  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id
    RelatedTable: Order  
    RelatedColumns: Order_Id
    ```  
  
- <span data-ttu-id="19807-119">Relacja między tabelami **Order** i **OrderDetail.**</span><span class="sxs-lookup"><span data-stu-id="19807-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="19807-120">Właściwość **Zagnieżdżona** dla tej relacji jest ustawiona na **True,** ponieważ elementy **Order** i **OrderDetail** są zagnieżdżone w schemacie.</span><span class="sxs-lookup"><span data-stu-id="19807-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```text  
    ParentTable: Order  
    ParentColumns: Order_Id
    ChildTable: OrderDetail  
    ChildColumns: Order_Id
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="19807-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="19807-121">See also</span></span>

- [<span data-ttu-id="19807-122">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="19807-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="19807-123">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="19807-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="19807-124">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="19807-124">ADO.NET Overview</span></span>](../ado-net-overview.md)
