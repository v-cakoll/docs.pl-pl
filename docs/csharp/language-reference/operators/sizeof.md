---
title: sizeof operator - odwołanie do języka C#
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: a9e80ecb3288479a2ca81b43c9d088809ed5f2f0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78847290"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="a98ec-102">operator sizeof (odwołanie do języka C#)</span><span class="sxs-lookup"><span data-stu-id="a98ec-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="a98ec-103">Operator `sizeof` zwraca liczbę bajtów zajmowanych przez zmienną danego typu.</span><span class="sxs-lookup"><span data-stu-id="a98ec-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="a98ec-104">Argument `sizeof` do operatora musi być nazwa [typu niezarządzanego](../builtin-types/unmanaged-types.md) lub parametr typu, który jest [ograniczony](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) do typu niezarządzanego.</span><span class="sxs-lookup"><span data-stu-id="a98ec-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="a98ec-105">Operator `sizeof` wymaga [niebezpiecznego](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="a98ec-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="a98ec-106">Jednak wyrażenia przedstawione w poniższej tabeli są obliczane w czasie kompilacji do odpowiednich wartości stałych i nie wymagają niebezpiecznego kontekstu:</span><span class="sxs-lookup"><span data-stu-id="a98ec-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="a98ec-107">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="a98ec-107">Expression</span></span>|<span data-ttu-id="a98ec-108">Stała wartość</span><span class="sxs-lookup"><span data-stu-id="a98ec-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="a98ec-109">1</span><span class="sxs-lookup"><span data-stu-id="a98ec-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="a98ec-110">1</span><span class="sxs-lookup"><span data-stu-id="a98ec-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="a98ec-111">2</span><span class="sxs-lookup"><span data-stu-id="a98ec-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="a98ec-112">2</span><span class="sxs-lookup"><span data-stu-id="a98ec-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="a98ec-113">4</span><span class="sxs-lookup"><span data-stu-id="a98ec-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="a98ec-114">4</span><span class="sxs-lookup"><span data-stu-id="a98ec-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="a98ec-115">8</span><span class="sxs-lookup"><span data-stu-id="a98ec-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="a98ec-116">8</span><span class="sxs-lookup"><span data-stu-id="a98ec-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="a98ec-117">2</span><span class="sxs-lookup"><span data-stu-id="a98ec-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="a98ec-118">4</span><span class="sxs-lookup"><span data-stu-id="a98ec-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="a98ec-119">8</span><span class="sxs-lookup"><span data-stu-id="a98ec-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="a98ec-120">16</span><span class="sxs-lookup"><span data-stu-id="a98ec-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="a98ec-121">1</span><span class="sxs-lookup"><span data-stu-id="a98ec-121">1</span></span>|

<span data-ttu-id="a98ec-122">Nie trzeba również używać niebezpiecznego kontekstu, gdy operand `sizeof` operatora jest nazwą typu [wyliczenia.](../builtin-types/enum.md)</span><span class="sxs-lookup"><span data-stu-id="a98ec-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="a98ec-123">W poniższym przykładzie przedstawiono `sizeof` użycie operatora:</span><span class="sxs-lookup"><span data-stu-id="a98ec-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](snippets/SizeOfOperator.cs)]

<span data-ttu-id="a98ec-124">Operator `sizeof` zwraca liczbę bajtów, które zostaną przydzielone przez środowisko uruchomieniowe języka wspólnego w pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="a98ec-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="a98ec-125">Dla typów [struktury,](../builtin-types/struct.md) ta wartość zawiera dopełnienie, jak pokazano w poprzednim przykładzie.</span><span class="sxs-lookup"><span data-stu-id="a98ec-125">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="a98ec-126">Wynik `sizeof` operatora może się różnić od <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> wyniku metody, która zwraca rozmiar typu w pamięci *niezarządzanej.*</span><span class="sxs-lookup"><span data-stu-id="a98ec-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="a98ec-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a98ec-127">C# language specification</span></span>

<span data-ttu-id="a98ec-128">Aby uzyskać więcej informacji, zobacz [sekcję operatora sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)</span><span class="sxs-lookup"><span data-stu-id="a98ec-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a98ec-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="a98ec-129">See also</span></span>

- [<span data-ttu-id="a98ec-130">Dokumentacja języka C#</span><span class="sxs-lookup"><span data-stu-id="a98ec-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="a98ec-131">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="a98ec-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="a98ec-132">Operatory związane ze wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="a98ec-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="a98ec-133">Typy wskaźnika</span><span class="sxs-lookup"><span data-stu-id="a98ec-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="a98ec-134">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="a98ec-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="a98ec-135">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="a98ec-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
