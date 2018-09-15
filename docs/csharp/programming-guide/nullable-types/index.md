---
title: Typy dopuszczające wartości zerowe (C# Programming Guide)
description: Informacje na temat typów dopuszczających wartości zerowe C# i sposobu ich używania
ms.date: 07/30/2018
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: 2af0704abcad00c75a5d40bfe2d0523d07ee6a3f
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/15/2018
ms.locfileid: "45658707"
---
# <a name="nullable-types-c-programming-guide"></a>Typy dopuszczające wartości zerowe (C# Programming Guide)

Typy dopuszczające wartości null są wystąpieniami <xref:System.Nullable%601?displayProperty=nameWithType> struktury. Typy dopuszczające wartość null może reprezentować wszystkie wartości typu bazowego `T`wraz z dodatkowymi [null](../../language-reference/keywords/null.md) wartość. Typ podstawowy `T` może być dowolne niedopuszczający [typu wartości](../../language-reference/keywords/value-types.md). `T` nie może być typem referencyjnym.

Na przykład możesz przypisać `null` lub dowolnej wartości liczby całkowitej z <xref:System.Int32.MinValue?displayProperty=nameWithType> do <xref:System.Int32.MaxValue?displayProperty=nameWithType> do `Nullable<int>` i [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), lub `null` do `Nullable<bool>`.

Używasz typu dopuszczającego wartość null, jeśli potrzebujesz do reprezentowania niezdefiniowane wartości typu podstawowego. Wartość logiczna może mieć tylko dwie wartości: true i false. Nie ma żadnej wartości "undefined". W wielu aplikacjach programowania głównie interakcji bazy danych, wartość zmiennej może być niezdefiniowana lub jego brak. Na przykład pola w bazie danych może zawierać wartości true lub false lub może zawierać żadnej wartości w ogóle. Możesz użyć `Nullable<bool>` typu w takiej sytuacji.

Typy dopuszczające wartości zerowe mają następującą charakterystykę:
  
- Typy dopuszczające wartości zerowe reprezentują zmienne typu wartości, które można przypisać `null` wartość. Nie można utworzyć typu dopuszczającego wartość null, w oparciu o typ odwołania. (Już obsługuje typy odwołań `null` wartości.)  
  
- Składnia `T?` jest skrótem `Nullable<T>`. Dwa formularze są wymienne.  
  
- Przypisania wartości do typu dopuszczającego wartość null, tak samo jak dla podstawowego typu wartości: `int? x = 10;` lub `double? d = 4.108;`. Możesz również przypisać `null` wartość: `int? x = null;`.  
  
- Użyj <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> i <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> właściwości tylko do odczytu, aby sprawdzić wartość null i pobierać wartości, jak pokazano w poniższym przykładzie: `if (x.HasValue) y = x.Value;`  
  
  - <xref:System.Nullable%601.HasValue%2A> Właściwość zwraca `true` Jeśli zmienna zawiera wartość, lub `false` , gdy jest `null`.
  
  - <xref:System.Nullable%601.Value%2A> Właściwość zwraca wartość, jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `true`. W przeciwnym razie <xref:System.InvalidOperationException> zgłaszany.  
  
- Można również użyć `==` i `!=` operatory o typu dopuszczającego wartość null, jak pokazano w poniższym przykładzie: `if (x != null) y = x.Value;`. Jeśli `a` i `b` są ma wartość null, `a == b` daje w wyniku `true`.  

- Począwszy od języka C# 7.0, można użyć [dopasowywania do wzorca](../../pattern-matching.md#the-is-type-pattern-expression) do zbadania i Pobierz wartość typu dopuszczającego wartość null: `if (x is int valueOfX) y = valueOfX;`.
  
- Wartość domyślna `T?` jest wystąpieniem którego <xref:System.Nullable%601.HasValue%2A> właściwość zwraca `false`.  

- Użyj <xref:System.Nullable%601.GetValueOrDefault> metodę, aby zwrócić albo przypisaną wartość, lub [domyślne](../../language-reference/keywords/default-values-table.md) wartość bazowego typu wartości, jeśli wartość typu dopuszczającego wartość null jest `null`.  

- Użyj <xref:System.Nullable%601.GetValueOrDefault(%600)> metody do zwrócenia przypisaną wartość lub wartość domyślną podany, jeśli wartość typu dopuszczającego wartość null jest `null`.
  
- Użyj [operatorem łączenia wartości null](../../language-reference/operators/null-coalescing-operator.md), `??`, aby przypisać wartość do typu podstawowego, na podstawie wartości typu dopuszczającego wartość null: `int? x = null; int y = x ?? -1;`. W tym przykładzie ponieważ `x` jest null, wartość wyniku `y` jest `-1`.

- Jeśli nie zdefiniowano konwersji zdefiniowanej przez użytkownika między dwoma typami danych, tej samej konwersji można również z tych typów danych w wersji dopuszczającego wartość null.
  
- Zagnieżdżone typy dopuszczające wartości null są niedozwolone. Kompilacji nie następujący wiersz: `Nullable<Nullable<int>> n;`  

Aby uzyskać więcej informacji, zobacz [przy użyciu typów dopuszczających wartości zerowe](using-nullable-types.md) i [porady: Identyfikowanie typu dopuszczającego wartość null](how-to-identify-a-nullable-type.md) tematów.
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Nullable%601?displayProperty=nameWithType>  
- <xref:System.Nullable?displayProperty=nameWithType>  
- [??, operator](../../language-reference/operators/null-coalescing-operator.md)  
- [Przewodnik programowania w języku C#](../index.md)  
- [Przewodnik dla języka C#](../../index.md)  
- [Dokumentacja języka C#](../../language-reference/index.md)  
- [Typy o wartości zerowalnej (Visual Basic)](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)  
