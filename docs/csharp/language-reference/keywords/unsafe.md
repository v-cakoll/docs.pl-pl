---
title: słowa kluczowego unsafe — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: 81a293a6922a71f7428167c50aed064d7387a099
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660414"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="1f3ea-102">unsafe (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="1f3ea-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="1f3ea-103">`unsafe` — Słowo kluczowe określa niebezpieczny kontekst, który jest wymagany we wszystkich operacjach obejmujących wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="1f3ea-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="1f3ea-104">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f3ea-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="1f3ea-105">Możesz użyć `unsafe` modyfikatora w deklaracji typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1f3ea-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="1f3ea-106">W związku z tym niebezpieczny kontekst jest uważany za cały zakres tekstowa typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="1f3ea-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="1f3ea-107">Na przykład, następujące jest zadeklarowana za pomocą metody `unsafe` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="1f3ea-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="1f3ea-108">Zakres niebezpieczny kontekst rozciąga się od listy parametrów na końcu metody, więc wskaźniki można również na liście parametrów:</span><span class="sxs-lookup"><span data-stu-id="1f3ea-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="1f3ea-109">Blok niebezpieczne umożliwia również korzystanie z niebezpieczny kod wewnątrz tego bloku.</span><span class="sxs-lookup"><span data-stu-id="1f3ea-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="1f3ea-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="1f3ea-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="1f3ea-111">Aby skompilować kod niebezpieczny, należy określić [/ unsafe](../compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1f3ea-111">To compile unsafe code, you must specify the [/unsafe](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="1f3ea-112">Niebezpieczny kod nie jest możliwe do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="1f3ea-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="1f3ea-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f3ea-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="1f3ea-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1f3ea-114">C# language specification</span></span>

<span data-ttu-id="1f3ea-115">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="1f3ea-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="1f3ea-116">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="1f3ea-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="1f3ea-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="1f3ea-117">See also</span></span>

- [<span data-ttu-id="1f3ea-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1f3ea-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="1f3ea-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1f3ea-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="1f3ea-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="1f3ea-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="1f3ea-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="1f3ea-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="1f3ea-122">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="1f3ea-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="1f3ea-123">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="1f3ea-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)