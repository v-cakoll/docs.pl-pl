---
title: Jak używać wskaźników do kopiowania macierzy bajtów — Przewodnik programowania w języku C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 8c1afc06fb567a923d604ad53dc26f94178a8d60
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2020
ms.locfileid: "84397418"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="3f4a8-102">Jak używać wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="3f4a8-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="3f4a8-103">Poniższy przykład używa wskaźników do kopiowania bajtów z jednej tablicy do innej.</span><span class="sxs-lookup"><span data-stu-id="3f4a8-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="3f4a8-104">W tym przykładzie użyto słowa kluczowego [UNSAFE](../../language-reference/keywords/unsafe.md) , które umożliwia używanie wskaźników w `Copy` metodzie.</span><span class="sxs-lookup"><span data-stu-id="3f4a8-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="3f4a8-105">[Stała](../../language-reference/keywords/fixed-statement.md) Instrukcja służy do deklarowania wskaźników do tablicy źródłowej i docelowej.</span><span class="sxs-lookup"><span data-stu-id="3f4a8-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="3f4a8-106">`fixed`Instrukcja *przypina* lokalizację źródłową i docelową tablicę w pamięci, dzięki czemu nie będą one przenoszone przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="3f4a8-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="3f4a8-107">Bloki pamięci dla tablic są odpięte po `fixed` zakończeniu bloku.</span><span class="sxs-lookup"><span data-stu-id="3f4a8-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="3f4a8-108">Ponieważ `Copy` Metoda w tym przykładzie używa `unsafe` słowa kluczowego, należy ją skompilować przy użyciu opcji [niebezpiecznego](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="3f4a8-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="3f4a8-109">Ten przykład uzyskuje dostęp do elementów obydwu tablic przy użyciu indeksów zamiast drugiego niezarządzanego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="3f4a8-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="3f4a8-110">Deklaracja `pSource` `pTarget` wskaźników i przypina tablicę.</span><span class="sxs-lookup"><span data-stu-id="3f4a8-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="3f4a8-111">Ta funkcja jest dostępna od języka C# 7,3.</span><span class="sxs-lookup"><span data-stu-id="3f4a8-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="3f4a8-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="3f4a8-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](snippets/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="3f4a8-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3f4a8-113">See also</span></span>

- [<span data-ttu-id="3f4a8-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3f4a8-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="3f4a8-115">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="3f4a8-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="3f4a8-116">-unsafe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="3f4a8-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="3f4a8-117">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="3f4a8-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
