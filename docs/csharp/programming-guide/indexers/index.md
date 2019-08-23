---
title: Indeksatory — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 03/10/2017
f1_keywords:
- cs.indexers
helpviewer_keywords:
- indexers [C#]
- C# language, indexers
ms.assetid: 022cd27d-d5e0-4cfe-8b97-dc018cc3355d
ms.openlocfilehash: 5b135fee12ac5b78b41a657f2eb458ea104143fc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923933"
---
# <a name="indexers-c-programming-guide"></a><span data-ttu-id="f68fc-102">Indeksatory (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="f68fc-102">Indexers (C# Programming Guide)</span></span>

<span data-ttu-id="f68fc-103">Indeksatory umożliwiają indeksowanie wystąpień klasy lub struktury tak samo jak w przypadku tablic.</span><span class="sxs-lookup"><span data-stu-id="f68fc-103">Indexers allow instances of a class or struct to be indexed just like arrays.</span></span> <span data-ttu-id="f68fc-104">Indeksowaną wartość można ustawić lub pobrać bez jawnego określenia typu lub elementu członkowskiego wystąpienia.</span><span class="sxs-lookup"><span data-stu-id="f68fc-104">The indexed value can be set or retrieved without explicitly specifying a type or instance member.</span></span> <span data-ttu-id="f68fc-105">Indeksatory przypominają [Właściwości](../classes-and-structs/properties.md) , z tą różnicą, że ich metody dostępu pobierają parametry.</span><span class="sxs-lookup"><span data-stu-id="f68fc-105">Indexers resemble [properties](../classes-and-structs/properties.md) except that their accessors take parameters.</span></span>  
 
 <span data-ttu-id="f68fc-106">W poniższym przykładzie zdefiniowano klasę generyczną z prostymi metodami dostępu [Get](../../language-reference/keywords/get.md) i [Set](../../language-reference/keywords/set.md) do przypisywania i pobierania wartości.</span><span class="sxs-lookup"><span data-stu-id="f68fc-106">The following example defines a generic class with simple [get](../../language-reference/keywords/get.md) and [set](../../language-reference/keywords/set.md) accessor methods to assign and retrieve values.</span></span> <span data-ttu-id="f68fc-107">`Program` Klasa tworzy wystąpienie tej klasy do przechowywania ciągów.</span><span class="sxs-lookup"><span data-stu-id="f68fc-107">The `Program` class creates an instance of this class for storing strings.</span></span>  
  
 [!code-csharp[indexers#1](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-1.cs)]  
  
> [!NOTE]
> <span data-ttu-id="f68fc-108">Aby uzyskać więcej przykładów, zobacz sekcję [pokrewne](./index.md#BKMK_RelatedSections).</span><span class="sxs-lookup"><span data-stu-id="f68fc-108">For more examples, see [Related Sections](./index.md#BKMK_RelatedSections).</span></span>  
  
## <a name="expression-body-definitions"></a><span data-ttu-id="f68fc-109">Definicje treści wyrażenia</span><span class="sxs-lookup"><span data-stu-id="f68fc-109">Expression Body Definitions</span></span>  
 
<span data-ttu-id="f68fc-110">Metoda dostępu "Get" lub "Set" może składać się z pojedynczej instrukcji, która zwraca lub ustawia wartość.</span><span class="sxs-lookup"><span data-stu-id="f68fc-110">It is common for an indexer's get or set accessor to consist of a single statement that either returns or sets a value.</span></span> <span data-ttu-id="f68fc-111">Składowe w postaci wyrażeń zawierają uproszczoną składnię do obsługi tego scenariusza.</span><span class="sxs-lookup"><span data-stu-id="f68fc-111">Expression-bodied members provide a simplified syntax to support this scenario.</span></span> <span data-ttu-id="f68fc-112">Począwszy od C# 6, indeksator tylko do odczytu może być implementowany jako składowa z wyrażeniem, jak pokazano w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="f68fc-112">Starting with C# 6, a read-only indexer can be implemented as an expression-bodied member, as the following example shows.</span></span>

[!code-csharp[indexers#2](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-2.cs)]  

<span data-ttu-id="f68fc-113">Należy zauważyć `=>` , że wprowadza treść wyrażenia, a `get` słowo kluczowe nie jest używane.</span><span class="sxs-lookup"><span data-stu-id="f68fc-113">Note that `=>` introduces the expression body, and that the `get` keyword is not used.</span></span> 

<span data-ttu-id="f68fc-114">Począwszy od C# 7,0, obie metody dostępu get i Set mogą być zaimplementowane jako elementy członkowskie z wyrażeniami.</span><span class="sxs-lookup"><span data-stu-id="f68fc-114">Starting with C# 7.0, both the get and set accessor can be an implemented as expression-bodied members.</span></span> <span data-ttu-id="f68fc-115">W takim przypadku `get` należy użyć słów `set` kluczowych i.</span><span class="sxs-lookup"><span data-stu-id="f68fc-115">In this case, both `get` and `set` keywords must be used.</span></span> <span data-ttu-id="f68fc-116">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f68fc-116">For example:</span></span>

[!code-csharp[indexers#3](../../../../samples/snippets/csharp/programming-guide/indexers/indexer-3.cs)]  
  
## <a name="indexers-overview"></a><span data-ttu-id="f68fc-117">Omówienie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="f68fc-117">Indexers Overview</span></span>  
  
- <span data-ttu-id="f68fc-118">Indeksatory umożliwiają indeksowanie obiektów w podobny sposób do tablic.</span><span class="sxs-lookup"><span data-stu-id="f68fc-118">Indexers enable objects to be indexed in a similar manner to arrays.</span></span>  
  
- <span data-ttu-id="f68fc-119">`get` Metoda dostępu zwraca wartość.</span><span class="sxs-lookup"><span data-stu-id="f68fc-119">A `get` accessor returns a value.</span></span> <span data-ttu-id="f68fc-120">`set` Metoda dostępu przypisuje wartość.</span><span class="sxs-lookup"><span data-stu-id="f68fc-120">A `set` accessor assigns a value.</span></span>  
  
- <span data-ttu-id="f68fc-121">[To](../../language-reference/keywords/this.md) słowo kluczowe jest używane do definiowania indeksatora.</span><span class="sxs-lookup"><span data-stu-id="f68fc-121">The [this](../../language-reference/keywords/this.md) keyword is used to define the indexer.</span></span>  
  
- <span data-ttu-id="f68fc-122">Słowo kluczowe [Value](../../language-reference/keywords/value.md) służy do definiowania wartości przypisanej przez `set` indeksator.</span><span class="sxs-lookup"><span data-stu-id="f68fc-122">The [value](../../language-reference/keywords/value.md) keyword is used to define the value being assigned by the `set` indexer.</span></span>  
  
- <span data-ttu-id="f68fc-123">Indeksatory nie muszą być indeksowane przez wartość całkowitą; Istnieje możliwość zdefiniowania określonego mechanizmu wyszukiwania.</span><span class="sxs-lookup"><span data-stu-id="f68fc-123">Indexers do not have to be indexed by an integer value; it is up to you how to define the specific look-up mechanism.</span></span>  
  
- <span data-ttu-id="f68fc-124">Indeksatory mogą być przeciążone.</span><span class="sxs-lookup"><span data-stu-id="f68fc-124">Indexers can be overloaded.</span></span>  
  
- <span data-ttu-id="f68fc-125">Indeksatory mogą mieć więcej niż jeden parametr formalny, na przykład podczas uzyskiwania dostępu do tablicy dwuwymiarowej.</span><span class="sxs-lookup"><span data-stu-id="f68fc-125">Indexers can have more than one formal parameter, for example, when accessing a two-dimensional array.</span></span>  
  
## <a name="BKMK_RelatedSections"></a><span data-ttu-id="f68fc-126">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="f68fc-126">Related Sections</span></span>  
  
- [<span data-ttu-id="f68fc-127">Używanie indeksatorów</span><span class="sxs-lookup"><span data-stu-id="f68fc-127">Using Indexers</span></span>](./using-indexers.md)  
  
- [<span data-ttu-id="f68fc-128">Indeksatory w interfejsach</span><span class="sxs-lookup"><span data-stu-id="f68fc-128">Indexers in Interfaces</span></span>](./indexers-in-interfaces.md)  
  
- [<span data-ttu-id="f68fc-129">Porównanie właściwości i indeksatorów</span><span class="sxs-lookup"><span data-stu-id="f68fc-129">Comparison Between Properties and Indexers</span></span>](./comparison-between-properties-and-indexers.md)  
  
- [<span data-ttu-id="f68fc-130">Ograniczanie dostępności metody dostępu</span><span class="sxs-lookup"><span data-stu-id="f68fc-130">Restricting Accessor Accessibility</span></span>](../classes-and-structs/restricting-accessor-accessibility.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="f68fc-131">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f68fc-131">C# Language Specification</span></span>  

<span data-ttu-id="f68fc-132">Aby uzyskać więcej informacji, [](~/_csharplang/spec/classes.md#indexers) Zobacz indeksatory w [ C# specyfikacji języka](../../language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f68fc-132">For more information, see [Indexers](~/_csharplang/spec/classes.md#indexers) in the [C# Language Specification](../../language-reference/language-specification/index.md).</span></span> <span data-ttu-id="f68fc-133">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="f68fc-133">The language specification is the definitive source for C# syntax and usage.</span></span>
  
## <a name="see-also"></a><span data-ttu-id="f68fc-134">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f68fc-134">See also</span></span>

- [<span data-ttu-id="f68fc-135">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f68fc-135">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f68fc-136">Właściwości</span><span class="sxs-lookup"><span data-stu-id="f68fc-136">Properties</span></span>](../classes-and-structs/properties.md)
