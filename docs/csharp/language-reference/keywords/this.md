---
title: this (odwołanie w C#)
description: this — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: df1bf6a3e6d24b231bf5e3c7a960f49084c4e53a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44076005"
---
# <a name="this-c-reference"></a><span data-ttu-id="a0936-103">this (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a0936-103">this (C# Reference)</span></span>
<span data-ttu-id="a0936-104">`this` — Słowo kluczowe odwołuje się do bieżącego wystąpienia klasy, a także jest używane jako modyfikator pierwszy parametr metody rozszerzenia.</span><span class="sxs-lookup"><span data-stu-id="a0936-104">The `this` keyword refers to the current instance of the class and is also used as a modifier of the first parameter of an extension method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="a0936-105">W tym artykule omówiono używanie `this` przy użyciu wystąpienia klasy.</span><span class="sxs-lookup"><span data-stu-id="a0936-105">This article discusses the use of `this` with class instances.</span></span> <span data-ttu-id="a0936-106">Aby uzyskać więcej informacji na temat jej użycia w metody rozszerzenia zobacz [metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span><span class="sxs-lookup"><span data-stu-id="a0936-106">For more information about its use in extension methods, see [Extension Methods](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).</span></span>  
  
 <span data-ttu-id="a0936-107">Poniżej znajdują się najczęstsze zastosowania usługi `this`:</span><span class="sxs-lookup"><span data-stu-id="a0936-107">The following are common uses of `this`:</span></span>  
  
-   <span data-ttu-id="a0936-108">Aby zakwalifikować się elementy członkowskie ukrywane podobnych nazwach, na przykład:</span><span class="sxs-lookup"><span data-stu-id="a0936-108">To qualify members hidden by similar names, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#4](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_1.cs)]  
  
-   <span data-ttu-id="a0936-109">Aby przekazać obiekt jako parametr do innych metod, na przykład:</span><span class="sxs-lookup"><span data-stu-id="a0936-109">To pass an object as a parameter to other methods, for example:</span></span>  
  
    ```csharp  
    CalcTax(this);  
    ```  
  
-   <span data-ttu-id="a0936-110">Aby zadeklarować indeksatorów, na przykład:</span><span class="sxs-lookup"><span data-stu-id="a0936-110">To declare indexers, for example:</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#5](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_2.cs)]  
  
 <span data-ttu-id="a0936-111">Statyczne funkcje Członkowskie, ponieważ istnieją na poziomie klasy, a nie jako część obiektu, nie masz `this` wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="a0936-111">Static member functions, because they exist at the class level and not as part of an object, do not have a `this` pointer.</span></span> <span data-ttu-id="a0936-112">Jest to błąd do odwoływania się do `this` w metodzie statycznej.</span><span class="sxs-lookup"><span data-stu-id="a0936-112">It is an error to refer to `this` in a static method.</span></span>  
  
## <a name="example"></a><span data-ttu-id="a0936-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0936-113">Example</span></span>  
 <span data-ttu-id="a0936-114">W tym przykładzie `this` są używane do kwalifikowania `Employee` składowych, klasy `name` i `alias`, które są ukrywane o podobnych nazwach.</span><span class="sxs-lookup"><span data-stu-id="a0936-114">In this example, `this` is used to qualify the `Employee` class members, `name` and `alias`, which are hidden by similar names.</span></span> <span data-ttu-id="a0936-115">Służy również przekazać obiekt do metody `CalcTax`, która należy do innej klasy.</span><span class="sxs-lookup"><span data-stu-id="a0936-115">It is also used to pass an object to the method `CalcTax`, which belongs to another class.</span></span>  
  
 [!code-csharp[csrefKeywordsAccess#3](../../../csharp/language-reference/keywords/codesnippet/CSharp/this_3.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="a0936-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a0936-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="a0936-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0936-117">See Also</span></span>

- [<span data-ttu-id="a0936-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a0936-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="a0936-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="a0936-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="a0936-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a0936-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="a0936-121">base</span><span class="sxs-lookup"><span data-stu-id="a0936-121">base</span></span>](../../../csharp/language-reference/keywords/base.md)  
- [<span data-ttu-id="a0936-122">Metody</span><span class="sxs-lookup"><span data-stu-id="a0936-122">Methods</span></span>](../../../csharp/programming-guide/classes-and-structs/methods.md)
