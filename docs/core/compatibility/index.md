---
title: Rodzaje przełomowych zmian
description: Dowiedz się, jak program .NET Core próbuje zachować zgodność deweloperów w wersjach .NET i jaki rodzaj zmiany jest uważany za przełomową zmianę.
ms.date: 06/10/2019
ms.openlocfilehash: bf0cc35d69e6bb501640455604a99a1f48962c4a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "77628595"
---
# <a name="changes-that-affect-compatibility"></a>Zmiany wpływające na zgodność

W całej swojej historii .NET próbował utrzymać wysoki poziom zgodności z wersji do wersji i różnych smaków .NET. To nadal dotyczy .NET Core. Chociaż .NET Core można uznać za nową technologię, która jest niezależna od .NET Framework, dwa główne czynniki ograniczają możliwość odejścia programu .NET Core od platformy .NET Framework:

- Duża liczba deweloperów pierwotnie opracowanych lub nadal rozwijać aplikacje .NET Framework. Oczekują spójne zachowanie w implementacjach .NET.

- Projekty biblioteki standardu .NET umożliwiają deweloperom tworzenie bibliotek docelowych dla typowych interfejsów API współużytkowane przez .NET Core i .NET Framework. Deweloperzy oczekują, że biblioteka używana w aplikacji .NET Core powinna zachowywać się identycznie jak ta sama biblioteka używana w aplikacji .NET Framework.

Wraz ze zgodnością w implementacjach .NET deweloperzy oczekują wysokiego poziomu zgodności w wersjach .NET Core. W szczególności kod napisany dla starszej wersji programu .NET Core powinien działać bezproblemowo w nowszej wersji programu .NET Core. W rzeczywistości wielu deweloperów oczekuje, że nowe interfejsy API znalezione w nowo wydanych wersjach programu .NET Core powinny być również zgodne z wersjami wstępnymi, w których wprowadzono te interfejsy API.

W tym artykule opisano kategorie zmian zgodności (lub zmiany dotyczące podziału) oraz sposób, w jaki zespół .NET ocenia zmiany w każdej z tych kategorii. Zrozumienie, jak zespół platformy .NET podchodzi do możliwych zmian krytycznych, jest szczególnie przydatne dla deweloperów, którzy otwierają żądania ściągnięcia w repozytorium GitHub [dotnet/runtime,](https://github.com/dotnet/runtime) które modyfikują zachowanie istniejących interfejsów API.

> [!NOTE]
> Aby uzyskać definicję kategorii zgodności, takich jak zgodność binarna i zgodność z poprzednimi [wersjami,](categories.md)zobacz Kategorie zmian podziału .

W poniższych sekcjach opisano kategorie zmian w interfejsach API .NET Core i ich wpływ na zgodność aplikacji. Zmiany są dozwolone ✔️, ❌niedozwolone, lub wymagają oceny i oceny, jak przewidywalne, oczywiste i spójne poprzednie zachowanie było ❓.

> [!NOTE]
> Oprócz wyświetlania jako przewodnik po tym, jak są oceniane zmiany w bibliotekach .NET Core, deweloperzy bibliotek mogą również używać tych kryteriów do oceny zmian w swoich bibliotekach, które są przeznaczone dla wielu implementacji i wersji .NET.

## <a name="modifications-to-the-public-contract"></a>Zmiany w zamówień publicznych

Zmiany w tej kategorii modyfikują publiczny obszar powierzchni typu. Większość zmian w tej kategorii są niedozwolone, ponieważ naruszają *wsteczną zgodność* (zdolność aplikacji, która została opracowana z poprzedniej wersji interfejsu API do wykonania bez ponownej kompilacji w nowszej wersji).

### <a name="types"></a>Typy

- ✔️ **DOZWOLONE: Usuwanie implementacji interfejsu z typu, gdy interfejs jest już zaimplementowany przez typ podstawowy**

- ❓ **WYMAGA WYROKU: Dodawanie nowej implementacji interfejsu do typu**

  Jest to akceptowalna zmiana, ponieważ nie wpływa niekorzystnie na istniejących klientów. Wszelkie zmiany typu muszą działać w granicach dopuszczalnych zmian zdefiniowanych w tym miejscu, aby nowa implementacja pozostała możliwa do zaakceptowania. Szczególna ostrożność jest konieczne podczas dodawania interfejsów, które bezpośrednio wpływają na zdolność projektanta lub serializatora do generowania kodu lub danych, które nie mogą być używane w dół poziomu. Przykładem jest <xref:System.Runtime.Serialization.ISerializable> interfejs.

- ❓ **WYMAGA WYROKU: Wprowadzenie nowej klasy podstawowej**

  Typ można wprowadzić do hierarchii między dwoma istniejącymi typami, jeśli nie wprowadza żadnych nowych [abstrakcyjnych](../../csharp/language-reference/keywords/abstract.md) elementów członkowskich lub zmienić semantykę lub zachowanie istniejących typów. Na przykład w .NET Framework 2.0 <xref:System.Data.Common.DbConnection> klasa stała <xref:System.Data.SqlClient.SqlConnection>się nową klasą podstawową dla , która wcześniej pochodziła bezpośrednio z <xref:System.ComponentModel.Component>.

- ✔️ **DOZWOLONE: Przenoszenie typu z jednego zespołu do drugiego**

  *Stary* zespół musi być <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> oznaczony, że wskazuje na nowy zespół.

- ✔️ **DOZWOLONE: [struct](../../csharp/language-reference/builtin-types/struct.md) Zmiana typu struktury `readonly struct` na typ**

  Zmiana `readonly struct` typu na `struct` typ jest niedozwolona.

- ✔️ **DOZWOLONE: Dodawanie [zapieczętowanego](../../csharp/language-reference/keywords/sealed.md) lub [abstrakcyjnego](../../csharp/language-reference/keywords/abstract.md) słowa kluczowego do typu, gdy nie ma *dostępnych* (publicznych lub chronionych) konstruktorów**

- ✔️ **DOZWOLONE: Rozszerzenie widoczności typu**

- ❌**NIEDOZWOLONE: Zmiana obszaru nazw lub nazwy typu**

- ❌**NIEDOZWOLONE: Zmiana nazwy lub usunięcie typu publicznego**

   Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego typu.

- ❌**NIEDOZWOLONE: Zmiana podstawowego typu wyliczenia**

   Jest to zmiana podziału czasu kompilacji i zachowania, a także zmiana podziału binarnego, która może sprawić, że argumenty atrybutów będą nierozłączne.

- ❌**NIEDOZWOLONE: Uszczelnianie typu, który był wcześniej niezapieczętowany**

- ❌**NIEDOZWOLONE: Dodawanie interfejsu do zestawu typów podstawowych interfejsu**

   Jeśli interfejs implementuje interfejs, który wcześniej nie zaimplementował, wszystkie typy, które zaimplementowane oryginalnej wersji interfejsu są przerwane.

- ❓ **WYMAGA WYROKU: Usunięcie klasy z zestawu klas podstawowych lub interfejsu z zestawu zaimplementowanych interfejsów**

  Istnieje jeden wyjątek od reguły usuwania interfejsu: można dodać implementację interfejsu, który pochodzi z usuniętego interfejsu. Na przykład można <xref:System.IDisposable> usunąć, jeśli typ lub <xref:System.ComponentModel.IComponent>interfejs teraz <xref:System.IDisposable>implementuje , który implementuje .

- ❌**NIEDOZWOLONE: Zmiana `readonly struct` typu na typ [struktury](../../csharp/language-reference/builtin-types/struct.md) **

  Zmiana `struct` typu na typ `readonly struct` jest jednak dozwolona.

- ❌**NIEDOZWOLONE: Zmiana typu [struktury](../../csharp/language-reference/builtin-types/struct.md) na `ref struct` typ i na odwrót**

- ❌**NIEDOZWOLONE: Zmniejszenie widoczności typu**

   Jednak zwiększenie widoczności typu jest dozwolone.

### <a name="members"></a>Elementy członkowskie

- ✔️ **DOZWOLONE: Rozszerzanie widoczności elementu członkowskiego, który nie jest [wirtualny](../../csharp/language-reference/keywords/sealed.md) **

- ✔️ **DOZWOLONE: Dodawanie abstrakcyjnego elementu członkowskiego do typu publicznego, który nie ma *dostępnych* (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md) **

  Jednak dodanie abstrakcyjnego elementu członkowskiego do typu, który ma dostępne `sealed` (publiczne lub chronione) konstruktory i nie jest dozwolone.

- ✔️ **DOZWOLONE: Ograniczenie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego, gdy typ nie ma dostępnych (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md) **

- ✔️ **DOZWOLONE: Przeniesienie elementu członkowskiego do klasy wyższej w hierarchii niż typ, z którego został usunięty**

- ✔️ **DOZWOLONE: Dodawanie lub usuwanie zastąpienia**

  Wprowadzenie zastąpienia może spowodować, że poprzedni konsumenci przesunęli się przez zastąpienie podczas wywoływania [bazy](../../csharp/language-reference/keywords/base.md).

- ✔️ **DOZWOLONE: Dodawanie konstruktora do klasy wraz z konstruktorem bezparametrów, jeśli klasa wcześniej nie miała konstruktorów**

   Jednak dodanie konstruktora do klasy, która wcześniej nie miała konstruktorów *bez* dodawania konstruktora bezparametrów, nie jest dozwolone.

- ✔️ **DOZWOLONE: Zmiana elementu członkowskiego z [abstrakcyjnego](../../csharp/language-reference/keywords/abstract.md) na [wirtualny](../../csharp/language-reference/keywords/virtual.md) **

- ✔️ **DOZWOLONE: Zmiana `ref readonly` wartości `ref` zwracanej na wartość (z wyjątkiem metod wirtualnych lub interfejsów)**

- ✔️ **DOZWOLONE: Usuwanie [tylko odczytu](../../csharp/language-reference/keywords/readonly.md) z pola, chyba że typ statyczny pola jest typem wartości zapisywanych**

- ✔️ **DOZWOLONE: wywoływanie nowego zdarzenia, które nie było wcześniej zdefiniowane**

- ❓ **WYMAGA WYROKU: Dodawanie nowego pola instancji do typu**

   Ta zmiana ma wpływ na serializację.

- ❌**NIEDOZWOLONE: Zmiana nazwy lub usunięcie publicznego elementu członkowskiego lub parametru**

   Spowoduje to przerwanie całego kodu, który używa zmienionego lub usuniętego elementu członkowskiego lub parametru.

   Obejmuje to usunięcie lub zmianę nazwy getter lub setter z właściwości, a także zmiana nazwy lub usunięcie elementów członkowskich wyliczenia.

- ❌**NIEDOZWOLONE: Dodawanie elementu członkowskiego do interfejsu**

- ❌**NIEDOZWOLONE: Zmiana wartości elementu członkowskiego stałej publicznej lub wyliczenia**

- ❌**NIEDOZWOLONE: Zmiana typu właściwości, pola, parametru lub wartości zwracanej**

- ❌**NIEDOZWOLONE: Dodawanie, usuwanie lub zmienianie kolejności parametrów**

- ❌**NIEDOZWOLONE: Dodawanie lub usuwanie [słowa](../../csharp/language-reference/keywords/in.md)kluczowego in , [out](../../csharp/language-reference/keywords/out.md) lub [ref](../../csharp/language-reference/keywords/ref.md) z parametru**

- ❌**NIEDOZWOLONE: Zmiana nazwy parametru (w tym zmiana jego przypadku)**

  Jest to uważane za złamanie z dwóch powodów:

  - Przerywa scenariusze późnego wiązania, takie jak funkcja późnego wiązania w języku Visual Basic i [dynamiczna](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) w języku C#.

  - Przerywa [zgodność źródła,](categories.md#source-compatibility) gdy deweloperzy używają [nazwanych argumentów](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- ❌**NIEDOZWOLONE: Zmiana wartości `ref` zwracanej `ref readonly` na wartość zwracaną**

- ❌️**NIEDOZWOLONE: Zmiana wartości `ref readonly` zwracanej `ref` na wirtualną metodę lub interfejs**

- ❌**NIEDOZWOLONE: Dodawanie lub usuwanie [streszczenia](../../csharp/language-reference/keywords/abstract.md) z elementu członkowskiego**

- ❌**NIEDOZWOLONE: Usuwanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego z elementu członkowskiego**

  Chociaż często nie jest to zmiana podziału, ponieważ kompilator Języka C#ma tendencję do emitowania [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) języka pośredniego (IL) instrukcje do wywołania metod innych niż wirtualne (`callvirt` wykonuje sprawdzanie wartości null, podczas gdy normalne wywołanie nie), to zachowanie nie jest zmienna z kilku powodów:
  - C# nie jest jedynym językiem, który .

  - Kompilator Języka C# `callvirt` coraz częściej próbuje zoptymalizować do normalnego wywołania, gdy metoda docelowa nie jest wirtualny i prawdopodobnie nie jest null (na przykład metoda dostępna za pośrednictwem [?. null propagacji operatora).](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)

  Tworzenie metody wirtualnej oznacza, że kod konsumenta często kończy się wywołanie go nie-praktycznie.

- ❌**NIEDOZWOLONE: Dodawanie [wirtualnego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego do członka**

- ❌**NIEDOZWOLONE: Tworzenie abstrakcyjnego elementu wirtualnego**

  [Wirtualny element członkowski](../../csharp/language-reference/keywords/virtual.md) zapewnia implementację metody, które *mogą być* zastąpione przez klasę pochodną. [Abstrakcyjny element członkowski](../../csharp/language-reference/keywords/abstract.md) nie zapewnia implementacji i *musi zostać* zastąpiony.

- ❌**NIEDOZWOLONE: Dodawanie abstrakcyjnego elementu członkowskiego do typu publicznego, który ma dostępne (publiczne lub chronione) konstruktory i który nie jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md) **

- ❌**NIEDOZWOLONE: Dodawanie lub usuwanie [statycznego](../../csharp/language-reference/keywords/static.md) słowa kluczowego z elementu członkowskiego**

- ❌**NIEDOZWOLONE: Dodawanie przeciążenia, które wyklucza istniejące przeciążenie i definiuje inne zachowanie**

  Spowoduje to przerwanie istniejących klientów, które były powiązane z poprzednim przeciążeniem. Na przykład jeśli klasa ma jedną wersję <xref:System.UInt32>metody, która akceptuje , istniejący konsument pomyślnie powiąże <xref:System.Int32> się z tym przeciążeniem podczas przekazywania wartości. Jednak jeśli dodasz przeciążenie, <xref:System.Int32>które akceptuje , podczas ponownej kompilacji lub przy użyciu późnego wiązania, kompilator teraz wiąże się z nowym przeciążeniem. Jeśli różne wyniki zachowania, jest to zmiana podziału.

- ❌**NIEDOZWOLONE: Dodawanie konstruktora do klasy, która wcześniej nie miała konstruktora bez dodawania konstruktora bezparametrów**

- ❌️**NIEDOZWOLONE: Dodawanie tylko do [odczytu](../../csharp/language-reference/keywords/readonly.md) do pola**

- ❌**NIEDOZWOLONE: Zmniejszenie widoczności elementu członkowskiego**

   Obejmuje to zmniejszenie widoczności [chronionego](../../csharp/language-reference/keywords/protected.md) elementu członkowskiego,`public` `protected`gdy istnieją *dostępne* (lub) konstruktory, a typ *nie* jest [zapieczętowany.](../../csharp/language-reference/keywords/sealed.md) Jeśli tak nie jest, zmniejszenie widoczności chronionego elementu członkowskiego jest dozwolone.

   Zwiększenie widoczności elementu członkowskiego jest dozwolone.

- ❌**NIEDOZWOLONE: Zmiana typu elementu członkowskiego**

   Nie można zmodyfikować wartości zwracanej metody lub typu właściwości lub pola. Na przykład podpis metody, która <xref:System.Object> zwraca nie można <xref:System.String>zmienić, aby zwrócić , lub odwrotnie.

- ❌**NIEDOZWOLONE: Dodawanie pola do struktury, która wcześniej nie miała żadnego stanu**

  Reguły przypisania określonego zezwalają na używanie zmiennych niezainicjowanych, o ile typ zmiennej jest strukturą bezstanową. Jeśli struktura jest stanowa, kod może skończyć się z niezainicjowanych danych. Jest to zarówno potencjalnie źródło zerwania i binarnych zmian podziału.

- ❌**NIEDOZWOLONE: Wypalanie istniejącego zdarzenia, gdy nigdy nie zostało odpalone przed**

## <a name="behavioral-changes"></a>Zmiany w zachowaniu

### <a name="assemblies"></a>Zestawy

- ✔️ **DOZWOLONE: Wykonywanie przenośnego montażu, gdy te same platformy są nadal obsługiwane**

- ❌**NIEDOZWOLONE: Zmiana nazwy zestawu**
- ❌**NIEDOZWOLONE: Zmiana klucza publicznego zestawu**

### <a name="properties-fields-parameters-and-return-values"></a>Właściwości, pola, parametry i wartości zwracane

- ✔️ **DOZWOLONE: Zmiana wartości właściwości, pola, wartości zwracanej lub [parametru out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na typ bardziej pochodny**

  Na przykład metoda, która zwraca <xref:System.Object> typ <xref:System.String> może zwrócić wystąpienie. (Jednak podpis metody nie może ulec zmianie).

- ✔️ **DOZWOLONE: Zwiększenie zakresu akceptowanych wartości dla właściwości lub parametru, jeśli element [członkowski](../../csharp/language-reference/keywords/virtual.md) nie jest wirtualny**

  Podczas gdy zakres wartości, które mogą być przekazywane do metody lub są zwracane przez element członkowski można rozwinąć, parametr lub typ elementu członkowskiego nie może. Na przykład, podczas gdy wartości przekazywane do metody można rozwinąć od 0-124 do <xref:System.Byte> 0-255, typ parametru nie można zmienić z . <xref:System.Int32>

- ❌**NIEDOZWOLONE: Zwiększenie zakresu akceptowanych wartości dla właściwości lub parametru, jeśli element [członkowski](../../csharp/language-reference/keywords/virtual.md) jest wirtualny**

   Ta zmiana przerywa istniejące elementy nadrzędnego, które nie będą działać poprawnie dla rozszerzonego zakresu wartości.

- ❌**NIEDOZWOLONE: Zmniejszenie zakresu akceptowanych wartości dla właściwości lub parametru**

- ❌**NIEDOZWOLONE: Zwiększenie zakresu zwracanych wartości dla parametru właściwości, pola, wartości zwracanej lub [wychodzącej](../../csharp/language-reference/keywords/out-parameter-modifier.md) **

- ❌**NIEDOZWOLONE: Zmiana zwracanych wartości dla właściwości, pola, wartości zwracanej metody lub [parametru out](../../csharp/language-reference/keywords/out-parameter-modifier.md) **

- ❌**NIEDOZWOLONE: Zmiana wartości domyślnej właściwości, pola lub parametru**

- ❌**NIEDOZWOLONE: Zmiana dokładności wartości zwracanej liczbowej**

- ❓ **WYMAGA WYROKU: Zmiana w analizowaniu danych wejściowych i zgłaszaniu nowych wyjątków (nawet jeśli zachowanie analizy nie jest określone w dokumentacji**

### <a name="exceptions"></a>Wyjątki

- ✔️ **DOZWOLONE: Zgłaszanie wyjątku bardziej pochodnego niż istniejący wyjątek**

  Ponieważ nowy wyjątek jest podklasą istniejącego wyjątku, poprzedni kod obsługi wyjątków nadal obsługuje wyjątek. Na przykład w .NET Framework 4 metody tworzenia i pobierania <xref:System.Globalization.CultureNotFoundException> kultury <xref:System.ArgumentException> zaczęły zgłaszać zamiast if kultury nie można odnaleźć. Ponieważ <xref:System.Globalization.CultureNotFoundException> wywodzi się z <xref:System.ArgumentException>, jest to akceptowalna zmiana.

- ✔️ **DOZWOLONE: Rzucanie bardziej szczegółowy <xref:System.NotSupportedException> <xref:System.NotImplementedException>wyjątek <xref:System.NullReferenceException> niż ,**

- ✔️ **DOZWOLONE: Zgłaszanie wyjątku, który jest uważany za nieodwracalny**

  Nieodwracalne wyjątki nie powinny być przechwycone, ale zamiast tego powinny być obsługiwane przez program obsługi catch-all wysokiego poziomu. W związku z tym użytkownicy nie powinni mieć kod, który przechwytuje te jawne wyjątki. Nieodwracalne wyjątki to:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- ✔️ **DOZWOLONE: Zgłaszanie nowego wyjątku w nowej ścieżce kodu**

  Wyjątek musi mieć zastosowanie tylko do nowej ścieżki kodu, który jest wykonywany z nowych wartości parametrów lub stanu i które nie mogą być wykonywane przez istniejący kod, który jest przeznaczony dla poprzedniej wersji.

- ✔️ **DOZWOLONE: Usuwanie wyjątku, aby umożliwić bardziej niezawodne zachowanie lub nowe scenariusze**

  Na przykład `Divide` metoda, która wcześniej obsługiwała <xref:System.ArgumentOutOfRangeException> tylko wartości dodatnie i w przeciwnym razie, może zostać zmieniona w celu obsługi wartości ujemnych i dodatnich bez zgłaszania wyjątku.

- ✔️ **DOZWOLONE: Zmiana tekstu komunikatu o błędzie**

  Deweloperzy nie powinni polegać na tekście komunikatów o błędach, które również zmieniają się na podstawie kultury użytkownika.

- ❌**NIEDOZWOLONE: Zgłaszanie wyjątku w każdym innym przypadku nie wymienionym powyżej**

- ❌**NIEDOZWOLONE: Usuwanie wyjątku w każdym innym przypadku niewymienionym powyżej**

### <a name="attributes"></a>Atrybuty

- ✔️ **DOZWOLONE: Zmiana wartości atrybutu, który *nie* jest obserwowalny**

- ❌**NIEDOZWOLONE: Zmiana wartości atrybutu, który *jest* obserwowalny**

- ❓ **WYMAGA WYROKU: Usunięcie atrybutu**

  W większości przypadków usunięcie atrybutu <xref:System.NonSerializedAttribute>(na przykład) jest zmianą podziału.

## <a name="platform-support"></a>Obsługa platform

- ✔️ **DOZWOLONE: Obsługa operacji na platformie, która wcześniej nie była obsługiwana**

- ❌**NIEDOZWOLONE: Nie obsługuje lub teraz wymaga określonego dodatku Service Pack dla operacji, która była wcześniej obsługiwana na platformie**

## <a name="internal-implementation-changes"></a>Zmiany w implementacji wewnętrznej

- ❓ **WYMAGA WYROKU: Zmiana powierzchni typu wewnętrznego**

   Takie zmiany są ogólnie dozwolone, chociaż łamią prywatną refleksję. W niektórych przypadkach, gdy popularne biblioteki innych firm lub duża liczba deweloperów zależy od wewnętrznych interfejsów API, takie zmiany mogą nie być dozwolone.

- ❓ **WYMAGA WYROKU: Zmiana wewnętrznego wdrożenia członka**

  Zmiany te są ogólnie dozwolone, chociaż przerywają prywatną refleksję. W niektórych przypadkach, gdy kod klienta często zależy od prywatnego odbicia lub gdy zmiana wprowadza niezamierzone skutki uboczne, zmiany te mogą nie być dozwolone.

- ✔️ **DOZWOLONE: Poprawa wydajności operacji**

   Możliwość modyfikowania wydajności operacji jest niezbędna, ale takie zmiany mogą złamać kod, który opiera się na bieżącej szybkości operacji. Jest to szczególnie prawdziwe w przypadku kodu, który zależy od czasu operacji asynchronicznych. Zmiana wydajności nie powinna mieć wpływu na inne zachowanie danego interfejsu API; w przeciwnym razie zmiana będzie przełomowa.

- ✔️ **DOZWOLONE: Pośrednio (i często niekorzystnie) zmiana wykonania operacji**

  Jeśli dany przepis nie jest sklasyfikowany jako łamanie z innego powodu, jest to dopuszczalne. Często należy podjąć działania, które mogą obejmować dodatkowe operacje lub które dodają nowe funkcje. To prawie zawsze wpłynie na wydajność, ale może być niezbędne, aby interfejs API, o których mowa, działał zgodnie z oczekiwaniami.

- ❌**NIEDOZWOLONE: Zmiana synchronicznego interfejsu API na asynchroniczny (i odwrotnie)**

## <a name="code-changes"></a>Zmiany kodu

- ✔️ **DOZWOLONE: Dodawanie [paramów](../../csharp/language-reference/keywords/params.md) do parametru**

- ❌**NIEDOZWOLONE: Zmiana [struktury](../../csharp/language-reference/builtin-types/struct.md) na [klasę](../../csharp/language-reference/keywords/class.md) i odwrotnie**

- ❌**NIEDOZWOLONE: Dodawanie [zaznaczonego](../../csharp/language-reference/keywords/virtual.md) słowa kluczowego do bloku kodu**

   Ta zmiana może spowodować kod, <xref:System.OverflowException> który wcześniej wykonywane do wyrzucania i jest nie do przyjęcia.

- ❌**NIEDOZWOLONE: Usuwanie [paramów](../../csharp/language-reference/keywords/params.md) z parametru**

- ❌**NIEDOZWOLONE: Zmiana kolejności, w jakiej zdarzenia są uruchamiane**

  Deweloperzy mogą rozsądnie oczekiwać, że zdarzenia będą uruchamiane w tej samej kolejności, a kod dewelopera często zależy od kolejności, w jakiej są uruchamiane zdarzenia.

- ❌**NIEDOZWOLONE: Usuwanie poruszenie zdarzenia w danej akcji**

- ❌**NIEDOZWOLONE: Zmiana liczby podanych zdarzeń jest wywoływana**

- ❌**NIEDOZWOLONE: Dodawanie <xref:System.FlagsAttribute> do typu wyliczenia**
