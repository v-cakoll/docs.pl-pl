---
title: struct (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: ddea59e76835ccccd07c299f819796336cddada8
ms.sourcegitcommit: 89c93d05c2281b4c834f48f6c8df1047e1410980
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2018
ms.locfileid: "34172152"
---
# <a name="struct-c-reference"></a><span data-ttu-id="5101e-102">struct (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="5101e-102">struct (C# Reference)</span></span>
<span data-ttu-id="5101e-103">A `struct` typem jest typ wartości, która jest zwykle używana w celu hermetyzacji małych grup zmienne pokrewne, takie jak współrzędne prostokąta lub właściwości elementu w magazynie.</span><span class="sxs-lookup"><span data-stu-id="5101e-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="5101e-104">W poniższym przykładzie przedstawiono deklaracji struktury prosty:</span><span class="sxs-lookup"><span data-stu-id="5101e-104">The following example shows a simple struct declaration:</span></span>  
  
```csharp  
public struct Book  
{  
    public decimal price;  
    public string title;  
    public string author;  
}  
```  
  
## <a name="remarks"></a><span data-ttu-id="5101e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="5101e-105">Remarks</span></span>  
 <span data-ttu-id="5101e-106">Struktury mogą również zawierać [konstruktorów](../../../csharp/programming-guide/classes-and-structs/constructors.md), [stałe](../../../csharp/programming-guide/classes-and-structs/constants.md), [pola](../../../csharp/programming-guide/classes-and-structs/fields.md), [metody](../../../csharp/programming-guide/classes-and-structs/methods.md), [właściwości](../../../csharp/programming-guide/classes-and-structs/properties.md), [indeksatory](../../../csharp/programming-guide/indexers/index.md), [operatory](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [zdarzenia](../../../csharp/programming-guide/events/index.md), i [zagnieżdżone typy](../../../csharp/programming-guide/classes-and-structs/nested-types.md), ale jeśli kilka takich elementów są wymagane, możesz należy rozważyć, co danego typu, klasę zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="5101e-106">Structs can also contain [constructors](../../../csharp/programming-guide/classes-and-structs/constructors.md), [constants](../../../csharp/programming-guide/classes-and-structs/constants.md), [fields](../../../csharp/programming-guide/classes-and-structs/fields.md), [methods](../../../csharp/programming-guide/classes-and-structs/methods.md), [properties](../../../csharp/programming-guide/classes-and-structs/properties.md), [indexers](../../../csharp/programming-guide/indexers/index.md), [operators](../../../csharp/programming-guide/statements-expressions-operators/operators.md), [events](../../../csharp/programming-guide/events/index.md), and [nested types](../../../csharp/programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>  
  
 <span data-ttu-id="5101e-107">Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="5101e-107">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
 <span data-ttu-id="5101e-108">Struktury można zaimplementować interfejsu, ale nie może dziedziczyć innego struktury.</span><span class="sxs-lookup"><span data-stu-id="5101e-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="5101e-109">Z tego powodu elementy członkowskie struktury nie można zadeklarować jako `protected`.</span><span class="sxs-lookup"><span data-stu-id="5101e-109">For that reason, struct members cannot be declared as `protected`.</span></span>  
  
 <span data-ttu-id="5101e-110">Aby uzyskać więcej informacji, zobacz [struktury](../../../csharp/programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="5101e-110">For more information, see [Structs](../../../csharp/programming-guide/classes-and-structs/structs.md).</span></span>  
  
## <a name="examples"></a><span data-ttu-id="5101e-111">Przykłady</span><span class="sxs-lookup"><span data-stu-id="5101e-111">Examples</span></span>  
 <span data-ttu-id="5101e-112">Aby uzyskać więcej informacji, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="5101e-112">For examples and more information, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="c-language-specification"></a><span data-ttu-id="5101e-113">Specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5101e-113">C# Language Specification</span></span>  
 <span data-ttu-id="5101e-114">Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="5101e-114">For examples, see [Using Structs](../../../csharp/programming-guide/classes-and-structs/using-structs.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5101e-115">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="5101e-115">See Also</span></span>  
 [<span data-ttu-id="5101e-116">Odwołanie w C#</span><span class="sxs-lookup"><span data-stu-id="5101e-116">C# Reference</span></span>](../../../csharp/language-reference/index.md)  
 [<span data-ttu-id="5101e-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="5101e-117">C# Programming Guide</span></span>](../../../csharp/programming-guide/index.md)  
 [<span data-ttu-id="5101e-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="5101e-118">C# Keywords</span></span>](../../../csharp/language-reference/keywords/index.md)  
 [<span data-ttu-id="5101e-119">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="5101e-119">Default Values Table</span></span>](../../../csharp/language-reference/keywords/default-values-table.md)  
 [<span data-ttu-id="5101e-120">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="5101e-120">Built-In Types Table</span></span>](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [<span data-ttu-id="5101e-121">Typy</span><span class="sxs-lookup"><span data-stu-id="5101e-121">Types</span></span>](../../../csharp/language-reference/keywords/types.md)  
 [<span data-ttu-id="5101e-122">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="5101e-122">Value Types</span></span>](../../../csharp/language-reference/keywords/value-types.md)  
 [<span data-ttu-id="5101e-123">class</span><span class="sxs-lookup"><span data-stu-id="5101e-123">class</span></span>](../../../csharp/language-reference/keywords/class.md)  
 [<span data-ttu-id="5101e-124">interface</span><span class="sxs-lookup"><span data-stu-id="5101e-124">interface</span></span>](../../../csharp/language-reference/keywords/interface.md)  
 [<span data-ttu-id="5101e-125">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="5101e-125">Classes and Structs</span></span>](../../../csharp/programming-guide/classes-and-structs/index.md)
