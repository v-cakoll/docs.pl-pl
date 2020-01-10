---
title: podstawowe słowo kluczowe C# — odwołanie
description: Dowiedz się więcej o słowie kluczowym Base, które służy do uzyskiwania dostępu do elementów członkowskich klasy bazowej z C#poziomu klasy pochodnej w.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75713769"
---
# <a name="base-c-reference"></a>base (odwołanie w C#)

Słowo kluczowe `base` służy do uzyskiwania dostępu do składowych klasy bazowej z poziomu klasy pochodnej:

- Wywołaj metodę w klasie bazowej, która została zastąpiona przez inną metodę.

- Określ, który Konstruktor klasy bazowej powinien być wywoływany podczas tworzenia wystąpień klasy pochodnej.

Dostęp do klasy podstawowej jest dozwolony tylko w konstruktorze, metodzie wystąpienia lub akcesorze właściwości wystąpienia.

Wystąpił błąd, aby użyć słowa kluczowego `base` z metody statycznej.

Dostępną klasą bazową jest klasa bazowa określona w deklaracji klasy. Na przykład jeśli określisz `class ClassB : ClassA`, członkowie ClassA są dostępni z ClassB, niezależnie od klasy bazowej ClassA.

## <a name="example"></a>Przykład

W tym przykładzie zarówno Klasa bazowa, `Person`, jak i Klasa pochodna, `Employee`, mają metodę o nazwie `Getinfo`. Za pomocą słowa kluczowego `base` można wywołać metodę `Getinfo` w klasie bazowej z poziomu klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Aby uzyskać więcej przykładów, zobacz [nowe](new-modifier.md), [wirtualne](virtual.md)i [przesłonięcie](override.md).

## <a name="example"></a>Przykład

Ten przykład pokazuje, jak określić Konstruktor klasy bazowej wywoływany podczas tworzenia wystąpień klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz także

- [Dokumentacja języka C#](../index.md)
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [this](./this.md)
