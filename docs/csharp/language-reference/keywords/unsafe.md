---
title: niebezpieczne słowo kluczowe C# — odwołanie
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: aa22eac9d4ae06753bbed1fd5733eddeddd81a46
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422268"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="07e0c-102">unsafe (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="07e0c-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="07e0c-103">Słowo kluczowe `unsafe` oznacza niebezpieczny kontekst, który jest wymagany dla każdej operacji obejmującej wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="07e0c-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="07e0c-104">Aby uzyskać więcej informacji, zobacz artykuł [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="07e0c-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="07e0c-105">Można użyć modyfikatora `unsafe` w deklaracji typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="07e0c-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="07e0c-106">Cały tekstowy zakres typu lub elementu członkowskiego jest traktowany jako niebezpieczny kontekst.</span><span class="sxs-lookup"><span data-stu-id="07e0c-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="07e0c-107">Na przykład poniżej przedstawiono metodę zadeklarowaną z modyfikatorem `unsafe`:</span><span class="sxs-lookup"><span data-stu-id="07e0c-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="07e0c-108">Zakres niebezpiecznego kontekstu rozciąga się od listy parametrów na koniec metody, dlatego na liście parametrów można również używać wskaźników:</span><span class="sxs-lookup"><span data-stu-id="07e0c-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="07e0c-109">Można również użyć niebezpiecznego bloku, aby umożliwić użycie niebezpiecznego kodu wewnątrz tego bloku.</span><span class="sxs-lookup"><span data-stu-id="07e0c-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="07e0c-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="07e0c-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="07e0c-111">Aby skompilować niebezpieczny kod, należy określić opcję kompilatora [`-unsafe`](../compiler-options/unsafe-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="07e0c-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="07e0c-112">Kod niebezpieczny nie jest możliwy do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="07e0c-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="07e0c-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="07e0c-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="07e0c-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="07e0c-114">C# language specification</span></span>

<span data-ttu-id="07e0c-115">Aby uzyskać więcej informacji, zobacz artykuł [niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="07e0c-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="07e0c-116">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="07e0c-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="07e0c-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="07e0c-117">See also</span></span>

- [<span data-ttu-id="07e0c-118">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="07e0c-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="07e0c-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="07e0c-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="07e0c-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="07e0c-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="07e0c-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="07e0c-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="07e0c-122">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="07e0c-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="07e0c-123">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="07e0c-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
