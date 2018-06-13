---
title: 'Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)'
ms.date: 04/20/2018
helpviewer_keywords:
- byte arrays [C#]
- arrays [C#], byte
- pointers [C#], to copy bytes
ms.openlocfilehash: 800a600f0fa7ca52d0433c8d90039434bf6b7f19
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33331204"
---
# <a name="how-to-use-pointers-to-copy-an-array-of-bytes--c-programming-guide"></a><span data-ttu-id="0258b-102">Porady: użycie wskaźników do kopiowania tablicy bajtów (Przewodnik programowania w języku C#)</span><span class="sxs-lookup"><span data-stu-id="0258b-102">How to: Use Pointers to Copy an Array of Bytes  (C# Programming Guide)</span></span>

<span data-ttu-id="0258b-103">W poniższym przykładzie użyto wskaźników do skopiowania do innej tablicy bajtów.</span><span class="sxs-lookup"><span data-stu-id="0258b-103">The following example uses pointers to copy bytes from one array to another.</span></span>

<span data-ttu-id="0258b-104">W tym przykładzie użyto [niebezpieczne](../../language-reference/keywords/unsafe.md) — słowo kluczowe, co pozwala na użycie wskaźników w `Copy` metody.</span><span class="sxs-lookup"><span data-stu-id="0258b-104">This example uses the [unsafe](../../language-reference/keywords/unsafe.md) keyword, which enables you to use pointers in the `Copy` method.</span></span> <span data-ttu-id="0258b-105">[Stałej](../../language-reference/keywords/fixed-statement.md) instrukcji służy do deklarowania wskaźniki do tablic źródłowym i docelowym.</span><span class="sxs-lookup"><span data-stu-id="0258b-105">The [fixed](../../language-reference/keywords/fixed-statement.md) statement is used to declare pointers to the source and destination arrays.</span></span> <span data-ttu-id="0258b-106">`fixed` Instrukcji *numerów PIN* lokalizacja źródłowa i docelowa stałych w pamięci, dzięki czemu nie będą przenoszone przez wyrzucanie elementów bezużytecznych.</span><span class="sxs-lookup"><span data-stu-id="0258b-106">The `fixed` statement *pins* the location of the source and destination arrays in memory so that they will not be moved by garbage collection.</span></span> <span data-ttu-id="0258b-107">Bloki pamięci dla tablic są odpiąć, gdy `fixed` bloku zostało zakończone.</span><span class="sxs-lookup"><span data-stu-id="0258b-107">The memory blocks for the arrays are unpinned when the `fixed` block is completed.</span></span> <span data-ttu-id="0258b-108">Ponieważ `Copy` używa metody w tym przykładzie `unsafe` — słowo kluczowe, jego musi być kompilowana przy użyciu [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="0258b-108">Because the `Copy` method in this example uses the `unsafe` keyword, it must be compiled with the [-unsafe](../../language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>

<span data-ttu-id="0258b-109">W tym przykładzie uzyskuje dostęp do elementów zarówno tablic przy użyciu indeksów niż drugi niezarządzanego wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="0258b-109">This example accesses the elements of both arrays using indices rather than a second unmanaged pointer.</span></span> <span data-ttu-id="0258b-110">Deklaracja `pSource` i `pTarget` wskaźniki PIN tablic.</span><span class="sxs-lookup"><span data-stu-id="0258b-110">The declaration of the `pSource` and `pTarget` pointers pins the arrays.</span></span> <span data-ttu-id="0258b-111">Ta funkcja jest dostępna, począwszy od 7.3 C#.</span><span class="sxs-lookup"><span data-stu-id="0258b-111">This feature is available starting with C# 7.3.</span></span>

## <a name="example"></a><span data-ttu-id="0258b-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="0258b-112">Example</span></span>

[!code-csharp[Struct with embedded inline array](../../../../samples/snippets/csharp/keywords/FixedKeywordExamples.cs#8)]

## <a name="see-also"></a><span data-ttu-id="0258b-113">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0258b-113">See Also</span></span>
 [<span data-ttu-id="0258b-114">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0258b-114">C# Programming Guide</span></span>](../index.md)  
 [<span data-ttu-id="0258b-115">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="0258b-115">Unsafe Code and Pointers</span></span>](index.md)  
 [<span data-ttu-id="0258b-116">-unsafe (opcje kompilatora C#)</span><span class="sxs-lookup"><span data-stu-id="0258b-116">-unsafe (C# Compiler Options)</span></span>](../../language-reference/compiler-options/unsafe-compiler-option.md)  
 [<span data-ttu-id="0258b-117">Odzyskiwanie pamięci</span><span class="sxs-lookup"><span data-stu-id="0258b-117">Garbage Collection</span></span>](../../../standard/garbage-collection/index.md)  
