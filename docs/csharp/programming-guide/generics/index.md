---
title: Ogólne — C# przewodnik programowania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
ms.openlocfilehash: 03a5a594db86f5286979dbe22a8841f0e7d4518c
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240870"
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="2f2b6-102">Typy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="2f2b6-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="2f2b6-103">Typy ogólne zostały dodane do wersji języka C# i środowisko uruchomieniowe języka wspólnego (CLR) w wersji 2.0.</span><span class="sxs-lookup"><span data-stu-id="2f2b6-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="2f2b6-104">Ogólne wprowadzenie do programu .NET Framework pojęcia parametrami typu, które umożliwiają projektowanie klas i metod, które Odrocz specyfikację jeden lub więcej typów, dopóki klasy lub metody jest zadeklarowana i tworzone przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="2f2b6-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="2f2b6-105">Na przykład za pomocą parametru typu generycznego T, można napisać jedną klasę, używaną przez inny kod klienta bez ponoszenia kosztów ani ryzyka rzutowania środowiska uruchomieniowego lub operacje na polach, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="2f2b6-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="2f2b6-106">Przegląd typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="2f2b6-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="2f2b6-107">Aby zmaksymalizować ponowne wykorzystanie kodu, bezpieczeństwa i wydajności, należy użyć typów ogólnych.</span><span class="sxs-lookup"><span data-stu-id="2f2b6-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="2f2b6-108">Najczęściej używane typy ogólne są do tworzenia klas kolekcji.</span><span class="sxs-lookup"><span data-stu-id="2f2b6-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="2f2b6-109">Biblioteka klas .NET Framework zawiera kilka nowych klas ogólnych kolekcji w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2f2b6-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="2f2b6-110">Powinny one być stosowane zawsze, gdy to możliwe, zamiast klasy, takie jak <xref:System.Collections.ArrayList> w <xref:System.Collections> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="2f2b6-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="2f2b6-111">Możesz utworzyć własne interfejsy ogólne, klas, metod, zdarzeń i delegatów.</span><span class="sxs-lookup"><span data-stu-id="2f2b6-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="2f2b6-112">Klasy ogólne może być ograniczona umożliwiające dostęp do metod w typach danych.</span><span class="sxs-lookup"><span data-stu-id="2f2b6-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="2f2b6-113">W czasie wykonywania można uzyskać informacje na temat typów, które są używane w typie danych typu ogólnego przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="2f2b6-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="2f2b6-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="2f2b6-114">Related Sections</span></span>  
 <span data-ttu-id="2f2b6-115">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="2f2b6-115">For more information:</span></span>  
  
-   [<span data-ttu-id="2f2b6-116">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="2f2b6-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="2f2b6-117">Zalety typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="2f2b6-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="2f2b6-118">Parametry typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="2f2b6-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="2f2b6-119">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="2f2b6-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="2f2b6-120">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="2f2b6-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="2f2b6-121">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="2f2b6-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="2f2b6-122">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="2f2b6-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="2f2b6-123">Delegaci ogólni</span><span class="sxs-lookup"><span data-stu-id="2f2b6-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="2f2b6-124">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="2f2b6-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="2f2b6-125">Typy ogólne i odbicie</span><span class="sxs-lookup"><span data-stu-id="2f2b6-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="2f2b6-126">Typy ogólne w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="2f2b6-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="2f2b6-127">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="2f2b6-127">C# Language Specification</span></span>  
 <span data-ttu-id="2f2b6-128">Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](~/_csharplang/spec/types.md#constructed-types).</span><span class="sxs-lookup"><span data-stu-id="2f2b6-128">For more information, see the [C# Language Specification](~/_csharplang/spec/types.md#constructed-types).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2f2b6-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="2f2b6-129">See Also</span></span>

- <xref:System.Collections.Generic>  
- [<span data-ttu-id="2f2b6-130">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="2f2b6-130">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="2f2b6-131">Typy</span><span class="sxs-lookup"><span data-stu-id="2f2b6-131">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
- [<span data-ttu-id="2f2b6-132">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="2f2b6-132">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
- [<span data-ttu-id="2f2b6-133">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="2f2b6-133">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)  
- [<span data-ttu-id="2f2b6-134">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="2f2b6-134">Generics in .NET</span></span>](../../../standard/generics/index.md)  