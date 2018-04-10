---
title: this (odwołanie w C#)
description: to słowo kluczowe (odwołanie w C#)
keywords: Ta (C#), to słowo kluczowe (C#), to słowo kluczowe (odwołanie w C#), to słowo kluczowe (język odwołanie w C#)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: f159967707061481a34e72a97ec8cc8316d982ca
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="this-c-reference"></a><span data-ttu-id="086d7-104">this (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="086d7-104">this (C# Reference)</span></span>
<span data-ttu-id="086d7-105">`this` — Słowo kluczowe odwołuje się do bieżącego wystąpienia klasy, a także jest używane jako modyfikator pierwszy parametr metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="086d7-105">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="086d7-106">W tym artykule omówiono używanie `this` z wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="086d7-106">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="086d7-107">Aby uzyskać więcej informacji dotyczących używania jej w metody rozszerzenia, zobacz [metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="086d7-107">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="086d7-108">Poniżej przedstawiono typowe zastosowania `this`:</span><span class="sxs-lookup"><span data-stu-id="086d7-108">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="086d7-109">Aby zakwalifikować członków ukryty przez podobne nazwy, na przykład:</span><span class="sxs-lookup"><span data-stu-id="086d7-109">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="086d7-110">Aby przekazać obiektu jako parametr do innych metod, na przykład:</span><span class="sxs-lookup"><span data-stu-id="086d7-110">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="086d7-111">Aby zadeklarować indeksatorów, na przykład:</span><span class="sxs-lookup"><span data-stu-id="086d7-111">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="086d7-112">Statyczne funkcje Członkowskie, ponieważ istnieją one na poziomie klasy, a nie jako część obiektu nie jest dostępna `this` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="086d7-112">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="086d7-113">Błąd w odwołaniu do `this` w metodzie statycznej.</span><span class="sxs-lookup"><span data-stu-id="086d7-113">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="086d7-114">Przykład</span><span class="sxs-lookup"><span data-stu-id="086d7-114">Example</span></span>  
 <span data-ttu-id="086d7-115">W tym przykładzie `this` są używane do kwalifikowania `Employee` klasy elementów członkowskich, `name` i `alias`, które zostały ukryte za podobne nazwy.</span><span class="sxs-lookup"><span data-stu-id="086d7-115">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="086d7-116">On również używany do przekazywania obiektu do metody `CalcTax`, która należy do innej klasy.</span><span class="sxs-lookup"><span data-stu-id="086d7-116">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="086d7-117">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="086d7-117">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="086d7-118">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="086d7-118">See Also</span></span>  
 [<span data-ttu-id="086d7-119">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="086d7-119">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="086d7-120">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="086d7-120">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="086d7-121">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="086d7-121">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="086d7-122">Podstawa</span><span class="sxs-lookup"><span data-stu-id="086d7-122">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="086d7-123">Metody</span><span class="sxs-lookup"><span data-stu-id="086d7-123">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
