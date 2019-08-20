---
title: This — odwołanie C# do tego słowa kluczowego
ms.custom: seodec18
description: this — słowoC# kluczowe (odwołanie)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 4a3342e73fef3effd54f72e68283eb6085eef5b5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69608443"
---
# <a name="this-c-reference"></a>this (odwołanie w C#)

`this` Słowo kluczowe odwołuje się do bieżącego wystąpienia klasy i jest również używane jako modyfikator pierwszego parametru metody rozszerzenia.

> [!NOTE]
> W tym artykule omówiono użycie `this` z wystąpieniami klas. Aby uzyskać więcej informacji o używaniu metod rozszerzających, zobacz [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

Poniżej przedstawiono typowe zastosowania `this`:

- Aby zakwalifikować członków ukrytych przy użyciu podobnych nazw, na przykład:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Aby przekazać obiekt jako parametr do innych metod, na przykład:

  ```csharp
  CalcTax(this);
  ```

- Aby zadeklarować indeksatory, na przykład:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Statyczne funkcje członkowskie, ponieważ istnieją na poziomie klasy, a nie jako część obiektu, nie mają `this` wskaźnika. Wystąpił błąd podczas odwoływania się `this` do w metodzie statycznej.

## <a name="example"></a>Przykład

W tym przykładzie `this` jest używany do `Employee` kwalifikowania elementów członkowskich `name` klasy i `alias`, które są ukryte przez podobne nazwy. Jest on również używany do przekazywania obiektu do metody `CalcTax`, która należy do innej klasy.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [base](base.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
