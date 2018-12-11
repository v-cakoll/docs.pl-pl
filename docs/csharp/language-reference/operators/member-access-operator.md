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
ms.openlocfilehash: f5048761973e10bec9650469383e2f52cee74da4
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235049"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="01383-103">.</span><span class="sxs-lookup"><span data-stu-id="01383-103">.</span></span> <span data-ttu-id="01383-104">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="01383-104">Operator (C# Reference)</span></span>
<span data-ttu-id="01383-105">Operator kropki (`.`) służy do uzyskiwania dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="01383-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="01383-106">Określa on element członkowski typu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="01383-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="01383-107">Operator kropki umożliwia na przykład dostęp do określonych metod w ramach biblioteki klas .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="01383-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="01383-108">Na przykład rozważmy następujące klasy:</span><span class="sxs-lookup"><span data-stu-id="01383-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="01383-109">Zmienna `s` ma dwa elementy członkowskie, `a` i `b`; Aby uzyskać do nich dostęp, użyj operatora kropka:</span><span class="sxs-lookup"><span data-stu-id="01383-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="01383-110">Kropka (.) jest również używana do formułowania nazw kwalifikowanych określających na przykład przestrzeń nazw lub interfejs, do których należą te nazwy.</span><span class="sxs-lookup"><span data-stu-id="01383-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="01383-111">Dyrektywa using sprawia, że część kwalifikacji nazwy jest opcjonalna:</span><span class="sxs-lookup"><span data-stu-id="01383-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="01383-112">Jednak gdy identyfikator jest niejednoznaczny, kwalifikacja nazwy jest wymagana:</span><span class="sxs-lookup"><span data-stu-id="01383-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="01383-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="01383-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="01383-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="01383-114">See Also</span></span>

- [<span data-ttu-id="01383-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="01383-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="01383-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="01383-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="01383-117">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="01383-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
