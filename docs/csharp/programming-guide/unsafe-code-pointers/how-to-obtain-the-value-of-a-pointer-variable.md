---
title: 'Porady: uzyskiwanie wartości zmiennej wskaźnikowej (Przewodnik programowania w języku C#)'
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 66f341e193a0f018adb76a40617f85266519e602
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541195"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="56bcb-102">Porady: uzyskiwanie wartości zmiennej wskaźnikowej (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="56bcb-102">How to: Obtain the Value of a Pointer Variable (C# Programming Guide)</span></span>
<span data-ttu-id="56bcb-103">Użyj operatora pośredniego wskaźnika można uzyskać zmiennej w lokalizacji wskazywanej przez kursor.</span><span class="sxs-lookup"><span data-stu-id="56bcb-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="56bcb-104">Wyrażenie ma następującą postać, gdzie `p` jest typem wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="56bcb-104">The expression takes the following form, where `p` is a pointer type:</span></span>  
  
```  
*p;  
```  
  
 <span data-ttu-id="56bcb-105">Jednoargumentowy operator pośredni nie można używać na wyrażeniu dowolnego typu innego niż typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="56bcb-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="56bcb-106">Ponadto nie można zastosować go do [void](../../../csharp/language-reference/keywords/void.md) wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="56bcb-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  
  
 <span data-ttu-id="56bcb-107">Po zastosowaniu operatora pośredniego do [null](../../../csharp/language-reference/keywords/null.md) wskaźnika, wynik zależy od implementacji.</span><span class="sxs-lookup"><span data-stu-id="56bcb-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  
  
## <a name="example"></a><span data-ttu-id="56bcb-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="56bcb-108">Example</span></span>  
 <span data-ttu-id="56bcb-109">W poniższym przykładzie zmienna typu `char` odbywa się za pomocą wskaźników różnego typu.</span><span class="sxs-lookup"><span data-stu-id="56bcb-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="56bcb-110">Należy pamiętać, że adres `theChar` różnią się w celu uruchamiania, ponieważ można zmienić adresu fizycznego przydzielone do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="56bcb-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  
  
 [!code-csharp[csProgGuidePointers#5](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_1.cs)]  
  
 [!code-csharp[csProgGuidePointers#6](../../../csharp/programming-guide/unsafe-code-pointers/codesnippet/CSharp/how-to-obtain-the-value-of-a-pointer-variable_2.cs)]  
  
<span data-ttu-id="56bcb-111">**Wartość theChar = Z**
**adres theChar = 12F718**
**wartość pChar = Z**
**wartość Pinta = 90**</span><span class="sxs-lookup"><span data-stu-id="56bcb-111">**Value of theChar = Z**
**Address of theChar = 12F718**
**Value of pChar = Z**
**Value of pInt = 90**</span></span>

## <a name="see-also"></a><span data-ttu-id="56bcb-112">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="56bcb-112">See Also</span></span>

- [<span data-ttu-id="56bcb-113">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="56bcb-113">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="56bcb-114">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="56bcb-114">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)  
- [<span data-ttu-id="56bcb-115">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="56bcb-115">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)  
- [<span data-ttu-id="56bcb-116">Typy</span><span class="sxs-lookup"><span data-stu-id="56bcb-116">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
- [<span data-ttu-id="56bcb-117">unsafe</span><span class="sxs-lookup"><span data-stu-id="56bcb-117">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="56bcb-118">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="56bcb-118">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="56bcb-119">stackalloc</span><span class="sxs-lookup"><span data-stu-id="56bcb-119">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
