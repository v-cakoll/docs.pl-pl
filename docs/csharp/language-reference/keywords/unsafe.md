---
title: niebezpieczne słowo kluczowe — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75712991"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="a0138-102">unsafe (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="a0138-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="a0138-103">Słowo `unsafe` kluczowe oznacza niebezpieczny kontekst, który jest wymagany dla każdej operacji z udziałem wskaźników.</span><span class="sxs-lookup"><span data-stu-id="a0138-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="a0138-104">Aby uzyskać więcej informacji, zobacz [Niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="a0138-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="a0138-105">Modyfikatora `unsafe` można użyć w deklaracji typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="a0138-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="a0138-106">Cały zakres tekstowy typu lub elementu członkowskiego jest zatem uważany za niebezpieczny kontekst.</span><span class="sxs-lookup"><span data-stu-id="a0138-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="a0138-107">Na przykład, o to metoda `unsafe` zadeklarowana za pomocą modyfikatora:</span><span class="sxs-lookup"><span data-stu-id="a0138-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="a0138-108">Zakres niebezpiecznego kontekstu rozciąga się od listy parametrów do końca metody, więc wskaźniki mogą być również używane na liście parametrów:</span><span class="sxs-lookup"><span data-stu-id="a0138-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="a0138-109">Można również użyć niebezpiecznego bloku, aby włączyć użycie niebezpiecznego kodu wewnątrz tego bloku.</span><span class="sxs-lookup"><span data-stu-id="a0138-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="a0138-110">Przykład:</span><span class="sxs-lookup"><span data-stu-id="a0138-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="a0138-111">Aby skompilować niebezpieczny kod, [`-unsafe`](../compiler-options/unsafe-compiler-option.md) należy określić opcję kompilatora.</span><span class="sxs-lookup"><span data-stu-id="a0138-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="a0138-112">Niebezpieczny kod nie jest weryfikowalny przez program runtime języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="a0138-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="a0138-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="a0138-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="a0138-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a0138-114">C# language specification</span></span>

<span data-ttu-id="a0138-115">Aby uzyskać więcej informacji, zobacz [Niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) w [specyfikacji języka Języka C#](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="a0138-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="a0138-116">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="a0138-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="a0138-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a0138-117">See also</span></span>

- [<span data-ttu-id="a0138-118">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="a0138-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="a0138-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="a0138-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="a0138-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="a0138-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="a0138-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="a0138-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="a0138-122">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="a0138-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="a0138-123">Bufory o stałym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="a0138-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
