---
title: this (odwołanie w C#)
description: to słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 04496079114be45388926993b67e8f1d3f2e9f15
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
---
# <a name="this-c-reference"></a><span data-ttu-id="a9e18-103">this (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a9e18-103">this (C# Reference)</span></span>
<span data-ttu-id="a9e18-104">`this` — Słowo kluczowe odwołuje się do bieżącego wystąpienia klasy, a także jest używane jako modyfikator pierwszy parametr metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="a9e18-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a9e18-105">W tym artykule omówiono używanie `this` z wystąpień klasy.</span><span class="sxs-lookup"><span data-stu-id="a9e18-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="a9e18-106">Aby uzyskać więcej informacji dotyczących używania jej w metody rozszerzenia, zobacz [metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a9e18-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="a9e18-107">Poniżej przedstawiono typowe zastosowania `this`:</span><span class="sxs-lookup"><span data-stu-id="a9e18-107">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="a9e18-108">Aby zakwalifikować członków ukryty przez podobne nazwy, na przykład:</span><span class="sxs-lookup"><span data-stu-id="a9e18-108">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="a9e18-109">Aby przekazać obiektu jako parametr do innych metod, na przykład:</span><span class="sxs-lookup"><span data-stu-id="a9e18-109">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="a9e18-110">Aby zadeklarować indeksatorów, na przykład:</span><span class="sxs-lookup"><span data-stu-id="a9e18-110">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="a9e18-111">Statyczne funkcje Członkowskie, ponieważ istnieją one na poziomie klasy, a nie jako część obiektu nie jest dostępna `this` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="a9e18-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="a9e18-112">Błąd w odwołaniu do `this` w metodzie statycznej.</span><span class="sxs-lookup"><span data-stu-id="a9e18-112">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a9e18-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a9e18-113">Example</span></span>  
 <span data-ttu-id="a9e18-114">W tym przykładzie `this` są używane do kwalifikowania `Employee` klasy elementów członkowskich, `name` i `alias`, które zostały ukryte za podobne nazwy.</span><span class="sxs-lookup"><span data-stu-id="a9e18-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="a9e18-115">On również używany do przekazywania obiektu do metody `CalcTax`, która należy do innej klasy.</span><span class="sxs-lookup"><span data-stu-id="a9e18-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a9e18-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a9e18-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a9e18-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a9e18-117">See Also</span></span>  
 [<span data-ttu-id="a9e18-118">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="a9e18-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="a9e18-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a9e18-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="a9e18-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a9e18-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="a9e18-121">base</span><span class="sxs-lookup"><span data-stu-id="a9e18-121">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
 [<span data-ttu-id="a9e18-122">Metody</span><span class="sxs-lookup"><span data-stu-id="a9e18-122">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
