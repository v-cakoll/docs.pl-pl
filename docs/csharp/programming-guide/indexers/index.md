---
title: Indeksatory (Przewodnik programowania w języku C#)
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: acc82ca370a71a0469fc543d042da9c279d69fb2
ms.sourcegitcommit: a1e35d4e94edab384a63406c0a5438306873031b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2018
ms.locfileid: "42753968"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="6e142-102">Indeksatory (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="6e142-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="6e142-103">Indeksatory umożliwiają wystąpienia klasy lub struktury, które mają być indeksowane, podobnie jak tablice.</span><span class="sxs-lookup"><span data-stu-id="6e142-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="6e142-104">Indeksowanej wartości można ustawić lub pobrać bez jawne określenie typu lub wystąpienia elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="6e142-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="6e142-105">Indeksatory przypominają [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md) z tą różnicą, że ich metod dostępu przyjmują parametry.</span><span class="sxs-lookup"><span data-stu-id="6e142-105">Indexers resemble [properties](../../../csharp/programming-guide/classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="6e142-106">W poniższym przykładzie zdefiniowano klasę ogólną za pomocą prostego [uzyskać](../../../csharp/language-reference/keywords/get.md) i [ustaw](../../../csharp/language-reference/keywords/set.md) metody dostępu do przypisywania i pobierać wartości.</span><span class="sxs-lookup"><span data-stu-id="6e142-106">The following example defines a generic class with simple [get](../../../csharp/language-reference/keywords/get.md) and [set](../../../csharp/language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="6e142-107">`Program` Klasy tworzy wystąpienie tej klasy do przechowywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="6e142-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
>  <span data-ttu-id="6e142-108">Aby uzyskać więcej przykładów, zobacz [sekcje pokrewne](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="6e142-108">For more examples, see [Related Sections](../../../csharp/programming-guide/indexers/index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="6e142-109">Definicje treści wyrażenia</span><span class="sxs-lookup"><span data-stu-id="6e142-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="6e142-110">Bardzo często indeksator get lub metody dostępu set składają się z pojedynczej instrukcji, która zwraca lub ustawia wartość.</span><span class="sxs-lookup"><span data-stu-id="6e142-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="6e142-111">Elementy członkowskie z wyrażeniem zapewniają uproszczoną składnię do obsługi tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="6e142-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="6e142-112">Począwszy od C# 6, indeksator tylko do odczytu można zaimplementować jako wyrażeniem w treści elementu członkowskiego, co ilustruje poniższy przykład.</span><span class="sxs-lookup"><span data-stu-id="6e142-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="6e142-113">Należy pamiętać, że `=>` wprowadza treści wyrażenia, a `get` — słowo kluczowe nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="6e142-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="6e142-114">Począwszy od C# 7.0, zarówno get, jak i metody dostępu set mogą być implementowane jako elementy członkowskie z wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="6e142-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="6e142-115">W takim przypadku zarówno `get` i `set` należy używać słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="6e142-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="6e142-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="6e142-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="6e142-117">Omówienie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="6e142-117">Indexers Overview</span></span>  
  
-   <span data-ttu-id="6e142-118">Indeksatory Włącz obiekty, które mają być indeksowane w sposób podobny do tablic.</span><span class="sxs-lookup"><span data-stu-id="6e142-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
-   <span data-ttu-id="6e142-119">A `get` akcesor zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="6e142-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="6e142-120">A `set` akcesor przypisuje wartość.</span><span class="sxs-lookup"><span data-stu-id="6e142-120">A `set` accessor assigns a value.</span></span>  
  
-   <span data-ttu-id="6e142-121">[To](../../../csharp/language-reference/keywords/this.md) — słowo kluczowe jest używane do definiowania indeksatora.</span><span class="sxs-lookup"><span data-stu-id="6e142-121">The [this](../../../csharp/language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
-   <span data-ttu-id="6e142-122">[Wartość](../../../csharp/language-reference/keywords/value.md) — słowo kluczowe jest używane do definiowania wartości przypisywane przez `set` indeksatora.</span><span class="sxs-lookup"><span data-stu-id="6e142-122">The [value](../../../csharp/language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
-   <span data-ttu-id="6e142-123">Indeksatory nie muszą być indeksowane przez wartość całkowitą; jest do Ciebie sposób definiowania mechanizm określonych wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="6e142-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
-   <span data-ttu-id="6e142-124">Indeksatory mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="6e142-124">Indexers can be overloaded.</span></span>  
  
-   <span data-ttu-id="6e142-125">Indeksatory może mieć więcej niż jeden parametr formalny, na przykład podczas uzyskiwania dostępu do tablicy dwuwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="6e142-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
##  <a name="BKMK_RelatedSections"></a> <span data-ttu-id="6e142-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="6e142-126">Related Sections</span></span>  
  
-   [<span data-ttu-id="6e142-127">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="6e142-127">Using Indexers</span></span>](../../../csharp/programming-guide/indexers/using-indexers.md)  
  
-   [<span data-ttu-id="6e142-128">Indeksatory w interfejsach</span><span class="sxs-lookup"><span data-stu-id="6e142-128">Indexers in Interfaces</span></span>](../../../csharp/programming-guide/indexers/indexers-in-interfaces.md)  
  
-   [<span data-ttu-id="6e142-129">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="6e142-129">Comparison Between Properties and Indexers</span></span>](../../../csharp/programming-guide/indexers/comparison-between-properties-and-indexers.md)  
  
-   [<span data-ttu-id="6e142-130">Ograniczanie dostępności metody dostępu</span><span class="sxs-lookup"><span data-stu-id="6e142-130">Restricting Accessor Accessibility</span></span>](../../../csharp/programming-guide/classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="6e142-131">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6e142-131">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="6e142-132">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6e142-132">See Also</span></span>  
 [<span data-ttu-id="6e142-133">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6e142-133">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="6e142-134">Właściwości</span><span class="sxs-lookup"><span data-stu-id="6e142-134">Properties</span></span>](../../../csharp/programming-guide/classes-and-structs/properties.md)
