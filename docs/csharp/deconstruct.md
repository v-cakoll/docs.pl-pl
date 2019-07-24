---
title: Dekonstrukcja krotek i innych typów
description: Dowiedz się, jak dekonstruować krotki i inne typy.
author: rpetrusha
ms.author: ronpet
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 5d37f9567570666c280be437aa0472a620a16c63
ms.sourcegitcommit: 24a4a8eb6d8cfe7b8549fb6d823076d7c697e0c6
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/23/2019
ms.locfileid: "68400405"
---
# <a name="deconstructing-tuples-and-other-types"></a>Dekonstrukcja krotek i innych typów

Krotka zapewnia lekki sposób pobierania wielu wartości z wywołania metody. Ale po pobraniu krotki musisz obsłużyć poszczególne elementy. Wykonanie tej czynności na zasadzie elementu po elemencie jest uciążliwe, jak pokazano w poniższym przykładzie. `QueryCityData` Metoda zwraca 3-krotkę, a każdy z jej elementów jest przypisany do zmiennej w oddzielnej operacji.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Pobieranie wielu wartości pól i właściwości z obiektu może być równie uciążliwe: należy przypisać pole lub wartość właściwości do zmiennej w zasadzie składowej.

Począwszy od C# 7,0, można pobrać wiele elementów z krotki lub pobrać wiele pól, właściwości i wartości obliczanych z obiektu w jednej operacji dekonstrukcji. Podczas dekonstruowania krotki należy przypisać jej elementy do poszczególnych zmiennych. Podczas dekonstruowania obiektu, należy przypisać wybrane wartości do poszczególnych zmiennych.

## <a name="deconstructing-a-tuple"></a>Dekonstrukcja krotki

C#wbudowane funkcje obsługujące tworzenie krotek, które umożliwiają rozpakowanie wszystkich elementów w kolekcji w ramach jednej operacji. Ogólna składnia służąca do dekonstruowania krotki jest podobna do składni definiującej ją: należy umieścić zmienne, do których każdy element ma być przypisany w nawiasach po lewej stronie instrukcji przypisania. Na przykład poniższa instrukcja przypisuje elementy 4-krotki do czterech oddzielnych zmiennych:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Istnieją trzy sposoby dekonstrukcji krotki:

- Można jawnie zadeklarować typ każdego pola wewnątrz nawiasów. Poniższy przykład używa tego podejścia do dekonstruowania 3-spójnej kolekcji zwracanej `QueryCityData` przez metodę.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Możesz użyć `var` słowa kluczowego, aby C# wnioskuje typ każdej zmiennej. `var` Słowo kluczowe jest umieszczane poza nawiasami. Poniższy przykład używa wnioskowania o typie podczas dekonstruowania 3-spójnej kolekcji zwróconej `QueryCityData` przez metodę.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Można również użyć `var` słowa kluczowego osobno z dowolnymi lub wszystkimi zmiennymi deklaracji w nawiasach.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Jest to bardzo skomplikowane i nie jest zalecane.

- Na koniec można rozgałęziać krotkę na zmienne, które zostały już zadeklarowane.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Należy zauważyć, że nie można określić określonego typu poza nawiasami, nawet jeśli każde pole w krotek ma ten sam typ. Spowoduje to wygenerowanie błędu kompilatora CS8136, "dekonstrukcja" var (...) "nie zezwala na określony typ dla" var ".

Należy pamiętać, że należy również przypisać każdy element krotki do zmiennej. W przypadku pominięcia jakichkolwiek elementów kompilator generuje błąd CS8132, "nie można dekonstruować krotki elementów" x "w zmiennych" y "."

Należy zauważyć, że nie można mieszać deklaracji i przypisań do istniejących zmiennych po lewej stronie dekonstrukcji. Kompilator generuje błąd CS8184, "dekonstrukcja nie może mieszać deklaracji i wyrażeń po lewej stronie". gdy elementy członkowskie zawierają nowo zadeklarowane i istniejące zmienne.

## <a name="deconstructing-tuple-elements-with-discards"></a>Dekonstrukcja elementów krotki z odrzuconymi

Często podczas dekonstruowania krotki interesuje się wartości tylko niektórych elementów. Począwszy od C# 7,0, można C#wykorzystać obsługę odrzutów, które są zmiennymi tylko do zapisu, których wartości zostały wybrane do ignorowania. Odrzucanie jest oznaczone znakiem podkreślenia ("\_") w przypisaniu. Możesz odrzucić dowolną liczbę wartości. wszystkie są reprezentowane przez pojedyncze odrzucanie `_`,.

Poniższy przykład ilustruje użycie krotek z odrzutami. `QueryCityDataForYears` Metoda zwraca 6-krotkę z nazwą miasta, jego obszarem, rokiem, populacją miasta dla tego roku, drugi rok i populacją miasta dla tego drugiego roku. W przykładzie pokazano zmianę populacji między tymi dwoma latami. Danych dostępnych w spójnej kolekcji nie ma w tym obszarze miasta i wiemy, że imię i nazwisko miasto oraz dwie daty w czasie projektowania. W związku z tym interesuje tylko dwie wartości populacji przechowywane w spójnej kolekcji i mogą obsługiwać pozostałe wartości jako odrzucenia.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a>Dekonstrukcja typów zdefiniowanych przez użytkownika

C#nie oferuje wbudowanej obsługi dla dekonstrukcji typów bez krotek. Jednak jako autor klasy, struktury lub interfejsu można zezwolić na dekonstrukcja wystąpień typu przez zaimplementowanie jednej lub kilku `Deconstruct` metod. Metoda zwraca wartość void, a każda wartość do odbudowy jest wskazywana przez parametr [out](language-reference/keywords/out-parameter-modifier.md) w podpisie metody. Na przykład następująca `Deconstruct` Metoda `Person` klasy zwraca pierwszą, środkową i nazwisko:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Następnie można dekonstruować wystąpienie `Person` klasy o nazwie `p` z przypisaniem podobnym do następującego:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Poniższy przykład przeciąża `Deconstruct` metodę, aby zwrócić różne kombinacje właściwości `Person` obiektu. Zwracanie pojedynczych przeciążeń:

- Imię i nazwisko.
- Nazwa pierwszego, ostatniego i drugiego.
- Imię i nazwisko, nazwisko, nazwa miasta i Nazwa stanu.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Ponieważ można przeciążać `Deconstruct` metodę w celu odzwierciedlenia grup danych, które są powszechnie wyodrębniane z obiektu, należy zachować ostrożność `Deconstruct` , aby zdefiniować metody z podpisami, które są charakterystyczne i niejednoznaczne. Wiele `Deconstruct` metod, które mają taką samą `out` liczbę parametrów lub tę `out` samą liczbę i typ parametrów w innej kolejności może spowodować pomyłkę.

Przeciążona `Deconstruct` Metoda w poniższym przykładzie ilustruje jedno z możliwych źródeł pomyłek. Pierwsze Przeciążenie zwraca imię i nazwisko, drugie imię, nazwisko i wiek `Person` obiektu, w tej kolejności. Drugie Przeciążenie zwraca informacje o nazwie tylko wraz z rocznym przychodem, ale pierwszy, średni i nazwisko są w innej kolejności. Ułatwia to pomylić kolejności argumentów podczas dekonstruowania `Person` wystąpienia.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Dekonstrukcja typu zdefiniowanego przez użytkownika z odrzuconymi

Podobnie jak w przypadku [krotek](#deconstructing-tuple-elements-with-discards), można użyć odrzucania, aby zignorować zaznaczone elementy zwrócone przez `Deconstruct` metodę. Każdy odrzucony jest zdefiniowany przez zmienną o nazwie\_"", a pojedyncza operacja dekonstrukcja może obejmować wiele odrzutów.

Poniższy przykład dekonstruuje `Person` obiekt na cztery ciągi (imię i nazwisko, miasto i stan), ale odrzuca ostatnią nazwę i stan.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Dekonstrukcja typu zdefiniowanego przez użytkownika za pomocą metody rozszerzenia

Jeśli nie utworzono klasy, struktury lub interfejsu, można nadal dekonstruować obiekty tego typu przez implementację co najmniej jednej `Deconstruct` [metody rozszerzenia](programming-guide/classes-and-structs/extension-methods.md) w celu zwrócenia odpowiednich wartości.

W poniższym przykładzie zdefiniowano `Deconstruct` dwie metody rozszerzające <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> dla klasy. Pierwszy zwraca zestaw wartości wskazujący charakterystykę właściwości, w tym jej typ, czy jest to element statyczny, czy wystąpienie, czy jest tylko do odczytu i czy jest indeksowany. Drugi wskazuje dostępność właściwości. Ponieważ dostępność metody dostępu get i set może się różnić, wartości logiczne wskazują, czy właściwość ma oddzielne metody dostępu get i Set, a jeśli tak, to czy mają one taką samą dostępność. Jeśli istnieje tylko jedna metoda dostępu lub metoda dostępu get i Set ma tę samą dostępność, `access` zmienna wskazuje dostępność właściwości jako całości. W przeciwnym razie dostępność funkcji dostępu get i Set jest wskazywana przez `getAccess` zmienne i. `setAccess`

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Zobacz także

- [Odrzucenia](discards.md)
- [Krotki](tuples.md)
