---
title: "Porady: bezpieczne rzutowanie bool? na bool (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
caps.latest.revision: "9"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1a6fa65c15bb5f1da9960dbc17bd25b4087ab862
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a><span data-ttu-id="ff520-102">Porady: bezpieczne rzutowanie bool? na bool (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="ff520-102">How to: Safely Cast from bool? to bool (C# Programming Guide)</span></span>
<span data-ttu-id="ff520-103">`bool?` Typ dopuszczający wartość null, mogą zawierać trzy różne wartości: `true`, `false`, i `null`.</span><span class="sxs-lookup"><span data-stu-id="ff520-103">The `bool?` nullable type can contain three different values: `true`, `false`, and `null`.</span></span> <span data-ttu-id="ff520-104">W związku z tym `bool?` typu nie można używać w warunków, takich jak z `if`, `for`, lub `while`.</span><span class="sxs-lookup"><span data-stu-id="ff520-104">Therefore, the `bool?` type cannot be used in conditionals such as with `if`, `for`, or `while`.</span></span> <span data-ttu-id="ff520-105">Na przykład następujący kod powoduje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="ff520-105">For example, the following code causes a compiler error.</span></span>  
  
```  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 <span data-ttu-id="ff520-106">To jest niedozwolona, ponieważ nie jest jasne co `null` oznacza, że w kontekście warunkowego.</span><span class="sxs-lookup"><span data-stu-id="ff520-106">This is not allowed because it is unclear what `null` means in the context of a conditional.</span></span> <span data-ttu-id="ff520-107">Umożliwia `bool?` w instrukcji warunkowej, sprawdź najpierw jego <xref:System.Nullable%601.HasValue%2A> właściwości, aby upewnić się, że jego wartość nie jest `null`, a następnie rzutować go na `bool`.</span><span class="sxs-lookup"><span data-stu-id="ff520-107">To use a `bool?` in a conditional statement, first check its <xref:System.Nullable%601.HasValue%2A> property to ensure that its value is not `null`, and then cast it to `bool`.</span></span> <span data-ttu-id="ff520-108">Aby uzyskać więcej informacji, zobacz [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="ff520-108">For more information, see [bool](../../../csharp/language-reference/keywords/bool.md).</span></span> <span data-ttu-id="ff520-109">Jeśli wykonać Rzutowanie na `bool?` o wartości `null`, <xref:System.InvalidOperationException> zostanie zgłoszony w test warunkowy.</span><span class="sxs-lookup"><span data-stu-id="ff520-109">If you perform the cast on a `bool?` with a value of `null`, a <xref:System.InvalidOperationException> will be thrown in the conditional test.</span></span> <span data-ttu-id="ff520-110">Poniższy przykład przedstawia sposób bezpieczne rzutowanie z `bool?` do `bool`:</span><span class="sxs-lookup"><span data-stu-id="ff520-110">The following example shows one way to safely cast from `bool?` to `bool`:</span></span>  
  
## <a name="example"></a><span data-ttu-id="ff520-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="ff520-111">Example</span></span>  
  
```csharp  
bool? test = null;  
// Other code that may or may not  
// give a value to test.  
if(!test.HasValue) //check for a value  
{  
    // Assume that IsInitialized  
    // returns either true or false.  
    test = IsInitialized();  
}  
if((bool)test) //now this cast is safe  
{  
   // Do something.  
}  
```  
  
## <a name="see-also"></a><span data-ttu-id="ff520-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ff520-112">See Also</span></span>  
 [<span data-ttu-id="ff520-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ff520-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ff520-114">Słowa kluczowe literału</span><span class="sxs-lookup"><span data-stu-id="ff520-114">Literal Keywords</span></span>](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [<span data-ttu-id="ff520-115">Typy dopuszczające wartości zerowe</span><span class="sxs-lookup"><span data-stu-id="ff520-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="ff520-116">?? Operator</span><span class="sxs-lookup"><span data-stu-id="ff520-116">?? Operator</span></span>](../../../csharp/language-reference/operators/null-conditional-operator.md)
