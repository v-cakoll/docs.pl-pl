---
title: Typy niezarządzane — odwołanie do języka C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 8a4599514115aa21f17c32848ce203fea704072e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78846470"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="11657-102">Typy niezarządzane (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="11657-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="11657-103">Typ jest **typem niezarządzanym,** jeśli jest to którykolwiek z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="11657-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="11657-104">`sbyte``byte`, `short`, `ushort` `int`, `uint` `long`, `ulong` `char`, `float` `double`, `decimal`, , lub`bool`</span><span class="sxs-lookup"><span data-stu-id="11657-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="11657-105">Dowolny typ [wyliczenia](enum.md)</span><span class="sxs-lookup"><span data-stu-id="11657-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="11657-106">Dowolny typ [wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="11657-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="11657-107">Każdy typ [struktury](struct.md) zdefiniowany przez użytkownika, który zawiera pola tylko typów niezarządzanych i w języku C# 7.3 i starszym nie jest typem konstruowanym (typem zawierającym co najmniej jeden argument typu)</span><span class="sxs-lookup"><span data-stu-id="11657-107">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="11657-108">Począwszy od Języka C# 7.3, można użyć [ `unmanaged` ograniczenia,](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) aby określić, że parametr typu jest niewskaźnik, nienullable niezarządzane typu.</span><span class="sxs-lookup"><span data-stu-id="11657-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="11657-109">Począwszy od Języka C# 8.0, *skonstruowany* typ struktury, który zawiera pola tylko typy niezarządzane jest również niezarządzane, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="11657-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="11657-110">Struktura ogólna może być źródłem typów skonstruowanych niezarządzanych i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="11657-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="11657-111">W poprzednim przykładzie definiuje strukturę `Coords<T>` rodzajową i przedstawia przykłady typów skonstruowanych niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="11657-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="11657-112">Przykładem nie typu niezarządzanego `Coords<object>`jest .</span><span class="sxs-lookup"><span data-stu-id="11657-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="11657-113">Nie jest niezarządzany, ponieważ ma pola `object` typu, który nie jest niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="11657-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="11657-114">Jeśli chcesz, aby *wszystkie* typy skonstruowane `unmanaged` były typami niezarządzanymi, należy użyć ograniczenia w definicji struktury ogólnej:</span><span class="sxs-lookup"><span data-stu-id="11657-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="11657-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="11657-115">C# language specification</span></span>

<span data-ttu-id="11657-116">Aby uzyskać więcej informacji, zobacz [pointer typy](~/_csharplang/spec/unsafe-code.md#pointer-types) sekcji [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="11657-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="11657-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="11657-117">See also</span></span>

- [<span data-ttu-id="11657-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="11657-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="11657-119">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="11657-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="11657-120">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="11657-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="11657-121">sizeof, operator</span><span class="sxs-lookup"><span data-stu-id="11657-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="11657-122">stackalloc, operator</span><span class="sxs-lookup"><span data-stu-id="11657-122">stackalloc operator</span></span>](../operators/stackalloc.md)
