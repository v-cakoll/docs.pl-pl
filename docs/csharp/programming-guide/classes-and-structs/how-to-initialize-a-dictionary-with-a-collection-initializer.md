---
title: Inicjowanie słownika z inicjatorem kolekcji — C# Przewodnik programowania
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: 1e6e7fac9dd49ad1943ac9046bd9e4932c383257
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/08/2020
ms.locfileid: "75741368"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Inicjowanie słownika przy użyciu inicjatora kolekcji (C# Przewodnik programowania)

<xref:System.Collections.Generic.Dictionary%602> zawiera kolekcję par klucz/wartość. Jego <xref:System.Collections.Generic.Dictionary%602.Add%2A> Metoda przyjmuje dwa parametry, jeden dla klucza i jeden dla wartości. Jednym ze sposobów inicjowania <xref:System.Collections.Generic.Dictionary%602>lub dowolnej kolekcji, której `Add` Metoda przyjmuje wiele parametrów, jest ujęcie każdego zestawu parametrów w nawiasach klamrowych, jak pokazano w poniższym przykładzie. Innym rozwiązaniem jest użycie inicjatora indeksu, również w poniższym przykładzie.

## <a name="example"></a>Przykład

W poniższym przykładzie kodu <xref:System.Collections.Generic.Dictionary%602> jest inicjowany z wystąpieniami typu `StudentName`.  Pierwsze inicjowanie używa metody `Add` z dwoma argumentami. Kompilator generuje wywołanie do `Add` dla każdej pary kluczy `int` i `StudentName` wartości. Druga używa metody indeksu publicznego odczytu/zapisu klasy `Dictionary`:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Zwróć uwagę na dwie pary nawiasów klamrowych w każdym elemencie kolekcji w pierwszej deklaracji. Wewnętrzne nawiasy klamrowe otaczające inicjatora obiektów dla `StudentName`, a skrajne nawiasy klamrowe obejmują inicjator pary klucz/wartość, które zostaną dodane do <xref:System.Collections.Generic.Dictionary%602>`students`. Na koniec cały inicjator kolekcji dla słownika jest ujęty w nawiasy klamrowe. Podczas drugiego inicjowania po lewej stronie przypisania jest kluczem, a po prawej stronie jest wartością, przy użyciu inicjatora obiektów dla `StudentName`.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../index.md)
- [Inicjatory obiektów i kolekcji](./object-and-collection-initializers.md)
