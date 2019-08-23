---
title: funkcja zdefiniowana przez model
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 05a44e86a118b649490cde849c8ca2c2bb0d2f15
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69934520"
---
# <a name="model-defined-function"></a><span data-ttu-id="e7da5-102">funkcja zdefiniowana przez model</span><span class="sxs-lookup"><span data-stu-id="e7da5-102">model-defined function</span></span>
<span data-ttu-id="e7da5-103">*Funkcja zdefiniowana przez model* jest funkcją zdefiniowaną w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="e7da5-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="e7da5-104">Treść funkcji zdefiniowanej przez model jest wyrażona w [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), która umożliwia określenie, że funkcja ma być wyrażona niezależnie od zasad lub języków obsługiwanych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="e7da5-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="e7da5-105">Definicja dla funkcji zdefiniowanej przez model zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="e7da5-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="e7da5-106">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="e7da5-106">A function name.</span></span> <span data-ttu-id="e7da5-107">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="e7da5-107">(Required)</span></span>  
  
- <span data-ttu-id="e7da5-108">Typ wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="e7da5-108">The type of the return value.</span></span> <span data-ttu-id="e7da5-109">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e7da5-109">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="e7da5-110">Jeśli nie określono typu zwracanego, wartość zwracana to void.</span><span class="sxs-lookup"><span data-stu-id="e7da5-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="e7da5-111">Informacje o parametrach.</span><span class="sxs-lookup"><span data-stu-id="e7da5-111">Parameter information.</span></span> <span data-ttu-id="e7da5-112">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="e7da5-112">(Optional)</span></span>  
  
- <span data-ttu-id="e7da5-113">Wyrażenie [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) definiujące treść funkcji.</span><span class="sxs-lookup"><span data-stu-id="e7da5-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="e7da5-114">Należy zauważyć, że funkcje zdefiniowane przez model nie obsługują parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="e7da5-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="e7da5-115">To ograniczenie jest stosowane, aby można było składać funkcje zdefiniowane przez model.</span><span class="sxs-lookup"><span data-stu-id="e7da5-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e7da5-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="e7da5-116">Example</span></span>  
 <span data-ttu-id="e7da5-117">Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.</span><span class="sxs-lookup"><span data-stu-id="e7da5-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Zrzut ekranu, który pokazuje model z datą opublikowaną.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="e7da5-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="e7da5-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="e7da5-120">Poniższy CSDL definiuje funkcję w modelu koncepcyjnym, która zwraca liczbę lat od momentu opublikowania wystąpienia `Book` obiektu (na diagramie powyżej).</span><span class="sxs-lookup"><span data-stu-id="e7da5-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="e7da5-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e7da5-121">See also</span></span>

- [<span data-ttu-id="e7da5-122">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="e7da5-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="e7da5-123">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="e7da5-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
- [<span data-ttu-id="e7da5-124">Entity Data Model: Typy danych pierwotnych</span><span class="sxs-lookup"><span data-stu-id="e7da5-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
