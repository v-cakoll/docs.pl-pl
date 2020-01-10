---
title: niebezpieczne słowo kluczowe C# — odwołanie
ms.date: 07/20/2015
f1_keywords:
- unsafe_CSharpKeyword
- unsafe
helpviewer_keywords:
- unsafe keyword [C#]
ms.assetid: 7e818009-1c6e-4b9e-b769-3728a01586a0
ms.openlocfilehash: ef98809eae0329c028dfb318c4a437aae4736db1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75712991"
---
# <a name="unsafe-c-reference"></a><span data-ttu-id="82143-102">unsafe (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="82143-102">unsafe (C# Reference)</span></span>

<span data-ttu-id="82143-103">Słowo kluczowe `unsafe` oznacza niebezpieczny kontekst, który jest wymagany dla każdej operacji obejmującej wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="82143-103">The `unsafe` keyword denotes an unsafe context, which is required for any operation involving pointers.</span></span> <span data-ttu-id="82143-104">Aby uzyskać więcej informacji, zobacz artykuł [niebezpieczny kod i wskaźniki](../../programming-guide/unsafe-code-pointers/index.md).</span><span class="sxs-lookup"><span data-stu-id="82143-104">For more information, see [Unsafe Code and Pointers](../../programming-guide/unsafe-code-pointers/index.md).</span></span>

<span data-ttu-id="82143-105">Można użyć modyfikatora `unsafe` w deklaracji typu lub elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="82143-105">You can use the `unsafe` modifier in the declaration of a type or a member.</span></span> <span data-ttu-id="82143-106">Cały tekstowy zakres typu lub elementu członkowskiego jest traktowany jako niebezpieczny kontekst.</span><span class="sxs-lookup"><span data-stu-id="82143-106">The entire textual extent of the type or member is therefore considered an unsafe context.</span></span> <span data-ttu-id="82143-107">Na przykład poniżej przedstawiono metodę zadeklarowaną z modyfikatorem `unsafe`:</span><span class="sxs-lookup"><span data-stu-id="82143-107">For example, the following is a method declared with the `unsafe` modifier:</span></span>

```csharp
unsafe static void FastCopy(byte[] src, byte[] dst, int count)
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="82143-108">Zakres niebezpiecznego kontekstu rozciąga się od listy parametrów na koniec metody, dlatego na liście parametrów można również używać wskaźników:</span><span class="sxs-lookup"><span data-stu-id="82143-108">The scope of the unsafe context extends from the parameter list to the end of the method, so pointers can also be used in the parameter list:</span></span>

```csharp
unsafe static void FastCopy ( byte* ps, byte* pd, int count ) {...}
```

<span data-ttu-id="82143-109">Można również użyć niebezpiecznego bloku, aby umożliwić użycie niebezpiecznego kodu wewnątrz tego bloku.</span><span class="sxs-lookup"><span data-stu-id="82143-109">You can also use an unsafe block to enable the use of an unsafe code inside this block.</span></span> <span data-ttu-id="82143-110">Na przykład:</span><span class="sxs-lookup"><span data-stu-id="82143-110">For example:</span></span>

```csharp
unsafe
{
    // Unsafe context: can use pointers here.
}
```

<span data-ttu-id="82143-111">Aby skompilować niebezpieczny kod, należy określić opcję kompilatora [`-unsafe`](../compiler-options/unsafe-compiler-option.md) .</span><span class="sxs-lookup"><span data-stu-id="82143-111">To compile unsafe code, you must specify the [`-unsafe`](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span> <span data-ttu-id="82143-112">Kod niebezpieczny nie jest możliwy do zweryfikowania przez środowisko uruchomieniowe języka wspólnego.</span><span class="sxs-lookup"><span data-stu-id="82143-112">Unsafe code is not verifiable by the common language runtime.</span></span>

## <a name="example"></a><span data-ttu-id="82143-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="82143-113">Example</span></span>

[!code-csharp[csrefKeywordsModifiers#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="82143-114">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="82143-114">C# language specification</span></span>

<span data-ttu-id="82143-115">Aby uzyskać więcej informacji, zobacz artykuł [niebezpieczny kod](~/_csharplang/spec/unsafe-code.md) w [ C# specyfikacji języka](/dotnet/csharp/language-reference/language-specification/introduction).</span><span class="sxs-lookup"><span data-stu-id="82143-115">For more information, see [Unsafe code](~/_csharplang/spec/unsafe-code.md) in the [C# Language Specification](/dotnet/csharp/language-reference/language-specification/introduction).</span></span> <span data-ttu-id="82143-116">Specyfikacja języka jest ostatecznym źródłem informacji o składni i użyciu języka C#.</span><span class="sxs-lookup"><span data-stu-id="82143-116">The language specification is the definitive source for C# syntax and usage.</span></span>

## <a name="see-also"></a><span data-ttu-id="82143-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="82143-117">See also</span></span>

- [<span data-ttu-id="82143-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="82143-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="82143-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="82143-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="82143-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="82143-120">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="82143-121">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="82143-121">fixed Statement</span></span>](fixed-statement.md)
- [<span data-ttu-id="82143-122">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="82143-122">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="82143-123">Bufory o ustalonym rozmiarze</span><span class="sxs-lookup"><span data-stu-id="82143-123">Fixed Size Buffers</span></span>](../../programming-guide/unsafe-code-pointers/fixed-size-buffers.md)
