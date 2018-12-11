---
title: 'Porady: uzyskiwanie dostępu do członka za pomocą wskaźnika - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointers [C#], member access
ms.assetid: 1e998498-8c85-4a78-8ce2-4d8c20f08342
ms.openlocfilehash: 777c6e1aa057bd0abe81adc63bed1d947f11b837
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53240596"
---
# <a name="how-to-access-a-member-with-a-pointer-c-programming-guide"></a><span data-ttu-id="7e0b9-102">Porady: uzyskiwanie dostępu do członka za pomocą wskaźnika (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="7e0b9-102">How to: access a member with a pointer (C# Programming Guide)</span></span>
<span data-ttu-id="7e0b9-103">Do uzyskania dostępu do członka struktury, która jest zadeklarowana w niebezpiecznym kontekście, można używać operatora dostępu do elementu członkowskiego, jak pokazano w poniższym przykładzie, w którym `p` jest wskaźnikiem do [struktury](../../../csharp/language-reference/keywords/struct.md) zawierający element członkowski `x`.</span><span class="sxs-lookup"><span data-stu-id="7e0b9-103">To access a member of a struct that is declared in an unsafe context, you can use the member access operator as shown in the following example in which `p` is a pointer to a [struct](../../../csharp/language-reference/keywords/struct.md) that contains a member `x`.</span></span>  
  
```  
CoOrds* p = &home;  
p -> x = 25; //member access operator ->  
```  
  
## <a name="example"></a><span data-ttu-id="7e0b9-104">Przykład</span><span class="sxs-lookup"><span data-stu-id="7e0b9-104">Example</span></span>  
 <span data-ttu-id="7e0b9-105">W tym przykładzie [struktury](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, zawierający dwie współrzędne `x` i `y` jest zadeklarowana i uruchomiony.</span><span class="sxs-lookup"><span data-stu-id="7e0b9-105">In this example, a [struct](../../../csharp/language-reference/keywords/struct.md), `CoOrds`, that contains the two coordinates `x` and `y` is declared and instantiated.</span></span> <span data-ttu-id="7e0b9-106">Za pomocą operatora dostępu do elementu członkowskiego `->` i wskaźnik do wystąpienia `home`, `x` i `y` mają przypisane wartości.</span><span class="sxs-lookup"><span data-stu-id="7e0b9-106">By using the member access operator `->` and a pointer to the instance `home`, `x` and `y` are assigned values.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="7e0b9-107">Należy zauważyć, że wyrażenie `p->x` jest równoważne wyrażeniu `(*p).x`, i ten sam efekt można uzyskać przy użyciu jednej z dwóch wyrażeń.</span><span class="sxs-lookup"><span data-stu-id="7e0b9-107">Notice that the expression `p->x` is equivalent to the expression `(*p).x`, and you can obtain the same result by using either of the two expressions.</span></span>  
  
 [!code-csharp[csProgGuidePointers#9](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#10](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-access-a-member-with-a-pointer_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7e0b9-108">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="7e0b9-108">See Also</span></span>

- [<span data-ttu-id="7e0b9-109">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="7e0b9-109">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="7e0b9-110">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="7e0b9-110">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="7e0b9-111">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="7e0b9-111">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="7e0b9-112">Typy</span><span class="sxs-lookup"><span data-stu-id="7e0b9-112">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="7e0b9-113">unsafe</span><span class="sxs-lookup"><span data-stu-id="7e0b9-113">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="7e0b9-114">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="7e0b9-114">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="7e0b9-115">stackalloc</span><span class="sxs-lookup"><span data-stu-id="7e0b9-115">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
