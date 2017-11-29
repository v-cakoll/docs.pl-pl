---
title: Funkcja zadeklarowana modelu
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: aba87f13-5685-4f6b-ad14-918e8a7d5c2a
caps.latest.revision: "3"
author: JennieHubbard
ms.author: jhubbard
manager: jhubbard
ms.openlocfilehash: 0e47c89524bf149d862ae872c0c5956b7debd818
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="model-declared-function"></a><span data-ttu-id="2e373-102">Funkcja zadeklarowana modelu</span><span class="sxs-lookup"><span data-stu-id="2e373-102">model-declared function</span></span>
<span data-ttu-id="2e373-103">A *funkcja zadeklarowana modelu* to funkcja, która jest zadeklarowana w modelu koncepcyjnym, ale nie jest zdefiniowany w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2e373-103">A *model-declared function* is a function that is declared in a conceptual model, but is not defined in that conceptual model.</span></span> <span data-ttu-id="2e373-104">Funkcja może być zdefiniowana w środowisku obsługującym lub magazynu.</span><span class="sxs-lookup"><span data-stu-id="2e373-104">The function might be defined in the hosting or storage environment.</span></span> <span data-ttu-id="2e373-105">Na przykład funkcja zadeklarowana modelu może być mapowana na funkcję, która jest zdefiniowana w bazie danych, w związku z tym udostępnianie funkcje po stronie serwera w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="2e373-105">For example, a model-declared function might be mapped to a function that is defined in a database, thus exposing server-side functionality in the conceptual model.</span></span>  
  
 <span data-ttu-id="2e373-106">Deklaracja funkcji zadeklarowany modelu zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="2e373-106">The declaration of a model-declared function contains the following information:</span></span>  
  
-   <span data-ttu-id="2e373-107">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="2e373-107">The name of the function.</span></span> <span data-ttu-id="2e373-108">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="2e373-108">(Required)</span></span>  
  
-   <span data-ttu-id="2e373-109">Typ zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="2e373-109">The type of the return value.</span></span> <span data-ttu-id="2e373-110">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="2e373-110">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="2e373-111">Jeśli wartość zwrotu nie zostanie określona, typ zwracany jest typ void.</span><span class="sxs-lookup"><span data-stu-id="2e373-111">If no return value is specified, the return type is void.</span></span>  
  
-   <span data-ttu-id="2e373-112">Informacje o parametrach, jak nazwa parametru typu.</span><span class="sxs-lookup"><span data-stu-id="2e373-112">Parameter information, including parameter name and type.</span></span> <span data-ttu-id="2e373-113">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="2e373-113">(Optional)</span></span>  
  
## <a name="example"></a><span data-ttu-id="2e373-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="2e373-114">Example</span></span>  
 <span data-ttu-id="2e373-115">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="2e373-115">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="2e373-116">W pliku CSDL, jest jedna implementacja funkcji zadeklarowany modelu [import funkcji](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d).</span><span class="sxs-lookup"><span data-stu-id="2e373-116">In CSDL, one implementation of a model-declared function is a [function import](http://msdn.microsoft.com/en-us/125704ae-56c7-4233-80b7-389a10f3a65d).</span></span> <span data-ttu-id="2e373-117">Następujący plik CSDL definiuje kontenera jednostek z definicji funkcji importu.</span><span class="sxs-lookup"><span data-stu-id="2e373-117">The following CSDL defines an entity container with a function import definition.</span></span> <span data-ttu-id="2e373-118">Należy pamiętać, że typ zwracany dla funkcji void, ponieważ nie zwracany określono typu.</span><span class="sxs-lookup"><span data-stu-id="2e373-118">Note that the return type for the function is void since no return type is specified.</span></span>  
  
 [!code-xml[EDM_Example_Model#FunctionImport](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#functionimport)]  
  
## <a name="see-also"></a><span data-ttu-id="2e373-119">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2e373-119">See Also</span></span>  
 [<span data-ttu-id="2e373-120">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="2e373-120">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="2e373-121">Modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="2e373-121">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
