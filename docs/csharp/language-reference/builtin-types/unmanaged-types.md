---
title: Typy niezarządzane — C# odwołanie
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 469309276c440493f6ed5b655139167f9a8b0885
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/03/2020
ms.locfileid: "78239745"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="fa34a-102">Typy niezarządzane (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="fa34a-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="fa34a-103">Typ jest **typem niezarządzanym** , jeśli jest dowolnego z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="fa34a-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="fa34a-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`lub `bool`</span><span class="sxs-lookup"><span data-stu-id="fa34a-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="fa34a-105">Dowolny typ [wyliczeniowy](enum.md)</span><span class="sxs-lookup"><span data-stu-id="fa34a-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="fa34a-106">Dowolny typ [wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="fa34a-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="fa34a-107">Dowolny zdefiniowany przez użytkownika typ [struktury](struct.md) , który zawiera pola tylko typy niezarządzane i, w C# 7,3 i wcześniejszych, nie jest typem skonstruowanym (typ, który zawiera co najmniej jeden argument typu)</span><span class="sxs-lookup"><span data-stu-id="fa34a-107">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="fa34a-108">Począwszy od C# 7,3, można użyć [ograniczenia`unmanaged`](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) , aby określić, że parametr typu jest niewskaźnikiem niebędącym typem niepuszczającym wartości null.</span><span class="sxs-lookup"><span data-stu-id="fa34a-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="fa34a-109">Począwszy od C# 8,0, *skonstruowany* typ struktury, który zawiera pola typów niezarządzanych, również jest niezarządzany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="fa34a-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](~/samples/snippets/csharp/language-reference/builtin-types/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="fa34a-110">Struktura generyczna może być źródłem zarówno typów niezarządzanych, jak i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="fa34a-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="fa34a-111">W poprzednim przykładzie zdefiniowano strukturę generyczną `Coords<T>` i przedstawiono przykłady niezarządzanych typów skonstruowanych.</span><span class="sxs-lookup"><span data-stu-id="fa34a-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="fa34a-112">Przykładem niezarządzanego typu jest `Coords<object>`.</span><span class="sxs-lookup"><span data-stu-id="fa34a-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="fa34a-113">Nie jest ona zarządzana, ponieważ zawiera pola typu `object`, które nie są zarządzane.</span><span class="sxs-lookup"><span data-stu-id="fa34a-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="fa34a-114">Jeśli chcesz, aby *wszystkie* skonstruowane typy były typami niezarządzanymi, użyj ograniczenia `unmanaged` w definicji generycznej struktury:</span><span class="sxs-lookup"><span data-stu-id="fa34a-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](~/samples/snippets/csharp/language-reference/builtin-types/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="fa34a-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="fa34a-115">C# language specification</span></span>

<span data-ttu-id="fa34a-116">Aby uzyskać więcej informacji, zobacz sekcję [typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="fa34a-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="fa34a-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="fa34a-117">See also</span></span>

- [<span data-ttu-id="fa34a-118">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="fa34a-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="fa34a-119">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="fa34a-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="fa34a-120">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="fa34a-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="fa34a-121">sizeof — Operator</span><span class="sxs-lookup"><span data-stu-id="fa34a-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="fa34a-122">operator stackalloc</span><span class="sxs-lookup"><span data-stu-id="fa34a-122">stackalloc operator</span></span>](../operators/stackalloc.md)
