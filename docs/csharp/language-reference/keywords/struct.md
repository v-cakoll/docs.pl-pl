---
title: struct- C# Reference
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- struct_CSharpKeyword
helpviewer_keywords:
- struct keyword [C#]
- structs [C#], struct keyword
ms.assetid: ff3dd9b7-dc93-4720-8855-ef5558f65c7c
ms.openlocfilehash: a78488ad902b0a96a30ad197b0ece043543c3d69
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/01/2019
ms.locfileid: "73422313"
---
# <a name="struct-c-reference"></a><span data-ttu-id="367ed-102">struct (odwołanie w C#)</span><span class="sxs-lookup"><span data-stu-id="367ed-102">struct (C# Reference)</span></span>

<span data-ttu-id="367ed-103">Typ `struct` jest typem wartości, który zwykle jest używany do hermetyzowania małych grup powiązanych zmiennych, takich jak współrzędne prostokąta lub Charakterystyka elementu w spisie.</span><span class="sxs-lookup"><span data-stu-id="367ed-103">A `struct` type is a value type that is typically used to encapsulate small groups of related variables, such as the coordinates of a rectangle or the characteristics of an item in an inventory.</span></span> <span data-ttu-id="367ed-104">Poniższy przykład pokazuje prostą deklarację struktury:</span><span class="sxs-lookup"><span data-stu-id="367ed-104">The following example shows a simple struct declaration:</span></span>

```csharp
public struct Book
{
    public decimal price;
    public string title;
    public string author;
}
```

## <a name="remarks"></a><span data-ttu-id="367ed-105">Uwagi</span><span class="sxs-lookup"><span data-stu-id="367ed-105">Remarks</span></span>

<span data-ttu-id="367ed-106">Struktury mogą również zawierać [konstruktory](../../programming-guide/classes-and-structs/constructors.md), [stałe](../../programming-guide/classes-and-structs/constants.md), [pola](../../programming-guide/classes-and-structs/fields.md), [metody](../../programming-guide/classes-and-structs/methods.md), [Właściwości](../../programming-guide/classes-and-structs/properties.md), [indeksatory](../../programming-guide/indexers/index.md), [Operatory](../operators/index.md), [zdarzenia](../../programming-guide/events/index.md)i [typy zagnieżdżone](../../programming-guide/classes-and-structs/nested-types.md), chociaż w przypadku wielu takich członków wymagane, należy rozważyć przeprowadzenie klasy w zamian.</span><span class="sxs-lookup"><span data-stu-id="367ed-106">Structs can also contain [constructors](../../programming-guide/classes-and-structs/constructors.md), [constants](../../programming-guide/classes-and-structs/constants.md), [fields](../../programming-guide/classes-and-structs/fields.md), [methods](../../programming-guide/classes-and-structs/methods.md), [properties](../../programming-guide/classes-and-structs/properties.md), [indexers](../../programming-guide/indexers/index.md), [operators](../operators/index.md), [events](../../programming-guide/events/index.md), and [nested types](../../programming-guide/classes-and-structs/nested-types.md), although if several such members are required, you should consider making your type a class instead.</span></span>

<span data-ttu-id="367ed-107">Aby zapoznać się z przykładami, zobacz [using structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="367ed-107">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

<span data-ttu-id="367ed-108">Struktury mogą implementować interfejs, ale nie mogą dziedziczyć z innej struktury.</span><span class="sxs-lookup"><span data-stu-id="367ed-108">Structs can implement an interface but they cannot inherit from another struct.</span></span> <span data-ttu-id="367ed-109">Z tego powodu elementy członkowskie struktury nie mogą być deklarowane jako `protected`.</span><span class="sxs-lookup"><span data-stu-id="367ed-109">For that reason, struct members cannot be declared as `protected`.</span></span>

<span data-ttu-id="367ed-110">Aby uzyskać więcej informacji, zobacz [struktury](../../programming-guide/classes-and-structs/structs.md).</span><span class="sxs-lookup"><span data-stu-id="367ed-110">For more information, see [Structs](../../programming-guide/classes-and-structs/structs.md).</span></span>

## <a name="examples"></a><span data-ttu-id="367ed-111">Przykłady</span><span class="sxs-lookup"><span data-stu-id="367ed-111">Examples</span></span>

<span data-ttu-id="367ed-112">Aby uzyskać przykłady i więcej informacji, zobacz [using struktury](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="367ed-112">For examples and more information, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="367ed-113">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="367ed-113">C# language specification</span></span>

<span data-ttu-id="367ed-114">Aby zapoznać się z przykładami, zobacz [using structs](../../programming-guide/classes-and-structs/using-structs.md).</span><span class="sxs-lookup"><span data-stu-id="367ed-114">For examples, see [Using Structs](../../programming-guide/classes-and-structs/using-structs.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="367ed-115">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="367ed-115">See also</span></span>

- [<span data-ttu-id="367ed-116">C#Odwoła</span><span class="sxs-lookup"><span data-stu-id="367ed-116">C# Reference</span></span>](../index.md)
- [<span data-ttu-id="367ed-117">Przewodnik programowania w języku C#</span><span class="sxs-lookup"><span data-stu-id="367ed-117">C# Programming Guide</span></span>](../../programming-guide/index.md)
- [<span data-ttu-id="367ed-118">Słowa kluczowe języka C#</span><span class="sxs-lookup"><span data-stu-id="367ed-118">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="367ed-119">Tabela wartości domyślnych</span><span class="sxs-lookup"><span data-stu-id="367ed-119">Default Values Table</span></span>](default-values-table.md)
- [<span data-ttu-id="367ed-120">Tabela typów wbudowanych</span><span class="sxs-lookup"><span data-stu-id="367ed-120">Built-In Types Table</span></span>](built-in-types-table.md)
- [<span data-ttu-id="367ed-121">Typy</span><span class="sxs-lookup"><span data-stu-id="367ed-121">Types</span></span>](/dotnet/csharp/language-reference/keywords)
- [<span data-ttu-id="367ed-122">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="367ed-122">Value Types</span></span>](value-types.md)
- [<span data-ttu-id="367ed-123">class</span><span class="sxs-lookup"><span data-stu-id="367ed-123">class</span></span>](class.md)
- [<span data-ttu-id="367ed-124">interface</span><span class="sxs-lookup"><span data-stu-id="367ed-124">interface</span></span>](interface.md)
- [<span data-ttu-id="367ed-125">Klasy i struktury</span><span class="sxs-lookup"><span data-stu-id="367ed-125">Classes and Structs</span></span>](../../programming-guide/classes-and-structs/index.md)
