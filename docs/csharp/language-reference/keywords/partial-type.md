---
title: Typ częściowej — C# odwołania
ms.custom: seodec18
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 5dba3759d8d0046f2a491e1d3408acb54bd0343d
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/15/2019
ms.locfileid: "65633372"
---
# <a name="partial-type-c-reference"></a>typu częściowego (odwołanie w C#)

Definicje typu częściowego umożliwiają definicji klasy, struktury lub interfejsu ma być podzielony na wiele plików.

W *File1.cs*:

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

W *File2.cs* deklaracji:

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Uwagi

Podział klasy, struktury lub interfejsu typ za pośrednictwem kilku plików może być przydatny podczas pracy z dużymi projektami lub z automatycznie wygenerowanego kodu, takim jak udostępniany przez [Windows Forms Designer](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md). Może zawierać typu częściowego [metody częściowej](partial-method.md). Aby uzyskać więcej informacji, zobacz [klasy częściowe i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Modyfikatory](modifiers.md)
- [Wprowadzenie do typów ogólnych](../../programming-guide/generics/introduction-to-generics.md)
