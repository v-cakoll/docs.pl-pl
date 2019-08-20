---
title: C# Informacje o domenie dostępności
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 814aa8d3965674abe8bdb60b738cbeff93701ceb
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69606139"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="e8f13-102">Domena dostępności (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="e8f13-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="e8f13-103">Domena dostępności elementu członkowskiego określa, w którym sekcji programu można odwoływać się do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e8f13-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="e8f13-104">Jeśli element członkowski jest zagnieżdżony w innym typie, jego domena dostępności jest określana przez zarówno [poziom dostępności](./accessibility-levels.md) elementu członkowskiego, jak i domenę dostępności typu natychmiastowego.</span><span class="sxs-lookup"><span data-stu-id="e8f13-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="e8f13-105">Domena dostępności typu najwyższego poziomu jest co najmniej tekstem programu w projekcie, w którym jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="e8f13-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="e8f13-106">Oznacza to, że domena zawiera wszystkie pliki źródłowe tego projektu.</span><span class="sxs-lookup"><span data-stu-id="e8f13-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="e8f13-107">Domena dostępności typu zagnieżdżonego jest co najmniej tekstem programu typu, w którym jest zadeklarowana.</span><span class="sxs-lookup"><span data-stu-id="e8f13-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="e8f13-108">Oznacza to, że domena jest treścią typu, która obejmuje wszystkie typy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="e8f13-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="e8f13-109">Domena dostępności typu zagnieżdżonego nigdy nie przekracza typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="e8f13-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="e8f13-110">Te koncepcje przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="e8f13-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f13-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="e8f13-111">Example</span></span>  
 <span data-ttu-id="e8f13-112">Ten przykład zawiera typ najwyższego poziomu, `T1`i dwie `M1` klasy zagnieżdżone i `M2`.</span><span class="sxs-lookup"><span data-stu-id="e8f13-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="e8f13-113">Klasy zawierają pola, które mają inne zadeklarowane podano.</span><span class="sxs-lookup"><span data-stu-id="e8f13-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="e8f13-114">`Main` W metodzie komentarz jest zgodny z każdą instrukcją, aby wskazać domenę dostępności każdego elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="e8f13-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="e8f13-115">Zwróć uwagę, że instrukcje, które próbują odwołać się do niedostępnych elementów członkowskich, są oznaczone jako komentarz. Jeśli chcesz zobaczyć błędy kompilatora spowodowane odwołaniem do niedostępnego elementu członkowskiego, Usuń Komentarze pojedynczo.</span><span class="sxs-lookup"><span data-stu-id="e8f13-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="e8f13-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e8f13-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="e8f13-117">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="e8f13-117">See also</span></span>

- [<span data-ttu-id="e8f13-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="e8f13-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="e8f13-119">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="e8f13-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="e8f13-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="e8f13-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="e8f13-121">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="e8f13-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="e8f13-122">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="e8f13-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="e8f13-123">Ograniczenia dotyczące używania poziomów ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="e8f13-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="e8f13-124">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="e8f13-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="e8f13-125">public</span><span class="sxs-lookup"><span data-stu-id="e8f13-125">public</span></span>](./public.md)
- [<span data-ttu-id="e8f13-126">private</span><span class="sxs-lookup"><span data-stu-id="e8f13-126">private</span></span>](./private.md)
- [<span data-ttu-id="e8f13-127">protected</span><span class="sxs-lookup"><span data-stu-id="e8f13-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="e8f13-128">internal</span><span class="sxs-lookup"><span data-stu-id="e8f13-128">internal</span></span>](./internal.md)
