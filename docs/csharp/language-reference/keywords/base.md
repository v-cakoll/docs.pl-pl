---
title: base (odwołanie w C#)
description: Więcej informacji na temat base — słowo kluczowe, która umożliwia dostęp do elementów członkowskich klasy podstawowej z w klasie pochodnej w języku C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: 69885ba0b2d05c79f2b7ba9458e7ba8c8b7aa0c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33214484"
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

[!code-csharp[csrefKeywordsAccess#1](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_1.cs)]

Dodatkowe przykłady można znaleźć [nowe](../../../csharp/language-reference/keywords/new.md), [wirtualnego](../../../csharp/language-reference/keywords/virtual.md), i [zastąpienia](../../../csharp/language-reference/keywords/override.md).

## <a name="example"></a>Przykład
Ten przykład przedstawia sposób określenia konstruktora klasy podstawowej, wywoływana podczas tworzenia wystąpień klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#2](../../../csharp/language-reference/keywords/codesnippet/CSharp/base_2.cs)]

## <a name="c-language-specification"></a>specyfikacja języka C#
[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Słowa kluczowe języka C#](../../../csharp/language-reference/keywords/index.md)  
 [this](../../../csharp/language-reference/keywords/this.md)