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
ms.openlocfilehash: f4490c4632d9344eb879ea55c20787b838781d91
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333736"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="976f0-102">\* — operator (C# odwołania)</span><span class="sxs-lookup"><span data-stu-id="976f0-102">\* operator (C# Reference)</span></span>

<span data-ttu-id="976f0-103">Operator mnożenia (`*`) oblicza iloczyn argumentów.</span><span class="sxs-lookup"><span data-stu-id="976f0-103">The multiplication operator (`*`) computes the product of its operands.</span></span> <span data-ttu-id="976f0-104">Wszystkie typy liczbowe zostały wstępnie zdefiniowane operatorów mnożenia.</span><span class="sxs-lookup"><span data-stu-id="976f0-104">All numeric types have predefined multiplication operators.</span></span>

<span data-ttu-id="976f0-105">`*` Służy również jako operator wyłuskania, która umożliwia odczytywanie i zapisywanie do wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="976f0-105">`*` also serves as the dereference operator, which allows reading and writing to a pointer.</span></span>

## <a name="remarks"></a><span data-ttu-id="976f0-106">Uwagi</span><span class="sxs-lookup"><span data-stu-id="976f0-106">Remarks</span></span>

<span data-ttu-id="976f0-107">`*` Operator służy także do deklarowania typów wskaźnika i celu wyłuskania wskaźników.</span><span class="sxs-lookup"><span data-stu-id="976f0-107">The `*` operator is also used to declare pointer types and to dereference pointers.</span></span> <span data-ttu-id="976f0-108">Ten operator należy używać tylko w kontekstach niebezpieczne wskazywane przez użycie [niebezpieczne](../keywords/unsafe.md) — słowo kluczowe która wymaga [/ unsafe](../compiler-options/unsafe-compiler-option.md) — opcja kompilatora.</span><span class="sxs-lookup"><span data-stu-id="976f0-108">This operator can only be used in unsafe contexts, denoted by the use of the [unsafe](../keywords/unsafe.md) keyword, and requiring the [/unsafe](../compiler-options/unsafe-compiler-option.md) compiler option.</span></span>  <span data-ttu-id="976f0-109">Operator wyłuskania jest również nazywany operatora pośredniego.</span><span class="sxs-lookup"><span data-stu-id="976f0-109">The dereference operator is also known as the indirection operator.</span></span>

<span data-ttu-id="976f0-110">Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia pliku binarnego `*` — operator (zobacz [operator](../keywords/operator.md)).</span><span class="sxs-lookup"><span data-stu-id="976f0-110">User-defined types can overload the binary `*` operator (see [operator](../keywords/operator.md)).</span></span> <span data-ttu-id="976f0-111">Gdy jest przeciążony operator binarny, odpowiedniego operatora przypisania, jest również niejawnie przeciążona.</span><span class="sxs-lookup"><span data-stu-id="976f0-111">When a binary operator is overloaded, the corresponding assignment operator, if any, is also implicitly overloaded.</span></span>

## <a name="example"></a><span data-ttu-id="976f0-112">Przykład</span><span class="sxs-lookup"><span data-stu-id="976f0-112">Example</span></span>

[!code-csharp-interactive[csRefOperators#50](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#50)]

## <a name="example"></a><span data-ttu-id="976f0-113">Przykład</span><span class="sxs-lookup"><span data-stu-id="976f0-113">Example</span></span>

[!code-csharp[csRefOperators#51](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#51)]

## <a name="see-also"></a><span data-ttu-id="976f0-114">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="976f0-114">See also</span></span>

- [<span data-ttu-id="976f0-115">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="976f0-115">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="976f0-116">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="976f0-116">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="976f0-117">Niebezpieczny kod i wskaźniki</span><span class="sxs-lookup"><span data-stu-id="976f0-117">Unsafe Code and Pointers</span></span>](../../programming-guide/unsafe-code-pointers/index.md)
- [<span data-ttu-id="976f0-118">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="976f0-118">C# Operators</span></span>](index.md)