---
title: Operator [] — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- '[]_CSharpKeyword'
helpviewer_keywords:
- subscript operator [C#]
- square brackets [ ] operator [C#]
- '[] operator [C#]'
- indexing operator [C#]
ms.assetid: 5c16bb45-88f7-45ff-b42c-1af1972b042c
ms.openlocfilehash: 3e2ce5c4b74cbf79e00410791ffcc31368f78648
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53244006"
---
# <a name="-operator-c-reference"></a><span data-ttu-id="3dc49-102">Operator [] (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="3dc49-102">[] Operator (C# Reference)</span></span>
<span data-ttu-id="3dc49-103">Nawiasy kwadratowe (`[]`) są używane do obsługi tablic, indeksatorów i atrybutów.</span><span class="sxs-lookup"><span data-stu-id="3dc49-103">Square brackets (`[]`) are used for arrays, indexers, and attributes.</span></span> <span data-ttu-id="3dc49-104">Mogą być również używane ze wskaźnikami.</span><span class="sxs-lookup"><span data-stu-id="3dc49-104">They can also be used with pointers.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="3dc49-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="3dc49-105">Remarks</span></span>  
 <span data-ttu-id="3dc49-106">Typ tablicy jest typem następującym po `[]`:</span><span class="sxs-lookup"><span data-stu-id="3dc49-106">An array type is a type followed by `[]`:</span></span>  
  
 [!code-csharp[csRefOperators#43](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_1.cs)]  
  
 <span data-ttu-id="3dc49-107">Aby uzyskać dostęp do elementu tablicy, indeks żądanego elementu musi zostać ujęty w nawiasy kwadratowe:</span><span class="sxs-lookup"><span data-stu-id="3dc49-107">To access an element of an array, the index of the desired element is enclosed in brackets:</span></span>  
  
 [!code-csharp[csRefOperators#44](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_2.cs)]  
  
 <span data-ttu-id="3dc49-108">Wyjątek jest generowany, jeśli indeks tablicy jest poza zakresem.</span><span class="sxs-lookup"><span data-stu-id="3dc49-108">An exception is thrown if an array index is out of range.</span></span>  
  
 <span data-ttu-id="3dc49-109">Tablica indeksowania operator nie może zostać przeciążony; jednak typów można zdefiniować indeksatorów, które przyjmują jeden lub więcej parametrów.</span><span class="sxs-lookup"><span data-stu-id="3dc49-109">The array indexing operator cannot be overloaded; however, types can define indexers that take one or more parameters.</span></span> <span data-ttu-id="3dc49-110">Parametry indeksatora są ujęte w nawiasy kwadratowe, podobnie jak indeksy tablicy, ale parametry indeksatora mogą być deklarowane jako dowolny typ — w odróżnieniu od indeksów tablicy, które muszą być wartością całkowitą.</span><span class="sxs-lookup"><span data-stu-id="3dc49-110">Indexer parameters are enclosed in square brackets, just like array indexes, but indexer parameters can be declared to be of any type, unlike array indexes, which must be integral.</span></span>  
  
 <span data-ttu-id="3dc49-111">Na przykład: .NET Framework definiuje typ `Hashtable`, który kojarzy klucze i wartości dowolnego typu:</span><span class="sxs-lookup"><span data-stu-id="3dc49-111">For example, the .NET Framework defines a `Hashtable` type that associates keys and values of arbitrary type:</span></span>  
  
 [!code-csharp[csRefOperators#45](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_3.cs)]  
  
 <span data-ttu-id="3dc49-112">Nawiasy kwadratowe są również używane do określenia [atrybutów](../../../csharp/programming-guide/concepts/attributes/index.md):</span><span class="sxs-lookup"><span data-stu-id="3dc49-112">Square brackets are also used to specify [Attributes](../../../csharp/programming-guide/concepts/attributes/index.md):</span></span>  
  
 [!code-csharp[csRefOperators#46](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_4.cs)]  
  
 <span data-ttu-id="3dc49-113">Nawiasów kwadratowych można użyć do odindeksowania wskaźnika:</span><span class="sxs-lookup"><span data-stu-id="3dc49-113">You can use square brackets to index off a pointer:</span></span>  
  
 [!code-csharp[csRefOperators#47](../../../csharp/language-reference/operators/codesnippet/CSharp/index-operator_5.cs)]  
  
 <span data-ttu-id="3dc49-114">Nie jest wykonywane sprawdzanie granic.</span><span class="sxs-lookup"><span data-stu-id="3dc49-114">No bounds checking is performed.</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="3dc49-115">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3dc49-115">C# Language Specification</span></span>  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a><span data-ttu-id="3dc49-116">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="3dc49-116">See Also</span></span>

- [<span data-ttu-id="3dc49-117">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="3dc49-117">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
- [<span data-ttu-id="3dc49-118">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="3dc49-118">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
- [<span data-ttu-id="3dc49-119">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="3dc49-119">C# Operators</span></span>](../../../csharp/language-reference/operators/index.md)  
- [<span data-ttu-id="3dc49-120">Tablice</span><span class="sxs-lookup"><span data-stu-id="3dc49-120">Arrays</span></span>](../../../csharp/programming-guide/arrays/index.md)  
- [<span data-ttu-id="3dc49-121">Indeksatory</span><span class="sxs-lookup"><span data-stu-id="3dc49-121">Indexers</span></span>](../../../csharp/programming-guide/indexers/index.md)  
- [<span data-ttu-id="3dc49-122">unsafe</span><span class="sxs-lookup"><span data-stu-id="3dc49-122">unsafe</span></span>](../../../csharp/language-reference/keywords/unsafe.md)  
- [<span data-ttu-id="3dc49-123">fixed, instrukcja</span><span class="sxs-lookup"><span data-stu-id="3dc49-123">fixed Statement</span></span>](../../../csharp/language-reference/keywords/fixed-statement.md)
