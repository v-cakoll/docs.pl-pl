---
title: . Operator - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: a59f69d0349a054c8c2a5b701b8f63df113a6580
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333723"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="f87b3-103">.</span><span class="sxs-lookup"><span data-stu-id="f87b3-103">.</span></span> <span data-ttu-id="f87b3-104">operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="f87b3-104">operator (C# Reference)</span></span>

<span data-ttu-id="f87b3-105">Operator kropki (`.`) służy do uzyskiwania dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="f87b3-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="f87b3-106">Określa on element członkowski typu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="f87b3-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="f87b3-107">Operator kropki umożliwia na przykład dostęp do określonych metod w ramach biblioteki klas .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="f87b3-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>

[!code-csharp[csRefOperators#16](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#16)]

<span data-ttu-id="f87b3-108">Na przykład rozważmy następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="f87b3-108">For example, consider the following class:</span></span>

[!code-csharp[csRefOperators#17](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#17)]

[!code-csharp[csRefOperators#18](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#18)]

<span data-ttu-id="f87b3-109">Zmienna `s` ma dwa elementy członkowskie, `a` i `b`; Aby uzyskać do nich dostęp, użyj operatora kropka:</span><span class="sxs-lookup"><span data-stu-id="f87b3-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>

[!code-csharp[csRefOperators#19](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#19)]

<span data-ttu-id="f87b3-110">Kropka (.) jest również używana do formułowania nazw kwalifikowanych określających na przykład przestrzeń nazw lub interfejs, do których należą te nazwy.</span><span class="sxs-lookup"><span data-stu-id="f87b3-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>

[!code-csharp[csRefOperators#20](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#20)]

<span data-ttu-id="f87b3-111">Dyrektywa using sprawia, że część kwalifikacji nazwy jest opcjonalna:</span><span class="sxs-lookup"><span data-stu-id="f87b3-111">The using directive makes some name qualification optional:</span></span>

[!code-csharp[csRefOperators#21](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#21)]

<span data-ttu-id="f87b3-112">Jednak gdy identyfikator jest niejednoznaczny, kwalifikacja nazwy jest wymagana:</span><span class="sxs-lookup"><span data-stu-id="f87b3-112">But when an identifier is ambiguous, it must be qualified:</span></span>

[!code-csharp[csRefOperators#22](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#22)]

## <a name="c-language-specification"></a><span data-ttu-id="f87b3-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f87b3-113">C# language specification</span></span>

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a><span data-ttu-id="f87b3-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="f87b3-114">See also</span></span>

- [<span data-ttu-id="f87b3-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f87b3-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="f87b3-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="f87b3-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="f87b3-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="f87b3-117">C# Operators</span></span>](index.md)