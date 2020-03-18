---
title: Indeksatory - Przewodnik programowania C#
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 539b2861e975c0c758c43c8a5d4cca86e3d2bb2c
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79167546"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="a9ddf-102">Indeksatory (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="a9ddf-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="a9ddf-103">Indeksatory zezwalają na indeksowanie wystąpień klasy lub struktury, podobnie jak tablice.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="a9ddf-104">Wartość indeksowana można ustawić lub pobrać bez jawnego określenia typu lub elementu członkowskiego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="a9ddf-105">Indeksatory przypominają [właściwości,](../classes-and-structs/properties.md) z tą różnicą, że ich akcesory przyjmują parametry.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  

 <span data-ttu-id="a9ddf-106">W poniższym przykładzie definiuje klasę rodzajową z [prosteget](../../language-reference/keywords/get.md) i [set](../../language-reference/keywords/set.md) metody akcesora do przypisywania i pobierania wartości.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="a9ddf-107">Klasa `Program` tworzy wystąpienie tej klasy do przechowywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="a9ddf-108">Aby uzyskać więcej przykładów, zobacz [powiązane sekcje](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="a9ddf-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="a9ddf-109">Definicje treści wyrażeń</span><span class="sxs-lookup"><span data-stu-id="a9ddf-109">Expression Body Definitions</span></span>  

<span data-ttu-id="a9ddf-110">Jest wspólne dla indeksatora get lub set akcesor składa się z pojedynczej instrukcji, która zwraca lub ustawia wartość.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="a9ddf-111">Elementy członkowskie zabudowane wyrażeniem zapewniają uproszczoną składnię do obsługi tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="a9ddf-112">Począwszy od C# 6 indeksator tylko do odczytu można zaimplementować jako element członkowski zabudowany wyrażeniem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="a9ddf-113">Należy `=>` zauważyć, że wprowadza treść `get` wyrażenia i że słowo kluczowe nie jest używany.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span>

<span data-ttu-id="a9ddf-114">Począwszy od języka C# 7.0, get i set akcesor może być implementowane jako elementy członkowskie zabudowane wyrażeniem.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="a9ddf-115">W takim przypadku `get` `set` należy użyć zarówno słów kluczowych, jak i słów kluczowych.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="a9ddf-116">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a9ddf-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="a9ddf-117">Omówienie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="a9ddf-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="a9ddf-118">Indeksatory umożliwiają indeksowanie obiektów w sposób podobny do tablic.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="a9ddf-119">Akcesor `get` zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="a9ddf-120">Akcesor `set` przypisuje wartość.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="a9ddf-121">[To](../../language-reference/keywords/this.md) słowo kluczowe służy do definiowania indeksatora.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="a9ddf-122">Value [value](../../language-reference/keywords/value.md) — słowo kluczowe służy do definiowania wartości przypisanej `set` przez indeksatora.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="a9ddf-123">Indeksatory nie muszą być indeksowane przez wartość całkowitą; to od Ciebie zależy, jak zdefiniować konkretny mechanizm wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="a9ddf-124">Indeksatory mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="a9ddf-125">Indeksatory mogą mieć więcej niż jeden parametr formalny, na przykład podczas uzyskiwania dostępu do tablicy dwuwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a><span data-ttu-id="a9ddf-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="a9ddf-126">Related Sections</span></span>  
  
- [<span data-ttu-id="a9ddf-127">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="a9ddf-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="a9ddf-128">Indeksatory w interfejsach</span><span class="sxs-lookup"><span data-stu-id="a9ddf-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="a9ddf-129">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="a9ddf-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="a9ddf-130">Ograniczanie dostępności metody dostępu</span><span class="sxs-lookup"><span data-stu-id="a9ddf-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="a9ddf-131">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a9ddf-131">C# Language Specification</span></span>  

<span data-ttu-id="a9ddf-132">Aby uzyskać więcej informacji, zobacz [Indeksatory](~/_csharplang/spec/classes.md#indexers) w [specyfikacji języka Języka C #](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="a9ddf-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="a9ddf-133">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="a9ddf-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="a9ddf-134">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9ddf-134">See also</span></span>

- [<span data-ttu-id="a9ddf-135">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="a9ddf-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="a9ddf-136">Właściwości</span><span class="sxs-lookup"><span data-stu-id="a9ddf-136">Properties</span></span>](../classes-and-structs/properties.md)
