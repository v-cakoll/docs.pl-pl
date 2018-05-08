---
title: Deconstructing krotek i innych typów
description: Dowiedz się, jak deconstruct krotek i innych typów.
author: rpetrusha
ms.author: ronpet
ms.date: 07/18/2016
ms.assetid: 0b0c4b0f-4a47-4f66-9b8e-f5c63b195960
ms.openlocfilehash: 726a391a4a747e5446e252e669c5b16248a5e0ad
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="deconstructing-tuples-and-other-types"></a>Deconstructing krotek i innych typów #

Krotka zawiera lekki sposób pobierania wiele wartości z wywołania metody. Jednak po pobraniu spójnej kolekcji, do obsługi jego poszczególne elementy. Na podstawie elementów — jest to obciążeniem, jak przedstawiono na poniższym przykładzie. `QueryCityData` Metoda zwraca krotka 3 i wszystkich jego elementów jest przypisany do zmiennej w oddzielnych operacji.

[!code-csharp[WithoutDeconstruction](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple1.cs)]

Pobieranie wielu pól i wartości właściwości z obiektu może być skomplikowane jednakowo: należy przypisać wartość pola lub właściwości do zmiennej na podstawie elementu członkowskiego elementu członkowskiego. 

Począwszy od wersji 7.0 C#, możesz pobrać wiele elementów z spójnej kolekcji lub pobrać wiele pola, właściwości i obliczonych wartości z obiektu w jednym *deconstruct* operacji. Gdy deconstruct spójnej kolekcji, jego elementy są przypisywane do poszczególnych zmiennych. Gdy deconstruct obiektu, można przypisać wybranych wartości poszczególnych zmiennych. 

## <a name="deconstructing-a-tuple"></a>Deconstructing spójnych kolekcji

C# funkcje wbudowane obsługę deconstructing krotek, co umożliwia rozpakować wszystkie elementy w spójnej kolekcji w ramach jednej operacji. Ogólna składnia deconstructing Krotka jest podobny do składni do definiowania jedną: ujmij zmienne, do których każdy element ma być przypisana w nawiasach po lewej stronie instrukcji przypisania. Na przykład następująca instrukcja przypisuje elementy krotka 4 do czterech oddzielnych zmiennych:

```csharp
var (name, address, city, zip) = contact.GetAddressInfo();
```

Istnieją trzy sposoby deconstruct spójnych kolekcji:

- Można jawnie deklarować typu każdego pola w nawiasach. W poniższym przykładzie użyto takie podejście do deconstruct krotki 3 zwrócony przez `QueryCityData` metody.

    [!code-csharp[Deconstruction-Explicit](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple2.cs#1)]

- Można użyć `var` — słowo kluczowe, tak że C# wnioskuje typ każdej zmiennej. Możesz umieścić `var` — słowo kluczowe poza nawiasów. W poniższym przykładzie użyto wnioskowanie o typie, gdy deconstructing krotki 3 zwrócony przez `QueryCityData` metody.
 
    [!code-csharp[Deconstruction-Infer](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple3.cs#1)]

    Można również użyć `var` — słowo kluczowe indywidualnie z dowolnego lub wszystkich deklaracji zmiennych wewnątrz nawiasów. 

    [!code-csharp[Deconstruction-Infer-Some](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple4.cs#1)]

    To jest skomplikowane i nie jest zalecane.

- Ponadto może deconstruct spójnej kolekcji do zmiennych, które już zadeklarowany.

    [!code-csharp[Deconstruction-Declared](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-tuple5.cs#1)]

Zauważ, że nie można określić określonego typu poza nawiasy, nawet w przypadku każdego pola w spójnej kolekcji ma tego samego typu. Generuje błąd kompilatora CS8136 "Deconstruction formularza"var (...)"nie zezwala na określony typ dla"var".".

Należy pamiętać, że należy również przypisać każdy element spójna kolekcja znajdująca się do zmiennej. W przypadku pominięcia elementów, kompilator generuje błąd CS8132 "Nie może deconstruct spójnych kolekcji z elementów" x"do zmiennych"y"."

Należy pamiętać, że nie można mieszać deklaracje i przypisania do istniejących zmiennych po lewej stronie deconstruction. Kompilator generuje błąd CS8184 "deconstruction nie można mieszać wyrażeń z lewego-nadwozia1-strony i deklaracje". gdy członków obejmują zmienne nowo zadeklarowane i istniejące.

## <a name="deconstructing-tuple-elements-with-discards"></a>Odrzuca deconstructing spójnej kolekcji elementów z

Często zdarza się deconstructing krotka, interesują Cię wartości tylko niektórych elementów. Począwszy od wersji 7.0 C#, możesz korzystać C# dla obsługi *odrzuca*, które są zmienne tylko do zapisu wartości, którego wybrano opcję Ignoruj. Odrzucenia jest wskazywany przez się od znaku podkreślenia ("\_") w ramach przypisania. Można odrzucić dowolną liczbę wartości jak; wszystkie są reprezentowane przez jeden odrzucenia, `_`.

Poniższy przykład przedstawia użycie spójnych kolekcji zawierający odrzucenia. `QueryCityDataForYears` Metoda zwraca krotka 6 nazwą miasta, jego obszar, roku, miasta wypełniania tego roku, drugiego roku i wypełniania Miasto drugiego roku. W przykładzie zmiany w populacji między te dwa lata. Danych dostępne w spójnej kolekcji, jesteśmy unconcerned z obszarem mieście i wiemy, nazwę miejscowości i dwiema datami w czasie projektowania. W związku z tym możemy tylko w przypadku zainteresowani dwa wypełniania wartościami przechowywanymi w spójnej kolekcji, a może obsłużyć pozostałych wartości jako odrzucenia.  

[!code-csharp[Tuple-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/discard-tuple1.cs)]

### <a name="deconstructing-user-defined-types"></a>Deconstructing typy danych zdefiniowane przez użytkownika

Typy parametrów nie nie oferuje wbudowaną obsługę odrzuca. Jednak autor klasy, struktury lub interfejsu, można zezwolić wystąpień typu, który ma być deconstructed zaimplementowanie co najmniej jeden `Deconstruct` metody. Metoda zwraca wartość typu void i każdej wartości można deconstructed jest określane przez [limit](language-reference/keywords/out-parameter-modifier.md) parametru w podpisie metody. Na przykład następująca `Deconstruct` metody `Person` klasy zwraca nazwę pierwszego, drugie imię i nazwisko:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#1)]

Następnie można deconstruct wystąpienia `Person` klasy o nazwie `p` z przydziałem podobnie do następującej:

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class1.cs#2)]

Następujący przykład przeciążeń `Deconstruct` metodę, aby zwrócić różnych kombinacji właściwości `Person` obiektu. Zwróć poszczególnych przeciążenia:

- Imię i nazwisko.
- First, last i drugie imię.
- Podaj pierwsze imię, nazwisko, nazwę miejscowości i nazwę stanu.

[!code-csharp[Class-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-class2.cs)]

Ponieważ można przeciążać `Deconstruct` metody w celu uwzględnienia grupy danych, które zwykle są wyodrębniane z obiektu należy zachować ostrożność zdefiniować `Deconstruct` metod podpisy charakterystyczne i jednoznaczny. Wiele `Deconstruct` metod, które mają taką samą liczbę `out` parametrów lub taka sama liczbę i typ `out` parametrów w innej kolejności może spowodować ryzyko pomyłek. 

Przeciążone `Deconstruct` metody w poniższym przykładzie przedstawiono jeden możliwe źródło pomyłek. Zwraca pierwszy przeciążenia imię, drugie imię, nazwisko i wiek `Person` obiektu w podanej kolejności. Drugi przeciążenia zwraca informacje o nazwę tylko wraz z rocznego dochodu, ale nazwa pierwszego, drugie imię i nazwisko są w innym porządku. Dzięki temu łatwo pomylić Kolejność argumentów, gdy deconstructing `Person` wystąpienia.

[!code-csharp[Deconstruct-ambiguity](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-ambiguous.cs)]

## <a name="deconstructing-a-user-defined-type-with-discards"></a>Typ zdefiniowany przez użytkownika z deconstructing odrzuca

Podobnie jak w [krotek](#deconstructing-tuple-elements-with-discards), można zignorować wybranych elementów zwróconych przez odrzucenia `Deconstruct` metody. Każdy odrzucenia jest definiowana za pomocą zmiennej o nazwie "\_", i operacją pojedynczego deconstruction może obejmować wiele odrzucenia.

Poniższy przykład deconstructs `Person` obiektu do czterech ciągów (imiona i nazwiska, miasta i stan) ale odrzuca nazwisko i stanu.

[!code-csharp[Class-discard](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/class-discard1.cs#1)]

## <a name="deconstructing-a-user-defined-type-with-an-extension-method"></a>Deconstructing typu zdefiniowanego przez użytkownika z metody rozszerzenia

Jeśli nie możesz tworzyć klasy, struktury lub interfejsu, można nadal deconstruct obiekty tego typu, implementując co najmniej jeden `Deconstruct` [metody rozszerzenia](programming-guide/classes-and-structs/extension-methods.md) zwracać wartości, w których Cię. 

W poniższym przykładzie zdefiniowano dwa `Deconstruct` metody rozszerzenia dla <xref:System.Reflection.PropertyInfo?displayProperty=nameWithType> klasy. Pierwszy zwraca zestaw wartości, których wskazania charakterystyki właściwości, w tym jego typ jest statyczny lub wystąpienia, czy jest tylko do odczytu i czy jest indeksowany. Drugi wskazuje właściwość ułatwień dostępu. Ponieważ dostępność elementu get i metody dostępu set może się różnić, wartościami logicznymi wskazują, czy właściwość zawiera osobne get i set metody dostępu i jeśli tak, czy mają one tą samą dostępnością. Czy istnieje tylko jedną metodę dostępu zarówno get, jak i metody dostępu set mieć tą samą dostępnością `access` zmienna wskazuje dostępność właściwość jako całość. W przeciwnym razie wartość dostępność get i set metody dostępu są oznaczone accessaccessibility jest określane przez `getAccess` i `setAccess` zmiennych.

[!code-csharp[Extension-deconstruct](../../samples/snippets/csharp/programming-guide/deconstructing-tuples/deconstruct-extension1.cs)]
 
## <a name="see-also"></a>Zobacz także
[Odrzuca](discards.md)   
[Krotki](tuples.md)  
