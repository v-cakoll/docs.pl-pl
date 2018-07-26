---
title: Typy dopuszczające wartości zerowe (Przewodnik programowania w języku C#)
ms.date: 05/15/2017
helpviewer_keywords:
- nullable types [C#]
- C# language, nullable types
- types [C#], nullable
ms.assetid: e473cb01-28ca-42be-9cea-f717055d72c6
ms.openlocfilehash: 64b326b82cd022ed6590a232546690e2ec2a5c78
ms.sourcegitcommit: 70c76a12449439bac0f7a359866be5a0311ce960
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/25/2018
ms.locfileid: "39245596"
---
# <a name="nullable-types-c-programming-guide"></a>Typy dopuszczające wartości zerowe (Przewodnik programowania w języku C#)
Typy dopuszczające wartości null są wystąpieniami <xref:System.Nullable%601?displayProperty=nameWithType> struktury. Typ dopuszczający wartość null może reprezentować poprawny zakres wartości dla jego podstawowy typ wartości, a także dodatkowe `null` wartość. Na przykład `Nullable<Int32>`, Wymowa: "Dopuszcza wartości null typu Int32," można przypisać dowolną wartość od -2147483648 do 2147483647 lub może ona zostać przypisana `null` wartość. A `Nullable<bool>` można przypisać wartości [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md), lub [null](../../../csharp/language-reference/keywords/null.md). Możliwość przypisania `null` typów liczbowych i logicznych jest szczególnie przydatna podczas masz do czynienia z bazami danych i inne typy danych, które zawierają elementy, których nie można przypisać jej wartości. Na przykład pola logicznych w bazie danych można przechowywać wartości `true` lub `false`, lub może być niezdefiniowana. 
  
[!code-csharp[nullable-types](../../../../samples/snippets/csharp/programming-guide/nullable-types/nullable-ex1.cs)]  
  
Aby uzyskać więcej przykładów, zobacz [przy użyciu typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/using-nullable-types.md)  
  
## <a name="nullable-types-overview"></a>Przegląd typów dopuszczających wartości zerowe  
 Typy dopuszczające wartości zerowe mają następującą charakterystykę:  
  
-   Typy dopuszczające wartości zerowe reprezentują zmienne typu wartości, które można przypisać wartość `null`. Nie można utworzyć typu dopuszczającego wartość null, w oparciu o typ odwołania. (Już obsługuje typy odwołań `null` wartości.)  
  
-   Składnia `T?` jest skrótem <xref:System.Nullable%601>, gdzie `T` jest typem wartości. Dwa formularze są wymienne.  
  
-   Przypisania wartości do typu dopuszczającego wartość null, tak jak w przypadku zwykłej wartości typu, na przykład `int? x = 10;` lub `double? d = 4.108;`. Typ dopuszczający wartość NULL można przypisać wartość `null`: `int? x = null;`.  
  
-   Użyj <xref:System.Nullable%601.GetValueOrDefault%2A?displayProperty=nameWithType> metodę, aby zwrócić przypisaną wartość lub wartość domyślna dla typu podstawowego, jeśli wartość jest `null`, na przykład `int j = x.GetValueOrDefault();`  
  
-   Użyj <xref:System.Nullable%601.HasValue%2A> i <xref:System.Nullable%601.Value%2A> właściwości tylko do odczytu do testowania dla wartości null i pobierać wartości, jak pokazano w poniższym przykładzie: `if(x.HasValue) j = x.Value;`  
  
    -   `HasValue` Właściwość zwraca `true` Jeśli zmienna zawiera wartość, lub `false` , gdy jest `null`.  
  
    -   `Value` Właściwość zwraca wartość, jeśli jeden jest przypisany. W przeciwnym razie <xref:System.InvalidOperationException?displayProperty=nameWithType> zgłaszany.  
  
    -   Wartością domyślną dla `HasValue` jest `false`. `Value` Właściwość nie ma wartości domyślnej.  
  
    -   Można również użyć `==` i `!=` operatory o typu dopuszczającego wartość null, jak pokazano w poniższym przykładzie: `if (x != null) y = x;`  
  
-   Użyj `??` operatora, aby przypisać wartość domyślną, które zostaną zastosowane, gdy typ dopuszczający wartość null, w której bieżąca wartość to `null` jest przypisany do typu wartości null, na przykład `int? x = null; int y = x ?? -1;`  
  
-   Zagnieżdżone typy dopuszczające wartości null są niedozwolone. Nie zostanie skompilowany następujący wiersz: `Nullable<Nullable<int>> n;`  
  
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
 [Dokumentacja języka C#](../../../csharp/language-reference/index.md)  
 [Co dokładnie "podniesiony" oznacza?](https://blogs.msdn.microsoft.com/ericlippert/2007/06/27/what-exactly-does-lifted-mean/)
