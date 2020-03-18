---
title: Typy wartości — odwołanie do języka C#
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 406e5b8bbe0802146a65bb4b9a053e753a7827ee
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399582"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="f05f2-102">Typy wartości (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="f05f2-102">Value types (C# reference)</span></span>

<span data-ttu-id="f05f2-103">*Typy wartości* i [typy odwołań](../keywords/reference-types.md) są dwiegłówne kategorie typów C#.</span><span class="sxs-lookup"><span data-stu-id="f05f2-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="f05f2-104">Zmienna typu wartości zawiera wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="f05f2-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="f05f2-105">Różni się od zmiennej typu odwołania, która zawiera odwołanie do wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="f05f2-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="f05f2-106">Domyślnie w przypadku [przypisania](../operators/assignment-operator.md), przekazywania argumentu do metody i zwracania wyniku metody są kopiowane wartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="f05f2-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, and returning a method result, variable values are copied.</span></span> <span data-ttu-id="f05f2-107">W przypadku zmiennych typu wartości są kopiowane odpowiednie wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="f05f2-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="f05f2-108">W poniższym przykładzie przedstawiono to zachowanie:</span><span class="sxs-lookup"><span data-stu-id="f05f2-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](snippets/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="f05f2-109">Jak pokazano w poprzednim przykładzie, operacje na zmiennej typu wartości wpływają tylko na to wystąpienie typu wartości, przechowywane w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="f05f2-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="f05f2-110">Jeśli typ wartości zawiera element członkowski danych typu odwołania, tylko odwołanie do wystąpienia typu odwołania jest kopiowane podczas kopiowania wystąpienia typu wartości.</span><span class="sxs-lookup"><span data-stu-id="f05f2-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="f05f2-111">Zarówno kopia, jak i oryginalne wystąpienie typu wartości mają dostęp do tego samego wystąpienia typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="f05f2-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="f05f2-112">W poniższym przykładzie przedstawiono to zachowanie:</span><span class="sxs-lookup"><span data-stu-id="f05f2-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](snippets/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="f05f2-113">Aby kod był mniej podatny na błędy i bardziej niezawodny, należy zdefiniować i użyć niezmiennych typów wartości.</span><span class="sxs-lookup"><span data-stu-id="f05f2-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="f05f2-114">W tym artykule użyto typów wartości zapisywalnych tylko do celów demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="f05f2-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="f05f2-115">Rodzaje typów wartości</span><span class="sxs-lookup"><span data-stu-id="f05f2-115">Kinds of value types</span></span>

<span data-ttu-id="f05f2-116">Typ wartości może być jednym z dwóch następujących rodzajów:</span><span class="sxs-lookup"><span data-stu-id="f05f2-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="f05f2-117">[typ konstrukcji,](struct.md)który hermetyzuje dane i powiązane funkcje</span><span class="sxs-lookup"><span data-stu-id="f05f2-117">a [structure type](struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="f05f2-118">[typ wyliczenia](enum.md), który jest definiowany przez zestaw nazwanych stałych i reprezentuje wybór lub kombinację wyborów</span><span class="sxs-lookup"><span data-stu-id="f05f2-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="f05f2-119">[Typ](nullable-value-types.md) `T?` wartości nullable reprezentuje wszystkie wartości jego `T` podstawowego typu wartości i dodatkowej wartości [null.](../keywords/null.md)</span><span class="sxs-lookup"><span data-stu-id="f05f2-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="f05f2-120">Nie można `null` przypisać do zmiennej typu wartości, chyba że jest to typ wartości z wartością null.</span><span class="sxs-lookup"><span data-stu-id="f05f2-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="f05f2-121">Wbudowane typy wartości</span><span class="sxs-lookup"><span data-stu-id="f05f2-121">Built-in value types</span></span>

<span data-ttu-id="f05f2-122">C# zawiera następujące wbudowane typy wartości, znane również jako *typy proste:*</span><span class="sxs-lookup"><span data-stu-id="f05f2-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="f05f2-123">Typy liczb całkowitych</span><span class="sxs-lookup"><span data-stu-id="f05f2-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="f05f2-124">Zmiennoprzecinkowe rodzaje wartości numerycznych</span><span class="sxs-lookup"><span data-stu-id="f05f2-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="f05f2-125">[bool](bool.md) reprezentujący wartość logiczną</span><span class="sxs-lookup"><span data-stu-id="f05f2-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="f05f2-126">[char,](char.md) który reprezentuje znak Unicode UTF-16</span><span class="sxs-lookup"><span data-stu-id="f05f2-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="f05f2-127">Wszystkie typy proste są typy struktury i różnią się od innych typów struktury, ponieważ pozwalają one na pewne dodatkowe operacje:</span><span class="sxs-lookup"><span data-stu-id="f05f2-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="f05f2-128">Można użyć literału, aby zapewnić wartość typu prostego.</span><span class="sxs-lookup"><span data-stu-id="f05f2-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="f05f2-129">Na przykład `'A'` jest literałem `char` `2001` typu i jest `int`literałem typu .</span><span class="sxs-lookup"><span data-stu-id="f05f2-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="f05f2-130">Za pomocą słowa kluczowego [const](../keywords/const.md) można deklarować stałe typów prostych.</span><span class="sxs-lookup"><span data-stu-id="f05f2-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="f05f2-131">Nie jest możliwe, aby mieć stałe innych typów struktury.</span><span class="sxs-lookup"><span data-stu-id="f05f2-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="f05f2-132">Wyrażenia stałe, których argumenty są wszystkie stałe typów prostych, są oceniane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="f05f2-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="f05f2-133">Począwszy od języka C# 7.0, C# obsługuje [krotek wartości](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="f05f2-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="f05f2-134">Krotka wartości jest typem wartości, ale nie jest typem prostym.</span><span class="sxs-lookup"><span data-stu-id="f05f2-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="f05f2-135">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f05f2-135">C# language specification</span></span>

<span data-ttu-id="f05f2-136">Aby uzyskać więcej informacji, zobacz następujące sekcje [specyfikacji języka Języka C#:](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="f05f2-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="f05f2-137">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="f05f2-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="f05f2-138">Typy proste</span><span class="sxs-lookup"><span data-stu-id="f05f2-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="f05f2-139">Zmienne</span><span class="sxs-lookup"><span data-stu-id="f05f2-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="f05f2-140">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="f05f2-140">See also</span></span>

- [<span data-ttu-id="f05f2-141">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="f05f2-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="f05f2-142">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="f05f2-142">Reference types</span></span>](../keywords/reference-types.md)
