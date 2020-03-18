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
# <a name="sizeof-operator-c-reference"></a>operator sizeof (odwołanie do języka C#)

Operator `sizeof` zwraca liczbę bajtów zajmowanych przez zmienną danego typu. Argument `sizeof` do operatora musi być nazwa [typu niezarządzanego](../builtin-types/unmanaged-types.md) lub parametr typu, który jest [ograniczony](../../programming-guide/generics/constraints-on-type-parameters.md#unmanaged-constraint) do typu niezarządzanego.

Operator `sizeof` wymaga [niebezpiecznego](../keywords/unsafe.md) kontekstu. Jednak wyrażenia przedstawione w poniższej tabeli są obliczane w czasie kompilacji do odpowiednich wartości stałych i nie wymagają niebezpiecznego kontekstu:

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

Nie trzeba również używać niebezpiecznego kontekstu, gdy operand `sizeof` operatora jest nazwą typu [wyliczenia.](../builtin-types/enum.md)

W poniższym przykładzie przedstawiono `sizeof` użycie operatora:

[!code-csharp[sizeof examples](snippets/SizeOfOperator.cs)]

Operator `sizeof` zwraca liczbę bajtów, które zostaną przydzielone przez środowisko uruchomieniowe języka wspólnego w pamięci zarządzanej. Dla typów [struktury,](../builtin-types/struct.md) ta wartość zawiera dopełnienie, jak pokazano w poprzednim przykładzie. Wynik `sizeof` operatora może się różnić od <xref:System.Runtime.InteropServices.Marshal.SizeOf%2A?displayProperty=nameWithType> wyniku metody, która zwraca rozmiar typu w pamięci *niezarządzanej.*

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [sekcję operatora sizeof](~/_csharplang/spec/unsafe-code.md#the-sizeof-operator) [specyfikacji języka Języka C#.](~/_csharplang/spec/introduction.md)

## <a name="see-also"></a>Zobacz też

- [Dokumentacja języka C#](../index.md)
- [Operatory języka C#](index.md)
- [Operatory związane ze wskaźnikiem](pointer-related-operators.md)
- [Typy wskaźnika](../../programming-guide/unsafe-code-pointers/pointer-types.md)
- [Pamięć i typy związane z zakresem](../../../standard/memory-and-spans/index.md)
- [Typy ogólne w .NET](../../../standard/generics/index.md)
