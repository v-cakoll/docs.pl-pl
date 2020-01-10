---
title: This — odwołanie C# do tego słowa kluczowego
description: this — słowoC# kluczowe (odwołanie)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715108"
---
# <a name="this-c-reference"></a>this (odwołanie w C#)

Słowo kluczowe `this` odwołuje się do bieżącego wystąpienia klasy i jest również używane jako modyfikator pierwszego parametru metody rozszerzenia.

> [!NOTE]
> W tym artykule omówiono sposób użycia `this` z wystąpieniami klas. Aby uzyskać więcej informacji o używaniu metod rozszerzających, zobacz [metody rozszerzenia](../../programming-guide/classes-and-structs/extension-methods.md).

Poniżej przedstawiono typowe zastosowania `this`:

- Aby zakwalifikować członków ukrytych przy użyciu podobnych nazw, na przykład:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Aby przekazać obiekt jako parametr do innych metod, na przykład:

  ```csharp
  CalcTax(this);
  ```

- Aby zadeklarować indeksatory, na przykład:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Statyczne funkcje członkowskie, ponieważ istnieją na poziomie klasy, a nie jako część obiektu, nie mają wskaźnika `this`. Wystąpił błąd podczas odwoływania się do `this` w metodzie statycznej.

## <a name="example"></a>Przykład

W tym przykładzie `this` jest używany do kwalifikowania `Employee` członków klasy, `name` i `alias`, które są ukryte przez podobne nazwy. Jest on również używany do przekazywania obiektu do metody `CalcTax`, która należy do innej klasy.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [base](base.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
