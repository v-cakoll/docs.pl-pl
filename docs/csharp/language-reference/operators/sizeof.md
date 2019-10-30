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
# <a name="sizeof-operator-c-reference"></a>sizeof — OperatorC# (odwołanie)

Operator `sizeof` zwraca liczbę bajtów zajmowanych przez zmienną danego typu. Argument operatora `sizeof` musi być nazwą [typu niezarządzanego](../builtin-types/unmanaged-types.md) lub parametrem typu, który jest [ograniczony](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) jako typ niezarządzany.

Operator `sizeof` wymaga [niebezpiecznego](../keywords/unsafe.md) kontekstu. Jednak wyrażenia przedstawione w poniższej tabeli są oceniane w czasie kompilacji do odpowiednich wartości stałych i nie wymagają niebezpiecznego kontekstu:

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

Nie trzeba również używać niebezpiecznego kontekstu, gdy argument operacji operatora `sizeof` jest nazwą typu [wyliczeniowego](../keywords/enum.md) .

Poniższy przykład ilustruje użycie operatora `sizeof`:

[!code-csharp[sizeof examples](~/samples/csharp/language-reference/operators/SizeOfOperator.cs)]

Operator `sizeof` zwraca liczbę bajtów, które zostałyby przydzielone przez środowisko uruchomieniowe języka wspólnego w pamięci zarządzanej. W przypadku typów [struktur](../keywords/struct.md) ta wartość obejmuje wszelkie uzupełnienia, jak pokazano w powyższym przykładzie. Wynik operatora `sizeof` może różnić się od wyniku metody <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType>, która zwraca rozmiar typu w pamięci *niezarządzanej* .

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz sekcję [operator sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) w [ C# specyfikacji języka](~/_csharplang/spec/introduction.md).

## <a name="see-also"></a>Zobacz także

- [C#odwoła](../index.md)
- [Operatory języka C#](index.md)
- [Operatory powiązane z wskaźnikiem](pointer-related-operators.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
