---
title: '* Operator (odwołanie w C#)'
ms.date: 04/04/2018
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- '*_CSharpKeyword'
helpviewer_keywords:
- multiplication operator (*) [C#]
- '* operator [C#]'
ms.assetid: abd9a5f0-9b24-431e-971a-09ee1c45c50e
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 07d06d668ba43ebc3f4fae394d7b6641b122f4a6
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/09/2018
---
# <a name="-operator-c-reference"></a><span data-ttu-id="d9128-102">\* — Operator (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="d9128-102">\* Operator (C# Reference)</span></span>
<span data-ttu-id="d9128-103">Operator mnożenia (`*`) oblicza iloczyn argumentów.</span><span class="sxs-lookup"><span data-stu-id="d9128-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="d9128-104">Wszystkie typy liczbowe ma wstępnie zdefiniowane operatory mnożenia.</span><span class="sxs-lookup"><span data-stu-id="d9128-104">All numeric types have predefined multiplication operators.</span></span>  

<span data-ttu-id="d9128-105">`*` Służy również jako operatora dereference, który umożliwia odczytywanie i zapisywanie do wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="d9128-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>
  
## <a name="remarks"></a><span data-ttu-id="d9128-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="d9128-106">Remarks</span></span>  
 <span data-ttu-id="d9128-107">`*` Operator służy również do deklarować typów wskaźnikowych i usunąć odwołania do wskaźników.</span><span class="sxs-lookup"><span data-stu-id="d9128-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="d9128-108">Ten operator jest możliwe tylko w kontekstach niebezpieczne, oznaczona za pomocą [niebezpieczne](../../../csharp/language-reference/keywords/unsafe.md) — słowo kluczowe i wymagający [/ unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="d9128-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../../../csharp/language-reference/keywords/unsafe.md) keyword, and requiring the [/unsafe](../../../csharp/language-reference/compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="d9128-109">Dereference operator jest nazywana operator pośredni.</span><span class="sxs-lookup"><span data-stu-id="d9128-109">The dereference operator is also known as the indirection operator.</span></span>  
  
 <span data-ttu-id="d9128-110">Typy definiowane przez użytkownika można przeciążać plik binarny `*` — operator (zobacz [operator](../../../csharp/language-reference/keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="d9128-110">User-defined types can overload the binary `*` operator (see [operator](../../../csharp/language-reference/keywords/operator.md)).</span></span> <span data-ttu-id="d9128-111">Jeśli jest przeciążony operator binarny, odpowiedniego operatora przypisania, jeśli taki występuje, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="d9128-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d9128-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9128-112">Example</span></span>  
 [!code-csharp[csRefOperators#50](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_1.cs)]  
  
## <a name="example"></a><span data-ttu-id="d9128-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="d9128-113">Example</span></span>  
 [!code-csharp[csRefOperators#51](../../../csharp/language-reference/operators/codesnippet/CSharp/multiplication-operator_2.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="d9128-114">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="d9128-114">See Also</span></span>  
 [<span data-ttu-id="d9128-115">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="d9128-115">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="d9128-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="d9128-116">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="d9128-117">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="d9128-117">Unsafe Code and Pointers</span></span>](../../../csharp/programming-guide/unsafe-code-pointers/index.md)  
 [<span data-ttu-id="d9128-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="d9128-118">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)
