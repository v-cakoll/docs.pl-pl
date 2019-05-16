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
ms.openlocfilehash: 8b220e0d6b7e6ab5a7b6d964d1910eaafb63d2d9
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633933"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="f2cb6-102">unsafe (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f2cb6-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="f2cb6-103">`unsafe` — Słowo kluczowe określa niebezpieczny kontekst, który jest wymagany we wszystkich operacjach obejmujących wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="f2cb6-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="f2cb6-104">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2cb6-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="f2cb6-105">Możesz użyć `unsafe` modyfikatora w deklaracji typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f2cb6-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="f2cb6-106">W związku z tym niebezpieczny kontekst jest uważany za cały zakres tekstowa typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f2cb6-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="f2cb6-107">Na przykład, następujące jest zadeklarowana za pomocą metody `unsafe` modyfikator:</span><span class="sxs-lookup"><span data-stu-id="f2cb6-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="f2cb6-108">Zakres niebezpieczny kontekst rozciąga się od listy parametrów na końcu metody, więc wskaźniki można również na liście parametrów:</span><span class="sxs-lookup"><span data-stu-id="f2cb6-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="f2cb6-109">Blok niebezpieczne umożliwia również korzystanie z niebezpieczny kod wewnątrz tego bloku.</span><span class="sxs-lookup"><span data-stu-id="f2cb6-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="f2cb6-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="f2cb6-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="f2cb6-111">Aby skompilować kod niebezpieczny, należy określić [/ unsafe](../compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f2cb6-111">To compile unsafe code, you must specify the [/unsafe](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="f2cb6-112">Niebezpieczny kod nie jest możliwe do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="f2cb6-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="f2cb6-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="f2cb6-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="f2cb6-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f2cb6-114">C# language specification</span></span>

<span data-ttu-id="f2cb6-115">Aby uzyskać więcej informacji, zobacz [niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](../language-specification/index.md).</span><span class="sxs-lookup"><span data-stu-id="f2cb6-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](../language-specification/index.md).</span></span> <span data-ttu-id="f2cb6-116">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="f2cb6-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="f2cb6-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f2cb6-117">See also</span></span>

- [<span data-ttu-id="f2cb6-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f2cb6-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f2cb6-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f2cb6-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f2cb6-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="f2cb6-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="f2cb6-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="f2cb6-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="f2cb6-122">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="f2cb6-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="f2cb6-123">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="f2cb6-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
