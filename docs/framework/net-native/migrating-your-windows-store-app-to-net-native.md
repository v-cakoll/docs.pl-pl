---
title: Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
ms.openlocfilehash: 36f9ac4647b349ff379869f3415a5fb9e55228e3
ms.sourcegitcommit: 7980a91f90ae5eca859db7e6bfa03e23e76a1a50
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/13/2020
ms.locfileid: "81241948"
---
# <a name="migrate-your-windows-store-app-to-net-native"></a>Migrowanie aplikacji ze Sklepu Windows do macierzystej platformy .NET

Program .NET Native zapewnia statyczną kompilację aplikacji w Sklepie Windows lub na komputerze dewelopera. Różni się to od kompilacji dynamicznej wykonywanej dla aplikacji ze Sklepu Windows przez kompilator just-in-time (JIT) lub [natywny generator obrazów (Ngen.exe)](../tools/ngen-exe-native-image-generator.md) na urządzeniu. Pomimo różnic program .NET Native próbuje zachować zgodność z [aplikacjami ze Sklepu Windows .NET dla aplikacji ze Sklepu Windows](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29). W przeważającej części działa również z aplikacjami .NET dla Sklepu Windows.  Jednak w niektórych przypadkach mogą wystąpić zmiany w zachowaniu. W tym dokumencie omówiono te różnice między standardową platformą .NET dla aplikacji ze Sklepu Windows a platformą .NET Native w następujących obszarach:

- [Ogólne różnice czasu wykonywania](#Runtime)

- [Dynamiczne różnice w programowaniu](#Dynamic)

- [Inne różnice związane z refleksją](#Reflection)

- [Nieobsługiwały się scenariusze i interfejsy API](#Unsupported)

- [Różnice w programie Visual Studio](#VS)

<a name="Runtime"></a>

## <a name="general-runtime-differences"></a>Ogólne różnice czasu wykonywania

- Wyjątki, takie <xref:System.TypeLoadException>jak , które są generowane przez kompilator JIT, gdy aplikacja jest uruchamiana w środowisku uruchomieniowym języka wspólnego (CLR) zazwyczaj powoduje błędy w czasie kompilacji podczas przetwarzania przez .NET Native.

- Nie wywoływaj <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metody z wątku interfejsu użytkownika aplikacji. Może to spowodować zakleszczenie na natywnym .NET.

- Nie polegaj na kolejności wywoływania konstruktora klasy statycznej. W programie .NET Native kolejność wywołania różni się od kolejności w standardowym czasie wykonywania. (Nawet w przypadku standardowego środowiska uruchomieniowego nie należy polegać na kolejności wykonywania konstruktorów klas statycznych).

- Nieskończone zapętlanie bez wywoływania (na `while(true);`przykład) w dowolnym wątku może doprowadzić aplikację do zatrzymania. Podobnie duże lub nieskończone oczekiwania mogą doprowadzić aplikację do zatrzymania.

- Niektóre ogólne cykle inicjowania nie zgłaszają wyjątków w .NET Native. Na przykład następujący kod zgłasza <xref:System.TypeLoadException> wyjątek w standardowym programie CLR. W .NET Native, nie.

  [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]

- W niektórych przypadkach .NET Native udostępnia różne implementacje bibliotek klas programu .NET Framework. Obiekt zwrócony z metody zawsze zaimplementuje elementy członkowskie zwracanego typu. Jednak ponieważ jego implementacji kopii zapasowej jest inna, może nie być w stanie oddać go do tego samego zestawu typów, jak można na innych platformach .NET Framework. Na przykład w niektórych przypadkach może nie <xref:System.Collections.Generic.IEnumerable%601> być możliwe rzutowania <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> obiektu <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> `T[]`interfejsu zwróconego metodami, takimi jak lub do .

- Pamięć podręczna WinInet nie jest domyślnie włączona w aplikacjiach ze Sklepu Windows .NET, ale jest na natywna .NET. Zwiększa to wydajność, ale ma wpływ na zestaw roboczy. Nie jest konieczne żadne działanie dewelopera.

<a name="Dynamic"></a>

## <a name="dynamic-programming-differences"></a>Dynamiczne różnice w programowaniu

.NET Natywne statycznie łącza w kodzie z .NET Framework, aby kod app-local dla maksymalnej wydajności. Jednak rozmiary binarne muszą pozostać małe, więc nie można wniesieć całego programu .NET Framework. Kompilator natywny platformy .NET rozwiązuje to ograniczenie przy użyciu reduktora zależności, który usuwa odwołania do nieużytego kodu. Jednak .NET Native może nie obsługiwać lub generować niektóre informacje o typie i kod, gdy informacje te nie można wywnioskować statycznie w czasie kompilacji, ale zamiast tego jest pobierana dynamicznie w czasie wykonywania.

Program .NET Native umożliwia odbicie i dynamiczne programowanie. Jednak nie wszystkie typy mogą być oznaczone do odbicia, ponieważ spowodowałoby to rozmiar wygenerowanego kodu zbyt duży (zwłaszcza, że odbijanie się na publicznych interfejsów API w programie .NET Framework jest obsługiwane). Kompilator natywny platformy .NET dokonuje inteligentnych wyborów dotyczących typów, które powinny obsługiwać odbicie, a także przechowuje metadane i generuje kod tylko dla tych typów.

Na przykład powiązanie danych wymaga aplikacji, aby móc mapować nazwy właściwości do funkcji. W aplikacjach .NET dla Sklepu Windows środowisko wykonawcze języka wspólnego automatycznie używa odbicia, aby zapewnić tę możliwość dla typów zarządzanych i publicznie dostępnych typów natywnych. W programie .NET Native kompilator automatycznie zawiera metadane dla typów, z którymi wiążą się dane.

Kompilator natywny platformy .NET może również <xref:System.Collections.Generic.List%601> obsługiwać powszechnie używane typy ogólne, takie jak i <xref:System.Collections.Generic.Dictionary%602>, które działają bez konieczności żadnych wskazówek lub dyrektyw. [Dynamiczne](../../csharp/language-reference/builtin-types/reference-types.md#the-dynamic-type) słowo kluczowe jest również obsługiwane w określonych granicach.

> [!NOTE]
> Należy dokładnie przetestować wszystkie ścieżki kodu dynamicznego podczas przenoszenia aplikacji do platformy .NET Native.

Domyślna konfiguracja dla platformy .NET Native jest wystarczająca dla większości deweloperów, ale niektórzy deweloperzy mogą chcieć dostosować swoje konfiguracje przy użyciu pliku dyrektyw środowiska uruchomieniowego (.rd.xml). Ponadto w niektórych przypadkach kompilator natywny platformy .NET nie może określić, które metadane muszą być dostępne do odbicia i opiera się na wskazówkach, szczególnie w następujących przypadkach:

- Niektóre konstrukcje <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> lubią i nie mogą być ustalone statycznie.

- Ponieważ kompilator nie może określić wystąpienia, typ ogólny, który chcesz odzwierciedlić, musi być określony przez dyrektywy środowiska wykonawczego. Nie jest to tylko dlatego, że cały kod musi być uwzględniony, ale ponieważ odbicie typów ogólnych może tworzyć nieskończony cykl (na przykład, gdy metoda rodzajowa jest wywoływana na typ ogólny).

> [!NOTE]
> Dyrektywy środowiska uruchomieniowego są zdefiniowane w pliku dyrektyw środowiska uruchomieniowego (.rd.xml). Aby uzyskać ogólne informacje dotyczące korzystania z tego pliku, zobacz [Wprowadzenie](getting-started-with-net-native.md). Aby uzyskać informacje na temat dyrektyw środowiska wykonawczego, zobacz [Odwołanie do plików konfiguracyjnych dyrektyw środowiska wykonawczego (rd.xml).](runtime-directives-rd-xml-configuration-file-reference.md)

Program .NET Native zawiera również narzędzia profilowania, które pomagają deweloperowi określić, które typy poza zestawem domyślnym powinny obsługiwać odbicie.

<a name="Reflection"></a>

## <a name="other-reflection-related-differences"></a>Inne różnice związane z refleksją

Istnieje wiele innych indywidualnych różnic związanych z odbiciem w zachowaniu między aplikacjami .NET dla Sklepu Windows a programem .NET Native.

W .NET native:

- Prywatne odbicie nad typami i członkami w bibliotece klas .NET Framework nie jest obsługiwane. Można jednak odzwierciedlać własne typy prywatne i członków, a także typy i elementy członkowskie w bibliotekach innych firm.

- Właściwość <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> poprawnie `false` zwraca <xref:System.Reflection.ParameterInfo> dla obiektu, który reprezentuje wartość zwracaną. W aplikacjiach .NET dla Sklepu `true`Windows zwraca program . Język pośredni (IL) nie obsługuje tego bezpośrednio, a interpretacja jest pozostawiona w języku.

- Członkowie publiczni <xref:System.RuntimeFieldHandle> <xref:System.RuntimeMethodHandle> na i struktur nie są obsługiwane. Te typy są obsługiwane tylko dla LINQ, drzewa wyrażeń i inicjowania tablic statycznych.

- <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType>i <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> dołączyć ukryte elementy członkowskie w klasach podstawowych i w związku z tym mogą być zastąpione bez jawnych zastąpienia. Dotyczy to również innych metod [RuntimeReflectionExtensions.GetRuntime*.](xref:System.Reflection.RuntimeReflectionExtensions)

- <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType>i <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> nie zawiedziej podczas próby utworzenia pewnych kombinacji (na przykład tablicy byrefs).

- Nie można użyć odbicia do wywoływania elementów członkowskich, które mają parametry wskaźnika.

- Odbicie nie można używać do uzyskania lub ustawionego pola wskaźnika.

- Gdy liczba argumentów jest nieprawidłowa, a typ jednego z argumentów <xref:System.ArgumentException> jest niepoprawny, .NET Native zgłasza zamiast <xref:System.Reflection.TargetParameterCountException>.

- Serializacja binarna wyjątków zazwyczaj nie jest obsługiwana. W rezultacie obiekty nieserwialne mogą być <xref:System.Exception.Data%2A?displayProperty=nameWithType> dodawane do słownika.

<a name="Unsupported"></a>

## <a name="unsupported-scenarios-and-apis"></a>Nieobsługiwały się scenariusze i interfejsy API

W poniższych sekcjach lista nieobsługiwane scenariusze i interfejsy API dla ogólnego rozwoju, interop i technologii, takich jak HTTPClient i Windows Communication Foundation (WCF):

- [Ogólny rozwój](#General)

- [Funkcja HttpClient](#HttpClient)

- [Interop](#Interop)

- [Nieobsługiwały interfejsy API](#APIs)

<a name="General"></a>

### <a name="general-development-differences"></a>Ogólne różnice rozwojowe

**Typy wartości**

- Jeśli zastąpisz <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> i <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody dla typu wartości, nie należy wywoływać implementacji klasy podstawowej. W aplikacji .NET dla Sklepu Windows te metody opierają się na odbiciu. W czasie kompilacji .NET Native generuje implementację, która nie opiera się na odbicie środowiska uruchomieniowego. Oznacza to, że jeśli nie zastąpisz tych dwóch metod, będą działać zgodnie z oczekiwaniami, ponieważ .NET Native generuje implementację w czasie kompilacji. Jednak zastąpienie tych metod, ale wywołanie implementacji klasy podstawowej powoduje wyjątek.

- Typy wartości większe niż jeden megabajt nie są obsługiwane.

- Typy wartości nie mogą mieć konstruktora bez parametrów w .NET Native. (C# i Visual Basic zabraniają konstruktorów bez parametrów na typach wartości. Można je jednak utworzyć w IL.)

**Tablice**

- Tablice z dolną granicą inną niż zero nie są obsługiwane. Zazwyczaj te tablice są tworzone <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> przez wywołanie przeciążenia.

- Dynamiczne tworzenie tablic wielowymiarowych nie jest obsługiwane. Takie tablice są zazwyczaj tworzone przez wywołanie przeciążenia <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metody, która zawiera `lengths` parametr lub wywołując <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metodę.

- Tablice wielowymiarowe, które mają cztery lub więcej wymiarów, nie są obsługiwane; oznacza to, <xref:System.Array.Rank%2A?displayProperty=nameWithType> że ich wartość nieruchomości wynosi cztery lub więcej. Zamiast tego należy użyć [tablic postrzępionych](../../csharp/programming-guide/arrays/jagged-arrays.md) (tablicy tablic). Na przykład `array[x,y,z]` jest nieprawidłowy, ale `array[x][y][z]` nie jest.

- Odchylenie dla tablic wielowymiarowych nie jest <xref:System.InvalidCastException> obsługiwane i powoduje wyjątek w czasie wykonywania.

**Typy ogólne**

- Nieskończone rozszerzenie typu ogólnego powoduje błąd kompilatora. Na przykład ten kod nie można skompilować:

  [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]

**Wskaźniki**

- Tablice wskaźników nie są obsługiwane.

- Odbicie nie można używać do uzyskania lub ustawionego pola wskaźnika.

**Serializacja**

Atrybut <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> nie jest obsługiwany. Zamiast <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> tego użyj atrybutu.

**Zasoby**

Użycie zlokalizowanych zasobów z <xref:System.Diagnostics.Tracing.EventSource> klasą nie jest obsługiwane. Właściwość <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> nie definiuje zlokalizowanych zasobów.

**Delegaty**

`Delegate.BeginInvoke`i `Delegate.EndInvoke` nie są obsługiwane.

**Różne interfejsy API**

- [Właściwość TypeInfo.GUID](xref:System.Type.GUID) zgłasza <xref:System.PlatformNotSupportedException> wyjątek, jeśli <xref:System.Runtime.InteropServices.GuidAttribute> atrybut nie jest stosowany do typu. Identyfikator GUID jest używany głównie do obsługi COM.

- Metoda <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> poprawnie analizuje ciągi, które zawierają krótkie daty w .NET Native. Nie utrzymuje jednak zgodności ze zmianami w analizowaniu daty i godziny opisanymi w artykułach bazy wiedzy Microsoft Knowledge Base [KB2803771](https://support.microsoft.com/kb/2803771) i [KB2803755](https://support.microsoft.com/kb/2803755).

- <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType>`("E")` jest poprawnie zaokrąglona w pliku .NET Native. W niektórych wersjach CLR ciąg wynik jest obcinany zamiast zaokrąglone.

<a name="HttpClient"></a>

### <a name="httpclient-differences"></a>Różnice w clientie http

W programie .NET <xref:System.Net.Http.HttpClientHandler> Native klasa wewnętrznie używa usługi <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> WinINet (za <xref:System.Net.WebRequest> <xref:System.Net.WebResponse> pośrednictwem klasy) zamiast klas i używanych w standardowej sieci .NET dla aplikacji ze Sklepu Windows.  WinINet nie obsługuje wszystkich opcji konfiguracji, które obsługuje <xref:System.Net.Http.HttpClientHandler> klasa.  W efekcie:

- Niektóre właściwości możliwości w <xref:System.Net.Http.HttpClientHandler> przypadku `false` zwrotu na natywnych `true` platformy .NET, podczas gdy zwracają one w standardowej sieci .NET dla aplikacji ze Sklepu Windows.

- Niektóre akcesory właściwości `get` konfiguracji zawsze zwracają stałą wartość na natywną platformy .NET, która różni się od domyślnej wartości konfigurowalnej w programie .NET dla aplikacji ze Sklepu Windows.

Niektóre dodatkowe różnice w zachowaniu są omówione w następujących podsekcjach.

**Proxy**

Klasa <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> nie obsługuje konfigurowania lub zastępowania serwera proxy na podstawie żądania.  Oznacza to, że wszystkie żądania na natywne platformy .NET używają serwera proxy <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> skonfigurowanego przez system lub nie ma serwera proxy, w zależności od wartości właściwości.  W aplikacji .NET dla Sklepu Windows serwer <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> proxy jest definiowany przez właściwość.  W programie .NET <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> Native ustawienie wartości `null` innej <xref:System.PlatformNotSupportedException> niż zgłasza wyjątek.  Właściwość <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> `false` zwraca na poziomie natywnym `true` platformy .NET, podczas gdy zwraca w standardowym programie .NET Framework dla aplikacji ze Sklepu Windows.

**Automatyczne przekierowanie**

Klasa <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> nie zezwala na skonfigurowanie maksymalnej liczby automatycznych przekierowań.  Wartość <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> właściwości jest domyślnie 50 w standardzie .NET dla aplikacji ze Sklepu Windows i mogą być modyfikowane. W programie .NET Native wartość tej właściwości wynosi 10, a <xref:System.PlatformNotSupportedException> próba zmodyfikowania zgłasza wyjątek.  Właściwość <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> `false` zwraca na natywną `true` platformę .NET, podczas gdy zwraca w programie .NET dla aplikacji ze Sklepu Windows.

**Automatyczna dekompresja**

.NET dla aplikacji ze Sklepu <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> Windows <xref:System.Net.DecompressionMethods.Deflate>umożliwia <xref:System.Net.DecompressionMethods.GZip>ustawienie <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>właściwości <xref:System.Net.DecompressionMethods.None>na , , i , lub .  Program .NET <xref:System.Net.DecompressionMethods.Deflate> Native <xref:System.Net.DecompressionMethods.GZip>obsługuje <xref:System.Net.DecompressionMethods.None>tylko razem z programem , lub .  Próba ustawienie <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> właściwości na <xref:System.Net.DecompressionMethods.Deflate> jedną <xref:System.Net.DecompressionMethods.GZip> lub samotnie po <xref:System.Net.DecompressionMethods.Deflate> <xref:System.Net.DecompressionMethods.GZip>cichu ustawia ją na obie i .

**Plik cookie**

Obsługa plików cookie jest <xref:System.Net.Http.HttpClient> wykonywana jednocześnie przez i WinINet.  Pliki cookie <xref:System.Net.CookieContainer> są łączone z plikami cookie w pamięci podręcznej plików cookie WinINet.  Usunięcie pliku cookie <xref:System.Net.CookieContainer> uniemożliwia <xref:System.Net.Http.HttpClient> wysyłanie pliku cookie, ale jeśli plik cookie był już widoczny przez WinINet, a pliki cookie nie zostały usunięte przez użytkownika, WinINet wysyła go.  Nie można programowo usunąć pliku cookie z usługi WinINet <xref:System.Net.Http.HttpClientHandler>za <xref:System.Net.CookieContainer> pomocą interfejsu <xref:System.Net.Http.HttpClient>API .  Ustawienie <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> właściwości `false` na <xref:System.Net.Http.HttpClient> powoduje, że tylko przestać wysyłać pliki cookie; WinINet może nadal zawierać swoje pliki cookie w żądaniu.

**Poświadczenia**

W aplikacjach .NET dla <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> Sklepu Windows i właściwości działają niezależnie.  Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość akceptuje dowolny obiekt, który <xref:System.Net.ICredentials> implementuje interfejs.  W .NET Native <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> ustawienie `true` właściwości <xref:System.Net.Http.HttpClientHandler.Credentials%2A> powoduje, `null`że właściwość staje się .  Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość można ustawić tylko `null` <xref:System.Net.CredentialCache.DefaultCredentials%2A>na , lub <xref:System.Net.NetworkCredential>obiekt typu .  Przypisywanie innego <xref:System.Net.ICredentials> obiektu, z których <xref:System.Net.CredentialCache>najbardziej popularne <xref:System.Net.Http.HttpClientHandler.Credentials%2A> jest , <xref:System.PlatformNotSupportedException>do właściwości rzuca .

**Inne nieobsługiwanych lub niekonfigurowalnych funkcji**

W .NET native:

- Wartość <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> właściwości jest zawsze <xref:System.Net.Http.ClientCertificateOption.Automatic>.  W programie .NET dla aplikacji <xref:System.Net.Http.ClientCertificateOption.Manual>ze Sklepu Windows wartość domyślna to .

- Właściwość <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> nie jest konfigurowalna.

- Obiekt <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> jest `true`zawsze.  W programie .NET dla aplikacji `false`ze Sklepu Windows wartość domyślna to .

- Nagłówek `SetCookie2` w odpowiedziach jest ignorowany jako przestarzały.

<a name="Interop"></a>
### <a name="interop-differences"></a>Różnice międzyoperacyjne
 **Przestarzałe interfejsy API**

 Liczba rzadko używanych interfejsów API dla współdziałania z kodem zarządzanym zostały przestarzałe. W przypadku użycia z .NET Native te <xref:System.NotImplementedException> <xref:System.PlatformNotSupportedException> interfejsy API mogą zgłaszać lub wyjątek lub spowodować błąd kompilatora. W aplikacjach .NET dla Sklepu Windows te interfejsy API są oznaczone jako przestarzałe, chociaż wywołanie ich generuje ostrzeżenie kompilatora, a nie błąd kompilatora.

 Przestarzałe interfejsy `VARIANT` API do organizowania obejmują:

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>

 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType>jest obsługiwany, ale zgłasza wyjątek w niektórych scenariuszach, takich jak gdy jest używany z [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) lub byref wariantów.

 Przestarzałe interfejsy API dla obsługi [funkcji IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) obejmują:

- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>

Przestarzałe interfejsy API dla klasycznych zdarzeń COM obejmują:

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>

Przestarzałe interfejsy <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> API w interfejsie, który nie jest obsługiwany w .NET Native, obejmują:

- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>(wszyscy członkowie)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>(wszyscy członkowie)
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>(wszyscy członkowie)
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>

Inne nieobsługiwały funkcje interop obejmują:

- <xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>(wszyscy członkowie)
- <xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>(wszyscy członkowie)
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>

 Rzadko używane kierowanie interfejsów API:

- <xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29?displayProperty=fullName>

 **Platforma wywołać i com międzyop zgodności**

 Większość scenariuszy interop platformy wywołać i COM są nadal obsługiwane w .NET Native. W szczególności wszystkie współdziałanie z interfejsami API środowiska wykonawczego systemu Windows (WinRT) i wszystkie kierowanie wymagane dla środowiska wykonawczego systemu Windows jest obsługiwane. Obejmuje to kierowanie wsparcie dla:

- Tablice (w tym) <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>

- `BStr`

- Delegaty

- Ciągi (Unicode, Ansi i HSTRING)

- Struktury (`byref` i `byval`)

- Unie

- Uchwyty Win32

- Wszystkie konstrukcje WinRT

- Częściowa obsługa typów wariantów organizowania. Obsługiwane są następujące funkcje:

  - <xref:System.Boolean>

  - <xref:System.Byte>

  - <xref:System.Decimal>

  - <xref:System.Double>

  - <xref:System.Int16>

  - <xref:System.Int32>

  - <xref:System.Int64>

  - <xref:System.SByte>

  - <xref:System.Single>

  - <xref:System.UInt16>

  - <xref:System.UInt32>

  - <xref:System.UInt64>

  - `BStr`

  - [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)

Jednak .NET Native nie obsługuje następujących czynności:

- Korzystanie z klasycznych zdarzeń COM

- Implementowanie <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsu w typie zarządzanym

- Implementowanie interfejsu [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) na typ <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> zarządzany za pomocą atrybutu. Należy jednak pamiętać, że nie można `IDispatch`wywołać obiektów COM za `IDispatch`pośrednictwem obiektu, a obiekt zarządzany nie może zaimplementować .

Za pomocą odbicia do wywołania platformy wywołać metodę nie jest obsługiwany. Można obejść to ograniczenie, zawijając wywołanie metody w innej metodzie i za pomocą odbicia, aby zamiast tego wywołać otokę.

<a name="APIs"></a>

### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Inne różnice w porównaniu z interfejsami API platformy .NET dla aplikacji ze Sklepu Windows

W tej sekcji wymieniono pozostałe interfejsy API, które nie są obsługiwane w programie .NET Native. Największy zestaw nieobsługiwał interfejsów API są interfejsy API programu Windows Communication Foundation (WCF).

**Usługi DataAnnotations (System.ComponentModel.DataAnnotations)**

Typy w <xref:System.ComponentModel.DataAnnotations> <xref:System.ComponentModel.DataAnnotations.Schema> i przestrzenie nazw nie są obsługiwane w .NET Native. Należą do nich następujące typy, które są obecne w aplikacjach ze Sklepu Windows dla systemu Windows dla systemu Windows 8:

- <xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>
- <xref:System.ComponentModel.DataAnnotations.EditableAttribute>
- <xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>
- <xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>
- <xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>

 **Visual Basic**

Visual Basic nie jest obecnie obsługiwany w programie .NET Native. Następujące typy <xref:Microsoft.VisualBasic> w <xref:Microsoft.VisualBasic.CompilerServices> obszarach i nazw nie są dostępne w obszarze natywnym platformy .NET:

- <xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>
- <xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>

**Kontekst odbicia (obszar nazw System.Reflection.Context)**

Klasa <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> nie jest obsługiwana w .NET Native.

**RTC (System.Net.http.rtc)**

Klasa `System.Net.Http.RtcRequestFactory` nie jest obsługiwana w .NET Native.

**Windows Communication Foundation (WCF) (System.ServiceModel.\*)**

Typy w [przestrzeniach nazw System.ServiceModel.*](xref:System.ServiceModel) nie są obsługiwane w obszarze .NET Native. Obejmują one następujące typy:

- <xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>
- <xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>
- <xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>
- <xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>
- <xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>
- <xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>
- <xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>
- <xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>
- <xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>
- <xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>
- <xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>
- <xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>
- <xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>
- <xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>
- <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>
- <xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>

### <a name="differences-in-serializers"></a>Różnice w serializatorach

Następujące różnice dotyczą serializacji i deserializacji z <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>i <xref:System.Xml.Serialization.XmlSerializer> klasami:

- W .NET <xref:System.Runtime.Serialization.DataContractSerializer> Native <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> i nie można serializować lub deserialize klasy pochodnej, która ma element członkowski klasy podstawowej, którego typ nie jest głównym typem serializacji. Na przykład w poniższym kodzie próba serializacji `Y` lub deserializacji powoduje błąd:

  [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]

  Typ `InnerType` nie jest znany serializatorowi, ponieważ członkowie klasy podstawowej nie są przemierzane podczas serializacji.

- <xref:System.Runtime.Serialization.DataContractSerializer>i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować klasy lub <xref:System.Collections.Generic.IEnumerable%601> struktury, która implementuje interfejs. Na przykład następujące typy nie można serializować lub deserialize:

- <xref:System.Xml.Serialization.XmlSerializer>nie można serializować następującą wartość obiektu, ponieważ nie zna dokładnego typu obiektu, który ma być serializowany:

- <xref:System.Xml.Serialization.XmlSerializer>nie powiedzie się serializacji lub deserializacji, <xref:System.Xml.XmlQualifiedName>jeśli typem obiektu serializowanego jest .

- Wszystkie serializatory<xref:System.Runtime.Serialization.DataContractSerializer> <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>( <xref:System.Xml.Serialization.XmlSerializer>, , i ) nie <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> generują kodu serializacji dla typu lub typu, który zawiera <xref:System.Xml.Linq.XElement>. Zamiast tego wyświetlają błędy czasu kompilacji.

- Następujące konstruktory typów serializacji nie są gwarantowane do pracy zgodnie z oczekiwaniami:

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29>

  - <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29>

  - <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29>

- <xref:System.Xml.Serialization.XmlSerializer>nie można wygenerować kodu dla typu, który ma metody przypisane z dowolnym z następujących atrybutów:

  - <xref:System.Runtime.Serialization.OnSerializingAttribute>

  - <xref:System.Runtime.Serialization.OnSerializedAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializingAttribute>

  - <xref:System.Runtime.Serialization.OnDeserializedAttribute>

- <xref:System.Xml.Serialization.XmlSerializer>nie honoruje <xref:System.Xml.Serialization.IXmlSerializable> niestandardowego interfejsu serializacji. Jeśli masz klasę, która implementuje <xref:System.Xml.Serialization.XmlSerializer> ten interfejs, uważa typ zwykły stary obiekt CLR (POCO) typu i serializuje tylko jego właściwości publicznych.

- Serializacja zwykłego <xref:System.Exception> obiektu nie działa <xref:System.Runtime.Serialization.DataContractSerializer> dobrze <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>i .

<a name="VS"></a>

## <a name="visual-studio-differences"></a>Różnice w programie Visual Studio

**Wyjątki i debugowanie**

Podczas uruchamiania aplikacji skompilowanych przy użyciu platformy .NET Native w debugerze wyjątki pierwszej szansy są włączone dla następujących typów wyjątków:

- <xref:System.MemberAccessException>

- <xref:System.TypeAccessException>

**Tworzenie aplikacji**

Użyj narzędzi kompilacji x86, które są domyślnie używane przez program Visual Studio. Nie zalecamy używania narzędzi AMD64 MSBuild, które znajdują się w folderze C:\Program Files (x86)\MSBuild\12.0\bin\amd64; mogą one powodować problemy z kompilacją.

**Profilowania**

- Profiler procesora CPU visual studio i profiler pamięci XAML nie są wyświetlane just-my-code poprawnie.

- Profiler pamięci XAML nie dokładnie wyświetla dane zarządzanego sterty.

- Profiler procesora CPU nie poprawnie zidentyfikować moduły i wyświetla nazwy funkcji z prefiksem.

**Projekty biblioteki testów jednostkowych**

Włączenie programu .NET native w bibliotece testów jednostkowych dla projektu aplikacji ze Sklepu Windows nie jest obsługiwane i powoduje, że projekt nie może się zbudować.

## <a name="see-also"></a>Zobacz też

- [Wprowadzenie](getting-started-with-net-native.md)
- [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](runtime-directives-rd-xml-configuration-file-reference.md)
- [.NET Dla aplikacji ze Sklepu Windows — omówienie](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)
- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
