---
title: Typy niezarządzane — odwołanie do języka C#
ms.date: 09/06/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 9dd2ab4e044b8a86bfe72a6fcf2481b8e1e80bf4
ms.sourcegitcommit: 2514f4e3655081dcfe1b22470c0c28500f952c42
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/18/2020
ms.locfileid: "79507233"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="6ac72-102">Typy niezarządzane (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="6ac72-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="6ac72-103">Typ jest **typem niezarządzanym,** jeśli jest to jeden z następujących typów:</span><span class="sxs-lookup"><span data-stu-id="6ac72-103">A type is an **unmanaged type** if it's any of the following types:</span></span>

- <span data-ttu-id="6ac72-104">`sbyte`, `byte` `short`, `ushort` `int`, `uint` `long`, `ulong` `char`, `float` `double`, `decimal`, , , , , , , lub`bool`</span><span class="sxs-lookup"><span data-stu-id="6ac72-104">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="6ac72-105">Dowolny typ [wyliczenia](enum.md)</span><span class="sxs-lookup"><span data-stu-id="6ac72-105">Any [enum](enum.md) type</span></span>
- <span data-ttu-id="6ac72-106">Dowolny typ [wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="6ac72-106">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="6ac72-107">Każdy zdefiniowany przez użytkownika typ [struktury,](struct.md) który zawiera tylko pola typów niezarządzanych i w języku C# 7.3 i wcześniejszych nie jest typem skonstruowanym (typ, który zawiera co najmniej jeden argument typu)</span><span class="sxs-lookup"><span data-stu-id="6ac72-107">Any user-defined [struct](struct.md) type that contains fields of unmanaged types only and, in C# 7.3 and earlier, is not a constructed type (a type that includes at least one type argument)</span></span>

<span data-ttu-id="6ac72-108">Począwszy od języka C# 7.3, można użyć [ `unmanaged` ograniczenia,](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) aby określić, że parametr typu jest nie-wskaźnik, non-null typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="6ac72-108">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer, non-nullable unmanaged type.</span></span>

<span data-ttu-id="6ac72-109">Począwszy od języka C# 8.0, *skonstruowany* typ struktury, który zawiera tylko pola typów niezarządzanych, jest również niezarządzany, jak pokazano w poniższym przykładzie:</span><span class="sxs-lookup"><span data-stu-id="6ac72-109">Beginning with C# 8.0, a *constructed* struct type that contains fields of unmanaged types only is also unmanaged, as the following example shows:</span></span>

[!code-csharp[unmanaged constructed types](snippets/UnmanagedTypes.cs#ProgramExample)]

<span data-ttu-id="6ac72-110">Struktura rodzajowa może być źródłem typów bez mana i niezarządzanych.</span><span class="sxs-lookup"><span data-stu-id="6ac72-110">A generic struct may be the source of both unmanaged and not unmanaged constructed types.</span></span> <span data-ttu-id="6ac72-111">W poprzednim przykładzie definiuje strukturę `Coords<T>` rodzajową i przedstawia przykłady niezarządzanych typów skonstruowanych.</span><span class="sxs-lookup"><span data-stu-id="6ac72-111">The preceding example defines a generic struct `Coords<T>` and presents the examples of unmanaged constructed types.</span></span> <span data-ttu-id="6ac72-112">Przykładem typu niezarządzanego `Coords<object>`jest .</span><span class="sxs-lookup"><span data-stu-id="6ac72-112">The example of not an unmanaged type is `Coords<object>`.</span></span> <span data-ttu-id="6ac72-113">Nie jest niezarządzane, ponieważ ma `object` pola typu, który nie jest niezarządzane.</span><span class="sxs-lookup"><span data-stu-id="6ac72-113">It's not unmanaged because it has the fields of the `object` type, which is not unmanaged.</span></span> <span data-ttu-id="6ac72-114">Jeśli *chcesz,* aby wszystkie typy skonstruowane były `unmanaged` typami niezarządzanym, użyj ograniczenia w definicji struktury ogólnej:</span><span class="sxs-lookup"><span data-stu-id="6ac72-114">If you want *all* constructed types to be unmanaged types, use the `unmanaged` constraint in the definition of a generic struct:</span></span>

[!code-csharp[unmanaged constraint in type definition](snippets/UnmanagedTypes.cs#AlwaysUnmanaged)]

## <a name="c-language-specification"></a><span data-ttu-id="6ac72-115">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6ac72-115">C# language specification</span></span>

<span data-ttu-id="6ac72-116">Aby uzyskać więcej informacji, zobacz sekcję [Typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [specyfikacji języka języka języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="6ac72-116">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6ac72-117">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="6ac72-117">See also</span></span>

- [<span data-ttu-id="6ac72-118">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6ac72-118">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6ac72-119">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="6ac72-119">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="6ac72-120">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="6ac72-120">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="6ac72-121">sizeof, operator</span><span class="sxs-lookup"><span data-stu-id="6ac72-121">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="6ac72-122">stackalloc</span><span class="sxs-lookup"><span data-stu-id="6ac72-122">stackalloc</span></span>](../operators/stackalloc.md)
