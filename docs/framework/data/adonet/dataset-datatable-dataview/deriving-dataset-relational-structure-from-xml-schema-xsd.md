---
title: Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)
ms.date: 03/30/2017
ms.assetid: 8f6cd04d-6197-4bc4-9096-8c51c7e4acae
ms.openlocfilehash: d32b5cb86bc5a138f9a5f438629d8e231be4ba94
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79151172"
---
# <a name="deriving-dataset-relational-structure-from-xml-schema-xsd"></a><span data-ttu-id="7330a-102">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="7330a-102">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>
<span data-ttu-id="7330a-103">Ta sekcja zawiera omówienie sposobu, w `DataSet` jaki schemat relacyjny a jest zbudowany z dokumentu schematu języka XSD (XSD) języka schematu schematu schematu XMD.</span><span class="sxs-lookup"><span data-stu-id="7330a-103">This section provides an overview of how the relational schema of a `DataSet` is built from an XML Schema definition language (XSD) schema document.</span></span> <span data-ttu-id="7330a-104">Ogólnie rzecz biorąc `complexType` dla każdego elementu podrzędnego elementu schematu `DataSet`tabela jest generowana w pliku .</span><span class="sxs-lookup"><span data-stu-id="7330a-104">In general, for each `complexType` child element of a schema element, a table is generated in the `DataSet`.</span></span> <span data-ttu-id="7330a-105">Struktura tabeli jest określana przez definicję typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="7330a-105">The table structure is determined by the definition of the complex type.</span></span> <span data-ttu-id="7330a-106">Tabele są `DataSet` tworzone w forach elementów najwyższego poziomu w schemacie.</span><span class="sxs-lookup"><span data-stu-id="7330a-106">Tables are created in the `DataSet` for top-level elements in the schema.</span></span> <span data-ttu-id="7330a-107">Jednak tabela jest tworzona tylko `complexType` dla `complexType` elementu najwyższego poziomu, gdy element jest `complexType` zagnieżdżony `DataTable` wewnątrz `DataSet`innego `complexType` elementu, w którym to przypadku zagnieżdżony element jest mapowany na w obrębie . .</span><span class="sxs-lookup"><span data-stu-id="7330a-107">However, a table is only created for a top-level `complexType` element when the `complexType` element is nested inside another `complexType` element, in which case the nested `complexType` element is mapped to a `DataTable` within the `DataSet`.</span></span>  
  
 <span data-ttu-id="7330a-108">Aby uzyskać więcej informacji na temat XSD, zobacz World Wide Web Consortium (W3C) [XML Schema Część 0: Primer Zalecenie](https://www.w3.org/TR/xmlschema-0/), [Schemat XML Część 1: Zalecenia struktur](https://www.w3.org/TR/xmlschema-1/)i Schemat [XML Część 2: Datatypes Zalecenie](https://www.w3.org/TR/xmlschema-2/).</span><span class="sxs-lookup"><span data-stu-id="7330a-108">For more information about the XSD, see the World Wide Web Consortium (W3C) [XML Schema Part 0: Primer Recommendation](https://www.w3.org/TR/xmlschema-0/), the [XML Schema Part 1: Structures Recommendation](https://www.w3.org/TR/xmlschema-1/), and the [XML Schema Part 2: Datatypes Recommendation](https://www.w3.org/TR/xmlschema-2/).</span></span>  
  
 <span data-ttu-id="7330a-109">Poniższy przykład pokazuje schemat XML, gdzie `customers` jest `MyDataSet` elementem podrzędnym elementu, który jest **elementem DataSet.**</span><span class="sxs-lookup"><span data-stu-id="7330a-109">The following example demonstrates an XML Schema where `customers` is the child element of the `MyDataSet` element, which is a **DataSet** element.</span></span>  
  
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
  
 <span data-ttu-id="7330a-110">W poprzednim przykładzie element `customers` jest elementem typu złożonego.</span><span class="sxs-lookup"><span data-stu-id="7330a-110">In the preceding example, the element `customers` is a complex type element.</span></span> <span data-ttu-id="7330a-111">W związku z tym definicja typu złożonego jest analizowana, a proces mapowania tworzy następującą tabelę.</span><span class="sxs-lookup"><span data-stu-id="7330a-111">Therefore, the complex type definition is parsed, and the mapping process creates the following table.</span></span>  
  
```text  
Customers (CustomerID, CompanyName, Phone)  
```  
  
 <span data-ttu-id="7330a-112">Typ danych każdej kolumny w tabeli jest pochodną typu schematu XML odpowiedniego określonego elementu lub atrybutu.</span><span class="sxs-lookup"><span data-stu-id="7330a-112">The data type of each column in the table is derived from the XML Schema type of the corresponding element or attribute specified.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7330a-113">Jeśli element `customers` ma prosty typ danych schematu XML, taki jak **liczba całkowita,** nie jest generowana żadna tabela.</span><span class="sxs-lookup"><span data-stu-id="7330a-113">If the element `customers` is of a simple XML Schema data type such as **integer**, no table is generated.</span></span> <span data-ttu-id="7330a-114">Tabele są tworzone tylko dla elementów najwyższego poziomu, które są typami złożonymi.</span><span class="sxs-lookup"><span data-stu-id="7330a-114">Tables are only created for the top-level elements that are complex types.</span></span>  
  
 <span data-ttu-id="7330a-115">W poniższym schemacie XML element **Schemat** ma `InStateCustomers` `OutOfStateCustomers`dwa elementy podrzędne i .</span><span class="sxs-lookup"><span data-stu-id="7330a-115">In the following XML Schema, the **Schema** element has two element children, `InStateCustomers` and `OutOfStateCustomers`.</span></span>  
  
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
  
 <span data-ttu-id="7330a-116">Zarówno `InStateCustomers` elementy `OutOfStateCustomers` podrzędne, jak i`customerType`elementy podrzędne są złożonymi elementami typu ( ).</span><span class="sxs-lookup"><span data-stu-id="7330a-116">Both the `InStateCustomers` and the `OutOfStateCustomers` child elements are complex type elements (`customerType`).</span></span> <span data-ttu-id="7330a-117">W związku z tym proces mapowania generuje `DataSet`następujące dwie identyczne tabele w .</span><span class="sxs-lookup"><span data-stu-id="7330a-117">Therefore, the mapping process generates the following two identical tables in the `DataSet`.</span></span>  
  
```text  
InStateCustomers (CustomerID, CompanyName, Phone)  
OutOfStateCustomers (CustomerID, CompanyName, Phone)  
```  
  
## <a name="in-this-section"></a><span data-ttu-id="7330a-118">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="7330a-118">In This Section</span></span>  
 [<span data-ttu-id="7330a-119">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="7330a-119">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>](mapping-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="7330a-120">W tym artykule opisano elementy schematu XML używane `DataSet`do tworzenia unikatowych i obcych ograniczeń klucza w pliku .</span><span class="sxs-lookup"><span data-stu-id="7330a-120">Describes the XML Schema elements used to create unique and foreign key constraints in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="7330a-121">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="7330a-121">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="7330a-122">Opisuje elementy schematu XML używane do tworzenia relacji `DataSet`między kolumnami tabel w programie .</span><span class="sxs-lookup"><span data-stu-id="7330a-122">Describes the XML Schema elements used to create relations between table columns in a `DataSet`.</span></span>  
  
 [<span data-ttu-id="7330a-123">Relacje i ograniczenia schematu XML</span><span class="sxs-lookup"><span data-stu-id="7330a-123">XML Schema Constraints and Relationships</span></span>](xml-schema-constraints-and-relationships.md)  
 <span data-ttu-id="7330a-124">Opisuje, jak relacje są tworzone niejawnie podczas tworzenia ograniczeń `DataSet`przy użyciu elementów schematu XML w programie .</span><span class="sxs-lookup"><span data-stu-id="7330a-124">Describes how relations are created implicitly when using XML Schema elements to create constraints in a `DataSet`.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="7330a-125">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="7330a-125">Related Sections</span></span>  
 [<span data-ttu-id="7330a-126">Używanie języka XML w elemencie DataSet</span><span class="sxs-lookup"><span data-stu-id="7330a-126">Using XML in a DataSet</span></span>](using-xml-in-a-dataset.md)  
 <span data-ttu-id="7330a-127">Opisuje sposób ładowania i utrwalania relacyjnej struktury i danych w `DataSet` danych XML jako.</span><span class="sxs-lookup"><span data-stu-id="7330a-127">Describes how to load and persist the relational structure and data in a `DataSet` as XML data.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7330a-128">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7330a-128">See also</span></span>

- [<span data-ttu-id="7330a-129">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="7330a-129">ADO.NET Overview</span></span>](../ado-net-overview.md)
