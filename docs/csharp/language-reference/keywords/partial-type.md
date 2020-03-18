---
title: typ częściowy — odwołanie do języka C#
ms.date: 07/20/2015
f1_keywords:
- partialtype
- partialtype_CSharpKeyword
helpviewer_keywords:
- partial types [C#]
ms.assetid: 27320743-a22e-4c7b-b0b3-53afe3607334
ms.openlocfilehash: 551145b9cdf5fa24f3ae365665e8ff06cf5e9307
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715208"
---
# <a name="partial-type-c-reference"></a>typ częściowy (odwołanie do języka C#)

Definicje typów częściowych umożliwiają podzielenie definicji klasy, struktury lub interfejsu na wiele plików.

W *File1.cs:*

[!code-csharp[csrefKeywordsContextual#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#3)]  

W *File2.cs* deklaracja:

[!code-csharp[csrefKeywordsContextual#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsContextual/CS/csrefKeywordsContextual.cs#4)]  

## <a name="remarks"></a>Uwagi

Dzielenie typu klasy, struktury lub interfejsu na kilka plików może być przydatne podczas pracy z dużymi projektami lub z automatycznie generowanym kodem, takim jak ten dostarczony przez [Projektanta formularzy systemu Windows](../../../framework/winforms/controls/developing-windows-forms-controls-at-design-time.md). Typ częściowy może zawierać [metodę częściową](partial-method.md). Aby uzyskać więcej informacji, zobacz [Klasy częściowe i metody](../../programming-guide/classes-and-structs/partial-classes-and-methods.md).

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Modyfikatory](index.md)
- [Wprowadzenie do typów ogólnych](../../programming-guide/generics/index.md)
