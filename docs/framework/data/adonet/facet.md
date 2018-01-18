---
title: facet
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-ado
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 91c4e6aa-3e54-4b6c-a38a-abf27808cc85
caps.latest.revision: "2"
author: douglaslMS
ms.author: douglasl
manager: craigg
ms.workload: dotnet
ms.openlocfilehash: 23346fe2095cea2b3f0d705c7d6d8914c35c06f7
ms.sourcegitcommit: ed26cfef4e18f6d93ab822d8c29f902cff3519d1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/17/2018
---
# <a name="facet"></a><span data-ttu-id="b54c1-102">facet</span><span class="sxs-lookup"><span data-stu-id="b54c1-102">facet</span></span>
<span data-ttu-id="b54c1-103">A *aspektu* służy do dodawania szczegółów do definicji właściwości typu pierwotnego.</span><span class="sxs-lookup"><span data-stu-id="b54c1-103">A *facet* is used to add detail to a primitive type property definition.</span></span> <span data-ttu-id="b54c1-104">A [właściwości](../../../../docs/framework/data/adonet/property.md) definicja zawiera informacje o typie właściwości, ale często konieczne jest bardziej szczegółowo.</span><span class="sxs-lookup"><span data-stu-id="b54c1-104">A [property](../../../../docs/framework/data/adonet/property.md) definition contains information about the property type, but often more detail is necessary.</span></span> <span data-ttu-id="b54c1-105">Na przykład typ jednostki w modelu koncepcyjnym może mieć właściwość typu `String` wartości, których nie można ustawić na wartość null.</span><span class="sxs-lookup"><span data-stu-id="b54c1-105">For example, an entity type in a conceptual model might have a property of type `String` whose value cannot be set to null.</span></span> <span data-ttu-id="b54c1-106">Aspekty umożliwiają określenie ten poziom szczegółowości.</span><span class="sxs-lookup"><span data-stu-id="b54c1-106">Facets allow you to specify this level of detail.</span></span>  
  
 <span data-ttu-id="b54c1-107">W poniższej tabeli opisano aspekty, które są obsługiwane w EDM.</span><span class="sxs-lookup"><span data-stu-id="b54c1-107">The table below describes the facets that are supported in the EDM.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="b54c1-108">Dokładne wartości i zachowania aspekty są określane przez środowisko wykonawcze, z którego korzysta implementację EDM.</span><span class="sxs-lookup"><span data-stu-id="b54c1-108">The exact values and behaviors of facets are determined by the run-time environment that uses an EDM implementation.</span></span>  
  
|<span data-ttu-id="b54c1-109">Aspekt</span><span class="sxs-lookup"><span data-stu-id="b54c1-109">Facet</span></span>|<span data-ttu-id="b54c1-110">Opis</span><span class="sxs-lookup"><span data-stu-id="b54c1-110">Description</span></span>|<span data-ttu-id="b54c1-111">Informacje zawarte w tym artykule dotyczą</span><span class="sxs-lookup"><span data-stu-id="b54c1-111">Applies to</span></span>|  
|-----------|-----------------|----------------|  
|`Collation`|<span data-ttu-id="b54c1-112">Określa kolejność sortowania (lub sekwencji sortowania) do użycia podczas wykonywania porównania i kolejność operacji na wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="b54c1-112">Specifies the collating sequence (or sorting sequence) to be used when performing comparison and ordering operations on values of the property.</span></span>|`String`|  
|`ConcurrencyMode`|<span data-ttu-id="b54c1-113">Wskazuje, że wartość właściwości powinny być używane do kontroli optymistycznej współbieżności.</span><span class="sxs-lookup"><span data-stu-id="b54c1-113">Indicates that the value of the property should be used for optimistic concurrency checks.</span></span>|<span data-ttu-id="b54c1-114">Wszystkie właściwości typu pierwotnego</span><span class="sxs-lookup"><span data-stu-id="b54c1-114">All primitive type properties</span></span>|  
|`Default`|<span data-ttu-id="b54c1-115">Określa wartość domyślną właściwości, jeśli żadna wartość nie jest dostarczony na wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="b54c1-115">Specifies the default value of the property if no value is supplied upon instantiation.</span></span>|<span data-ttu-id="b54c1-116">Wszystkie właściwości typu pierwotnego</span><span class="sxs-lookup"><span data-stu-id="b54c1-116">All primitive type properties</span></span>|  
|`FixedLength`|<span data-ttu-id="b54c1-117">Określa, czy długość wartości właściwości mogą się różnić.</span><span class="sxs-lookup"><span data-stu-id="b54c1-117">Specifies whether the length of the property value can vary.</span></span>|<span data-ttu-id="b54c1-118">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="b54c1-118">`Binary`, `String`</span></span>|  
|`MaxLength`|<span data-ttu-id="b54c1-119">Określa maksymalną długość wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="b54c1-119">Specifies the maximum length of the property value.</span></span>|<span data-ttu-id="b54c1-120">`Binary`, `String`</span><span class="sxs-lookup"><span data-stu-id="b54c1-120">`Binary`, `String`</span></span>|  
|`Nullable`|<span data-ttu-id="b54c1-121">Określa, czy właściwość może mieć wartości null.</span><span class="sxs-lookup"><span data-stu-id="b54c1-121">Specifies whether the property can have a null value.</span></span>|<span data-ttu-id="b54c1-122">Wszystkie właściwości typu pierwotnego</span><span class="sxs-lookup"><span data-stu-id="b54c1-122">All primitive type properties</span></span>|  
|`Precision`|<span data-ttu-id="b54c1-123">Dla właściwości typu `Decimal`, określa liczbę cyfr, może mieć wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="b54c1-123">For properties of type `Decimal`, specifies the number of digits a property value can have.</span></span> <span data-ttu-id="b54c1-124">Dla właściwości typu `Time`, `DateTime`, i `DateTimeOffset`, określa liczbę cyfr ułamkowych części sekundy wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="b54c1-124">For properties of type `Time`, `DateTime`, and `DateTimeOffset`, specifies the number of digits for the fractional part of seconds of the property value.</span></span>|<span data-ttu-id="b54c1-125">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span><span class="sxs-lookup"><span data-stu-id="b54c1-125">`DateTime`, `DateTimeOffset`, `Decimal`, `Time`,</span></span>|  
|`Scale`|<span data-ttu-id="b54c1-126">Określa liczbę cyfr z prawej strony punktu dziesiętnego dla wartości właściwości.</span><span class="sxs-lookup"><span data-stu-id="b54c1-126">Specifies the number of digits to the right of the decimal point for the property value.</span></span>|<span data-ttu-id="b54c1-127">Wartość dziesiętna</span><span class="sxs-lookup"><span data-stu-id="b54c1-127">Decimal</span></span>|  
|`Unicode`|<span data-ttu-id="b54c1-128">Wskazuje, czy wartość właściwości jest przechowywane w formacie Unicode.</span><span class="sxs-lookup"><span data-stu-id="b54c1-128">Indicates whether the property value is stored as Unicode.</span></span>|`String`|  
  
## <a name="example"></a><span data-ttu-id="b54c1-129">Przykład</span><span class="sxs-lookup"><span data-stu-id="b54c1-129">Example</span></span>  
 <span data-ttu-id="b54c1-130">[ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) używa języka specyficznego dla domeny (DSL) w nazwie schematu koncepcyjnego definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) do definiowania modeli koncepcyjnych.</span><span class="sxs-lookup"><span data-stu-id="b54c1-130">The [ADO.NET Entity Framework](../../../../docs/framework/data/adonet/ef/index.md) uses a domain-specific language (DSL) called conceptual schema definition language ([CSDL](../../../../docs/framework/data/adonet/ef/language-reference/csdl-specification.md)) to define conceptual models.</span></span> <span data-ttu-id="b54c1-131">Definiuje następujące CSDL `Book` typu jednostki.</span><span class="sxs-lookup"><span data-stu-id="b54c1-131">The following CSDL defines a `Book` entity type.</span></span> <span data-ttu-id="b54c1-132">Należy pamiętać, że aspekty są zaimplementowane jako atrybuty XML.</span><span class="sxs-lookup"><span data-stu-id="b54c1-132">Note that facets are implemented as XML attributes.</span></span> <span data-ttu-id="b54c1-133">Wartości aspektu wskazują, że właściwości nie można ustawić wartość null, a `Scale` i `Precision` z `Revision` właściwości każdego ustawiono 29.</span><span class="sxs-lookup"><span data-stu-id="b54c1-133">The facet values indicate that no property can be set to null, and that the `Scale` and `Precision` of the `Revision` property are each set to 29.</span></span>  
  
 [!code-xml[EDM_Example_Model#EntityExample](../../../../samples/snippets/xml/VS_Snippets_Data/edm_example_model/xml/books.edmx#entityexample)]  
  
## <a name="see-also"></a><span data-ttu-id="b54c1-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="b54c1-134">See Also</span></span>  
 [<span data-ttu-id="b54c1-135">Kluczowe założenia modelu danych jednostki</span><span class="sxs-lookup"><span data-stu-id="b54c1-135">Entity Data Model Key Concepts</span></span>](../../../../docs/framework/data/adonet/entity-data-model-key-concepts.md)  
 [<span data-ttu-id="b54c1-136">Model danych jednostki</span><span class="sxs-lookup"><span data-stu-id="b54c1-136">Entity Data Model</span></span>](../../../../docs/framework/data/adonet/entity-data-model.md)
