---
title: Funkcja zadeklarowana modelu
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: 5db7d49fd4b839cef47db8086b4ef39ce4dc6aea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54725145"
---
# <a name="model-declared-function"></a><span data-ttu-id="885e2-102">Funkcja zadeklarowana modelu</span><span class="sxs-lookup"><span data-stu-id="885e2-102">model-declared function</span></span>
<span data-ttu-id="885e2-103">A *funkcja zadeklarowana modelu* jest funkcją, która jest zadeklarowana w modelu koncepcyjnym, ale nie jest zdefiniowany w tym modelu koncepcyjnego.</span><span class="sxs-lookup"><span data-stu-id="885e2-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="885e2-104">Funkcja może być zdefiniowana w środowisku hostingu lub magazynu.</span><span class="sxs-lookup"><span data-stu-id="885e2-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="885e2-105">Na przykład funkcja zadeklarowana modelu może być mapowana do funkcji, która jest zdefiniowana w bazie danych, w związku z tym udostępnianie funkcje po stronie serwera w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="885e2-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="885e2-106">Deklaracja funkcji zadeklarowana modelu zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="885e2-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="885e2-107">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="885e2-107">The name of the function.</span></span> <span data-ttu-id="885e2-108">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="885e2-108">(Required)</span></span>  
  
-   <span data-ttu-id="885e2-109">Typ wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="885e2-109">The type of the return value.</span></span> <span data-ttu-id="885e2-110">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="885e2-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="885e2-111">Jeśli żadna wartość zwracana jest określony, zwracany typ jest typ void.</span><span class="sxs-lookup"><span data-stu-id="885e2-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="885e2-112">Informacje o parametrach, takie jak nazwa parametru i typu.</span><span class="sxs-lookup"><span data-stu-id="885e2-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="885e2-113">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="885e2-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="885e2-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="885e2-114">Example</span></span>  
 <span data-ttu-id="885e2-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL), o nazwie język definicji schematu koncepcyjnego ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="885e2-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="885e2-116">W CSDL, jest jedna implementacja funkcja zadeklarowana modelu [funkcji importu](https://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span><span class="sxs-lookup"><span data-stu-id="885e2-116">In CSDL, one implementation of a model-declared function is a [function import](https://msdn.microsoft.com/library/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="885e2-117">Następujące CSDL definiuje kontener jednostek, definicje importu funkcji.</span><span class="sxs-lookup"><span data-stu-id="885e2-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="885e2-118">Należy zauważyć, że zwracany typ funkcji jest nieważne, ponieważ określono bez zwrotu typu.</span><span class="sxs-lookup"><span data-stu-id="885e2-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="885e2-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="885e2-119">See also</span></span>
- [<span data-ttu-id="885e2-120">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="885e2-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)
- [<span data-ttu-id="885e2-121">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="885e2-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
