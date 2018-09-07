---
title: Dekonstrukcja krotek i innych typów
description: Dowiedz się, jak dekonstruować krotki a innymi typami danych.
author: rpetrusha
ms.author: ronpet
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 48724c65de4fe71294eb5c61c1891d9d56c9b5a4
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/07/2018
ms.locfileid: "44079623"
---
# <a name="deconstructing-tuples-and-other-types"></a>Dekonstrukcja krotek i innych typów

Spójna kolekcja zapewnia sposób lekki Pobieranie wielu wartości z wywołania metody. Jednak po pobraniu spójnej kolekcji, trzeba obsługiwać poszczególne elementy. Na podstawie elementów — jest to skomplikowane, co ilustruje poniższy przykład. `QueryCityData` Metoda zwróci wartość 3-krotka, a każdy z jej elementów jest przypisany do zmiennej w oddzielnych operacji.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Pobieranie wielu pól i wartości właściwości z obiektu może być kłopotliwe równie: należy przypisać wartość pola lub właściwości do zmiennej na podstawie elementu członkowskiego elementu członkowskiego.

Począwszy od języka C# 7.0, możesz pobrać wiele elementów z spójnej kolekcji lub pobieranie wielu pola, właściwości i obliczonych wartości z obiektu w jednym *dekonstruować* operacji. Gdy można dekonstruować krotki, jego elementy są przypisywane do poszczególnych zmiennych. Gdy obiekt jest dekonstruować, wybranych wartości są przypisywane do poszczególnych zmiennych.

## <a name="deconstructing-a-tuple"></a>Dekonstrukcja krotki

Funkcje języka C# wbudowaną obsługę dekonstrukcja krotek, które umożliwia rozpakować wszystkie elementy w krotce w ramach jednej operacji. Ogólna składnia dekonstrukcja krotki przypomina składnię definiować po jednym alercie: ująć zmienne, do których każdy element ma być przypisana w nawiasach po lewej stronie instrukcji przypisania. Na przykład następująca instrukcja przypisuje elementów krotki 4 do czterech oddzielnych zmiennych:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Istnieją trzy sposoby dekonstruować krotki:

- Można jawnie deklarować typ każdego pola w nawiasach. W poniższym przykładzie użyto tej metody można dekonstruować krotki 3 zwracane przez `QueryCityData` metody.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Możesz użyć `var` — słowo kluczowe, więc w tym C# wnioskuje typ każdej zmiennej. Możesz umieścić `var` — słowo kluczowe poza nawiasy. W poniższym przykładzie użyto wnioskowanie o typie, gdy dekonstrukcja krotki 3 zwracane przez `QueryCityData` metody.

    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Można również użyć `var` — słowo kluczowe za pomocą dowolnego lub wszystkich deklaracji zmiennych wewnątrz nawiasów.

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    To jest skomplikowane i nie jest zalecane.

- Ponadto może dekonstruować krotki do zmiennych, które już zostały zadeklarowane.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Zauważ, że nie można określić określonego typu poza nawiasy, nawet wtedy, gdy każde pole w spójnej kolekcji ma tego samego typu. Spowoduje to wygenerowanie błędu kompilatora CS8136, "Dekonstrukcji"var (...)"dekonstrukcji nie zezwala na specyficzny typ"var".".

Należy pamiętać o tym, należy również przypisać każdego elementu spójnej kolekcji do zmiennej. Jeżeli pominięto żadnych elementów, kompilator generuje błąd CS8132, "Nie można dekonstruować krotki"x"elementów do zmiennych"y"."

Należy pamiętać, że nie można mieszać deklaracji i przypisania do istniejących zmiennych po lewej stronie dekonstrukcji. Kompilator generuje błąd CS8184, "dekonstrukcji nie można mieszać deklaracji i wyrażeń po lewej stronie". Gdy elementy członkowskie obejmują nowo zadeklarowana i istniejących zmienne.

## <a name="deconstructing-tuple-elements-with-discards"></a>Dekonstrukcja krotki elementy z odrzuca

Często w przypadku, gdy dekonstrukcja krotki, interesuje Cię wartości tylko niektóre elementy. Począwszy od języka C# 7.0, możesz korzystać z zalet języka C# w obsługę *odrzuca*, które są zmienne tylko do zapisu wartości, których wybrane do ignorowania. Odrzucenia została wyznaczona przez znak podkreślenia ("\_") w ramach przypisania. Można odrzucić, jak wiele wartości, jak chcesz; wszystkie są reprezentowane przez pojedynczy odrzucenia, `_`.

Poniższy przykład ilustruje użycie spójnych kolekcji zawierający odrzucenia. `QueryCityDataForYears` Metoda zwraca 6-krotka nazwą miasta, jego obszaru, roku, to miasto populację na potrzeby tego roku, drugiego roku i miasta populację na potrzeby tego drugiego roku. W przykładzie pokazano zmianę populacji między te dwa lata. Dane udostępniła spójnej kolekcji, jesteśmy unconcerned z obszarem miasta i wiemy, nazwę miasta i dwiema datami w czasie projektowania. W rezultacie firma Microsoft interesują jedynie wartości dwóch populacji, przechowywane w spójnej kolekcji i może obsługiwać jego pozostałe wartości jako odrzucenia.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

### <a name="deconstructing-user-defined-types"></a>Dekonstrukcja typy zdefiniowane przez użytkownika

Typy non-elementowe spójne kolekcje nie oferuje wbudowaną obsługę odrzuca. Jednak jako autor klasy, struktury lub interfejsu, można zezwolić wystąpienia typu, który ma zostać zdekonstruowana implementując co najmniej jeden `Deconstruct` metody. Metoda zwraca wartość void, a każda wartość, aby zostać zdekonstruowana jest wskazywany przez [się](language-reference/keywords/out-parameter-modifier.md) parametru w podpisie metody. Na przykład następująca `Deconstruct` metody `Person` klasy zwraca nazwę pierwszego, drugie imię i nazwisko:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Następnie można dekonstruować wystąpienie `Person` klasę o nazwie `p` z przydziałem podobnie do poniższego:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Poniższy przykład przeciążenia `Deconstruct` metody zwracają różne kombinacje właściwości `Person` obiektu. Zwróć poszczególnych przeciążeń:

- Imię i nazwisko.
- Pierwsza, ostatnia, a drugie imię.
- Podaj pierwsze imię, nazwisko, nazwę miasta i nazwę stanu.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Ponieważ może doprowadzić do przeciążenia `Deconstruct` metodę, aby odzwierciedlić grupy danych, które często są wyodrębniane z obiektu, należy zachować ostrożność zdefiniować `Deconstruct` metodami z podpisami, które są szczególne i jednoznaczna. Wiele `Deconstruct` metody, które mają taką samą liczbę `out` parametrów lub taka sama liczba i rodzaj `out` parametrów w innej kolejności może nie być jasne.

Przeciążone `Deconstruct` metody w poniższym przykładzie pokazano jedno źródło możliwości popełnienia błędu. Pierwsze przeciążenie zwraca imię, imienia, nazwiska i wieku `Person` obiektów w tej kolejności. Drugie przeciążenie zwraca informacje o nazwie tylko wraz z dochodów rocznych, ale nazwa pierwszego, drugie imię i nazwisko znajdują się w innej kolejności. To ułatwia mylić Kolejność argumentów, gdy dekonstrukcja `Person` wystąpienia.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Dekonstrukcja typu zdefiniowanego przez użytkownika, za pomocą odrzuca

Podobnie jak w przypadku [krotek](#deconstructing-tuple-elements-with-discards), można użyć odrzucenia ignorowanie wybranych elementów zwróconych przez `Deconstruct` metody. Każdy odrzucenia jest zdefiniowany przez zmienną o nazwie "\_", i operacją pojedynczego dekonstrukcji może obejmować wiele odrzucenia.

Poniższy przykład deconstructs `Person` obiektu do czterech ciągów (imiona i nazwiska, miasta i stanu), ale odrzuca nazwisko i stanu.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Dekonstrukcja typ zdefiniowany przez użytkownika za pomocą metody rozszerzenia

Jeśli nie możesz tworzyć klasy, struktury lub interfejsu, nadal można dekonstruować obiektów tego typu przez zaimplementowanie co najmniej jeden `Deconstruct` [metody rozszerzenia](programming-guide/classes-and-structs/extension-methods.md) zwracać wartości, w których interesują.

W poniższym przykładzie zdefiniowano dwa `Deconstruct` metody rozszerzenia dla <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> klasy. Pierwsza zwraca zestaw wartości, które wskazują cechy właściwości, w tym jego typ jest statyczna lub wystąpienia, czy jest tylko do odczytu i czy są indeksowane. Drugi wskazuje właściwości ułatwień dostępu. Ponieważ dostępność metody get i metody dostępu set mogą się różnić, wartościami logicznymi wskazywania, czy właściwość ma oddzielne pobieranie i ustawianie metody dostępu i, jeśli istnieje, czy mają identyczną dostępność. Czy istnieje tylko jedna metoda dostępu zarówno get, jak i metody dostępu set mieć identyczną dostępność `access` zmienna wskazuje dostępność właściwości jako całości. W przeciwnym razie dostępność metody get i set metody dostępu są wskazywane przez accessaccessibility jest wskazywany przez `getAccess` i `setAccess` zmiennych.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]

## <a name="see-also"></a>Zobacz także

- [Odrzucenia](discards.md)
- [Krotki](tuples.md)  
