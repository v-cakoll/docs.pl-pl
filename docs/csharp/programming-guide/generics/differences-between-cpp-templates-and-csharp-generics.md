---
title: "Różnice między szablonami C++ i typami ogólnymi C# (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
helpviewer_keywords:
- generics [C#], vs. C++ templates
ms.assetid: 1da6beeb-d4a4-4da0-87b7-0cfbe04920b7
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: aea1b51c26a8f3de56ea66b9cf89e75bfeb59d81
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="differences-between-c-templates-and-c-generics-c-programming-guide"></a><span data-ttu-id="bf5a3-102">Różnice między szablonami C++ i typami ogólnymi C# (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="bf5a3-102">Differences Between C++ Templates and C# Generics (C# Programming Guide)</span></span>
<span data-ttu-id="bf5a3-103">Szablony typami ogólnymi C# i C++ są obie funkcje języka, które obsługują typy z parametrami.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-103">C# Generics and C++ templates are both language features that provide support for parameterized types.</span></span> <span data-ttu-id="bf5a3-104">Istnieje jednak wiele różnice między nimi.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-104">However, there are many differences between the two.</span></span> <span data-ttu-id="bf5a3-105">Na poziomie składni typami ogólnymi C# są prostsze typom sparametryzowane bez złożoności szablonów języka C++.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-105">At the syntax level, C# generics are a simpler approach to parameterized types without the complexity of C++ templates.</span></span> <span data-ttu-id="bf5a3-106">Ponadto C# nie podejmowana próba udostępnienia wszystkie funkcje, które zapewniają szablonów języka C++.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-106">In addition, C# does not attempt to provide all of the functionality that C++ templates provide.</span></span> <span data-ttu-id="bf5a3-107">Na poziomie implementacji podstawowa różnica polega na podstawienia typu ogólnego C# są wykonywane w czasie wykonywania, a informacje o typie ogólnym co są zachowywane dla wystąpień obiektów.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-107">At the implementation level, the primary difference is that C# generic type substitutions are performed at runtime and generic type information is thereby preserved for instantiated objects.</span></span> <span data-ttu-id="bf5a3-108">Aby uzyskać więcej informacji, zobacz [typy ogólne w czasie wykonywania](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span><span class="sxs-lookup"><span data-stu-id="bf5a3-108">For more information, see [Generics in the Run Time](../../../csharp/programming-guide/generics/generics-in-the-run-time.md).</span></span>  
  
 <span data-ttu-id="bf5a3-109">Poniżej przedstawiono podstawowe różnice między szablony C++ i typami ogólnymi C#:</span><span class="sxs-lookup"><span data-stu-id="bf5a3-109">The following are the key differences between C# Generics and C++ templates:</span></span>  
  
-   <span data-ttu-id="bf5a3-110">Typami ogólnymi C# nie udostępniają samo elastyczność jako szablonów języka C++.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-110">C# generics do not provide the same amount of flexibility as C++ templates.</span></span> <span data-ttu-id="bf5a3-111">Na przykład go nie jest możliwe do wywołania operatorów arytmetycznych w języku C# klasy ogólnej, chociaż można wywołać operatory zdefiniowane przez użytkownika.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-111">For example, it is not possible to call arithmetic operators in a C# generic class, although it is possible to call user defined operators.</span></span>  
  
-   <span data-ttu-id="bf5a3-112">C# nie zezwala na parametry szablonu bez typu, takich jak `template C<int i> {}`.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-112">C# does not allow non-type template parameters, such as `template C<int i> {}`.</span></span>  
  
-   <span data-ttu-id="bf5a3-113">C# nie obsługuje jawnej specjalizacji; oznacza to, że implementacja niestandardowa szablonu dla określonego typu.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-113">C# does not support explicit specialization; that is, a custom implementation of a template for a specific type.</span></span>  
  
-   <span data-ttu-id="bf5a3-114">C# nie obsługuje częściowa specjalizacja: implementacja niestandardowa dla podzbioru argumentów typu.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-114">C# does not support partial specialization: a custom implementation for a subset of the type arguments.</span></span>  
  
-   <span data-ttu-id="bf5a3-115">C# nie zezwala na parametr typu do użycia jako klasę podstawową dla typu ogólnego.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-115">C# does not allow the type parameter to be used as the base class for the generic type.</span></span>  
  
-   <span data-ttu-id="bf5a3-116">C# nie zezwala na parametry typu mają domyślnych typów.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-116">C# does not allow type parameters to have default types.</span></span>  
  
-   <span data-ttu-id="bf5a3-117">W języku C#, parametru typu ogólnego nie może sam być ogólnego, chociaż typy utworzone mogą być używane jako ogólne.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-117">In C#, a generic type parameter cannot itself be a generic, although constructed types can be used as generics.</span></span> <span data-ttu-id="bf5a3-118">Zezwalaj na C++ parametrów szablonu.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-118">C++ does allow template parameters.</span></span>  
  
-   <span data-ttu-id="bf5a3-119">C++ pozwala kod, który nie jest prawidłowe dla wszystkich parametrów typu w szablonie, który następnie jest sprawdzany pod kątem określonego typu użyć jako parametru typu.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-119">C++ allows code that might not be valid for all type parameters in the template, which is then checked for the specific type used as the type parameter.</span></span> <span data-ttu-id="bf5a3-120">C# wymaga kod w klasie, do zapisania w taki sposób, że będzie ona działać w przypadku każdego typu spełniającego ograniczenia.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-120">C# requires code in a class to be written in such a way that it will work with any type that satisfies the constraints.</span></span> <span data-ttu-id="bf5a3-121">Na przykład w języku C++ istnieje możliwość zapisu funkcję, która używa operatorów arytmetycznych `+` i `-` na obiektach parametr typu, który utworzy wystąpił błąd w czasie tworzenia wystąpienia szablonu z typem, który nie obsługuje te operatory.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-121">For example, in C++ it is possible to write a function that uses the arithmetic operators `+` and `-` on objects of the type parameter, which will produce an error at the time of instantiation of the template with a type that does not support these operators.</span></span> <span data-ttu-id="bf5a3-122">C# nie są dozwolone. konstrukcji języka tylko dozwolone są tymi, które wynikają z ograniczeniami.</span><span class="sxs-lookup"><span data-stu-id="bf5a3-122">C# disallows this; the only language constructs allowed are those that can be deduced from the constraints.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bf5a3-123">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="bf5a3-123">See Also</span></span>  
 [<span data-ttu-id="bf5a3-124">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="bf5a3-124">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="bf5a3-125">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="bf5a3-125">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
 [<span data-ttu-id="bf5a3-126">Szablony</span><span class="sxs-lookup"><span data-stu-id="bf5a3-126">Templates</span></span>](/cpp/cpp/templates-cpp)
