---
title: funkcja zadeklarowana modelu
ms.date: 03/30/2017
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
ms.openlocfilehash: cb2fca52604bd57f25469f5621c292a27638c76f
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2019
ms.locfileid: "70794797"
---
# <a name="model-declared-function"></a><span data-ttu-id="ee508-102">funkcja zadeklarowana modelu</span><span class="sxs-lookup"><span data-stu-id="ee508-102">model-declared function</span></span>
<span data-ttu-id="ee508-103">*Funkcja zadeklarowana przez model* to funkcja zadeklarowana w modelu koncepcyjnym, ale nie jest zdefiniowana w tym modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="ee508-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="ee508-104">Funkcja może być zdefiniowana w środowisku hostingu lub magazynu.</span><span class="sxs-lookup"><span data-stu-id="ee508-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="ee508-105">Na przykład funkcja zadeklarowana przez model może zostać zmapowana do funkcji, która jest zdefiniowana w bazie danych, dzięki czemu udostępnia funkcje po stronie serwera w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="ee508-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="ee508-106">Deklaracja funkcji zadeklarowanej przez model zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="ee508-106">The declaration of a model-declared function contains the following information:</span></span>  
  
- <span data-ttu-id="ee508-107">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="ee508-107">The name of the function.</span></span> <span data-ttu-id="ee508-108">Potrzeb</span><span class="sxs-lookup"><span data-stu-id="ee508-108">(Required)</span></span>  
  
- <span data-ttu-id="ee508-109">Typ wartości zwracanej.</span><span class="sxs-lookup"><span data-stu-id="ee508-109">The type of the return value.</span></span> <span data-ttu-id="ee508-110">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="ee508-110">(Optional)</span></span>  
  
    > [!NOTE]
    > <span data-ttu-id="ee508-111">Jeśli nie określono wartości zwracanej, zwracany typ to void.</span><span class="sxs-lookup"><span data-stu-id="ee508-111">If no return value is specified, the return type is void.</span></span>  
  
- <span data-ttu-id="ee508-112">Informacje o parametrach, w tym nazwa parametru i typ.</span><span class="sxs-lookup"><span data-stu-id="ee508-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="ee508-113">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="ee508-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="ee508-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="ee508-114">Example</span></span>  
 <span data-ttu-id="ee508-115">[ADO.NET Entity Framework](./ef/index.md) używa języka specyficznego dla domeny (DSL) zwanego językiem definicji schematu koncepcyjnego ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="ee508-115">The [ADO.NET Entity Framework](./ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec)) to define conceptual models.</span></span> <span data-ttu-id="ee508-116">W obszarze CSDL jedna implementacja funkcji zadeklarowanej przez model jest importem funkcji (przy użyciu [elementu FunctionImport](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span><span class="sxs-lookup"><span data-stu-id="ee508-116">In CSDL, one implementation of a model-declared function is a function import (using the [FunctionImport element](/ef/ef6/modeling/designer/advanced/edmx/csdl-spec#functionimport-element-csdl)).</span></span> <span data-ttu-id="ee508-117">Poniższy plik CSDL definiuje kontener jednostek z definicją importu funkcji.</span><span class="sxs-lookup"><span data-stu-id="ee508-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="ee508-118">Zwróć uwagę, że zwracany typ dla funkcji to void, ponieważ nie określono typu zwracanego.</span><span class="sxs-lookup"><span data-stu-id="ee508-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="ee508-119">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="ee508-119">See also</span></span>

- [<span data-ttu-id="ee508-120">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="ee508-120">Entity Data Model Key Concepts</span></span>](entity-data-model-key-concepts.md)
- [<span data-ttu-id="ee508-121">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="ee508-121">Entity Data Model</span></span>](entity-data-model.md)
