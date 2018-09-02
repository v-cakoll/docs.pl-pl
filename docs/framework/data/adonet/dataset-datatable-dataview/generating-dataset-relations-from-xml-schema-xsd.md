---
title: Generowanie relacji elementu DataSet ze schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: 7c73dcec3d23b094436791af6649de83b9eacad9
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/01/2018
ms.locfileid: "43416355"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="fc9ad-102">Generowanie relacji elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="fc9ad-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="fc9ad-103">W <xref:System.Data.DataSet>, formularza skojarzenia między co najmniej dwóch kolumn, tworząc relację nadrzędny podrzędny.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="fc9ad-104">Istnieją trzy sposoby do reprezentowania **DataSet** relacji w ramach schematu języka (XSD) definicji schematu XML:</span><span class="sxs-lookup"><span data-stu-id="fc9ad-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
-   <span data-ttu-id="fc9ad-105">Określ zagnieżdżonych typów złożonych.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-105">Specify nested complex types.</span></span>  
  
-   <span data-ttu-id="fc9ad-106">Użyj **msdata:Relationship** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-106">Use the **msdata:Relationship** annotation.</span></span>  
  
-   <span data-ttu-id="fc9ad-107">Określ **xs:keyref** bez **msdata:ConstraintOnly** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="fc9ad-108">Zagnieżdżone typy złożone</span><span class="sxs-lookup"><span data-stu-id="fc9ad-108">Nested Complex Types</span></span>  
 <span data-ttu-id="fc9ad-109">Definicje zagnieżdżonych typów złożonych w schemacie wskazują relacje nadrzędny podrzędny elementów.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="fc9ad-110">Poniższy fragment schematu XML pokazują, że **OrderDetail** jest elementem podrzędnym **kolejności** elementu.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
```xml  
<xs:element name="Order">  
  <xs:complexType>  
     <xs:sequence>          
       <xs:element name="OrderDetail" />  
           <xs:complexType>               
           </xs:complexType>  
     </xs:sequence>  
  </xs:complexType>  
</xs:element>  
```  
  
 <span data-ttu-id="fc9ad-111">Proces mapowania schematu XML tworzy tabele w **DataSet** odpowiadające zagnieżdżone typy złożone w schemacie.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="fc9ad-112">Tworzy również dodatkowe kolumny, które są używane jako element nadrzędny**-** kolumn podrzędnych dla wygenerowanego tabel.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="fc9ad-113">Należy zauważyć, że te nadrzędnego**-** kolumn podrzędnych określa relacje, które nie jest taka sama jak określanie ograniczeń klucza podstawowego/klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="fc9ad-114">MSDATA:Relationship adnotacji</span><span class="sxs-lookup"><span data-stu-id="fc9ad-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="fc9ad-115">**Msdata:Relationship** adnotacji można jawnie określić relacji nadrzędny podrzędny między elementami w schemacie, które nie są osadzone.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="fc9ad-116">Poniższy przykład pokazuje strukturę **relacji** elementu.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"    
msdata:parent=""    
msdata:child=""    
msdata:parentkey=""    
msdata:childkey="" />  
```  
  
 <span data-ttu-id="fc9ad-117">Atrybuty **msdata:Relationship** adnotacji identyfikowania elementów uczestniczących w relacji nadrzędny podrzędny, jak również jako **elementy parentkey** i **childkey** elementy i atrybuty uczestniczących w relacji.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="fc9ad-118">Proces mapowania używa tych informacji w celu wygenerowania tabel w **DataSet** i utworzyć podstawowy klucz/relacji klucza obcego między tymi tabelami.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="fc9ad-119">Na przykład poniższy fragment schemat określa **kolejności** i **OrderDetail** elementów na tym samym poziomie (niezagnieżdżony).</span><span class="sxs-lookup"><span data-stu-id="fc9ad-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="fc9ad-120">Schemat określa **msdata:Relationship** adnotacji, który określa relacji nadrzędny podrzędny między tymi dwoma elementami.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="fc9ad-121">W tym przypadku wyraźnej relacji musi być określony przy użyciu **msdata:Relationship** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
```xml  
 <xs:element name="MyDataSet" msdata:IsDataSet="true">  
  <xs:complexType>  
    <xs:choice maxOccurs="unbounded">  
        <xs:element name="OrderDetail">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
       <xs:element name="Order">  
          <xs:complexType>  
  
          </xs:complexType>  
       </xs:element>  
    </xs:choice>  
  </xs:complexType>  
</xs:element>  
   <xs:annotation>  
     <xs:appinfo>  
       <msdata:Relationship name="OrdOrdDetailRelation"  
          msdata:parent="Order"  
          msdata:child="OrderDetail"   
          msdata:parentkey="OrderNumber"  
          msdata:childkey="OrderNo"/>  
     </xs:appinfo>  
  </xs:annotation>  
```  
  
 <span data-ttu-id="fc9ad-122">Proces mapowania używa **relacji** elementu do utworzenia relacji nadrzędny podrzędny między **OrderNumber** kolumny w **kolejności** tabeli i **OrderNo** kolumny w **OrderDetail** tabelę **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="fc9ad-123">Proces mapowania określa tylko relacji; nie automatycznie określa wszelkie ograniczenia na podstawie wartości w tych kolumnach, tak jak podstawowego klucza/ograniczenia klucza obcego w relacyjnych baz danych.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="fc9ad-124">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="fc9ad-124">In This Section</span></span>  
 [<span data-ttu-id="fc9ad-125">Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu</span><span class="sxs-lookup"><span data-stu-id="fc9ad-125">Map Implicit Relations Between Nested Schema Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="fc9ad-126">W tym artykule opisano ograniczenia i relacje, które są tworzone niejawnie w **DataSet** po napotkaniu elementów zagnieżdżonych w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="fc9ad-127">Mapowanie relacji określonych dla zagnieżdżonych elementów</span><span class="sxs-lookup"><span data-stu-id="fc9ad-127">Map Relations Specified for Nested Elements</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="fc9ad-128">Opisuje sposób jawnie ustawić relacji między deweloperami rozwiązań **zestawu danych** dla elementów zagnieżdżonych w schematu XML.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="fc9ad-129">Określanie relacji między elementami bez zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="fc9ad-129">Specify Relations Between Elements with No Nesting</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="fc9ad-130">W tym artykule opisano sposób tworzenia relacji w **DataSet** między elementami schematu XML, które nie są osadzone.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="fc9ad-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="fc9ad-131">Related Sections</span></span>  
 [<span data-ttu-id="fc9ad-132">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="fc9ad-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="fc9ad-133">W tym artykule opisano relacyjnej struktury lub schematu z **DataSet** , jest tworzona na podstawie schematu języka (XSD) definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="fc9ad-134">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="fc9ad-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="fc9ad-135">Opisano elementy schematu XML, używany do tworzenia unikatowych obcych kluczy ograniczeń i **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="fc9ad-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc9ad-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fc9ad-136">See Also</span></span>  
 [<span data-ttu-id="fc9ad-137">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="fc9ad-137">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
