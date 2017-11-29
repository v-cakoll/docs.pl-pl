---
title: "Operator [] (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
caps.latest.revision: "20"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 03664f5604bb7d7dce9e8ae2ff0ec045c6a203b1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-c-reference"></a><span data-ttu-id="ddbbe-102">Operator [] (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ddbbe-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="ddbbe-103">Nawiasy kwadratowe (`[]`) są używane dla tablic, indeksatorów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="ddbbe-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="ddbbe-104">Mogą one również używane z wskaźniki.</span><span class="sxs-lookup"><span data-stu-id="ddbbe-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="ddbbe-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ddbbe-105">Remarks</span></span>  
 <span data-ttu-id="ddbbe-106">Typ tablicy jest typem następuje `[]`:</span><span class="sxs-lookup"><span data-stu-id="ddbbe-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="ddbbe-107">Aby uzyskać dostęp do elementu tablicy, indeks żądany element jest ujęty w nawiasy:</span><span class="sxs-lookup"><span data-stu-id="ddbbe-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="ddbbe-108">Jeśli indeks tablicy jest poza zakresem, jest zgłaszany wyjątek.</span><span class="sxs-lookup"><span data-stu-id="ddbbe-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="ddbbe-109">Operator indeksowanie tablicy nie może zostać przeciążony; jednak typów można zdefiniować, indeksatorów i właściwości, które przyjmują co najmniej jeden parametr.</span><span class="sxs-lookup"><span data-stu-id="ddbbe-109">The array indexing operator cannot be overloaded; however, types can define indexers, and properties that take one or more parameters.</span></span> <span data-ttu-id="ddbbe-110">Indeksator parametry są ujęte w nawiasy kwadratowe, podobnie jak indeksy tablicy, ale indeksatora parametry mogą być deklarowane jako dowolnego typu, w odróżnieniu od indeksy tablicy, które musi być wartością całkowitą.</span><span class="sxs-lookup"><span data-stu-id="ddbbe-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="ddbbe-111">Na przykład, .NET Framework definiuje `Hashtable` typu, który kojarzy kluczy i wartości dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="ddbbe-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="ddbbe-112">Nawiasy kwadratowe są również używane do określenia [atrybuty](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="ddbbe-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="ddbbe-113">Nawiasy kwadratowe umożliwia indeksu poza wskaźnik:</span><span class="sxs-lookup"><span data-stu-id="ddbbe-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="ddbbe-114">Nie granice sprawdzanie jest wykonywane.</span><span class="sxs-lookup"><span data-stu-id="ddbbe-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ddbbe-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ddbbe-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="ddbbe-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ddbbe-116">See Also</span></span>  
 [<span data-ttu-id="ddbbe-117">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="ddbbe-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ddbbe-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ddbbe-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ddbbe-119">Operatory C#</span><span class="sxs-lookup"><span data-stu-id="ddbbe-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
 [<span data-ttu-id="ddbbe-120">Tablice</span><span class="sxs-lookup"><span data-stu-id="ddbbe-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
 [<span data-ttu-id="ddbbe-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="ddbbe-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
 [<span data-ttu-id="ddbbe-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="ddbbe-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
 [<span data-ttu-id="ddbbe-123">Fixed — instrukcja</span><span class="sxs-lookup"><span data-stu-id="ddbbe-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
