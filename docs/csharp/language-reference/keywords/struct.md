---
title: struct- C# Reference
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: 74e9909fda83c781b5a15727f79ff755e7682b0f
ms.sourcegitcommit: c01c18755bb7b0f82c7232314ccf7955ea7834db
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/15/2020
ms.locfileid: "75963121"
---
# <a name="struct-c-reference"></a><span data-ttu-id="6a48e-102">struct (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="6a48e-102">struct (C# Reference)</span></span>

<span data-ttu-id="6a48e-103">Typ `struct` jest typem wartości, który zwykle jest używany do hermetyzowania małych grup powiązanych zmiennych, takich jak współrzędne prostokąta lub Charakterystyka elementu w spisie.</span><span class="sxs-lookup"><span data-stu-id="6a48e-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="6a48e-104">Poniższy przykład pokazuje prostą deklarację struktury:</span><span class="sxs-lookup"><span data-stu-id="6a48e-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="6a48e-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="6a48e-105">Remarks</span></span>

<span data-ttu-id="6a48e-106">Struktury mogą również zawierać [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [stałe](../../programming-guide/classes-and-structs/constants.md), [pola](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [Właściwości](../../programming-guide/classes-and-structs/properties.md), [indeksatory](../../programming-guide/indexers/index.md), [Operatory](../operators/index.md), [zdarzenia](../../programming-guide/events/index.md)i [typy zagnieżdżone](../../programming-guide/classes-and-structs/nested-types.md), chociaż jeśli jest wymagana kilka takich elementów członkowskich, należy rozważyć przeprowadzenie klasy w zamian.</span><span class="sxs-lookup"><span data-stu-id="6a48e-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../operators/index.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="6a48e-107">Aby zapoznać się z przykładami, zobacz [using structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="6a48e-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="6a48e-108">Struktury mogą implementować interfejs, ale nie mogą dziedziczyć z innej struktury.</span><span class="sxs-lookup"><span data-stu-id="6a48e-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="6a48e-109">Z tego powodu elementy członkowskie struktury nie mogą być deklarowane jako `protected`.</span><span class="sxs-lookup"><span data-stu-id="6a48e-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="6a48e-110">Aby uzyskać więcej informacji, zobacz [struktury](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="6a48e-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="6a48e-111">Przykłady</span><span class="sxs-lookup"><span data-stu-id="6a48e-111">Examples</span></span>

<span data-ttu-id="6a48e-112">Aby uzyskać przykłady i więcej informacji, zobacz [using struktury](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="6a48e-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6a48e-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6a48e-113">C# language specification</span></span>

<span data-ttu-id="6a48e-114">Aby zapoznać się z przykładami, zobacz [using structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="6a48e-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a48e-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a48e-115">See also</span></span>

- [<span data-ttu-id="6a48e-116">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6a48e-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="6a48e-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="6a48e-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="6a48e-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="6a48e-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="6a48e-119">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="6a48e-119">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="6a48e-120">Typy</span><span class="sxs-lookup"><span data-stu-id="6a48e-120">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="6a48e-121">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="6a48e-121">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="6a48e-122">class</span><span class="sxs-lookup"><span data-stu-id="6a48e-122">class</span></span>](class.md)
- [<span data-ttu-id="6a48e-123">interface</span><span class="sxs-lookup"><span data-stu-id="6a48e-123">interface</span></span>](interface.md)
- [<span data-ttu-id="6a48e-124">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="6a48e-124">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)
