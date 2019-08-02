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
ms.openlocfilehash: 4852e1166a975b1a45c5bd905123a35fc846aa28
ms.sourcegitcommit: 463f3f050cecc0b6403e67f19a61f870fb8e7b7d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/26/2019
ms.locfileid: "68513161"
---
# <a name="sizeof-operator-c-reference"></a>sizeof — OperatorC# (odwołanie)

`sizeof` Operator zwraca liczbę bajtów zajmowanych przez zmienną danego typu. Argument `sizeof` operatora musi być nazwą [typu](../builtin-types/unmanaged-types.md) niezarządzanego lub parametrem typu, który jest [ograniczony](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) do niezarządzanego typu.

Operator wymaga niebezpiecznego kontekstu. [](../keywords/unsafe.md) `sizeof` Jednak wyrażenia przedstawione w poniższej tabeli są oceniane w czasie kompilacji do odpowiednich wartości stałych i nie wymagają niebezpiecznego kontekstu:

|Wyrażenie|Stała wartość|
|---------|---------------|
|`sizeof(sbyte)`|1|
|`sizeof(byte)`|1|
|`sizeof(short)`|2|
|`sizeof(ushort)`|2|
|`sizeof(int)`|4|
|`sizeof(uint)`|4|
|`sizeof(long)`|8|
|`sizeof(ulong)`|8|
|`sizeof(char)`|2|
|`sizeof(float)`|4|
|`sizeof(double)`|8|
|`sizeof(decimal)`|16|
|`sizeof(bool)`|1|

Nie trzeba również używać niebezpiecznego kontekstu, gdy operand `sizeof` operatora jest nazwą typu wyliczeniowego. [](../keywords/enum.md)

Poniższy przykład ilustruje użycie `sizeof` operatora:

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

`sizeof` Operator zwraca liczbę bajtów, które zostałyby przydzielone przez środowisko uruchomieniowe języka wspólnego w pamięci zarządzanej. W przypadku typów [struktur](../keywords/struct.md) ta wartość obejmuje wszelkie uzupełnienia, jak pokazano w powyższym przykładzie. Wynik `sizeof` operatora może się różnić od wyniku <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> metody, która zwraca rozmiar typu w pamięci niezarządzanej.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [operator sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Operatory powiązane z wskaźnikiem](pointer-related-operators.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
