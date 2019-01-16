---
title: operator () - C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- ()_CSharpKeyword
helpviewer_keywords:
- type conversion [C#], () operator
- cast operator [C#]
- () operator [C#]
ms.assetid: 846e1f94-8a8c-42fc-a42c-fbd38e70d8cc
ms.openlocfilehash: 656a1ca7a992df43ff857d2c4ecb62b044f7e06f
ms.sourcegitcommit: 5c36aaa8299a2437c155700c810585aff19edbec
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/16/2019
ms.locfileid: "54333281"
---
# <a name="-operator-c-reference"></a>() — operator (C# odwołania)

Oprócz określania kolejności operacji w wyrażeniach nawiasy są też używane do następujących zadań:

1. Określanie rzutowania lub konwersji typów.

    [!code-csharp[csRefOperators#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#1)]

2. Wywoływanie metody lub delegatów.

    [!code-csharp[csRefOperators#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#2)]

## <a name="remarks"></a>Uwagi

Rzutowanie jawnie wywołuje operatora konwersji z jednego typu do drugiego. Rzutowanie kończy się niepowodzeniem, jeśli żaden operator konwersji nie jest zdefiniowany. Aby zdefiniować operatora konwersji, zobacz [jawne](../keywords/explicit.md) i [niejawne](../keywords/implicit.md) definiowanie operatorów konwersji.

 Operator `()` nie może być przeciążony.

 Aby uzyskać więcej informacji, zobacz [Rzutowanie i konwersje typów](../../programming-guide/types/casting-and-type-conversions.md). 

 Aby uzyskać więcej informacji na temat wywołania metody, zobacz [metody](../../programming-guide/classes-and-structs/methods.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)