---
title: Typy wartości — C# odwołanie
ms.date: 01/22/2020
f1_keywords:
- cs.valuetypes
helpviewer_keywords:
- value types [C#]
- types [C#], value types
- C# language, value types
ms.assetid: 471eb994-2958-49d5-a6be-19b4313f80a3
ms.openlocfilehash: 6b96d65f657f2af1af5c9a245e956640ee06260e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76748518"
---
# <a name="value-types-c-reference"></a><span data-ttu-id="479b1-102">Typy wartości (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="479b1-102">Value types (C# reference)</span></span>

<span data-ttu-id="479b1-103">*Typy wartości* i [typy odwołań](../keywords/reference-types.md) to dwie główne kategorie C# typów.</span><span class="sxs-lookup"><span data-stu-id="479b1-103">*Value types* and [reference types](../keywords/reference-types.md) are the two main categories of C# types.</span></span> <span data-ttu-id="479b1-104">Zmienna typu wartości zawiera wystąpienie typu.</span><span class="sxs-lookup"><span data-stu-id="479b1-104">A variable of a value type contains an instance of the type.</span></span> <span data-ttu-id="479b1-105">Różni się to od zmiennej typu referencyjnego, która zawiera odwołanie do wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="479b1-105">This differs from a variable of a reference type, which contains a reference to an instance of the type.</span></span> <span data-ttu-id="479b1-106">Domyślnie podczas [przypisywania](../operators/assignment-operator.md), przekazywania argumentu do metody lub zwracając wynik metody, kopiowane są wartości zmiennych.</span><span class="sxs-lookup"><span data-stu-id="479b1-106">By default, on [assignment](../operators/assignment-operator.md), passing an argument to a method, or returning a method result, variable values are copied.</span></span> <span data-ttu-id="479b1-107">W przypadku zmiennych typu wartość są kopiowane odpowiednie wystąpienia typu.</span><span class="sxs-lookup"><span data-stu-id="479b1-107">In the case of value-type variables, the corresponding type instances are copied.</span></span> <span data-ttu-id="479b1-108">Poniższy przykład ilustruje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="479b1-108">The following example demonstrates that behavior:</span></span>

[!code-csharp[copy of values](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ValueTypeCopied)]

<span data-ttu-id="479b1-109">Jak pokazano w powyższym przykładzie, operacje na zmiennej typu wartości wpływają tylko na to wystąpienie typu wartości przechowywane w zmiennej.</span><span class="sxs-lookup"><span data-stu-id="479b1-109">As the preceding example shows, operations on a value-type variable affect only that instance of the value type, stored in the variable.</span></span>

<span data-ttu-id="479b1-110">Jeśli typ wartości zawiera element członkowski danych typu referencyjnego, podczas kopiowania wystąpienia typu wartości jest kopiowane tylko odwołanie do wystąpienia typu referencyjnego.</span><span class="sxs-lookup"><span data-stu-id="479b1-110">If a value type contains a data member of a reference type, only the reference to the instance of the reference type is copied when a value-type instance is copied.</span></span> <span data-ttu-id="479b1-111">Zarówno kopia, jak i oryginalne wystąpienie typu wartości mają dostęp do tego samego wystąpienia typu odwołania.</span><span class="sxs-lookup"><span data-stu-id="479b1-111">Both the copy and original value-type instance have access to the same reference-type instance.</span></span> <span data-ttu-id="479b1-112">Poniższy przykład ilustruje takie zachowanie:</span><span class="sxs-lookup"><span data-stu-id="479b1-112">The following example demonstrates that behavior:</span></span>

[!code-csharp[shallow copy](~/samples/csharp/language-reference/builtin-types/ValueTypes.cs#ShallowCopy)]

> [!NOTE]
> <span data-ttu-id="479b1-113">Aby kod był mniej podatny na błędy i bardziej niezawodny, definiować i korzystać z niezmiennego typu wartości.</span><span class="sxs-lookup"><span data-stu-id="479b1-113">To make your code less error-prone and more robust, define and use immutable value types.</span></span> <span data-ttu-id="479b1-114">W tym artykule są stosowane modyfikowalne typy wartości tylko w celach demonstracyjnych.</span><span class="sxs-lookup"><span data-stu-id="479b1-114">This article uses mutable value types only for demonstration purposes.</span></span>

## <a name="kinds-of-value-types"></a><span data-ttu-id="479b1-115">Rodzaje typów wartości</span><span class="sxs-lookup"><span data-stu-id="479b1-115">Kinds of value types</span></span>

<span data-ttu-id="479b1-116">Typ wartości może być jednym z dwóch następujących rodzajów:</span><span class="sxs-lookup"><span data-stu-id="479b1-116">A value type can be one of the two following kinds:</span></span>

- <span data-ttu-id="479b1-117">[Typ struktury](../keywords/struct.md), który hermetyzuje dane i powiązane funkcje</span><span class="sxs-lookup"><span data-stu-id="479b1-117">a [structure type](../keywords/struct.md), which encapsulates data and related functionality</span></span>
- <span data-ttu-id="479b1-118">[Typ wyliczeniowy](enum.md), który jest zdefiniowany przez zestaw nazwanych stałych i reprezentuje wybór lub kombinację opcji</span><span class="sxs-lookup"><span data-stu-id="479b1-118">an [enumeration type](enum.md), which is defined by a set of named constants and represents a choice or a combination of choices</span></span>

<span data-ttu-id="479b1-119">[Typ wartości null](nullable-value-types.md) `T?` reprezentuje wszystkie wartości jego bazowego typu wartości `T` i dodatkową wartość [null](../keywords/null.md) .</span><span class="sxs-lookup"><span data-stu-id="479b1-119">A [nullable value type](nullable-value-types.md) `T?` represents all values of its underlying value type `T` and an additional [null](../keywords/null.md) value.</span></span> <span data-ttu-id="479b1-120">Nie można przypisać `null` do zmiennej typu wartości, chyba że jest to typ wartości null.</span><span class="sxs-lookup"><span data-stu-id="479b1-120">You cannot assign `null` to a variable of a value type, unless it's a nullable value type.</span></span>

## <a name="built-in-value-types"></a><span data-ttu-id="479b1-121">Wbudowane typy wartości</span><span class="sxs-lookup"><span data-stu-id="479b1-121">Built-in value types</span></span>

<span data-ttu-id="479b1-122">C#Program udostępnia następujące wbudowane typy wartości, znane także jako *typy proste*:</span><span class="sxs-lookup"><span data-stu-id="479b1-122">C# provides the following built-in value types, also known as *simple types*:</span></span>

- [<span data-ttu-id="479b1-123">Całkowite typy liczbowe</span><span class="sxs-lookup"><span data-stu-id="479b1-123">Integral numeric types</span></span>](integral-numeric-types.md)
- [<span data-ttu-id="479b1-124">Zmiennoprzecinkowe typy liczbowe</span><span class="sxs-lookup"><span data-stu-id="479b1-124">Floating-point numeric types</span></span>](floating-point-numeric-types.md)
- <span data-ttu-id="479b1-125">[bool](bool.md) reprezentujący wartość logiczną</span><span class="sxs-lookup"><span data-stu-id="479b1-125">[bool](bool.md) that represents a Boolean value</span></span>
- <span data-ttu-id="479b1-126">[char](char.md) , który reprezentuje znak Unicode UTF-16</span><span class="sxs-lookup"><span data-stu-id="479b1-126">[char](char.md) that represents a Unicode UTF-16 character</span></span>

<span data-ttu-id="479b1-127">Wszystkie typy proste są typami struktury i różnią się od innych typów struktury w tym, że dopuszczają pewne dodatkowe operacje:</span><span class="sxs-lookup"><span data-stu-id="479b1-127">All simple types are structure types and differ from other structure types in that they permit certain additional operations:</span></span>

- <span data-ttu-id="479b1-128">Można użyć literałów, aby podać wartość typu prostego.</span><span class="sxs-lookup"><span data-stu-id="479b1-128">You can use literals to provide a value of a simple type.</span></span> <span data-ttu-id="479b1-129">Na przykład `'A'` jest literałem typu `char`, a `2001` jest literałem typu `int`.</span><span class="sxs-lookup"><span data-stu-id="479b1-129">For example, `'A'` is a literal of the type `char` and `2001` is a literal of the type `int`.</span></span>

- <span data-ttu-id="479b1-130">Stałe typów prostych można zadeklarować za pomocą słowa kluczowego [const](../keywords/const.md) .</span><span class="sxs-lookup"><span data-stu-id="479b1-130">You can declare constants of the simple types with the [const](../keywords/const.md) keyword.</span></span> <span data-ttu-id="479b1-131">Nie jest możliwe posiadanie stałych dla innych typów struktury.</span><span class="sxs-lookup"><span data-stu-id="479b1-131">It's not possible to have constants of other structure types.</span></span>

- <span data-ttu-id="479b1-132">Wyrażenia stałe, których operandy to wszystkie stałe typów prostych, są oceniane w czasie kompilacji.</span><span class="sxs-lookup"><span data-stu-id="479b1-132">Constant expressions, whose operands are all constants of the simple types, are evaluated at compile time.</span></span>

<span data-ttu-id="479b1-133">Począwszy od C# 7,0, C# obsługuje [krotki wartości](../../tuples.md).</span><span class="sxs-lookup"><span data-stu-id="479b1-133">Beginning with C# 7.0, C# supports [value tuples](../../tuples.md).</span></span> <span data-ttu-id="479b1-134">Krotka wartości jest typem wartości, ale nie typem prostym.</span><span class="sxs-lookup"><span data-stu-id="479b1-134">A value tuple is a value type, but not a simple type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="479b1-135">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="479b1-135">C# language specification</span></span>

<span data-ttu-id="479b1-136">Aby uzyskać więcej informacji, zobacz następujące sekcje [ C# specyfikacji języka](~/_csharplang/spec/introduction.md):</span><span class="sxs-lookup"><span data-stu-id="479b1-136">For more information, see the following sections of the [C# language specification](~/_csharplang/spec/introduction.md):</span></span>

- [<span data-ttu-id="479b1-137">Typy wartości</span><span class="sxs-lookup"><span data-stu-id="479b1-137">Value types</span></span>](~/_csharplang/spec/types.md#value-types)
- [<span data-ttu-id="479b1-138">Typy proste</span><span class="sxs-lookup"><span data-stu-id="479b1-138">Simple types</span></span>](~/_csharplang/spec/types.md#simple-types)
- [<span data-ttu-id="479b1-139">Zmienne</span><span class="sxs-lookup"><span data-stu-id="479b1-139">Variables</span></span>](~/_csharplang/spec/variables.md)

## <a name="see-also"></a><span data-ttu-id="479b1-140">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="479b1-140">See also</span></span>

- [<span data-ttu-id="479b1-141">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="479b1-141">C# reference</span></span>](../index.md)
- <xref:System.ValueType?displayProperty=nameWithType>
- [<span data-ttu-id="479b1-142">Typy odwołań</span><span class="sxs-lookup"><span data-stu-id="479b1-142">Reference types</span></span>](../keywords/reference-types.md)
