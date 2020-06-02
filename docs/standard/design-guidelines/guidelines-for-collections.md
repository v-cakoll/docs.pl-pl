---
title: Wskazówki dotyczące kolekcji
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: cc853be2310cf72c4eb559f625c6a37a44ed7db8
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/02/2020
ms.locfileid: "84276052"
---
# <a name="guidelines-for-collections"></a>Wskazówki dotyczące kolekcji
Każdy typ przeznaczony specjalnie do manipulowania grupą obiektów, które mają pewną wspólną charakterystykę, może być traktowany jako kolekcja. Jest prawie zawsze odpowiednie dla takich typów do wdrożenia <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601> , dlatego w tej sekcji rozważamy tylko typy implementujące jeden lub oba te interfejsy, które mają być kolekcjami.

 ❌NIE używaj słabo wpisanych kolekcji w publicznych interfejsach API.

 Typ wszystkich wartości zwracanych i parametrów reprezentujących elementy kolekcji musi być dokładnym typem elementu, a nie żadnym z jego typów podstawowych (dotyczy to tylko publicznych członków kolekcji).

 ❌NIE używaj <xref:System.Collections.ArrayList> ani <xref:System.Collections.Generic.List%601> w publicznych interfejsach API.

 Te typy są strukturami danych przeznaczonymi do użycia w wewnętrznej implementacji, a nie w publicznych interfejsach API. `List<T>`jest zoptymalizowany pod kątem wydajności i mocy na koszt czyszczenia interfejsów API i elastyczności. Na przykład jeśli powrócisz `List<T>` , nie będziesz mieć możliwości otrzymywania powiadomień, gdy kod klienta modyfikuje kolekcję. Ponadto program `List<T>` udostępnia wiele elementów członkowskich, takich jak <xref:System.Collections.Generic.List%601.BinarySearch%2A> , które nie są przydatne ani mają zastosowania w wielu scenariuszach. W poniższych dwóch sekcjach opisano typy (abstrakcje) przeznaczone specjalnie do użycia w publicznych interfejsach API.

 ❌NIE używaj `Hashtable` ani `Dictionary<TKey,TValue>` w publicznych interfejsach API.

 Te typy są strukturami danych przeznaczonymi do użycia w wewnętrznej implementacji. Publiczne interfejsy API powinny używać <xref:System.Collections.IDictionary> , `IDictionary <TKey, TValue>` lub być typu niestandardowego implementującego jeden lub oba interfejsy.

 ❌NIE używaj <xref:System.Collections.Generic.IEnumerator%601> , <xref:System.Collections.IEnumerator> ani innego typu, który implementuje któregokolwiek z tych interfejsów, z wyjątkiem zwracanego typu `GetEnumerator` metody.

 Typy zwracające moduły wyliczające z metod innych niż `GetEnumerator` nie można używać z `foreach` instrukcją.

 ❌NIE należy implementować obu `IEnumerator<T>` i `IEnumerable<T>` tego samego typu. To samo dotyczy interfejsów nierodzajowych `IEnumerator` i `IEnumerable` .

## <a name="collection-parameters"></a>Parametry kolekcji
 ✔️ używać typu najmniej wyspecjalizowanego możliwego jako typ parametru. Większość elementów członkowskich przyjmujących kolekcje jako parametry używają `IEnumerable<T>` interfejsu.

 ❌Należy unikać używania <xref:System.Collections.Generic.ICollection%601> lub <xref:System.Collections.ICollection> jako parametru tylko w celu uzyskania dostępu do `Count` właściwości.

 Zamiast tego należy rozważyć użycie `IEnumerable<T>` lub `IEnumerable` i dynamiczne sprawdzenie, czy obiekt implementuje `ICollection<T>` lub `ICollection` .

## <a name="collection-properties-and-return-values"></a>Właściwości kolekcji i wartości zwracane
 ❌Nie udostępniaj właściwości kolekcji settable.

 Użytkownicy mogą zastąpić zawartość kolekcji, czyszcząc najpierw kolekcję, a następnie dodając nową zawartość. Jeśli zastępowanie całej kolekcji jest typowym scenariuszem, rozważ dostarczenie `AddRange` metody do kolekcji.

 ✔️ używać `Collection<T>` lub podklasy `Collection<T>` dla właściwości lub zwracanych wartości reprezentujących kolekcje odczytu/zapisu.

 Jeśli nie `Collection<T>` spełnia pewnej wymagania (np. kolekcja nie może być zaimplementowana <xref:System.Collections.IList> ), Użyj kolekcji niestandardowej przez implementację `IEnumerable<T>` , `ICollection<T>` lub <xref:System.Collections.Generic.IList%601> .

 ✔️ do użycia <xref:System.Collections.ObjectModel.ReadOnlyCollection%601> , podklasa `ReadOnlyCollection<T>` lub w rzadkich przypadkach `IEnumerable<T>` dla właściwości lub wartości zwracanych reprezentujących kolekcje tylko do odczytu.

 Ogólnie rzecz biorąc `ReadOnlyCollection<T>` . Jeśli nie spełnia pewnej wymagania (np. kolekcja nie może być zaimplementowana `IList` ), Użyj kolekcji niestandardowej przez implementację `IEnumerable<T>` , `ICollection<T>` lub `IList<T>` . Jeśli implementujesz niestandardową kolekcję tylko do odczytu, zaimplementuj `ICollection<T>.IsReadOnly` ją w celu zwrócenia `true` .

 W przypadkach, w których wiadomo, że jedynym scenariuszem, który będzie potrzebny do obsługi, jest iteracja tylko do przodu, można po prostu użyć `IEnumerable<T>` .

 ✔️ ROZWAŻYĆ użycie podklas ogólnych kolekcji podstawowych zamiast bezpośredniego używania kolekcji.

 Pozwala to na lepszą nazwę i Dodawanie członków pomocników, których nie ma w typach kolekcji podstawowej. Jest to szczególnie przydatne w przypadku interfejsów API wysokiego poziomu.

 ✔️ ROZWAŻYĆ zwrócenie podklasy `Collection<T>` lub `ReadOnlyCollection<T>` z bardzo często używanych metod i właściwości.

 Dzięki temu można dodać metody pomocnika lub zmienić implementację kolekcji w przyszłości.

 ✔️ ROZWAŻYĆ użycie kolekcji z podzbiorem, jeśli elementy przechowywane w kolekcji mają unikatowe klucze (nazwy, identyfikatory itp.). Kolekcje z kluczami są kolekcjami, które można indeksować za pomocą liczby całkowitej i klucza i są zwykle zaimplementowane przez dziedziczenie z `KeyedCollection<TKey,TItem>` .

 Kolekcje z równoważeniem rozmiaru zazwyczaj mają większe rozmiary pamięci i nie powinny być używane, jeśli obciążenie pamięci zawiera zalety kluczy.

 ❌Nie zwracaj wartości null z właściwości kolekcji ani z metod zwracających kolekcje. W zamian Zwróć pustą kolekcję lub pustą tablicę.

 Ogólna reguła to wartość null i puste (0 elementów) kolekcje lub tablice powinny być traktowane jako takie same.

### <a name="snapshots-versus-live-collections"></a>Migawki a kolekcje na żywo
 Kolekcje reprezentujące stan w pewnym momencie są nazywane kolekcjami migawek. Na przykład Kolekcja zawierająca wiersze zwrócone z kwerendy bazy danych będzie migawką. Kolekcje, które zawsze reprezentują bieżący stan, są nazywane kolekcjami dynamicznymi. Na przykład kolekcja `ComboBox` elementów jest kolekcją dynamiczną.

 ❌Nie zwracaj kolekcji migawek z właściwości. Właściwości powinny zwracać kolekcje dynamiczne.

 Metody pobierające właściwości powinny być bardzo lekkimi operacjami. Zwracanie migawki wymaga utworzenia kopii kolekcji wewnętrznej w operacji O (n).

 ✔️ używać kolekcji migawek lub na żywo `IEnumerable<T>` (lub jego podtypu) do reprezentowania kolekcji, które są nietrwałe (tj. mogą ulec zmianie bez jawnego modyfikowania kolekcji).

 Ogólnie rzecz biorąc, wszystkie kolekcje reprezentujące zasób udostępniony (np. pliki w katalogu) są nietrwałe. Takie kolekcje są bardzo trudne lub niemożliwe do wdrożenia jako kolekcje dynamiczne, chyba że implementacja to po prostu moduł wyliczający tylko do przodu.

## <a name="choosing-between-arrays-and-collections"></a>Wybór między tablicami a kolekcjami
 ✔️ Preferuj kolekcje za pośrednictwem tablic.

 Kolekcje zapewniają większą kontrolę nad zawartością, mogą być rozwijane z upływem czasu i są bardziej użyteczne. Ponadto nie zaleca się używania tablic dla scenariuszy tylko do odczytu, ponieważ koszt klonowania tablicy jest zabroniony. Badania użyteczności wykazały, że niektórzy deweloperzy są bardziej wygodni przy użyciu interfejsów API opartych na kolekcji.

 Jeśli jednak tworzysz interfejsy API niskiego poziomu, lepiej jest używać tablic do scenariuszy odczytu i zapisu. Tablice mają mniejsze rozmiary pamięci, co ułatwia zmniejszenie zestawu roboczego i dostęp do elementów w tablicy jest szybszy, ponieważ jest zoptymalizowany pod kątem środowiska uruchomieniowego.

 ✔️ ROZWAŻYĆ użycie tablic w interfejsach API niskiego poziomu w celu zminimalizowania zużycia pamięci i zmaksymalizowania wydajności.

 ✔️ Używaj tablic bajtowych zamiast kolekcji bajtów.

 ❌NIE używaj tablic dla właściwości, jeśli właściwość będzie musiała zwracać nową tablicę (np. kopię tablicy wewnętrznej) za każdym razem, gdy wywoływana jest metoda pobierająca właściwości.

## <a name="implementing-custom-collections"></a>Implementowanie kolekcji niestandardowych
 ✔️ NALEŻY rozważyć dziedziczenie z `Collection<T>` , `ReadOnlyCollection<T>` lub `KeyedCollection<TKey,TItem>` podczas projektowania nowych kolekcji.

 ✔️ Implementowanie `IEnumerable<T>` podczas projektowania nowych kolekcji. Rozważ zaimplementowanie `ICollection<T>` lub nawet `IList<T>` tam, gdzie jest to zrozumiałe.

 Podczas wdrażania takiej niestandardowej kolekcji postępuj zgodnie z wzorcem interfejsu API ustanowionym przez `Collection<T>` i `ReadOnlyCollection<T>` tak blisko jak to możliwe. Oznacza to, że Zaimplementuj jawnie te same elementy członkowskie, nazwij te parametry, jak te dwie nazwy kolekcji i tak dalej.

 ✔️ ROZWAŻYĆ wdrożenie interfejsów kolekcji niegenerycznych ( `IList` i `ICollection` ), jeśli kolekcja często będzie przenoszona do interfejsów API przyjmujących te interfejsy jako dane wejściowe.

 ❌UNIKAj implementowania interfejsów kolekcji dla typów z złożonymi interfejsami API, które nie są związane z koncepcją kolekcji.

 ❌NIE Dziedzicz z nieogólnych kolekcji podstawowych, takich jak `CollectionBase` . Użyj `Collection<T>` , `ReadOnlyCollection<T>` , i `KeyedCollection<TKey,TItem>` zamiast.

### <a name="naming-custom-collections"></a>Nazewnictwo kolekcji niestandardowych
 Kolekcje (typy, które implementują `IEnumerable` ) są tworzone głównie z dwóch powodów: (1), aby utworzyć nową strukturę danych z operacjami specyficznymi dla określonej struktury i często różnymi charakterystykami wydajności niż istniejące struktury danych (np.,, <xref:System.Collections.Generic.List%601> <xref:System.Collections.Generic.LinkedList%601> <xref:System.Collections.Generic.Stack%601> ) i (2) do tworzenia wyspecjalizowanej kolekcji do przechowywania określonego zestawu elementów (np. <xref:System.Collections.Specialized.StringCollection> ). Struktury danych są najczęściej używane w wewnętrznej implementacji aplikacji i bibliotek. Wyspecjalizowane kolekcje są głównie udostępniane w interfejsach API (jako typy właściwości i parametrów).

 ✔️ Użyj sufiksu "dictionary" w nazwach abstrakcji implementujących `IDictionary` lub `IDictionary<TKey,TValue>` .

 ✔️ Użyj sufiksu "Kolekcja" w nazwach typów implementujących `IEnumerable` (lub dowolnych z jego obiektów podrzędnych) i reprezentujących listę elementów.

 ✔️ używać odpowiedniej nazwy struktury danych dla niestandardowych struktur danych.

 ❌UNIKAj używania dowolnych sufiksów oznaczających konkretną implementację, taką jak "LinkedList" lub "Hashtable", w nazwach abstrakcji kolekcji.

 ✔️ Rozważ umieszczenie prefiksu nazw kolekcji z nazwą typu elementu. Na przykład kolekcja przechowująca elementy typu `Address` (implementująca `IEnumerable<Address>` ) powinna mieć nazwę `AddressCollection` . Jeśli typ elementu to interfejs, prefiks "I" typu elementu można pominąć. W ten sposób kolekcja <xref:System.IDisposable> elementów może być wywoływana `DisposableCollection` .

 ✔️ Rozważ użycie prefiksu "ReadOnly" w nazwach kolekcji tylko do odczytu, Jeśli odpowiednia kolekcja może zostać dodana lub już istnieje w strukturze.

 Na przykład Kolekcja ciągów tylko do odczytu powinna być wywoływana `ReadOnlyStringCollection` .

 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*

 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*

## <a name="see-also"></a>Zobacz także

- [Wskazówki dotyczące projektowania struktury](index.md)
- [Wskazówki dotyczące użycia](usage-guidelines.md)
