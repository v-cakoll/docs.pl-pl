---
title: Funkcja zadeklarowana modelu
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: 31efbab4b8323ff8cec9498fa20fa40b1efb819e
ms.sourcegitcommit: c6f69b0cf149f6b54483a6d5c2ece222913f43ce
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/08/2019
ms.locfileid: "55904074"
---
# <a name="model-declared-function"></a><span data-ttu-id="f0292-102">Funkcja zadeklarowana modelu</span><span class="sxs-lookup"><span data-stu-id="f0292-102">model-declared function</span></span>
<span data-ttu-id="f0292-103">A *funkcja zadeklarowana modelu* jest funkcją, która jest zadeklarowana w modelu koncepcyjnym, ale nie jest zdefiniowany w tym modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="f0292-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="f0292-104">Funkcja może być zdefiniowana w środowisku hostingu lub magazynu.</span><span class="sxs-lookup"><span data-stu-id="f0292-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="f0292-105">Na przykład funkcja zadeklarowana modelu może być mapowana do funkcji, która jest zdefiniowana w bazie danych, w związku z tym udostępnianie funkcje po stronie serwera w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="f0292-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="f0292-106">Deklaracja funkcji zadeklarowana modelu zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="f0292-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="f0292-107">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0292-107">The name of the function.</span></span> <span data-ttu-id="f0292-108">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="f0292-108">(Required)</span></span>  
  
-   <span data-ttu-id="f0292-109">Typ wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="f0292-109">The type of the return value.</span></span> <span data-ttu-id="f0292-110">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="f0292-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="f0292-111">Jeśli żadna wartość zwracana jest określony, zwracany typ jest typ void.</span><span class="sxs-lookup"><span data-stu-id="f0292-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="f0292-112">Informacje o parametrach, takie jak nazwa parametru i typu.</span><span class="sxs-lookup"><span data-stu-id="f0292-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="f0292-113">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="f0292-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="f0292-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="f0292-114">Example</span></span>  
 <span data-ttu-id="f0292-115">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="f0292-115">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="f0292-116">W CSDL, jedna implementacja funkcja zadeklarowana modelu jest importowanie funkcji (przy użyciu [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span><span class="sxs-lookup"><span data-stu-id="f0292-116">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="f0292-117">Następujące CSDL definiuje kontener jednostek, definicje importu funkcji.</span><span class="sxs-lookup"><span data-stu-id="f0292-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="f0292-118">Należy zauważyć, że zwracany typ funkcji jest nieważne, ponieważ określono bez zwrotu typu.</span><span class="sxs-lookup"><span data-stu-id="f0292-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="f0292-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f0292-119">See also</span></span>
- [<span data-ttu-id="f0292-120">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="f0292-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="f0292-121">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="f0292-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
