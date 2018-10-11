---
title: unsafe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: f4fcff02166091ae5dbd83e7ddf7762373fd9836
ms.sourcegitcommit: 2eb5ca4956231c1a0efd34b6a9cab6153a5438af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/11/2018
ms.locfileid: "49086456"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="aa49b-102">unsafe (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="aa49b-102">unsafe (C# Reference)</span></span>
<span data-ttu-id="aa49b-103">`unsafe` — Słowo kluczowe określa niebezpieczny kontekst, który jest wymagany we wszystkich operacjach obejmujących wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="aa49b-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="aa49b-104">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="aa49b-104">For more information, see [Unsafe Code and Pointers](../../../csharp/programming-guide/unsafe-code-pointers/index.md).</span></span>  
  
 <span data-ttu-id="aa49b-105">Możesz użyć `unsafe` modyfikatora w deklaracji typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="aa49b-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="aa49b-106">W związku z tym niebezpieczny kontekst jest uważany za cały zakres tekstowa typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="aa49b-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="aa49b-107">Na przykład, następujące jest zadeklarowana za pomocą metody `unsafe` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="aa49b-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>  
  
```csharp  
unsafe static void FastCopy(byte[] src, byte[] dst, int count)  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="aa49b-108">Zakres niebezpieczny kontekst rozciąga się od listy parametrów na końcu metody, więc wskaźniki można również na liście parametrów:</span><span class="sxs-lookup"><span data-stu-id="aa49b-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>  
  
```csharp  
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}  
```  
  
 <span data-ttu-id="aa49b-109">Blok niebezpieczne umożliwia również korzystanie z niebezpieczny kod wewnątrz tego bloku.</span><span class="sxs-lookup"><span data-stu-id="aa49b-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="aa49b-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="aa49b-110">For example:</span></span>  
  
```csharp  
unsafe  
{  
    // Unsafe context: can use pointers here.  
}  
```  
  
 <span data-ttu-id="aa49b-111">Aby skompilować kod niebezpieczny, należy określić [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="aa49b-111">To compile unsafe code, you must specify the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="aa49b-112">Niebezpieczny kod nie jest możliwe do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="aa49b-112">Unsafe code is not verifiable by the common language runtime.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aa49b-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="aa49b-113">Example</span></span>  
 [!code-csharp[csrefKeywordsModifiers#22](../../../csharp/language-reference/keywords/codesnippet/CSharp/unsafe_1.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="aa49b-114">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="aa49b-114">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="aa49b-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="aa49b-115">See Also</span></span>

- [<span data-ttu-id="aa49b-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="aa49b-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="aa49b-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="aa49b-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="aa49b-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="aa49b-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
- [<span data-ttu-id="aa49b-119">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="aa49b-119">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)  
- [<span data-ttu-id="aa49b-120">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="aa49b-120">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="aa49b-121">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="aa49b-121">Fixed Size Buffers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
