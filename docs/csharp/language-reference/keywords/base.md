---
title: base (odwołanie w C#)
description: Więcej informacji na temat base — słowo kluczowe, która umożliwia dostęp do elementów członkowskich klasy podstawowej z w klasie pochodnej w języku C#.
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
caps.latest.revision: 14
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 1bbaa0cc05b35f822113bc3a8c3cde966b1484ef
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
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
 [Ten](../../../csharp/language-reference/keywords/this.md)