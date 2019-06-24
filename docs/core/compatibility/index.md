---
title: Oceń przełomowych zmianach — .NET Core
description: Dowiedz się więcej o sposobach, w którym próbuje zachować zgodność dla deweloperów w różnych wersjach .NET platformy .NET Core.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: b58edd9ff0bd56b12b861162cc92d484a3b36c8b
ms.sourcegitcommit: a970268118ea61ce14207e0916e17243546a491f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/21/2019
ms.locfileid: "67307495"
---
# <a name="evaluate-breaking-changes-in-net-core"></a>Oceń przełomowe zmiany w programie .NET Core

Całej swojej historii .NET próbował utrzymanie wysokiego poziomu zgodności z wersji do wersji i w różnych wersjach programu .NET. Ten proces jest kontynuowany prawdziwe dla platformy .NET Core. Mimo że platformy .NET Core może być traktowany jako nową technologię, która jest niezależna od programu .NET Framework, dwa główne czynniki Ogranicz możliwość rozdzielić z .NET Framework .NET Core:

- Wielu deweloperów pierwotnie opracowana albo kontynuować tworzenie aplikacji .NET Framework. Spójne zachowanie spełniają oczekiwane przez implementacje platformy .NET.

- Projekty biblioteki .NET standard umożliwia deweloperom tworzenie bibliotek, których platformą docelową, wspólnych interfejsów API udostępnionych przez oprogramowanie .NET Core i .NET Framework. Deweloperzy oczekują, że biblioteki używane w aplikacji .NET Core powinny działać identycznie do tej samej biblioteki używane w aplikacji .NET Framework.

Wraz z zgodność między implementacje platformy .NET deweloperów oczekują wysokiego poziomu zgodności między wersjami .NET Core. W szczególności przeznaczony dla starszej wersji programu .NET Core powinien zostać uruchomiony kod bezproblemowo w nowszej wersji programu .NET Core. W rzeczywistości wielu deweloperów się spodziewać, że nowe interfejsy API znaleziony w nowo wydane wersje programu .NET Core powinny być zgodne ze wstępnymi wersjami, w których wprowadzono tych interfejsów API.

W tym artykule przedstawiono kategorie zmiany zgodności (lub zmiany powodujące niezgodność) i sposób, w którym zespół .NET daje w wyniku zmiany w każdej z tych kategorii. Zrozumienie, jak zbliża się do zespołu .NET możliwych przełomowych zmian jest szczególnie przydatne dla programistów, którzy są otwieranie żądania ściągnięcia w [dotnet/corefx](https://github.com/dotnet/corefx) repozytorium GitHub, które modyfikują zachowanie istniejących interfejsów API.

> [!NOTE]
> Dla definicji kategorii zgodności, takich jak zgodność binarną i zgodności z poprzednimi wersjami, zobacz [istotnej zmiany kategorie](categories.md).

Poniższe sekcje w tym artykule opisano rodzaje zmian wprowadzonych do interfejsów API platformy .NET Core i ich wpływ na zgodność aplikacji. Ikona ✔️ wskazuje, że określonego rodzaju zmian jest dozwolone, ❌ wskazuje, że jest to niedozwolone, natomiast ❓ oznacza zmianę, która może być lub może być zablokowany. Zmiany w tej ostatniej kategorii wymagają orzeczenia i został ocenę jak przewidywalnym oczywisty i spójne poprzednie zachowanie.

> [!NOTE]
> Oprócz służy jako przewodnik dotyczący sposobu zmiany w bibliotekach .NET Core są oceniane, deweloperów bibliotek można również użyć tych kryteriów można ocenić zmian wprowadzonych do ich bibliotek przeznaczonych do wielu implementacji platformy .NET i wersje.

## <a name="modifications-to-the-public-contract"></a>Modyfikacje publicznego kontraktu

Zmiany w tej kategorii *zmodyfikować* publiczny obszar powierzchni typu. Większość zmian w tej kategorii są niedozwolone, ponieważ mogą naruszyć *wstecznej zgodności* (możliwości aplikacji, który został opracowany przy użyciu poprzedniej wersji interfejsu API do wykonania bez ponownej kompilacji w nowszej wersji).

### <a name="types"></a>Types

- **✔️ Usuwanie implementację interfejsu z typu, gdy interfejs został już zaimplementowany przez typ podstawowy**

- **Dodawanie nowej implementacji interfejsu na typ ❓**

  Jest to dopuszczalne zmiany, ponieważ nie niekorzystnie wpłynąć na istniejących klientów. Wszelkie zmiany typu musi działać w granicach dopuszczalne zmiany zdefiniowane w tym miejscu dla nowej implementacji pozostaje dopuszczalne. Należy zachować wyjątkową ostrożność zachodzi podczas dodawania interfejsów, które bezpośrednio wpływają na zdolność projektanta lub serializatora do generowania kodu lub dane, które nie mogą być używane niskiego poziomu. Na przykład <xref:System.Runtime.Serialization.ISerializable> interfejsu.

- **Wprowadzenie do nowej klasy ❓**

  Typu mogą zostać wprowadzone do hierarchii między dwoma typami istniejących, jeśli go nie będzie żadnego wprowadzenie nowych [abstrakcyjne](../../csharp/language-reference/keywords/abstract.md) członków lub zmień semantyki oraz zachowanie istniejących typów. Na przykład w programie .NET Framework 2.0 <xref:System.Data.Common.DbConnection> klasy stało się nowe klasy bazowej dla <xref:System.Data.SqlClient.SqlConnection>, które było wcześniej pochodzi bezpośrednio z <xref:System.ComponentModel.Component>.

- **Przenoszenie typu z jednego zestawu do innego ✔️**

  Należy pamiętać, że *stare* zestawu musi być oznaczony przez <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> wskazującego na nowego zestawu.

- **✔️ Zmiana [struktury](../../csharp/language-reference/keywords/struct.md) typ `readonly struct` typu**

  Należy pamiętać, że zmiana `readonly struct` typ `struct` typ nie jest dozwolony.
  
- **✔️ Dodawanie [zapieczętowanego](../../csharp/language-reference/keywords/sealed.md) lub [abstrakcyjne](../../csharp/language-reference/keywords/abstract.md) — słowo kluczowe do typu, gdy istnieją nie *dostępny* konstruktory (publiczny lub chroniony)**

- **Rozwijanie widoczność typu ✔️**

- **❌ Zmienianie przestrzeni nazw lub nazwa typu**

- **❌ Zmienianie nazw lub usuwanie typów publicznych**

   Spowoduje to podzielenie cały kod, który używa typu usunięty lub zmieniono jego nazwę.

- **❌ Zmiana podstawowym typem wyliczenia**

   Jest to czasu kompilacji i zachowania istotnej zmiany, a także binarne istotną zmianę, który może zgłaszać błędny argumentów atrybutu.

- **❌ pieczętowania typ, który był wcześniej otwarty**

- **Dodawanie interfejsu do zestawu podstawowych typów interfejsu ❌**

   Jeśli interfejs implementuje interfejs, który ją wcześniej nie implementuje interfejsu, wszystkie typy, które są implementowane oryginalną wersję interfejsu są uszkodzone.

- **Usuwanie klasy z zestawu klas podstawowych lub interfejs z zestawu implementowane interfejsy ❓**

  Istnieje jeden wyjątek reguły do usunięcia interfejsu: można dodać implementacji interfejsu, która wynika z usuniętych interfejsu. Na przykład, możesz usunąć <xref:System.IDisposable> Jeśli typ lub interfejs implementuje teraz <xref:System.ComponentModel.IComponent>, który implementuje <xref:System.IDisposable>.

- **❌ Zmiana `readonly struct` typ [struktury](../../csharp/language-reference/keywords/struct.md) typu**

  Należy pamiętać, że zmiana `struct` typ `readonly struct` typ jest dozwolony.

- **❌ Zmiana [struktury](../../csharp/language-reference/keywords/struct.md) typ `ref struct` typu i na odwrót**

- **Zmniejszanie widoczności typu ❌**

   Jednakże zwiększając widoczność obramowania typem jest dozwolone.

### <a name="members"></a>Elementy członkowskie

- **Rozwijanie widoczność elementu członkowskiego, który nie jest ✔️ [wirtualny](../../csharp/language-reference/keywords/sealed.md)**

- **✔️ Dodawanie abstrakcyjną składową do typu publicznego, który nie ma przypisanego *dostępny* konstruktory (publiczny lub chroniony) lub typ [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**

  Jednak dodanie abstrakcyjną składową do typu, który jest dostępny żaden konstruktor (publiczny lub chroniony), a nie `sealed` jest niedozwolone.

- **Ograniczanie widoczności ✔️ [chronione](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy typ nie ma dostępnych konstruktorów (publiczny lub chroniony) lub typ jest [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**

- **✔️ Przenoszenie członka do klasy wyżej w hierarchii niż typ, z którego został usunięty**

- **✔️ Dodanie lub usunięcie zastąpienia**

  Wprowadzenie do zastąpienia może powodować poprzedniego odbiorcy pominąć zastępowania podczas wywoływania [podstawowy](../../csharp/language-reference/keywords/base.md).

- **✔️ Dodanie konstruktora do klasy, wraz z domyślnego (bezparametrowego) konstruktora, jeśli klasa miała wcześniej konstruktorów**

   Jednak dodanie konstruktora do klasy, która miała wcześniej konstruktorów *bez* dodanie konstruktora domyślnego nie jest dozwolone.

- **✔️ Zmiana elementu członkowskiego w [abstrakcyjne](../../csharp/language-reference/keywords/abstract.md) do [wirtualny](../../csharp/language-reference/keywords/virtual.md)**

- **✔️ Zmiana z `ref readonly` do `ref` zwracają wartość (z wyjątkiem metod wirtualnych lub interfejsów)**

- **✔️ Usunięcie [tylko do odczytu](../../csharp/language-reference/keywords/readonly.md) z polem, chyba że typu statycznego pola jest typem wartości modyfikowalne**

- **✔️ Wywoływania nowe zdarzenie, który nie został wcześniej zdefiniowany**

- **Dodawanie nowego pola wystąpienia typu ❓**

   Ta zmiana wpływa na serializacji.

- **❌ Zmienianie nazw lub usuwanie członka publicznego lub parametru**

   Spowoduje to podzielenie cały kod, który używa usunięty lub zmieniono jego nazwę elementu członkowskiego lub parametrów.

   Należy pamiętać, że obejmuje usunięcie lub zmiana nazwy metody pobierającej lub ustawiającej z właściwością, a także zmiana nazwy lub usunięcie elementów członkowskich wyliczenia.

- **Dodawanie członka do interfejsu ❌**

- **❌, zmieniając wartość publiczny członek stałej lub wyliczenia**

- **Zmiana typu właściwości, pola, parametru lub zwracanej wartości ❌**

- **❌ Dodawanie, usuwanie lub zmiana kolejności parametrów**

- **❌ Dodawanie lub usuwanie [w](../../csharp/language-reference/keywords/in.md), [się](../../csharp/language-reference/keywords/out.md) , lub [ref](../../csharp/language-reference/keywords/ref.md) — słowo kluczowe z parametru**

- **❌ Zmiana nazwy parametru (w tym zmienianie jej wielkości liter)**

  Jest uznawane za istotne dwóch powodów:
  
  - Przerywa z późnym wiązaniem scenariuszy, takich jak funkcji późne powiązania w języku Visual Basic i [dynamiczne](../../csharp/language-reference/keywords/dynamic.md) w C#.
  
  - Przerywa [źródła zgodności](categories.md#source-compatibility) kiedy używać deweloperzy [argumenty nazwane](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- **❌ Zmiana z `ref` wartości zwracanej, aby `ref readonly` zwracają wartość**

- **❌️ Zmiana z `ref readonly` do `ref` zwracają wartość metody wirtualnej lub interfejsu**

- **❌ Dodawanie lub usuwanie [abstrakcyjne](../../csharp/language-reference/keywords/abstract.md) od elementu członkowskiego**

- **❌ Usunięcie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) — słowo kluczowe od elementu członkowskiego**

  Chociaż często nie jest to istotna zmiana ponieważ C# kompilatora zwykle do emitowania [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) instrukcje języka pośredniego (IL), aby wywołać metody niewirtualnej (`callvirt` wykonuje sprawdzanie wartości null, podczas gdy normalne wywołanie nie ), to zachowanie nie jest invariable z kilku powodów:
  - C#to nie tylko języka współpracującego .NET.
  
  - C# Kompilator próbuje coraz bardziej zoptymalizować `callvirt` na normalne wywołanie, zawsze wtedy, gdy niewirtualną metodę docelową i prawdopodobnie nie jest null (np. metody udostępnianej [?. operatora propagowania wartości null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).
  
  Wprowadzanie metody wirtualnej oznacza, że kod konsumenta często pojawiłyby-niemal jej wywołanie.

- **❌ Dodawanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) — słowo kluczowe do elementu członkowskiego**

- **❌ Wprowadzania wirtualny element członkowski jest abstrakcyjna**

  A [wirtualna elementu członkowskiego](../../csharp/language-reference/keywords/virtual.md) dostarcza implementację metody, która *może być* zastąpiona przez klasę pochodną. [Abstrakcyjną składową](../../csharp/language-reference/keywords/abstract.md) zapewnia żadnej implementacji i *musi być* przesłonięcia.

- **❌ Dodawanie abstrakcyjną składową do typu publicznego, który ma dostępnych konstruktorów (publiczny lub chroniony) i który nie jest [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**

- **❌ Dodawanie lub usuwanie [statyczne](../../csharp/language-reference/keywords/static.md) — słowo kluczowe od elementu członkowskiego**

- **Dodanie przeciążenia wyklucza istniejących przeciążenia, która definiuje zachowanie różnych ❌**

  Spowoduje to podzielenie istniejących klientów, które były powiązane z poprzednim przeciążenia. Na przykład, jeśli klasę utworzono według jednej wersji metody, która akceptuje <xref:System.UInt32>, istniejących klientów pomyślnie powiąże tego przeciążenia przy przekazywaniu <xref:System.Int32> wartość. Jednak jeśli dodasz przeciążenia akceptujący <xref:System.Int32>, podczas ponownej kompilacji lub korzystanie z późnym wiązaniem, kompilator teraz wiąże się z nowym przeciążeniem. Jeśli powoduje różne zachowanie, to istotnej zmiany.

- **❌ Dodanie konstruktora do klasy, która miała wcześniej żaden konstruktor bez dodawania Konstruktor domyślny**

- **❌️ Dodawanie [tylko do odczytu](../../csharp/language-reference/keywords/readonly.md) do pola**

- **❌ Zmniejszanie widoczności elementu członkowskiego**

   Obejmuje to zmniejszenie widoczność [chronione](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy istnieją *dostępny* konstruktory (publiczny lub chroniony) i typ jest *nie* [ zapieczętowane](../../csharp/language-reference/keywords/sealed.md). Jeśli nie jest to możliwe, zmniejszając widoczność chroniony element członkowski jest dozwolone.

   Pamiętaj, że zwiększając widoczność elementu członkowskiego jest dozwolone.

- **❌ Zmianę typu składowej**

   Nie można zmodyfikować wartość zwracaną metody lub typu pola lub właściwości. Na przykład, podpis metody, która zwraca <xref:System.Object> nie można zmienić, aby zwrócić <xref:System.String>, lub na odwrót.

- **❌ Dodanie pola do struktury, która miała wcześniej bez stanu**

  Asercja określonego przydziału reguły umożliwia niezainicjowane zmienne tak długo, jak typ zmiennej jest strukturą bezstanowe. Jeśli struktura jest stanowa, kod może wystąpić niezainicjowanych danych. To plik binarny zmiana powodująca niezgodność oraz potencjalnie źródłowej, które są istotne.

- **Wyzwalanie istniejące zdarzenie, gdy nigdy nie zostało wywołane przed ❌**

## <a name="behavioral-changes"></a>Zmiany zachowania

### <a name="assemblies"></a>Zestawy

- **✔️ Tworzenie przenośnej zestawu podczas tych samych platformach są nadal obsługiwane.**

- **Zmienianie nazwy zestawu ❌**
- **Zmiana klucza publicznego zestawu ❌**

### <a name="properties-fields-parameters-and-return-values"></a>Właściwości, pola, parametrów i zwracanych wartości

- **✔️ Zmiana wartości właściwości, pola, wartość zwracana lub [się](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametr typu bardziej pochodnego**

  Na przykład metodę, która zwraca typ <xref:System.Object> może zwrócić <xref:System.String> wystąpienia. (Jednak sygnatury metody nie można zmienić).

- **Zwiększenie zakresu ✔️ akceptowane wartości dla właściwości lub parametru, jeśli element członkowski nie jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**

  Pamiętaj, że podczas zakres wartości, które mogą być przekazywane do metody lub są zwracane przez element członkowski można rozwinąć, nie typem parametru lub elementu członkowskiego. Na przykład, gdy wartości przekazywane do metody, można zwiększyć z 0 124 0-255, typ parametru nie można zmienić z <xref:System.Byte> do <xref:System.Int32>.

- **Zwiększenie zakresu ❌ akceptowane wartości dla właściwości lub parametru, jeśli element jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**

   Ta zmiana spowoduje przerwanie istniejących zgodnym z przesłoniętą elementy członkowskie, których nie będzie działać prawidłowo dla rozszerzonego zakresu wartości.

- **❌ Zmniejszenie zakresu akceptowanych wartości dla właściwości lub parametru**

- **Zwiększenie zakresu ❌ zwracane wartości dla właściwości, pola, wartość zwracana lub [się](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru**

- **❌ Zmiana zwracane wartości dla właściwości, pola, wartość zwracana przez metodę, lub [się](../../csharp/language-reference/keywords/out-parameter-modifier.md) parametru**

- **Zmiana wartości domyślnej właściwości, pola lub parametr ❌**

- **Zmiana dokładność liczbowa wartość zwrotna ❌**

- **Zmiana ❓ A analizowania danych wejściowych i zgłaszanie nowych wyjątków (nawet, jeśli zachowanie analizowania, nie jest określony w dokumentacji**

### <a name="exceptions"></a>Wyjątki

- **Zgłaszanie wyjątku typu bardziej pochodnego niż istniejący wyjątek ✔️**

  Ponieważ nowy wyjątek jest podklasą istniejących wyjątek, poprzedniego kodu obsługi wyjątków w dalszym ciągu obsłużyć wyjątek. Na przykład w programie .NET Framework 4, metod tworzenia i pobierania kultury rozpoczął się zgłosić <xref:System.Globalization.CultureNotFoundException> zamiast <xref:System.ArgumentException> Jeśli nie można odnaleźć kultury. Ponieważ <xref:System.Globalization.CultureNotFoundException> pochodzi od klasy <xref:System.ArgumentException>, jest to dopuszczalne zmiany.

- **Zgłaszanie bardziej konkretny wyjątek niż ✔️ <xref:System.NotSupportedException>, <xref:System.NotImplementedException>, <xref:System.NullReferenceException>**

- **✔️ zostanie zgłoszony wyjątek, który jest uważany za nieodwracalny**

  Nieodwracalny wyjątki nie powinny być przechwytywane, ale zamiast tego powinno zostać obsłużone przez wysokiego poziomu obsługi catch-all. W związku z tym użytkownicy nie powinny mieć kod, który przechwytuje tych jawnych wyjątków. Nieodwracalny wyjątki są:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **✔️ Zgłaszanie nowy wyjątek nową ścieżkę kodu**

  Wyjątek musi dotyczyć tylko nową ścieżkę kodu które jest wykonywane przy użyciu nowych wartości parametru lub stan i nie można wykonać przez istniejący kod przeznaczonego poprzedniej wersji.

- **Usuwanie wyjątek, aby umożliwić bardziej niezawodne działanie lub udostępnione nowe scenariusze ✔️**

  Na przykład `Divide` metodę, która wcześniej tylko obsługiwane wartości dodatnich i zgłosił <xref:System.ArgumentOutOfRangeException> można zmienić do obsługi wartości dodatnie i ujemne bez zgłoszenia wyjątku.

- **Zmiana tekstu komunikatu o błędzie ✔️**

  Deweloperzy nie należy polegać na tekst komunikaty o błędach, które zmieniają się również na podstawie kultury użytkownika.

- **❌ w innym przypadku nie jest wymieniona powyżej zostanie zgłoszony wyjątek**

- **Usuwanie wyjątek w innym przypadku niewymienionego powyżej ❌**

### <a name="attributes"></a>Atrybuty

- **✔️, zmieniając wartość atrybutu, który jest *nie* możliwość obserwowania**

- **Zmiana wartości atrybutu ❌, *jest* możliwość obserwowania**

- **Usuwanie atrybutu ❓**

  W większości przypadków, usunięcie atrybutu (takie jak <xref:System.NonSerializedAttribute>) jest zmianą przerywającą.

## <a name="platform-support"></a>Obsługa różnych platform

- **✔️ Obsługi operacji na platformie, która wcześniej nie jest obsługiwana**

- **❌ Nie obsługi lub teraz wymagających określonego dodatku do operacji, która wcześniej była obsługiwana na platformie**

## <a name="internal-implementation-changes"></a>Wewnętrznej implementacji zmian

- **Zmienianie obszaru powierzchni wewnętrzny typ ❓**

   Takie zmiany są ogólnie dozwolone, mimo że dzielą się one prywatnej odbicia. W niektórych przypadkach, w którym popularnych bibliotek innych firm lub dużej liczby deweloperów zależą od wewnętrznych interfejsach API, takie zmiany może być zablokowany.

- **❓ Zmianę wewnętrznej implementacji elementu członkowskiego**

  Te zmiany są ogólnie dozwolone, mimo że dzielą się one prywatnej odbicia. W niektórych przypadkach, gdy kod klienta często zależy od prywatnych odbicia lub gdzie zmiany wprowadzono wystąpienie niezamierzonych skutków ubocznych, te zmiany może być zablokowany.

- **✔️ Poprawę wydajności operacji**

   Możliwość modyfikowania wydajność operacji jest niezbędne, ale takie zmiany może przerwać kodu, która opiera się na bieżącej szybkości operacji. Jest to szczególnie istotne, kodu, który jest zależny od czasu operacji asynchronicznych. Należy pamiętać, że zmiana wydajności nie powinna mieć żadnego wpływu na inne zachowanie interfejsu API w danym; w przeciwnym razie zostaną istotne zmiany.

- **✔️ Pośrednio (i często niekorzystnie) Zmiana wydajności operacji**

  Jeśli w danym zmian nie jest traktowane jako podziału innego powodu, jest to dopuszczalne. Często potrzeba akcje do wykonania, która może zawierać dodatkowe operacje lub dodaje nowe funkcje. To prawie zawsze mieć wpływ na wydajność, ale może być niezbędny do uzyskania interfejsu API w funkcji pytania, zgodnie z oczekiwaniami.

- **❌ Zmiana synchronicznego interfejsu API do asynchronicznego (i na odwrót)**

## <a name="code-changes"></a>Zmiany w kodzie

- **✔️ Dodawanie [params](../../csharp/language-reference/keywords/params.md) do parametru**

- **❌ Zmiana [struktury](../../csharp/language-reference/keywords/struct.md) do [klasy](../../csharp/language-reference/keywords/class.md) i na odwrót**

- **❌ Dodawanie [zaznaczone](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego blok kodu**

   Ta zmiana może spowodować kod, który wcześniej wykonywanego zgłosić <xref:System.OverflowException> i jest nie do przyjęcia.

- **❌ Usunięcie [params](../../csharp/language-reference/keywords/params.md) z parametru**

- **Zmiana kolejności, w której zdarzenia są uruchamiane ❌**

  Deweloperzy mogą spodziewać zdarzenia w tej samej kolejności, a kod dewelopera zależy często kolejność, w której zdarzenia są uruchamiane.

- **❌ Usuwanie wywoływanie zdarzeń w danej akcji**

- **❌ Zmiana liczby danego zdarzenia są wywoływane.**

- **❌ Dodawanie <xref:System.FlagsAttribute> na typ wyliczenia**
