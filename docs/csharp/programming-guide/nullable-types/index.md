---
title: Typy dopuszczające wartości zerowe (Przewodnik programowania w języku C#)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: fcff492f420a60a41b373bf9042ed0c2d66d0446
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/23/2018
ms.locfileid: "34456591"
---
# <a name="nullable-types-c-programming-guide"></a>Typy dopuszczające wartości zerowe (Przewodnik programowania w języku C#)
Typy dopuszczające wartości null są wystąpieniami klasy <xref:System.Nullable%601?displayProperty=nameWithType> struktury. Typ dopuszczający wartość null może reprezentować poprawny zakres wartości dla jego typem podstawowym wartości, a także dodatkowe `null` wartość. Na przykład `Nullable<Int32>`, wyraźnym "Dopuszcza wartości null z Int32," można przypisać wartości od -2147483648 do 2147483647 lub można go przypisać `null` wartość. A `Nullable<bool>` można przypisać wartości [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), lub [null](../../../csharp/language-reference/keywords/null.md). Możliwość przypisania `null` do typów liczbowych i logicznych jest szczególnie przydatne podczas mamy do czynienia z bazami danych i inne typy danych, które zawierają elementy, które nie może być przypisana wartość. Na przykład polem w bazie danych można zapisać wartości `true` lub `false`, lub może być niezdefiniowana. 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
Aby uzyskać więcej przykładów, zobacz [przy użyciu typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## <a name="nullable-types-overview"></a>Typy dopuszczające wartości zerowe — omówienie  
 Typy dopuszczające wartości zerowe mają następującą charakterystykę:  
  
-   Typy dopuszczające wartości zerowe reprezentuje typ wartości zmiennych, które można przypisać wartość `null`. Nie można utworzyć typu zerowalnego na podstawie typu odwołania. (Odniesienia obsługują typy już `null` wartości.)  
  
-   Składnia `T?` jest skróconą formą <xref:System.Nullable%601>, gdzie `T` jest typem wartości. Dwa formularze są wymienne.  
  
-   Przypisywanie wartości do typu dopuszczającego wartość null, tak samo jak dla typu wartości zwykłej, na przykład `int? x = 10;` lub `double? d = 4.108`. Typ dopuszczający wartość NULL można również przypisać wartość `null`: `int? x = null.`  
  
-   Użyj <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> metodę, aby zwrócić przypisaną wartość lub wartość domyślna dla typu źródłowego, jeśli wartość jest `null`, na przykład `int j = x.GetValueOrDefault();`  
  
-   Użyj <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> właściwości tylko do odczytu do testowania w przypadku wartości null i pobrać wartość, jak pokazano w poniższym przykładzie: `if(x.HasValue) j = x.Value;`  
  
    -   `HasValue` Zwraca `true` Jeśli zmienna zawiera wartość, lub `false` przypadku `null`.  
  
    -   `Value` Właściwość zwraca wartość, jeśli jeden jest przypisany. W przeciwnym razie <xref:System.InvalidOperationException?displayProperty=nameWithType> jest generowany.  
  
    -   Wartość domyślna dla `HasValue` jest `false`. `Value` Właściwość nie ma wartości domyślnej.  
  
    -   Można również użyć `==` i `!=` operatory typu dopuszczającego wartość null, jak pokazano w poniższym przykładzie: `if (x != null) y = x;`  
  
-   Użyj `??` operatora, aby przypisać wartość domyślną, który zostanie zastosowany, gdy typ dopuszczający wartość null, w których bieżąca wartość jest `null` jest przypisany do typu wartości null, na przykład `int? x = null; int y = x ?? -1;`  
  
-   Zagnieżdżone typy dopuszczające wartości null są niedozwolone. Następujący wiersz nie zostanie skompilowany: `Nullable<Nullable<int>> n;`  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 Informacje dodatkowe:  
  
-   [Używanie typów dopuszczających wartości null](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
-   [Konwersja boxing typów dopuszczających wartości null](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
  
-   [??, operator](../../../csharp/language-reference/operators/null-coalescing-operator.md)  
  
## <a name="c-language-specification"></a>Specyfikacja języka C#  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Nullable>  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [C#](../../../csharp/index.md)  
 [Odwołanie w C#](../../../csharp/language-reference/index.md)  
 [Co dokładnie "unosiło" oznacza?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
