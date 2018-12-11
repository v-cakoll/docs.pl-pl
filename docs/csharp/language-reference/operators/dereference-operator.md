---
title: -&gt; Operator - C# odwołania
ms.custom: seodec18
ms.date: 11/26/2018
f1_keywords:
- ->_CSharpKeyword
helpviewer_keywords:
- member access operator (->) [C#]
- -> operator [C#]
ms.assetid: e39ccdc1-f1ff-4a92-bf1d-ac2c8c11316a
ms.openlocfilehash: bb1ccd026f403e68565c5c7681943d8017578d01
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53234893"
---
# <a name="-gt-operator-c-reference"></a>-&gt; Operator (odwołanie w C#)

Operator dostępu do elementu członkowskiego wskaźnika `->` łączy dostępu wskaźnika pośredniego i elementów członkowskich.

Jeśli `x` jest wskaźnikiem typu `T*` i `y` jest dostępny członek `T`, wyrażenie formularza

```csharp
x->y
```

odpowiada wyrażeniu

```csharp
(*x).y
```

`->` Operator wymaga [niebezpieczne](../keywords/unsafe.md) kontekstu.

Aby uzyskać więcej informacji, zobacz [porady: uzyskiwanie dostępu do członka za pomocą wskaźnika](../../programming-guide/unsafe-code-pointers/how-to-access-a-member-with-a-pointer.md).

## <a name="operator-overloadability"></a>Overloadability — operator

Operator `->` nie może być przeciążony.

## <a name="c-language-specification"></a>specyfikacja języka C#

Aby uzyskać więcej informacji, zobacz [dostęp do elementu członkowskiego wskaźnika](~/_csharplang/spec/unsafe-code.md#pointer-member-access) części [ C# specyfikacji języka](../language-specification/index.md).

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)
- [Typy wskaźników](../../programming-guide/unsafe-code-pointers/pointer-types.md)
