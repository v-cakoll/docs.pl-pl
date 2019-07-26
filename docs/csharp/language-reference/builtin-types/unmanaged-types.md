---
title: Typy niezarządzane — C# odwołanie
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 5b08b55f5c52fe2ad20cb25bca0449eb26e333ca
ms.sourcegitcommit: 1e7ac70be1b4d89708c0d9552897515f2cbf52c4
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/24/2019
ms.locfileid: "68440237"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="15433-102">Typy niezarządzane (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="15433-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="15433-103">**Typem** niezarządzanym jest dowolny typ, który nie jest typem referencyjnym lub typem konstruowanym (typ, który zawiera co najmniej jeden argument typu) i nie zawiera pól typu referencyjnego lub typu złożonego na dowolnym poziomie zagnieżdżania.</span><span class="sxs-lookup"><span data-stu-id="15433-103">An **unmanaged type** is any type that isn't a reference type or constructed type (a type that includes at least one type argument), and doesn't contain reference type or constructed type fields at any level of nesting.</span></span> <span data-ttu-id="15433-104">Innymi słowy, niezarządzany typ jest jednym z następujących:</span><span class="sxs-lookup"><span data-stu-id="15433-104">In other words, an unmanaged type is one of the following:</span></span>

- <span data-ttu-id="15433-105">`sbyte`, `byte` `short` ,`uint` ,,`float`,, ,`long` ,,`decimal`, ,`double`lub `ushort` `ulong` `int` `char``bool`</span><span class="sxs-lookup"><span data-stu-id="15433-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="15433-106">Dowolny typ [wyliczeniowy](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="15433-106">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="15433-107">Dowolny typ [wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="15433-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="15433-108">Dowolny zdefiniowany przez użytkownika typ [struktury](../keywords/struct.md) , który nie jest typem skonstruowanym i zawiera pola tylko typów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="15433-108">Any user-defined [struct](../keywords/struct.md) type that is not a constructed type and contains fields of unmanaged types only</span></span>

<span data-ttu-id="15433-109">Począwszy od C# 7,3, można użyć [ `unmanaged` ograniczenia](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) , aby określić, że parametr typu jest typem niezarządzanym wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="15433-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="15433-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="15433-110">C# language specification</span></span>

<span data-ttu-id="15433-111">Aby uzyskać więcej informacji, zobacz sekcję [typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="15433-111">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="15433-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="15433-112">See also</span></span>

- [<span data-ttu-id="15433-113">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="15433-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="15433-114">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="15433-114">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="15433-115">sizeof — Operator</span><span class="sxs-lookup"><span data-stu-id="15433-115">sizeof operator</span></span>](../keywords/sizeof.md)
- [<span data-ttu-id="15433-116">operator stackalloc</span><span class="sxs-lookup"><span data-stu-id="15433-116">stackalloc operator</span></span>](../operators/stackalloc.md)
