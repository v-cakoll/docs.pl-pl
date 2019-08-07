---
title: sizeof — C# odwołanie operatora
ms.custom: seodec18
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: c455804923f4d0e7cc8f556bb9b9df34b6332d82
ms.sourcegitcommit: bbfcc913c275885381820be28f61efcf8e83eecc
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/05/2019
ms.locfileid: "68796514"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="6a40a-102">sizeof — OperatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="6a40a-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="6a40a-103">`sizeof` Operator zwraca liczbę bajtów zajmowanych przez zmienną danego typu.</span><span class="sxs-lookup"><span data-stu-id="6a40a-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="6a40a-104">Argument `sizeof` operatora musi być nazwą [typu](../builtin-types/unmanaged-types.md) niezarządzanego lub parametrem typu, który jest [ograniczony](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) do niezarządzanego typu.</span><span class="sxs-lookup"><span data-stu-id="6a40a-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="6a40a-105">Operator wymaga niebezpiecznego kontekstu. [](../keywords/unsafe.md) `sizeof`</span><span class="sxs-lookup"><span data-stu-id="6a40a-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="6a40a-106">Jednak wyrażenia przedstawione w poniższej tabeli są oceniane w czasie kompilacji do odpowiednich wartości stałych i nie wymagają niebezpiecznego kontekstu:</span><span class="sxs-lookup"><span data-stu-id="6a40a-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="6a40a-107">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="6a40a-107">Expression</span></span>|<span data-ttu-id="6a40a-108">Stała wartość</span><span class="sxs-lookup"><span data-stu-id="6a40a-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="6a40a-109">1</span><span class="sxs-lookup"><span data-stu-id="6a40a-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="6a40a-110">1</span><span class="sxs-lookup"><span data-stu-id="6a40a-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="6a40a-111">2</span><span class="sxs-lookup"><span data-stu-id="6a40a-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="6a40a-112">2</span><span class="sxs-lookup"><span data-stu-id="6a40a-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="6a40a-113">4</span><span class="sxs-lookup"><span data-stu-id="6a40a-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="6a40a-114">4</span><span class="sxs-lookup"><span data-stu-id="6a40a-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="6a40a-115">8</span><span class="sxs-lookup"><span data-stu-id="6a40a-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="6a40a-116">8</span><span class="sxs-lookup"><span data-stu-id="6a40a-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="6a40a-117">2</span><span class="sxs-lookup"><span data-stu-id="6a40a-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="6a40a-118">4</span><span class="sxs-lookup"><span data-stu-id="6a40a-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="6a40a-119">8</span><span class="sxs-lookup"><span data-stu-id="6a40a-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="6a40a-120">16</span><span class="sxs-lookup"><span data-stu-id="6a40a-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="6a40a-121">1</span><span class="sxs-lookup"><span data-stu-id="6a40a-121">1</span></span>|

<span data-ttu-id="6a40a-122">Nie trzeba również używać niebezpiecznego kontekstu, gdy operand `sizeof` operatora jest nazwą typu wyliczeniowego. [](../keywords/enum.md)</span><span class="sxs-lookup"><span data-stu-id="6a40a-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="6a40a-123">Poniższy przykład ilustruje użycie `sizeof` operatora:</span><span class="sxs-lookup"><span data-stu-id="6a40a-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="6a40a-124">`sizeof` Operator zwraca liczbę bajtów, które zostałyby przydzielone przez środowisko uruchomieniowe języka wspólnego w pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="6a40a-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="6a40a-125">W przypadku typów [struktur](../keywords/struct.md) ta wartość obejmuje wszelkie uzupełnienia, jak pokazano w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="6a40a-125">For [struct](../keywords/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="6a40a-126">Wynik `sizeof` operatora może się różnić od wyniku <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, która zwraca rozmiar typu w pamięci niezarządzanej.</span><span class="sxs-lookup"><span data-stu-id="6a40a-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="6a40a-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="6a40a-127">C# language specification</span></span>

<span data-ttu-id="6a40a-128">Aby uzyskać więcej informacji, zobacz sekcję [operator sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="6a40a-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6a40a-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="6a40a-129">See also</span></span>

- [<span data-ttu-id="6a40a-130">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="6a40a-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="6a40a-131">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="6a40a-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="6a40a-132">Operatory powiązane z wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="6a40a-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="6a40a-133">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="6a40a-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="6a40a-134">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="6a40a-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
