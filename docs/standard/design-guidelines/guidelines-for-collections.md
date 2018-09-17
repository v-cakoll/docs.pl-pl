---
title: Wytyczne dotyczące kolekcji
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 297b8f1d-b11f-4dc6-960a-8e990817304e
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 3571ebb2fdd2bcdfd8be1f0087d096e01f18790a
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2018
ms.locfileid: "45964847"
---
# <a name="guidelines-for-collections"></a>Wytyczne dotyczące kolekcji
Dowolny typ, zaprojektowany specjalnie w celu manipulowania grupy obiektów mających pewne cechy wspólne jest uznawana za kolekcji. Prawie zawsze jest odpowiednia dla tych typów do zaimplementowania <xref:System.Collections.IEnumerable> lub <xref:System.Collections.Generic.IEnumerable%601>, więc w tej sekcji możemy tylko należy wziąć pod uwagę typy Implementowanie jedno lub oba te interfejsy jako kolekcji.  
  
 **X DO NOT** w publicznych interfejsach API za pomocą lekko typu kolekcji.  
  
 Typ wszystkich wartości zwracane i parametry przedstawiające elementów kolekcji powinien być typu dokładnie elementu, nie dowolny z jej typów podstawowych (dotyczy to tylko publiczne elementy członkowskie kolekcji).  
  
 **X DO NOT** użyj <xref:System.Collections.ArrayList> lub <xref:System.Collections.Generic.List%601> w publicznych interfejsach API.  
  
 Te typy są strukturami danych przeznaczone do użytku w wewnętrznych implementacji, nie znajduje się w publicznych interfejsów API. `List<T>` jest zoptymalizowany pod kątem wydajności i mocy kosztem czystości interfejsów API i elastyczność. Na przykład, jeśli wrócisz `List<T>`, nie nigdy nie będzie mogła odbierać powiadomienia, gdy kod klienta modyfikuje kolekcję. Ponadto `List<T>` udostępnia wiele elementów członkowskich, takich jak <xref:System.Collections.Generic.List%601.BinarySearch%2A>, które nie są przydatne ani nie ma to zastosowanie w wielu scenariuszach. Poniższych sekcjach opisano typy (abstrakcje), przeznaczone specjalnie do użycia w publicznych interfejsów API.  
  
 **X DO NOT** użyj `Hashtable` lub `Dictionary<TKey,TValue>` w publicznych interfejsach API.  
  
 Te typy są strukturami danych przeznaczone do użytku w wewnętrznych implementacji. Należy użyć publicznych interfejsów API <xref:System.Collections.IDictionary>, `IDictionary <TKey, TValue>`, lub niestandardowy typ wdrażania jednego lub obu interfejsów.  
  
 **X DO NOT** użyj <xref:System.Collections.Generic.IEnumerator%601>, <xref:System.Collections.IEnumerator>, lub innego typu, który implementuje jednej z tych interfejsów, z wyjątkiem jako typ zwracany `GetEnumerator` metody.  
  
 Zwracanie moduły wyliczające z metod innych niż typy `GetEnumerator` nie można używać z `foreach` instrukcji.  
  
 **X DO NOT** implementować jednocześnie `IEnumerator<T>` i `IEnumerable<T>` do tego samego typu. To samo dotyczy nierodzajowymi interfejsów `IEnumerator` i `IEnumerable`.  
  
## <a name="collection-parameters"></a>Kolekcja parametrów  
 **✓ DO** używać jak specjalizowany najmniej typu jako parametr typu. Większość elementów członkowskich, biorąc kolekcji, jak używać parametrów `IEnumerable<T>` interfejsu.  
  
 **X AVOID** przy użyciu <xref:System.Collections.Generic.ICollection%601> lub <xref:System.Collections.ICollection> jako parametr tylko w celu uzyskania dostępu `Count` właściwości.  
  
 Zamiast tego Rozważ użycie `IEnumerable<T>` lub `IEnumerable` i dynamicznie sprawdzanie, czy obiekt implementuje `ICollection<T>` lub `ICollection`.  
  
## <a name="collection-properties-and-return-values"></a>Kolekcja właściwości i wartości zwracane  
 **X DO NOT** dostarczenie kolekcji można ustawić właściwości.  
  
 Użytkownicy mogą zastąpić zawartość kolekcji najpierw wyczyścić kolekcję, a następnie dodając nowej zawartości. W przypadku zastąpienia w całej kolekcji mimo to typowy scenariusz, należy wziąć pod uwagę zapewnienie `AddRange` metody w kolekcji.  
  
 **✓ DO** użyj `Collection<T>` lub podklasa klasy of `Collection<T>` dla właściwości lub return wartości reprezentujące kolekcje odczytu/zapisu.  
  
 Jeśli `Collection<T>` nie spełnia wymagań, niektóre (np. Kolekcja nie musi implementować <xref:System.Collections.IList>), użyj niestandardowej kolekcji przez zaimplementowanie `IEnumerable<T>`, `ICollection<T>`, lub <xref:System.Collections.Generic.IList%601>.  
  
 **✓ DO** użyj <xref:System.Collections.ObjectModel.ReadOnlyCollection%601>, podklasa klasy `ReadOnlyCollection<T>`, lub w rzadkich przypadkach `IEnumerable<T>` dla właściwości lub return wartości reprezentujące kolekcji tylko do odczytu.  
  
 Ogólnie rzecz biorąc, Preferuj `ReadOnlyCollection<T>`. Jeśli nie spełnia wymagań niektóre (np. Kolekcja nie musi implementować `IList`), użyj niestandardowej kolekcji przez zaimplementowanie `IEnumerable<T>`, `ICollection<T>`, lub `IList<T>`. W przypadku zastosowania niestandardowych kolekcji tylko do odczytu, należy zaimplementować `ICollection<T>.IsReadOnly` do zwrócenia `true`.  
  
 W przypadkach, gdy masz pewność, że jedyny scenariusz, które kiedykolwiek chcesz obsługiwać jest tylko do przodu iteracji, można po prostu użyć `IEnumerable<T>`.  
  
 **✓ CONSIDER** za pomocą podklasy kolekcje podstawowej ogólne zamiast bezpośrednio przy użyciu kolekcji.  
  
 Dzięki temu nazwa lepiej i dodawania elementów członkowskich pomocnika, które nie są obecne w typach podstawowych kolekcji. Jest to szczególnie dotyczy to interfejsy API wysokiego poziomu.  
  
 **✓ CONSIDER** zwracanie podklasą `Collection<T>` lub `ReadOnlyCollection<T>` z bardzo często używanych metod i właściwości.  
  
 To umożliwi dodają metody pomocników lub zmień implementację kolekcji w przyszłości.  
  
 **✓ CONSIDER** przy użyciu kolekcji kluczem, jeśli elementy przechowywane w kolekcji ma unikatowy kluczy (nazwy, identyfikatory itp.). Kolekcje zabezpieczone kluczami są kolekcjami, które mogą być indeksowane przez liczbę całkowitą i kluczem i są zazwyczaj implementowane przez dziedziczenie z `KeyedCollection<TKey,TItem>`.  
  
 Kolekcje zabezpieczone kluczami zazwyczaj ma większe udzielaniu pamięci i nie powinny być używane, jeśli obciążenie pamięci przewyższa korzyści z kluczami.  
  
 **X DO NOT** zwracać wartości null z kolekcji właściwości lub metody zwracających kolekcje. Zamiast tego zwracają pustą kolekcję lub pusta tablica.  
  
 Ogólną zasadą jest, o wartości null i pustych kolekcji (0 elementów) lub tablic powinny być traktowane jako taki sam.  
  
### <a name="snapshots-versus-live-collections"></a>Migawki w porównaniu z kolekcji na żywo  
 Kolekcje reprezentujący stan w pewnym momencie w czasie są nazywane kolekcjami migawki. Na przykład kolekcja zawierająca wiersze zwrócone przez zapytanie bazy danych będzie migawki. Kolekcje, które zawsze reprezentują bieżący stan są nazywane kolekcjami na żywo. Na przykład zbiór `ComboBox` elementów jest kolekcją na żywo.  
  
 **X DO NOT** zwrócić migawki kolekcji z właściwości. Właściwości powinny zwracać kolekcji na żywo.  
  
 Metody pobierające właściwości powinny być bardzo operacji. Zwracanie migawki wymaga, tworząc kopię wewnętrznej kolekcji w operacji O(n).  
  
 **✓ DO** za pomocą kolekcji migawki lub na żywo `IEnumerable<T>` (lub jej podtyp) do reprezentowania kolekcje, które są volatile (tj., które można zmienić bez jawnie modyfikowania kolekcji).  
  
 Ogólnie rzecz biorąc wszystkie kolekcje reprezentujący zasób udostępniony (np. pliki w katalogu) są nietrwałe. Takie kolekcje są bardzo trudne lub niemożliwe do zaimplementowania jako kolekcje na żywo, chyba że implementacji jest po prostu wyliczający tylko do przodu.  
  
## <a name="choosing-between-arrays-and-collections"></a>Wybieranie między tablice i kolekcje  
 **✓ DO** Preferuj kolekcji przed tablic.  
  
 Kolekcje zapewniają większą kontrolę nad zawartością, mogą z czasem ewoluować i są bardziej użyteczne. Ponadto przy użyciu tablic dla scenariuszy tylko do odczytu nie jest zalecane, ponieważ koszt klonowania tablicy jest wysokie. Użyteczność badania wykazały, że niektórzy deweloperzy bez obaw więcej przy użyciu interfejsów API opartych na kolekcji.  
  
 Jednak jeśli tworzysz interfejsy API niskiego poziomu, może być lepiej używać tablic w scenariuszach odczytu i zapisu. Tablice mają mniejsze zużycie pamięci, która pomaga zmniejszyć zestaw roboczy, a dostęp do elementów w tablicy jest szybsze, ponieważ jest zoptymalizowany w czasie wykonywania.  
  
 **✓ CONSIDER** używanie tablic w niskiego poziomu interfejsów API do zminimalizowania zużycia pamięci i zmaksymalizować wydajność.  
  
 **✓ DO** Użyj tablice typu byte zamiast kolekcji bajtów.  
  
 **X DO NOT** Użycie tablic dla właściwości, jeśli właściwość musiałaby zwracać nowej tablicy (np. kopia tablicy wewnętrznej) zawsze jest wywoływana metoda pobierająca właściwości.  
  
## <a name="implementing-custom-collections"></a>Implementowanie kolekcji niestandardowych  
 **✓ CONSIDER** dziedziczących `Collection<T>`, `ReadOnlyCollection<T>`, lub `KeyedCollection<TKey,TItem>` podczas projektowania nowej kolekcji.  
  
 **✓ DO** zaimplementować `IEnumerable<T>` podczas projektowania nowej kolekcji. Rozważ zaimplementowanie `ICollection<T>` lub nawet `IList<T>` gdzie dobrym pomysłem.  
  
 Podczas implementowania takich niestandardowej kolekcji, oparte na wzorcu interfejsu API ustanowione przez `Collection<T>` i `ReadOnlyCollection<T>` możliwie najlepszy sposób. Oznacza to należy zaimplementować te same elementy członkowskie jawnie, nazwy parametrów, takich jak te dwie kolekcje, nazwij je i tak dalej.  
  
 **✓ CONSIDER** implementowanie interfejsów kolekcji nierodzajowe (`IList` i `ICollection`) Jeśli kolekcji będą często przekazywane do interfejsów API biorąc te interfejsy jako dane wejściowe.  
  
 **X AVOID** implementowanie interfejsów kolekcji na typach z złożonych interfejsów API niezwiązanych ze sobą koncepcji kolekcji.  
  
 **X DO NOT** dziedziczyć nierodzajowe kolekcje podstawowej takich jak `CollectionBase`. Użyj `Collection<T>`, `ReadOnlyCollection<T>`, i `KeyedCollection<TKey,TItem>` zamiast tego.  
  
### <a name="naming-custom-collections"></a>Nazewnictwo kolekcje niestandardowe  
 Kolekcje (typami, które implementują `IEnumerable`) są tworzone głównie dwóch powodów: (1), aby utworzyć nową strukturę danych za pomocą operacji specyficznych dla struktury i często różną charakterystykę wydajności niż istniejącymi strukturami danych (np. <xref:System.Collections.Generic.List%601>, <xref:System.Collections.Generic.LinkedList%601>, <xref:System.Collections.Generic.Stack%601>), a (2), aby utworzyć kolekcję specjalne do przechowywania określony zbiór elementów (np. <xref:System.Collections.Specialized.StringCollection>). Struktury danych są najczęściej używane w wewnętrznej implementacji aplikacji i bibliotek. Specjalne kolekcje są głównie ujawnianie w interfejsach API (jako typy właściwości i parametrów).  
  
 **✓ DO** Użyj sufiksu "Słownik" w nazwach obiektów abstrakcyjnych implementacja `IDictionary` lub `IDictionary<TKey,TValue>`.  
  
 **✓ DO** Użyj sufiksu "Kolekcji" w nazwach typów implementujących `IEnumerable` (lub któregokolwiek z jej obiektów podrzędnych) i reprezentujący listę elementów.  
  
 **✓ DO** Użyj nazwy struktury danych w strukturach danych niestandardowych.  
  
 **X AVOID** przy użyciu wszelkie sufiksy podejrzeń konkretnej implementacji, takie jak "LinkedList" lub "Hashtable," w nazwach obiektów abstrakcyjnych kolekcji.  
  
 **✓ CONSIDER** prefiksu nazwy kolekcji o nazwie typu elementu. Na przykład przechowywanie elementów tego typu kolekcji `Address` (Implementowanie `IEnumerable<Address>`) powinno się nazywać `AddressCollection`. Jeśli typ elementu to interfejs, prefiks "I" elementu typu można pominąć. W związku z tym, zbiór <xref:System.IDisposable> elementy mogą być wywoływane `DisposableCollection`.  
  
 **✓ CONSIDER** przy użyciu prefiksu "ReadOnly" w nazwach kolekcji tylko do odczytu, jeśli odpowiedniej kolekcji zapisu mogą być dodane lub już istnieje w ramach.  
  
 Na przykład, można wywołać tylko do odczytu kolekcji ciągów `ReadOnlyStringCollection`.  
  
 *Portions © 2005, 2009 Microsoft Corporation. Wszelkie prawa zastrzeżone.*  
  
 *Przedrukowano przez uprawnienie Pearson edukacji, Inc. z [wytyczne dotyczące projektowania Framework: konwencje Idiomy i wzorce wielokrotnego użytku, do bibliotek .NET, wydanie 2](https://www.informit.com/store/framework-design-guidelines-conventions-idioms-and-9780321545619) Krzysztof Cwalina i Brad Abrams opublikowane 22 Oct 2008 przez Professional Addison Wesley jako część serii rozwoju Windows firmy Microsoft.*  
  
## <a name="see-also"></a>Zobacz także

- [Struktura — zalecenia dotyczące projektowania](../../../docs/standard/design-guidelines/index.md)  
- [Zalecenia dotyczące użytkowania](../../../docs/standard/design-guidelines/usage-guidelines.md)
