---
title: readonly (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- readonly_CSharpKeyword
- readonly
helpviewer_keywords:
- readonly keyword [C#]
ms.assetid: 2f8081f6-0de2-4903-898d-99696c48d2f4
ms.openlocfilehash: d2f8a2f192dc319ad806aeef4bfbaeecc44b07a3
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172636"
---
# <a name="readonly-c-reference"></a><span data-ttu-id="9863f-102">readonly (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="9863f-102">readonly (C# Reference)</span></span>
<span data-ttu-id="9863f-103">`readonly` — Słowo kluczowe jest modyfikator, pomocne w polach.</span><span class="sxs-lookup"><span data-stu-id="9863f-103">The `readonly` keyword is a modifier that you can use on fields.</span></span> <span data-ttu-id="9863f-104">Jeżeli zawiera deklarację pola `readonly` , modyfikator przypisania do pól wprowadzone przez deklaracja może występować tylko w ramach deklaracji lub w Konstruktorze w tej samej klasy.</span><span class="sxs-lookup"><span data-stu-id="9863f-104">When a field declaration includes a `readonly` modifier, assignments to the fields introduced by the declaration can only occur as part of the declaration or in a constructor in the same class.</span></span>  
  
## <a name="readonly-field-example"></a><span data-ttu-id="9863f-105">Przykład pola tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9863f-105">Readonly field example</span></span>  
 <span data-ttu-id="9863f-106">W tym przykładzie wartość pola `year` nie można zmienić w metodzie `ChangeYear`, nawet jeśli jest przypisywana wartość w konstruktorze klasy:</span><span class="sxs-lookup"><span data-stu-id="9863f-106">In this example, the value of the field `year` cannot be changed in the method `ChangeYear`, even though it is assigned a value in the class constructor:</span></span>  
  
 [!code-csharp[csrefKeywordsModifiers#14](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_1.cs)]  
  
 <span data-ttu-id="9863f-107">Można przypisać wartości do `readonly` tylko w następujących sytuacjach:</span><span class="sxs-lookup"><span data-stu-id="9863f-107">You can assign a value to a `readonly` field only in the following contexts:</span></span>  
  
-   <span data-ttu-id="9863f-108">Jeśli zmienna jest ustawiana w deklaracji, na przykład:</span><span class="sxs-lookup"><span data-stu-id="9863f-108">When the variable is initialized in the declaration, for example:</span></span>  
  
    ```csharp  
    public readonly int y = 5;  
    ```  
  
-   <span data-ttu-id="9863f-109">Dla pola wystąpienia w konstruktorach wystąpień klasy zawiera deklarację pola lub statycznego pola statycznego konstruktora klasy zawiera deklarację pola.</span><span class="sxs-lookup"><span data-stu-id="9863f-109">For an instance field, in the instance constructors of the class that contains the field declaration, or for a static field, in the static constructor of the class that contains the field declaration.</span></span> <span data-ttu-id="9863f-110">Te są również tylko kontekstów, w których jest nieprawidłowy do przekazania `readonly` pole jako [limit](../../../csharp/language-reference/keywords/out-parameter-modifier.md) lub [ref](../../../csharp/language-reference/keywords/ref.md) parametru.</span><span class="sxs-lookup"><span data-stu-id="9863f-110">These are also the only contexts in which it is valid to pass a `readonly` field as an [out](../../../csharp/language-reference/keywords/out-parameter-modifier.md) or [ref](../../../csharp/language-reference/keywords/ref.md) parameter.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="9863f-111">`readonly` — Słowo kluczowe różni się od [const](../../../csharp/language-reference/keywords/const.md) — słowo kluczowe.</span><span class="sxs-lookup"><span data-stu-id="9863f-111">The `readonly` keyword is different from the [const](../../../csharp/language-reference/keywords/const.md) keyword.</span></span> <span data-ttu-id="9863f-112">A `const` pól mogą być inicjowane tylko w deklaracji pola.</span><span class="sxs-lookup"><span data-stu-id="9863f-112">A `const` field can only be initialized at the declaration of the field.</span></span> <span data-ttu-id="9863f-113">A `readonly` pól mogą być inicjowane w deklaracji lub w konstruktorze.</span><span class="sxs-lookup"><span data-stu-id="9863f-113">A `readonly` field can be initialized either at the declaration or in a constructor.</span></span> <span data-ttu-id="9863f-114">W związku z tym `readonly` pola mogą mieć różne wartości w zależności od Konstruktor używany.</span><span class="sxs-lookup"><span data-stu-id="9863f-114">Therefore, `readonly` fields can have different values depending on the constructor used.</span></span> <span data-ttu-id="9863f-115">Ponadto podczas `const` pole jest stałą czasu kompilacji `readonly` pole może być używane dla środowiska uruchomieniowego stałe, jak w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="9863f-115">Also, while a `const` field is a compile-time constant, the `readonly` field can be used for runtime constants as in the following example:</span></span>  
  
```csharp  
public static readonly uint timeStamp = (uint)DateTime.Now.Ticks;  
```  
  
## <a name="comparing-readonly-and-non-readonly-instance-fields"></a><span data-ttu-id="9863f-116">Porównanie pola wystąpienia tylko do odczytu i nie tylko do odczytu</span><span class="sxs-lookup"><span data-stu-id="9863f-116">Comparing readonly and non-readonly instance fields</span></span>  
 [!code-csharp[csrefKeywordsModifiers#15](../../../csharp/language-reference/keywords/codesnippet/CSharp/readonly_2.cs)]  
  
 <span data-ttu-id="9863f-117">W poprzednim przykładzie, jeśli używana jest instrukcja następująco:</span><span class="sxs-lookup"><span data-stu-id="9863f-117">In the preceding example, if you use a statement like this:</span></span>  
  
 `p2.y = 66;        // Error`  
  
 <span data-ttu-id="9863f-118">otrzymasz komunikat o błędzie kompilatora:</span><span class="sxs-lookup"><span data-stu-id="9863f-118">you will get the compiler error message:</span></span>  
  
 `The left-hand side of an assignment must be an l-value`  
  
 <span data-ttu-id="9863f-119">która jest ten sam błąd, które pojawia się podczas próby przypisać wartość stałą.</span><span class="sxs-lookup"><span data-stu-id="9863f-119">which is the same error you get when you attempt to assign a value to a constant.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="9863f-120">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="9863f-120">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="9863f-121">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="9863f-121">See Also</span></span>  
 [<span data-ttu-id="9863f-122">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="9863f-122">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="9863f-123">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="9863f-123">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="9863f-124">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="9863f-124">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="9863f-125">Modyfikatory</span><span class="sxs-lookup"><span data-stu-id="9863f-125">Modifiers</span></span>](../../../csharp/language-reference/keywords/modifiers.md)  
 [<span data-ttu-id="9863f-126">const</span><span class="sxs-lookup"><span data-stu-id="9863f-126">const</span></span>](../../../csharp/language-reference/keywords/const.md)  
 [<span data-ttu-id="9863f-127">Pola</span><span class="sxs-lookup"><span data-stu-id="9863f-127">Fields</span></span>](../../../csharp/programming-guide/classes-and-structs/fields.md)
