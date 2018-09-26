---
title: Base — słowo kluczowe (odwołanie w C#)
description: Więcej informacji na temat base — słowo kluczowe, które umożliwia dostęp do elementów członkowskich klasy bazowej z poziomu klasy pochodnej w języku C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 8719ab79273701173530760ad1bec837c4f4302d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/25/2018
ms.locfileid: "47077895"
---
# <a name="base-c-reference"></a>base (odwołanie w C#)

`base` Słowo kluczowe jest używane do dostępu do składowych klasy bazowej z poziomu klasy pochodnej:

- Wywołania metody w klasie bazowej, która została zastąpiona przy użyciu innej metody.

- Określ, powinna być wywoływana konstruktora klasy bazowej, podczas tworzenia wystąpień klasy pochodnej.

Dostęp klasy bazowej jest dozwolona tylko w konstruktorem, metodą wystąpienia lub metody dostępu właściwości wystąpienia.

Jest to błąd, aby użyć `base` — słowo kluczowe z wewnątrz metody statycznej.

Klasa bazowa, która jest dostępna jest klasa bazowa, określonym w deklaracji klasy. Na przykład, jeśli określisz `class ClassB : ClassA`, członkowie ClassA są dostępne z ClassB, niezależnie od tego, klasa bazowa ClassA.

## <a name="example"></a>Przykład

W tym przykładzie, zarówno klasy bazowej, `Person`i klasy pochodnej `Employee`, ma metodę o nazwie `Getinfo`. Za pomocą `base` — słowo kluczowe, jest możliwe do wywołania `Getinfo` metody w klasie bazowej, z poziomu klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Aby uzyskać więcej przykładów, zobacz [nowe](../../../csharp/language-reference/keywords/new.md), [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), i [zastąpienia](../../../csharp/language-reference/keywords/override.md).

## <a name="example"></a>Przykład

Ten przykład przedstawia sposób określania konstruktora klasy bazowej, wywoływana podczas tworzenia wystąpień klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
- [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
- [this](../../../csharp/language-reference/keywords/this.md)