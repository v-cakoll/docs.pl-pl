---
title: Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 126276840ee12bdba99f5ce1c164762340bb580c
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/27/2018
ms.locfileid: "50183935"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a>Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native
.NET native udostępnia statyczny kompilacji aplikacji Windows Store lub na komputerze dewelopera. To różni się od kompilacji dynamicznej wykonywane dla aplikacji Windows Store przez kompilator just-in-time (JIT) lub [Native Image Generator (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) na urządzeniu. Mimo różnic, .NET Native próbuje zachować zgodność z [.NET for Windows Store apps](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29). W większości przypadków rzeczy, które działają w aplikacjach .NET for Windows Store również działać z architekturą .NET Native.  Jednak w niektórych przypadkach mogą wystąpić zmiany zachowania. W tym dokumencie omówiono te różnice między standardowe aplikacje .NET for Windows Store i platforma .NET Native w następujących obszarach:  
  
-   [Różnice ogólne w czasie wykonywania](#Runtime)  
  
-   [Różnice programowania dynamicznego](#Dynamic)  
  
-   [Inne różnice dotyczące odbicia](#Reflection)  
  
-   [Nieobsługiwane scenariusze oraz interfejsów API](#Unsupported)  
  
-   [Różnice w programie Visual Studio](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a>Różnice ogólne w czasie wykonywania  
  
-   Wyjątki, takich jak <xref:System.TypeLoadException>, które są zgłaszane przez kompilator JIT gdy aplikacja jest uruchamiana na wspólnej aparatu plików wykonywalnych języka (wspólnego CLR) zazwyczaj powoduje błędy kompilacji podczas przetwarzania przez .NET Native.  
  
-   Nie wywołuj <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metody z wątku interfejsu użytkownika aplikacji. Może to spowodować zakleszczenie .NET Native.  
  
-   Nie należy polegać na określanie kolejności wywołania konstruktora klasy statycznej. W .NET Native kolejności wywołania różni się od kolejności dla standardowego środowiska uruchomieniowego. (Nawet w przypadku standardowego środowiska uruchomieniowego, nie należy traktować kolejności wykonywania konstruktorów w klasie statycznej.)  
  
-   Odtwarzanie w pętli nieskończonej bez nawiązywania połączenia (na przykład `while(true);`) dotyczące dowolnego wątku, mogą powodować jej zatrzymania. Podobnie czeka dużych lub nieskończonej może zwrócić jej zatrzymania.  
  
-   Niektóre ogólne inicjowanie cykle nie zgłaszają wyjątki w .NET Native. Na przykład, poniższy kod zgłasza <xref:System.TypeLoadException> wyjątku dla standardowego środowiska CLR. W .NET Native nie.  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   W niektórych przypadkach program .NET Native zapewnia różne implementacje biblioteki klas .NET Framework. Obiekt zwrócony z metody zawsze wdroży elementy członkowskie typu zwracanego. Jednak ponieważ jego implementacja zapasowy jest inny, nie może być można rzutować do tego samego zestawu typów, jak można wykonać następujące akcje na innych platformach .NET Framework. Na przykład w niektórych przypadkach nie można rzutować <xref:System.Collections.Generic.IEnumerable%601> obiektu interfejsu zwracane przez metody takie jak <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> lub <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> do `T[]`.  
  
-   Pamięci podręcznej WinInet nie jest domyślnie włączona, przy użyciu platformy .NET dla Windows Store apps, ale nie znajduje się na .NET Native. Zwiększa wydajność, ale ma skutki zestawu pracy. Dla deweloperów jest wymagana żadna akcja.  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a>Różnice programowania dynamicznego  
 .NET native statycznie łączy w kodzie z programu .NET Framework, aby kod aplikacji — lokalny, aby osiągnąć najwyższą wydajność. Rozmiary binarnego musi jednak pozostaną małe, więc całego środowiska .NET Framework nie można przełączyć. .NET Native kompilator rozpoznaje tego ograniczenia przy użyciu reduktor zależności, które powoduje usunięcie odwołań do nieużywanych kodu. Jednak .NET Native może nie obsługiwać lub generować niektóre informacje o typie i kodu, gdy te informacje nie można wywnioskować statycznie w czasie kompilacji, ale zamiast tego jest pobierany dynamicznie w czasie wykonywania.  
  
 .NET native Włącz odbicia i programowanie dynamiczne. Jednak nie wszystkie typy mogą być oznaczane w celu odbicia, ponieważ dzięki temu upewnisz się rozmiar wygenerowanego kodu zbyt duży (przede wszystkim dlatego rozważania na temat publicznych interfejsów API w programie .NET Framework jest obsługiwany). Kompilator platformy .NET Native sprawia, że opcje inteligentne, o których typy powinien obsługiwać odbicia i przechowuje metadane i generuje kod tylko dla tych typów.  
  
 Na przykład powiązanie danych wymaga aplikację, aby można było do mapowania nazw właściwości funkcji. W aplikacjach .NET for Windows Store środowisko uruchomieniowe języka wspólnego automatycznie używa odbicia do zapewnienia tej funkcji typami zarządzanymi i publicznie dostępnych typach natywnych. W .NET Native kompilator automatycznie zawiera metadanych dla typów, dla których wiązanie danych.  
  
 .NET Native kompilator może również obsługiwać powszechnie używane typy rodzajowe taką jak <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602>, które działają bez żadnych wskazówek dotyczących serwerów lub dyrektywy. [Dynamiczne](~/docs/csharp/language-reference/keywords/dynamic.md) — słowo kluczowe jest również obsługiwane w ramach określonych ograniczeń.  
  
> [!NOTE]
>  Należy dokładnie przetestuj wszystkie ścieżki kodu dynamicznej podczas przenoszenia aplikacji do platformy .NET Native.  
  
 Domyślna konfiguracja dla platformy .NET Native są wystarczające dla większości deweloperów, ale niektórzy deweloperzy chcieć szczegółowe dostosować swoje konfiguracje za pomocą dyrektywy środowiska uruchomieniowego (. rd.xml) pliku. Ponadto w niektórych przypadkach kompilator platformy .NET Native jest nie można ustalić metadanych, które muszą być dostępne dla odbicia i opiera się na wskazówek, szczególnie w następujących przypadkach:  
  
-   Niektóre konstrukcji, takich jak <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> i <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> nie może być określana statycznie.  
  
-   Ponieważ kompilator nie może określić wystąpień, typ ogólny, który ma być zastanowić się nad musi być określone przez dyrektywy środowiska uruchomieniowego. Nie jest to po prostu, ponieważ cały kod musi być uwzględniony, ale ponieważ odbicie w typach ogólnych może tworzyć nieskończoną cyklu (na przykład podczas wywoływania metody ogólnej dla typu ogólnego).  
  
> [!NOTE]
>  Dyrektywy środowiska uruchomieniowego są zdefiniowane w dyrektywy środowiska uruchomieniowego (. rd.xml) pliku. Aby uzyskać ogólne informacje dotyczące korzystania z tego pliku, zobacz [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md). Aby uzyskać informacji dotyczących dyrektyw środowiska uruchomieniowego, zobacz [dyrektywy środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 .NET native obejmuje również narzędzia pomagające deweloperów określania typów poza na wybranie domyślnego zestawu powinna obsługiwać odbicia profilowania.  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a>Inne różnice dotyczące odbicia  
 Istnieje szereg innych poszczególnych dotyczące odbicia różnice w zachowaniu między aplikacjami .NET for Windows Store i platformy .NET Native.  
  
 W architektura .NET Native:  
  
-   Prywatne odbicia przez typy i elementy członkowskie w bibliotece klas programu .NET Framework nie jest obsługiwane. Można jednak odzwierciedlają, za pośrednictwem własnych prywatnych typów i członków, a także typy i członków w bibliotek innych firm.  
  
-   <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Niepoprawnie zwraca wartość właściwości `false` dla <xref:System.Reflection.ParameterInfo> obiekt, który reprezentuje wartość zwracaną. W aplikacjach .NET for Windows Store, zwraca `true`. Języka pośredniego (IL) nie obsługuje tej bezpośrednio i interpretacji pozostanie ustawiony na język.  
  
-   Publiczne elementy członkowskie na <xref:System.RuntimeFieldHandle> i <xref:System.RuntimeMethodHandle> struktury nie są obsługiwane. Te typy są obsługiwane tylko dla programu LINQ, drzew wyrażeń i inicjowania tablicy statycznej.  
  
-   <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> i <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> Uwzględnij ukryte elementy członkowskie w klasach bazowych i dlatego może być przeciążona bez jawne przesłonięcia. Dotyczy to również innych [RuntimeReflectionExtensions.GetRuntime*](xref:System.Reflection.RuntimeReflectionExtensions) metody.  
  
-   <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> i <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> nie zakończyć się niepowodzeniem podczas próby utworzenia niektóre połączenia (na przykład tablica zkratka).  
  
-   Nie można używać odbicia do wywołania elementów członkowskich, które mają parametry wskaźnika.  
  
-   Za pomocą odbicia nie można pobrać lub ustawić pole wskaźnika.  
  
-   Gdy liczba argumentów jest nieprawidłowa, a typ jednego z argumentów jest niepoprawny, zgłasza .NET Native <xref:System.ArgumentException> zamiast <xref:System.Reflection.TargetParameterCountException>.  
  
-   Serializacja binarna wyjątków ogólnie nie jest obsługiwana. W rezultacie nie można serializować obiekty mogą być dodawane do <xref:System.Exception.Data%2A?displayProperty=nameWithType> słownika.  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a>Nieobsługiwane scenariusze oraz interfejsów API  
 W poniższych sekcjach wymieniono nieobsługiwane scenariusze oraz interfejsów API ogólne ustawienia projektowania, współdziałanie i technologii, takich jak HTTPClient i Windows Communication Foundation (WCF):  
  
-   [Ogólne ustawienia projektowania](#General)  
  
-   [HttpClient](#HttpClient)  
  
-   [Interop](#Interop)  
  
-   [Nieobsługiwana interfejsów API](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a>Ogólne ustawienia projektowania różnice  
 **Typy wartości**  
  
-   Jeśli zastąpisz <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> i <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody dla typu wartości Nie wywołuj implementacji klasy podstawowej. W aplikacjach .NET for Windows Store te metody działają na podstawie odbicia. W czasie kompilacji platformy .NET Native generuje implementację, które nie działają na podstawie odbicia środowiska uruchomieniowego. Oznacza to, że jeśli nie zastąpisz te dwie metody, będą one działać zgodnie z oczekiwaniami, ponieważ .NET Native generuje implementacji w czasie kompilacji. Jednak zastąpienie tych metod, ale wywołanie do implementacji klasy podstawowej powoduje wyjątek.  
  
-   Typy wartości jest większa niż jeden megabajt nie są obsługiwane.  
  
-   Typy wartości nie może mieć domyślnego konstruktora w .NET Native. (C# i Visual Basic ze Stanów Zjednoczonych zabraniają konstruktory domyślne dla typów wartości. Jednak można je utworzyć w IL.)  
  
 **Tablice**  
  
-   Tablice za pomocą dolnej granicy różną od zera nie są obsługiwane. Zazwyczaj te tablice są tworzone przez wywołanie <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> przeciążenia.  
  
-   Dynamiczne tworzenie tablic wielowymiarowych nie jest obsługiwane. Takie tablice są zwykle tworzone przez wywołanie przeciążenia <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metodę, która obejmuje `lengths` parametr, lub przez wywołanie <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> metody.  
  
-   Tablice wielowymiarowe, które mają co najmniej czterech wymiarów nie są obsługiwane; oznacza to, że ich <xref:System.Array.Rank%2A?displayProperty=nameWithType> wartość właściwości jest 4 lub nowszej. Użyj [nierówne tablic](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (tablicy tablic) zamiast tego. Na przykład `array[x,y,z]` jest nieprawidłowy, ale `array[x][y][z]` nie jest.  
  
-   Wariancja dla tablic wielowymiarowych nie jest obsługiwane i powoduje, że <xref:System.InvalidCastException> wyjątek w czasie wykonywania.  
  
 **Typy ogólne**  
  
-   Rozszerzenia typu ogólnego nieskończonej powoduje błąd kompilatora. Na przykład ten kod nie zostanie skompilowany:  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 **Wskaźniki**  
  
-   Tablice wskaźników typu nie są obsługiwane.  
  
-   Za pomocą odbicia nie można pobrać lub ustawić pole wskaźnika.  
  
 **Serializacja**  
  
 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Atrybut nie jest obsługiwany. Użyj <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> zamiast tego atrybutu.  
  
 **Zasoby**  
  
 Użycie zlokalizowanych zasobów za pomocą <xref:System.Diagnostics.Tracing.EventSource> klasy nie jest obsługiwane. <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Właściwości nie definiuje zlokalizowane zasoby.  
  
 **Delegaty**  
  
 `Delegate.BeginInvoke` i `Delegate.EndInvoke` nie są obsługiwane.  
  
 **Różne interfejsy API**  
  
-   <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Zgłasza właściwości <xref:System.PlatformNotSupportedException> wyjątek Jeśli <xref:System.Runtime.InteropServices.GuidAttribute> atrybut nie jest stosowany do typu. Identyfikator GUID jest używany głównie do obsługi COM.  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metoda poprawnie analizuje ciągów, które zawierają daty krótkie w .NET Native. Jednak go nie zachować zgodność z zmiany daty i czasu podczas analizowania opisane w artykułach bazy wiedzy Microsoft Knowledge Base [KB2803771](https://support.microsoft.com/kb/2803771) i [KB2803755](https://support.microsoft.com/kb/2803755).  
  
-   <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` poprawnie jest zaokrąglana w .NET Native. W niektórych wersjach środowiska CLR zostały obcięte wynikowego ciągu zamiast zaokrąglane.  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a>Różnice HttpClient  
 W .NET Native <xref:System.Net.Http.HttpClientHandler> klasa używa wewnętrznie WinINet (za pośrednictwem <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> klasy) zamiast <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy używane w standardowe aplikacje .NET for Windows Store.  WinINet nie obsługuje wszystkich opcji konfiguracji, który <xref:System.Net.Http.HttpClientHandler> klasy obsługuje.  W efekcie:  
  
-   Niektóre właściwości możliwości na <xref:System.Net.Http.HttpClientHandler> zwracają `false` na platformy .NET Native, natomiast zwracają `true` w standardowe aplikacje .NET for Windows Store.  
  
-   Niektóre właściwości konfiguracji `get` metod dostępu zawsze zwraca wartość stałą na .NET Native, która jest inna niż domyślna wartość można konfigurować w aplikacjach .NET for Windows Store.  
  
 Niektóre dodatkowe różnicami znajdują się w następujących podsekcjach.  
  
 **Proxy**  
  
 <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Klasa nie obsługuje konfigurowania lub zastępowania serwera proxy na podstawie danego żądania.  Oznacza to, że wszystkie żądania na .NET Native przy użyciu serwera proxy system skonfigurowany lub żaden serwer proxy, w zależności od wartości <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> właściwości.  W aplikacjach .NET for Windows Store, serwer proxy jest definiowany przez <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> właściwości.  W .NET Native, ustawienie <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> wartość inną niż `null` zgłasza <xref:System.PlatformNotSupportedException> wyjątku.  <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Właściwość zwraca `false` na platformy .NET Native, natomiast funkcja zwraca `true` w standardowe aplikacje programu .NET Framework dla Windows Store.  
  
 **Automatyczne przekierowania**  
  
 <xref:Windows.Web.Http.Filters.HttpBaseProtocolFilter> Klasy nie zezwala na maksymalną liczbę przekierowań automatycznych do skonfigurowania.  Wartość <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> właściwości wynosi 50, domyślnie w standardowe aplikacje .NET for Windows Store i może być modyfikowany. Na platformy .NET Native, wartość tej właściwości jest 10 i zmodyfikuj go zgłasza wyjątek w trakcie <xref:System.PlatformNotSupportedException> wyjątku.  <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Właściwość zwraca `false` na platformy .NET Native, natomiast funkcja zwraca `true` w aplikacjach .NET for Windows Store.  
  
 **Dekompresja automatyczna jest**  
  
 .NET for Windows Store apps pozwala na ustawienie <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> właściwości <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, zarówno <xref:System.Net.DecompressionMethods.Deflate> i <xref:System.Net.DecompressionMethods.GZip>, lub <xref:System.Net.DecompressionMethods.None>.  .NET native obsługuje tylko <xref:System.Net.DecompressionMethods.Deflate> wraz z <xref:System.Net.DecompressionMethods.GZip>, lub <xref:System.Net.DecompressionMethods.None>.  Ustawiany <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> właściwości albo <xref:System.Net.DecompressionMethods.Deflate> lub <xref:System.Net.DecompressionMethods.GZip> samodzielnie dyskretnie ustawia ją na wartość oba <xref:System.Net.DecompressionMethods.Deflate> i <xref:System.Net.DecompressionMethods.GZip>.  
  
 **Plik cookie**  
  
 Obsługa pliku cookie jest wykonywane jednocześnie przez <xref:System.Net.Http.HttpClient> i WinINet.  Pliki cookie z <xref:System.Net.CookieContainer> są łączone za pomocą plików cookie w pamięci podręcznej plików cookie WinINet.  Usuwanie pliku cookie z <xref:System.Net.CookieContainer> zapobiega <xref:System.Net.Http.HttpClient> wysyłanie plików cookie, ale jeśli plik cookie został już widzianych przez WinINet i pliki cookie nie zostały usunięte przez użytkownika, WinINet wysyła je.  Nie będzie już możliwe programowo usunąć plik cookie z WinINet przy użyciu <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, lub <xref:System.Net.CookieContainer> interfejsu API.  Ustawienie <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> właściwości `false` powoduje, że tylko <xref:System.Net.Http.HttpClient> Aby zatrzymać wysyłanie plików cookie. WinINet nadal mogą obejmować jego plików cookie w żądaniu.  
  
 **Poświadczenia**  
  
 W aplikacjach .NET for Windows Store <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> i <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> właściwości działać niezależnie.  Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość akceptuje dowolny obiekt, który implementuje <xref:System.Net.ICredentials> interfejsu.  W .NET Native, ustawienie <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> właściwości `true` powoduje, że <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwości `null`.  Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość można ustawić tylko do `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, lub obiekt typu <xref:System.Net.NetworkCredential>.  Przypisywanie inne <xref:System.Net.ICredentials> obiektu, najpopularniejsze z nich jest <xref:System.Net.CredentialCache>, <xref:System.Net.Http.HttpClientHandler.Credentials%2A> zgłasza właściwości <xref:System.PlatformNotSupportedException>.  
  
 **Inne funkcje nieobsługiwane lub unconfigurable**  
  
 W architektura .NET Native:  
  
-   Wartość <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> właściwość jest zawsze <xref:System.Net.Http.ClientCertificateOption.Automatic>.  W aplikacjach .NET for Windows Store, wartość domyślna to <xref:System.Net.Http.ClientCertificateOption.Manual>.  
  
-   <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Właściwość nie jest konfigurowalne.  
  
-   <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Właściwość jest zawsze `true`.  W aplikacjach .NET for Windows Store, wartość domyślna to `false`.  
  
-   `SetCookie2` Nagłówka w odpowiedzi jest ignorowana jako przestarzałe.  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a>Różnice międzyoperacyjności  
 **Przestarzałe interfejsy API**  
  
 Liczba rzadko używanych interfejsów API na potrzeby współdziałania z kodem zarządzanym są przestarzałe. W przypadku użycia z architekturą .NET Native, te interfejsy API może zgłaszać <xref:System.NotImplementedException> lub <xref:System.PlatformNotSupportedException> wyjątku lub wynik błędu kompilatora. W aplikacjach .NET for Windows Store tych interfejsów API są oznaczone jako przestarzałe, mimo, że wywołanie ich generuje ostrzeżenie kompilatora, a nie błąd kompilatora.  
  
 Przestarzałe interfejsy API dla `VARIANT` marshaling obejmują:  

- <xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>  
- <xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>
  
 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> jest obsługiwany, ale zgłasza wyjątek, w niektórych scenariuszach, na przykład gdy jest używany z [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) lub wariantów byref.  
  
 Przestarzałe interfejsy API dla [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) pomocy technicznej obejmują:  
  
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch?displayProperty=fullName>
- <xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual?displayProperty=fullName> 
- <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>  

Przestarzałe interfejsy API dla zdarzeń COM klasycznego obejmują:

- <xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>
- <xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>
  
Przestarzałe interfejsy API w <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsu, który nie jest obsługiwany w .NET Native, obejmują:  
  
- <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> (wszystkie elementy członkowskie)  
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType> (wszystkie elementy członkowskie)  
- <xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType> (wszystkie elementy członkowskie)  
- <xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=fullName>  
  
Inne nieobsługiwane funkcje międzyoperacyjności:  
  
- <xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType> (wszystkie elementy członkowskie)  
- <xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType> (wszystkie elementy członkowskie)  
- <xref:System.Runtime.InteropServices.UnmanagedType.Currency?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.AsAny?displayProperty=fullName>  
- <xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler?displayProperty=fullName>  
  
 Rzadko używane kierujące interfejsów API:  
  
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
  
 **Wywołanie platformy i zgodność międzyoperacyjnego modelu COM**  
  
 Wywołanie platformy większości i scenariuszy międzyoperacyjnego modelu COM są nadal obsługiwane w .NET Native. W szczególności wszystkich współdziałania z programem obsługi Windows (WinRT) interfejsów API i kierowanie wszystkich wymaganych dla środowiska uruchomieniowego Windows jest obsługiwane. Obejmuje to organizowanie obsługę:  
  
-   Tablice (w tym <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)  
  
-   `BStr`  
  
-   Delegaty  
  
-   Ciągi (Unicode, Ansi i HSTRING)  
  
-   Struktury (`byref` i `byval`)  
  
-   Unie  
  
-   Uchwyty Win32  
  
-   Wszystkie konstrukcje WinRT  
  
-   Częściowa Obsługa marshaling typów variant. Obsługiwane są następujące funkcje:  
  
    -   <xref:System.Boolean>  
  
    -   <xref:System.Byte>  
  
    -   <xref:System.Decimal>  
  
    -   <xref:System.Double>  
  
    -   <xref:System.Int16>  
  
    -   <xref:System.Int32>  
  
    -   <xref:System.Int64>  
  
    -   <xref:System.SByte>  
  
    -   <xref:System.Single>  
  
    -   <xref:System.UInt16>  
  
    -   <xref:System.UInt32>  
  
    -   <xref:System.UInt64>  
  
    -   `BStr`  
  
    -   [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown)  
  
 Jednak .NET Native nie obsługuje następujących działań:  
  
-   Za pomocą klasycznego zdarzenia COM  
  
-   Implementowanie <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsu na typ zarządzany  
  
-   Implementowanie [IDispatch](https://docs.microsoft.com/previous-versions/windows/desktop/api/oaidl/nn-oaidl-idispatch) interfejsu na typ zarządzany za pomocą <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atrybutu. Należy jednak zauważyć, że nie można wywołać obiektów COM za pomocą `IDispatch`, i nie może implementować zarządzany obiekt `IDispatch`.  
  
 Przy użyciu odbicia do wywołania platformy wywołania metody nie jest obsługiwane. To ograniczenie można obejść, zawijanie wywołania metody w innej metody i przy użyciu odbicia, aby zamiast tego wywołania otoki.  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Inne różnice z interfejsów API platformy .NET dla Windows Store apps  
 W tej sekcji przedstawiono pozostałych interfejsów API, które nie są obsługiwane przez .NET Native. Największy zestaw nieobsługiwany interfejsów API jest Windows Communication Foundation (WCF) interfejsów API.  
  
 **DataAnnotations (System.ComponentModel.DataAnnotations)**  
  
 Typy w <xref:System.ComponentModel.DataAnnotations> i <xref:System.ComponentModel.DataAnnotations.Schema> przestrzeni nazw nie są obsługiwane przez .NET Native. Obejmują one następujące typy, które znajdują się w aplikacjach .NET for Windows Store dla systemu Windows 8:  
  
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
  
 Visual Basic nie jest obecnie obsługiwane w .NET Native. Następujące typy w <xref:Microsoft.VisualBasic> i <xref:Microsoft.VisualBasic.CompilerServices> przestrzenie nazw są niedostępne w przypadku platformy .NET Native:  

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
  
 **Kontekstu odbicia (przestrzeń nazw System.Reflection.Context)**  
  
 <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Klasy nie jest obsługiwany w .NET Native.  
  
 **RTC (System.Net.Http.Rtc)**  
  
 <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Klasy nie jest obsługiwany w .NET Native.  
  
 **Windows Communication Foundation (WCF) (System.ServiceModel.\*)**  
  
 Typy w [przestrzenie nazw System.ServiceModel.*](xref:System.ServiceModel) nie są obsługiwane przez .NET Native. Te zawiera następujące typy:  
  
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
  
### <a name="differences-in-serializers"></a>Różnice serializatorów  
 Następujące różnice dotyczą serializacji i deserializacji za pomocą <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klasy:  
  
-   W .NET Native <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> zakończyć się niepowodzeniem do serializacji lub deserializacji klasy pochodnej, która ma składową klasy bazowej, w której typ nie jest głównego typu serializacji. Na przykład w poniższym kodzie próby serializacji lub deserializacji `Y` powoduje błąd:  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     Typ `InnerType` nie jest znana, serializator, ponieważ elementy członkowskie klasy bazowej nie są przesunięta podczas serializacji.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować klasy lub struktury, która implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Na przykład do serializacji lub deserializacji zakończona niepowodzeniem następujących typów:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> nie może serializować następującą wartość obiektu, ponieważ nie wie, dokładna typ obiektu do zserializowania:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> kończy się niepowodzeniem do serializacji lub deserializacji, jeśli typ Zserializowany obiekt <xref:System.Xml.XmlQualifiedName>.  
  
-   Wszystkie serializatory (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer>) nie można wygenerować kodu serializacji dla typu <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> lub typu, który zawiera <xref:System.Xml.Linq.XElement>. Zamiast tego są wyświetlane błędy czasu kompilacji.  
  
-   Następujące konstruktory serializacji typów nie są gwarantowane zgodnie z oczekiwaniami:  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.DataContractSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.String%2CSystem.String%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.DataContractSerializer.%23ctor%28System.Type%2CSystem.Xml.XmlDictionaryString%2CSystem.Xml.XmlDictionaryString%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Runtime.Serialization.Json.DataContractJsonSerializerSettings%29?displayProperty=nameWithType>  
  
    -   <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer.%23ctor%28System.Type%2CSystem.Collections.Generic.IEnumerable%7BSystem.Type%7D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.String%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Type%5B%5D%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlRootAttribute%29?displayProperty=nameWithType>  
  
    -   <xref:System.Xml.Serialization.XmlSerializer.%23ctor%28System.Type%2CSystem.Xml.Serialization.XmlAttributeOverrides%2CSystem.Type%5B%5D%2CSystem.Xml.Serialization.XmlRootAttribute%2CSystem.String%29?displayProperty=nameWithType>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> Nie można wygenerować kodu dla typu, który posiada metody opartego na atrybutach z dowolnymi z następujących atrybutów:  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> nie uznaje <xref:System.Xml.Serialization.IXmlSerializable> interfejsu niestandardowej serializacji. Jeśli masz klasę, która implementuje ten interfejs <xref:System.Xml.Serialization.XmlSerializer> uwzględnia typu plain stary typ obiektu (POCO) środowiska CLR i serializuje tylko właściwości publiczne.  
  
-   Serializacja zwykły <xref:System.Exception> obiektu, na przykład następujące polecenie, nie działają prawidłowo w przypadku <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a>Różnice w programie Visual Studio  
 **Wyjątki i debugowanie**  
  
 Jeśli korzystasz z aplikacji, skompilowane przy użyciu platformy .NET Native debugera, wyjątki pierwszej szansy są włączone dla następujących typów wyjątków:  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 **Tworzenie aplikacji**  
  
 Użyj x86 kompilacji narzędzia, które są stosowane domyślnie przez program Visual Studio. Nie zaleca się za pomocą narzędzia AMD64 MSBuild, które znajdują się w folderze C:\Program Files (x86)\MSBuild\12.0\bin\amd64; mogą one tworzyć problemów związanych z kompilacją.  
  
 **Profilery**  
  
-   Profiler procesora CPU w usłudze Visual Studio i Profiler pamięci XAML nie Just My-kodu są poprawnie wyświetlane.  
  
-   Profiler pamięci XAML nie są wyświetlane dokładne dane sterty zarządzanej.  
  
-   Profiler procesora CPU nie poprawnie zidentyfikować modułów i wyświetla prefiks nazwy funkcji.  
  
 **Projekty Biblioteka testów jednostkowych**  
  
 Włączenie .NET Native na Biblioteka testów jednostkowych dla projektu aplikacji Windows Store nie jest obsługiwane i powoduje, że projekt, aby kompilacja się nie powieść.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Omówienie aplikacji .NET dla Windows Store](https://docs.microsoft.com/previous-versions/windows/apps/br230302%28v=vs.140%29)  
 [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
