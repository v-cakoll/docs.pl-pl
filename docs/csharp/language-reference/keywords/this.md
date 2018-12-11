---
title: this — słowo kluczowe (odwołanie w C#)
description: this — słowo kluczowe (odwołanie w C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 52e7fce0ebeeccfbf5f56dbbcade9fae2890dfe1
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53130823"
---
# <a name="this-c-reference"></a>this (odwołanie w C#)

`this` — Słowo kluczowe odwołuje się do bieżącego wystąpienia klasy, a także jest używane jako modyfikator pierwszy parametr metody rozszerzenia.

> [!NOTE]
> W tym artykule omówiono używanie `this` przy użyciu wystąpienia klasy. Aby uzyskać więcej informacji na temat jej użycia w metody rozszerzenia zobacz [metody rozszerzenia](../../../csharp/programming-guide/classes-and-structs/extension-methods.md).

Poniżej znajdują się najczęstsze zastosowania usługi `this`:

- Aby zakwalifikować się elementy członkowskie ukrywane podobnych nazwach, na przykład:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Aby przekazać obiekt jako parametr do innych metod, na przykład:

  ```csharp
  CalcTax(this);
  ```

- Aby zadeklarować indeksatorów, na przykład:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Statyczne funkcje Członkowskie, ponieważ istnieją na poziomie klasy, a nie jako część obiektu, nie masz `this` wskaźnika. Jest to błąd do odwoływania się do `this` w metodzie statycznej.

## <a name="example"></a>Przykład

W tym przykładzie `this` są używane do kwalifikowania `Employee` składowych, klasy `name` i `alias`, które są ukrywane o podobnych nazwach. Służy również przekazać obiekt do metody `CalcTax`, która należy do innej klasy.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [base](base.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
