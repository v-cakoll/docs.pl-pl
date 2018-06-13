---
title: unsafe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: c476bdcea4993b27c0e8f8148a985f18a43ba09b
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34171957"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="e3029-102">unsafe (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e3029-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="e3029-103">`unsafe` — Słowo kluczowe oznacza niebezpiecznym kontekście, który jest wymagany do żadnej operacji obejmujący wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="e3029-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="e3029-104">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="e3029-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="e3029-105">Można użyć `unsafe` modyfikatora w deklaracji typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e3029-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="e3029-106">W związku z tym niebezpiecznym kontekście jest uważany za cały zakres tekstowa typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e3029-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="e3029-107">Na przykład poniżej przedstawiono metody zadeklarowanej z `unsafe` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="e3029-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```csharp  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="e3029-108">Zakres niebezpiecznym kontekście rozciąga się od listy parametrów na końcu metody, więc wskaźniki można również na liście parametrów:</span><span class="sxs-lookup"><span data-stu-id="e3029-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```csharp  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="e3029-109">Blok niebezpieczny umożliwia również korzystanie z niebezpieczny kod wewnątrz tego bloku.</span><span class="sxs-lookup"><span data-stu-id="e3029-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="e3029-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="e3029-110">For example:</span></span>  
  
```csharp  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="e3029-111">Aby skompilować kod niezabezpieczony, należy określić [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="e3029-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="e3029-112">Niebezpieczny kod nie jest możliwe do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="e3029-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e3029-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="e3029-113">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="e3029-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e3029-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e3029-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="e3029-115">See Also</span></span>  
 [<span data-ttu-id="e3029-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="e3029-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="e3029-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e3029-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="e3029-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e3029-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="e3029-119">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="e3029-119">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="e3029-120">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="e3029-120">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="e3029-121">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="e3029-121">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
