---
title: Wyprowadzanie relacyjnej struktury DataSet ze schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 76fd0126f32eb2b22a12ee0b67e1f81794ff9445
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195297"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="e91cc-102">Wyprowadzanie relacyjnej struktury DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="e91cc-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="e91cc-103">Ta sekcja zawiera omówienie sposobów schemat relacyjnej `DataSet` została stworzona od do dokumentu schematu języka (XSD) definicji schematu XML.</span><span class="sxs-lookup"><span data-stu-id="e91cc-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="e91cc-104">Ogólnie rzecz biorąc, dla każdego `complexType` element podrzędny elementu schematu, tabeli jest generowany w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e91cc-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="e91cc-105">Struktura tabeli jest określana zgodnie z definicją typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="e91cc-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="e91cc-106">Tabele zostały utworzone w `DataSet` najwyższego poziomu elementów w schemacie.</span><span class="sxs-lookup"><span data-stu-id="e91cc-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="e91cc-107">Jednak tabeli jest tworzone tylko dla najwyższego poziomu `complexType` elementu po `complexType` element jest zagnieżdżony w innym `complexType` zamierzone, Zapisz zagnieżdżonego elementu, w którym `complexType` element jest mapowany na `DataTable` w ramach `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e91cc-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="e91cc-108">Aby uzyskać więcej informacji na temat XSD, zobacz World Wide Web Consortium (W3C) [XML schematu część 0: zalecenie Elementarz](https://www.w3.org/TR/xmlschema-0/), [XML schematu część 1: zalecenie struktur](https://www.w3.org/TR/xmlschema-1/)i [XML Schematu część 2: Typy danych zalecenie](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="e91cc-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="e91cc-109">W poniższym przykładzie pokazano schematu XML gdzie `customers` jest elementem podrzędnym `MyDataSet` elementu, który jest **DataSet** elementu.</span><span class="sxs-lookup"><span data-stu-id="e91cc-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element name="customers" >   
           <xs:complexType >  
             <xs:sequence>  
               <xs:element name="CustomerID" type="xs:integer"   
                            minOccurs="0" />  
               <xs:element name="CompanyName" type="xs:string"   
                            minOccurs="0" />  
               <xs:element name="Phone" type="xs:string" />  
             </xs:sequence>  
           </xs:complexType>  
          </xs:element>  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="e91cc-110">W powyższym przykładzie elementu `customers` jest elementem typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="e91cc-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="e91cc-111">W związku z tym definicji typu złożonego jest analizowany, a proces mapowania tworzy w poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="e91cc-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="e91cc-112">Typ danych każdej kolumny w tabeli jest pochodną typu schematu XML odpowiedniego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="e91cc-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="e91cc-113">Jeśli element `customers` jest prosty typ danych schematu XML, takie jak **całkowitą**, tabela nie jest generowany.</span><span class="sxs-lookup"><span data-stu-id="e91cc-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="e91cc-114">Tabele są tworzone tylko dla elementów najwyższego poziomu, które są typy złożone.</span><span class="sxs-lookup"><span data-stu-id="e91cc-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="e91cc-115">W poniższym schemacie XML **schematu** element ma dwa elementy podrzędne, `InStateCustomers` i `OutOfStateCustomers`.</span><span class="sxs-lookup"><span data-stu-id="e91cc-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
```xml  
<xs:schema id="SomeID"   
            xmlns=""   
            xmlns:xs="http://www.w3.org/2001/XMLSchema"   
            xmlns:msdata="urn:schemas-microsoft-com:xml-msdata">  
   <xs:element name="InStateCustomers" type="customerType" />  
   <xs:element name="OutOfStateCustomers" type="customerType" />  
    <xs:complexType name="customerType" >  
  
     </xs:complexType>  
  
   <xs:element name="MyDataSet" msdata:IsDataSet="true">  
     <xs:complexType>  
       <xs:choice maxOccurs="unbounded">  
         <xs:element ref="customers" />  
       </xs:choice>  
     </xs:complexType>  
   </xs:element>  
 </xs:schema>  
```  
  
 <span data-ttu-id="e91cc-116">Zarówno `InStateCustomers` i `OutOfStateCustomers` elementy podrzędne są elementami typu złożonego (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="e91cc-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="e91cc-117">W związku z tym, proces mapowania generuje dwóch następujących tabelach identyczne w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e91cc-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="e91cc-118">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e91cc-118">In This Section</span></span>  
 [<span data-ttu-id="e91cc-119">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="e91cc-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="e91cc-120">Opisano elementy schematu XML, używany do tworzenia unikatowych obcych kluczy ograniczeń i `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e91cc-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="e91cc-121">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="e91cc-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="e91cc-122">Opisano elementy schematu XML, używany do tworzenia relacji między kolumnami tabeli w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e91cc-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="e91cc-123">Relacje i ograniczenia schematu XML</span><span class="sxs-lookup"><span data-stu-id="e91cc-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="e91cc-124">W tym artykule opisano, jak relacje są tworzone niejawnie za pomocą elementów schematu XML do utworzenia ograniczeń `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="e91cc-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e91cc-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e91cc-125">Related Sections</span></span>  
 [<span data-ttu-id="e91cc-126">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="e91cc-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="e91cc-127">Opisuje sposób ładowania i zachować relacyjnej struktury i danych w `DataSet` jako danych XML.</span><span class="sxs-lookup"><span data-stu-id="e91cc-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e91cc-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e91cc-128">See Also</span></span>  
 [<span data-ttu-id="e91cc-129">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="e91cc-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
