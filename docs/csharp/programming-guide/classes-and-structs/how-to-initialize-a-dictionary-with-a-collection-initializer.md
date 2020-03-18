---
title: Jak zainicjować słownik z inicjatora kolekcji - C# Programming Guide
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 1e6e7fac9dd49ad1943ac9046bd9e4932c383257
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "75741368"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Jak zainicjować słownik z inicjatora kolekcji (C# Programming Guide)

A <xref:System.Collections.Generic.Dictionary%602> zawiera kolekcję par klucz/wartość. Jego <xref:System.Collections.Generic.Dictionary%602.Add%2A> metoda przyjmuje dwa parametry, jeden dla klucza i jeden dla wartości. Jednym ze sposobów zainicjowania <xref:System.Collections.Generic.Dictionary%602>lub dowolnej `Add` kolekcji, której metoda przyjmuje wiele parametrów, jest ująć każdy zestaw parametrów w nawiasy klamrowe, jak pokazano w poniższym przykładzie. Inną opcją jest użycie inicjatora indeksu, również pokazane w poniższym przykładzie.

## <a name="example"></a>Przykład

W poniższym przykładzie <xref:System.Collections.Generic.Dictionary%602> kodu a jest inicjowany `StudentName`z wystąpieniami typu .  Pierwsza inicjalizacja używa `Add` metody z dwoma argumentami. Kompilator generuje wywołanie `Add` dla każdej pary `int` kluczy i `StudentName` wartości. Drugi używa publicznej metody indeksatora `Dictionary` odczytu / zapisu klasy:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Należy zwrócić uwagę na dwie pary nawiasów klamrowych w każdym elemencie kolekcji w pierwszej deklaracji. Najbardziej wewnętrzne nawiasy klamrowe otaczają `StudentName`inicjatora obiektu dla , a najbardziej zewnętrzne nawiasy klamrowe otaczają inicjatora dla pary klucz/wartość, która zostanie dodana do `students` <xref:System.Collections.Generic.Dictionary%602>pliku . Na koniec inicjator całej kolekcji dla słownika jest ujęty w nawiasy klamrowe. W drugiej inicjalizacji po lewej stronie przypisania jest klucz, a po prawej `StudentName`stronie wartość, przy użyciu inicjatora obiektu dla .

## <a name="see-also"></a>Zobacz też

- [Przewodnik programowania języka C#](../index.md)
- [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md)
