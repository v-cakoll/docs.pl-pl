---
title: Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet
ms.date: 03/30/2017
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
ms.openlocfilehash: b44c3193e1b9e2e52e086111eab0ab0b0cae5c97
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70786078"
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="ba5a5-102">Mapowanie ograniczeń schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ba5a5-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="ba5a5-103">Język definicji schematu XML (XSD) umożliwia określenie ograniczeń dla elementów i atrybutów, które definiuje.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="ba5a5-104">Podczas mapowania schematu XML na schemat relacyjny w programie <xref:System.Data.DataSet>ograniczenia schematu XML są mapowane na odpowiednie ograniczenia relacyjne dla tabel i kolumn w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="ba5a5-105">W tej sekcji omówiono mapowanie następujących ograniczeń schematu XML:</span><span class="sxs-lookup"><span data-stu-id="ba5a5-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
- <span data-ttu-id="ba5a5-106">Ograniczenie unikatowości określone przy użyciu **unikatowego** elementu.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
- <span data-ttu-id="ba5a5-107">Ograniczenie klucza określone za pomocą elementu **Key** .</span><span class="sxs-lookup"><span data-stu-id="ba5a5-107">The key constraint specified using the **key** element.</span></span>  
  
- <span data-ttu-id="ba5a5-108">Ograniczenie keyref określone przy użyciu elementu **keyref** .</span><span class="sxs-lookup"><span data-stu-id="ba5a5-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="ba5a5-109">Przy użyciu ograniczenia dotyczącego elementu lub atrybutu należy określić pewne ograniczenia dotyczące wartości elementu w dowolnym wystąpieniu dokumentu.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="ba5a5-110">Na przykład ograniczenie klucza dla elementu podrzędnego **CustomerID** elementu **klienta** w schemacie wskazuje, że wartości elementu podrzędnego **CustomerID** muszą być unikatowe w każdym wystąpieniu dokumentu, a wartości null są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="ba5a5-111">Można również określić ograniczenia między elementami i atrybutami w dokumencie, aby określić relację w dokumencie.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="ba5a5-112">Ograniczenia Key i keyref są używane w schemacie, aby określić ograniczenia w dokumencie, co skutkuje relacją między elementami dokumentu a atrybutami.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="ba5a5-113">Proces mapowania konwertuje te ograniczenia schematu na odpowiednie ograniczenia dotyczące tabel utworzonych w ramach **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ba5a5-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="ba5a5-114">In This Section</span></span>  
 [<span data-ttu-id="ba5a5-115">Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ba5a5-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="ba5a5-116">Opisuje elementy schematu XML używane do tworzenia unikatowych ograniczeń w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="ba5a5-117">Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ba5a5-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="ba5a5-118">Opisuje elementy schematu XML używane do tworzenia ograniczeń klucza (unikatowych ograniczeń, w których wartości null są niedozwolone) w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="ba5a5-119">Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="ba5a5-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="ba5a5-120">Opisuje elementy schematu XML używane do tworzenia ograniczeń keyref (klucza obcego) w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ba5a5-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="ba5a5-121">Related Sections</span></span>  
 [<span data-ttu-id="ba5a5-122">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ba5a5-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="ba5a5-123">Opisuje strukturę relacyjną lub schemat **zestawu danych** , który jest tworzony na podstawie schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="ba5a5-124">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="ba5a5-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="ba5a5-125">Opisuje elementy schematu XML używane do tworzenia relacji między kolumnami tabeli w **zestawie danych**.</span><span class="sxs-lookup"><span data-stu-id="ba5a5-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ba5a5-126">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ba5a5-126">See also</span></span>

- [<span data-ttu-id="ba5a5-127">Omówienie ADO.NET</span><span class="sxs-lookup"><span data-stu-id="ba5a5-127">ADO.NET Overview</span></span>](../ado-net-overview.md)
