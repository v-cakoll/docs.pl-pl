---
title: System typów (jednostka SQL)
ms.date: 03/30/2017
ms.assetid: 818a505b-a196-41dd-aaac-2ccd5f7a2f1a
ms.openlocfilehash: 0afeffd3ad180d6cc6175010140754e279988b38
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59134566"
---
# <a name="type-system-entity-sql"></a><span data-ttu-id="fc415-102">System typów (jednostka SQL)</span><span class="sxs-lookup"><span data-stu-id="fc415-102">Type System (Entity SQL)</span></span>
[!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc415-103">obsługuje wiele typów:</span><span class="sxs-lookup"><span data-stu-id="fc415-103">supports a number of types:</span></span>  
  
-   <span data-ttu-id="fc415-104">Typy pierwotne (proste), takich jak `Int32` i</span><span class="sxs-lookup"><span data-stu-id="fc415-104">Primitive (simple) types such as `Int32` and</span></span> `String.`  
  
-   <span data-ttu-id="fc415-105">Nominalna typy, które są zdefiniowane w schemacie, takie jak <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, i <xref:System.Data.Metadata.Edm.RelationshipType>.</span><span class="sxs-lookup"><span data-stu-id="fc415-105">Nominal types that are defined in the schema, such as <xref:System.Data.Metadata.Edm.EntityType>, <xref:System.Data.Metadata.Edm.ComplexType>, and <xref:System.Data.Metadata.Edm.RelationshipType>.</span></span>  
  
-   <span data-ttu-id="fc415-106">Typy anonimowe, które nie są zdefiniowane w schemacie na jawnie: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, i <xref:System.Data.Metadata.Edm.RefType>.</span><span class="sxs-lookup"><span data-stu-id="fc415-106">Anonymous types that are not defined in the schema explicitly: <xref:System.Data.Metadata.Edm.CollectionType>, <xref:System.Data.Metadata.Edm.RowType>, and <xref:System.Data.Metadata.Edm.RefType>.</span></span>  
  
 <span data-ttu-id="fc415-107">W tej sekcji omówiono typy anonimowe, które nie są zdefiniowane w schemacie na jawnie, ale są obsługiwane przez jednostki SQL.</span><span class="sxs-lookup"><span data-stu-id="fc415-107">This section discusses the anonymous types that are not defined in the schema explicitly but are supported by Entity SQL.</span></span> <span data-ttu-id="fc415-108">Informacje o typach pierwotnych i nominalną, zobacz [koncepcyjny modelu typy (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span><span class="sxs-lookup"><span data-stu-id="fc415-108">For information on primitive and nominal types, see [Conceptual Model Types (CSDL)](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#conceptual-model-types-csdl).</span></span>  
  
## <a name="rows"></a><span data-ttu-id="fc415-109">Wiersze</span><span class="sxs-lookup"><span data-stu-id="fc415-109">Rows</span></span>  
 <span data-ttu-id="fc415-110">Struktura wiersz zależy od sekwencji nazwane i wpisane elementów członkowskich, które składają się wiersz.</span><span class="sxs-lookup"><span data-stu-id="fc415-110">The structure of a row depends on the sequence of typed and named members that the row consists of.</span></span> <span data-ttu-id="fc415-111">Typ wiersza jest Brak tożsamości i nie może być dziedziczona z.</span><span class="sxs-lookup"><span data-stu-id="fc415-111">A row type has no identity and cannot be inherited from.</span></span> <span data-ttu-id="fc415-112">Wystąpienia tego samego typu wiersza są równoważne, jeżeli elementy członkowskie są odpowiednio równoważne.</span><span class="sxs-lookup"><span data-stu-id="fc415-112">Instances of the same row type are equivalent if the members are respectively equivalent.</span></span> <span data-ttu-id="fc415-113">Wiersze nie zachowanie poza ich równoważność strukturalnych i nie mają odpowiednika w środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="fc415-113">Rows have no behavior beyond their structural equivalence and have no equivalent in the common language runtime.</span></span> <span data-ttu-id="fc415-114">Zapytania może spowodować struktur, które zawierają wiersze lub kolekcji wierszy.</span><span class="sxs-lookup"><span data-stu-id="fc415-114">Queries can result in structures that contain rows or collections of rows.</span></span> <span data-ttu-id="fc415-115">Interfejs API powiązania między [!INCLUDE[esql](../../../../../../includes/esql-md.md)] zapytania i języka hosta definiuje, jak wiersze są realizowane w zapytaniu, wytworzonego wynik.</span><span class="sxs-lookup"><span data-stu-id="fc415-115">The API binding between the [!INCLUDE[esql](../../../../../../includes/esql-md.md)] queries and the host language defines how rows are realized in the query that produced the result.</span></span> <span data-ttu-id="fc415-116">Aby uzyskać informacji na temat sposobu tworzenia wystąpienia wiersza, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fc415-116">For information on how to construct a row instance, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="collections"></a><span data-ttu-id="fc415-117">Kolekcje</span><span class="sxs-lookup"><span data-stu-id="fc415-117">Collections</span></span>  
 <span data-ttu-id="fc415-118">Typy kolekcji reprezentują zero lub więcej wystąpień innych obiektów.</span><span class="sxs-lookup"><span data-stu-id="fc415-118">Collection types represent zero or more instances of other objects.</span></span> <span data-ttu-id="fc415-119">Aby uzyskać informacje na temat sposobu tworzenia kolekcji, zobacz [konstruowanie typów](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span><span class="sxs-lookup"><span data-stu-id="fc415-119">For information on how to construct collection, see [Constructing Types](../../../../../../docs/framework/data/adonet/ef/language-reference/constructing-types-entity-sql.md).</span></span>  
  
## <a name="references"></a><span data-ttu-id="fc415-120">Odwołania</span><span class="sxs-lookup"><span data-stu-id="fc415-120">References</span></span>  
 <span data-ttu-id="fc415-121">Odwołanie jest logiczną wskaźnik do określonej jednostki w zestawie określonej jednostki.</span><span class="sxs-lookup"><span data-stu-id="fc415-121">A reference is a logical pointer to a specific entity in a specific entity set.</span></span>  
  
 [!INCLUDE[esql](../../../../../../includes/esql-md.md)] <span data-ttu-id="fc415-122">obsługuje następujące operatory do konstruowania, dekonstruować i nawigowanie po odwołania:</span><span class="sxs-lookup"><span data-stu-id="fc415-122">supports the following operators to construct, deconstruct, and navigate through references:</span></span>  
  
-   [<span data-ttu-id="fc415-123">REF</span><span class="sxs-lookup"><span data-stu-id="fc415-123">REF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/ref-entity-sql.md)  
  
-   [<span data-ttu-id="fc415-124">CREATEREF</span><span class="sxs-lookup"><span data-stu-id="fc415-124">CREATEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/createref-entity-sql.md)  
  
-   [<span data-ttu-id="fc415-125">KEY</span><span class="sxs-lookup"><span data-stu-id="fc415-125">KEY</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/key-entity-sql.md)  
  
-   [<span data-ttu-id="fc415-126">DEREF</span><span class="sxs-lookup"><span data-stu-id="fc415-126">DEREF</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/deref-entity-sql.md)  
  
 <span data-ttu-id="fc415-127">Możesz przejść przez odwołanie za pomocą operatora dostępu (kropka) elementu członkowskiego (`.`).</span><span class="sxs-lookup"><span data-stu-id="fc415-127">You can navigate through a reference by using the member access (dot) operator(`.`).</span></span> <span data-ttu-id="fc415-128">Poniższy fragment kodu wyodrębnia Właściwość Id (zamówienia), przechodząc za pomocą właściwości r (odwołania).</span><span class="sxs-lookup"><span data-stu-id="fc415-128">The following snippet extracts the Id property (of Order) by navigating through the r (reference) property.</span></span>  
  
```  
select o2.r.Id   
from (select ref(o) as r from LOB.Orders as o) as o2   
```  
  
 <span data-ttu-id="fc415-129">Jeśli ma wartość odniesienia null, lub jeśli celem odwołania nie istnieje, wynikiem jest wartość null.</span><span class="sxs-lookup"><span data-stu-id="fc415-129">If the reference value is null, or if the target of the reference does not exist, the result is null.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fc415-130">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="fc415-130">See also</span></span>

- [<span data-ttu-id="fc415-131">Przegląd języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fc415-131">Entity SQL Overview</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-overview.md)
- [<span data-ttu-id="fc415-132">Odwołanie do języka Entity SQL</span><span class="sxs-lookup"><span data-stu-id="fc415-132">Entity SQL Reference</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-reference.md)
- [<span data-ttu-id="fc415-133">CAST</span><span class="sxs-lookup"><span data-stu-id="fc415-133">CAST</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/cast-entity-sql.md)
- [<span data-ttu-id="fc415-134">CSDL, SSDL i MSL specyfikacji</span><span class="sxs-lookup"><span data-stu-id="fc415-134">CSDL, SSDL, and MSL Specifications</span></span>](../../../../../../docs/framework/data/adonet/ef/language-reference/csdl-ssdl-and-msl-specifications.md)
