---
title: Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 076e3ec6e5a00fd294fa3c6d7998cfab3a136240
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59182078"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="9ae52-102">Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu</span><span class="sxs-lookup"><span data-stu-id="9ae52-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="9ae52-103">Schemat języka (XSD) definicji schematu XML może mieć typy złożone, zagnieżdżone wewnątrz siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="9ae52-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="9ae52-104">W takim przypadku proces mapowania stosuje domyślne mapowanie i tworzy następujące <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="9ae52-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="9ae52-105">Jedną tabelę dla każdego z typów złożonych (nadrzędnych i podrzędnych).</span><span class="sxs-lookup"><span data-stu-id="9ae52-105">One table for each of the complex types (parent and child).</span></span>  
  
-   <span data-ttu-id="9ae52-106">Jeśli nie ograniczenia unique znajduje się na element nadrzędny, co dodatkowe kolumny klucza podstawowego dla definicji tabeli o nazwie *TableName*_identyfikator gdzie *TableName* jest nazwą tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="9ae52-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
-   <span data-ttu-id="9ae52-107">Ograniczenia klucza podstawowego w tabeli nadrzędnej identyfikowanie dodatkową kolumnę jako klucz podstawowy (przez ustawienie **IsPrimaryKey** właściwości **True**).</span><span class="sxs-lookup"><span data-stu-id="9ae52-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="9ae52-108">Ograniczenie o nazwie ograniczenie\# gdzie \# to 1, 2, 3 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9ae52-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="9ae52-109">Na przykład domyślna nazwa pierwszego ograniczenia jest Constraint1.</span><span class="sxs-lookup"><span data-stu-id="9ae52-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
-   <span data-ttu-id="9ae52-110">Ograniczenia klucza obcego dla tabeli podrzędnej identyfikuje dodatkową kolumnę jako klucz obcy odwołujące się do klucza podstawowego tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="9ae52-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="9ae52-111">Ograniczenie o nazwie *ParentTable_ChildTable* gdzie *ParentTable* jest nazwą tabeli nadrzędnej i *ChildTable* jest nazwą tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="9ae52-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
-   <span data-ttu-id="9ae52-112">Relacje danych między tabelami nadrzędnymi i podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="9ae52-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="9ae52-113">Poniższy przykład przedstawia schematu gdzie **OrderDetail** jest elementem podrzędnym **kolejności**.</span><span class="sxs-lookup"><span data-stu-id="9ae52-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="9ae52-114">Proces mapowania schematu XML tworzy następujące **zestawu danych**:</span><span class="sxs-lookup"><span data-stu-id="9ae52-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
-   <span data-ttu-id="9ae52-115">**Kolejności** i **OrderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="9ae52-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   <span data-ttu-id="9ae52-116">Ograniczenia unique wobec **kolejności** tabeli.</span><span class="sxs-lookup"><span data-stu-id="9ae52-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="9ae52-117">Należy pamiętać, że **IsPrimaryKey** właściwość jest ustawiona na **True**.</span><span class="sxs-lookup"><span data-stu-id="9ae52-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   <span data-ttu-id="9ae52-118">Ograniczenie klucza obcego w **OrderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="9ae52-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   <span data-ttu-id="9ae52-119">Relacja między **kolejności** i **OrderDetail** tabel.</span><span class="sxs-lookup"><span data-stu-id="9ae52-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="9ae52-120">**Zagnieżdżone** dla tej relacji jest właściwością **True** ponieważ **kolejności** i **OrderDetail** elementów jest zagnieżdżanych w schemacie .</span><span class="sxs-lookup"><span data-stu-id="9ae52-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
    ```  
    ParentTable: Order  
    ParentColumns: Order_Id   
    ChildTable: OrderDetail  
    ChildColumns: Order_Id   
    ParentKeyConstraint: Constraint1  
    ChildKeyConstraint: Order_OrderDetail  
    RelationName: Order_OrderDetail  
    Nested: True  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="9ae52-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9ae52-121">See also</span></span>

- [<span data-ttu-id="9ae52-122">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9ae52-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="9ae52-123">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="9ae52-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="9ae52-124">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="9ae52-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
