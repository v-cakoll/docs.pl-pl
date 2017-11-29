---
title: "Odrzucenia — przewodnik C#"
description: "Opisuje C# w obsługę odrzucenia, które są nieprzypisane, zmienne discardable i sposoby, w którym można odrzucenia."
keywords: .NET, .NET core
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.topic: article
ms.prod: .net
ms.technology: devlang-csharp
ms.devlang: csharp
ms.openlocfilehash: 800a27d2d186c738dceb6838aa669377a0c07b01
ms.sourcegitcommit: 882e02b086d7cb9c75f748494cf7a8d3377c5874
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/17/2017
---
# <a name="discards---c-guide"></a>Odrzucenia — przewodnik C#

Począwszy od C# 7, C# obsługuje odrzuca, które są tymczasowe, fikcyjny zmienne, które są celowo nieużywane w kodzie aplikacji. Odrzucenia są równoważne nieprzypisane zmiennych; nie mają one wartość. Ponieważ jest zmienną pojedynczego odrzucenia, a tej zmiennej nie może jeszcze być alokowana magazynu, odrzucenia można zmniejszyć alokacji pamięci. Ponieważ one być celem wyczyść kodu, zwiększyć jego czytelności i łatwości konserwacji.

Można wskazać, że zmienna jest odrzucenia przypisując podkreślenie (`_`) jako jego nazwę. Na przykład następujące wywołanie metody zwraca 3 podwójnego, w którym pierwszej i drugiej wartości są odrzucenia i *obszaru* poprzednio zadeklarowana zmienna ustawioną odpowiadającego składnika trzeciej zwrócony przez  *GetCityInformation*:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

W języku C# 7 odrzucenia są obsługiwane w przypisaniach w następujących sytuacjach:

- Spójnej kolekcji i obiektów [deconstruction](deconstruct.md).
- Dopasowywanie do wzorca za [jest](language-reference/keywords/is.md) i [przełącznika](language-reference/keywords/switch.md).
- Wywołania metod z `out` parametrów.
- Autonomiczny `_` gdy nie `_` znajduje się w zakresie.

Gdy `_` jest prawidłowy odrzucenia, próby pobrania jej wartość lub użyj jej w operacji przypisania generuje błąd kompilatora CS0301, "Nazwa"\_"nie istnieje w bieżącym kontekście". Jest to spowodowane `_` nie jest przypisywana wartość i nie może jeszcze być przypisany lokalizacji magazynu. Jeśli ich rzeczywista zmienna nie może odrzucić więcej niż jedną wartość, jak w poprzednim przykładzie.

## <a name="tuple-and-object-deconstruction"></a>Deconstruction spójnej kolekcji i obiektów

Odrzucenia są szczególnie przydatne w pracy z krotek, gdy kod aplikacji używa niektóre elementy spójnej kolekcji, ale ignoruje inne. Na przykład następująca `QueryCityDataForYears` metoda zwraca krotka 6 nazwą miasta, jego obszar, roku, miasta wypełniania tego roku, drugiego roku i wypełniania Miasto drugiego roku. W przykładzie zmiany w populacji między te dwa lata. Danych dostępne w spójnej kolekcji, jesteśmy unconcerned z obszarem mieście i wiemy, nazwę miejscowości i dwiema datami w czasie projektowania. W związku z tym możemy tylko w przypadku zainteresowani dwa wypełniania wartościami przechowywanymi w spójnej kolekcji, a może obsłużyć pozostałych wartości jako odrzucenia.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Aby uzyskać więcej informacji na deconstructing spójnych kolekcji zawierający odrzucenia, zobacz [Deconstructing krotek i innych typów](deconstruct.md#deconstructing-tuple-elements-with-discards).

`Deconstruct` Metody klasy, struktury lub interfejsu umożliwia również pobrać i deconstruct określonego zestawu danych z obiektu. Jeśli interesuje Cię w pracy z tylko podzestaw deconstructed wartości można użyć odrzucenia. Poniższy przykład deconstructs Ihe `Person` obiektu do czterech ciągów (imiona i nazwiska, miasta i stanu), ale odrzuca nazwisko i stanu.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Aby uzyskać więcej informacji na deconstructing typy danych zdefiniowane przez użytkownika z odrzucenia, zobacz [Deconstructing krotek i innych typów](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Dopasowywanie do wzorca za `switch` i`is`

*Odrzucić wzorzec* mogą być używane w dopasowywanie do wzorca za [jest](language-reference/keywords/is.md) i [przełącznika](language-reference/keywords/switch.md) słów kluczowych. Każdy wyrażenie zawsze odpowiada wzorcowi odrzucenia.

W poniższym przykładzie zdefiniowano `ProvidesFormatInfo` metody, która używa [jest](language-reference/keywords/is.md) instrukcje, aby określić, czy obiekt udostępnia <xref:System.IFormatProvider> implementacji i testy czy obiekt jest `null`. Używa również wzorzec odrzucenia do obsługi obiektów inną niż null z innego typu.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Wywołania metod z parametrów out

Podczas wywoływania metody `Deconstruct` deconstruct zdefiniowane przez użytkownika typu (wystąpienia klasy, struktury lub interfejsu), można odrzucić wartości poszczególne metody `out` argumentów. Ale można również odrzucić wartość `out` argumenty podczas wywołaniem jakiejkolwiek jego metody z parametrem out. 

Następujące przykładowe wywołania [DateTime.TryParse (ciąg, limit DateTime)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) metodę, aby określić, czy reprezentacja ciągu daty jest nieprawidłowy w bieżącej kultury. Ponieważ przykład dotyczy tylko z sprawdzanie poprawności ciąg daty i nie analizowania plik w celu wyodrębnienia data `out` argument do metody jest odrzucenia.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Odrzuć autonomiczny

Odrzuć autonomiczny można służy do wskazywania żadnych zmiennej, która zostanie zignorowany. W poniższym przykładzie użyto odrzucenia autonomicznej do ignorowania <xref:System.Threading.Tasks.Task> obiektu zwróconego przez operację asynchroniczną. Skutkuje to pomijania wyjątek, która zgłasza operacji, ponieważ jest o przeprowadzenie.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Należy pamiętać, że `_` również jest prawidłowym identyfikatorem. Użycie poza obsługiwanych kontekstu, `_` jest traktowane nie jako odrzucenia, ale jako prawidłową zmienną. Jeśli identyfikator o nazwie `_` znajduje się już w zakresie, użycie `_` jako autonomiczny może spowodować odrzucenia:

- Przypadkowe modyfikacji wartości w zakresie `_` zmiennej przypisując wartość zamierzone odrzucenia. Na przykład:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]
 
- Błąd kompilatora za naruszenie zabezpieczeń. Na przykład:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]
 
- Błąd kompilatora CS0136, "lokalnego lub parametr o nazwie"_"nie można zadeklarować w tym zakresie, ponieważ ta nazwa jest używana w otaczającym zakresie lokalnym do zdefiniowania elementu lokalnego lub parametr." Na przykład:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Zobacz także
[Deconstructing krotek i innych typów](deconstruct.md)   
[`is`słowo kluczowe](language-reference/keywords/is.md)   
[`switch`słowo kluczowe](language-reference/keywords/switch.md)   
