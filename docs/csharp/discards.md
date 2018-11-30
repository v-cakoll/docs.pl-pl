---
title: Odrzuca — Przewodnik po języku C#
description: Opisano obsługę języka C# w odrzucenia, które są nieprzypisane, discardable zmienne i sposoby, w którym można odrzucenia.
author: rpetrusha
ms.author: ronpet
ms.date: 07/21/2017
ms.openlocfilehash: 761fb69d3bc774975caf63b8aa665f8c19c0430a
ms.sourcegitcommit: 7f7664837d35320a0bad3f7e4ecd68d6624633b2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/30/2018
ms.locfileid: "52671943"
---
# <a name="discards---c-guide"></a>Odrzuca — Przewodnik po języku C#

Począwszy od języka C# 7.0, C# obsługuje odrzuca, służą do tymczasowego, fikcyjnego zmiennych, które są celowo nieużywane w kodzie aplikacji. Odrzuca są równoważne nieprzypisane zmiennych; nie mają wartości. Ponieważ jest zmienną pojedynczego odrzucenia, a tej zmiennej nie może jeszcze być alokowana magazynu, odrzucenia może zmniejszyć alokacji pamięci. Ponieważ ich zamiar zwykłego kodu, zwiększyć jego czytelność i łatwość konserwacji.

Można wskazać, że zmienna jest odrzucenia, przypisując go znak podkreślenia (`_`) jako jego nazwę. Na przykład, następujące wywołanie metody zwraca 3-krotka, w którym wartości pierwszego i drugiego to odrzutów i *obszaru* poprzednio zadeklarowana zmienna, należy ustawić odpowiadającego składnika trzeciej zwrócony przez  *GetCityInformation*:

```csharp
(_, _, area) = city.GetCityInformation(cityName);
```

W języku C# 7.0 odrzucenia są obsługiwane w przypisania w następujących okolicznościach:

- Krotki i obiekt [dekonstrukcja](deconstruct.md).
- Za pomocą dopasowywania do wzorca [jest](language-reference/keywords/is.md) i [Przełącz](language-reference/keywords/switch.md).
- Wywołania do metod z `out` parametrów.
- Autonomiczny `_` gdy nie `_` znajduje się w zakresie.

Gdy `_` jest prawidłowy odrzucenia próby pobrania jej wartość lub użyj jej w operacji przypisania generuje błąd kompilatora CS0301, "Nazwa"\_"nie istnieje w bieżącym kontekście". Jest to spowodowane `_` nie jest przypisywana wartość i nie może jeszcze być przypisany lokalizacji magazynu. W przypadku rzeczywista zmienna, nie może odrzucić więcej niż jedną wartość, tak jak w poprzednim przykładzie.

## <a name="tuple-and-object-deconstruction"></a>Dekonstrukcja krotki i obiektu

Odrzuca są szczególnie przydatne w pracy z krotek, gdy kod aplikacji używa niektórych elementów krotki, ale ignoruje inne osoby. Na przykład następująca `QueryCityDataForYears` metoda zwraca 6-krotka nazwą miasta, jego obszaru, roku, to miasto populację na potrzeby tego roku, drugiego roku i miasta populację na potrzeby tego drugiego roku. W przykładzie pokazano zmianę populacji między te dwa lata. Dane udostępniła spójnej kolekcji, jesteśmy unconcerned z obszarem miasta i wiemy, nazwę miasta i dwiema datami w czasie projektowania. W rezultacie firma Microsoft interesują jedynie wartości dwóch populacji, przechowywane w spójnej kolekcji i może obsługiwać jego pozostałe wartości jako odrzucenia.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

Aby uzyskać więcej informacji na temat dekonstrukcja krotek przy użyciu odrzucenia, zobacz [Dekonstrukcja krotek i innych typów](deconstruct.md#deconstructing-tuple-elements-with-discards).

`Deconstruct` Metody klasy, struktury lub interfejsu umożliwia również pobrać i dekonstruować określonego zestawu danych z obiektu. Możesz użyć odrzucenia, jeśli interesują Cię Praca z podzbiorem śródwierszową wartości. Poniższy przykład deconstructs `Person` obiektu do czterech ciągów (imiona i nazwiska, miasta i stanu), ale odrzuca nazwisko i stanu.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs)]

Aby uzyskać więcej informacji na temat dekonstrukcja typy zdefiniowane przez użytkownika przy użyciu odrzucenia, zobacz [Dekonstrukcja krotek i innych typów](deconstruct.md#deconstructing-a-user-defined-type-with-discards).

## <a name="pattern-matching-with-switch-and-is"></a>Za pomocą dopasowywania do wzorca `switch` i `is`

*Odrzucić wzorzec* mogą być używane w dopasowywania do wzorca z [jest](language-reference/keywords/is.md) i [Przełącz](language-reference/keywords/switch.md) słów kluczowych. Każde wyrażenie zawsze zgodny ze wzorcem odrzucenia.

W poniższym przykładzie zdefiniowano `ProvidesFormatInfo` metody, która używa [jest](language-reference/keywords/is.md) instrukcje, aby określić, czy zawiera obiekt <xref:System.IFormatProvider> implementacji i testów czy obiekt jest `null`. Używa również wzorca odrzucania obsługi obiektów innych niż null innego typu.

[!code-csharp[discard-pattern](../../samples/snippets/csharp/programming-guide/discards/discard-pattern2.cs)]

## <a name="calls-to-methods-with-out-parameters"></a>Wywołania metod za pomocą parametrów out

Podczas wywoływania `Deconstruct` metody typu zdefiniowanego przez użytkownika (wystąpienia klasy, struktury lub interfejsu), możesz odrzucić wartości poszczególnych dekonstruować `out` argumentów. Ale można również odrzucić wartość `out` argumentów podczas wywoływania dowolnej metody z parametrem out.

Poniższy przykład wywołuje [DateTime.TryParse (ciąg, out daty/godziny)](<xref:System.DateTime.TryParse(System.String,System.DateTime@)>) metodę, aby określić, czy reprezentacją ciągu daty jest nieprawidłowy w bieżącej kultury. Ponieważ przykład dotyczy tylko w przypadku sprawdzania poprawności ciągu daty i nie ich w celu wyodrębnienia Data, analizowania `out` argument do metody jest odrzucenia.

[!code-csharp[discard-with-out](../../samples/snippets/csharp/programming-guide/discards/discard-out1.cs)]

## <a name="a-standalone-discard"></a>Odrzuć autonomiczny

Odrzucenia autonomiczny służy do wskazania jakakolwiek zmienna, która zostanie zignorowany. W poniższym przykładzie użyto odrzucenia autonomiczne do ignorowania <xref:System.Threading.Tasks.Task> obiektu zwróconego przez operację asynchroniczną. Skutkuje to pomijania wyjątek, który zgłasza operacji, jak zbliża się zakończyć.

[!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard1.cs)]

Należy pamiętać, że `_` jest również prawidłowym identyfikatorem. Gdy jest używana poza kontekstem obsługiwanych, `_` jest traktowany jako prawidłową zmienną, ale nie jako odrzucenia. Jeśli nazwany identyfikator `_` jest już w zakresie użytkowania `_` jako autonomiczny odrzucenia może doprowadzić do:

- Przypadkowe modyfikacji wartości w zakresie `_` zmiennej, przypisując jej wartość zamierzony odrzucenia. Na przykład:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#1)]

- Błąd kompilatora za naruszenie bezpieczeństwa typu. Na przykład:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#2)]

- Błąd kompilatora CS0136, "element lokalny lub parametr o nazwie"\_"nie można zadeklarować w tym zakresie, ponieważ w tym nazwa jest używana w otaczającym zakresie lokalnym do zdefiniowania elementu lokalnego lub parametru." Na przykład:

   [!code-csharp[standalone-discard](../../samples/snippets/csharp/programming-guide/discards/standalone-discard2.cs#3)]

## <a name="see-also"></a>Zobacz także

- [Dekonstrukcja krotek i innych typów](deconstruct.md)
- [`is` Słowo kluczowe](language-reference/keywords/is.md)
- [`switch` Słowo kluczowe](language-reference/keywords/switch.md)
