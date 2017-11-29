---
title: "struct (odwołanie w C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
caps.latest.revision: "23"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: e8a848d5543291ef335e72cb7806158827e865dd
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="struct-c-reference"></a><span data-ttu-id="ce700-102">struct (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="ce700-102">struct (C# Reference)</span></span>
<span data-ttu-id="ce700-103">A `struct` typem jest typ wartości, która jest zwykle używana w celu hermetyzacji małych grup zmienne pokrewne, takie jak współrzędne prostokąta lub właściwości elementu w magazynie.</span><span class="sxs-lookup"><span data-stu-id="ce700-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="ce700-104">W poniższym przykładzie przedstawiono deklaracji struktury prosty:</span><span class="sxs-lookup"><span data-stu-id="ce700-104">The following example shows a simple struct declaration:</span></span>  
  
```  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="ce700-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="ce700-105">Remarks</span></span>  
 <span data-ttu-id="ce700-106">Struktury mogą również zawierać [konstruktorów](../../../csharp/programming-guide/classes-and-structs/constructors.md), [stałe](../../../csharp/programming-guide/classes-and-structs/constants.md), [pola](../../../csharp/programming-guide/classes-and-structs/fields.md), [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [indeksatory](../../../csharp/programming-guide/indexers/index.md), [operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [zdarzenia](../../../csharp/programming-guide/events/index.md), i [zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md), ale jeśli kilka takich elementów są wymagane, możesz należy rozważyć, co danego typu, klasę zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="ce700-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="ce700-107">Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="ce700-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="ce700-108">Struktury można zaimplementować interfejsu, ale nie może dziedziczyć innego struktury.</span><span class="sxs-lookup"><span data-stu-id="ce700-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="ce700-109">Z tego powodu elementy członkowskie struktury nie można zadeklarować jako `protected`.</span><span class="sxs-lookup"><span data-stu-id="ce700-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="ce700-110">Aby uzyskać więcej informacji, zobacz [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="ce700-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="ce700-111">Przykłady</span><span class="sxs-lookup"><span data-stu-id="ce700-111">Examples</span></span>  
 <span data-ttu-id="ce700-112">Aby uzyskać więcej informacji, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="ce700-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="ce700-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="ce700-113">C# Language Specification</span></span>  
 <span data-ttu-id="ce700-114">Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="ce700-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ce700-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="ce700-115">See Also</span></span>  
 [<span data-ttu-id="ce700-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="ce700-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="ce700-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="ce700-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="ce700-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="ce700-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="ce700-119">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="ce700-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="ce700-120">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="ce700-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="ce700-121">Typy</span><span class="sxs-lookup"><span data-stu-id="ce700-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="ce700-122">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="ce700-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="ce700-123">klasy</span><span class="sxs-lookup"><span data-stu-id="ce700-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="ce700-124">Interfejs</span><span class="sxs-lookup"><span data-stu-id="ce700-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="ce700-125">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="ce700-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
