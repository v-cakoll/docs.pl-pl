---
title: Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu
ms.date: 03/30/2017
ms.assetid: 6b25002a-352e-4d9b-bae3-15129458a355
ms.openlocfilehash: e9ea85db98a577991e06e0239a0738a2ca5bada6
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/31/2019
ms.locfileid: "70203482"
---
# <a name="map-implicit-relations-between-nested-schema-elements"></a><span data-ttu-id="9d766-102">Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu</span><span class="sxs-lookup"><span data-stu-id="9d766-102">Map Implicit Relations Between Nested Schema Elements</span></span>
<span data-ttu-id="9d766-103">Schemat języka definicji schematu XML (XSD) może mieć złożone typy zagnieżdżone wewnątrz siebie.</span><span class="sxs-lookup"><span data-stu-id="9d766-103">An XML Schema definition language (XSD) schema can have complex types nested inside one another.</span></span> <span data-ttu-id="9d766-104">W takim przypadku proces mapowania stosuje domyślne mapowanie i tworzy następujące elementy w <xref:System.Data.DataSet>:</span><span class="sxs-lookup"><span data-stu-id="9d766-104">In this case, the mapping process applies default mapping and creates the following in the <xref:System.Data.DataSet>:</span></span>  
  
- <span data-ttu-id="9d766-105">Jedna tabela dla każdego z typów złożonych (nadrzędnych i podrzędnych).</span><span class="sxs-lookup"><span data-stu-id="9d766-105">One table for each of the complex types (parent and child).</span></span>  
  
- <span data-ttu-id="9d766-106">Jeśli w obiekcie nadrzędnym nie istnieje ograniczenie UNIQUE, jedna dodatkowa kolumna klucza podstawowego dla definicji tabelio nazwie TableName _Id, gdzie *TableName* jest nazwą tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="9d766-106">If no unique constraint exists on the parent, one additional primary key column per table definition named *TableName*_Id where *TableName* is the name of the parent table.</span></span>  
  
- <span data-ttu-id="9d766-107">Ograniczenie PRIMARY KEY w tabeli nadrzędnej identyfikujące dodatkową kolumnę jako klucz podstawowy (przez ustawienie właściwości IsPrimaryKey na **wartość true**).</span><span class="sxs-lookup"><span data-stu-id="9d766-107">A primary key constraint on the parent table identifying the additional column as the primary key (by setting the **IsPrimaryKey** property to **True**).</span></span> <span data-ttu-id="9d766-108">Ograniczenie ma nazwę Constraint\# , gdzie \# ma wartość 1, 2, 3 i tak dalej.</span><span class="sxs-lookup"><span data-stu-id="9d766-108">The constraint is named Constraint\# where \# is 1, 2, 3, and so on.</span></span> <span data-ttu-id="9d766-109">Na przykład domyślna nazwa pierwszego ograniczenia to Constraint1.</span><span class="sxs-lookup"><span data-stu-id="9d766-109">For example, the default name for the first constraint is Constraint1.</span></span>  
  
- <span data-ttu-id="9d766-110">Ograniczenie klucza obcego w tabeli podrzędnej identyfikującej dodatkową kolumnę jako klucz obcy odwołujący się do klucza podstawowego tabeli nadrzędnej.</span><span class="sxs-lookup"><span data-stu-id="9d766-110">A foreign key constraint on the child table identifying the additional column as the foreign key referring to the primary key of the parent table.</span></span> <span data-ttu-id="9d766-111">Ograniczenie ma nazwę *ParentTable_ChildTable* , gdzie *element parentname* jest nazwą tabeli nadrzędnej i *elementem podrzędnym* jest nazwa tabeli podrzędnej.</span><span class="sxs-lookup"><span data-stu-id="9d766-111">The constraint is named *ParentTable_ChildTable* where *ParentTable* is the name of the parent table and *ChildTable* is the name of the child table.</span></span>  
  
- <span data-ttu-id="9d766-112">Relacja danych między tabelami nadrzędnymi i podrzędnymi.</span><span class="sxs-lookup"><span data-stu-id="9d766-112">A data relation between the parent and child tables.</span></span>  
  
 <span data-ttu-id="9d766-113">W poniższym przykładzie przedstawiono schemat, gdzie **OrderDetail** jest elementem podrzędnym **zamówienia**.</span><span class="sxs-lookup"><span data-stu-id="9d766-113">The following example shows a schema where **OrderDetail** is a child element of **Order**.</span></span>  
  
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
  
 <span data-ttu-id="9d766-114">Proces mapowania schematu XML tworzy następujące elementy w **zestawie danych**:</span><span class="sxs-lookup"><span data-stu-id="9d766-114">The XML Schema mapping process creates the following in the **DataSet**:</span></span>  
  
- <span data-ttu-id="9d766-115">**Zamówienie** i tabela **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="9d766-115">An **Order** and an **OrderDetail** table.</span></span>  
  
    ```  
    Order(OrderNumber, EmpNumber, Order_Id)  
    OrderDetail(OrderNo, ItemNo, Order_Id)  
    ```  
  
- <span data-ttu-id="9d766-116">Unikatowe ograniczenie tabeli **Order** .</span><span class="sxs-lookup"><span data-stu-id="9d766-116">A unique constraint on the **Order** table.</span></span> <span data-ttu-id="9d766-117">Należy pamiętać, że właściwość IsPrimaryKey jest ustawiona na **wartość true**.</span><span class="sxs-lookup"><span data-stu-id="9d766-117">Note that the **IsPrimaryKey** property is set to **True**.</span></span>  
  
    ```  
    ConstraintName: Constraint1  
    Type: UniqueConstraint  
    Table: Order  
    Columns: Order_Id   
    IsPrimaryKey: True  
    ```  
  
- <span data-ttu-id="9d766-118">Ograniczenie klucza obcego w tabeli **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="9d766-118">A foreign key constraint on the **OrderDetail** table.</span></span>  
  
    ```  
    ConstraintName: Order_OrderDetail  
    Type: ForeignKeyConstraint  
    Table: OrderDetail  
    Columns: Order_Id   
    RelatedTable: Order  
    RelatedColumns: Order_Id   
    ```  
  
- <span data-ttu-id="9d766-119">Relacja między tabelami **Order** i **OrderDetail** .</span><span class="sxs-lookup"><span data-stu-id="9d766-119">A relationship between the **Order** and **OrderDetail** tables.</span></span> <span data-ttu-id="9d766-120">Właściwość **zagnieżdżona** dla tej relacji jest ustawiona na **wartość true** , ponieważ elementy **Order** i **OrderDetail** są zagnieżdżone w schemacie.</span><span class="sxs-lookup"><span data-stu-id="9d766-120">The **Nested** property for this relationship is set to **True** because the **Order** and **OrderDetail** elements are nested in the schema.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="9d766-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9d766-121">See also</span></span>

- [<span data-ttu-id="9d766-122">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="9d766-122">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)
- [<span data-ttu-id="9d766-123">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="9d766-123">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)
- [<span data-ttu-id="9d766-124">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="9d766-124">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
