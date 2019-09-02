---
title: Oszacowanie istotnych zmian — .NET Core
description: Dowiedz się więcej na temat sposobu, w jaki platforma .NET Core próbuje zachować zgodność dla deweloperów w różnych wersjach programu .NET.
author: rpetrusha
ms.author: ronpet
ms.date: 06/10/2019
ms.openlocfilehash: c68a19b8b98a98bb9c64f5b9fa60b378935e6e93
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/02/2019
ms.locfileid: "67736561"
---
# <a name="evaluate-breaking-changes-in-net-core"></a>Oszacowanie istotnych zmian w programie .NET Core

W całej historii środowisko .NET podjęło próbę utrzymania wysokiego poziomu zgodności z wersji do wersji i w różnych wersjach platformy .NET. Jest to nadal prawdziwe dla platformy .NET Core. Mimo że platforma .NET Core może być traktowana jako nowa technologia, która jest niezależna od .NET Framework, dwa główne czynniki ograniczają możliwość rozbieżności programu .NET Core od .NET Framework:

- Duża liczba deweloperów pierwotnie opracowała lub kontynuowała opracowywanie .NET Framework aplikacji. Oczekują one spójnego zachowania w implementacjach platformy .NET.

- .NET Standard projekty biblioteki umożliwiają deweloperom tworzenie bibliotek przeznaczonych dla wspólnych interfejsów API udostępnionych przez platformę .NET Core i .NET Framework. Deweloperzy oczekują, że biblioteka używana w aplikacji .NET Core powinna zachowywać się identycznie z tą samą biblioteką używaną w aplikacji .NET Framework.

Wraz ze zgodnością w ramach implementacji platformy .NET deweloperzy oczekują wysokiego poziomu zgodności między wersjami programu .NET Core. W szczególności kod zapisany dla starszej wersji programu .NET Core powinien działać bezproblemowo na nowszej wersji platformy .NET Core. W rzeczywistości wielu deweloperów oczekuje, że nowe interfejsy API znajdujące się w nowo wydanej wersji platformy .NET Core powinny również być zgodne z wersjami wstępnymi, w których zostały wprowadzone te interfejsy API.

W tym artykule przedstawiono kategorie zmian zgodności (lub istotne zmiany) oraz sposób, w jaki zespół .NET oceni zmiany w każdej z tych kategorii. Zrozumienie, w jaki sposób zespół .NET poddaje potencjalne istotne zmiany, jest szczególnie przydatny dla deweloperów, którzy otwierają żądania ściągnięcia w repozytorium GitHub [/corefx](https://github.com/dotnet/corefx) , które modyfikują zachowanie istniejących interfejsów API.

> [!NOTE]
> Aby zapoznać się z definicją kategorii zgodności, takich jak zgodność binarna i zgodność z poprzednimi wersjami, zobacz artykuł dotyczący [zmiany kategorii](categories.md).

W poniższych sekcjach opisano kategorie zmian wprowadzonych w interfejsach API programu .NET Core i ich wpływ na zgodność aplikacji. Ikona ✔️ wskazuje, że określony rodzaj zmiany jest dozwolony, ❌ wskazuje, że jest niedozwolone, a ❓ wskazuje zmianę, która może lub nie jest dozwolona. Zmiany w tej ostatniej kategorii wymagają orzeczenia i oceny, jak przewidywalne, oczywiste i spójne poprzednie zachowanie było.

> [!NOTE]
> Oprócz obsługi programu jako wskazówki dotyczącej oceny zmian w bibliotekach .NET Core, deweloperzy biblioteki mogą również używać tych kryteriów do oceny zmian w bibliotekach przeznaczonych dla wielu implementacji i wersji platformy .NET.

## <a name="modifications-to-the-public-contract"></a>Modyfikacje kontraktu publicznego

Zmiany w tej kategorii *modyfikują* publiczną powierzchnię typu. Większość zmian w tej kategorii jest niedozwolona, ponieważ naruszają *zgodność* z poprzednimi wersjami (zdolność aplikacji, która została opracowana przy użyciu poprzedniej wersji interfejsu API do wykonania bez ponownej kompilacji w nowszej wersji).

### <a name="types"></a>Types

- **✔️ usuwania implementacji interfejsu z typu, gdy interfejs jest już zaimplementowany przez typ podstawowy**

- **❓ Dodawanie nowej implementacji interfejsu do typu**

  Jest to akceptowalna zmiana, ponieważ nie ma negatywnego wpływu na istniejących klientów. Wszelkie zmiany w typie muszą działać w granicach akceptowalnych zmian zdefiniowanych w tym miejscu dla nowej implementacji, która pozostanie akceptowalna. Należy zachować szczególną ostrożność przy dodawaniu interfejsów, które bezpośrednio wpływają na zdolność projektanta lub serializatorów do generowania kodu lub danych, których nie można użyć na poziomie niskiego poziomu. Przykładem jest <xref:System.Runtime.Serialization.ISerializable> interfejs.

- **❓ Wprowadzenie nowej klasy bazowej**

  Typ może być wprowadzany do hierarchii między dwoma istniejącymi typami, jeśli nie wprowadza żadnych nowych [abstrakcyjnych](../../csharp/language-reference/keywords/abstract.md) elementów członkowskich lub zmiany semantyki lub zachowania istniejących typów. Na przykład w .NET Framework 2,0, <xref:System.Data.Common.DbConnection> Klasa stał się nową klasą bazową dla <xref:System.Data.SqlClient.SqlConnection>, która wcześniej <xref:System.ComponentModel.Component>była bezpośrednio pochodną.

- **✔️ przeniesienie typu z jednego zestawu do innego**

  Należy zauważyć, że *stary* zestaw musi być oznaczony jako <xref:System.Runtime.CompilerServices.TypeForwardedToAttribute> wskazujący nowy zestaw.

- **✔️ zmienić typu [struktury](../../csharp/language-reference/keywords/struct.md) na `readonly struct` typ**

  Należy zauważyć, że `readonly struct` zmiana typu `struct` na typ jest niedozwolona.
  
- **✔️ dodawania [zapieczętowanego](../../csharp/language-reference/keywords/sealed.md) lub [abstrakcyjnego](../../csharp/language-reference/keywords/abstract.md) słowa kluczowego do typu, gdy nie ma *dostępnych* (publicznych lub chronionych) konstruktorów**

- **✔️ Rozszerzanie widoczności typu**

- **❌ Zmienić przestrzeni nazw lub nazwy typu**

- **❌ Zmienianie nazwy lub usuwanie typu publicznego**

   Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego typu.

- **❌ Zmienianie typu podstawowego wyliczenia**

   Jest to niezależna od czasu kompilowania i zachowania zmiana, a także zmiana podziału binarnego, która może sprawiać, że argumenty atrybutów nie są przewidziane do przeanalizowania.

- **❌ Opieczętowanie typu, który był wcześniej niezapieczętowany**

- **❌ Dodawania interfejsu do zestawu typów podstawowych interfejsu**

   Jeśli interfejs implementuje interfejs, który wcześniej nie został zaimplementowany, wszystkie typy, które implementują oryginalną wersję interfejsu, są uszkodzone.

- **❓ Usunięcie klasy z zestawu klas bazowych lub interfejsu z zestawu zaimplementowanych interfejsów**

  Istnieje jeden wyjątek dla reguły usuwania interfejsu: można dodać implementację interfejsu, która pochodzi od usuniętego interfejsu. Można na przykład usunąć <xref:System.IDisposable> , czy typ lub interfejs implementuje <xref:System.ComponentModel.IComponent>teraz, który implementuje <xref:System.IDisposable>.

- **❌ Zmienić `readonly struct` typu na typ [struktury](../../csharp/language-reference/keywords/struct.md)**

  Należy zauważyć, że zmiana `struct` typu `readonly struct` na typ jest dozwolona.

- **❌ Zmienić typu [struktury](../../csharp/language-reference/keywords/struct.md) na `ref struct` typ i na odwrót**

- **❌ Zmniejszania widoczności typu**

   Jednak zwiększenie widoczności typu jest dozwolone.

### <a name="members"></a>Elementy członkowskie

- **✔️ Rozszerzanie widoczności elementu członkowskiego, który nie jest [wirtualny](../../csharp/language-reference/keywords/sealed.md)**

- **✔️ dodawania abstrakcyjnej składowej do typu publicznego, który ma *niedostępne* (publiczne lub chronione) konstruktory lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md)**

  Jednak dodanie abstrakcyjnej składowej do typu, który ma dostępne (publiczne lub chronione) konstruktorów, i `sealed` nie jest dozwolone.

- **✔️ Ograniczanie widoczności chronionego elementu [](../../csharp/language-reference/keywords/protected.md) Członkowskiego, gdy typ nie ma dostępnych (publicznych lub chronionych) konstruktorów lub typ jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md)**

- **✔️ przeniesienie elementu członkowskiego do klasy wyższej w hierarchii niż typ, z którego został usunięty**

- **✔️ Dodawanie lub usuwanie przesłonięcia**

  Należy pamiętać, że wprowadzenie przesłonięcia może spowodować, że poprzedni odbiorcy pominięcia przesłonięcia podczas wywoływania [podstawy](../../csharp/language-reference/keywords/base.md).

- **✔️ dodać konstruktora do klasy wraz z domyślnym konstruktorem (bez parametrów), jeśli Klasa nie miała wcześniej konstruktorów**

   Jednak dodanie konstruktora do klasy, która wcześniej nie miała konstruktorów *bez* dodawania konstruktora bezparametrowego, nie jest dozwolone.

- **✔️ zmienić elementu członkowskiego [](../../csharp/language-reference/keywords/abstract.md) z abstrakcyjnego na [wirtualny](../../csharp/language-reference/keywords/virtual.md)**

- **✔️ zmienić z `ref readonly` `ref` na wartość zwracaną (z wyjątkiem metod wirtualnych lub interfejsów)**

- **✔️ Usuwanie elementu [ReadOnly](../../csharp/language-reference/keywords/readonly.md) z pola, chyba że typ statyczny pola jest modyfikowalnym typem wartości**

- **✔️ Wywoływanie nowego zdarzenia, które nie zostało wcześniej zdefiniowane**

- **❓ Dodać nowego pola wystąpienia do typu**

   Ta zmiana wpływa na serializację.

- **❌ Zmienianie nazwy lub usuwanie publicznego elementu członkowskiego lub parametru**

   Spowoduje to przerwanie całego kodu, który używa nazwy lub usuniętego elementu członkowskiego lub parametru.

   Należy zauważyć, że obejmuje to usunięcie lub zmianę nazwy metody pobierającej lub setter z właściwości, a także zmianę nazwy lub usunięcie elementów członkowskich wyliczenia.

- **❌ Dodawanie elementu członkowskiego do interfejsu**

- **❌ Zmienić wartości stałej publicznej lub składowej wyliczenia**

- **❌ Zmienić typu właściwości, pola, parametru lub wartości zwracanej**

- **❌ Dodawania, usuwania lub zmiany kolejności parametrów**

- **❌ Dodawanie lub usuwanie słowa kluczowego [in](../../csharp/language-reference/keywords/in.md), [out](../../csharp/language-reference/keywords/out.md) lub [ref](../../csharp/language-reference/keywords/ref.md) z parametru**

- **❌ Zmianę nazwy parametru (w tym zmiana jego wielkości liter)**

  Jest to uważane za rozdzielenie z dwóch powodów:
  
  - Dzieli scenariusze z późnym wiązaniem, takie jak funkcja późnego wiązania [](../../csharp/language-reference/keywords/dynamic.md) w Visual Basic C#i dynamiczna w.
  
  - Jest ona podzielona na [zgodność źródłową](categories.md#source-compatibility) , gdy deweloperzy używają [nazwanych argumentów](../../csharp/programming-guide/classes-and-structs/named-and-optional-arguments.md#named-arguments).

- **❌ Zmiany z `ref` wartości zwracanej `ref readonly` na wartość zwracaną**

- **❌️ zmiany z `ref readonly` `ref` do wartości zwracanej w wirtualnej metodzie lub interfejsie**

- **❌ Dodawanie lub usuwanie [abstrakcyjnej](../../csharp/language-reference/keywords/abstract.md) z elementu członkowskiego**

- **❌ Usunięcie słowa kluczowego [Virtual](../../csharp/language-reference/keywords/virtual.md) z elementu członkowskiego**

  Chociaż często nie jest to istotna zmiana, C# ponieważ kompilator zamierza emitować instrukcje języka pośredniego (IL) elementu [callvirt](<xref:System.Reflection.Emit.OpCodes.Callvirt>) do wywoływania metod niewirtualnych (`callvirt` wykonuje sprawdzanie wartości null, podczas gdy normalne wywołanie nie jest), to zachowanie nie jest Niezmienna z kilku powodów:
  - C#nie jest jedynym językiem, który jest obiektem docelowym platformy .NET.
  
  - C# Kompilator coraz bardziej próbuje zoptymalizować `callvirt` do normalnego wywołania, gdy metoda docelowa nie jest wirtualna i prawdopodobnie nie ma wartości null (na przykład do metody dostępnej za pomocą [operatora propagacji?. null](../../csharp/language-reference/operators/member-access-operators.md#null-conditional-operators--and-)).
  
  Zastosowanie metody wirtualnej oznacza, że kod konsumenta często kończy wywoływanie go niepraktycznie.

- **❌ Dodawania słowa kluczowego [Virtual](../../csharp/language-reference/keywords/virtual.md) do elementu członkowskiego**

- **❌ Tworzenia abstrakcyjnej składowej wirtualnego**

  [Wirtualny element członkowski](../../csharp/language-reference/keywords/virtual.md) zawiera implementację metody, która *może zostać* zastąpiona przez klasę pochodną. [Abstrakcyjny element członkowski](../../csharp/language-reference/keywords/abstract.md) nie zawiera implementacji i *musi zostać* zastąpiony.

- **❌ Dodawania abstrakcyjnej składowej do typu publicznego, który ma dostępne (publiczne lub chronione) konstruktory, które nie są [zapieczętowane](../../csharp/language-reference/keywords/sealed.md)**

- **❌ Dodawanie lub usuwanie [statycznego](../../csharp/language-reference/keywords/static.md) słowa kluczowego z elementu członkowskiego**

- **❌ Dodawania przeciążenia, które wyklucza istniejące Przeciążenie i definiuje inne zachowanie**

  Spowoduje to przerwanie istniejących klientów, które zostały powiązane z poprzednim przeciążeniem. Na przykład jeśli klasa ma jedną wersję metody, która akceptuje <xref:System.UInt32>, istniejący Klient pomyślnie powiąże się z tym przeciążeniem podczas <xref:System.Int32> przekazywania wartości. Jeśli jednak zostanie dodane Przeciążenie, które akceptuje <xref:System.Int32>, podczas ponownej kompilacji lub użycia późnego wiązania, kompilator tworzy teraz powiązanie z nowym przeciążeniem. W przypadku innych wyników zachowania jest to istotna zmiana.

- **❌ Dodać konstruktora do klasy, która wcześniej nie miała konstruktora bez dodawania konstruktora bezparametrowego**

- **❌️ Dodawanie elementu [ReadOnly](../../csharp/language-reference/keywords/readonly.md) do pola**

- **❌ Zmniejszania widoczności elementu członkowskiego**

   Obejmuje to zmniejszenie widoczności chronionego elementu [](../../csharp/language-reference/keywords/protected.md) Członkowskiego, gdy są *dostępne* (publiczne lub chronione) konstruktory, a typ *nie* jest [zapieczętowany](../../csharp/language-reference/keywords/sealed.md). Jeśli tak się nie dzieje, zmniejszenie widoczności chronionego elementu członkowskiego jest dozwolone.

   Należy zauważyć, że zwiększenie widoczności składowej jest dozwolone.

- **❌ Zmienić typu elementu członkowskiego**

   Nie można zmodyfikować wartości zwracanej przez metodę lub typ właściwości lub pola. Na przykład sygnatura metody zwracającej wartość <xref:System.Object> nie może zostać zmieniona w celu <xref:System.String>zwrócenia lub odwrotnie.

- **❌ Dodawanie pola do struktury, która wcześniej nie miała stanu**

  Określone reguły przypisywania umożliwiają użycie niezainicjowanych zmiennych, tak długo, jak typ zmiennej jest strukturą bezstanową. Jeśli struktura jest stanowa, kod może kończyć się zainicjowanymi danymi. Może to być zarówno uszkodzenie źródła, jak i uszkodzenie binarne.

- **❌ Wyzwalanie istniejącego zdarzenia, gdy wcześniej nie zostało ono wyzwolone**

## <a name="behavioral-changes"></a>Zmiany behawioralne

### <a name="assemblies"></a>Zestawy

- **✔️ tworzenia zestawu przenośnego, gdy te same platformy są nadal obsługiwane**

- **❌ Zmienić nazwy zestawu**
- **❌ Zmienić klucza publicznego zestawu**

### <a name="properties-fields-parameters-and-return-values"></a>Właściwości, pola, parametry i wartości zwracane

- **✔️ zmiany wartości właściwości, pola, wartości zwracanej lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md) na bardziej pochodny typ**

  Na przykład Metoda zwracająca typ <xref:System.Object> może <xref:System.String> zwracać wystąpienie. Nie można jednak zmienić sygnatury metody.)

- **✔️ zwiększenie zakresu akceptowanych wartości dla właściwości lub parametru, jeśli element członkowski nie jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**

  Należy zauważyć, że podczas gdy zakres wartości, które mogą być przesyłane do metody lub są zwracane przez element członkowski, można rozwinąć, parametr lub typ elementu członkowskiego nie mogą. Na przykład, podczas gdy wartości przekazaną do metody można rozszerzyć od 0-124 do 0-255, typ parametru nie może zmienić <xref:System.Byte> z <xref:System.Int32>na.

- **❌ Zwiększenie zakresu akceptowanych wartości właściwości lub parametru, jeśli element członkowski jest [wirtualny](../../csharp/language-reference/keywords/virtual.md)**

   Ta zmiana powoduje przerwanie istniejących przesłoniętych elementów członkowskich, które nie będą działać poprawnie dla rozszerzonego zakresu wartości.

- **❌ Zmniejszania zakresu akceptowanych wartości dla właściwości lub parametru**

- **❌ Zwiększyć zakres wartości zwracanych dla właściwości, pola, wartości zwracanej lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**

- **❌ Zmienić zwracanych wartości dla właściwości, pola, wartości zwracanej metody lub parametru [out](../../csharp/language-reference/keywords/out-parameter-modifier.md)**

- **❌ Zmiany wartości domyślnej właściwości, pola lub parametru**

- **❌ Zmiany dokładności liczbowej zwracanej wartości**

- **❓ Zmianę podczas analizowania danych wejściowych i zgłaszających nowe wyjątki (nawet jeśli nie określono zachowania analizy w dokumentacji**

### <a name="exceptions"></a>Wyjątki

- **✔️ Zgłaszanie bardziej pochodnego wyjątku niż istniejący wyjątek**

  Ponieważ nowy wyjątek jest podklasą istniejącego wyjątku, poprzedni kod obsługi wyjątków nadal obsłużył wyjątek. Na przykład w .NET Framework 4, metody tworzenia i pobierania kultur zaczęły zgłosić <xref:System.Globalization.CultureNotFoundException> zamiast <xref:System.ArgumentException> elementu, jeśli nie można znaleźć kultury. Ponieważ <xref:System.Globalization.CultureNotFoundException> pochodzi od <xref:System.ArgumentException>, jest to akceptowalna zmiana.

- **✔️ zgłaszania bardziej szczegółowego wyjątku <xref:System.NotSupportedException>niż <xref:System.NotImplementedException>,,<xref:System.NullReferenceException>**

- **✔️ zgłaszania wyjątku, który jest uznawany za niemożliwy do odzyskania**

  Niemożliwy do odzyskania wyjątki nie powinny być przechwytywane, ale powinny być obsługiwane przez obsługę catch-all o wysokim poziomie. W związku z tym użytkownicy nie powinny mieć kodu, który przechwytuje te jawne wyjątki. Nieodwracalne wyjątki są następujące:

  - <xref:System.AccessViolationException>
  - <xref:System.ExecutionEngineException>
  - <xref:System.Runtime.InteropServices.SEHException>
  - <xref:System.StackOverflowException>

- **✔️ Zgłaszanie nowego wyjątku w nowej ścieżce kodu**

  Wyjątek musi dotyczyć tylko nowej ścieżki kodu, która jest wykonywana przy użyciu nowych wartości parametrów lub stanu, i które nie mogą być wykonywane przez istniejący kod, który jest przeznaczony dla poprzedniej wersji.

- **✔️ usunąć wyjątek, aby umożliwić bardziej niezawodne zachowanie lub nowe scenariusze**

  Na przykład `Divide` Metoda, która wcześniej obsługiwała tylko wartości dodatnie i <xref:System.ArgumentOutOfRangeException> zgłosiła w przeciwnym razie, może zostać zmieniona, aby obsługiwała wartości ujemne i dodatnie bez zgłaszania wyjątku.

- **✔️ zmienić tekstu komunikatu o błędzie**

  Deweloperzy nie powinni polegać na tekście komunikatów o błędach, które również zmieniają się w zależności od kultury użytkownika.

- **❌ Zgłaszanie wyjątku w innym przypadku niewymienionym powyżej**

- **❌ Usunąć wyjątek w każdym innym przypadku niewymienionym powyżej**

### <a name="attributes"></a>Atrybuty

- **✔️ zmienić wartości atrybutu, który *nie* jest zauważalny**

- **❌ Zmienić wartości atrybutu, który *jest* zauważalny**

- **❓ Usunąć atrybutu**

  W większości przypadków usunięcie atrybutu (na przykład <xref:System.NonSerializedAttribute>) jest istotną zmianą.

## <a name="platform-support"></a>Obsługa platform

- **✔️ Obsługa operacji na platformie, która była wcześniej nieobsługiwana**

- **❌ Nie obsługiwać lub obecnie wymaganego dodatku Service Pack dla operacji, która była wcześniej obsługiwana na platformie**

## <a name="internal-implementation-changes"></a>Wewnętrzne zmiany implementacji

- **❓ Zmienić obszaru powierzchni typu wewnętrznego**

   Takie zmiany są zwykle dozwolone, chociaż przerywają odbicie prywatne. W niektórych przypadkach, gdy popularne biblioteki innych firm lub duża liczba deweloperów zależą od wewnętrznych interfejsów API, takie zmiany mogą nie być dozwolone.

- **❓ Zmiana wewnętrznej implementacji elementu członkowskiego**

  Te zmiany są ogólnie dozwolone, chociaż przerywają odbicie prywatne. W niektórych przypadkach, gdzie kod klienta często zależy od odbicia prywatnego lub gdzie zmiana wprowadza niezamierzone efekty uboczne, te zmiany mogą być niedozwolone.

- **✔️ poprawy wydajności operacji**

   Możliwość modyfikowania wydajności operacji jest istotna, ale takie zmiany mogą spowodować przerwanie kodu, który opiera się na bieżącej szybkości operacji. Jest to szczególnie prawdziwe w przypadku kodu, który zależy od chronometrażu operacji asynchronicznych. Należy zauważyć, że zmiana wydajności nie powinna mieć wpływu na inne zachowanie interfejsu API. w przeciwnym razie zmiana zostanie przerwana.

- **✔️ pośrednio (i często nieszkodliwe) zmiana wydajności operacji**

  Jeśli dana zmiana nie zostanie skategoryzowana z innego powodu, jest to dopuszczalne. Często należy podjąć działania, które mogą obejmować dodatkowe operacje lub dodając nowe funkcje. Prawie zawsze ma to wpływ na wydajność, ale może być konieczne, aby interfejs API działał w oczekiwany sposób.

- **❌ Zmiany synchronicznego interfejsu API na asynchroniczny (i odwrotnie)**

## <a name="code-changes"></a>Zmiany kodu

- **✔️ dodawania [parametrów](../../csharp/language-reference/keywords/params.md) do parametru**

- **❌ Zmienić [struktury](../../csharp/language-reference/keywords/struct.md) na [klasę](../../csharp/language-reference/keywords/class.md) i odwrotnie**

- **❌ Dodawania słowa kluczowego [Checked](../../csharp/language-reference/keywords/virtual.md) do bloku kodu**

   Ta zmiana może spowodować, że kod, który został wcześniej <xref:System.OverflowException> wykonany w celu wygenerowania i jest nieakceptowalny.

- **❌ Usuwanie [parametrów](../../csharp/language-reference/keywords/params.md) z parametru**

- **❌ Zmienić kolejność, w której są uruchamiane zdarzenia**

  Deweloperzy mogą w rozsądny sposób oczekiwać, że wyzwalają zdarzenia w tej samej kolejności, a kod dewelopera często zależy od kolejności, w jakiej są uruchamiane zdarzenia.

- **❌ Usunąć podnoszenie poziomu zdarzenia na daną akcję**

- **❌ Zmienić liczbę wywoływanych zdarzeń**

- **❌ Dodawania <xref:System.FlagsAttribute> do typu wyliczenia**
