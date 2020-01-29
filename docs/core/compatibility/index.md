---
title: Typy istotnych zmian — .NET Core
description: Dowiedz się, jak platforma .NET Core próbuje zachować zgodność dla deweloperów w różnych wersjach programu .NET i jakiego rodzaju zmiana jest traktowana jako istotna zmiana.
ms.date: 06/10/2019
ms.openlocfilehash: 76d04504c4476f0f7517a633cfbf1c0aa9d5797e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/24/2020
ms.locfileid: "76738572"
---
# <a name="changes-that-affect-compatibility"></a>Zmiany wpływające na zgodność

W całej historii środowisko .NET podjęło próbę utrzymania wysokiego poziomu zgodności z wersji do wersji i w różnych wersjach platformy .NET. Jest to nadal prawdziwe dla platformy .NET Core. Mimo że platforma .NET Core może być traktowana jako nowa technologia, która jest niezależna od .NET Framework, dwa główne czynniki ograniczają możliwość rozbieżności programu .NET Core od .NET Framework:

- Duża liczba deweloperów pierwotnie opracowała lub kontynuowała opracowywanie .NET Framework aplikacji. Oczekują one spójnego zachowania w implementacjach platformy .NET.

- .NET Standard projekty biblioteki umożliwiają deweloperom tworzenie bibliotek przeznaczonych dla wspólnych interfejsów API udostępnionych przez platformę .NET Core i .NET Framework. Deweloperzy oczekują, że biblioteka używana w aplikacji .NET Core powinna zachowywać się identycznie z tą samą biblioteką używaną w aplikacji .NET Framework.

Wraz ze zgodnością w ramach implementacji platformy .NET deweloperzy oczekują wysokiego poziomu zgodności między wersjami programu .NET Core. W szczególności kod zapisany dla starszej wersji programu .NET Core powinien działać bezproblemowo na nowszej wersji platformy .NET Core. W rzeczywistości wielu deweloperów oczekuje, że nowe interfejsy API znajdujące się w nowo wydanej wersji platformy .NET Core powinny również być zgodne z wersjami wstępnymi, w których zostały wprowadzone te interfejsy API.

W tym artykule przedstawiono kategorie zmian zgodności (lub istotne zmiany) oraz sposób, w jaki zespół .NET oceni zmiany w każdej z tych kategorii. Zrozumienie, w jaki sposób zespół .NET zbliża się do możliwych istotnych zmian, jest szczególnie przydatny dla deweloperów, którzy otwierają żądania ściągnięcia w repozytorium GitHub [/środowiska uruchomieniowego](https://github.com/dotnet/runtime) w serwisie w witrynie w serwisie w serwisie w witrynie

> [!NOTE]
> Aby zapoznać się z definicją kategorii zgodności, takich jak zgodność binarna i zgodność z poprzednimi wersjami, zobacz artykuł dotyczący [zmiany kategorii](categories.md).

W poniższych sekcjach opisano kategorie zmian wprowadzonych w interfejsach API programu .NET Core i ich wpływ na zgodność aplikacji. Zmiany są dozwolone ✔️, niedozwolone ❌lub wymagają orzeczenia oraz oceny sposobu, w jaki przewidywalne, oczywiste i spójne poprzednie zachowanie zostało ❓.

> [!NOTE]
> Oprócz obsługi programu jako wskazówki dotyczącej oceny zmian w bibliotekach .NET Core, deweloperzy biblioteki mogą również używać tych kryteriów do oceny zmian w bibliotekach przeznaczonych dla wielu implementacji i wersji platformy .NET.

## <a name="modifications-to-the-public-contract"></a>Modyfikacje kontraktu publicznego

Zmiany w tej kategorii modyfikują publiczną powierzchnię typu. Większość zmian w tej kategorii jest niedozwolona, ponieważ naruszają *zgodność z poprzednimi* wersjami (zdolność aplikacji, która została opracowana przy użyciu poprzedniej wersji interfejsu API do wykonania bez ponownej kompilacji w nowszej wersji).

### <a name="types"></a>Types

- ✔️ **dozwolone: usuwanie implementacji interfejsu z typu, gdy interfejs jest już zaimplementowany przez typ podstawowy**

- ❓ **Wymaga orzeczenia: Dodawanie nowej implementacji interfejsu do typu**

  Jest to akceptowalna zmiana, ponieważ nie ma negatywnego wpływu na istniejących klientów. Wszelkie zmiany w typie muszą działać w granicach akceptowalnych zmian zdefiniowanych w tym miejscu dla nowej implementacji, która pozostanie akceptowalna. Należy zachować szczególną ostrożność przy dodawaniu interfejsów, które bezpośrednio wpływają na zdolność projektanta lub serializatorów do generowania kodu lub danych, których nie można użyć na poziomie niskiego poziomu. Przykładem jest interfejs <xref:System.Runtime.Serialization.ISerializable>.

- ❓ **Wymaga orzeczenia: wprowadzenie nowej klasy bazowej**

  Typ może być wprowadzany do hierarchii między dwoma istniejącymi typami, jeśli nie wprowadza żadnych nowych [abstrakcyjnych](../../csharp/language-reference/keywords/abstract.md) elementów członkowskich lub zmiany semantyki lub zachowania istniejących typów. Na przykład w .NET Framework 2,0, Klasa <xref:System.Data.Common.DbConnection> stała się nową klasą bazową dla <xref:System.Data.SqlClient.SqlConnection>, która wcześniej była bezpośrednio pochodną <xref:System.ComponentModel.Component>.

- ✔️ **dozwolone: przeniesienie typu z jednego zestawu do innego**

  *Stary* zestaw musi być oznaczony <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute>, który wskazuje na nowy zestaw.

- ✔️ **dozwolone: zmiana typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `readonly struct`**

  Zmiana typu `readonly struct` na typ `struct` jest niedozwolona.

- ✔️ **dozwolone: dodanie [zapieczętowanego](../../csharp/language-reference/keywords/sealed.md) lub [abstrakcyjnego](../../csharp/language-reference/keywords/abstract.md) słowa kluczowego do typu w przypadku braku *dostępnych* (publicznych lub chronionych) konstruktorów**

- ✔️ **dozwolone: rozszerzanie widoczności typu**

- niedozwolone ❌ **: zmiana przestrzeni nazw lub nazwy typu**

- niedozwolone ❌ **: zmiana nazwy lub usuwanie typu publicznego**

   Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego typu.

- niedozwolone ❌ **: zmiana podstawowego typu wyliczenia**

   Jest to niezależna od czasu kompilowania i zachowania zmiana, a także zmiana podziału binarnego, która może sprawiać, że argumenty atrybutów nie są przewidziane do przeanalizowania.

- niedozwolone ❌ **: opieczętowanie typu, który był wcześniej niezapieczętowany**

- niedozwolone ❌ **: Dodawanie interfejsu do zestawu typów podstawowych interfejsu**

   Jeśli interfejs implementuje interfejs, który wcześniej nie został zaimplementowany, wszystkie typy, które implementują oryginalną wersję interfejsu, są uszkodzone.

- ❓ **Wymaga orzeczenia: usunięcie klasy z zestawu klas bazowych lub interfejsu z zestawu zaimplementowanych interfejsów**

  Istnieje jeden wyjątek dla reguły usuwania interfejsu: można dodać implementację interfejsu, która pochodzi od usuniętego interfejsu. Na przykład można usunąć <xref:System.IDisposable>, jeśli typ lub interfejs implementuje teraz <xref:System.ComponentModel.IComponent>, który implementuje <xref:System.IDisposable>.

- niedozwolone ❌ **: zmiana typu `readonly struct` na typ [struktury](../../csharp/language-reference/keywords/struct.md)**

  Istnieje jednak możliwość zmiany typu `struct` typu `readonly struct`.

- niedozwolone ❌ **: zmiana typu [struktury](../../csharp/language-reference/keywords/struct.md) na typ `ref struct` i odwrotnie**

- niedozwolone ❌ **: zmniejszanie widoczności typu**

   Jednak zwiększenie widoczności typu jest dozwolone.

### <a name="members"></a>Elementy członkowskie

- ✔️ **dozwolone: rozszerzanie widoczności elementu członkowskiego, który nie jest [wirtualny](../../csharp/language-reference/keywords/sealed.md)**

- ✔️ **dozwolone: Dodawanie abstrakcyjnej składowej do typu publicznego, który nie ma *dostępnych* (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md)**

  Jednak dodanie abstrakcyjnej składowej do typu, który ma dostępne (publiczne lub chronione) konstruktorów, i nie jest `sealed` jest niedozwolone.

- ✔️ **dozwolone: ograniczanie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy typ nie ma dostępnych (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md)**

- ✔️ **dozwolone: przeniesienie elementu członkowskiego do klasy wyższej w hierarchii niż typ, z którego został usunięty**

- ✔️ **dozwolone: Dodawanie lub usuwanie przesłonięcia**

  Wprowadzenie przesłonięcia może spowodować, że poprzedni odbiorcy pominięcia przesłonięcia podczas wywoływania [podstawy](../../csharp/language-reference/keywords/base.md).

- ✔️ **dozwolone: Dodawanie konstruktora do klasy wraz z konstruktorem bez parametrów, jeśli Klasa nie miała wcześniej konstruktorów**

   Jednak dodanie konstruktora do klasy, która wcześniej nie miała konstruktorów *bez* dodawania konstruktora bezparametrowego, nie jest dozwolone.

- ✔️ **dozwolone: zmiana składowej z [abstrakcyjnej](../../csharp/language-reference/keywords/abstract.md) na [wirtualną](../../csharp/language-reference/keywords/virtual.md)**

- ✔️ **dozwolone: zmiana z `ref readonly` na `ref` wartość zwracana (z wyjątkiem metod wirtualnych lub interfejsów)**

- ✔️ **dozwolone: usuwanie elementu [ReadOnly](../../csharp/language-reference/keywords/readonly.md) z pola, chyba że typ statyczny pola jest modyfikowalnym typem wartości**

- ✔️ **dozwolone: wywoływanie nowego zdarzenia, które nie zostało wcześniej zdefiniowane**

- ❓ **Wymaga orzeczenia: dodanie nowego pola wystąpienia do typu**

   Ta zmiana wpływa na serializację.

- niedozwolone ❌ **: zmiana nazwy lub usunięcie publicznego elementu członkowskiego lub parametru**

   Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego elementu członkowskiego lub parametru.

   Obejmuje to usunięcie lub zmianę nazwy metody pobierającej lub setter z właściwości, a także zmianę nazwy lub usunięcie elementów członkowskich wyliczenia.

- niedozwolone ❌ **: Dodawanie elementu członkowskiego do interfejsu**

- niedozwolone ❌ **: zmiana wartości stałej publicznej lub elementu członkowskiego wyliczenia**

- niedozwolone ❌ **: zmiana typu właściwości, pola, parametru lub wartości zwracanej**

- niedozwolone ❌ **: Dodawanie, usuwanie lub zmienianie kolejności parametrów**

- niedozwolone ❌ **: Dodawanie lub usuwanie słowa kluczowego [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) lub [ref](../../csharp/language-reference/keywords/ref.md) z parametru**

- niedozwolone ❌ **: zmiana nazwy parametru (w tym zmiana jego wielkości liter)**

  Jest to uważane za rozdzielenie z dwóch powodów:

  - Dzieli scenariusze z późnym wiązaniem, takie jak funkcja późnego wiązania w Visual Basic C#i [dynamiczna](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) w.

  - Jest ona podzielona na [zgodność źródłową](categories.md#source-compatibility) , gdy deweloperzy używają [nazwanych argumentów](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- ❌ **niedozwolone: zmiana z `ref` wartości zwracanej na `ref readonly` wartość zwracana**

- niedozwolone ❌️ **: zmiana z `ref readonly` na `ref` wartość zwracana w wirtualnej metodzie lub interfejsie**

- niedozwolone ❌ **: Dodawanie lub usuwanie [abstrakcyjnej](../../csharp/language-reference/keywords/abstract.md) z elementu członkowskiego**

- niedozwolone ❌ **: Usuwanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego z elementu członkowskiego**

  Chociaż często nie jest to istotna zmiana, C# ponieważ kompilator zamierza emitować instrukcje języka pośredniego (IL) elementu [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) do wywoływania metod niewirtualnych (`callvirt` wykonuje sprawdzanie wartości null, podczas gdy normalne wywołanie nie jest), to zachowanie nie jest zmienne z kilku powodów:
  - C#nie jest jedynym językiem, który jest obiektem docelowym platformy .NET.

  - C# Kompilator coraz bardziej próbuje zoptymalizować `callvirt` do normalnego wywołania, gdy metoda docelowa nie jest wirtualna i prawdopodobnie nie ma wartości null (na przykład metodę dostępną za pomocą [operatora propagacji?. null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).

  Zastosowanie metody wirtualnej oznacza, że kod konsumenta często kończy wywoływanie go niepraktycznie.

- niedozwolone ❌ **: Dodawanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego do elementu członkowskiego**

- niedozwolone ❌ **: wykonywanie abstrakcyjnej składowej wirtualnego**

  [Wirtualny element członkowski](../../csharp/language-reference/keywords/virtual.md) zawiera implementację metody, która *może zostać* zastąpiona przez klasę pochodną. [Abstrakcyjny element członkowski](../../csharp/language-reference/keywords/abstract.md) nie zawiera implementacji i *musi zostać* zastąpiony.

- niedozwolone ❌ **: Dodawanie abstrakcyjnej składowej do typu publicznego, który ma dostępne (publiczne lub chronione) konstruktory, które nie są [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**

- niedozwolone ❌ **: Dodawanie lub usuwanie [statycznego](../../csharp/language-reference/keywords/static.md) słowa kluczowego z elementu członkowskiego**

- niedozwolone ❌ **: Dodawanie przeciążenia, które wyklucza istniejące Przeciążenie i definiuje inne zachowanie**

  Spowoduje to przerwanie istniejących klientów, które zostały powiązane z poprzednim przeciążeniem. Na przykład jeśli klasa ma jedną wersję metody, która akceptuje <xref:System.UInt32>, istniejący Klient pomyślnie powiąże się z tym przeciążeniem podczas przekazywania wartości <xref:System.Int32>. Jednakże jeśli dodasz Przeciążenie, które akceptuje <xref:System.Int32>, podczas ponownego kompilowania lub korzystania z późnego wiązania, kompilator teraz tworzy powiązanie z nowym przeciążeniem. W przypadku innych wyników zachowania jest to istotna zmiana.

- niedozwolone ❌ **: Dodawanie konstruktora do klasy, która wcześniej nie miała konstruktora bez dodawania konstruktora bezparametrowego**

- niedozwolone ❌️ **: Dodawanie elementu [ReadOnly](../../csharp/language-reference/keywords/readonly.md) do pola**

- niedozwolone ❌ **: zmniejszanie widoczności elementu członkowskiego**

   Obejmuje to zmniejszenie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy istnieją *dostępne* konstruktory (`public` lub `protected`), a typ *nie* jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md). Jeśli tak się nie dzieje, zmniejszenie widoczności chronionego elementu członkowskiego jest dozwolone.

   Zwiększenie widoczności elementu członkowskiego jest dozwolone.

- niedozwolone ❌ **: zmiana typu elementu członkowskiego**

   Nie można zmodyfikować wartości zwracanej przez metodę lub typ właściwości lub pola. Na przykład sygnatura metody zwracającej <xref:System.Object> nie może zostać zmieniona w celu zwrócenia <xref:System.String>lub na odwrót.

- niedozwolone ❌ **: Dodawanie pola do struktury, która wcześniej nie miała stanu**

  Określone reguły przypisywania umożliwiają użycie niezainicjowanych zmiennych, tak długo, jak typ zmiennej jest strukturą bezstanową. Jeśli struktura jest stanowa, kod może kończyć się zainicjowanymi danymi. Może to być zarówno uszkodzenie źródła, jak i uszkodzenie binarne.

- niedozwolone ❌ **: wyzwalanie istniejącego zdarzenia, gdy wcześniej nie zostało ono wyzwolone**

## <a name="behavioral-changes"></a>Zmiany behawioralne

### <a name="assemblies"></a>Zestawy

- ✔️ **dozwolone: Tworzenie zestawu przenośnego, gdy te same platformy są nadal obsługiwane**

- niedozwolone ❌ **: zmiana nazwy zestawu**
- niedozwolone ❌ **: Zmiana klucza publicznego zestawu**

### <a name="properties-fields-parameters-and-return-values"></a>Właściwości, pola, parametry i wartości zwracane

- ✔️ **dozwolone: zmiana wartości właściwości, pola, wartości zwracanej lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na bardziej pochodny typ**

  Na przykład Metoda zwracająca typ <xref:System.Object> może zwracać wystąpienie <xref:System.String>. Nie można jednak zmienić sygnatury metody.)

- ✔️ **dozwolone: zwiększenie zakresu akceptowanych wartości właściwości lub parametru, jeśli element członkowski nie jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**

  W czasie, gdy zakres wartości, które mogą być przesyłane do metody lub są zwracane przez element członkowski, można rozwinąć, parametr lub typ elementu członkowskiego nie mogą. Na przykład, podczas gdy wartości przesyłane do metody mogą rozszerzać od 0-124 do 0-255, typ parametru nie może ulec zmianie z <xref:System.Byte> na <xref:System.Int32>.

- niedozwolone ❌ **: zwiększenie zakresu akceptowanych wartości właściwości lub parametru, jeśli element członkowski jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**

   Ta zmiana powoduje przerwanie istniejących przesłoniętych elementów członkowskich, które nie będą działać poprawnie dla rozszerzonego zakresu wartości.

- niedozwolone ❌ **: zmniejszanie zakresu akceptowanych wartości dla właściwości lub parametru**

- niedozwolone ❌ **: zwiększenie zakresu zwracanych wartości dla właściwości, pola, wartości zwracanej lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**

- niedozwolone ❌ **: zmiana zwracanych wartości właściwości, pola, wartości zwracanej metody lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**

- niedozwolone ❌ **: zmiana wartości domyślnej właściwości, pola lub parametru**

- niedozwolone ❌ **: zmiana dokładności liczbowej wartości zwracanej**

- ❓ **Wymaga orzeczenia: zmiana analizy danych wejściowych i zgłaszanie nowych wyjątków (nawet jeśli nie określono zachowania analizy w dokumentacji**

### <a name="exceptions"></a>Wyjątki

- ✔️ **dozwolone: Zgłaszanie bardziej pochodnego wyjątku niż istniejący wyjątek**

  Ponieważ nowy wyjątek jest podklasą istniejącego wyjątku, poprzedni kod obsługi wyjątków nadal obsłużył wyjątek. Na przykład w .NET Framework 4, metody tworzenia i pobierania kultur zaczęły zgłosić <xref:System.Globalization.CultureNotFoundException> zamiast <xref:System.ArgumentException>, jeśli nie można odnaleźć kultury. Ponieważ <xref:System.Globalization.CultureNotFoundException> pochodzi od <xref:System.ArgumentException>, jest to akceptowalna zmiana.

- ✔️ **dozwolone: Zgłaszanie bardziej szczegółowego wyjątku niż <xref:System.NotSupportedException>, <xref:System.NotImplementedException><xref:System.NullReferenceException>**

- ✔️ **dozwolone: Zgłaszanie wyjątku, który jest uznawany za niemożliwy do odzyskania**

  Niemożliwy do odzyskania wyjątki nie powinny być przechwytywane, ale powinny być obsługiwane przez obsługę catch-all o wysokim poziomie. W związku z tym użytkownicy nie powinny mieć kodu, który przechwytuje te jawne wyjątki. Nieodwracalne wyjątki są następujące:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- ✔️ **dozwolone: Zgłaszanie nowego wyjątku w nowej ścieżce kodu**

  Wyjątek musi dotyczyć tylko nowej ścieżki kodu, która jest wykonywana z nowymi wartościami parametrów lub stanem, ale nie może zostać wykonana przez istniejący kod, który jest przeznaczony dla poprzedniej wersji.

- ✔️ **dozwolone: usuwanie wyjątku, aby umożliwić bardziej niezawodne zachowanie lub nowe scenariusze**

  Na przykład Metoda `Divide`, która wcześniej obsługiwała tylko wartości dodatnie i wywołała <xref:System.ArgumentOutOfRangeException> w przeciwnym razie można zmienić, aby obsługiwała wartości ujemne i dodatnie bez zgłaszania wyjątku.

- ✔️ **dozwolone: Zmiana tekstu komunikatu o błędzie**

  Deweloperzy nie powinni polegać na tekście komunikatów o błędach, które również zmieniają się w zależności od kultury użytkownika.

- niedozwolone ❌ **: Zgłaszanie wyjątku w innym przypadku niewymienionym powyżej**

- niedozwolone ❌ **: usuwanie wyjątku w żadnym innym przypadku niewymienionym powyżej**

### <a name="attributes"></a>{1&gt;{2&gt;Atrybuty&lt;2}&lt;1}

- ✔️ **dozwolone: zmiana wartości atrybutu, który *nie* jest zauważalny**

- ❌ **niedozwolone: zmiana wartości atrybutu, który *jest* zauważalny**

- ❓ **Wymaga orzeczenia: usuwanie atrybutu**

  W większości przypadków usunięcie atrybutu (takiego jak <xref:System.NonSerializedAttribute>) jest istotną zmianą.

## <a name="platform-support"></a>Obsługa platform

- ✔️ **dozwolone: obsługa operacji na platformie, która była wcześniej nieobsługiwana**

- niedozwolone ❌ **: nieobsługujące lub obecnie wymagający określonego dodatku Service Pack dla operacji, która była wcześniej obsługiwana na platformie**

## <a name="internal-implementation-changes"></a>Wewnętrzne zmiany implementacji

- ❓ **Wymaga orzeczenia: zmiana obszaru powierzchni typu wewnętrznego**

   Takie zmiany są zwykle dozwolone, chociaż przerywają odbicie prywatne. W niektórych przypadkach, gdy popularne biblioteki innych firm lub duża liczba deweloperów zależą od wewnętrznych interfejsów API, takie zmiany mogą nie być dozwolone.

- ❓ **Wymaga orzeczenia: zmiana wewnętrznej implementacji elementu członkowskiego**

  Te zmiany są ogólnie dozwolone, chociaż przerywają odbicie prywatne. W niektórych przypadkach, gdzie kod klienta często zależy od odbicia prywatnego lub gdzie zmiana wprowadza niezamierzone efekty uboczne, te zmiany mogą być niedozwolone.

- ✔️ **dozwolone: poprawa wydajności operacji**

   Możliwość modyfikowania wydajności operacji jest istotna, ale takie zmiany mogą spowodować przerwanie kodu, który opiera się na bieżącej szybkości operacji. Jest to szczególnie prawdziwe w przypadku kodu, który zależy od chronometrażu operacji asynchronicznych. Zmiana wydajności nie powinna mieć wpływu na inne zachowanie interfejsu API. w przeciwnym razie zmiana zostanie przerwana.

- ✔️ **dozwolone: pośrednio (i często niekorzystnie) zmiana wydajności operacji**

  Jeśli dana zmiana nie zostanie skategoryzowana z innego powodu, jest to dopuszczalne. Często należy podjąć działania, które mogą obejmować dodatkowe operacje lub dodając nowe funkcje. Prawie zawsze ma to wpływ na wydajność, ale może być konieczne, aby interfejs API działał w oczekiwany sposób.

- niedozwolone ❌ **: zmiana synchronicznego interfejsu API na asynchroniczny (i odwrotnie)**

## <a name="code-changes"></a>Zmiany kodu

- ✔️ **dozwolone: Dodawanie [parametrów](../../csharp/language-reference/keywords/params.md) do parametru**

- ❌ **niedozwolone: zmiana [struktury](../../csharp/language-reference/keywords/struct.md) na [klasę](../../csharp/language-reference/keywords/class.md) i odwrotnie**

- niedozwolone ❌ **: Dodawanie słowa kluczowego [Checked](../../csharp/language-reference/keywords/virtual.md) do bloku kodu**

   Ta zmiana może spowodować, że kod, który został wcześniej wykonany, aby zgłosić <xref:System.OverflowException> i jest nieakceptowalny.

- niedozwolone ❌ **: Usuwanie [parametrów](../../csharp/language-reference/keywords/params.md) z parametru**

- niedozwolone ❌ **: zmiana kolejności, w której są uruchamiane zdarzenia**

  Deweloperzy mogą w rozsądny sposób oczekiwać, że wyzwalają zdarzenia w tej samej kolejności, a kod dewelopera często zależy od kolejności, w jakiej są uruchamiane zdarzenia.

- niedozwolone ❌ **: usuwanie podniesienia poziomu zdarzenia do danej akcji**

- niedozwolone ❌ **: zmiana liczby przypadków, gdy są wywoływane zdarzenia**

- niedozwolone ❌ **: dodawanie <xref:System.FlagsAttribute> do typu wyliczenia**
