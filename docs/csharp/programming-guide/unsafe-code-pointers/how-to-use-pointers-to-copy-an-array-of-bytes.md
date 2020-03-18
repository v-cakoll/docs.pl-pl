---
title: Jak używać wskaźników do kopiowania tablicy bajtów - Przewodnik programowania C#
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 4929699c2d1e07b16d4694cff79f9b1394b1de38
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75698459"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes-c-programming-guide"></a><span data-ttu-id="23be0-102">Jak używać wskaźników do kopiowania tablicy bajtów (Przewodnik programowania C#)</span><span class="sxs-lookup"><span data-stu-id="23be0-102">How to use pointers to copy an array of bytes (C# Programming Guide)</span></span>

<span data-ttu-id="23be0-103">W poniższym przykładzie użyto wskaźników do kopiowania bajtów z jednej tablicy do drugiej.</span><span class="sxs-lookup"><span data-stu-id="23be0-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="23be0-104">W tym przykładzie użyto [niebezpiecznego](../../language-reference/keywords/unsafe.md) słowa kluczowego, które umożliwia użycie wskaźników w metodzie. `Copy`</span><span class="sxs-lookup"><span data-stu-id="23be0-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="23be0-105">[Stała](../../language-reference/keywords/fixed-statement.md) instrukcja służy do deklarowania wskaźników do tablic źródłowych i docelowych.</span><span class="sxs-lookup"><span data-stu-id="23be0-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="23be0-106">Instrukcja `fixed` *przypina* lokalizację tablic źródłowych i docelowych w pamięci, dzięki czemu nie zostaną one przeniesione przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="23be0-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="23be0-107">Bloki pamięci dla tablic są odpięte po zakończeniu `fixed` bloku.</span><span class="sxs-lookup"><span data-stu-id="23be0-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="23be0-108">Ponieważ `Copy` metoda w tym `unsafe` przykładzie używa słowa kluczowego, musi być skompilowany z [opcją -niebezpieczne](../../language-reference/compiler-options/unsafe-compiler-option.md) kompilatora.</span><span class="sxs-lookup"><span data-stu-id="23be0-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="23be0-109">W tym przykładzie uzyskuje dostęp do elementów obu tablic przy użyciu indeksów, a nie drugi wskaźnik niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="23be0-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="23be0-110">Deklaracja `pSource` i `pTarget` wskaźniki przypina tablice.</span><span class="sxs-lookup"><span data-stu-id="23be0-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="23be0-111">Ta funkcja jest dostępna od języka C# 7.3.</span><span class="sxs-lookup"><span data-stu-id="23be0-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="23be0-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="23be0-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="23be0-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="23be0-113">See also</span></span>

- [<span data-ttu-id="23be0-114">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="23be0-114">C# Programming Guide</span></span>](../index.md)
- [<span data-ttu-id="23be0-115">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="23be0-115">Unsafe Code and Pointers</span></span>](index.md)
- [<span data-ttu-id="23be0-116">-niebezpieczne (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="23be0-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)
- [<span data-ttu-id="23be0-117">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="23be0-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)
