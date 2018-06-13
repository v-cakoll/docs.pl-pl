---
title: Mapowanie niejawnych relacji między elementami zagnieżdżonych schematu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: 1bce0c2815ac94787055794942807777232df295
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32763631"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="fe36d-102">Mapowanie niejawnych relacji między elementami zagnieżdżonych schematu</span><span class="sxs-lookup"><span data-stu-id="fe36d-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="fe36d-103">Schemat schematu XML definition language (XSD) może mieć typów złożonych zagnieżdżona siebie nawzajem.</span><span class="sxs-lookup"><span data-stu-id="fe36d-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="fe36d-104">W takim przypadku proces mapowania stosuje domyślne mapowanie i tworzy następujące opcje w <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="fe36d-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
-   <span data-ttu-id="fe36d-105">Jedna tabela dla każdego z typów złożonych (nadrzędnych i podrzędnych).</span><span class="sxs-lookup"><span data-stu-id="fe36d-105">One table for each of the complex types (parent and child).</span></span>  
  
-   <span data-ttu-id="fe36d-106">Jeśli nie ograniczenia unique istnieje w nadrzędnej, co dodatkowe kolumny klucza podstawowego dla definicji tabeli o nazwie *TableName*_Id gdzie *TableName* jest nazwą tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="fe36d-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
-   <span data-ttu-id="fe36d-107">Ograniczenia klucza podstawowego w tabeli nadrzędnej identyfikowanie dodatkowych kolumn jako klucz podstawowy (przez ustawienie **IsPrimaryKey** właściwości **True**).</span><span class="sxs-lookup"><span data-stu-id="fe36d-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="fe36d-108">Ograniczenie o nazwie ograniczenie*#* gdzie *#* 1, 2, 3 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="fe36d-108">The constraint is named Constraint*#* where *#* is 1, 2, 3, and so on.</span></span> <span data-ttu-id="fe36d-109">Na przykład domyślna nazwa ograniczenia pierwszy to Constraint1.</span><span class="sxs-lookup"><span data-stu-id="fe36d-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
-   <span data-ttu-id="fe36d-110">Ograniczenie klucza obcego w tabeli podrzędnej identyfikację dodatkowych kolumn jako klucz obcy odwołujących się do klucza podstawowego tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="fe36d-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="fe36d-111">Ograniczenie o nazwie *ParentTable_ChildTable* gdzie *ParentTable* jest nazwą tabeli nadrzędnej i *ChildTable* jest nazwą tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="fe36d-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
-   <span data-ttu-id="fe36d-112">Dane relacji między tabelą nadrzędną i podrzędną.</span><span class="sxs-lookup"><span data-stu-id="fe36d-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="fe36d-113">W poniższym przykładzie przedstawiono schematu gdzie **OrderDetail** jest elementem podrzędnym **kolejności**.</span><span class="sxs-lookup"><span data-stu-id="fe36d-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="fe36d-114">Proces mapowania schematu XML tworzy następujące opcje w **zestawu danych**:</span><span class="sxs-lookup"><span data-stu-id="fe36d-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
-   <span data-ttu-id="fe36d-115">**Kolejności** i **OrderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="fe36d-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
-   <span data-ttu-id="fe36d-116">Ograniczenia unique wobec **kolejności** tabeli.</span><span class="sxs-lookup"><span data-stu-id="fe36d-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="fe36d-117">Należy pamiętać, że **IsPrimaryKey** właściwość jest ustawiona na **True**.</span><span class="sxs-lookup"><span data-stu-id="fe36d-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
-   <span data-ttu-id="fe36d-118">Ograniczenie klucza obcego w **OrderDetail** tabeli.</span><span class="sxs-lookup"><span data-stu-id="fe36d-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
-   <span data-ttu-id="fe36d-119">Relacja między **kolejności** i **OrderDetail** tabel.</span><span class="sxs-lookup"><span data-stu-id="fe36d-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="fe36d-120">**Zagnieżdżone** ma ustawioną wartość właściwości dla tej relacji **True** ponieważ **kolejności** i **OrderDetail** elementy są zagnieżdżone w schemacie .</span><span class="sxs-lookup"><span data-stu-id="fe36d-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="fe36d-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fe36d-121">See Also</span></span>  
 [<span data-ttu-id="fe36d-122">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="fe36d-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 [<span data-ttu-id="fe36d-123">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="fe36d-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 [<span data-ttu-id="fe36d-124">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="fe36d-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
