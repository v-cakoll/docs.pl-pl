---
title: '* Operator - C# odwołania'
ms.custom: seodec18
ms.date: 04/04/2018
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
ms.openlocfilehash: 24ac4a99c48f1e8204b821bfbf5f7fbc0a2b2f1d
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53237353"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="41205-102">\* — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="41205-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="41205-103">Operator mnożenia (`*`) oblicza iloczyn argumentów.</span><span class="sxs-lookup"><span data-stu-id="41205-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="41205-104">Wszystkie typy liczbowe zostały wstępnie zdefiniowane operatorów mnożenia.</span><span class="sxs-lookup"><span data-stu-id="41205-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="41205-105">`*` Służy również jako operator wyłuskania, która umożliwia odczytywanie i zapisywanie do wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="41205-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="41205-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="41205-106">Remarks</span></span>  
 <span data-ttu-id="41205-107">`*` Operator służy także do deklarowania typów wskaźnika i celu wyłuskania wskaźników.</span><span class="sxs-lookup"><span data-stu-id="41205-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="41205-108">Ten operator należy używać tylko w kontekstach niebezpieczne wskazywane przez użycie [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe która wymaga [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="41205-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="41205-109">Operator wyłuskania jest również nazywany operatora pośredniego.</span><span class="sxs-lookup"><span data-stu-id="41205-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="41205-110">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia pliku binarnego `*` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="41205-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="41205-111">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="41205-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="41205-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="41205-112">Example</span></span>  
 [!code-csharp-interactive[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="41205-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="41205-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="41205-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="41205-114">See Also</span></span>

- [<span data-ttu-id="41205-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="41205-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="41205-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="41205-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="41205-117">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="41205-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
- [<span data-ttu-id="41205-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="41205-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
