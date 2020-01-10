---
title: Jak użyć wskaźników do kopiowania tablicy bajtów — C# Przewodnik programowania
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75698459"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="f5425-102">Jak używać wskaźników do kopiowania tablicy bajtów (C# Przewodnik programowania)</span><span class="sxs-lookup"><span data-stu-id="f5425-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="f5425-103">Poniższy przykład używa wskaźników do kopiowania bajtów z jednej tablicy do innej.</span><span class="sxs-lookup"><span data-stu-id="f5425-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="f5425-104">W tym przykładzie użyto słowa kluczowego [UNSAFE](../../language-reference/keywords/unsafe.md) , które umożliwia używanie wskaźników w metodzie `Copy`.</span><span class="sxs-lookup"><span data-stu-id="f5425-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="f5425-105">[Stała](../../language-reference/keywords/fixed-statement.md) Instrukcja służy do deklarowania wskaźników do tablicy źródłowej i docelowej.</span><span class="sxs-lookup"><span data-stu-id="f5425-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="f5425-106">Instrukcja `fixed` *przypina* lokalizację źródłową i docelową tablicę w pamięci, dzięki czemu nie będą one przenoszone przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="f5425-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="f5425-107">Bloki pamięci dla tablic są odpięte po zakończeniu bloku `fixed`.</span><span class="sxs-lookup"><span data-stu-id="f5425-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="f5425-108">Ponieważ metoda `Copy` w tym przykładzie używa słowa kluczowego `unsafe`, należy ją skompilować przy użyciu opcji [niebezpiecznego](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="f5425-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="f5425-109">Ten przykład uzyskuje dostęp do elementów obydwu tablic przy użyciu indeksów zamiast drugiego niezarządzanego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="f5425-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="f5425-110">Deklaracja `pSource` i `pTarget` wskaźników przypina tablicę.</span><span class="sxs-lookup"><span data-stu-id="f5425-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="f5425-111">Ta funkcja jest dostępna od C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="f5425-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="f5425-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="f5425-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="f5425-113">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f5425-113">See also</span></span>

- [<span data-ttu-id="f5425-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f5425-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="f5425-115">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="f5425-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="f5425-116">-unsafeC# (opcje kompilatora)</span><span class="sxs-lookup"><span data-stu-id="f5425-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="f5425-117">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="f5425-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
