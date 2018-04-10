---
title: unsafe (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
caps.latest.revision: 19
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1fffbe36e39d279b2364b178188381a403c8ff86
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="45238-102">unsafe (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="45238-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="45238-103">`unsafe` — Słowo kluczowe oznacza niebezpiecznym kontekście, który jest wymagany do żadnej operacji obejmujący wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="45238-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="45238-104">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="45238-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="45238-105">Można użyć `unsafe` modyfikatora w deklaracji typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="45238-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="45238-106">W związku z tym niebezpiecznym kontekście jest uważany za cały zakres tekstowa typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="45238-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="45238-107">Na przykład poniżej przedstawiono metody zadeklarowanej z `unsafe` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="45238-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```  
      unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="45238-108">Zakres niebezpiecznym kontekście rozciąga się od listy parametrów na końcu metody, więc wskaźniki można również na liście parametrów:</span><span class="sxs-lookup"><span data-stu-id="45238-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="45238-109">Blok niebezpieczny umożliwia również korzystanie z niebezpieczny kod wewnątrz tego bloku.</span><span class="sxs-lookup"><span data-stu-id="45238-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="45238-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="45238-110">For example:</span></span>  
  
```  
      unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="45238-111">Aby skompilować kod niezabezpieczony, należy określić [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="45238-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="45238-112">Niebezpieczny kod nie jest możliwe do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="45238-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="45238-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="45238-113">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="45238-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="45238-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="45238-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="45238-115">See Also</span></span>  
 [<span data-ttu-id="45238-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="45238-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="45238-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="45238-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="45238-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="45238-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="45238-119">Fixed — instrukcja</span><span class="sxs-lookup"><span data-stu-id="45238-119">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
 [<span data-ttu-id="45238-120">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="45238-120">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="45238-121">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="45238-121">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
