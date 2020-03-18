---
title: Domena ułatwień dostępu — odwołanie do języka C#
ms.date: 07/20/2015
helpviewer_keywords:
- accessibility domain [C#]
ms.assetid: 8af779c1-275b-44be-a864-9edfbca71bcc
ms.openlocfilehash: 4a4319b03f3e0d7f9ec721e611b78c124a8a8ee5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713834"
---
# <a name="accessibility-domain-c-reference"></a><span data-ttu-id="856f6-102">Domena dostępności (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="856f6-102">Accessibility Domain (C# Reference)</span></span>
<span data-ttu-id="856f6-103">Domena ułatwień dostępu członka określa, do których sekcji programu można odwoływać się do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="856f6-103">The accessibility domain of a member specifies in which program sections a member can be referenced.</span></span> <span data-ttu-id="856f6-104">Jeśli element członkowski jest zagnieżdżony w innym typie, jego domena ułatwień dostępu jest określana zarówno przez [poziom ułatwień dostępu](./accessibility-levels.md) elementu członkowskiego, jak i domenę ułatwień dostępu typu bezpośrednio zawierającego.</span><span class="sxs-lookup"><span data-stu-id="856f6-104">If the member is nested within another type, its accessibility domain is determined by both the [accessibility level](./accessibility-levels.md) of the member and the accessibility domain of the immediately containing type.</span></span>  
  
 <span data-ttu-id="856f6-105">Domeną ułatwień dostępu typu najwyższego poziomu jest co najmniej tekst programu projektu, w który jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="856f6-105">The accessibility domain of a top-level type is at least the program text of the project that it is declared in.</span></span> <span data-ttu-id="856f6-106">Oznacza to, że domena zawiera wszystkie pliki źródłowe tego projektu.</span><span class="sxs-lookup"><span data-stu-id="856f6-106">That is, the domain includes all of the source files of this project.</span></span> <span data-ttu-id="856f6-107">Domeną ułatwień dostępu typu zagnieżdżonego jest co najmniej tekst programu typu, w którym jest zadeklarowany.</span><span class="sxs-lookup"><span data-stu-id="856f6-107">The accessibility domain of a nested type is at least the program text of the type in which it is declared.</span></span> <span data-ttu-id="856f6-108">Oznacza to, że domena jest treścią typu, która zawiera wszystkie typy zagnieżdżone.</span><span class="sxs-lookup"><span data-stu-id="856f6-108">That is, the domain is the type body, which includes all nested types.</span></span> <span data-ttu-id="856f6-109">Domena ułatwień dostępu typu zagnieżdżonego nigdy nie przekracza domeny typu zawierającego.</span><span class="sxs-lookup"><span data-stu-id="856f6-109">The accessibility domain of a nested type never exceeds that of the containing type.</span></span> <span data-ttu-id="856f6-110">Pojęcia te przedstawiono w poniższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="856f6-110">These concepts are demonstrated in the following example.</span></span>  
  
## <a name="example"></a><span data-ttu-id="856f6-111">Przykład</span><span class="sxs-lookup"><span data-stu-id="856f6-111">Example</span></span>  
 <span data-ttu-id="856f6-112">W tym przykładzie zawiera typ `T1`najwyższego poziomu i `M1` `M2`dwie klasy zagnieżdżone i .</span><span class="sxs-lookup"><span data-stu-id="856f6-112">This example contains a top-level type, `T1`, and two nested classes, `M1` and `M2`.</span></span> <span data-ttu-id="856f6-113">Klasy zawierają pola, które mają różne zadeklarowane accessibilities.</span><span class="sxs-lookup"><span data-stu-id="856f6-113">The classes contain fields that have different declared accessibilities.</span></span> <span data-ttu-id="856f6-114">W `Main` metodzie komentarz następuje każdej instrukcji, aby wskazać domeny ułatwień dostępu każdego członka.</span><span class="sxs-lookup"><span data-stu-id="856f6-114">In the `Main` method, a comment follows each statement to indicate the accessibility domain of each member.</span></span> <span data-ttu-id="856f6-115">Należy zauważyć, że instrukcje, które próbują odwoływać się do niedostępnych członków są komentowane. Jeśli chcesz zobaczyć błędy kompilatora spowodowane odwołaniem się do niedostępnego elementu członkowskiego, usuń komentarze po jednym naraz.</span><span class="sxs-lookup"><span data-stu-id="856f6-115">Notice that the statements that try to reference the inaccessible members are commented out. If you want to see the compiler errors caused by referencing an inaccessible member, remove the comments one at a time.</span></span>  
  
[!code-csharp[csrefKeywordsModifiers#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsModifiers/CS/csrefKeywordsModifiers.cs#4)]
  
## <a name="c-language-specification"></a><span data-ttu-id="856f6-116">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="856f6-116">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="856f6-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="856f6-117">See also</span></span>

- [<span data-ttu-id="856f6-118">Odwołanie do języka C#</span><span class="sxs-lookup"><span data-stu-id="856f6-118">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="856f6-119">Przewodnik programowania języka C#</span><span class="sxs-lookup"><span data-stu-id="856f6-119">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="856f6-120">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="856f6-120">C# Keywords</span></span>](./index.md)
- [<span data-ttu-id="856f6-121">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="856f6-121">Access Modifiers</span></span>](./access-modifiers.md)
- [<span data-ttu-id="856f6-122">Poziomy ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="856f6-122">Accessibility Levels</span></span>](./accessibility-levels.md)
- [<span data-ttu-id="856f6-123">Ograniczenia dotyczące używania poziomów ułatwień dostępu</span><span class="sxs-lookup"><span data-stu-id="856f6-123">Restrictions on Using Accessibility Levels</span></span>](./restrictions-on-using-accessibility-levels.md)
- [<span data-ttu-id="856f6-124">Modyfikatory dostępu</span><span class="sxs-lookup"><span data-stu-id="856f6-124">Access Modifiers</span></span>](../../programming-guide/classes-and-structs/access-modifiers.md)
- [<span data-ttu-id="856f6-125">Publicznego</span><span class="sxs-lookup"><span data-stu-id="856f6-125">public</span></span>](./public.md)
- [<span data-ttu-id="856f6-126">Prywatny</span><span class="sxs-lookup"><span data-stu-id="856f6-126">private</span></span>](./private.md)
- [<span data-ttu-id="856f6-127">protected</span><span class="sxs-lookup"><span data-stu-id="856f6-127">protected</span></span>](./protected.md)
- [<span data-ttu-id="856f6-128">Wewnętrznego</span><span class="sxs-lookup"><span data-stu-id="856f6-128">internal</span></span>](./internal.md)
