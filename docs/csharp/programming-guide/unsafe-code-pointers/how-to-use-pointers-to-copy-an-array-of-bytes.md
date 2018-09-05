---
title: 'Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 061bbbc4557cb25d39edfb1f6235bb065a5de7bd
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43541461"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="63740-102">Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="63740-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="63740-103">W poniższym przykładzie użyto wskaźników do skopiowania do innej tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="63740-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="63740-104">W tym przykładzie użyto [niebezpieczne](../../language-reference/keywords/unsafe.md) — słowo kluczowe, co pozwala na użycie wskaźników w `Copy` metody.</span><span class="sxs-lookup"><span data-stu-id="63740-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="63740-105">[Stałej](../../language-reference/keywords/fixed-statement.md) instrukcja jest używane do deklarowania wskaźniki do tablic źródłowym i docelowym.</span><span class="sxs-lookup"><span data-stu-id="63740-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="63740-106">`fixed` Instrukcji *numerów PIN* lokalizacji źródłowych i docelowych Indeksy tablic w pamięci, dzięki czemu nie będą przenoszone przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="63740-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="63740-107">Bloki pamięci dla tablic, są odpięte, gdy `fixed` blok zostanie ukończona.</span><span class="sxs-lookup"><span data-stu-id="63740-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="63740-108">Ponieważ `Copy` korzysta z metody w tym przykładzie `unsafe` — słowo kluczowe, jego musi być skompilowana przy użyciu [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="63740-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="63740-109">Ten przykład uzyskuje dostęp do elementów obu tablicach, przy użyciu indeksów zamiast drugiego wskaźników niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="63740-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="63740-110">Deklaracja `pSource` i `pTarget` wskaźniki Przypina tablic.</span><span class="sxs-lookup"><span data-stu-id="63740-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="63740-111">Ta funkcja jest dostępna, począwszy od języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="63740-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="63740-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="63740-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="63740-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="63740-113">See Also</span></span>

- [<span data-ttu-id="63740-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="63740-114">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="63740-115">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="63740-115">Unsafe Code and Pointers</span></span>](index.md)  
- [<span data-ttu-id="63740-116">-unsafe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="63740-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)  
- [<span data-ttu-id="63740-117">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="63740-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
