---
title: kontener jednostek
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: d2ad565ce73b2de4b10d2f15406b283a13bbef6e
ms.sourcegitcommit: 3630c2515809e6f4b7dbb697a3354efec105a5cd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/25/2019
ms.locfileid: "58409890"
---
# <a name="entity-container"></a><span data-ttu-id="a7a07-102">kontener jednostek</span><span class="sxs-lookup"><span data-stu-id="a7a07-102">entity container</span></span>
<span data-ttu-id="a7a07-103">*Kontener jednostek* jest logicznym grupowaniem [zestawy jednostek](../../../../docs/framework/data/adonet/entity-set.md), [zestawów skojarzeń](../../../../docs/framework/data/adonet/association-set.md), i [funkcji Importy](../../../../docs/framework/data/adonet/model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="a7a07-103">An *entity container* is a logical grouping of [entity sets](../../../../docs/framework/data/adonet/entity-set.md), [association sets](../../../../docs/framework/data/adonet/association-set.md), and [function imports](../../../../docs/framework/data/adonet/model-declared-function.md).</span></span>  
  
 <span data-ttu-id="a7a07-104">Wymaga spełnienia następujących warunków zdefiniowanych w modelu koncepcyjnym kontenera jednostki:</span><span class="sxs-lookup"><span data-stu-id="a7a07-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
-   <span data-ttu-id="a7a07-105">Co najmniej jedną jednostkę kontenera muszą być zdefiniowane w każdego modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="a7a07-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
-   <span data-ttu-id="a7a07-106">Kontener jednostek musi mieć unikatową nazwę w ramach każdego modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="a7a07-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="a7a07-107">Kontener jednostek można zdefiniować zestawy jednostek lub zestawów skojarzeń, które używają typów jednostek lub skojarzenia zdefiniowane w jeden lub kilka przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="a7a07-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="a7a07-108">Aby uzyskać więcej informacji, zobacz [modelu danych jednostki: Przestrzenie nazw](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="a7a07-108">For more information, see [Entity Data Model: Namespaces](../../../../docs/framework/data/adonet/entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a7a07-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="a7a07-109">Example</span></span>  
 <span data-ttu-id="a7a07-110">Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="a7a07-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="a7a07-111">Zobacz przykład dalej, aby uzyskać więcej informacji.</span><span class="sxs-lookup"><span data-stu-id="a7a07-111">See the next example for more information.</span></span>  
  
 ![Przykładowy model przy użyciu trzech typów jednostek](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="a7a07-113">Mimo że diagram nie obejmują informacji dotyczących kontenera jednostki, model koncepcyjny zdefiniuj kontener jednostek.</span><span class="sxs-lookup"><span data-stu-id="a7a07-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="a7a07-114">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa o nazwie język definicji schematu koncepcyjnego języka DSL ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="a7a07-114">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="a7a07-115">Następujące CSDL definiuje kontener jednostek dla modelu koncepcyjnego pokazano na powyższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="a7a07-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="a7a07-116">Należy pamiętać, że nazwa kontenera jednostki jest zdefiniowany w atrybut XML.</span><span class="sxs-lookup"><span data-stu-id="a7a07-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="a7a07-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="a7a07-117">See also</span></span>
- [<span data-ttu-id="a7a07-118">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="a7a07-118">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="a7a07-119">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="a7a07-119">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
