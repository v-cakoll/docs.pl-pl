---
title: Wytyczne dotyczące kolekcji
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3d73ff726e9ddfe1ec1d16dd020f53445f984fb9
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33578862"
---
# <a name="guidelines-for-collections"></a>Wytyczne dotyczące kolekcji
Dowolny typ zaprojektowany specjalnie w celu manipulowania grupy obiektów o pewne cechy wspólne mogą zostać uwzględnione w kolekcji. Prawie zawsze jest ona odpowiednia dla takich typów do zaimplementowania <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>, więc w tej sekcji możemy tylko należy wziąć pod uwagę typy Implementowanie jedno lub oba te interfejsy można kolekcje.  
  
 **X DO NOT** w publicznych interfejsach API za pomocą lekko typu kolekcji.  
  
 Typ wszystkich zwracanych wartości i parametry przedstawiające elementy kolekcji powinna być typu elementu dokładne, nie dowolnego z jego typów podstawowych (dotyczy to tylko publiczne elementy członkowskie kolekcji).  
  
 **X DO NOT** użyj <xref:System.Collections.ArrayList> lub <xref:System.Collections.Generic.List%601> w publicznych interfejsach API.  
  
 Te typy są przeznaczone do użycia w wewnętrznej implementacji nie znajduje się w publicznych interfejsach API struktury danych. `List<T>` jest zoptymalizowana pod kątem wydajności i zasilania kosztem czystości interfejsów API i elastyczność. Na przykład, jeśli `List<T>`, nie kiedykolwiek będzie Aby otrzymywać powiadomienia, gdy kod klienta modyfikuje kolekcję. Ponadto `List<T>` udostępnia wiele elementów członkowskich, takich jak <xref:System.Collections.Generic.List%601.BinarySearch%2A>, które nie są przydatne lub mające zastosowanie w wielu scenariuszach. W poniższych sekcjach dwóch opisano typy (abstrakcje) przeznaczony specjalnie do użytku w publicznych interfejsach API.  
  
 **X DO NOT** użyj `Hashtable` lub `Dictionary<TKey,TValue>` w publicznych interfejsach API.  
  
 Te typy są przeznaczone do użycia w implementacji wewnętrznej struktury danych. Należy używać w publicznych interfejsach API <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, lub niestandardowy typ wdrażanie jednego lub obu interfejsów.  
  
 **X DO NOT** użyj <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, lub innego typu, który implementuje jednej z tych interfejsów, z wyjątkiem jako typ zwracany `GetEnumerator` metody.  
  
 Typy zwracania wyliczenia z metod innych niż `GetEnumerator` nie można używać z `foreach` instrukcji.  
  
 **X DO NOT** implementować jednocześnie `IEnumerator<T>` i `IEnumerable<T>` do tego samego typu. To samo dotyczy interfejsów nierodzajowe `IEnumerator` i `IEnumerable`.  
  
## <a name="collection-parameters"></a>Kolekcja parametrów  
 **✓ DO** używać jak specjalizowany najmniej typu jako parametr typu. Większość elementów członkowskich, biorąc kolekcje, jak używać parametrów `IEnumerable<T>` interfejsu.  
  
 **X AVOID** przy użyciu <xref:System.Collections.Generic.ICollection%601> lub <xref:System.Collections.ICollection> jako parametr tylko w celu uzyskania dostępu `Count` właściwości.  
  
 Zamiast tego Rozważ użycie `IEnumerable<T>` lub `IEnumerable` i dynamicznie sprawdzanie, czy obiekt implementuje `ICollection<T>` lub `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Kolekcja właściwości i wartości zwracane  
 **X DO NOT** dostarczenie kolekcji można ustawić właściwości.  
  
 Użytkownicy mogą zastąpić zawartość kolekcji przez wyczyszczenie kolekcji najpierw, a następnie dodanie nowej zawartości. Jeśli zastąpienie całej kolekcji jest typowy scenariusz, rozważ podanie `AddRange` metody w kolekcji.  
  
 **✓ DO** użyj `Collection<T>` lub podklasa klasy of `Collection<T>` dla właściwości lub return wartości reprezentujące kolekcje odczytu/zapisu.  
  
 Jeśli `Collection<T>` nie spełnia wymagań dotyczących niektórych (np. Kolekcja nie musi zawierać <xref:System.Collections.IList>), użyj kolekcji niestandardowej zaimplementowanie `IEnumerable<T>`, `ICollection<T>`, lub <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** użyj <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, podklasa klasy `ReadOnlyCollection<T>`, lub w rzadkich przypadkach `IEnumerable<T>` dla właściwości lub return wartości reprezentujące kolekcji tylko do odczytu.  
  
 Ogólnie rzecz biorąc, preferowane `ReadOnlyCollection<T>`. Jeśli go nie spełnia wymagań dotyczących niektórych (np. Kolekcja nie musi zawierać `IList`), użyj kolekcji niestandardowej zaimplementowanie `IEnumerable<T>`, `ICollection<T>`, lub `IList<T>`. Implementowanie niestandardowych kolekcji tylko do odczytu, należy wdrożyć `ICollection<T>.IsReadOnly` do zwrócenia `true`.  
  
 W przypadkach, gdy masz pewność, że jedyny scenariusz, w coraz można obsługiwać jest tylko do przodu iteracji, możesz użyć `IEnumerable<T>`.  
  
 **✓ CONSIDER** za pomocą podklasy kolekcje podstawowej ogólne zamiast bezpośrednio przy użyciu kolekcji.  
  
 Dzięki temu lepsze nazwy i dodawania elementów członkowskich pomocnika, które nie występują na typy podstawowe kolekcji. Jest to szczególnie dotyczy wysokiego poziomu interfejsów API.  
  
 **✓ CONSIDER** zwracanie podklasą `Collection<T>` lub `ReadOnlyCollection<T>` z bardzo często używanych metod i właściwości.  
  
 To umożliwi dodawanie metody pomocnicze lub zmień implementację kolekcji w przyszłości.  
  
 **✓ CONSIDER** przy użyciu kolekcji kluczem, jeśli elementy przechowywane w kolekcji ma unikatowy kluczy (nazwy, identyfikatory itp.). Kolekcje zabezpieczone kluczami są kolekcjami, które mogą być indeksowane według zarówno całkowitą, jak i klucz i są zwykle implementowany przez dziedziczenie z `KeyedCollection<TKey,TItem>`.  
  
 Kolekcje zabezpieczone kluczami zazwyczaj ma większe udzielaniu pamięci i nie powinna być używana, jeśli obciążenie pamięci przeważa nad korzyści kluczy.  
  
 **X DO NOT** zwracać wartości null z kolekcji właściwości lub metody zwracających kolekcje. Zwraca pustą kolekcję lub pusta tablica, zamiast tego.  
  
 Ogólną zasadą jest null i pusty kolekcji (0 elementów) lub tablicą powinien być traktowany takie same.  
  
### <a name="snapshots-versus-live-collections"></a>Migawki i kolekcje na żywo  
 Kolekcje reprezentujący stan w pewnym momencie w czasie są nazywane kolekcje migawki. Kolekcja zawierająca wiersze zwrócone w wyniku zapytania bazy danych będzie na przykład migawki. Kolekcje, które zawsze reprezentują bieżący stan są nazywane kolekcje na żywo. Na przykład kolekcja `ComboBox` elementów jest kolekcją na żywo.  
  
 **X DO NOT** zwrócić migawki kolekcji z właściwości. Właściwości powinny zwracać kolekcje na żywo.  
  
 Metody pobierające właściwości powinny być bardzo prostą i wygodną operacji. Zwracanie migawki wymaga tworzenie kopii wewnętrznej kolekcji w operacji O(n).  
  
 **✓ DO** za pomocą kolekcji migawki lub na żywo `IEnumerable<T>` (lub jej podtyp) do reprezentowania kolekcje, które są volatile (tj., które można zmienić bez jawnie modyfikowania kolekcji).  
  
 Ogólnie rzecz biorąc wszystkie kolekcje reprezentujący udostępnianego zasobu (np. pliki w katalogu) są nietrwałe. Takie kolekcje są bardzo trudne lub niemożliwe do zaimplementowania jako kolekcje na żywo, chyba że implementacja jest po prostu wyliczający tylko do przodu.  
  
## <a name="choosing-between-arrays-and-collections"></a>Wybór między tablicami i kolekcji  
 **✓ DO** Preferuj kolekcji przed tablic.  
  
 Kolekcje zapewniają większą kontrolę nad zawartością, można rozwijać, wraz z upływem czasu i są bardziej użyteczne. Ponadto używanie tablic w scenariuszach tylko do odczytu nie jest zalecane, ponieważ koszt Sklonowanie tablicy jest zaporowe. Użyteczność badania wykazały, że niektórzy deweloperzy bezpiecznie więcej za pomocą opartego na kolekcji interfejsów API.  
  
 Jednak jeśli tworzysz API niskiego poziomu, może być lepiej używać różnych macierzy dla scenariuszy odczytu i zapisu. Tablice mają mniejsze zużycie pamięci, co zmniejsza zestaw roboczy, a dostęp do elementów w tablicy trwa krócej, ponieważ jest zoptymalizowany w czasie wykonywania.  
  
 **✓ CONSIDER** używanie tablic w niskiego poziomu interfejsów API do zminimalizowania zużycia pamięci i zmaksymalizować wydajność.  
  
 **✓ DO** Użyj tablice typu byte zamiast kolekcji bajtów.  
  
 **X DO NOT** Użycie tablic dla właściwości, jeśli właściwość musiałaby zwracać nowej tablicy (np. kopia tablicy wewnętrznej) zawsze jest wywoływana metoda pobierająca właściwości.  
  
## <a name="implementing-custom-collections"></a>Implementowanie kolekcje niestandardowe  
 **✓ CONSIDER** dziedziczących `Collection<T>`, `ReadOnlyCollection<T>`, lub `KeyedCollection<TKey,TItem>` podczas projektowania nowej kolekcji.  
  
 **✓ DO** zaimplementować `IEnumerable<T>` podczas projektowania nowej kolekcji. Rozważ zaimplementowanie `ICollection<T>` lub nawet `IList<T>` których warto.  
  
 Podczas wdrażania tych kolekcji niestandardowych, zgodne ze wzorcem interfejsu API, ustala `Collection<T>` i `ReadOnlyCollection<T>` możliwym stopniu. Oznacza to, że jawnie implementować tych samych elementów członkowskich, nazwy parametrów, takich jak te dwie kolekcje nazwy ich i tak dalej.  
  
 **✓ CONSIDER** implementowanie interfejsów kolekcji nierodzajowe (`IList` i `ICollection`) Jeśli kolekcji będą często przekazywane do interfejsów API biorąc te interfejsy jako dane wejściowe.  
  
 **X AVOID** implementowanie interfejsów kolekcji na typach z złożonych interfejsów API niezwiązanych ze sobą koncepcji kolekcji.  
  
 **X DO NOT** dziedziczyć nierodzajowe kolekcje podstawowej takich jak `CollectionBase`. Użyj `Collection<T>`, `ReadOnlyCollection<T>`, i `KeyedCollection<TKey,TItem>` zamiast tego.  
  
### <a name="naming-custom-collections"></a>Kolekcje niestandardowe nazewnictwa  
 Kolekcje (typy, które implementują `IEnumerable`) są tworzone głównie z dwóch przyczyn: (1), aby utworzyć nową strukturę danych z operacjami specyficzne dla struktury i często charakterystyki wydajności innego niż istniejących struktur danych (np. <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) i (2), aby utworzyć kolekcję specjalne do przechowywania określonych elementów (np. <xref:System.Collections.Specialized.StringCollection>). Struktury danych są najczęściej używane w wewnętrznej implementacji aplikacji i bibliotek. Specjalne kolekcje są głównie mają być uwidaczniane w interfejsów API (jako typów właściwości oraz parametru).  
  
 **✓ DO** Użyj sufiksu "Słownik" w nazwach obiektów abstrakcyjnych implementacja `IDictionary` lub `IDictionary<TKey,TValue>`.  
  
 **✓ DO** Użyj sufiksu "Kolekcji" w nazwach typów implementujących `IEnumerable` (lub któregokolwiek z jej obiektów podrzędnych) i reprezentujący listę elementów.  
  
 **✓ DO** Użyj nazwy struktury danych w strukturach danych niestandardowych.  
  
 **X AVOID** przy użyciu wszelkie sufiksy podejrzeń konkretnej implementacji, takie jak "LinkedList" lub "Hashtable," w nazwach obiektów abstrakcyjnych kolekcji.  
  
 **✓ CONSIDER** prefiksu nazwy kolekcji o nazwie typu elementu. Na przykład kolekcja przechowywanie elementów typu `Address` (Implementowanie `IEnumerable<Address>`) powinno być nazwanym `AddressCollection`. Jeśli typ elementu jest interfejsem, prefiks "I" elementu typu można pominąć. W związku z tym Kolekcja <xref:System.IDisposable> elementów można wywołać `DisposableCollection`.  
  
 **✓ CONSIDER** przy użyciu prefiksu "ReadOnly" w nazwach kolekcji tylko do odczytu, jeśli odpowiedniej kolekcji zapisu mogą być dodane lub już istnieje w ramach.  
  
 Na przykład powinna być wywoływana tylko do odczytu kolekcji ciągów `ReadOnlyStringCollection`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Drukowane uprawnieniami wariancji x edukacji, Inc. z [Framework zaleceń dotyczących projektowania: konwencje, Idioms i wzorce dla bibliotek .NET wielokrotnego użytku, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Abrams Brada opublikowane 22 Oct 2008 przez Professional Addison-Wesley jako część serii rozwoju systemu Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz też  
 [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
 [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
