---
title: Jak inicjowanie słownika przy użyciu inicjatora kolekcji - C# Programming Guide
ms.custom: seodec18
ms.date: 12/20/2018
helpviewer_keywords:
- collection initializers [C#], with Dictionary
ms.assetid: 25283922-f8ee-40dc-a639-fac30804ec71
ms.openlocfilehash: bab2c4c996f7780cec572d58eb572a90aeea592a
ms.sourcegitcommit: 4c41ec195caf03d98b7900007c3c8e24eba20d34
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/20/2019
ms.locfileid: "67267668"
---
# <a name="how-to-initialize-a-dictionary-with-a-collection-initializer-c-programming-guide"></a>Jak inicjowanie słownika przy użyciu inicjatora kolekcji (C# Programming Guide)

Element <xref:System.Collections.Generic.Dictionary%602> zawiera kolekcję par klucz/wartość. Jego <xref:System.Collections.Generic.Dictionary%602.Add*> metoda przyjmuje dwa parametry: jeden dla klucza i jeden dla wartości. Jednym ze sposobów, aby zainicjować <xref:System.Collections.Generic.Dictionary%602>, lub dowolnej kolekcji którego `Add` metoda przyjmuje kilka parametrów, jest ujęcie każdego zestawu parametrów w nawiasach klamrowych, jak pokazano w poniższym przykładzie. Innym rozwiązaniem jest używać inicjatora indeksu także pokazano w poniższym przykładzie.

## <a name="example"></a>Przykład

W poniższym przykładzie kodu <xref:System.Collections.Generic.Dictionary%602> jest inicjowany za pomocą wystąpienia typu `StudentName`.  Używa pierwszego inicjowania `Add` metody za pomocą dwóch argumentów. Kompilator generuje wywołanie `Add` dla każdej pary `int` kluczy i `StudentName` wartości. Drugi używa publicznego odczytu i zapisu metody indeksatora `Dictionary` klasy:

[!code-csharp[InitializerExample](../../../../samples/snippets/csharp/programming-guide/classes-and-structs/object-collection-initializers/HowToDictionaryInitializer.cs#HowToDictionaryInitializer)]  

Należy pamiętać, dwie pary nawiasów klamrowych w każdym elemencie kolekcji w pierwszej deklaracji. Najbardziej nawiasów klamrowych, należy ująć Inicjator obiektu `StudentName`, i najbardziej zewnętrznej nawiasów klamrowych ująć inicjator dla pary klucz/wartość, która zostanie dodana do `students` <xref:System.Collections.Generic.Dictionary%602>. Na koniec całej kolekcji inicjatora słownika jest ujęte w nawiasy klamrowe. W drugim inicjowania po lewej stronie przypisania jest kluczem i po prawej stronie jest wartością, za pomocą inicjatora obiektów dla `StudentName`.

## <a name="see-also"></a>Zobacz także

- [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)
- [Inicjatory obiektów i kolekcji](../../../csharp/programming-guide/classes-and-structs/object-and-collection-initializers.md)
