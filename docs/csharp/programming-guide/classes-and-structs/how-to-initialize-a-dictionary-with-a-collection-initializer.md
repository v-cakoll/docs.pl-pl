---
title: Inicjowanie słownika z inicjatorem kolekcji — Przewodnik programowania w języku C#
description: Dowiedz się, jak zainicjować słownik w języku C# przy użyciu metody Add lub inicjatora indeksu. Ten przykład pokazuje obie opcje.
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 2f33240b02785c5c886a1ebebb8984d29c9f7795
ms.sourcegitcommit: 3d84eac0818099c9949035feb96bbe0346358504
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/21/2020
ms.locfileid: "86865050"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Inicjowanie słownika przy użyciu inicjatora kolekcji (Przewodnik programowania w języku C#)

A <xref:System.Collections.Generic.Dictionary%602> zawiera kolekcję par klucz/wartość. Jego <xref:System.Collections.Generic.Dictionary%602.Add%2A> Metoda przyjmuje dwa parametry — jeden dla klucza i jeden dla tej wartości. Jednym ze sposobów na zainicjowanie <xref:System.Collections.Generic.Dictionary%602> lub dowolna kolekcja, której `Add` Metoda przyjmuje wiele parametrów, jest ujęcie każdego zestawu parametrów w nawiasach klamrowych, jak pokazano w poniższym przykładzie. Innym rozwiązaniem jest użycie inicjatora indeksu, również w poniższym przykładzie.

## <a name="example"></a>Przykład

W poniższym przykładzie kodu element <xref:System.Collections.Generic.Dictionary%602> jest inicjowany z wystąpieniami typu `StudentName` .  Pierwsze inicjowanie używa `Add` metody z dwoma argumentami. Kompilator generuje wywołanie `Add` dla każdej pary `int` kluczy i `StudentName` wartości. Druga używa metody indeksu publicznego odczytu/zapisu `Dictionary` klasy:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Zwróć uwagę na dwie pary nawiasów klamrowych w każdym elemencie kolekcji w pierwszej deklaracji. Wewnętrzne nawiasy klamrowe otaczające inicjatora obiektów dla `StudentName` , a skrajne nawiasy klamrowe obejmują inicjator dla pary klucz/wartość, które zostaną dodane do `students` <xref:System.Collections.Generic.Dictionary%602> . Na koniec cały inicjator kolekcji dla słownika jest ujęty w nawiasy klamrowe. Podczas drugiego inicjowania po lewej stronie przypisania jest kluczem, a po prawej stronie jest wartością, przy użyciu inicjatora obiektu dla `StudentName` .

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md)
