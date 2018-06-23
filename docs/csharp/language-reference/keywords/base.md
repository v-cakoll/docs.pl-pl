---
title: Base — słowo kluczowe (odwołanie w C#)
description: Więcej informacji na temat base — słowo kluczowe, która umożliwia dostęp do elementów członkowskich klasy podstawowej z w klasie pochodnej w języku C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 94bfcbacd8c222004c1a013cc855ac8d46aab05f
ms.sourcegitcommit: c217b067985905cb21eafc5dd9a83568d7ff4e45
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/22/2018
ms.locfileid: "36314662"
---
# <a name="base-c-reference"></a>base (odwołanie w C#)

`base` Umożliwia dostęp do elementów członkowskich klasy podstawowej z w klasie pochodnej — słowo kluczowe:

- Wywołanie metody w klasie podstawowej, która już została zastąpiona przy użyciu innej metody.

- Określ, które konstruktora klasy podstawowej powinna być wywoływana podczas tworzenia wystąpień klasy pochodnej.

Dostęp klasa podstawowa jest dozwolony tylko w konstruktorze, metody wystąpienia lub metody dostępu właściwości wystąpienia.

Jest błędem `base` — słowo kluczowe z wewnątrz metody statycznej.

Klasa podstawowa, który jest dostępny jest klasą bazową określony w deklaracji klasy. Na przykład jeśli określisz `class ClassB : ClassA`, członkowie ClassA są dostępne z ClassB, niezależnie od tego, w klasie podstawowej ClassA.

## <a name="example"></a>Przykład

W tym przykładzie zarówno klasę podstawową, `Person`i klasy pochodnej `Employee`, ma metodę o nazwie `Getinfo`. Za pomocą `base` — słowo kluczowe, jest możliwe do wywołania `Getinfo` metody w klasie podstawowej, za pomocą klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Dodatkowe przykłady można znaleźć [nowe](../../../csharp/language-reference/keywords/new.md), [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), i [zastąpienia](../../../csharp/language-reference/keywords/override.md).

## <a name="example"></a>Przykład

Ten przykład przedstawia sposób określenia konstruktora klasy podstawowej, wywoływana podczas tworzenia wystąpień klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

[Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
[Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
[Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
[this](../../../csharp/language-reference/keywords/this.md)