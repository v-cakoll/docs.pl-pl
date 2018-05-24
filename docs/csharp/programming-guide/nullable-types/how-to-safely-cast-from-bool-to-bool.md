---
title: 'Porady: bezpieczne rzutowanie bool? na bool (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- casting [C#], nullable types
- nullable types [C#], casting bool? to bool
ms.assetid: e06e4274-a443-422d-8ef1-9dbf9df55237
ms.openlocfilehash: e04e34abd477730f9dd01486ec6bddcde4943edc
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
---
# <a name="how-to-safely-cast-from-bool-to-bool-c-programming-guide"></a><span data-ttu-id="11d92-102">Porady: bezpieczne rzutowanie bool? na bool (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="11d92-102">How to: Safely Cast from bool? to bool (C# Programming Guide)</span></span>
<span data-ttu-id="11d92-103">`bool?` Typ dopuszczający wartość null, mogą zawierać trzy różne wartości: `true`, `false`, i `null`.</span><span class="sxs-lookup"><span data-stu-id="11d92-103">The `bool?` nullable type can contain three different values: `true`, `false`, and `null`.</span></span> <span data-ttu-id="11d92-104">W związku z tym `bool?` typu nie można używać w warunków, takich jak z `if`, `for`, lub `while`.</span><span class="sxs-lookup"><span data-stu-id="11d92-104">Therefore, the `bool?` type cannot be used in conditionals such as with `if`, `for`, or `while`.</span></span> <span data-ttu-id="11d92-105">Na przykład następujący kod powoduje błąd kompilatora.</span><span class="sxs-lookup"><span data-stu-id="11d92-105">For example, the following code causes a compiler error.</span></span>  
  
```csharp  
bool? b = null;  
if (b) // Error CS0266.  
{  
}  
```  
  
 <span data-ttu-id="11d92-106">To jest niedozwolona, ponieważ nie jest jasne co `null` oznacza, że w kontekście warunkowego.</span><span class="sxs-lookup"><span data-stu-id="11d92-106">This is not allowed because it is unclear what `null` means in the context of a conditional.</span></span> <span data-ttu-id="11d92-107">Umożliwia `bool?` w instrukcji warunkowej, sprawdź najpierw jego <xref:System.Nullable%601.HasValue%2A> właściwości, aby upewnić się, że jego wartość nie jest `null`, a następnie rzutować go na `bool`.</span><span class="sxs-lookup"><span data-stu-id="11d92-107">To use a `bool?` in a conditional statement, first check its <xref:System.Nullable%601.HasValue%2A> property to ensure that its value is not `null`, and then cast it to `bool`.</span></span> <span data-ttu-id="11d92-108">Aby uzyskać więcej informacji, zobacz [bool](../../../csharp/language-reference/keywords/bool.md).</span><span class="sxs-lookup"><span data-stu-id="11d92-108">For more information, see [bool](../../../csharp/language-reference/keywords/bool.md).</span></span> <span data-ttu-id="11d92-109">Jeśli wykonać Rzutowanie na `bool?` o wartości `null`, <xref:System.InvalidOperationException> zostanie zgłoszony w test warunkowy.</span><span class="sxs-lookup"><span data-stu-id="11d92-109">If you perform the cast on a `bool?` with a value of `null`, a <xref:System.InvalidOperationException> will be thrown in the conditional test.</span></span> <span data-ttu-id="11d92-110">Poniższy przykład przedstawia sposób bezpieczne rzutowanie z `bool?` do `bool`:</span><span class="sxs-lookup"><span data-stu-id="11d92-110">The following example shows one way to safely cast from `bool?` to `bool`:</span></span>  
  
## <a name="example"></a><span data-ttu-id="11d92-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="11d92-111">Example</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="11d92-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11d92-112">See Also</span></span>  
 [<span data-ttu-id="11d92-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="11d92-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="11d92-114">Słowa kluczowe literału</span><span class="sxs-lookup"><span data-stu-id="11d92-114">Literal Keywords</span></span>](../../../csharp/language-reference/keywords/literal-keywords.md)  
 [<span data-ttu-id="11d92-115">Typy dopuszczające wartości null</span><span class="sxs-lookup"><span data-stu-id="11d92-115">Nullable Types</span></span>](../../../csharp/programming-guide/nullable-types/index.md)  
 [<span data-ttu-id="11d92-116">??, operator</span><span class="sxs-lookup"><span data-stu-id="11d92-116">?? Operator</span></span>](../../../csharp/language-reference/operators/null-coalescing-operator.md)
