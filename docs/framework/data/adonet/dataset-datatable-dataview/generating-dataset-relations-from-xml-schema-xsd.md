---
title: Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 1c9a1413-c0d2-4447-88ba-9a2b0cbc0aa8
ms.openlocfilehash: feb0be7f66bf0f407e54ef0830c13f0c4a8a6418
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151133"
---
# <a name="generating-dataset-relations-from-xml-schema-xsd"></a><span data-ttu-id="ce423-102">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ce423-102">Generating DataSet Relations from XML Schema (XSD)</span></span>
<span data-ttu-id="ce423-103">W <xref:System.Data.DataSet>polu , tworzysz skojarzenie między dwiema lub więcej kolumnami, tworząc relację nadrzędny podrzędny.</span><span class="sxs-lookup"><span data-stu-id="ce423-103">In a <xref:System.Data.DataSet>, you form an association between two or more columns by creating a parent-child relation.</span></span> <span data-ttu-id="ce423-104">Istnieją trzy sposoby reprezentowania relacji **DataSet** w schemacie języka XSD (XSD) języka schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu schematu:</span><span class="sxs-lookup"><span data-stu-id="ce423-104">There are three ways to represent a **DataSet** relation within an XML Schema definition language (XSD) schema:</span></span>  
  
- <span data-ttu-id="ce423-105">Określ zagnieżdżone typy złożone.</span><span class="sxs-lookup"><span data-stu-id="ce423-105">Specify nested complex types.</span></span>  
  
- <span data-ttu-id="ce423-106">Użyj **adnotacji msdata:Relationship.**</span><span class="sxs-lookup"><span data-stu-id="ce423-106">Use the **msdata:Relationship** annotation.</span></span>  
  
- <span data-ttu-id="ce423-107">Określ **xs:keyref** bez **msdata:ConstraintOnly** adnotacji.</span><span class="sxs-lookup"><span data-stu-id="ce423-107">Specify an **xs:keyref** without the **msdata:ConstraintOnly** annotation.</span></span>  
  
## <a name="nested-complex-types"></a><span data-ttu-id="ce423-108">Zagnieżdżone typy złożone</span><span class="sxs-lookup"><span data-stu-id="ce423-108">Nested Complex Types</span></span>  
 <span data-ttu-id="ce423-109">Definicje typów złożonych zagnieżdżonych w schemacie wskazują relacje nadrzędny-podrzędny elementów.</span><span class="sxs-lookup"><span data-stu-id="ce423-109">Nested complex type definitions in a schema indicate the parent-child relationships of the elements.</span></span> <span data-ttu-id="ce423-110">Poniższy fragment schematu XML pokazuje, że **OrderDetail** jest elementem podrzędnym **elementu Order.**</span><span class="sxs-lookup"><span data-stu-id="ce423-110">The following XML Schema fragment shows that **OrderDetail** is a child element of the **Order** element.</span></span>  
  
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
  
 <span data-ttu-id="ce423-111">Proces mapowania schematu XML tworzy tabele w **zestawie danych,** które odpowiadają zagnieżdżonych typom złożonym w schemacie.</span><span class="sxs-lookup"><span data-stu-id="ce423-111">The XML Schema mapping process creates tables in the **DataSet** that correspond to the nested complex types in the schema.</span></span> <span data-ttu-id="ce423-112">Tworzy również dodatkowe kolumny, które**-** są używane jako nadrzędne kolumny podrzędne dla wygenerowanych tabel.</span><span class="sxs-lookup"><span data-stu-id="ce423-112">It also creates additional columns that are used as parent**-** child columns for the generated tables.</span></span> <span data-ttu-id="ce423-113">Należy zauważyć,**-** że te nadrzędne kolumny podrzędne określają relacje, które nie są takie same jak określanie ograniczeń klucza podstawowego/klucza obcego.</span><span class="sxs-lookup"><span data-stu-id="ce423-113">Note that these parent**-** child columns specify relationships, which is not the same as specifying primary key/foreign key constraints.</span></span>  
  
## <a name="msdatarelationship-annotation"></a><span data-ttu-id="ce423-114">msdata:Adnotacja relacji</span><span class="sxs-lookup"><span data-stu-id="ce423-114">msdata:Relationship Annotation</span></span>  
 <span data-ttu-id="ce423-115">Adnotacja **msdata:Relationship** umożliwia jawne określenie relacji nadrzędny-podrzędny między elementami w schemacie, które nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="ce423-115">The **msdata:Relationship** annotation allows you to explicitly specify parent-child relationships between elements in the schema that are not nested.</span></span> <span data-ttu-id="ce423-116">Poniższy przykład przedstawia strukturę **Relationship** element.</span><span class="sxs-lookup"><span data-stu-id="ce423-116">The following example shows the structure of the **Relationship** element.</span></span>  
  
```xml  
<msdata:Relationship name="CustOrderRelationship"
msdata:parent=""
msdata:child=""
msdata:parentkey=""
msdata:childkey="" />  
```  
  
 <span data-ttu-id="ce423-117">Atrybuty **msdata:Relationship** adnotacji zidentyfikować elementy zaangażowane w relacji nadrzędny podrzędny, a także **parentkey** i **childkey** elementy i atrybuty zaangażowane w relacji.</span><span class="sxs-lookup"><span data-stu-id="ce423-117">The attributes of the **msdata:Relationship** annotation identify the elements involved in the parent-child relationship, as well as the **parentkey** and **childkey** elements and attributes involved in the relationship.</span></span> <span data-ttu-id="ce423-118">Proces mapowania używa tych informacji do generowania tabel w **zestawie danych** i tworzenia relacji klucz podstawowy/klucz obcy między tymi tabelami.</span><span class="sxs-lookup"><span data-stu-id="ce423-118">The mapping process uses this information to generate tables in the **DataSet** and to create the primary key/foreign key relationship between these tables.</span></span>  
  
 <span data-ttu-id="ce423-119">Na przykład poniższy fragment schematu określa **Order** i **OrderDetail** elementów na tym samym poziomie (nie zagnieżdżone).</span><span class="sxs-lookup"><span data-stu-id="ce423-119">For example, the following schema fragment specifies **Order** and **OrderDetail** elements at the same level (not nested).</span></span> <span data-ttu-id="ce423-120">Schemat określa **adnotację msdata:Relationship,** która określa relację nadrzędny-podrzędny między tymi dwoma elementami.</span><span class="sxs-lookup"><span data-stu-id="ce423-120">The schema specifies an **msdata:Relationship** annotation, which specifies the parent-child relationship between these two elements.</span></span> <span data-ttu-id="ce423-121">W takim przypadku jawna relacja musi być określona przy użyciu **adnotacji msdata:Relationship.**</span><span class="sxs-lookup"><span data-stu-id="ce423-121">In this case, an explicit relationship must be specified using the **msdata:Relationship** annotation.</span></span>  
  
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
  
 <span data-ttu-id="ce423-122">Proces mapowania używa elementu **Relacja** do utworzenia relacji nadrzędny-podrzędny między kolumną **OrderNumber** w tabeli **Order** **i OrderNo** w tabeli **OrderDetail** w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="ce423-122">The mapping process uses the **Relationship** element to create a parent-child relationship between the **OrderNumber** column in the **Order** table and the **OrderNo** column in the **OrderDetail** table in the **DataSet**.</span></span> <span data-ttu-id="ce423-123">Proces mapowania określa tylko relację; nie określa automatycznie żadnych ograniczeń wartości w tych kolumnach, podobnie jak ograniczenia klucza podstawowego/klucza obcego w relacyjnych bazach danych.</span><span class="sxs-lookup"><span data-stu-id="ce423-123">The mapping process only specifies the relationship; it does not automatically specify any constraints on the values in these columns, as do the primary key/foreign key constraints in relational databases.</span></span>  
  
### <a name="in-this-section"></a><span data-ttu-id="ce423-124">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ce423-124">In This Section</span></span>  
 [<span data-ttu-id="ce423-125">Mapowanie niejawnych relacji między zagnieżdżonymi elementami schematu</span><span class="sxs-lookup"><span data-stu-id="ce423-125">Map Implicit Relations Between Nested Schema Elements</span></span>](map-implicit-relations-between-nested-schema-elements.md)  
 <span data-ttu-id="ce423-126">Opisuje ograniczenia i relacje, które są niejawnie tworzone w **zestawie danych,** gdy elementy zagnieżdżone są napotkane w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="ce423-126">Describes the constraints and relations that are implicitly created in a **DataSet** when nested elements are encountered in XML Schema.</span></span>  
  
 [<span data-ttu-id="ce423-127">Mapowanie relacji określonych dla zagnieżdżonych elementów</span><span class="sxs-lookup"><span data-stu-id="ce423-127">Map Relations Specified for Nested Elements</span></span>](map-relations-specified-for-nested-elements.md)  
 <span data-ttu-id="ce423-128">Opisuje sposób jawnego ustawiania relacji w **zestawie danych** dla elementów zagnieżdżonych w schemacie XML.</span><span class="sxs-lookup"><span data-stu-id="ce423-128">Describes how to explicitly set relations in a **DataSet** for nested elements in XML Schema.</span></span>  
  
 [<span data-ttu-id="ce423-129">Określanie relacji między elementami bez zagnieżdżania</span><span class="sxs-lookup"><span data-stu-id="ce423-129">Specify Relations Between Elements with No Nesting</span></span>](specify-relations-between-elements-with-no-nesting.md)  
 <span data-ttu-id="ce423-130">W tym artykule opisano sposób tworzenia relacji w **zestawie danych** między elementami schematu XML, które nie są zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="ce423-130">Describes how to create relations in a **DataSet** between XML Schema elements that are not nested.</span></span>  
  
### <a name="related-sections"></a><span data-ttu-id="ce423-131">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ce423-131">Related Sections</span></span>  
 [<span data-ttu-id="ce423-132">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ce423-132">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="ce423-133">Opisuje strukturę relacyjną lub schemat **zestawu danych** utworzonego na podstawie schematu języka XSD (XSD) schematu definicji schematu schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="ce423-133">Describes the relational structure, or schema, of a **DataSet** that is created from XML Schema definition language (XSD) schema.</span></span>  
  
 [<span data-ttu-id="ce423-134">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ce423-134">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="ce423-135">W tym artykule opisano elementy schematu XML używane do tworzenia unikatowych i obcych ograniczeń klucza w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="ce423-135">Describes the XML Schema elements used to create unique and foreign key constraints in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce423-136">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce423-136">See also</span></span>

- [<span data-ttu-id="ce423-137">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ce423-137">ADO.NET Overview</span></span>](../ado-net-overview.md)
