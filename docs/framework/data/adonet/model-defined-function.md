---
title: funkcja zdefiniowana przez model
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 4f98bbc9fdc19159354ec3e414c1a1c26029cb47
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645845"
---
# <a name="model-defined-function"></a><span data-ttu-id="9492f-102">funkcja zdefiniowana przez model</span><span class="sxs-lookup"><span data-stu-id="9492f-102">model-defined function</span></span>
<span data-ttu-id="9492f-103">A *funkcja zdefiniowana przez model* jest funkcją, która jest zdefiniowana w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="9492f-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="9492f-104">Treść funkcji definiowanych przez model danych jest wyrażona w [jednostki SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), co umożliwia funkcji wyrażane niezależnie od reguł lub języki obsługiwane w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="9492f-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="9492f-105">Definicja dla funkcji definiowanych przez model zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="9492f-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="9492f-106">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="9492f-106">A function name.</span></span> <span data-ttu-id="9492f-107">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="9492f-107">(Required)</span></span>  
  
- <span data-ttu-id="9492f-108">Typ wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="9492f-108">The type of the return value.</span></span> <span data-ttu-id="9492f-109">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="9492f-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="9492f-110">Jeśli żaden typ zwracany jest określony, wartość zwracana jest nieważne.</span><span class="sxs-lookup"><span data-stu-id="9492f-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="9492f-111">Informacje o parametrach.</span><span class="sxs-lookup"><span data-stu-id="9492f-111">Parameter information.</span></span> <span data-ttu-id="9492f-112">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="9492f-112">(Optional)</span></span>  
  
- <span data-ttu-id="9492f-113">[Jednostki SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) wyrażenia, który definiuje treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="9492f-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="9492f-114">Należy pamiętać, że funkcje zdefiniowane w modelu nie obsługują parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="9492f-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="9492f-115">To ograniczenie jest w miejscu, dzięki czemu mogą być składane funkcji definiowanych przez model.</span><span class="sxs-lookup"><span data-stu-id="9492f-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9492f-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="9492f-116">Example</span></span>  
 <span data-ttu-id="9492f-117">Poniższy diagram przedstawia modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="9492f-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Zrzut ekranu pokazujący model przy użyciu Data publikacji.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="9492f-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="9492f-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="9492f-120">Następujące CSDL definiuje funkcję w modelu koncepcyjnym, zwracające liczbę lat od wystąpienia `Book` (w powyższym diagramie) została opublikowana.</span><span class="sxs-lookup"><span data-stu-id="9492f-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="9492f-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="9492f-121">See also</span></span>

- [<span data-ttu-id="9492f-122">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="9492f-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="9492f-123">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="9492f-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="9492f-124">Model danych jednostki: Pierwotne typy danych</span><span class="sxs-lookup"><span data-stu-id="9492f-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
