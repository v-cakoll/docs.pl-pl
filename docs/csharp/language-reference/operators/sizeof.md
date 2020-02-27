---
title: sizeof — C# odwołanie operatora
ms.date: 07/25/2019
f1_keywords:
- sizeof_CSharpKeyword
- sizeof
helpviewer_keywords:
- sizeof keyword [C#]
ms.assetid: c548592c-677c-4f40-a4ce-e613f7529141
ms.openlocfilehash: 8e4518718d0975f8b4a65870f15d8c52d692c2f5
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/26/2020
ms.locfileid: "77625738"
---
# <a name="sizeof-operator-c-reference"></a><span data-ttu-id="1d823-102">sizeof — OperatorC# (odwołanie)</span><span class="sxs-lookup"><span data-stu-id="1d823-102">sizeof operator (C# reference)</span></span>

<span data-ttu-id="1d823-103">Operator `sizeof` zwraca liczbę bajtów zajmowanych przez zmienną danego typu.</span><span class="sxs-lookup"><span data-stu-id="1d823-103">The `sizeof` operator returns the number of bytes occupied by a variable of a given type.</span></span> <span data-ttu-id="1d823-104">Argument operatora `sizeof` musi być nazwą [typu niezarządzanego](../builtin-types/unmanaged-types.md) lub parametrem typu, który jest [ograniczony](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) jako typ niezarządzany.</span><span class="sxs-lookup"><span data-stu-id="1d823-104">The argument to the `sizeof` operator must be the name of an [unmanaged type](../builtin-types/unmanaged-types.md) or a type parameter that is [constrained](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) to be an unmanaged type.</span></span>

<span data-ttu-id="1d823-105">Operator `sizeof` wymaga [niebezpiecznego](../keywords/unsafe.md) kontekstu.</span><span class="sxs-lookup"><span data-stu-id="1d823-105">The `sizeof` operator requires an [unsafe](../keywords/unsafe.md) context.</span></span> <span data-ttu-id="1d823-106">Jednak wyrażenia przedstawione w poniższej tabeli są oceniane w czasie kompilacji do odpowiednich wartości stałych i nie wymagają niebezpiecznego kontekstu:</span><span class="sxs-lookup"><span data-stu-id="1d823-106">However, the expressions presented in the following table are evaluated in compile time to the corresponding constant values and don't require an unsafe context:</span></span>

|<span data-ttu-id="1d823-107">Wyrażenie</span><span class="sxs-lookup"><span data-stu-id="1d823-107">Expression</span></span>|<span data-ttu-id="1d823-108">Stała wartość</span><span class="sxs-lookup"><span data-stu-id="1d823-108">Constant value</span></span>|
|---------|---------------|
|`sizeof(sbyte)`|<span data-ttu-id="1d823-109">1</span><span class="sxs-lookup"><span data-stu-id="1d823-109">1</span></span>|
|`sizeof(byte)`|<span data-ttu-id="1d823-110">1</span><span class="sxs-lookup"><span data-stu-id="1d823-110">1</span></span>|
|`sizeof(short)`|<span data-ttu-id="1d823-111">2</span><span class="sxs-lookup"><span data-stu-id="1d823-111">2</span></span>|
|`sizeof(ushort)`|<span data-ttu-id="1d823-112">2</span><span class="sxs-lookup"><span data-stu-id="1d823-112">2</span></span>|
|`sizeof(int)`|<span data-ttu-id="1d823-113">4</span><span class="sxs-lookup"><span data-stu-id="1d823-113">4</span></span>|
|`sizeof(uint)`|<span data-ttu-id="1d823-114">4</span><span class="sxs-lookup"><span data-stu-id="1d823-114">4</span></span>|
|`sizeof(long)`|<span data-ttu-id="1d823-115">8</span><span class="sxs-lookup"><span data-stu-id="1d823-115">8</span></span>|
|`sizeof(ulong)`|<span data-ttu-id="1d823-116">8</span><span class="sxs-lookup"><span data-stu-id="1d823-116">8</span></span>|
|`sizeof(char)`|<span data-ttu-id="1d823-117">2</span><span class="sxs-lookup"><span data-stu-id="1d823-117">2</span></span>|
|`sizeof(float)`|<span data-ttu-id="1d823-118">4</span><span class="sxs-lookup"><span data-stu-id="1d823-118">4</span></span>|
|`sizeof(double)`|<span data-ttu-id="1d823-119">8</span><span class="sxs-lookup"><span data-stu-id="1d823-119">8</span></span>|
|`sizeof(decimal)`|<span data-ttu-id="1d823-120">16</span><span class="sxs-lookup"><span data-stu-id="1d823-120">16</span></span>|
|`sizeof(bool)`|<span data-ttu-id="1d823-121">1</span><span class="sxs-lookup"><span data-stu-id="1d823-121">1</span></span>|

<span data-ttu-id="1d823-122">Nie trzeba również używać niebezpiecznego kontekstu, gdy argument operacji operatora `sizeof` jest nazwą typu [wyliczeniowego](../builtin-types/enum.md) .</span><span class="sxs-lookup"><span data-stu-id="1d823-122">You also don't need to use an unsafe context when the operand of the `sizeof` operator is the name of an [enum](../builtin-types/enum.md) type.</span></span>

<span data-ttu-id="1d823-123">Poniższy przykład ilustruje użycie operatora `sizeof`:</span><span class="sxs-lookup"><span data-stu-id="1d823-123">The following example demonstrates the usage of the `sizeof` operator:</span></span>

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

<span data-ttu-id="1d823-124">Operator `sizeof` zwraca liczbę bajtów, które zostałyby przydzielone przez środowisko uruchomieniowe języka wspólnego w pamięci zarządzanej.</span><span class="sxs-lookup"><span data-stu-id="1d823-124">The `sizeof` operator returns a number of bytes that would be allocated by the common language runtime in managed memory.</span></span> <span data-ttu-id="1d823-125">W przypadku typów [struktur](../builtin-types/struct.md) ta wartość obejmuje wszelkie uzupełnienia, jak pokazano w powyższym przykładzie.</span><span class="sxs-lookup"><span data-stu-id="1d823-125">For [struct](../builtin-types/struct.md) types, that value includes any padding, as the preceding example demonstrates.</span></span> <span data-ttu-id="1d823-126">Wynik operatora `sizeof` może różnić się od wyniku metody <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, która zwraca rozmiar typu w pamięci *niezarządzanej* .</span><span class="sxs-lookup"><span data-stu-id="1d823-126">The result of the `sizeof` operator might differ from the result of the <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> method, which returns the size of a type in *unmanaged* memory.</span></span>

## <a name="c-language-specification"></a><span data-ttu-id="1d823-127">specyfikacja języka C#</span><span class="sxs-lookup"><span data-stu-id="1d823-127">C# language specification</span></span>

<span data-ttu-id="1d823-128">Aby uzyskać więcej informacji, zobacz sekcję [operator sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).</span><span class="sxs-lookup"><span data-stu-id="1d823-128">For more information, see [The sizeof operator](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) section of the [C# language specification](~/_csharplang/spec/introduction.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1d823-129">Zobacz też</span><span class="sxs-lookup"><span data-stu-id="1d823-129">See also</span></span>

- [<span data-ttu-id="1d823-130">C#odwoła</span><span class="sxs-lookup"><span data-stu-id="1d823-130">C# reference</span></span>](../index.md)
- [<span data-ttu-id="1d823-131">Operatory języka C#</span><span class="sxs-lookup"><span data-stu-id="1d823-131">C# operators</span></span>](index.md)
- [<span data-ttu-id="1d823-132">Operatory powiązane z wskaźnikiem</span><span class="sxs-lookup"><span data-stu-id="1d823-132">Pointer related operators</span></span>](pointer-related-operators.md)
- [<span data-ttu-id="1d823-133">Typy wskaźników</span><span class="sxs-lookup"><span data-stu-id="1d823-133">Pointer types</span></span>](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [<span data-ttu-id="1d823-134">Pamięć i typy związane z zakresem</span><span class="sxs-lookup"><span data-stu-id="1d823-134">Memory and span-related types</span></span>](../../../standard/memory-and-spans/index.md)
- [<span data-ttu-id="1d823-135">Typy ogólne w .NET</span><span class="sxs-lookup"><span data-stu-id="1d823-135">Generics in .NET</span></span>](../../../standard/generics/index.md)
