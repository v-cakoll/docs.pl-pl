---
title: Domena dostępności - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 529d256a553c4000c77bcd5096db1a4d943874ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59141755"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="cb0b5-102">Domena dostępności (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="cb0b5-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="cb0b5-103">Domena dostępności członka Określa, w sekcjach programów, które mogą być przywoływane członka.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="cb0b5-104">Jeśli element członkowski jest zagnieżdżony w ramach innego typu, jego domeny dostępności jest określana przez oba [poziom dostępności](../../../csharp/language-reference/keywords/accessibility-levels.md) członka i domena dostępności typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](../../../csharp/language-reference/keywords/accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="cb0b5-105">Domena dostępności typu najwyższego poziomu jest co najmniej i tekstu programu project, która jest zadeklarowana w.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="cb0b5-106">Oznacza to, że domeny obejmuje wszystkie pliki źródłowe tego projektu.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="cb0b5-107">Domena dostępności typu zagnieżdżonego jest co najmniej tekstem typu, w którym jest zdeklarowana.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="cb0b5-108">Oznacza to, że domena jest treści typu, który obejmuje wszystkie typy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="cb0b5-109">Domena dostępności typu zagnieżdżonego nigdy nie przekracza typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="cb0b5-110">Te pojęcia zostały przedstawione w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="cb0b5-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="cb0b5-111">Example</span></span>  
 <span data-ttu-id="cb0b5-112">Ten przykład zawiera typ najwyższego poziomu, `T1`i dwie klasy zagnieżdżonych, `M1` i `M2`.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="cb0b5-113">Klasy zawierają pola, które mają różne możliwości dostępu do zadeklarowane.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="cb0b5-114">W `Main` metody komentarz poniżej każdej instrukcji, aby wskazać, domena dostępności każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="cb0b5-115">Należy zauważyć, że instrukcje, w których podejmowana jest próba odwołania członkowie niedostępni są ujęte w komentarz. Jeśli chcesz wyświetlić błędy kompilatora spowodowany przez utworzenie odwołań do elementu członkowskiego niedostępny, Usuń komentarze jednego naraz.</span><span class="sxs-lookup"><span data-stu-id="cb0b5-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="cb0b5-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cb0b5-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="cb0b5-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="cb0b5-117">See also</span></span>

- [<span data-ttu-id="cb0b5-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="cb0b5-118">C# Reference</span></span>](../../../csharp/language-reference/index.md)
- [<span data-ttu-id="cb0b5-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="cb0b5-119">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)
- [<span data-ttu-id="cb0b5-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="cb0b5-120">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)
- [<span data-ttu-id="cb0b5-121">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="cb0b5-121">Access Modifiers</span></span>](../../../csharp/language-reference/keywords/access-modifiers.md)
- [<span data-ttu-id="cb0b5-122">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="cb0b5-122">Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/accessibility-levels.md)
- [<span data-ttu-id="cb0b5-123">Ograniczenia dotyczące używania poziomów ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="cb0b5-123">Restrictions on Using Accessibility Levels</span></span>](../../../csharp/language-reference/keywords/restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="cb0b5-124">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="cb0b5-124">Access Modifiers</span></span>](../../../csharp/programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="cb0b5-125">public</span><span class="sxs-lookup"><span data-stu-id="cb0b5-125">public</span></span>](../../../csharp/language-reference/keywords/public.md)
- [<span data-ttu-id="cb0b5-126">private</span><span class="sxs-lookup"><span data-stu-id="cb0b5-126">private</span></span>](../../../csharp/language-reference/keywords/private.md)
- [<span data-ttu-id="cb0b5-127">protected</span><span class="sxs-lookup"><span data-stu-id="cb0b5-127">protected</span></span>](../../../csharp/language-reference/keywords/protected.md)
- [<span data-ttu-id="cb0b5-128">internal</span><span class="sxs-lookup"><span data-stu-id="cb0b5-128">internal</span></span>](../../../csharp/language-reference/keywords/internal.md)
