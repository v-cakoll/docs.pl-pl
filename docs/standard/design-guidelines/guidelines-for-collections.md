---
title: Wskazówki dotyczące kolekcji
ms.date: 10/22/2008
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
ms.openlocfilehash: 231d8b04c11f19c4440e184533e1eeaded72b70b
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75709325"
---
# <a name="guidelines-for-collections"></a>Wskazówki dotyczące kolekcji
Każdy typ przeznaczony specjalnie do manipulowania grupą obiektów, które mają pewną wspólną charakterystykę, może być traktowany jako kolekcja. Jest prawie zawsze odpowiednie dla takich typów, aby zaimplementować <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>, dlatego w tej sekcji rozważamy tylko typy implementujące jeden lub oba te interfejsy, które mają być kolekcjami.  
  
 **X DO NOT** w publicznych interfejsach API za pomocą lekko typu kolekcji.  
  
 Typ wszystkich wartości zwracanych i parametrów reprezentujących elementy kolekcji musi być dokładnym typem elementu, a nie żadnym z jego typów podstawowych (dotyczy to tylko publicznych członków kolekcji).  
  
 **X DO NOT** użyj <xref:System.Collections.ArrayList> lub <xref:System.Collections.Generic.List%601> w publicznych interfejsach API.  
  
 Te typy są strukturami danych przeznaczonymi do użycia w wewnętrznej implementacji, a nie w publicznych interfejsach API. `List<T>` jest zoptymalizowany pod kątem wydajności i mocy na koszt czyszczenia interfejsów API i elastyczności. Na przykład jeśli powrócisz `List<T>`, nie będziesz mieć możliwości otrzymywania powiadomień, gdy kod klienta modyfikuje kolekcję. Ponadto `List<T>` uwidacznia wiele elementów członkowskich, takich jak <xref:System.Collections.Generic.List%601.BinarySearch%2A>, które nie są przydatne ani mają zastosowania w wielu scenariuszach. W poniższych dwóch sekcjach opisano typy (abstrakcje) przeznaczone specjalnie do użycia w publicznych interfejsach API.  
  
 **X DO NOT** użyj `Hashtable` lub `Dictionary<TKey,TValue>` w publicznych interfejsach API.  
  
 Te typy są strukturami danych przeznaczonymi do użycia w wewnętrznej implementacji. Publiczne interfejsy API powinny używać <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`lub typu niestandardowego implementującego jeden lub oba interfejsy.  
  
 **X DO NOT** użyj <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, lub innego typu, który implementuje jednej z tych interfejsów, z wyjątkiem jako typ zwracany `GetEnumerator` metody.  
  
 Typy zwracające moduły wyliczające z metod innych niż `GetEnumerator` nie mogą być używane z instrukcją `foreach`.  
  
 **X DO NOT** implementować jednocześnie `IEnumerator<T>` i `IEnumerable<T>` do tego samego typu. To samo dotyczy interfejsów nieogólnych `IEnumerator` i `IEnumerable`.  
  
## <a name="collection-parameters"></a>Parametry kolekcji  
 **✓ DO** używać jak specjalizowany najmniej typu jako parametr typu. Większość elementów członkowskich przyjmujących kolekcje jako parametry używają interfejsu `IEnumerable<T>`.  
  
 **X AVOID** przy użyciu <xref:System.Collections.Generic.ICollection%601> lub <xref:System.Collections.ICollection> jako parametr tylko w celu uzyskania dostępu `Count` właściwości.  
  
 Zamiast tego należy rozważyć użycie `IEnumerable<T>` lub `IEnumerable` i dynamiczne sprawdzanie, czy obiekt implementuje `ICollection<T>` lub `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Właściwości kolekcji i wartości zwracane  
 **X DO NOT** dostarczenie kolekcji można ustawić właściwości.  
  
 Użytkownicy mogą zastąpić zawartość kolekcji, czyszcząc najpierw kolekcję, a następnie dodając nową zawartość. Jeśli zastępowanie całej kolekcji jest typowym scenariuszem, rozważ dostarczenie metody `AddRange` w kolekcji.  
  
 **✓ DO** użyj `Collection<T>` lub podklasa klasy of `Collection<T>` dla właściwości lub return wartości reprezentujące kolekcje odczytu/zapisu.  
  
 Jeśli `Collection<T>` nie spełnia pewnego wymagania (np. kolekcja nie może implementować <xref:System.Collections.IList>), Użyj kolekcji niestandardowej przez implementację `IEnumerable<T>`, `ICollection<T>`lub <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** użyj <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, podklasa klasy `ReadOnlyCollection<T>`, lub w rzadkich przypadkach `IEnumerable<T>` dla właściwości lub return wartości reprezentujące kolekcji tylko do odczytu.  
  
 Ogólnie rzecz biorąc, Preferuj `ReadOnlyCollection<T>`. Jeśli nie spełnia pewnej wymagania (np. kolekcja nie może implementować `IList`), Użyj kolekcji niestandardowej przez implementację `IEnumerable<T>`, `ICollection<T>`lub `IList<T>`. W przypadku implementowania niestandardowej kolekcji tylko do odczytu należy zaimplementować `ICollection<T>.IsReadOnly`, aby zwracały `true`.  
  
 W przypadkach, w których wiadomo, że jedynym scenariuszem, który będzie potrzebny do obsługi, jest iteracja tylko do przodu, można po prostu użyć `IEnumerable<T>`.  
  
 **✓ CONSIDER** za pomocą podklasy kolekcje podstawowej ogólne zamiast bezpośrednio przy użyciu kolekcji.  
  
 Pozwala to na lepszą nazwę i Dodawanie członków pomocników, których nie ma w typach kolekcji podstawowej. Jest to szczególnie przydatne w przypadku interfejsów API wysokiego poziomu.  
  
 **✓ CONSIDER** zwracanie podklasą `Collection<T>` lub `ReadOnlyCollection<T>` z bardzo często używanych metod i właściwości.  
  
 Dzięki temu można dodać metody pomocnika lub zmienić implementację kolekcji w przyszłości.  
  
 **✓ CONSIDER** przy użyciu kolekcji kluczem, jeśli elementy przechowywane w kolekcji ma unikatowy kluczy (nazwy, identyfikatory itp.). Kolekcje z kluczami są kolekcjami, które można indeksować za pomocą liczby całkowitej i klucza i są zwykle zaimplementowane przez dziedziczenie z `KeyedCollection<TKey,TItem>`.  
  
 Kolekcje z równoważeniem rozmiaru zazwyczaj mają większe rozmiary pamięci i nie powinny być używane, jeśli obciążenie pamięci zawiera zalety kluczy.  
  
 **X DO NOT** zwracać wartości null z kolekcji właściwości lub metody zwracających kolekcje. W zamian Zwróć pustą kolekcję lub pustą tablicę.  
  
 Ogólna reguła to wartość null i puste (0 elementów) kolekcje lub tablice powinny być traktowane jako takie same.  
  
### <a name="snapshots-versus-live-collections"></a>Migawki a kolekcje na żywo  
 Kolekcje reprezentujące stan w pewnym momencie są nazywane kolekcjami migawek. Na przykład Kolekcja zawierająca wiersze zwrócone z kwerendy bazy danych będzie migawką. Kolekcje, które zawsze reprezentują bieżący stan, są nazywane kolekcjami dynamicznymi. Na przykład Kolekcja elementów `ComboBox` jest kolekcją dynamiczną.  
  
 **X DO NOT** zwrócić migawki kolekcji z właściwości. Właściwości powinny zwracać kolekcje dynamiczne.  
  
 Metody pobierające właściwości powinny być bardzo lekkimi operacjami. Zwracanie migawki wymaga utworzenia kopii kolekcji wewnętrznej w operacji O (n).  
  
 **✓ DO** za pomocą kolekcji migawki lub na żywo `IEnumerable<T>` (lub jej podtyp) do reprezentowania kolekcje, które są volatile (tj., które można zmienić bez jawnie modyfikowania kolekcji).  
  
 Ogólnie rzecz biorąc, wszystkie kolekcje reprezentujące zasób udostępniony (np. pliki w katalogu) są nietrwałe. Takie kolekcje są bardzo trudne lub niemożliwe do wdrożenia jako kolekcje dynamiczne, chyba że implementacja to po prostu moduł wyliczający tylko do przodu.  
  
## <a name="choosing-between-arrays-and-collections"></a>Wybór między tablicami a kolekcjami  
 **✓ DO** Preferuj kolekcji przed tablic.  
  
 Kolekcje zapewniają większą kontrolę nad zawartością, mogą być rozwijane z upływem czasu i są bardziej użyteczne. Ponadto nie zaleca się używania tablic dla scenariuszy tylko do odczytu, ponieważ koszt klonowania tablicy jest zabroniony. Badania użyteczności wykazały, że niektórzy deweloperzy są bardziej wygodni przy użyciu interfejsów API opartych na kolekcji.  
  
 Jeśli jednak tworzysz interfejsy API niskiego poziomu, lepiej jest używać tablic do scenariuszy odczytu i zapisu. Tablice mają mniejsze rozmiary pamięci, co ułatwia zmniejszenie zestawu roboczego i dostęp do elementów w tablicy jest szybszy, ponieważ jest zoptymalizowany pod kątem środowiska uruchomieniowego.  
  
 **✓ CONSIDER** używanie tablic w niskiego poziomu interfejsów API do zminimalizowania zużycia pamięci i zmaksymalizować wydajność.  
  
 **✓ DO** Użyj tablice typu byte zamiast kolekcji bajtów.  
  
 **X DO NOT** Użycie tablic dla właściwości, jeśli właściwość musiałaby zwracać nowej tablicy (np. kopia tablicy wewnętrznej) zawsze jest wywoływana metoda pobierająca właściwości.  
  
## <a name="implementing-custom-collections"></a>Implementowanie kolekcji niestandardowych  
 **✓ CONSIDER** dziedziczących `Collection<T>`, `ReadOnlyCollection<T>`, lub `KeyedCollection<TKey,TItem>` podczas projektowania nowej kolekcji.  
  
 **✓ DO** zaimplementować `IEnumerable<T>` podczas projektowania nowej kolekcji. Rozważ zaimplementowanie `ICollection<T>` lub nawet `IList<T>`, gdzie ma to sens.  
  
 Podczas wdrażania takiej niestandardowej kolekcji postępuj zgodnie z wzorcem interfejsu API ustanowionym przez `Collection<T>` i `ReadOnlyCollection<T>` tak jak to możliwe. Oznacza to, że Zaimplementuj jawnie te same elementy członkowskie, nazwij te parametry, jak te dwie nazwy kolekcji i tak dalej.  
  
 **✓ CONSIDER** implementowanie interfejsów kolekcji nierodzajowe (`IList` i `ICollection`) Jeśli kolekcji będą często przekazywane do interfejsów API biorąc te interfejsy jako dane wejściowe.  
  
 **X AVOID** implementowanie interfejsów kolekcji na typach z złożonych interfejsów API niezwiązanych ze sobą koncepcji kolekcji.  
  
 **X DO NOT** dziedziczyć nierodzajowe kolekcje podstawowej takich jak `CollectionBase`. Zamiast tego użyj `Collection<T>`, `ReadOnlyCollection<T>`i `KeyedCollection<TKey,TItem>`.  
  
### <a name="naming-custom-collections"></a>Nazewnictwo kolekcji niestandardowych  
 Kolekcje (typy implementujące `IEnumerable`) są tworzone głównie z dwóch powodów: (1) do tworzenia nowej struktury danych z operacjami specyficznymi dla określonej struktury i często różnymi cechami wydajności niż istniejące struktury danych (np., <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>) i (2) do tworzenia wyspecjalizowanej kolekcji do przechowywania określonego zestawu elementów (np. <xref:System.Collections.Specialized.StringCollection>). Struktury danych są najczęściej używane w wewnętrznej implementacji aplikacji i bibliotek. Wyspecjalizowane kolekcje są głównie udostępniane w interfejsach API (jako typy właściwości i parametrów).  
  
 **✓ DO** Użyj sufiksu "Słownik" w nazwach obiektów abstrakcyjnych implementacja `IDictionary` lub `IDictionary<TKey,TValue>`.  
  
 **✓ DO** Użyj sufiksu "Kolekcji" w nazwach typów implementujących `IEnumerable` (lub któregokolwiek z jej obiektów podrzędnych) i reprezentujący listę elementów.  
  
 **✓ DO** Użyj nazwy struktury danych w strukturach danych niestandardowych.  
  
 **X AVOID** przy użyciu wszelkie sufiksy podejrzeń konkretnej implementacji, takie jak "LinkedList" lub "Hashtable," w nazwach obiektów abstrakcyjnych kolekcji.  
  
 **✓ CONSIDER** prefiksu nazwy kolekcji o nazwie typu elementu. Na przykład, kolekcja przechowująca elementy typu `Address` (implementujący `IEnumerable<Address>`) powinna być nazywana `AddressCollection`. Jeśli typ elementu to interfejs, prefiks "I" typu elementu można pominąć. W ten sposób Kolekcja elementów <xref:System.IDisposable> może być wywoływana `DisposableCollection`.  
  
 **✓ CONSIDER** przy użyciu prefiksu "ReadOnly" w nazwach kolekcji tylko do odczytu, jeśli odpowiedniej kolekcji zapisu mogą być dodane lub już istnieje w ramach.  
  
 Na przykład Kolekcja ciągów tylko do odczytu powinna być nazywana `ReadOnlyStringCollection`.  
  
 *Fragmenty © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Ponownie Wydrukowano przez uprawnienie Pearson Education, Inc. z [wytycznych dotyczących projektowania platformy: konwencje, idiomy i wzorce dla bibliotek .NET do wielokrotnego użytku, 2. wydanie](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) przez Krzysztof Cwalina i Brad Abrams, opublikowane 22, 2008 przez Addison-Wesley Professional w ramach serii Microsoft Windows Development.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
