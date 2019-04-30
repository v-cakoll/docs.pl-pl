---
title: 'Porady: uzyskiwanie wartości zmiennej wskaźnikowej - C# Programming Guide'
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- pointer expressions [C#], indirection
- pointers [C#], indirection
- variables [C#], pointers
- pointers [C#], * operator
ms.assetid: 460a813a-4995-44c1-9de2-213b91dc7668
ms.openlocfilehash: 288d8cb2d286f55cc9a162614d45ef7b298f79f1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61677988"
---
# <a name="how-to-obtain-the-value-of-a-pointer-variable-c-programming-guide"></a><span data-ttu-id="395c0-102">Porady: uzyskiwanie wartości zmiennej wskaźnikowej (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="395c0-102">How to: obtain the value of a pointer variable (C# Programming Guide)</span></span>

<span data-ttu-id="395c0-103">Użyj operatora pośredniego wskaźnika można uzyskać zmiennej w lokalizacji wskazywanej przez kursor.</span><span class="sxs-lookup"><span data-stu-id="395c0-103">Use the pointer indirection operator to obtain the variable at the location pointed to by a pointer.</span></span> <span data-ttu-id="395c0-104">Wyrażenie ma następującą postać, gdzie `p` jest typem wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="395c0-104">The expression takes the following form, where `p` is a pointer type:</span></span>  

```csharp
*p;  
```

<span data-ttu-id="395c0-105">Jednoargumentowy operator pośredni nie można używać na wyrażeniu dowolnego typu innego niż typ wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="395c0-105">You cannot use the unary indirection operator on an expression of any type other than the pointer type.</span></span> <span data-ttu-id="395c0-106">Ponadto nie można zastosować go do [void](../../../csharp/language-reference/keywords/void.md) wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="395c0-106">Also, you cannot apply it to a [void](../../../csharp/language-reference/keywords/void.md) pointer.</span></span>  

<span data-ttu-id="395c0-107">Po zastosowaniu operatora pośredniego do [null](../../../csharp/language-reference/keywords/null.md) wskaźnika, wynik zależy od implementacji.</span><span class="sxs-lookup"><span data-stu-id="395c0-107">When you apply the indirection operator to a [null](../../../csharp/language-reference/keywords/null.md) pointer, the result depends on the implementation.</span></span>  

## <a name="example"></a><span data-ttu-id="395c0-108">Przykład</span><span class="sxs-lookup"><span data-stu-id="395c0-108">Example</span></span>

<span data-ttu-id="395c0-109">W poniższym przykładzie zmienna typu `char` odbywa się za pomocą wskaźników różnego typu.</span><span class="sxs-lookup"><span data-stu-id="395c0-109">In the following example, a variable of the type `char` is accessed by using pointers of different types.</span></span> <span data-ttu-id="395c0-110">Należy pamiętać, że adres `theChar` różnią się w celu uruchamiania, ponieważ można zmienić adresu fizycznego przydzielone do zmiennej.</span><span class="sxs-lookup"><span data-stu-id="395c0-110">Note that the address of `theChar` will vary from run to run, because the physical address allocated to a variable can change.</span></span>  

 [!code-csharp[csProgGuidePointers#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers2.cs#5)]  

 [!code-csharp[csProgGuidePointers#6](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csProgGuidePointers/CS/Pointers.cs#6)]  
  
<span data-ttu-id="395c0-111">**Wartość theChar = Z**</span><span class="sxs-lookup"><span data-stu-id="395c0-111">**Value of theChar = Z**</span></span>  
<span data-ttu-id="395c0-112">**Adres theChar = 12F718**</span><span class="sxs-lookup"><span data-stu-id="395c0-112">**Address of theChar = 12F718**</span></span>  
<span data-ttu-id="395c0-113">**Wartość pChar = Z**</span><span class="sxs-lookup"><span data-stu-id="395c0-113">**Value of pChar = Z**</span></span>  
<span data-ttu-id="395c0-114">**Wartość Pinta = 90**</span><span class="sxs-lookup"><span data-stu-id="395c0-114">**Value of pInt = 90**</span></span>  

## <a name="see-also"></a><span data-ttu-id="395c0-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="395c0-115">See also</span></span>

- [<span data-ttu-id="395c0-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="395c0-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="395c0-117">Wyrażenia wskaźników</span><span class="sxs-lookup"><span data-stu-id="395c0-117">Pointer Expressions</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-expressions.md)
- [<span data-ttu-id="395c0-118">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="395c0-118">Pointer types</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="395c0-119">Typy</span><span class="sxs-lookup"><span data-stu-id="395c0-119">Types</span></span>](../../../csharp/language-reference/keywords/types.md)
- [<span data-ttu-id="395c0-120">unsafe</span><span class="sxs-lookup"><span data-stu-id="395c0-120">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)
- [<span data-ttu-id="395c0-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="395c0-121">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
- [<span data-ttu-id="395c0-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="395c0-122">stackalloc</span></span>](../../../csharp/language-reference/keywords/stackalloc.md)
