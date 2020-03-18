---
title: podstawowe słowo kluczowe - Odwołanie do języka C#
description: Dowiedz się więcej o podstawowym senie kluczowym, które służy do uzyskiwania dostępu do członków klasy podstawowej z poziomu klasy pochodnej w języku C#.
ms.date: 07/20/2015
f1_keywords:
- base
- BaseClass.BaseClass
- base_CSharpKeyword
helpviewer_keywords:
- base keyword [C#]
ms.assetid: 8b645dbe-1a33-49b8-8716-1c401f9a5ea5
ms.openlocfilehash: a4686fc5d4245a50de5d77dc0e71c231772f40ef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75713769"
---
# <a name="base-c-reference"></a>base (odwołanie w C#)

Słowo `base` kluczowe służy do uzyskiwania dostępu do elementów członkowskich klasy podstawowej z poziomu klasy pochodnej:

- Wywołaj metodę w klasie podstawowej, która została zastąpiona przez inną metodę.

- Określ, który konstruktor klasy podstawowej powinien być wywoływany podczas tworzenia wystąpień klasy pochodnej.

Dostęp klasy podstawowej jest dozwolone tylko w konstruktora, metody wystąpienia lub akcesor właściwości wystąpienia.

Jest to błąd, `base` aby użyć słowa kluczowego z wewnątrz metody statycznej.

Klasa podstawowa, która jest dostępna jest klasa podstawowa określona w deklaracji klasy. Na przykład, jeśli `class ClassB : ClassA`określisz, członkowie ClassA są dostępne z ClassB, niezależnie od klasy podstawowej ClassA.

## <a name="example"></a>Przykład

W tym przykładzie zarówno klasa `Person`podstawowa, jak `Employee`i klasa pochodna , mają metodę o nazwie `Getinfo`. Za pomocą `base` słowa kluczowego, można `Getinfo` wywołać metodę na klasie podstawowej, z poziomu klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#1](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#1)]

Aby uzyskać dodatkowe przykłady, zobacz [nowe](new-modifier.md), [wirtualne](virtual.md)i [zastąp](override.md).

## <a name="example"></a>Przykład

W tym przykładzie pokazano, jak określić konstruktora klasy podstawowej wywoływane podczas tworzenia wystąpień klasy pochodnej.

[!code-csharp[csrefKeywordsAccess#2](~/samples/snippets/csharp/VS_Snippets_VBCSharp/csrefKeywordsAccess/CS/csrefKeywordsAccess.cs#2)]

## <a name="c-language-specification"></a>specyfikacja języka C#

[!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]

## <a name="see-also"></a>Zobacz też

- [Odwołanie do języka C#](../index.md)
- [Przewodnik programowania języka C#](../../programming-guide/index.md)
- [Słowa kluczowe języka C#](./index.md)
- [względem tego ruchu](./this.md)
