---
title: funkcja zdefiniowana przez model
ms.date: 03/30/2017
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
ms.openlocfilehash: 973d7ff9f7b76650782d62dcdcab60c8cedde18f
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/07/2019
ms.locfileid: "73735579"
---
# <a name="model-defined-function"></a><span data-ttu-id="51b4b-102">funkcja zdefiniowana przez model</span><span class="sxs-lookup"><span data-stu-id="51b4b-102">model-defined function</span></span>
<span data-ttu-id="51b4b-103">*Funkcja zdefiniowana przez model* jest funkcją zdefiniowaną w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="51b4b-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="51b4b-104">Treść funkcji zdefiniowanej przez model jest wyrażona w [Entity SQL](./ef/language-reference/entity-sql-language.md), która umożliwia określenie, że funkcja ma być wyrażona niezależnie od zasad lub języków obsługiwanych w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="51b4b-104">The body of a model-defined function is expressed in [Entity SQL](./ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="51b4b-105">Definicja dla funkcji zdefiniowanej przez model zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="51b4b-105">A definition for a model-defined function contains the following information:</span></span>  
  
- <span data-ttu-id="51b4b-106">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="51b4b-106">A function name.</span></span> <span data-ttu-id="51b4b-107">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="51b4b-107">(Required)</span></span>  
  
- <span data-ttu-id="51b4b-108">Typ wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="51b4b-108">The type of the return value.</span></span> <span data-ttu-id="51b4b-109">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="51b4b-109">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="51b4b-110">Jeśli nie określono typu zwracanego, wartość zwracana to void.</span><span class="sxs-lookup"><span data-stu-id="51b4b-110">If no return type is specified, the return value is void.</span></span>  
  
- <span data-ttu-id="51b4b-111">Informacje o parametrach.</span><span class="sxs-lookup"><span data-stu-id="51b4b-111">Parameter information.</span></span> <span data-ttu-id="51b4b-112">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="51b4b-112">(Optional)</span></span>  
  
- <span data-ttu-id="51b4b-113">Wyrażenie [Entity SQL](./ef/language-reference/entity-sql-language.md) definiujące treść funkcji.</span><span class="sxs-lookup"><span data-stu-id="51b4b-113">An [Entity SQL](./ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="51b4b-114">Należy zauważyć, że funkcje zdefiniowane przez model nie obsługują parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="51b4b-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="51b4b-115">To ograniczenie jest stosowane, aby można było składać funkcje zdefiniowane przez model.</span><span class="sxs-lookup"><span data-stu-id="51b4b-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="51b4b-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="51b4b-116">Example</span></span>  
 <span data-ttu-id="51b4b-117">Na poniższym diagramie przedstawiono model koncepcyjny z trzema typami jednostek: `Book`, `Publisher`i `Author`.</span><span class="sxs-lookup"><span data-stu-id="51b4b-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 ![Zrzut ekranu, który pokazuje model z datą opublikowaną.](./media/model-defined-function/model-published-date-three-entity-types.gif)  
  
 <span data-ttu-id="51b4b-119">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="51b4b-119">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="51b4b-120">Poniższy CSDL definiuje funkcję w modelu koncepcyjnym, która zwraca liczbę lat od momentu opublikowania wystąpienia `Book` (na diagramie powyżej).</span><span class="sxs-lookup"><span data-stu-id="51b4b-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="51b4b-121">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="51b4b-121">See also</span></span>

- [<span data-ttu-id="51b4b-122">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="51b4b-122">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="51b4b-123">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="51b4b-123">Entity Data Model</span></span>](entity-data-model.md)
- [<span data-ttu-id="51b4b-124">Model danych jednostki: Typy danych pierwotnych</span><span class="sxs-lookup"><span data-stu-id="51b4b-124">Entity Data Model: Primitive Data Types</span></span>](entity-data-model-primitive-data-types.md)
