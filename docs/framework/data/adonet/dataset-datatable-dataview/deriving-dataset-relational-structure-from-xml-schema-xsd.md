---
title: Wyprowadzanie relacyjne struktury zestawu danych z schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 7599577c4e0f485e336e7f79a6c3bd17f0f0c316
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/03/2018
ms.locfileid: "32759611"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="efb86-102">Wyprowadzanie relacyjne struktury zestawu danych z schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="efb86-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="efb86-103">Ta sekcja zawiera omówienie sposobu schemat relacyjny `DataSet` składa się z dokument schematu schematu XML definition language (XSD).</span><span class="sxs-lookup"><span data-stu-id="efb86-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="efb86-104">Ogólnie rzecz biorąc, dla każdego `complexType` elementem podrzędnym elementu schematu, tabeli jest generowana w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="efb86-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="efb86-105">Struktura tabeli jest określany przez definicję typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="efb86-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="efb86-106">Tabele są tworzone w `DataSet` dla elementów najwyższego poziomu w schemacie.</span><span class="sxs-lookup"><span data-stu-id="efb86-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="efb86-107">Jednak tabeli jest tworzony tylko dla najwyższego poziomu `complexType` elementu po `complexType` element jest zagnieżdżony w innym `complexType` element, w którym to przypadku zagnieżdżone `complexType` element jest zamapowany na `DataTable` w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="efb86-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="efb86-108">Aby uzyskać więcej informacji na temat XSD, zobacz część schematu XML sieci World Wide Web konsorcjum W3C 0: zalecenie Elementarz, część 1 schematu XML: zalecenie struktury i część 2 schematu XML: zalecenie typy danych, w lokalizacji [ http://www.w3.org/ ](http://www.w3.org/TR/).</span><span class="sxs-lookup"><span data-stu-id="efb86-108">For more information about the XSD, see the World Wide Web Consortium (W3C) XML Schema Part 0: Primer Recommendation, the XML Schema Part 1: Structures Recommendation, and the XML Schema Part 2: Datatypes Recommendation, located at [http://www.w3.org/](http://www.w3.org/TR/).</span></span>  
  
 <span data-ttu-id="efb86-109">W poniższym przykładzie pokazano schematu XML gdzie `customers` jest elementem podrzędnym `MyDataSet` element, który jest **DataSet** elementu.</span><span class="sxs-lookup"><span data-stu-id="efb86-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="efb86-110">W powyższym przykładzie element `customers` jest elementem typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="efb86-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="efb86-111">W związku z tym jest analizowana definicję typu złożonego, a proces mapowania tworzy poniższej tabeli.</span><span class="sxs-lookup"><span data-stu-id="efb86-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="efb86-112">Typ danych każdej kolumny w tabeli pochodzi od typu schematu XML odpowiadającego mu elementu lub atrybutu określony.</span><span class="sxs-lookup"><span data-stu-id="efb86-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="efb86-113">Jeśli element `customers` jest proste schematu XML typu danych, takich jak **całkowitą**, tabela nie zostanie wygenerowany.</span><span class="sxs-lookup"><span data-stu-id="efb86-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="efb86-114">Tabele są tworzone tylko dla elementów najwyższego poziomu, które są typami złożonymi.</span><span class="sxs-lookup"><span data-stu-id="efb86-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="efb86-115">W schemacie XML następujące **schematu** element ma dwa elementy podrzędne elementu `InStateCustomers` i `OutOfStateCustomers`.</span><span class="sxs-lookup"><span data-stu-id="efb86-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="efb86-116">Zarówno `InStateCustomers` i `OutOfStateCustomers` elementy podrzędne są elementami typu złożonego (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="efb86-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="efb86-117">W związku z tym, proces mapowania generuje dwóch poniższych tabelach identyczne w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="efb86-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="efb86-118">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="efb86-118">In This Section</span></span>  
 [<span data-ttu-id="efb86-119">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="efb86-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="efb86-120">Zawiera opis elementów schematu XML używany do tworzenia unikatowych obcego klucza ograniczeń i `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="efb86-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="efb86-121">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="efb86-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="efb86-122">Zawiera opis elementów schematu XML używany do tworzenia relacji między kolumnami tabeli w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="efb86-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="efb86-123">Relacje i ograniczenia schematu XML</span><span class="sxs-lookup"><span data-stu-id="efb86-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="efb86-124">W tym artykule opisano, jak relacje są tworzone niejawnie podczas za pomocą elementów schematu XML, aby utworzyć ograniczenia w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="efb86-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="efb86-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="efb86-125">Related Sections</span></span>  
 [<span data-ttu-id="efb86-126">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="efb86-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="efb86-127">Opisuje sposób obciążenia i zachować relacyjne struktury i dane w `DataSet` danych XML.</span><span class="sxs-lookup"><span data-stu-id="efb86-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="efb86-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="efb86-128">See Also</span></span>  
 [<span data-ttu-id="efb86-129">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="efb86-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
