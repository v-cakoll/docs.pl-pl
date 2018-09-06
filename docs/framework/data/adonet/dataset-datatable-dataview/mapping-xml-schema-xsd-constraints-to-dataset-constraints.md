---
title: Mapowania XML schematów (XSD) ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: c9cd97535a0165b82f0823c1f17f621491d4255c
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/05/2018
ms.locfileid: "43748621"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="e4a79-102">Mapowania XML schematów (XSD) ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="e4a79-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="e4a79-103">Język definicji schematu XML (XSD) umożliwia ograniczenie zezwalające na można określić elementów i atrybutów, które definiuje.</span><span class="sxs-lookup"><span data-stu-id="e4a79-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="e4a79-104">Podczas mapowania schematu XML na schemat relacyjny w <xref:System.Data.DataSet>, ograniczenia schematu XML są mapowane na odpowiednie ograniczenia relacyjnych tabel i kolumn w obrębie **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="e4a79-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="e4a79-105">W tej sekcji omówiono mapowanie następujące ograniczenia schematu XML:</span><span class="sxs-lookup"><span data-stu-id="e4a79-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
-   <span data-ttu-id="e4a79-106">Ograniczenie unikatowości określony za pomocą **unikatowy** elementu.</span><span class="sxs-lookup"><span data-stu-id="e4a79-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
-   <span data-ttu-id="e4a79-107">Ograniczenie klucza określony za pomocą **klucz** elementu.</span><span class="sxs-lookup"><span data-stu-id="e4a79-107">The key constraint specified using the **key** element.</span></span>  
  
-   <span data-ttu-id="e4a79-108">Ograniczenie keyref określony za pomocą **keyref** elementu.</span><span class="sxs-lookup"><span data-stu-id="e4a79-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="e4a79-109">Za pomocą ograniczenia na element lub atrybut, można określić pewne ograniczenia na podstawie wartości elementu w żadnym wystąpieniu klasy dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e4a79-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="e4a79-110">Na przykład: ograniczenie klucza w **CustomerID** element podrzędny elementu **klienta** elementu w schemacie wskazuje, że wartości **CustomerID** musi mieć element podrzędny Unikatowy w żadnym wystąpieniu dokumentów i wartości null są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="e4a79-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="e4a79-111">Ograniczenia można również określić między elementów i atrybutów w dokumencie, aby możliwe było nawiązanie relacji w obrębie dokumentu.</span><span class="sxs-lookup"><span data-stu-id="e4a79-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="e4a79-112">Ograniczenia klucza i keyref są używane w schemacie określanie ograniczeń w dokumencie skutkuje relację między dokumentu elementów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="e4a79-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="e4a79-113">Proces mapowania konwertuje te ograniczenia schematu na odpowiednie ograniczenia w tabelach, utworzone w ramach **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="e4a79-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e4a79-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="e4a79-114">In This Section</span></span>  
 [<span data-ttu-id="e4a79-115">Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="e4a79-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="e4a79-116">Opisano elementy schematu XML, używany do tworzenia unikatowych ograniczeń w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="e4a79-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="e4a79-117">Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="e4a79-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="e4a79-118">Opisano elementy schematu XML użyty do utworzenia ograniczenia klucza (ograniczenia unikatowe, której wartości null są niedozwolone) **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="e4a79-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="e4a79-119">Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="e4a79-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="e4a79-120">Opisano elementy schematu XML użyty do utworzenia keyref ograniczenia (z kluczem obcym) w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="e4a79-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e4a79-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="e4a79-121">Related Sections</span></span>  
 [<span data-ttu-id="e4a79-122">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="e4a79-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="e4a79-123">W tym artykule opisano relacyjnej struktury lub schematu z **DataSet** , jest tworzona na podstawie schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="e4a79-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="e4a79-124">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="e4a79-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="e4a79-125">Opisano elementy schematu XML, używany do tworzenia relacji między kolumnami tabeli w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="e4a79-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e4a79-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e4a79-126">See Also</span></span>  
 [<span data-ttu-id="e4a79-127">ADO.NET zarządzanego dostawcy i Centrum deweloperów zestawu danych</span><span class="sxs-lookup"><span data-stu-id="e4a79-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](https://go.microsoft.com/fwlink/?LinkId=217917)
