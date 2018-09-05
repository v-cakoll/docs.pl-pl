---
title: . Operator (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
ms.openlocfilehash: a092c1a916e3dc4bf6d96660c532540945e57554
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/04/2018
ms.locfileid: "43520711"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="c75a4-103">.</span><span class="sxs-lookup"><span data-stu-id="c75a4-103">.</span></span> <span data-ttu-id="c75a4-104">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="c75a4-104">Operator (C# Reference)</span></span>
<span data-ttu-id="c75a4-105">Operator kropki (`.`) służy do uzyskiwania dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="c75a4-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="c75a4-106">Określa on element członkowski typu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="c75a4-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="c75a4-107">Operator kropki umożliwia na przykład dostęp do określonych metod w ramach biblioteki klas .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="c75a4-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="c75a4-108">Na przykład rozważmy następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="c75a4-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="c75a4-109">Zmienna `s` ma dwa elementy członkowskie, `a` i `b`; Aby uzyskać do nich dostęp, użyj operatora kropka:</span><span class="sxs-lookup"><span data-stu-id="c75a4-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="c75a4-110">Kropka (.) jest również używana do formułowania nazw kwalifikowanych określających na przykład przestrzeń nazw lub interfejs, do których należą te nazwy.</span><span class="sxs-lookup"><span data-stu-id="c75a4-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="c75a4-111">Dyrektywa using sprawia, że część kwalifikacji nazwy jest opcjonalna:</span><span class="sxs-lookup"><span data-stu-id="c75a4-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="c75a4-112">Jednak gdy identyfikator jest niejednoznaczny, kwalifikacja nazwy jest wymagana:</span><span class="sxs-lookup"><span data-stu-id="c75a4-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="c75a4-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c75a4-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="c75a4-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="c75a4-114">See Also</span></span>

- [<span data-ttu-id="c75a4-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="c75a4-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="c75a4-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="c75a4-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="c75a4-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="c75a4-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
