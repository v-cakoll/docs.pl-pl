---
title: '- Operator - C# odwołania'
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- -_CSharpKeyword
helpviewer_keywords:
- '- operator [C#]'
- subtraction operator (-) [C#]
ms.assetid: 4de7a4fa-c69d-48e6-aff1-3130af970b2d
ms.openlocfilehash: 8cf6e8871a88e2b37b9531ecbd616289523473c7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61688803"
---
# <a name="--operator-c-reference"></a>-— operator (C# odwołania)

`-` Operator może działać jako jednoargumentowy lub binarny.

## <a name="remarks"></a>Uwagi

Jednoargumentowy `-` operatory są wstępnie zdefiniowane dla wszystkich typów liczbowych. Wynik jednoargumentowy `-` operacja na typ liczbowy jest liczbowe negacji operandu.

Binarny `-` operatory są wstępnie zdefiniowane dla wszystkich typów liczbowych i wyliczenia na potrzeby odejmowania drugiego operandu od pierwszego.

Typy delegatów udostępniają dane binarne `-` operatora, który wykonuje usuwanie delegata.

Typy zdefiniowane przez użytkownika może doprowadzić do przeciążenia jednoargumentowe `-` binarnej i `-` operatorów. Aby uzyskać więcej informacji, zobacz [operator — słowo kluczowe](../keywords/operator.md).

## <a name="example"></a>Przykład

[!code-csharp[csRefOperators#40](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefOperators/CS/csrefOperators.cs#40)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Operatory języka C#](index.md)