---
title: . Operator (odwołanie w C#)
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ._CSharpKeyword
helpviewer_keywords:
- member access operator (.) [C#]
- . operator [C#]
- dot operator (.) [C#]
ms.assetid: a1f54b52-b686-4ae5-a48e-a2a9ebd0eb7b
caps.latest.revision: 21
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2bb636bc110f57ace9a824a43afdd86246ed0a5c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="0f665-103">.</span><span class="sxs-lookup"><span data-stu-id="0f665-103">.</span></span> <span data-ttu-id="0f665-104">Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="0f665-104">Operator (C# Reference)</span></span>
<span data-ttu-id="0f665-105">Operator kropki (`.`) służy do dostępu do elementu członkowskiego.</span><span class="sxs-lookup"><span data-stu-id="0f665-105">The dot operator (`.`) is used for member access.</span></span> <span data-ttu-id="0f665-106">Operator kropki określa członkiem typu lub przestrzeni nazw.</span><span class="sxs-lookup"><span data-stu-id="0f665-106">The dot operator specifies a member of a type or namespace.</span></span> <span data-ttu-id="0f665-107">Na przykład operator kropki umożliwia dostęp do określonych metod w ramach biblioteki klas .NET Framework:</span><span class="sxs-lookup"><span data-stu-id="0f665-107">For example, the dot operator is used to access specific methods within the .NET Framework class libraries:</span></span>  
  
 [!code-csharp[csRefOperators#16](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_1.cs)]  
  
 <span data-ttu-id="0f665-108">Rozważmy na przykład następującej klasy:</span><span class="sxs-lookup"><span data-stu-id="0f665-108">For example, consider the following class:</span></span>  
  
 [!code-csharp[csRefOperators#17](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_2.cs)]  
  
 [!code-csharp[csRefOperators#18](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_3.cs)]  
  
 <span data-ttu-id="0f665-109">Zmienna `s` ma dwa elementy członkowskie, `a` i `b`; aby uzyskiwać do nich dostęp, użyj operatora kropki:</span><span class="sxs-lookup"><span data-stu-id="0f665-109">The variable `s` has two members, `a` and `b`; to access them, use the dot operator:</span></span>  
  
 [!code-csharp[csRefOperators#19](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_4.cs)]  
  
 <span data-ttu-id="0f665-110">Kropki (.) jest również używane do utworzenia nazwy kwalifikowanej, które są nazwy określające przestrzeni nazw lub interfejsu, na przykład, do którego należą.</span><span class="sxs-lookup"><span data-stu-id="0f665-110">The dot is also used to form qualified names, which are names that specify the namespace or interface, for example, to which they belong.</span></span>  
  
 [!code-csharp[csRefOperators#20](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_5.cs)]  
  
 <span data-ttu-id="0f665-111">Użycie dyrektywy sprawia, że niektóre kwantyfikacja nazwy są opcjonalne:</span><span class="sxs-lookup"><span data-stu-id="0f665-111">The using directive makes some name qualification optional:</span></span>  
  
 [!code-csharp[csRefOperators#21](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_6.cs)]  
  
 <span data-ttu-id="0f665-112">Jednak gdy identyfikator jest niejednoznaczny, musi być kwalifikowana:</span><span class="sxs-lookup"><span data-stu-id="0f665-112">But when an identifier is ambiguous, it must be qualified:</span></span>  
  
 [!code-csharp[csRefOperators#22](../../../csharp/language-reference/operators/codesnippet/CSharp/member-access-operator_7.cs)]  
  
## <a name="c-language-specification"></a><span data-ttu-id="0f665-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="0f665-113">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="0f665-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="0f665-114">See Also</span></span>  
 [<span data-ttu-id="0f665-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="0f665-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="0f665-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="0f665-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="0f665-117">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="0f665-117">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
