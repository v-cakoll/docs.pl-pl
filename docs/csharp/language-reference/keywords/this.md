---
title: to słowo kluczowe — odwołanie do języka C#
description: to słowo kluczowe (Odwołanie do języka C#)
ms.date: 07/20/2015
f1_keywords:
- this
- this_CSharpKeyword
helpviewer_keywords:
- this keyword [C#]
ms.assetid: d4f827fe-4710-410b-89b8-867dad44b8a3
ms.openlocfilehash: 2a2c487ad93e6fc75ecf95c541e859b8b60bb5b5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75715108"
---
# <a name="this-c-reference"></a>this (odwołanie w C#)

Słowo `this` kluczowe odnosi się do bieżącego wystąpienia klasy i jest również używany jako modyfikator pierwszego parametru metody rozszerzenia.

> [!NOTE]
> W tym artykule omówiono użycie z `this` wystąpieniami klasy. Aby uzyskać więcej informacji na temat jego użycia w metodach [rozszerzeń,](../../programming-guide/classes-and-structs/extension-methods.md)zobacz Metody rozszerzenia .

Oto typowe `this`zastosowania:

- Aby zakwalifikować członków ukrytych pod podobnymi nazwami, na przykład:

  [!code-csharp[csrefKeywordsAccess#4](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#4)]  

- Aby przekazać obiekt jako parametr do innych metod, na przykład:

  ```csharp
  CalcTax(this);
  ```

- Aby zadeklarować indeksatory, na przykład:

  [!code-csharp[csrefKeywordsAccess#5](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#5)]

Funkcje statyczne elementu członkowskiego, ponieważ istnieją na poziomie klasy, a `this` nie jako część obiektu, nie mają wskaźnika. Jest to błąd, `this` do wyniku do niego w metodzie statycznej.

## <a name="example"></a>Przykład

W tym `this` przykładzie jest używany `Employee` do `name` zakwalifikowania członków klasy i `alias`, które są ukryte pod podobnymi nazwami. Jest również używany do przekazywania obiektu `CalcTax`do metody , która należy do innej klasy.

[!code-csharp[csrefKeywordsAccess#3](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#3)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](index.md)
- [base](base.md)
- [Metody](../../programming-guide/classes-and-structs/methods.md)
