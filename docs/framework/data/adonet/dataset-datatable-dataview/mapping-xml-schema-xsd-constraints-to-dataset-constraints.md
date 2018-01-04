---
title: Ograniczenia (XSD) schematu XML mapowania do ograniczenia zestawu danych
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 3d0d1a4b-9104-434f-ac04-6c01ab5716b5
caps.latest.revision: "4"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.workload: dotnet
ms.openlocfilehash: 8ac310542ba9dea360acbc2a0fbcbb07b7a8d6fc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="mapping-xml-schema-xsd-constraints-to-dataset-constraints"></a><span data-ttu-id="161b1-102">Ograniczenia (XSD) schematu XML mapowania do ograniczenia zestawu danych</span><span class="sxs-lookup"><span data-stu-id="161b1-102">Mapping XML Schema (XSD) Constraints to DataSet Constraints</span></span>
<span data-ttu-id="161b1-103">Język definicji schematu XML (XSD) umożliwia ograniczenia określonych elementów i atrybutów, który definiuje.</span><span class="sxs-lookup"><span data-stu-id="161b1-103">The XML Schema definition language (XSD) allows constraints to be specified on the elements and attributes it defines.</span></span> <span data-ttu-id="161b1-104">Podczas mapowania schematu XML na schemat relacyjny w <xref:System.Data.DataSet>, ograniczenia schematu XML są mapowane na odpowiednich ograniczeń relacyjnych tabel i kolumn w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="161b1-104">When mapping an XML Schema to relational schema in a <xref:System.Data.DataSet>, XML Schema constraints are mapped to appropriate relational constraints on the tables and columns within the **DataSet**.</span></span>  
  
 <span data-ttu-id="161b1-105">W tej sekcji omówiono mapowanie schematu XML następujące ograniczenia:</span><span class="sxs-lookup"><span data-stu-id="161b1-105">This section discusses the mapping of the following XML Schema constraints:</span></span>  
  
-   <span data-ttu-id="161b1-106">Ograniczenie unikatowości określona za pomocą **unikatowy** elementu.</span><span class="sxs-lookup"><span data-stu-id="161b1-106">The uniqueness constraint specified using the **unique** element.</span></span>  
  
-   <span data-ttu-id="161b1-107">Ograniczenie klucza, określić przy użyciu **klucza** elementu.</span><span class="sxs-lookup"><span data-stu-id="161b1-107">The key constraint specified using the **key** element.</span></span>  
  
-   <span data-ttu-id="161b1-108">Ograniczenie keyref określona za pomocą **keyref** elementu.</span><span class="sxs-lookup"><span data-stu-id="161b1-108">The keyref constraint specified using the **keyref** element.</span></span>  
  
 <span data-ttu-id="161b1-109">Za pomocą ograniczenia na element lub atrybut, określeniu pewne ograniczenia w wartości elementu w żadnym wystąpieniu klasy dokumentu.</span><span class="sxs-lookup"><span data-stu-id="161b1-109">By using a constraint on an element or attribute, you specify certain restrictions on the values of the element in any instance of the document.</span></span> <span data-ttu-id="161b1-110">Na przykład, ograniczenie klucza na **CustomerID** elementem podrzędnym **klienta** elementu w schemacie wskazuje, że wartości **CustomerID** musi być elementem podrzędnym Unikatowy w żadnym wystąpieniu dokumentów i wartości null są niedozwolone.</span><span class="sxs-lookup"><span data-stu-id="161b1-110">For example, a key constraint on a **CustomerID** child element of a **Customer** element in the schema indicates that the values of the **CustomerID** child element must be unique in any document instance, and that null values are not allowed.</span></span>  
  
 <span data-ttu-id="161b1-111">Ograniczenia można również określić między elementów i atrybutów w dokumencie, aby ustanowić relację, w tym dokumencie.</span><span class="sxs-lookup"><span data-stu-id="161b1-111">Constraints can also be specified between elements and attributes in a document, in order to establish a relationship within the document.</span></span> <span data-ttu-id="161b1-112">Ograniczeń key i keyref są używane w schemacie można określić ograniczeń, w tym dokumencie, co w relacji między elementami dokumentu i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="161b1-112">The key and keyref constraints are used in the schema to specify the constraints within the document, resulting in a relationship between document elements and attributes.</span></span>  
  
 <span data-ttu-id="161b1-113">Proces mapowania konwertuje tych warunków ograniczających schematu na odpowiednie ograniczenia w tabelach utworzone w ramach **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="161b1-113">The mapping process converts these schema constraints into appropriate constraints on the tables created within the **DataSet**.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="161b1-114">W tej sekcji</span><span class="sxs-lookup"><span data-stu-id="161b1-114">In This Section</span></span>  
 [<span data-ttu-id="161b1-115">Mapowanie ograniczeń unique schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="161b1-115">Map unique XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-unique-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="161b1-116">Zawiera opis elementów schematu XML używany do tworzenia ograniczenia unique w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="161b1-116">Describes the XML Schema elements used to create unique constraints in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="161b1-117">Mapowanie ograniczeń key schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="161b1-117">Map key XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-key-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="161b1-118">Zawiera opis elementów schematu XML używany do tworzenia ograniczeń klucza (ograniczenia unique, której wartości null nie są dozwolone) w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="161b1-118">Describes the XML Schema elements used to create key constraints (unique constraints where null values are not allowed) in a **DataSet**.</span></span>  
  
 [<span data-ttu-id="161b1-119">Mapowanie ograniczeń keyref schematu XML (XSD) na ograniczenia elementu DataSet</span><span class="sxs-lookup"><span data-stu-id="161b1-119">Map keyref XML Schema (XSD) Constraints to DataSet Constraints</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/map-keyref-xml-schema-xsd-constraints-to-dataset-constraints.md)  
 <span data-ttu-id="161b1-120">Zawiera opis elementów schematu XML używany do tworzenia keyref ograniczeń (klucz obcy) **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="161b1-120">Describes the XML Schema elements used to create keyref (foreign key) constraints in a **DataSet**.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="161b1-121">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="161b1-121">Related Sections</span></span>  
 [<span data-ttu-id="161b1-122">Pobieranie relacyjnej struktury elementu DataSet ze schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="161b1-122">Deriving DataSet Relational Structure from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/deriving-dataset-relational-structure-from-xml-schema-xsd.md)  
 <span data-ttu-id="161b1-123">Opisuje relacyjne struktury lub schematu z **DataSet** która jest tworzona na podstawie schematu XSD.</span><span class="sxs-lookup"><span data-stu-id="161b1-123">Describes the relational structure, or schema, of a **DataSet** that is created from XSD schema.</span></span>  
  
 [<span data-ttu-id="161b1-124">Generowanie relacji elementu DataSet na podstawie schematu XML (XSD)</span><span class="sxs-lookup"><span data-stu-id="161b1-124">Generating DataSet Relations from XML Schema (XSD)</span></span>](../../../../../docs/framework/data/adonet/dataset-datatable-dataview/generating-dataset-relations-from-xml-schema-xsd.md)  
 <span data-ttu-id="161b1-125">Zawiera opis elementów schematu XML używany do tworzenia relacji między kolumnami tabeli w **zestawu danych**.</span><span class="sxs-lookup"><span data-stu-id="161b1-125">Describes the XML Schema elements used to create relations between table columns in a **DataSet**.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="161b1-126">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="161b1-126">See Also</span></span>  
 [<span data-ttu-id="161b1-127">ADO.NET zarządzanego dostawcy i zestawu danych w Centrum deweloperów</span><span class="sxs-lookup"><span data-stu-id="161b1-127">ADO.NET Managed Providers and DataSet Developer Center</span></span>](http://go.microsoft.com/fwlink/?LinkId=217917)
