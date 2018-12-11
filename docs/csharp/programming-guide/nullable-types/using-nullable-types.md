---
title: Przy użyciu typów dopuszczających wartości zerowe — C# Programming Guide
ms.custom: seodec18
description: Dowiedz się, jak pracować z typami zerowalnymi C#
ms.date: 08/02/2018
helpviewer_keywords:
- nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
ms.openlocfilehash: d2c6f2f78ed71558b71adcc1d4d8cc9a6f459d75
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235218"
---
# <a name="using-nullable-types-c-programming-guide"></a>Przy użyciu typów dopuszczających wartości zerowe (C# Programming Guide)

Typy dopuszczające wartości zerowe są typami, które reprezentują wartości typu podstawowego wartość `T`wraz z dodatkowymi [null](../../language-reference/keywords/null.md) wartość. Aby uzyskać więcej informacji, zobacz [typów dopuszczających wartości zerowe](index.md) tematu.

Możesz zapoznać się z typu dopuszczającego wartość null w dowolnej z następujących form: `Nullable<T>` lub `T?`. Te dwa formularze są wymienne.  
  
## <a name="declaration-and-assignment"></a>Deklarację i przypisanie

Zgodnie z typem wartości mogą być niejawnie konwertowane na odpowiedni typ dopuszczający wartość null, podobnie jak w przypadku jej typ podstawowy wartość możesz przypisać wartości do typu dopuszczającego wartość null. Możesz również przypisać `null` wartość.  Na przykład:
  
[!code-csharp[declare and assign](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#1)]

## <a name="examination-of-a-nullable-type-value"></a>Badanie wartości typu dopuszczającego wartość null

Użyj następujących właściwości tylko do odczytu do badania wystąpienie typu dopuszczającego wartość null w przypadku wartości null i pobierania wartości typu podstawowego:  
  
- <xref:System.Nullable%601.HasValue%2A?displayProperty=nameWithType> Wskazuje, czy wystąpienie typu dopuszczającego wartość null, ma wartość jego typ podstawowy.
  
- <xref:System.Nullable%601.Value%2A?displayProperty=nameWithType> pobiera wartość typu podstawowego, jeśli <xref:System.Nullable%601.HasValue%2A> jest `true`. Jeśli <xref:System.Nullable%601.HasValue%2A> jest `false`, <xref:System.Nullable%601.Value%2A> zgłasza właściwości <xref:System.InvalidOperationException>.
  
W kodzie w poniższym przykładzie użyto `HasValue` właściwości, aby sprawdzić, czy zmienna zawiera wartość, przed wyświetleniem go:
  
[!code-csharp-interactive[use HasValue](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#2)]
  
Można również porównać zmienną typu dopuszczającego wartość null z `null` zamiast `HasValue` właściwości, co ilustruje poniższy przykład:  
  
[!code-csharp-interactive[use comparison with null](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#3)]

Począwszy od języka C# 7.0, można użyć [dopasowywania do wzorca](../../pattern-matching.md) do zbadania i Pobierz wartość typu dopuszczającego wartość null:

[!code-csharp-interactive[use pattern matching](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#4)]

## <a name="conversion-from-a-nullable-type-to-an-underlying-type"></a>Konwersja z typu dopuszczającego wartość null na typ podstawowy

Jeśli musisz przypisać do typów innych niż NULL wartość typu dopuszczającego wartość null, użyj [operatorem łączenia wartości null `??` ](../../language-reference/operators/null-coalescing-operator.md) określić wartość do przypisania, jeśli wartość typu dopuszczającego wartość null jest równa null (możesz też użyć <xref:System.Nullable%601.GetValueOrDefault(%600)?displayProperty=nameWithType> celu metodę który):
  
[!code-csharp-interactive[?? operator](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#5)]

Użyj <xref:System.Nullable%601.GetValueOrDefault?displayProperty=nameWithType> metodę, jeśli wartość ma być używany, gdy wartość typu dopuszczającego wartość null jest równa null powinna być wartością domyślną typu wartości podstawowej.
  
Można jawnie rzutowane typu dopuszczającego wartość null do niedopuszczającej typu. Na przykład:  
  
[!code-csharp[explicit cast](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#6)]

W czasie wykonywania, jeśli wartość typu dopuszczającego wartość null jest pusta, jawnego rzutowania zgłasza <xref:System.InvalidOperationException>.

Typem wartościowym niebędącym jest niejawnie konwertowany na odpowiedni typ dopuszczający wartość null.
  
## <a name="operators"></a>Operatory

Jednoargumentowy wstępnie zdefiniowanych i operatory binarne i zdefiniowane przez użytkownika operatory, które istnieją w przypadku typów wartości może również używane przez typy dopuszczające wartości null. Te operatory generuje wartość null, jeśli jeden lub oba operandy są null; w przeciwnym razie operator używa wartości zawartej do obliczania wyniku. Na przykład:  
  
[!code-csharp[operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#7)]
  
Dla operatorów relacyjnych (`<`, `>`, `<=`, `>=`), jeśli jeden lub oba argumenty mają wartość null, wynik jest `false`. Nie przyjęto założenie, że ponieważ danym porównaniu (na przykład `<=`) zwraca `false`, przeciwne porównania (`>`) zwraca `true`. W poniższym przykładzie pokazano, że jest 10

- ani większa lub równa null,
- ani mniejsza niż wartość null.
  
[!code-csharp-interactive[relational and equality operators](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#8)]
  
Powyższy przykład pokazuje, że porównanie równości dwa typy dopuszczające wartość null, które są zarówno null daje w wyniku `true`.

## <a name="boxing-and-unboxing"></a>Konwersja boxing i konwersja unboxing

Jest typem wartościowym [opakowany](../types/boxing-and-unboxing.md) przez następujące reguły:

- Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `false`, generowany jest odwołanie o wartości null.  
- Jeśli <xref:System.Nullable%601.HasValue%2A> zwraca `true`, wartość typu podstawowego wartość `T` jest spakowany, nie wystąpienie <xref:System.Nullable%601>.

Rozpakowywanie z opakowanym typem wartościowym do odpowiedniego typu dopuszczającego wartość null, co ilustruje poniższy przykład:

[!code-csharp-interactive[boxing and unboxing](../../../../samples/snippets/csharp/programming-guide/nullable-types/NullableTypesUsage.cs#9)]

## <a name="the-bool-type"></a>Wartość logiczna? Typ

`bool?` Typu dopuszczającego wartość null może zawierać trzy różne wartości: [true](../../language-reference/keywords/true-literal.md), [false](../../language-reference/keywords/false-literal.md), i [null](../../language-reference/keywords/null.md). `bool?` Typu przypomina logiczna typ zmiennej, który jest używany w języku SQL. Aby upewnij się, że wyniki generowane przez `&` i `|` operatory są zgodne z przechowywanymi w trzech typu Boolean w języku SQL, znajdują się następujące operatory wstępnie zdefiniowane:

- `bool? operator &(bool? x, bool? y)`  
- `bool? operator |(bool? x, bool? y)`  
  
Semantyka te operatory jest zdefiniowane w poniższej tabeli:  
  
|x|t|x i y|x&#124;y|  
|-------|-------|---------|--------------|  
|true|true|true|true|  
|true|false|false|true|  
|true|null|null|true|  
|false|true|false|true|  
|false|false|false|false|  
|false|null|false|null|  
|null|true|null|true|  
|null|false|false|null|  
|null|null|null|null|  

Należy pamiętać, że te dwa operatory nie są zgodne z zasadami opisanymi w [operatory](#operators) sekcji: wynik oceny — operator może być inna niż null, nawet, jeśli jeden z argumentów ma wartość null.
  
## <a name="see-also"></a>Zobacz też

- [Typy dopuszczające wartości zerowe](index.md)  
- [Przewodnik programowania w języku C#](../../programming-guide/index.md)  
- [Co dokładnie "podniesiony" oznacza?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)  
