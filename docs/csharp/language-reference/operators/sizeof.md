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
ms.openlocfilehash: 32103043d4c3a8b38f4c8aad80282f6c0555719f
ms.sourcegitcommit: ad800f019ac976cb669e635fb0ea49db740e6890
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/29/2019
ms.locfileid: "73038936"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="5d8f3-102">sizeof — OperatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="5d8f3-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="5d8f3-103">Operator `sizeof` zwraca liczbę bajtów zajmowanych przez zmienną danego typu.</span><span class="sxs-lookup"><span data-stu-id="5d8f3-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="5d8f3-104">Argument operatora `sizeof` musi być nazwą [typu niezarządzanego](../builtin-types/unmanaged-types.md) lub parametrem typu, który jest [ograniczony](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) jako typ niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="5d8f3-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="5d8f3-105">Operator `sizeof` wymaga [niebezpiecznego](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="5d8f3-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="5d8f3-106">Jednak wyrażenia przedstawione w poniższej tabeli są oceniane w czasie kompilacji do odpowiednich wartości stałych i nie wymagają niebezpiecznego kontekstu:</span><span class="sxs-lookup"><span data-stu-id="5d8f3-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="5d8f3-107">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="5d8f3-107">Expression</span></span>|<span data-ttu-id="5d8f3-108">Stała wartość</span><span class="sxs-lookup"><span data-stu-id="5d8f3-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="5d8f3-109">1</span><span class="sxs-lookup"><span data-stu-id="5d8f3-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="5d8f3-110">1</span><span class="sxs-lookup"><span data-stu-id="5d8f3-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="5d8f3-111">2</span><span class="sxs-lookup"><span data-stu-id="5d8f3-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="5d8f3-112">2</span><span class="sxs-lookup"><span data-stu-id="5d8f3-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="5d8f3-113">4</span><span class="sxs-lookup"><span data-stu-id="5d8f3-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="5d8f3-114">4</span><span class="sxs-lookup"><span data-stu-id="5d8f3-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="5d8f3-115">8</span><span class="sxs-lookup"><span data-stu-id="5d8f3-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="5d8f3-116">8</span><span class="sxs-lookup"><span data-stu-id="5d8f3-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="5d8f3-117">2</span><span class="sxs-lookup"><span data-stu-id="5d8f3-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="5d8f3-118">4</span><span class="sxs-lookup"><span data-stu-id="5d8f3-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="5d8f3-119">8</span><span class="sxs-lookup"><span data-stu-id="5d8f3-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="5d8f3-120">16</span><span class="sxs-lookup"><span data-stu-id="5d8f3-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="5d8f3-121">1</span><span class="sxs-lookup"><span data-stu-id="5d8f3-121">1</span></span>|

<span data-ttu-id="5d8f3-122">Nie trzeba również używać niebezpiecznego kontekstu, gdy argument operacji operatora `sizeof` jest nazwą typu [wyliczeniowego](../keywords/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="5d8f3-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../keywords/enum.md) type.</span></span>

<span data-ttu-id="5d8f3-123">Poniższy przykład ilustruje użycie operatora `sizeof`:</span><span class="sxs-lookup"><span data-stu-id="5d8f3-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="5d8f3-124">Operator `sizeof` zwraca liczbę bajtów, które zostałyby przydzielone przez środowisko uruchomieniowe języka wspólnego w pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="5d8f3-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="5d8f3-125">W przypadku typów [struktur](../keywords/struct.md) ta wartość obejmuje wszelkie uzupełnienia, jak pokazano w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="5d8f3-125">For [struct](../keywords/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="5d8f3-126">Wynik operatora `sizeof` może różnić się od wyniku metody <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, która zwraca rozmiar typu w pamięci *niezarządzanej* .</span><span class="sxs-lookup"><span data-stu-id="5d8f3-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="5d8f3-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="5d8f3-127">C# language specification</span></span>

<span data-ttu-id="5d8f3-128">Aby uzyskać więcej informacji, zobacz sekcję [operator sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="5d8f3-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5d8f3-129">Zobacz także</span><span class="sxs-lookup"><span data-stu-id="5d8f3-129">See also</span></span>

- [<span data-ttu-id="5d8f3-130">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="5d8f3-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="5d8f3-131">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="5d8f3-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="5d8f3-132">Operatory powiązane z wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="5d8f3-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="5d8f3-133">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="5d8f3-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="5d8f3-134">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="5d8f3-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="5d8f3-135">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="5d8f3-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
