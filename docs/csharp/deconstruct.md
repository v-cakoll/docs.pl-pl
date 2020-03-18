---
title: Dekonstrukcja krotek i innych typów
description: Dowiedz się, jak dekonstruować krotek i innych typów.
ms.technology: csharp-fundamentals
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 23d193faf9702628698fe558f6667aeb130e8916
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "73100670"
---
# <a name="deconstructing-tuples-and-other-types"></a>Dekonstrukcja krotek i innych typów

Krotka zapewnia lekki sposób pobierania wielu wartości z wywołania metody. Ale po pobraniu krotki, trzeba obsługiwać jej poszczególnych elementów. Wykonywanie tego na podstawie elementu po elemencie jest kłopotliwe, jak pokazano w poniższym przykładzie. Metoda `QueryCityData` zwraca 3-krotki, a każdy z jej elementów jest przypisany do zmiennej w oddzielnej operacji.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Pobieranie wielu wartości pól i właściwości z obiektu może być równie kłopotliwe: należy przypisać wartość pola lub właściwości do zmiennej na podstawie elementu członkowskiego.

Począwszy od języka C# 7.0, można pobrać wiele elementów z krotki lub pobrać wiele pól, właściwości i obliczone wartości z obiektu w jednej operacji *dekonstrukcji.* Podczas dekonstrukcji krotki, należy przypisać jej elementy do poszczególnych zmiennych. Podczas dekonstrukcji obiektu wybrane wartości są przypisywane do poszczególnych zmiennych.

## <a name="deconstructing-a-tuple"></a>Dekonstrukcja krotki

C# funkcje wbudowanej obsługi dekonstrukcji krotek, który pozwala rozpakować wszystkie elementy w krotce w jednej operacji. Ogólna składnia dekonstrukcji krotki jest podobna do składni definiowania: należy ująć zmienne, do których każdy element ma być przypisany w nawiasach po lewej stronie instrukcji przypisania. Na przykład następująca instrukcja przypisuje elementy 4-krotki do czterech oddzielnych zmiennych:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Istnieją trzy sposoby dekonstrukcji krotki:

- Można jawnie zadeklarować typ każdego pola w nawiasach. W poniższym przykładzie użyto tego podejścia do dekonstrukcji `QueryCityData` 3-krotki zwracanej przez metodę.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Można użyć `var` słowa kluczowego, tak aby C# wnioskuje typ każdej zmiennej. Słowo `var` kluczowe można umieścić poza nawiasami. W poniższym przykładzie użyto wnioskowania o typie podczas dekonstrukcji 3-krotki zwracanej przez `QueryCityData` metodę.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Można również użyć `var` słowa kluczowego pojedynczo z dowolną lub wszystkimi deklaracjami zmiennych w nawiasach.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    Jest to uciążliwe i nie jest zalecane.

- Wreszcie można zdekonstruować krotki do zmiennych, które zostały już zadeklarowane.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Należy zauważyć, że nie można określić określonego typu poza nawiasami, nawet jeśli każde pole w krotce ma ten sam typ. Spowoduje to wygenerowanie błędu kompilatora CS8136, "Dekonstrukcja 'var (...)" formularz nie zezwala na określony typ dla 'var'.".

Należy zauważyć, że należy również przypisać każdy element krotki do zmiennej. Jeśli pominiesz jakiekolwiek elementy, kompilator generuje błąd CS8132, "Nie można zdekonstruować krotki elementów "x" na zmienne 'y'.

Należy zauważyć, że nie można mieszać deklaracji i przypisań z istniejącymi zmiennymi po lewej stronie dekonstrukcji. Kompilator generuje błąd CS8184, "dekonstrukcja nie może mieszać deklaracji i wyrażeń po lewej stronie." gdy elementy członkowskie zawierają nowo zadeklarowane i istniejące zmienne.

## <a name="deconstructing-tuple-elements-with-discards"></a>Dekonstrukcja elementów krotki za pomocą odrzutów

Często podczas dekonstrukcji krotki interesują Cię wartości tylko niektórych elementów. Począwszy od języka C# 7.0, można skorzystać z obsługi języka C#dla *odrzutów*, które są zmienne tylko do zapisu, których wartości zostały wybrane do zignorowania. Odrzucenie jest oznaczone znakiem podkreślenia\_(" ") w przypisaniu. Można odrzucić dowolną liczbę wartości; wszystkie są reprezentowane przez pojedyncze `_`odrzucenie, .

Poniższy przykład ilustruje użycie krotek z odrzutami. Metoda `QueryCityDataForYears` zwraca 6-krotka z nazwą miasta, jego obszar, rok, ludności miasta w tym roku, drugi rok, a ludności miasta na drugi rok. Przykład pokazuje zmianę populacji między tymi dwoma latami. Z danych dostępnych z krotki, nie jesteśmy zainteresowani obszarem miasta, znamy nazwę miasta i dwie daty w czasie projektowania. W rezultacie jesteśmy zainteresowani tylko dwie wartości populacji przechowywane w krotce i może obsługiwać jego pozostałe wartości jako odrzuty.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

## <a name="deconstructing-user-defined-types"></a>Dekonstrukcja typów zdefiniowanych przez użytkownika

C# nie oferuje wbudowaną obsługę dekonstrukcji typów niekrocliki. Jednak jako autor klasy, struktury lub interfejsu, można zezwolić na wystąpienia typu, które mają być `Deconstruct` zdekonstruowane przez implementowanie jednej lub więcej metod. Metoda zwraca void, a każda wartość do zdekonstruowania jest wskazywana przez parametr [out](language-reference/keywords/out-parameter-modifier.md) w podpisie metody. Na przykład następująca `Deconstruct` metoda `Person` klasy zwraca imię, środek i nazwisko:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Następnie można zdekonstruować `Person` wystąpienie `p` klasy o nazwie przy pomocą przypisania, takiego jak następujące:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Poniższy przykład przeciąża `Deconstruct` metodę, aby zwrócić różne `Person` kombinacje właściwości obiektu. Powrót poszczególnych przeciążeń:

- Imię i nazwisko.
- Imię, nazwisko i drugie imię.
- Imię, nazwisko, nazwa miasta i nazwa stanu.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Ponieważ można przeciążać metodę w `Deconstruct` celu odzwierciedlenia grup danych, `Deconstruct` które są często wyodrębniane z obiektu, należy uważać, aby zdefiniować metody z podpisami, które są odróżniające i jednoznaczne. Wiele `Deconstruct` metod, które mają `out` taką samą liczbę parametrów `out` lub taką samą liczbę i typ parametrów w innej kolejności może spowodować zamieszanie.

Metoda przeciążona `Deconstruct` w poniższym przykładzie ilustruje jedno możliwe źródło pomyłek. Pierwsze przeciążenie zwraca imię, drugie imię, nazwisko i `Person` wiek obiektu w tej kolejności. Drugie przeciążenie zwraca informacje o nazwie tylko wraz z rocznym dochodem, ale pierwsze, średnie i nazwisko są w innej kolejności. Ułatwia to pomylenie kolejności argumentów podczas `Person` dekonstrukcji wystąpienia.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Dekonstrukcja typu zdefiniowanego przez użytkownika za pomocą odrzutów

Podobnie jak w przypadku [krotek,](#deconstructing-tuple-elements-with-discards)można użyć odrzutów, aby `Deconstruct` zignorować wybrane elementy zwrócone metodą. Każde odrzucenie jest definiowane przez\_zmienną o nazwie " ", a pojedyncza operacja dekonstrukcji może zawierać wiele odrzutów.

Poniższy przykład dekonstruuje `Person` obiekt na cztery ciągi (imię i nazwisko, miasto i stan), ale odrzuca nazwisko i stan.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Dekonstrukcja typu zdefiniowanego przez użytkownika za pomocą metody rozszerzenia

Jeśli nie autor klasy, struktury lub interfejsu, nadal można zdekonstruować obiekty tego `Deconstruct` typu, implementując jedną lub więcej [metod rozszerzenia,](programming-guide/classes-and-structs/extension-methods.md) aby zwrócić wartości, które Cię interesują.

W poniższym przykładzie `Deconstruct` zdefiniowano <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> dwie metody rozszerzenia dla klasy. Pierwszy zwraca zestaw wartości, które wskazują właściwości właściwości, w tym jego typ, czy jest statyczny lub wystąpienie, czy jest tylko do odczytu i czy jest indeksowany. Drugi wskazuje dostępność właściwości. Ponieważ dostępność get i set akcesorów może się różnić, wartości logiczne wskazują, czy właściwość ma oddzielne get i set akcesorów i, jeśli tak, czy mają taką samą dostępność. Jeśli istnieje tylko jeden akcesor lub zarówno get i `access` set akcesor mają taką samą dostępność, zmienna wskazuje dostępność właściwości jako całości. W przeciwnym razie dostępność get i set akcesorów są wskazywane przez `getAccess` i `setAccess` zmiennych.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Zobacz też

- [Odrzucenia](discards.md)
- [Krotek](tuples.md)
