---
title: kontener jednostek
ms.date: 03/30/2017
ms.assetid: 16e80405-2c75-42fc-b0e4-b1df53b1c584
ms.openlocfilehash: 95740fb9d8b357a4fa160af6fdafb139711283cd
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70795259"
---
# <a name="entity-container"></a><span data-ttu-id="36480-102">kontener jednostek</span><span class="sxs-lookup"><span data-stu-id="36480-102">entity container</span></span>
<span data-ttu-id="36480-103">*Kontener jednostek* jest logiczną grupą [zestawów jednostek](entity-set.md), [zestawów skojarzeń](association-set.md)i [importów funkcji](model-declared-function.md).</span><span class="sxs-lookup"><span data-stu-id="36480-103">An *entity container* is a logical grouping of [entity sets](entity-set.md), [association sets](association-set.md), and [function imports](model-declared-function.md).</span></span>  
  
 <span data-ttu-id="36480-104">Następujące elementy muszą mieć wartość true kontenera Entity zdefiniowanego w modelu koncepcyjnym:</span><span class="sxs-lookup"><span data-stu-id="36480-104">The following must be true of an entity container defined in a conceptual model:</span></span>  
  
- <span data-ttu-id="36480-105">W każdym modelu koncepcyjnym musi być zdefiniowany co najmniej jeden kontener jednostek.</span><span class="sxs-lookup"><span data-stu-id="36480-105">At least one entity container must be defined in each conceptual model.</span></span>  
  
- <span data-ttu-id="36480-106">Kontener jednostek musi mieć unikatową nazwę w ramach każdego modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="36480-106">The entity container must have a unique name within each conceptual model.</span></span>  
  
 <span data-ttu-id="36480-107">Kontener jednostek może definiować zestawy jednostek lub zestawy skojarzeń, które używają typów jednostek lub skojarzeń zdefiniowanych w co najmniej jednym obszarze nazw.</span><span class="sxs-lookup"><span data-stu-id="36480-107">An entity container can define entity sets or association sets that use entity types or associations defined in one or more namespaces.</span></span> <span data-ttu-id="36480-108">Aby uzyskać więcej informacji, [zobacz Entity Data Model: Przestrzenie nazw](entity-data-model-namespaces.md).</span><span class="sxs-lookup"><span data-stu-id="36480-108">For more information, see [Entity Data Model: Namespaces](entity-data-model-namespaces.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="36480-109">Przykład</span><span class="sxs-lookup"><span data-stu-id="36480-109">Example</span></span>  
 <span data-ttu-id="36480-110">Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.</span><span class="sxs-lookup"><span data-stu-id="36480-110">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  <span data-ttu-id="36480-111">Aby uzyskać więcej informacji, zobacz następny przykład.</span><span class="sxs-lookup"><span data-stu-id="36480-111">See the next example for more information.</span></span>  
  
 ![Przykładowy model z trzema typami jednostek](./media/entity-container/example-model-three-entity-types.gif)  
  
 <span data-ttu-id="36480-113">Chociaż diagram nie przekazuje informacji kontenera jednostki, model koncepcyjny musi definiować kontener jednostek.</span><span class="sxs-lookup"><span data-stu-id="36480-113">Although the diagram does not convey entity container information, the conceptual model must define an entity container.</span></span> <span data-ttu-id="36480-114">[ADO.NET Entity Framework](./ef/index.md) używa języka DSL o nazwie koncepcyjny schemat definicji schematu ([CSDL](./ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="36480-114">The [ADO.NET Entity Framework](./ef/index.md) uses a DSL called conceptual schema definition language ([CSDL](./ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="36480-115">Następujący CSDL definiuje kontener jednostek dla modelu koncepcyjnego przedstawiony na powyższym diagramie.</span><span class="sxs-lookup"><span data-stu-id="36480-115">The following CSDL defines an entity container for the conceptual model shown in the diagram above.</span></span> <span data-ttu-id="36480-116">Należy zauważyć, że nazwa kontenera jednostek jest zdefiniowana w atrybucie XML.</span><span class="sxs-lookup"><span data-stu-id="36480-116">Note that the entity container name is defined in an XML attribute.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityContainerExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entitycontainerexample)]  
  
## <a name="see-also"></a><span data-ttu-id="36480-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="36480-117">See also</span></span>

- [<span data-ttu-id="36480-118">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="36480-118">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="36480-119">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="36480-119">Entity Data Model</span></span>](entity-data-model.md)
