---
title: 'Instrukcje: Użycie wskaźników do kopiowania tablicy bajtów - C# przewodnik programowania'
ms.custom: seodec18
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 49151c6d2a573a24e63f733a5279faeee40de1b7
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53241129"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="1f1b4-102">Instrukcje: Użycie wskaźników do kopiowania tablicy bajtów (C# Programming Guide)</span><span class="sxs-lookup"><span data-stu-id="1f1b4-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="1f1b4-103">W poniższym przykładzie użyto wskaźników do skopiowania do innej tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="1f1b4-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="1f1b4-104">W tym przykładzie użyto [niebezpieczne](../../language-reference/keywords/unsafe.md) — słowo kluczowe, co pozwala na użycie wskaźników w `Copy` metody.</span><span class="sxs-lookup"><span data-stu-id="1f1b4-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="1f1b4-105">[Stałej](../../language-reference/keywords/fixed-statement.md) instrukcja jest używane do deklarowania wskaźniki do tablic źródłowym i docelowym.</span><span class="sxs-lookup"><span data-stu-id="1f1b4-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="1f1b4-106">`fixed` Instrukcji *numerów PIN* lokalizacji źródłowych i docelowych Indeksy tablic w pamięci, dzięki czemu nie będą przenoszone przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="1f1b4-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="1f1b4-107">Bloki pamięci dla tablic, są odpięte, gdy `fixed` blok zostanie ukończona.</span><span class="sxs-lookup"><span data-stu-id="1f1b4-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="1f1b4-108">Ponieważ `Copy` korzysta z metody w tym przykładzie `unsafe` — słowo kluczowe, jego musi być skompilowana przy użyciu [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="1f1b4-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="1f1b4-109">Ten przykład uzyskuje dostęp do elementów obu tablicach, przy użyciu indeksów zamiast drugiego wskaźników niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="1f1b4-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="1f1b4-110">Deklaracja `pSource` i `pTarget` wskaźniki Przypina tablic.</span><span class="sxs-lookup"><span data-stu-id="1f1b4-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="1f1b4-111">Ta funkcja jest dostępna, począwszy od języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="1f1b4-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="1f1b4-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="1f1b4-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="1f1b4-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1f1b4-113">See Also</span></span>

- [<span data-ttu-id="1f1b4-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="1f1b4-114">C# Programming Guide</span></span>](../index.md)  
- [<span data-ttu-id="1f1b4-115">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="1f1b4-115">Unsafe Code and Pointers</span></span>](index.md)  
- [<span data-ttu-id="1f1b4-116">-unsafe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="1f1b4-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)  
- [<span data-ttu-id="1f1b4-117">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="1f1b4-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
