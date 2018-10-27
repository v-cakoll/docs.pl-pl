---
title: struct (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 46cf0b66a50685a717818fe762ad4f1de36d6156
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50185748"
---
# <a name="struct-c-reference"></a><span data-ttu-id="4143b-102">struct (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="4143b-102">struct (C# Reference)</span></span>

<span data-ttu-id="4143b-103">A `struct` typ jest typem wartości, które jest zazwyczaj używany do hermetyzacji mniejszym grupom powiązanych zmiennych, takich jak współrzędnych prostokąta lub właściwości elementu w magazynie.</span><span class="sxs-lookup"><span data-stu-id="4143b-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="4143b-104">Poniższy przykład przedstawia deklarację prostą strukturą:</span><span class="sxs-lookup"><span data-stu-id="4143b-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="4143b-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="4143b-105">Remarks</span></span>

<span data-ttu-id="4143b-106">Struktury mogą także zawierać [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [stałe](../../programming-guide/classes-and-structs/constants.md), [pola](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [właściwości](../../programming-guide/classes-and-structs/properties.md), [indeksatory](../../programming-guide/indexers/index.md), [operatory](../../programming-guide/statements-expressions-operators/operators.md), [zdarzenia](../../programming-guide/events/index.md), i [zagnieżdżone typy](../../programming-guide/classes-and-structs/nested-types.md), chociaż Jeśli kilka takich elementów członkowskich są wymagane, możesz należy wziąć pod uwagę klasy jako możliwej do typu Twojej zamiast tego.</span><span class="sxs-lookup"><span data-stu-id="4143b-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../../programming-guide/statements-expressions-operators/operators.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="4143b-107">Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="4143b-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="4143b-108">Struktury można zaimplementować interfejs, ale nie może dziedziczyć innej struktury.</span><span class="sxs-lookup"><span data-stu-id="4143b-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="4143b-109">Z tego powodu składowe struktury nie można zadeklarować jako `protected`.</span><span class="sxs-lookup"><span data-stu-id="4143b-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="4143b-110">Aby uzyskać więcej informacji, zobacz [struktury](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="4143b-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="4143b-111">Przykłady</span><span class="sxs-lookup"><span data-stu-id="4143b-111">Examples</span></span>

<span data-ttu-id="4143b-112">Aby uzyskać więcej informacji, zobacz [przy użyciu struktury](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="4143b-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="4143b-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4143b-113">C# language specification</span></span>

<span data-ttu-id="4143b-114">Aby uzyskać przykłady, zobacz [przy użyciu struktury](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="4143b-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4143b-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="4143b-115">See also</span></span>

- [<span data-ttu-id="4143b-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="4143b-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="4143b-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="4143b-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="4143b-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="4143b-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="4143b-119">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="4143b-119">Default Values Table</span></span>](default-values-table.md)
- [<span data-ttu-id="4143b-120">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="4143b-120">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="4143b-121">Typy</span><span class="sxs-lookup"><span data-stu-id="4143b-121">Types</span></span>](types.md)
- [<span data-ttu-id="4143b-122">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="4143b-122">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="4143b-123">class</span><span class="sxs-lookup"><span data-stu-id="4143b-123">class</span></span>](class.md)
- [<span data-ttu-id="4143b-124">interface</span><span class="sxs-lookup"><span data-stu-id="4143b-124">interface</span></span>](interface.md)
- [<span data-ttu-id="4143b-125">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="4143b-125">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)