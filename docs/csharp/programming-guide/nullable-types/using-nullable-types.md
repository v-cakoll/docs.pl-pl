---
title: "Używanie typów dopuszczających wartości zerowe (Przewodnik programowania w języku C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
helpviewer_keywords: nullable types [C#], about nullable types
ms.assetid: 0bacbe72-ce15-4b14-83e1-9c14e6380c28
caps.latest.revision: "31"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c8a42392bbcd2e53c54ff4c13bf98c048262ae4d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="using-nullable-types-c-programming-guide"></a>Używanie typów dopuszczających wartości zerowe (Przewodnik programowania w języku C#)
Typy dopuszczające wartości zerowe może reprezentować wszystkich wartości typu podstawowego i dodatkowego [null](../../../csharp/language-reference/keywords/null.md) wartość. Typy dopuszczające wartości null są zadeklarowane w jeden z dwóch sposobów:  
  
 `System.Nullable<T> variable`  
  
 —lub—  
  
 `T? variable`  
  
 `T`jest typem podstawowym typu dopuszczającego wartość null. `T`mogą być dowolnego typu wartości w tym `struct`; nie może być typem referencyjnym.  
  
 Na przykład kiedy może używać typu dopuszczającego wartość null, należy wziąć pod uwagę sposób zwykłej wartość logiczna może mieć dwie wartości: true i false. Nie istnieje wartość, która oznacza, że "undefined". W wielu aplikacjach programowania głównie bazy danych interakcji, zmienne może wystąpić w stanie niezdefiniowany. Na przykład pole w bazie danych może zawierać wartości PRAWDA lub FAŁSZ, ale może również zawierać żadnej wartości w ogóle. Podobnie można ustawić typy referencyjne `null` aby wskazać, że nie jest inicjowany.  
  
 Tej różnicy można utworzyć bardzo programowania pracy z dodatkowe zmienne używane do przechowywania informacji o stanie, użyj wartości specjalnych i tak dalej. Modyfikator typ dopuszczający wartość null umożliwia C# do tworzenia zmiennych Typ wartości, które wskazuje niezdefiniowaną wartość.  
  
## <a name="examples-of-nullable-types"></a>Przykłady typów dopuszczających wartości zerowe  
 Dowolny typ wartości może służyć jako podstawa dla typu dopuszczającego wartość null. Na przykład:  
  
 [!code-csharp[csProgGuideTypes#4](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_1.cs)]  
  
## <a name="the-members-of-nullable-types"></a>Elementów członkowskich typów dopuszczających wartości zerowe  
 Każde wystąpienie typu dopuszczającego wartości null ma dwie właściwości publiczne tylko do odczytu:  
  
-   `HasValue`  
  
     `HasValue`jest typu `bool`. Ma ustawioną wartość `true` Jeśli zmienna zawiera wartość inną niż null.  
  
-   `Value`  
  
     `Value`jest tego samego typu jako typu bazowego. Jeśli `HasValue` jest `true`, `Value` zawiera odpowiednią wartość. Jeśli `HasValue` jest `false`, podczas uzyskiwania dostępu do `Value` zgłosi <xref:System.InvalidOperationException>.  
  
 W tym przykładzie `HasValue` element członkowski jest używany do sprawdzenia, czy zmienna zawiera wartość, przed ponowną próbą go wyświetlić.  
  
 [!code-csharp[csProgGuideTypes#5](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_2.cs)]  
  
 Testowanie wartości można również wykonać jak w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideTypes#6](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_3.cs)]  
  
## <a name="explicit-conversions"></a>Jawne konwersje  
 Typ dopuszczający wartość null mogą być rzutowane na typu regularne jawnie z rzutowanie lub za pomocą `Value` właściwości. Na przykład:  
  
 [!code-csharp[csProgGuideTypes#7](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_4.cs)]  
  
 Jeśli konwersja zdefiniowana przez użytkownika jest zdefiniowany między dwoma typami, tym samym konwersji można również używać razem nullable wersje tych typów danych.  
  
## <a name="implicit-conversions"></a>Niejawne konwersje  
 Zmienna typu dopuszczającego wartość NULL można ustawić na wartość null z `null` — słowo kluczowe, jak pokazano w poniższym przykładzie:  
  
 [!code-csharp[csProgGuideTypes#8](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_5.cs)]  
  
 Konwersja z typu zwykłego na typ dopuszczający wartość null, jest niejawnie.  
  
 [!code-csharp[csProgGuideTypes#9](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_6.cs)]  
  
## <a name="operators"></a>Operatory  
 Wstępnie zdefiniowane jednoargumentowy i operatorów binarnych oraz wszystkie operatory zdefiniowane przez użytkownika, które istnieją dla typów wartości mogą również wykorzystywane przez typy dopuszczające wartości zerowe. Te operatorów daje wartość null, jeśli argumenty mają wartość null; w przeciwnym razie operator używa wartości zawartych w niej do obliczania wyniku. Na przykład:  
  
 [!code-csharp[csProgGuideTypes#10](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_7.cs)]  
  
 W przypadku wykonywania porównania z typy dopuszczające wartości null, jeśli wartość jednego z typów dopuszczających wartości zerowe ma wartość null, a drugi nie wszystkie porównania obliczać `false` z wyjątkiem `!=` (nie ma wartości). Ważne jest, aby nie zakłada, że ponieważ zwraca określonego porównanie `false`, w przeciwnym wypadku zwraca `true`. W poniższym przykładzie 10 nie jest większa, mniejsza ani równa null. Tylko `num1 != num2` daje w wyniku `true`.  
  
 [!code-csharp[csProgGuideTypes#11](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_8.cs)]  
  
 Daje w wyniku porównania równości dwóch typów wartości null, które są obie wartości null `true`.  
  
## <a name="the--operator"></a>? Operator  
 `??` Operator określa wartość domyślną, który jest zwracany, gdy typ dopuszczający wartość null jest przypisany do typu wartości null.  
  
 [!code-csharp[csProgGuideTypes#12](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_9.cs)]  
  
 Ten operator może również z wieloma typami wartości null. Na przykład:  
  
 [!code-csharp[csProgGuideTypes#13](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/using-nullable-types_10.cs)]  
  
## <a name="the-bool-type"></a>Bool? Typ  
 `bool?` Typ dopuszczający wartość null, mogą zawierać trzy różne wartości: [true](../../../csharp/language-reference/keywords/true.md), [false](../../../csharp/language-reference/keywords/false.md) i [null](../../../csharp/language-reference/keywords/null.md). Aby uzyskać informacje na temat rzutowania z typu wartość logiczna? Aby bool, zobacz [porady: bezpieczne rzutowanie z bool? na bool](../../../csharp/programming-guide/nullable-types/how-to-safely-cast-from-bool-to-bool.md).  
  
 Dopuszczające wartości zerowe wartości logiczne są podobne do logiczna typ zmiennej używanej w programie SQL. Do zapewnienia, że wyniki utworzonego przez `&` i `|` operatory są zgodne z przechowywanymi w trzech typu Boolean w programie SQL znajdują się następujące wstępnie zdefiniowane operatory:  
  
 `bool? operator &(bool? x, bool? y)`  
  
 `bool? operator |(bool? x, bool? y)`  
  
 W poniższej tabeli przedstawiono wyniki tych operatorów:  
  
|X|t|x & y|x &#124; y|  
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
  
## <a name="see-also"></a>Zobacz też  
 [Przewodnik programowania w języku C#](../../../csharp/programming-guide/index.md)  
 [Typy dopuszczające wartości zerowe](../../../csharp/programming-guide/nullable-types/index.md)  
 [Konwersja boxing typów dopuszczających wartości zerowe](../../../csharp/programming-guide/nullable-types/boxing-nullable-types.md)  
 [Typy dopuszczające wartości zerowe wartości](../../../visual-basic/programming-guide/language-features/data-types/nullable-value-types.md)
