---
title: podstawowe słowo kluczowe C# — odwołanie
ms.custom: seodec18
description: Dowiedz się więcej o słowie kluczowym Base, które służy do uzyskiwania dostępu do elementów członkowskich klasy bazowej z C#poziomu klasy pochodnej w.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: b882a8d1e5979ac184d184be379dd76f7bf3600f
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69602256"
---
# <a name="base-c-reference"></a>base (odwołanie w C#)

`base` Słowo kluczowe jest używane do uzyskiwania dostępu do składowych klasy bazowej z poziomu klasy pochodnej:

- Wywołaj metodę w klasie bazowej, która została zastąpiona przez inną metodę.

- Określ, który Konstruktor klasy bazowej powinien być wywoływany podczas tworzenia wystąpień klasy pochodnej.

Dostęp do klasy podstawowej jest dozwolony tylko w konstruktorze, metodzie wystąpienia lub akcesorze właściwości wystąpienia.

Wystąpił błąd przy użyciu `base` słowa kluczowego z metody statycznej.

Dostępną klasą bazową jest klasa bazowa określona w deklaracji klasy. Na przykład, jeśli określisz `class ClassB : ClassA`, członkowie ClassA są dostępni z ClassB, niezależnie od klasy bazowej ClassA.

## <a name="example"></a>Przykład

W tym przykładzie zarówno Klasa bazowa, `Person`, jak i `Employee`Klasa pochodna, mają metodę o nazwie `Getinfo`. Za pomocą `base` słowa kluczowego, można `Getinfo` wywołać metodę w klasie bazowej, z poziomu klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Aby uzyskać więcej przykładów, zobacz [nowe](new-modifier.md), [wirtualne](virtual.md)i [](override.md)przesłonięcie.

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
