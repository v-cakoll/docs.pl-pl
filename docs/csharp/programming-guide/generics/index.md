---
title: "Typy ogólne (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- C# language, generics
- generics [C#]
ms.assetid: 75ea8509-a4ea-4e7a-a2b3-cf72482e9282
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 0804ca0fcefcc53e06352accf9a2db19edb31037
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="generics-c-programming-guide"></a><span data-ttu-id="c2f66-102">Typy ogólne (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="c2f66-102">Generics (C# Programming Guide)</span></span>
<span data-ttu-id="c2f66-103">Typy ogólne zostały dodane do wersji 2.0 języka C# i środowisko uruchomieniowe języka wspólnego (CLR).</span><span class="sxs-lookup"><span data-stu-id="c2f66-103">Generics were added to version 2.0 of the C# language and the common language runtime (CLR).</span></span> <span data-ttu-id="c2f66-104">Ogólne wprowadzenie do programu .NET Framework pojęcia parametrów typu, które umożliwiają do projektu klasy i metody, które mają być odroczone specyfikację jeden lub więcej typów, aż klasa lub metoda jest zadeklarowany i utworzone przez kod klienta.</span><span class="sxs-lookup"><span data-stu-id="c2f66-104">Generics introduce to the .NET Framework the concept of type parameters, which make it possible to design classes and methods that defer the specification of one or more types until the class or method is declared and instantiated by client code.</span></span> <span data-ttu-id="c2f66-105">Na przykład za pomocą parametru typu ogólnego T można napisać jedną klasę, używaną przez inny kod klienta bez ponoszenia kosztów lub ryzyka środowiska uruchomieniowego rzutowania lub konwersji boxing operacji, jak pokazano poniżej:</span><span class="sxs-lookup"><span data-stu-id="c2f66-105">For example, by using a generic type parameter T you can write a single class that other client code can use without incurring the cost or risk of runtime casts or boxing operations, as shown here:</span></span>  
  
 [!code-csharp[csProgGuideGenerics#1](../../../csharp/programming-guide/generics/codesnippet/CSharp/index_1.cs)]  
  
## <a name="generics-overview"></a><span data-ttu-id="c2f66-106">Ogólne omówienie</span><span class="sxs-lookup"><span data-stu-id="c2f66-106">Generics Overview</span></span>  
  
-   <span data-ttu-id="c2f66-107">Typy ogólne można używać w celu zwiększenia ponowne użycie kodu, zabezpieczeń i wydajności.</span><span class="sxs-lookup"><span data-stu-id="c2f66-107">Use generic types to maximize code reuse, type safety, and performance.</span></span>  
  
-   <span data-ttu-id="c2f66-108">Najbardziej typowe typów ogólnych polega na utworzeniu klasy kolekcji.</span><span class="sxs-lookup"><span data-stu-id="c2f66-108">The most common use of generics is to create collection classes.</span></span>  
  
-   <span data-ttu-id="c2f66-109">Biblioteka klas programu .NET Framework zawiera kilka nowych klas kolekcji ogólnych w <xref:System.Collections.Generic> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c2f66-109">The .NET Framework class library contains several new generic collection classes in the <xref:System.Collections.Generic> namespace.</span></span> <span data-ttu-id="c2f66-110">Powinny być one używane zawsze, gdy to możliwe, zamiast klas takich jak <xref:System.Collections.ArrayList> w <xref:System.Collections> przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c2f66-110">These should be used whenever possible instead of classes such as <xref:System.Collections.ArrayList> in the <xref:System.Collections> namespace.</span></span>  
  
-   <span data-ttu-id="c2f66-111">Możesz utworzyć własne ogólnych interfejsów, klas, metod, zdarzeń i delegatów.</span><span class="sxs-lookup"><span data-stu-id="c2f66-111">You can create your own generic interfaces, classes, methods, events and delegates.</span></span>  
  
-   <span data-ttu-id="c2f66-112">Klasy ogólne może ograniczonego umożliwiające dostęp do metody na typach danych.</span><span class="sxs-lookup"><span data-stu-id="c2f66-112">Generic classes may be constrained to enable access to methods on particular data types.</span></span>  
  
-   <span data-ttu-id="c2f66-113">W czasie wykonywania można uzyskać informacji o typach, które są używane w typie ogólnym danych przy użyciu odbicia.</span><span class="sxs-lookup"><span data-stu-id="c2f66-113">Information on the types that are used in a generic data type may be obtained at run-time by using reflection.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="c2f66-114">Sekcje pokrewne</span><span class="sxs-lookup"><span data-stu-id="c2f66-114">Related Sections</span></span>  
 <span data-ttu-id="c2f66-115">Informacje dodatkowe:</span><span class="sxs-lookup"><span data-stu-id="c2f66-115">For more information:</span></span>  
  
-   [<span data-ttu-id="c2f66-116">Wprowadzenie do typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="c2f66-116">Introduction to Generics</span></span>](../../../csharp/programming-guide/generics/introduction-to-generics.md)  
  
-   [<span data-ttu-id="c2f66-117">Zalety typów ogólnych</span><span class="sxs-lookup"><span data-stu-id="c2f66-117">Benefits of Generics</span></span>](../../../csharp/programming-guide/generics/benefits-of-generics.md)  
  
-   [<span data-ttu-id="c2f66-118">Parametry typu ogólnego</span><span class="sxs-lookup"><span data-stu-id="c2f66-118">Generic Type Parameters</span></span>](../../../csharp/programming-guide/generics/generic-type-parameters.md)  
  
-   [<span data-ttu-id="c2f66-119">Ograniczenia dotyczące parametrów typu</span><span class="sxs-lookup"><span data-stu-id="c2f66-119">Constraints on Type Parameters</span></span>](../../../csharp/programming-guide/generics/constraints-on-type-parameters.md)  
  
-   [<span data-ttu-id="c2f66-120">Klasy ogólne</span><span class="sxs-lookup"><span data-stu-id="c2f66-120">Generic Classes</span></span>](../../../csharp/programming-guide/generics/generic-classes.md)  
  
-   [<span data-ttu-id="c2f66-121">Interfejsy ogólne</span><span class="sxs-lookup"><span data-stu-id="c2f66-121">Generic Interfaces</span></span>](../../../csharp/programming-guide/generics/generic-interfaces.md)  
  
-   [<span data-ttu-id="c2f66-122">Metody ogólne</span><span class="sxs-lookup"><span data-stu-id="c2f66-122">Generic Methods</span></span>](../../../csharp/programming-guide/generics/generic-methods.md)  
  
-   [<span data-ttu-id="c2f66-123">Delegaty ogólne</span><span class="sxs-lookup"><span data-stu-id="c2f66-123">Generic Delegates</span></span>](../../../csharp/programming-guide/generics/generic-delegates.md)  
  
-   [<span data-ttu-id="c2f66-124">Różnice między szablonami C++ i typami ogólnymi C#</span><span class="sxs-lookup"><span data-stu-id="c2f66-124">Differences Between C++ Templates and C# Generics</span></span>](../../../csharp/programming-guide/generics/differences-between-cpp-templates-and-csharp-generics.md)  
  
-   [<span data-ttu-id="c2f66-125">Typy ogólne i odbicie</span><span class="sxs-lookup"><span data-stu-id="c2f66-125">Generics and Reflection</span></span>](../../../csharp/programming-guide/generics/generics-and-reflection.md)  
  
-   [<span data-ttu-id="c2f66-126">Typy ogólne w czasie wykonywania</span><span class="sxs-lookup"><span data-stu-id="c2f66-126">Generics in the Run Time</span></span>](../../../csharp/programming-guide/generics/generics-in-the-run-time.md)  
  
-   [<span data-ttu-id="c2f66-127">Typy ogólne w bibliotece klas programu .NET Framework</span><span class="sxs-lookup"><span data-stu-id="c2f66-127">Generics in the .NET Framework Class Library</span></span>](../../../csharp/programming-guide/generics/generics-in-the-net-framework-class-library.md)  
  
## <a name="c-language-specification"></a><span data-ttu-id="c2f66-128">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c2f66-128">C# Language Specification</span></span>  
 <span data-ttu-id="c2f66-129">Aby uzyskać więcej informacji, zobacz [Specyfikacja języka C#](../../../csharp/language-reference/language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="c2f66-129">For more information, see the [C# Language Specification](../../../csharp/language-reference/language-specification/index.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2f66-130">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c2f66-130">See Also</span></span>  
 <xref:System.Collections.Generic>  
 [<span data-ttu-id="c2f66-131">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c2f66-131">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="c2f66-132">Typy</span><span class="sxs-lookup"><span data-stu-id="c2f66-132">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
 [<span data-ttu-id="c2f66-133">\<typeparam ></span><span class="sxs-lookup"><span data-stu-id="c2f66-133">\<typeparam></span></span>](../../../csharp/programming-guide/xmldoc/typeparam.md)  
 [<span data-ttu-id="c2f66-134">\<typeparamref ></span><span class="sxs-lookup"><span data-stu-id="c2f66-134">\<typeparamref></span></span>](../../../csharp/programming-guide/xmldoc/typeparamref.md)
