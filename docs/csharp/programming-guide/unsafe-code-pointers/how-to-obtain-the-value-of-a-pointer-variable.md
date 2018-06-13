---
title: 'Porady: uzyskiwanie wartości zmiennej wskaźnikowej (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: c53026149837681235c6d1001707a25b9c8b40b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33322955"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="16911-102">Porady: uzyskiwanie wartości zmiennej wskaźnikowej (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="16911-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="16911-103">Operator pośredni wskaźnik umożliwia uzyskanie zmiennej w lokalizacji wskazywanej przez kursor.</span><span class="sxs-lookup"><span data-stu-id="16911-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="16911-104">Wyrażenie ma następującą postać, gdzie `p` jest typem wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="16911-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="16911-105">Nie można użyć operatora jednoargumentowego operatora pośredniego na wyrażeniu dowolnego typu, innego niż typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="16911-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="16911-106">Ponadto nie można zastosować go do [void](../../../csharp/language-reference/keywords/void.md) wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="16911-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="16911-107">Po zastosowaniu operator pośredni do [null](../../../csharp/language-reference/keywords/null.md) wskaźnika, wynik zależy od implementacji.</span><span class="sxs-lookup"><span data-stu-id="16911-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="16911-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="16911-108">Example</span></span>  
 <span data-ttu-id="16911-109">W poniższym przykładzie zmienna typu `char` uzyskuje się dostęp za pomocą wskaźniki różnych typów.</span><span class="sxs-lookup"><span data-stu-id="16911-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="16911-110">Należy pamiętać, że adres `theChar` różni się od do rozpoczęcia realizacji, nie można zmienić adresu fizycznego przydzielone do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="16911-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
 <span data-ttu-id="16911-111">**Wartość theChar = Z**</span><span class="sxs-lookup"><span data-stu-id="16911-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="16911-112">**Adres theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="16911-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="16911-113">**Wartość pChar = Z** </span><span class="sxs-lookup"><span data-stu-id="16911-113">**Value of pChar = Z** </span></span>  
<span data-ttu-id="16911-114">**Wartość Pinta = 90**</span><span class="sxs-lookup"><span data-stu-id="16911-114">**Value of pInt = 90**</span></span>    
## <a name="see-also"></a><span data-ttu-id="16911-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="16911-115">See Also</span></span>  
 [<span data-ttu-id="16911-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="16911-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="16911-117">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="16911-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
 [<span data-ttu-id="16911-118">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="16911-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
 [<span data-ttu-id="16911-119">Typy</span><span class="sxs-lookup"><span data-stu-id="16911-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="16911-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="16911-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="16911-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="16911-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="16911-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="16911-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
