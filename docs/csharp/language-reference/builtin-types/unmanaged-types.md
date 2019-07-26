---
title: Typy niezarządzane — C# odwołanie
ms.date: 07/23/2019
helpviewer_keywords:
- unmanaged type [C#]
ms.openlocfilehash: 2b675be5dbc61006725549f4b69284326650401d
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68512078"
---
# <a name="unmanaged-types-c-reference"></a><span data-ttu-id="609ea-102">Typy niezarządzane (C# odwołanie)</span><span class="sxs-lookup"><span data-stu-id="609ea-102">Unmanaged types (C# reference)</span></span>

<span data-ttu-id="609ea-103">**Typem** niezarządzanym jest dowolny typ, który nie jest typem referencyjnym lub typem konstruowanym (typ, który zawiera co najmniej jeden argument typu) i nie zawiera pól typu referencyjnego lub typu złożonego na dowolnym poziomie zagnieżdżania.</span><span class="sxs-lookup"><span data-stu-id="609ea-103">An **unmanaged type** is any type that isn't a reference type or constructed type (a type that includes at least one type argument), and doesn't contain reference type or constructed type fields at any level of nesting.</span></span> <span data-ttu-id="609ea-104">Innymi słowy, niezarządzany typ jest jednym z następujących:</span><span class="sxs-lookup"><span data-stu-id="609ea-104">In other words, an unmanaged type is one of the following:</span></span>

- <span data-ttu-id="609ea-105">`sbyte`, `byte` `short` ,`uint` ,,`float`,, ,`long` ,,`decimal`, ,`double`lub `ushort` `ulong` `int` `char``bool`</span><span class="sxs-lookup"><span data-stu-id="609ea-105">`sbyte`, `byte`, `short`, `ushort`, `int`, `uint`, `long`, `ulong`, `char`, `float`, `double`, `decimal`, or `bool`</span></span>
- <span data-ttu-id="609ea-106">Dowolny typ [wyliczeniowy](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="609ea-106">Any [enum](../keywords/enum.md) type</span></span>
- <span data-ttu-id="609ea-107">Dowolny typ [wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)</span><span class="sxs-lookup"><span data-stu-id="609ea-107">Any [pointer](../../programming-guide/unsafe-code-pointers/pointer-types.md) type</span></span>
- <span data-ttu-id="609ea-108">Dowolny zdefiniowany przez użytkownika typ [struktury](../keywords/struct.md) , który nie jest typem skonstruowanym i zawiera pola tylko typów niezarządzanych</span><span class="sxs-lookup"><span data-stu-id="609ea-108">Any user-defined [struct](../keywords/struct.md) type that is not a constructed type and contains fields of unmanaged types only</span></span>

<span data-ttu-id="609ea-109">Począwszy od C# 7,3, można użyć [ `unmanaged` ograniczenia](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) , aby określić, że parametr typu jest typem niezarządzanym wskaźnika.</span><span class="sxs-lookup"><span data-stu-id="609ea-109">Beginning with C# 7.3, you can use the [`unmanaged` constraint](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to specify that a type parameter is a non-pointer unmanaged type.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="609ea-110">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="609ea-110">C# language specification</span></span>

<span data-ttu-id="609ea-111">Aby uzyskać więcej informacji, zobacz sekcję [typy wskaźników](~/_csharplang/spec/unsafe-code.md#pointer-types) [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="609ea-111">For more information, see the [Pointer types](~/_csharplang/spec/unsafe-code.md#pointer-types) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="609ea-112">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="609ea-112">See also</span></span>

- [<span data-ttu-id="609ea-113">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="609ea-113">C# reference</span></span>](../index.md)
- [<span data-ttu-id="609ea-114">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="609ea-114">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="609ea-115">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="609ea-115">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="609ea-116">sizeof — Operator</span><span class="sxs-lookup"><span data-stu-id="609ea-116">sizeof operator</span></span>](../operators/sizeof.md)
- [<span data-ttu-id="609ea-117">operator stackalloc</span><span class="sxs-lookup"><span data-stu-id="609ea-117">stackalloc operator</span></span>](../operators/stackalloc.md)
