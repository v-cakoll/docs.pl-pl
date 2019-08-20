---
title: Inicjowanie słownika z inicjatorem kolekcji — C# Przewodnik programowania
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 22f80365b974df66999ac68f7bc2a9ffa7d445a5
ms.sourcegitcommit: 986f836f72ef10876878bd6217174e41464c145a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/19/2019
ms.locfileid: "69596814"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Inicjowanie słownika przy użyciu inicjatora kolekcji (C# Przewodnik programowania)

A <xref:System.Collections.Generic.Dictionary%602> zawiera kolekcję par klucz/wartość. Jego <xref:System.Collections.Generic.Dictionary%602.Add*> Metoda przyjmuje dwa parametry — jeden dla klucza i jeden dla tej wartości. Jednym ze sposobów na zainicjowanie <xref:System.Collections.Generic.Dictionary%602>lub dowolna kolekcja, której `Add` Metoda przyjmuje wiele parametrów, jest ujęcie każdego zestawu parametrów w nawiasach klamrowych, jak pokazano w poniższym przykładzie. Innym rozwiązaniem jest użycie inicjatora indeksu, również w poniższym przykładzie.

## <a name="example"></a>Przykład

W poniższym przykładzie kodu element <xref:System.Collections.Generic.Dictionary%602> jest inicjowany z wystąpieniami typu. `StudentName`  Pierwsze inicjowanie używa `Add` metody z dwoma argumentami. Kompilator generuje wywołanie `Add` dla każdej `int` pary kluczy i `StudentName` wartości. Druga używa metody `Dictionary` indeksu publicznego odczytu/zapisu klasy:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Zwróć uwagę na dwie pary nawiasów klamrowych w każdym elemencie kolekcji w pierwszej deklaracji. Wewnętrzne nawiasy klamrowe otaczające inicjatora obiektów dla `StudentName`, a skrajne nawiasy klamrowe obejmują inicjator dla pary klucz/wartość, które zostaną dodane `students` <xref:System.Collections.Generic.Dictionary%602>do. Na koniec cały inicjator kolekcji dla słownika jest ujęty w nawiasy klamrowe. Podczas drugiego inicjowania po lewej stronie przypisania jest kluczem, a po prawej stronie jest wartością, przy użyciu inicjatora obiektu dla `StudentName`.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md)
