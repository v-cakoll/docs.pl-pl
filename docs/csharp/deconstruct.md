---
title: Dekonstrukcja krotek i innych typów
description: Dowiedz się, jak zdekonstruować krotek i innych typów.
ms.technology: csharp-fundamentals
ms.date: 11/23/2017
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: d238f6f520653befb1464377094b93e34dde0eca
ms.sourcegitcommit: 927b7ea6b2ea5a440c8f23e3e66503152eb85591
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/16/2020
ms.locfileid: "81463126"
---
# <a name="deconstructing-tuples-and-other-types"></a>Dekonstrukcja krotek i innych typów

Krotka zapewnia lekki sposób pobierania wielu wartości z wywołania metody. Ale po pobraniu krotki, trzeba obsługiwać jego poszczególnych elementów. Robi to na podstawie elementu po elemencie jest uciążliwe, jak pokazano w poniższym przykładzie. Metoda `QueryCityData` zwraca 3-krotki, a każdy z jego elementów jest przypisany do zmiennej w oddzielnej operacji.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Pobieranie wielu wartości pól i właściwości z obiektu może być równie uciążliwe: należy przypisać pole lub wartość właściwości do zmiennej na podstawie elementu członkowskiego.

Począwszy od języka C# 7.0, można pobrać wiele elementów z krotki lub pobrać wiele pól, właściwości i obliczonych wartości z obiektu w jednej operacji *dekonstrukcji.* Podczas dekonstrukcji krotki, należy przypisać jej elementy do poszczególnych zmiennych. Podczas dekonstruowania obiektu do poszczególnych zmiennych przypisywane są wybrane wartości.

## <a name="deconstructing-a-tuple"></a>Dekonstruowanie krotki

C# funkcje wbudowanej obsługi dekonstrukcji krotek, co pozwala rozpakować wszystkie elementy w krocie w jednej operacji. Ogólna składnia dekonstrukcji krotki jest podobna do składni definiowania jednej: należy ująć zmienne, do których każdy element ma być przypisany w nawiasach po lewej stronie instrukcji przypisania. Na przykład następująca instrukcja przypisuje elementy 4-krotki do czterech oddzielnych zmiennych:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Istnieją trzy sposoby dekonstrukcji krotki:

- Można jawnie zadeklarować typ każdego pola wewnątrz nawiasów. W poniższym przykładzie użyto tego podejścia do dekonstrukcji 3-krotki zwracane `QueryCityData` przez metodę.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Można użyć `var` słowa kluczowego, tak aby C# wywnioskować typ każdej zmiennej. Słowo kluczowe `var` jest umieszczane poza nawiasami. W poniższym przykładzie użyto inference typu podczas dekonstrukcji 3-krotka zwrócona `QueryCityData` przez metodę.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Można również użyć `var` słowa kluczowego indywidualnie z dowolnej lub wszystkich deklaracji zmiennych wewnątrz nawiasów.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Jest to uciążliwe i nie jest zalecane.

- Na koniec można zdekonstruować krotki na zmienne, które zostały już zadeklarowane.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Należy zauważyć, że nie można określić określonego typu poza nawiasami, nawet jeśli każde pole w krocie ma ten sam typ. Powoduje to wygenerowanie błędu kompilatora CS8136, "Formularz dekonstrukcji 'var (...)' nie zezwala na określony typ dla 'var'.".

Należy również przypisać każdy element krotki do zmiennej. Jeśli pominięto jakiekolwiek elementy, kompilator generuje błąd CS8132, "Nie można zdekonstruować krotki elementów 'x' na zmienne 'y'."

Należy zauważyć, że nie można mieszać deklaracji i przypisań do istniejących zmiennych po lewej stronie dekonstrukcji. Kompilator generuje błąd CS8184, "dekonstrukcja nie można mieszać deklaracji i wyrażeń po lewej stronie." gdy członkowie obejmują nowo zadeklarowane i istniejące zmienne.

## <a name="deconstructing-tuple-elements-with-discards"></a>Dekonstruowanie elementów krotki z odrzutami

Często podczas dekonstrukcji krotki, jesteś zainteresowany wartości tylko niektóre elementy. Począwszy od języka C# 7.0, można skorzystać z obsługi języka C#dla *odrzuceń,* które są zmienne tylko do zapisu, których wartości zostały wybrane do zignorowania. Odrzucenie jest oznaczane przez znak\_podkreślenia (" ") w przypisaniu. Możesz odrzucić dowolną liczbę wartości; wszystkie są reprezentowane przez `_`pojedynczy odrzut, .

Poniższy przykład ilustruje użycie krotek z odrzutami. Metoda `QueryCityDataForYears` zwraca 6-krotka z nazwą miasta, jego obszar, rok, populacji miasta w tym roku, drugi rok, a populacja miasta w tym drugim roku. Przykład pokazuje zmianę populacji między tymi dwoma latami. Z danych dostępnych z krotki, nie jesteśmy obojętni na obszar miasta, i znamy nazwę miasta i dwie daty w czasie projektowania. W rezultacie jesteśmy zainteresowani tylko dwie wartości populacji przechowywane w krotki i może obsługiwać jego pozostałe wartości jako odrzuca.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a>Dekonstrukcja typów zdefiniowanych przez użytkownika

C# nie oferuje wbudowanej obsługi dekonstrukcji typów nieprzeznaczających krotki. Jednak jako autor klasy, struktury lub interfejsu, można zezwolić wystąpienia typu, które mają być zdekonstruowane `Deconstruct` przez implementację jednej lub więcej metod. Metoda zwraca void, a każda wartość, która ma zostać zdekonstruowana, jest wskazywana przez parametr [out](language-reference/keywords/out-parameter-modifier.md) w podpisie metody. Na przykład następująca `Deconstruct` `Person` metoda klasy zwraca imię pierwszego, środkowego i nazwiska:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Następnie można zdekonstruować `Person` wystąpienie `p` klasy o nazwie z przypisaniem, takie jak następujące:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Poniższy przykład przeciąża `Deconstruct` metodę zwracania różnych kombinacji właściwości `Person` obiektu. Zwrot poszczególnych przeciążeń:

- Imię i nazwisko.
- Imię pierwsze, ostatnie i drugie.
- Imię, nazwisko, nazwa miasta i nazwa państwa.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Ponieważ można przeciążyć `Deconstruct` metodę, aby odzwierciedlić grupy danych, które `Deconstruct` są powszechnie wyodrębniane z obiektu, należy uważać, aby zdefiniować metody z podpisów, które są charakterystyczne i jednoznaczne. Wiele `Deconstruct` metod, które mają `out` taką samą liczbę `out` parametrów lub taką samą liczbę i typ parametrów w innej kolejności może powodować zamieszanie.

Przeciążona `Deconstruct` metoda w poniższym przykładzie ilustruje jedno możliwe źródło zamieszania. Pierwsze przeciążenie zwraca imię, drugie imię, nazwisko i `Person` wiek obiektu w tej kolejności. Drugie przeciążenie zwraca informacje o nazwie tylko wraz z rocznym dochodem, ale imię pierwsze, środkowe i nazwisko są w innej kolejności. Ułatwia to mylić kolejność argumentów podczas dekonstrukcji `Person` wystąpienia.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Dekonstrukcja typu zdefiniowanego przez użytkownika za pomocą odrzutów

Podobnie jak w przypadku [krotek,](#deconstructing-tuple-elements-with-discards)można użyć odrzutów, aby `Deconstruct` zignorować wybrane elementy zwrócone metodą. Każdy odrzut jest definiowany\_przez zmienną o nazwie " ", a pojedyncza operacja dekonstrukcji może zawierać wiele odrzutów.

Poniższy przykład dekonstruuje `Person` obiekt na cztery ciągi (imię i nazwisko, miasto i stan), ale odrzuca nazwisko i stan.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Dekonstrukcja typu zdefiniowanego przez użytkownika za pomocą metody rozszerzenia

Jeśli nie został autor klasy, struktury lub interfejsu, nadal można zdekonstruować obiekty tego `Deconstruct` typu, implementując jedną lub więcej [metod rozszerzenia,](programming-guide/classes-and-structs/extension-methods.md) aby zwrócić wartości, w których jesteś zainteresowany.

Poniższy przykład definiuje `Deconstruct` dwie metody <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> rozszerzenia dla klasy. Pierwszy zwraca zestaw wartości, które wskazują właściwości, w tym jej typ, czy jest statyczne lub wystąpienie, czy jest tylko do odczytu i czy jest indeksowany. Drugi wskazuje dostępność obiektu. Ponieważ dostępność get i set akcesory mogą się różnić, wartości logiczne wskazują, czy właściwość ma oddzielne get i set akcesorów i, jeśli tak, czy mają taką samą dostępność. Jeśli istnieje tylko jeden akcesor lub zarówno get i `access` set akcesor mają taką samą dostępność, zmienna wskazuje dostępność właściwości jako całości. W przeciwnym razie dostępność get i set akcesory są wskazywane przez `getAccess` i `setAccess` zmienne.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Zobacz też

- [Odrzucenia](discards.md)
- [Krotki](tuples.md)
