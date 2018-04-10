---
title: Indeksatory (Przewodnik programowania w języku C#)
ms.date: 03/10/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
caps.latest.revision: 29
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: db49a602b83940cab3f87dea17accb92a2be825d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="d4d20-102">Indeksatory (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="d4d20-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="d4d20-103">Indeksatory Zezwalaj wystąpienia klasy lub struktury zostać pomyślnie zindeksowane, podobnie jak tablic.</span><span class="sxs-lookup"><span data-stu-id="d4d20-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="d4d20-104">Indeksowane wartość można ustawić ani pobrać bez jawnego określenia członka typu lub wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="d4d20-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="d4d20-105">Indeksatory przypominać [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md) z tą różnicą, że ich metod dostępu przyjmować parametrów.</span><span class="sxs-lookup"><span data-stu-id="d4d20-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="d4d20-106">W poniższym przykładzie zdefiniowano klasy ogólnej przy prostego [uzyskać](../../../csharp/language-reference/keywords/get.md) i [ustawić](../../../csharp/language-reference/keywords/set.md) metod dostępu, aby przypisać lub pobrać wartości.</span><span class="sxs-lookup"><span data-stu-id="d4d20-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="d4d20-107">`Program` Klasy tworzy wystąpienie tej klasy do przechowywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="d4d20-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="d4d20-108">Aby uzyskać więcej przykładów, zobacz [sekcje pokrewne](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="d4d20-108">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="d4d20-109">Definicje treść wyrażenia</span><span class="sxs-lookup"><span data-stu-id="d4d20-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="d4d20-110">Bardzo często indeksator get lub składać się z jednej instrukcji, która zwraca lub ustawia wartość metody dostępu set.</span><span class="sxs-lookup"><span data-stu-id="d4d20-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="d4d20-111">Członkowie zabudowanych wyrażenie zapewniają uproszczoną składnię tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="d4d20-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="d4d20-112">Począwszy od języka C# 6, indeksatora tylko do odczytu można zaimplementować jako zabudowanych wyrażenie elementu członkowskiego, jak przedstawiono na poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="d4d20-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="d4d20-113">Należy pamiętać, że `=>` wprowadza treść wyrażenia, a `get` — słowo kluczowe nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="d4d20-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="d4d20-114">Począwszy od C# 7, zarówno get, jak i metody dostępu set może być wdrożony jako członków zabudowanych wyrażenia.</span><span class="sxs-lookup"><span data-stu-id="d4d20-114">Starting with C# 7, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="d4d20-115">W takim przypadku zarówno `get` i `set` słowa kluczowe muszą być używane.</span><span class="sxs-lookup"><span data-stu-id="d4d20-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="d4d20-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="d4d20-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="d4d20-117">Omówienie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="d4d20-117">Indexers Overview</span></span>  
  
-   <span data-ttu-id="d4d20-118">Indeksatory Włącz obiektów do zindeksowania w sposób podobny do tablic.</span><span class="sxs-lookup"><span data-stu-id="d4d20-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
-   <span data-ttu-id="d4d20-119">A `get` akcesor zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="d4d20-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="d4d20-120">A `set` akcesor przypisuje wartość.</span><span class="sxs-lookup"><span data-stu-id="d4d20-120">A `set` accessor assigns a value.</span></span>  
  
-   <span data-ttu-id="d4d20-121">[To](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe jest używane do definiowania indeksatora.</span><span class="sxs-lookup"><span data-stu-id="d4d20-121">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
-   <span data-ttu-id="d4d20-122">[Wartość](../../../csharp/language-reference/keywords/value.md) — słowo kluczowe jest używane do definiowania przypisywane przez wartość `set` indeksatora.</span><span class="sxs-lookup"><span data-stu-id="d4d20-122">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
-   <span data-ttu-id="d4d20-123">Indeksatory nie muszą być indeksowane według całkowitą; jest możesz sposób definiowania mechanizm określonego wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="d4d20-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
-   <span data-ttu-id="d4d20-124">Indeksatory mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="d4d20-124">Indexers can be overloaded.</span></span>  
  
-   <span data-ttu-id="d4d20-125">Indeksatory może mieć więcej niż jeden parametr formalny, na przykład podczas uzyskiwania dostępu do tablicą dwuwymiarową.</span><span class="sxs-lookup"><span data-stu-id="d4d20-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
##  <a name="BKMK_RelatedSections"></a><span data-ttu-id="d4d20-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="d4d20-126">Related Sections</span></span>  
  
-   [<span data-ttu-id="d4d20-127">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="d4d20-127">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="d4d20-128">Indeksatory w interfejsach</span><span class="sxs-lookup"><span data-stu-id="d4d20-128">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="d4d20-129">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="d4d20-129">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="d4d20-130">Ograniczanie dostępności metody dostępu</span><span class="sxs-lookup"><span data-stu-id="d4d20-130">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="d4d20-131">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="d4d20-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="d4d20-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d4d20-132">See Also</span></span>  
 [<span data-ttu-id="d4d20-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d4d20-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d4d20-134">Właściwości</span><span class="sxs-lookup"><span data-stu-id="d4d20-134">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
