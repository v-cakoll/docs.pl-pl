---
title: Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: 98c43b6af2913b9737085d2d983b37c6da4c1724
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934470"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="17dd5-102">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="17dd5-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="17dd5-103">Ta sekcja zawiera omówienie sposobu kompilowania schematu `DataSet` relacyjnego z dokumentu schematu języka definicji schematu XML (XSD).</span><span class="sxs-lookup"><span data-stu-id="17dd5-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="17dd5-104">Ogólnie rzecz biorąc dla każdego `complexType` elementu podrzędnego elementu schematu tabela jest generowana `DataSet`w.</span><span class="sxs-lookup"><span data-stu-id="17dd5-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="17dd5-105">Struktura tabeli jest określana na podstawie definicji typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="17dd5-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="17dd5-106">Tabele są tworzone w programie `DataSet` dla elementów najwyższego poziomu w schemacie.</span><span class="sxs-lookup"><span data-stu-id="17dd5-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="17dd5-107">Jednak tabela jest tworzona tylko dla elementu najwyższego poziomu `complexType` , `complexType` gdy element jest zagnieżdżony wewnątrz innego `complexType` elementu, w którym to `DataTable` przypadku `DataSet`zagnieżdżony `complexType` element jest mapowany do wewnątrz.</span><span class="sxs-lookup"><span data-stu-id="17dd5-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="17dd5-108">Aby uzyskać więcej informacji na temat XSD, zobacz temat schemat XML organizacja World Wide Web Consortium [(W3C), część 0: Zalecenie](https://www.w3.org/TR/xmlschema-0/) podstawowe[, część schematu XML 1: Zalecenia](https://www.w3.org/TR/xmlschema-1/)dotyczące struktur [oraz część 2 schematu XML: Zalecenie](https://www.w3.org/TR/xmlschema-2/)dotyczące typów danych.</span><span class="sxs-lookup"><span data-stu-id="17dd5-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="17dd5-109">Poniższy przykład ilustruje schemat XML, gdzie `customers` jest elementem `MyDataSet` podrzędnym elementu, który jest elementem **DataSet** .</span><span class="sxs-lookup"><span data-stu-id="17dd5-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="17dd5-110">W poprzednim przykładzie element `customers` jest elementem typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="17dd5-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="17dd5-111">W związku z tym definicja typu złożonego jest analizowana, a proces mapowania tworzy poniższą tabelę.</span><span class="sxs-lookup"><span data-stu-id="17dd5-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```  
Customers (CustomerID , CompanyName, Phone)  
```  
  
 <span data-ttu-id="17dd5-112">Typ danych każdej kolumny w tabeli pochodzi od typu schematu XML określonego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="17dd5-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="17dd5-113">Jeśli element `customers` składa się z prostego typu danych schematu XML, takiego jak **Integer**, nie jest generowana żadna tabela.</span><span class="sxs-lookup"><span data-stu-id="17dd5-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="17dd5-114">Tabele są tworzone tylko dla elementów najwyższego poziomu, które są typami złożonymi.</span><span class="sxs-lookup"><span data-stu-id="17dd5-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="17dd5-115">W poniższym schemacie XML element **schematu** ma dwa elementy podrzędne `InStateCustomers` elementów i. `OutOfStateCustomers`</span><span class="sxs-lookup"><span data-stu-id="17dd5-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="17dd5-116">`InStateCustomers` Elementy podrzędne`OutOfStateCustomers` i są elementami typu złożonego (`customerType`).</span><span class="sxs-lookup"><span data-stu-id="17dd5-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="17dd5-117">W związku z tym proces mapowania generuje następujące dwie identyczne tabele w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="17dd5-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```  
InStateCustomers (CustomerID , CompanyName, Phone)  
OutOfStateCustomers (CustomerID , CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="17dd5-118">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="17dd5-118">In This Section</span></span>  
 [<span data-ttu-id="17dd5-119">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="17dd5-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="17dd5-120">Opisuje elementy schematu XML używane do tworzenia ograniczeń unique i FOREIGN KEY w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="17dd5-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="17dd5-121">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="17dd5-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="17dd5-122">Opisuje elementy schematu XML używane do tworzenia relacji między kolumnami tabeli w `DataSet`.</span><span class="sxs-lookup"><span data-stu-id="17dd5-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="17dd5-123">Relacje i ograniczenia schematu XML</span><span class="sxs-lookup"><span data-stu-id="17dd5-123">XML Schema Constraints and Relationships</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="17dd5-124">Opisuje, `DataSet`w jaki sposób relacje są tworzone niejawnie podczas używania elementów schematu XML do tworzenia ograniczeń w.</span><span class="sxs-lookup"><span data-stu-id="17dd5-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="17dd5-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="17dd5-125">Related Sections</span></span>  
 [<span data-ttu-id="17dd5-126">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="17dd5-126">Using XML in a DataSet</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/using-xml-in-a-dataset.md)  
 <span data-ttu-id="17dd5-127">Opisuje sposób ładowania i utrwalania relacyjnej struktury i danych w `DataSet` postaci danych XML.</span><span class="sxs-lookup"><span data-stu-id="17dd5-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="17dd5-128">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="17dd5-128">See also</span></span>

- [<span data-ttu-id="17dd5-129">ADO.NET dostawcy zarządzani i centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="17dd5-129">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
