---
title: funkcja zdefiniowana przez model
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 8bb2edc8-e8e7-44c2-adc7-f44e11bda4f0
caps.latest.revision: "3"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: e1c9d438840a0b9c15597177ca4e6d870d526756
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="model-defined-function"></a><span data-ttu-id="bb2bd-102">funkcja zdefiniowana przez model</span><span class="sxs-lookup"><span data-stu-id="bb2bd-102">model-defined function</span></span>
<span data-ttu-id="bb2bd-103">A *funkcja zdefiniowana przez model* jest funkcją, która jest zdefiniowana w modelu koncepcyjnym.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-103">A *model-defined function* is a function that is defined in a conceptual model.</span></span> <span data-ttu-id="bb2bd-104">Treść funkcji zdefiniowanej przez model jest wyrażony w [SQL jednostki](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), dzięki czemu funkcję wyrażane niezależnie od zasady lub języki obsługiwane w źródle danych.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-104">The body of a model-defined function is expressed in [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md), which allows for the function to be expressed independently of rules or languages supported in the data source.</span></span>  
  
 <span data-ttu-id="bb2bd-105">Definicji dla funkcji zdefiniowanej przez model zawiera następujące informacje:</span><span class="sxs-lookup"><span data-stu-id="bb2bd-105">A definition for a model-defined function contains the following information:</span></span>  
  
-   <span data-ttu-id="bb2bd-106">Nazwa funkcji.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-106">A function name.</span></span> <span data-ttu-id="bb2bd-107">(Wymagane)</span><span class="sxs-lookup"><span data-stu-id="bb2bd-107">(Required)</span></span>  
  
-   <span data-ttu-id="bb2bd-108">Typ zwracanej wartości.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-108">The type of the return value.</span></span> <span data-ttu-id="bb2bd-109">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="bb2bd-109">(Optional)</span></span>  
  
    > [!NOTE]
    >  <span data-ttu-id="bb2bd-110">Jeśli żaden typ zwracany jest określony, wartość zwracana jest nieważne.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-110">If no return type is specified, the return value is void.</span></span>  
  
-   <span data-ttu-id="bb2bd-111">Informacje o parametrach.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-111">Parameter information.</span></span> <span data-ttu-id="bb2bd-112">(opcjonalnie)</span><span class="sxs-lookup"><span data-stu-id="bb2bd-112">(Optional)</span></span>  
  
-   <span data-ttu-id="bb2bd-113">[SQL jednostki](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) wyrażenie definiujące treści funkcji.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-113">An [Entity SQL](../../../../docs/framework/data/adonet/ef/language-reference/entity-sql-language.md) expression that defines the body of the function.</span></span>  
  
 <span data-ttu-id="bb2bd-114">Należy pamiętać, że funkcje zdefiniowane przez model nie obsługują parametrów wyjściowych.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-114">Note that model-defined functions do not support output parameters.</span></span> <span data-ttu-id="bb2bd-115">To ograniczenie jest w miejscu, dzięki czemu mogą być składane funkcje zdefiniowane przez model.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-115">This restriction is in place so that model-defined functions can be composed.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bb2bd-116">Przykład</span><span class="sxs-lookup"><span data-stu-id="bb2bd-116">Example</span></span>  
 <span data-ttu-id="bb2bd-117">Na poniższym diagramie przedstawiono modelu koncepcyjnego z trzech typów jednostek: `Book`, `Publisher`, i `Author`.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-117">The diagram below shows a conceptual model with three entity types: `Book`, `Publisher`, and `Author`.</span></span>  
  
 <span data-ttu-id="bb2bd-118">![Modelu z Data opublikowania](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span><span class="sxs-lookup"><span data-stu-id="bb2bd-118">![Model With Published Date](../../../../docs/framework/data/adonet/media/modelwithpublisheddate.gif "ModelWithPublishedDate")</span></span>  
  
 <span data-ttu-id="bb2bd-119">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-119">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="bb2bd-120">Następujący plik CSDL definiuje funkcję w modelu koncepcyjnym zwracające liczbę lat od wystąpienia `Book` (na powyższym diagramie) został opublikowany.</span><span class="sxs-lookup"><span data-stu-id="bb2bd-120">The following CSDL defines a function in the conceptual model that returns the numbers of years since an instance of a `Book` (in the diagram above) was published.</span></span>  
  
 [!code-xml[EDM_Example_Model#ModelDefinedFunction](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books4.edmx#modeldefinedfunction)]  
  
## <a name="see-also"></a><span data-ttu-id="bb2bd-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bb2bd-121">See Also</span></span>  
 [<span data-ttu-id="bb2bd-122">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="bb2bd-122">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="bb2bd-123">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="bb2bd-123">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)  
 [<span data-ttu-id="bb2bd-124">Model danych jednostki: Typy danych pierwotnych</span><span class="sxs-lookup"><span data-stu-id="bb2bd-124">Entity Data Model: Primitive Data Types</span></span>](../../../../docs/framework/data/adonet/entity-data-model-primitive-data-types.md)
