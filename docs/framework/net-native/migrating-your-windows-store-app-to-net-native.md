---
title: Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native
ms.date: 03/30/2017
ms.assetid: 4153aa18-6f56-4a0a-865b-d3da743a1d05
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a316cd8ed82f9833b23fe313b8f4c4903bd0a433
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33397783"
---
# <a name="migrating-your-windows-store-app-to-net-native"></a>Migrowanie aplikacji ze Sklepu Windows do architektury .NET Native
[!INCLUDE[net_native](../../../includes/net-native-md.md)] zawiera statyczny kompilacji aplikacji w Sklepie Windows lub na komputerze dewelopera. Ta różni się od kompilacji dynamicznej wykonywane dla aplikacji ze Sklepu Windows za pomocą kompilatora just-in-time (JIT) lub [Generator obrazu natywnego (Ngen.exe)](../../../docs/framework/tools/ngen-exe-native-image-generator.md) na urządzeniu. Pomimo różnic [!INCLUDE[net_native](../../../includes/net-native-md.md)] próbuje zachować zgodność z [.NET dla Sklepu Windows apps](http://msdn.microsoft.com/library/windows/apps/br230302.aspx). W większości przypadków rzeczy, które działają w aplikacjach .NET dla Sklepu Windows również współpracować z [!INCLUDE[net_native](../../../includes/net-native-md.md)].  Jednak w niektórych przypadkach może się pojawić zmiany zachowania. W tym dokumencie omówiono następujące różnice między standardowych aplikacji .NET dla Sklepu Windows i [!INCLUDE[net_native](../../../includes/net-native-md.md)] w następujących obszarach:  
  
-   [Różnice ogólne w czasie wykonywania](#Runtime)  
  
-   [Dynamiczne różnice programowania](#Dynamic)  
  
-   [Inne różnice związane z odbiciem](#Reflection)  
  
-   [Nieobsługiwane scenariusze i interfejsów API](#Unsupported)  
  
-   [Różnice w programie Visual Studio](#VS)  
  
<a name="Runtime"></a>   
## <a name="general-runtime-differences"></a>Różnice ogólne w czasie wykonywania  
  
-   Wyjątki, takich jak <xref:System.TypeLoadException>, który zgłoszony przez kompilator JIT, gdy aplikacja jest uruchamiana na wspólnej aparatu plików wykonywalnych języka (wspólnego CLR) zwykle spowodować błędy kompilacji podczas przetwarzania przez [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   Nie wywołuj <xref:System.GC.WaitForPendingFinalizers%2A?displayProperty=nameWithType> metody z wątku interfejsu użytkownika aplikacji. Może to doprowadzić do zakleszczenia w [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
-   Nie należy polegać na porządkowanie wywołania konstruktora klasy statycznej. W [!INCLUDE[net_native](../../../includes/net-native-md.md)], kolejność wywołania jest inna niż kolejność na standardowe środowisko uruchomieniowe. (Nawet w przypadku standardowego środowiska uruchomieniowego, nie należy traktować rzędu wykonywania konstruktorów statycznych klas.)  
  
-   Nieskończone pętle bez nawiązywania połączenia (na przykład `while(true);`) w którymkolwiek wątku mogą powodować aplikacji do zatrzymania. Podobnie duża lub nieskończone czeka może zwrócić aplikacji do zatrzymania.  
  
-   Niektórych cykle ogólne inicjowanie nie zgłaszają wyjątki [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Na przykład poniższy kod zgłasza <xref:System.TypeLoadException> wyjątek na standardowe środowisko CLR. W [!INCLUDE[net_native](../../../includes/net-native-md.md)], nie.  
  
     [!code-csharp[ProjectN#8](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat1.cs#8)]  
  
-   W niektórych przypadkach [!INCLUDE[net_native](../../../includes/net-native-md.md)] zapewnia różne implementacje bibliotek klas .NET Framework. Obiektu zwróconego z metody zawsze będzie implementować członków zwrócony typ. Jednak ponieważ jego implementacja zapasowego jest inny, nie można rzutować na ten sam zestaw typów, jak na innych platformach, .NET Framework. Na przykład w niektórych przypadkach nie można rzutować <xref:System.Collections.Generic.IEnumerable%601> obiektu interfejsu zwracane przez metody takie jak <xref:System.Reflection.TypeInfo.DeclaredMembers%2A?displayProperty=nameWithType> lub <xref:System.Reflection.TypeInfo.DeclaredProperties%2A?displayProperty=nameWithType> do `T[]`.  
  
-   Pamięć podręczna WinInet nie jest włączona domyślnie w aplikacjach .NET dla Sklepu Windows, ale nie znajduje się na [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Zwiększa wydajność, ale ma wpływ zestawu pracy. Nie są wymagane nie akcje projektanta.  
  
<a name="Dynamic"></a>   
## <a name="dynamic-programming-differences"></a>Dynamiczne różnice programowania  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] statycznie łączy w kodzie z programu .NET Framework, aby kod lokalnej dla aplikacji o maksymalnej wydajności. Rozmiary binarne jednak pozostają mały, całą .NET Framework nie można przełączyć. [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilatora usuwa to ograniczenie przy użyciu reduktor zależności, która usuwa odwołania do nieużywanych kodu. Jednak [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie może zachować lub generowania niektóre informacje o typie i kod tych informacji nie można wywnioskować statycznie w czasie kompilacji, ale zamiast tego jest pobierany dynamicznie w czasie wykonywania.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Włącz dynamiczne programowanie i odbicia. Jednak nie wszystkie typy mogą być oznaczane w celu odbicia, ponieważ może to być rozmiarowi wygenerowanego kodu za duży (szczególnie, ponieważ jest obsługiwana w czasie wykonywania odbicia w publicznych interfejsach API w programie .NET Framework). [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilatora sprawia, że inteligentne wybory dotyczące typów powinna obsługiwać odbicia, a zachowuje metadane i generuje kod tylko w przypadku tych typów.  
  
 Powiązanie danych wymaga na przykład aplikacja może mieć możliwość mapowania nazw właściwości do funkcji. Środowisko uruchomieniowe języka wspólnego .NET dla aplikacji ze Sklepu Windows, jest automatycznie używa odbicia mieli tej możliwości typy zarządzane i publicznie dostępnych typów natywnych. W [!INCLUDE[net_native](../../../includes/net-native-md.md)], kompilator automatycznie uwzględnia metadanych dla typów, do których powiązania danych.  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] Kompilatora może obsługiwać również często używanych typów ogólnych, takich jak <xref:System.Collections.Generic.List%601> i <xref:System.Collections.Generic.Dictionary%602>, która pracy bez żadnych wskazówek dotyczących serwerów lub dyrektywy. [Dynamiczne](~/docs/csharp/language-reference/keywords/dynamic.md) — słowo kluczowe jest również obsługiwany w ramach pewnych ograniczeń.  
  
> [!NOTE]
>  Należy przetestować wszystkie ścieżki kodu dynamiczne dokładnie podczas przenoszenia aplikacji [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 Konfigurację domyślną dla [!INCLUDE[net_native](../../../includes/net-native-md.md)] jest wystarczająca dla większość deweloperów, ale niektórzy deweloperzy mogą chcieć dokładnej strojenia ich konfiguracji przy użyciu dyrektyw środowiska uruchomieniowego (. rd.xml) pliku. Ponadto, w niektórych przypadkach [!INCLUDE[net_native](../../../includes/net-native-md.md)] kompilatora jest nie można ustalić metadanych, które muszą być dostępne w celu odbicia i zależy od wskazówek, szczególnie w następujących przypadkach:  
  
-   Niektóre konstrukcje, takich jak <xref:System.Type.MakeGenericType%2A?displayProperty=nameWithType> i <xref:System.Reflection.MethodInfo.MakeGenericMethod%2A?displayProperty=nameWithType> nie można ustalić statycznie.  
  
-   Kompilator nie może ustalić wystąpień, typu ogólnego, który chcesz uwzględnić musi być określony przez dyrektyw środowiska uruchomieniowego. To nie jest tak, ponieważ cały kod musi być uwzględniony, ale ponieważ odbicia na typach ogólnych utworzenia nieskończone cyklu (na przykład po wywołaniu metody rodzajowej w ramach typu ogólnego).  
  
> [!NOTE]
>  Dyrektyw środowiska uruchomieniowego są definiowane w dyrektyw środowiska uruchomieniowego (. rd.xml) pliku. Aby uzyskać ogólne informacje o korzystaniu z tego pliku, zobacz [wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md). Aby uzyskać informacje na temat dyrektyw środowiska uruchomieniowego, zobacz [dyrektyw środowiska uruchomieniowego (rd.xml) odwołanie do pliku konfiguracji](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md).  
  
 [!INCLUDE[net_native](../../../includes/net-native-md.md)] zawiera również narzędzia, które pomagają ustalić, jakie typy poza domyślny zestaw powinien obsługiwać odbicia dewelopera profilowania.  
  
<a name="Reflection"></a>   
## <a name="other-reflection-related-differences"></a>Inne różnice związane z odbiciem  
 Liczba innych poszczególnych związanych z odbiciem różnice w zachowaniu między aplikacji .NET dla Sklepu Windows i [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 W [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
-   Odbicie prywatnej przez typy i składniki w bibliotece klas programu .NET Framework nie jest obsługiwana. Można jednak uwzględnić, za pośrednictwem własnych prywatnych typów i członków, jak również typy i składniki w bibliotekach innych firm.  
  
-   <xref:System.Reflection.ParameterInfo.HasDefaultValue%2A?displayProperty=nameWithType> Właściwość poprawnie zwraca `false` dla <xref:System.Reflection.ParameterInfo> obiekt, który reprezentuje zwracaną wartość. W aplikacjach .NET dla Sklepu Windows zwraca `true`. Język pośredni (IL) nie obsługuje tej bezpośrednio i pozostanie interpretacji języka.  
  
-   Publiczne elementy członkowskie na <xref:System.RuntimeFieldHandle> i <xref:System.RuntimeMethodHandle> struktur nie są obsługiwane. Te typy są obsługiwane tylko w przypadku LINQ, drzew wyrażeń i Inicjowanie statyczne tablicy.  
  
-   <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeProperties%2A?displayProperty=nameWithType> i <xref:System.Reflection.RuntimeReflectionExtensions.GetRuntimeEvents%2A?displayProperty=nameWithType> obejmują ukrytych elementów członkowskich w klasach podstawowych i w związku z tym mogą być zastępowane bez jawnego przesłonięcia. Dotyczy to również innych [RuntimeReflectionExtensions.GetRuntime*](http://msdn.microsoft.com/library/system.reflection.runtimereflectionextensions_methods.aspx) metody.  
  
-   <xref:System.Type.MakeArrayType%2A?displayProperty=nameWithType> i <xref:System.Type.MakeByRefType%2A?displayProperty=nameWithType> nie zakończyć się niepowodzeniem podczas próby utworzenia niektórych kombinacji (na przykład tablicę ByRef).  
  
-   Odbicie nie można użyć do wywołania elementów członkowskich, które mają parametry wskaźnika.  
  
-   Za pomocą odbicia nie można pobrać lub ustawić pole wskaźnika.  
  
-   Jeśli liczba argumentów jest nieprawidłowa i typ jednego z argumentów jest nieprawidłowa, [!INCLUDE[net_native](../../../includes/net-native-md.md)] zgłasza <xref:System.ArgumentException> zamiast <xref:System.Reflection.TargetParameterCountException>.  
  
-   Ogólnie rzecz biorąc serializacji binarnej wyjątków nie jest obsługiwana. W związku z tym nie można serializować obiektów mogą być dodawane do <xref:System.Exception.Data%2A?displayProperty=nameWithType> słownika.  
  
<a name="Unsupported"></a>   
## <a name="unsupported-scenarios-and-apis"></a>Nieobsługiwane scenariusze i interfejsów API  
 W poniższych sekcjach wymieniono nieobsługiwane scenariusze i interfejsy API umożliwiające tworzenie ogólne, współdziałanie i technologii, takich jak HTTPClient i Windows Communication Foundation (WCF):  
  
-   [Programowanie ogólne](#General)  
  
-   [HttpClient](#HttpClient)  
  
-   [Współdziałanie](#Interop)  
  
-   [Nieobsługiwany interfejsów API](#APIs)  
  
<a name="General"></a>   
### <a name="general-development-differences"></a>Programowanie Ogólne różnice  
 **Typy wartości**  
  
-   Jeśli można zastąpić <xref:System.ValueType.Equals%2A?displayProperty=nameWithType> i <xref:System.ValueType.GetHashCode%2A?displayProperty=nameWithType> metody dla typu wartości nie mogą wywoływać implementacji klasy podstawowej. W aplikacjach .NET dla Sklepu Windows metody te zależą od odbicia. W czasie kompilacji [!INCLUDE[net_native](../../../includes/net-native-md.md)] generuje implementację, która nie działają na podstawie czasu wykonywania odbicia. Oznacza to, że jeśli nie można zastąpić te dwie metody, będą one działać zgodnie z oczekiwaniami, ponieważ [!INCLUDE[net_native](../../../includes/net-native-md.md)] generuje implementacji w czasie kompilacji. Jednak zastępowanie tych metod, ale wywołanie implementacji klasy podstawowej powoduje wygenerowanie wyjątku.  
  
-   Typy wartości jest większy niż 1 megabajt nie są obsługiwane.  
  
-   Typy wartości nie może mieć konstruktora domyślnego w [!INCLUDE[net_native](../../../includes/net-native-md.md)]. (C# i Visual Basic uniemożliwiają domyślnych konstruktorów w typach wartości. Jednak można je utworzyć w IL.)  
  
 **Tablice**  
  
-   Tablice z dolną granicą inną niż zero nie są obsługiwane. Zazwyczaj te tablice są tworzone przez wywołanie metody <xref:System.Array.CreateInstance%28System.Type%2CSystem.Int32%5B%5D%2CSystem.Int32%5B%5D%29?displayProperty=nameWithType> przeciążenia.  
  
-   Dynamiczne tworzenie tablic wielowymiarowych nie jest obsługiwana. Takie tablice są zwykle tworzone przez wywołanie metody przeciążenia <xref:System.Array.CreateInstance%2A?displayProperty=nameWithType> metodę, która obejmuje `lengths` parametru lub przez wywołanie metody <xref:System.Type.MakeArrayType%28System.Int32%29?displayProperty=nameWithType> — metoda.  
  
-   Tablice wielowymiarowe, które mają co najmniej czterema wymiarami nie są obsługiwane; oznacza to, że ich <xref:System.Array.Rank%2A?displayProperty=nameWithType> wartość właściwości jest 4 lub nowszej. Użyj [Tablice nieregularne](~/docs/csharp/programming-guide/arrays/jagged-arrays.md) (tablicy tablic) zamiast tego. Na przykład `array[x,y,z]` jest nieprawidłowa, ale `array[x][y][z]` nie jest.  
  
-   Wariancja dla tablic wielowymiarowych nie jest obsługiwane i powoduje, że <xref:System.InvalidCastException> wyjątek w czasie wykonywania.  
  
 **Typy ogólne**  
  
-   Błąd kompilatora powoduje nieskończone rozwijanie typu ogólnego. Na przykład ten kod nie powiedzie się do kompilacji:  
  
     [!code-csharp[ProjectN#9](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat2.cs#9)]  
  
 **Wskaźniki**  
  
-   Tablice wskaźniki nie są obsługiwane.  
  
-   Za pomocą odbicia nie można pobrać lub ustawić pole wskaźnika.  
  
 **Serializacja**  
  
 <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.String%29> Atrybut nie jest obsługiwany. Użyj <xref:System.Runtime.Serialization.KnownTypeAttribute.%23ctor%28System.Type%29> zamiast tego atrybutu.  
  
 **Zasoby**  
  
 Użycie zlokalizowane zasoby z <xref:System.Diagnostics.Tracing.EventSource> klasy nie jest obsługiwany. <xref:System.Diagnostics.Tracing.EventSourceAttribute.LocalizationResources%2A?displayProperty=nameWithType> Właściwości nie definiuje zlokalizowanych zasobów.  
  
 **Delegaci**  
  
 `Delegate.BeginInvoke` i `Delegate.EndInvoke` nie są obsługiwane.  
  
 **Async**  
  
 Wątkowość logikę przeciążenia IAsync zadania nie jest obsługiwana.  
  
 **Różne interfejsy API**  
  
-   <xref:System.Reflection.TypeInfo.GUID%2A?displayProperty=nameWithType> Zgłasza właściwości <xref:System.PlatformNotSupportedException> wyjątek Jeśli <xref:System.Runtime.InteropServices.GuidAttribute> atrybut nie jest stosowany do typu. Identyfikator GUID jest używany głównie do obsługi modelu COM.  
  
-   <xref:System.DateTime.Parse%2A?displayProperty=nameWithType> Metody poprawnie analizuje ciągi zawierające krótkiej daty w [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Jednak nie go zachować zgodność z zmiany daty i czasu przetwarzania opisane w artykułach bazy wiedzy Microsoft Knowledge Base [KB2803771](http://support.microsoft.com/kb/2803771) i [KB2803755](http://support.microsoft.com/kb/2803755).  
  
-   <xref:System.Numerics.BigInteger.ToString%2A?displayProperty=nameWithType> `("E")` poprawnie jest zaokrąglana w [!INCLUDE[net_native](../../../includes/net-native-md.md)]. W niektórych wersjach środowiska CLR zostały obcięte ciąg wyniku zamiast zaokrąglona.  
  
<a name="HttpClient"></a>   
### <a name="httpclient-differences"></a>Różnice HttpClient  
 W [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Net.Http.HttpClientHandler> klasy wewnętrznie używa WinINet (za pośrednictwem [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) klasy) zamiast <xref:System.Net.WebRequest> i <xref:System.Net.WebResponse> klasy używane standardowe .NET dla aplikacji ze Sklepu Windows.  WinINet nie obsługuje wszystkie opcje konfiguracji <xref:System.Net.Http.HttpClientHandler> obsługuje klasy.  W efekcie:  
  
-   Niektóre właściwości możliwości na <xref:System.Net.Http.HttpClientHandler> zwracać `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], podczas gdy zwracają `true` standardowe .NET dla aplikacji ze Sklepu Windows.  
  
-   Niektóre właściwości konfiguracji `get` akcesorów zawsze zwraca wartość stałą na [!INCLUDE[net_native](../../../includes/net-native-md.md)] która jest inna niż domyślna wartość można skonfigurować w aplikacjach .NET dla Sklepu Windows.  
  
 Niektóre dodatkowe różnicach są przedstawione w poniższych podsekcjach.  
  
 **Proxy**  
  
 [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) klasa nie obsługuje konfigurowania lub zastępowania serwera proxy na podstawie danego żądania.  Oznacza to, że wszystkie żądania na [!INCLUDE[net_native](../../../includes/net-native-md.md)] za pomocą serwera proxy skonfigurowanego systemu lub żadnego serwera proxy, w zależności od wartości <xref:System.Net.Http.HttpClientHandler.UseProxy%2A?displayProperty=nameWithType> właściwości.  .NET dla aplikacji ze Sklepu Windows, serwer proxy jest zdefiniowany przez <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> właściwości.  Na [!INCLUDE[net_native](../../../includes/net-native-md.md)], ustawienie <xref:System.Net.Http.HttpClientHandler.Proxy%2A?displayProperty=nameWithType> wartość inną niż `null` zgłasza <xref:System.PlatformNotSupportedException> wyjątku.  <xref:System.Net.Http.HttpClientHandler.SupportsProxy%2A?displayProperty=nameWithType> Zwraca `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], podczas gdy zwraca `true` standardowe .NET Framework dla aplikacji ze Sklepu Windows.  
  
 **Automatyczne przekierowanie**  
  
 [HttpBaseProtocolFilter](http://msdn.microsoft.com/library/windows/apps/windows.web.http.filters.httpbaseprotocolfilter.aspx) klasy nie zezwala na maksymalną liczbę przekierowań automatycznych do skonfigurowania.  Wartość <xref:System.Net.Http.HttpClientHandler.MaxAutomaticRedirections%2A?displayProperty=nameWithType> właściwości wynosi 50 domyślnie standardowa .NET dla aplikacji ze Sklepu Windows i może być modyfikowany. Na [!INCLUDE[net_native](../../../includes/net-native-md.md)], wartość tej właściwości jest 10 i w trakcie modyfikowania go zgłasza <xref:System.PlatformNotSupportedException> wyjątku.  <xref:System.Net.Http.HttpClientHandler.SupportsRedirectConfiguration%2A?displayProperty=nameWithType> Zwraca `false` na [!INCLUDE[net_native](../../../includes/net-native-md.md)], podczas gdy zwraca `true` w aplikacjach .NET dla Sklepu Windows.  
  
 **Automatycznej dekompresji**  
  
 .NET dla Sklepu Windows apps umożliwia ustawienie <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A?displayProperty=nameWithType> właściwości <xref:System.Net.DecompressionMethods.Deflate>, <xref:System.Net.DecompressionMethods.GZip>, oba <xref:System.Net.DecompressionMethods.Deflate> i <xref:System.Net.DecompressionMethods.GZip>, lub <xref:System.Net.DecompressionMethods.None>.  [!INCLUDE[net_native](../../../includes/net-native-md.md)] obsługuje tylko <xref:System.Net.DecompressionMethods.Deflate> razem z <xref:System.Net.DecompressionMethods.GZip>, lub <xref:System.Net.DecompressionMethods.None>.  Ustawiany <xref:System.Net.Http.HttpClientHandler.AutomaticDecompression%2A> właściwości albo <xref:System.Net.DecompressionMethods.Deflate> lub <xref:System.Net.DecompressionMethods.GZip> samodzielnie dyskretnie ustawia ją na obu <xref:System.Net.DecompressionMethods.Deflate> i <xref:System.Net.DecompressionMethods.GZip>.  
  
 **Plik cookie**  
  
 Obsługa plików cookie jest wykonywane jednocześnie przez <xref:System.Net.Http.HttpClient> i WinINet.  Pliki cookie z <xref:System.Net.CookieContainer> są łączone z plików cookie w pamięci podręcznej plików cookie WinINet.  Usuwanie pliku cookie z <xref:System.Net.CookieContainer> uniemożliwia <xref:System.Net.Http.HttpClient> wysyłania plików cookie, ale jeśli plik cookie został już odebrany przez WinINet i pliki cookie nie zostały usunięte przez użytkownika, WinINet wysyła go.  Nie można programistycznie usunąć plik cookie z WinINet przy użyciu <xref:System.Net.Http.HttpClient>, <xref:System.Net.Http.HttpClientHandler>, lub <xref:System.Net.CookieContainer> interfejsu API.  Ustawienie <xref:System.Net.Http.HttpClientHandler.UseCookies%2A?displayProperty=nameWithType> właściwości `false` powoduje, że tylko <xref:System.Net.Http.HttpClient> Aby zatrzymać wysyłanie plików cookie. WinINet nadal mogą obejmować jego plików cookie w żądaniu.  
  
 **poświadczenia**  
  
 .NET dla aplikacji ze Sklepu Windows <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A?displayProperty=nameWithType> i <xref:System.Net.Http.HttpClientHandler.Credentials%2A?displayProperty=nameWithType> właściwości działają niezależnie.  Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość akceptuje dowolny obiekt, który implementuje <xref:System.Net.ICredentials> interfejsu.  W [!INCLUDE[net_native](../../../includes/net-native-md.md)], ustawienie <xref:System.Net.Http.HttpClientHandler.UseDefaultCredentials%2A> właściwości `true` powoduje, że <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość, aby stać się `null`.  Ponadto <xref:System.Net.Http.HttpClientHandler.Credentials%2A> właściwość można ustawić tylko z `null`, <xref:System.Net.CredentialCache.DefaultCredentials%2A>, lub obiekt typu <xref:System.Net.NetworkCredential>.  Przypisywanie innych <xref:System.Net.ICredentials> obiektu, jest najbardziej popularnym którego <xref:System.Net.CredentialCache>, do <xref:System.Net.Http.HttpClientHandler.Credentials%2A> zgłasza właściwości <xref:System.PlatformNotSupportedException>.  
  
 **Inne funkcje nieobsługiwane lub unconfigurable**  
  
 W [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
-   Wartość <xref:System.Net.Http.HttpClientHandler.ClientCertificateOptions%2A?displayProperty=nameWithType> właściwość jest zawsze <xref:System.Net.Http.ClientCertificateOption.Automatic>.  .NET dla aplikacji ze Sklepu Windows, wartość domyślna to <xref:System.Net.Http.ClientCertificateOption.Manual>.  
  
-   <xref:System.Net.Http.HttpClientHandler.MaxRequestContentBufferSize%2A?displayProperty=nameWithType> Właściwości nie można skonfigurować.  
  
-   <xref:System.Net.Http.HttpClientHandler.PreAuthenticate%2A?displayProperty=nameWithType> Właściwość jest zawsze `true`.  .NET dla aplikacji ze Sklepu Windows, wartość domyślna to `false`.  
  
-   `SetCookie2` Nagłówka w odpowiedzi jest ignorowana jako przestarzałe.  
  
<a name="Interop"></a>   
### <a name="interop-differences"></a>Różnice międzyoperacyjne  
 **Przestarzałe interfejsy API**  
  
 Kilka interfejsów API, rzadko używane na współdziałanie z kodem zarządzanym są przestarzałe. W przypadku użycia z [!INCLUDE[net_native](../../../includes/net-native-md.md)], te interfejsy API może zgłaszać <xref:System.NotImplementedException> lub <xref:System.PlatformNotSupportedException> wyjątku lub spowodować błąd kompilatora. .NET dla aplikacji ze Sklepu Windows te interfejsy API są oznaczone jako przestarzałe, mimo że je wywołuje generuje ostrzeżenie kompilatora, a nie wystąpi błąd kompilatora.  
  
 Przestarzałe interfejsy API dla `VARIANT` organizowanie:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.BStrWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.CurrencyWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.DispatchWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ErrorWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnknownWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VariantWrapper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.IDispatch?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.UnmanagedType.SafeArray?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.VarEnum?displayProperty=nameWithType>|  
  
 <xref:System.Runtime.InteropServices.UnmanagedType.Struct?displayProperty=nameWithType> jest obsługiwana, ale zgłasza wyjątek w niektórych scenariuszach, na przykład gdy jest używana z [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) lub byref VARIANT.  
  
 Przestarzałe interfejsy API dla [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) obsługuje:  
  
|Typ|Element członkowski|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDispatch>|  
|<xref:System.Runtime.InteropServices.ClassInterfaceType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.ClassInterfaceType.AutoDual>|  
|<xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType>|Atrybut nie jest obsługiwany.|  
  
 Przestarzałe interfejsy API dla zdarzeń COM klasycznego:  
  
||  
|-|  
|<xref:System.Runtime.InteropServices.ComEventsHelper?displayProperty=nameWithType>|  
|<xref:System.Runtime.InteropServices.ComSourceInterfacesAttribute>|  
  
 Przestarzałe interfejsy API w <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejsu, który nie jest obsługiwany w [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
|Typ|Element członkowski|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType>|Wszystkie elementy członkowskie.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceMode?displayProperty=nameWithType>|Wszystkie elementy członkowskie.|  
|<xref:System.Runtime.InteropServices.CustomQueryInterfaceResult?displayProperty=nameWithType>|Wszystkie elementy członkowskie.|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.GetComInterfaceForObject%28System.Object%2CSystem.Type%2CSystem.Runtime.InteropServices.CustomQueryInterfaceMode%29?displayProperty=nameWithType>|  
  
 Inne nieobsługiwane funkcje międzyoperacyjnego:  
  
|Typ|Element członkowski|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.ICustomAdapter?displayProperty=nameWithType>|Wszystkie elementy członkowskie.|  
|<xref:System.Runtime.InteropServices.SafeBuffer?displayProperty=nameWithType>|Wszystkie elementy członkowskie.|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.Currency>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.VBByRefStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AnsiBStr>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.AsAny>|  
|<xref:System.Runtime.InteropServices.UnmanagedType?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.UnmanagedType.CustomMarshaler>|  
  
 Rzadko używane kierowanie interfejsów API:  
  
|Typ|Element członkowski|  
|----------|------------|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadByte%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt16%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt32%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadInt64%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.ReadIntPtr%28System.Object%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteByte%28System.Object%2CSystem.Int32%2CSystem.Byte%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt16%28System.Object%2CSystem.Int32%2CSystem.Int16%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt32%28System.Object%2CSystem.Int32%2CSystem.Int32%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteInt64%28System.Object%2CSystem.Int32%2CSystem.Int64%29>|  
|<xref:System.Runtime.InteropServices.Marshal?displayProperty=nameWithType>|<xref:System.Runtime.InteropServices.Marshal.WriteIntPtr%28System.Object%2CSystem.Int32%2CSystem.IntPtr%29>|  
  
 **Wywołanie platformy i zgodność międzyoperacyjnego modelu COM**  
  
 Wywołanie platformy większości i scenariusze międzyoperacyjnego COM nadal są obsługiwane w [!INCLUDE[net_native](../../../includes/net-native-md.md)]. W szczególności wszystkie współdziałanie z środowiska wykonawczego systemu Windows (WinRT) interfejsów API i organizowanie wszystkie wymagane przez środowisko wykonawcze systemu Windows jest obsługiwane. Obejmuje to przekazywanie obsługę:  
  
-   Tablice (w tym <xref:System.Runtime.InteropServices.UnmanagedType.ByValArray?displayProperty=nameWithType>)  
  
-   `BStr`  
  
-   Delegaty  
  
-   Ciągi (Unicode, Ansi i HSTRING)  
  
-   Struktury (`byref` i `byval`)  
  
-   Unie  
  
-   Uchwyty Win32  
  
-   Wszystkie konstrukcje WinRT  
  
-   Obsługa częściowej organizowanie typów variant. Obsługiwane są:  
  
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
  
    -   [IUnknown](http://msdn.microsoft.com/library/windows/desktop/ms680509.aspx)  
  
 Jednak [!INCLUDE[net_native](../../../includes/net-native-md.md)] nie obsługują następujące elementy:  
  
-   Przy użyciu klasycznego zdarzeń COM  
  
-   Implementowanie <xref:System.Runtime.InteropServices.ICustomQueryInterface?displayProperty=nameWithType> interfejs typu zarządzanego  
  
-   Implementowanie [IDispatch](http://msdn.microsoft.com/library/windows/apps/ms221608.aspx) interfejsu na typ zarządzany za pośrednictwem <xref:System.Runtime.InteropServices.ComDefaultInterfaceAttribute?displayProperty=nameWithType> atrybutu. Jednak należy pamiętać, że nie można wywołać obiektów COM za pomocą `IDispatch`, i nie można zaimplementować zarządzane obiektu `IDispatch`.  
  
 Za pomocą odbicia do wywołania platformy wywołania metody nie jest obsługiwany. To ograniczenie można obejść przez zawijanie wywołania metody w innej metody i zamiast tego wywołać otoka za pomocą odbicia.  
  
<a name="APIs"></a>   
### <a name="other-differences-from-net-apis-for-windows-store-apps"></a>Inne różnice z interfejsów API platformy .NET dla Sklepu Windows apps  
 Ta sekcja zawiera informacje o pozostałych interfejsów API, które nie są obsługiwane w [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Największy zbiór nieobsługiwany interfejsy API są Windows Communication Foundation (WCF) interfejsów API.  
  
 **DataAnnotations (System.ComponentModel.DataAnnotations)**  
  
 Typy w <xref:System.ComponentModel.DataAnnotations> i <xref:System.ComponentModel.DataAnnotations.Schema> przestrzeni nazw nie są obsługiwane w [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Obejmują one następujące typy, które znajdują się w aplikacji .NET dla Sklepu Windows dla systemu Windows 8:  
  
||  
|-|  
|<xref:System.ComponentModel.DataAnnotations.AssociationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ConcurrencyCheckAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.CustomValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataType?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DataTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayColumnAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.DisplayFormatAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EditableAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.EnumDataTypeAttribute>|  
|<xref:System.ComponentModel.DataAnnotations.FilterUIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.KeyAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RangeAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RegularExpressionAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.RequiredAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.StringLengthAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.TimestampAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.UIHintAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationContext?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationException?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.ValidationResult?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Validator?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:System.ComponentModel.DataAnnotations.Schema.DatabaseGeneratedOption?displayProperty=nameWithType>|  
  
 **Visual Basic**  
  
 Visual Basic nie jest obecnie obsługiwany w [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Następujące typy w <xref:Microsoft.VisualBasic> i <xref:Microsoft.VisualBasic.CompilerServices> przestrzeni nazw nie są dostępne w [!INCLUDE[net_native](../../../includes/net-native-md.md)]:  
  
||  
|-|  
|<xref:Microsoft.VisualBasic.CallType?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Constants?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.HideModuleNameAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.Strings?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Conversions?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.DesignerGeneratedAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.IncompleteInitialization?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.NewLateBinding?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ObjectFlowControl.ForLoopControl?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Operators?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionCompareAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.OptionTextAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.ProjectData?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StandardModuleAttribute?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.StaticLocalInitFlag?displayProperty=nameWithType>|  
|<xref:Microsoft.VisualBasic.CompilerServices.Utils?displayProperty=nameWithType>|  
  
 **Kontekście odbicia (przestrzeń nazw System.Reflection.Context)**  
  
 <xref:System.Reflection.Context.CustomReflectionContext?displayProperty=nameWithType> Klasy nie jest obsługiwany w [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **RTC (System.Net.Http.Rtc)**  
  
 <xref:System.Net.Http.RtcRequestFactory?displayProperty=nameWithType> Klasy nie jest obsługiwany w [!INCLUDE[net_native](../../../includes/net-native-md.md)].  
  
 **Windows Communication Foundation (WCF) (System.ServiceModel.\*)**  
  
 Typy w [przestrzeni nazw System.ServiceModel.*](http://msdn.microsoft.com/library/gg145010.aspx) nie są obsługiwane w [!INCLUDE[net_native](../../../includes/net-native-md.md)]. Te zawiera następujące typy:  
  
||  
|-|  
|<xref:System.ServiceModel.ActionNotSupportedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpMessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.BasicHttpSecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CallbackBehaviorAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.BeginOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.ChannelBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.EndOperationDelegate?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ClientBase%601.InvokeAsyncCompletedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectAbortedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationObjectFaultedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.CommunicationState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DataContractFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DnsEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.DuplexClientBase%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddress?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointAddressBuilder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EndpointNotFoundException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.EnvelopeVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ExceptionDetail?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultCode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultException%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReason?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.FaultReasonText?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpBindingBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.HttpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IClientChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ICommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IContextChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IDefaultCommunicationTimeouts?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensibleObject%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtension%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.IExtensionCollection%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InstanceContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.InvalidMessageContractException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageBodyMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageContractMemberAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeader%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageHeaderException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageParameterAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityOverTcp?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.MessageSecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetHttpMessageEncoding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.NetTcpSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContextScope?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.OperationFormatStyle?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ProtocolException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.QuotaExceededException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SecurityMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServerTooBusyException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceActivationException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceContractAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.ServiceKnownTypeAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.SpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpClientCredentialType?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TcpTransportSecurity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.TransferMode?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UnknownMessageReceivedEventArgs?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.UpnEndpointIdentity?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.XmlSerializerFormatAttribute?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressHeaderCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.AddressingVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelManagerBase?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ChannelParameterCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CommunicationObject?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CompressionFormat?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.FaultConverter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpRequestMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpResponseMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpsTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IChannelFactory%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IDuplexSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IHttpCookieContainerManager?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IInputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IMessageProperty?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IOutputSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.IRequestSessionChannel?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISession?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.ISessionChannel%601?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.LocalClientSecuritySettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.Message?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageBuffer?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoder?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncoderFactory?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageFault?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeader?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaderInfo?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageHeaders?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageProperties?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageState?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.MessageVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.RequestContext?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SecurityHeaderLayout?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpConnectionPoolSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TcpTransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.TransportSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportSettings?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WebSocketTransportUsage?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ClientCredentials?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ContractDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.DataContractSerializerOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.FaultDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IContractBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IEndpointBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.IOperationBehavior?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageBodyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageDirection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessageHeaderDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePartDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.MessagePropertyDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescription?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.OperationDescriptionCollection?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Description.ServiceEndpoint?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.ClientRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchOperation?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.DispatchRuntime?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.EndpointDispatcher?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageFormatter?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientMessageInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IClientOperationSelector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Dispatcher.IParameterInspector?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.BasicSecurityProfileVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.HttpDigestClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.MessageSecurityException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecureConversationVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityAccessDeniedException?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityPolicyVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.SecurityVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.TrustVersion?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.UserNamePasswordClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.WindowsClientCredential?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecureConversationSecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SecurityTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.SupportingTokenParameters?displayProperty=nameWithType>|  
|<xref:System.ServiceModel.Security.Tokens.UserNameSecurityTokenParameters?displayProperty=nameWithType>|  
  
### <a name="differences-in-serializers"></a>Różnice w serializatorów  
 Następujące różnice dotyczą serializacji i deserializacji z <xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer> klasy:  
  
-   W [!INCLUDE[net_native](../../../includes/net-native-md.md)], <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować lub deserializować klasy pochodnej, która ma element członkowski klasy podstawowej, której typ nie jest typu serializacji głównego. Na przykład w poniższym kodzie próby serializacji lub deserializacji `Y` powoduje wystąpienie błędu:  
  
     [!code-csharp[ProjectN#10](../../../samples/snippets/csharp/VS_Snippets_CLR/projectn/cs/compat3.cs#10)]  
  
     Typ `InnerType` nie jest znana do serializatora, ponieważ elementy członkowskie klasy podstawowej nie przechodzić podczas serializacji.  
  
-   <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer> nie można serializować klasy lub struktury, która implementuje <xref:System.Collections.Generic.IEnumerable%601> interfejsu. Na przykład następujące typy nie do serializacji lub deserializacji:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> nie powiedzie się do serializacji następującą wartość obiektu, ponieważ nie wie, dokładne typ obiektu do serializacji:  
  
  
  
-   <xref:System.Xml.Serialization.XmlSerializer> nie powiedzie się do serializacji lub deserializacji w przypadku typu serializacji obiektu <xref:System.Xml.XmlQualifiedName>.  
  
-   Wszystkie serializatorów (<xref:System.Runtime.Serialization.DataContractSerializer>, <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>, i <xref:System.Xml.Serialization.XmlSerializer>) nie można wygenerować kodu serializacji dla typu <xref:System.Xml.Linq.XElement?displayProperty=nameWithType> lub typu, który zawiera <xref:System.Xml.Linq.XElement>. Zamiast niej wyświetlane błędy w czasie kompilacji.  
  
-   Następujące konstruktory serializacji typów nie są gwarancji działać zgodnie z oczekiwaniami:  
  
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
  
-   <xref:System.Xml.Serialization.XmlSerializer> Nie można wygenerować kodu dla typu, który ma metodę z dowolnej z następujących atrybutów:  
  
    -   <xref:System.Runtime.Serialization.OnSerializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnSerializedAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializingAttribute>  
  
    -   <xref:System.Runtime.Serialization.OnDeserializedAttribute>  
  
-   <xref:System.Xml.Serialization.XmlSerializer> nie przestrzegać <xref:System.Xml.Serialization.IXmlSerializable> interfejsu niestandardowej serializacji. Jeśli masz klasy, który implementuje ten interfejs <xref:System.Xml.Serialization.XmlSerializer> uwzględnia typ zwykły stary typ obiektu (POCO) CLR i serializuje tylko właściwości publiczne.  
  
-   Serializacja zwykły <xref:System.Exception> obiektu, na przykład następujące polecenie, nie działają prawidłowo w przypadku <xref:System.Runtime.Serialization.DataContractSerializer> i <xref:System.Runtime.Serialization.Json.DataContractJsonSerializer>:  
  
  
  
<a name="VS"></a>   
## <a name="visual-studio-differences"></a>Różnice w programie Visual Studio  
 **Wyjątki i debugowania**  
  
 Jeśli używasz aplikacji skompilowanych za pomocą [!INCLUDE[net_native](../../../includes/net-native-md.md)] w debugerze, pierwszej szansy wyjątki są włączone dla następujących typów wyjątków:  
  
-   <xref:System.MemberAccessException>  
  
-   <xref:System.TypeAccessException>  
  
 **Tworzenie aplikacji**  
  
 Użyj x86 kompilacji narzędzi używanych domyślnie w programie Visual Studio. Nie zaleca się za pomocą narzędzia AMD64 MSBuild, które znajdują się w C:\Program Files (x86)\MSBuild\12.0\bin\amd64; to może spowodować problemy kompilacji.  
  
 **Profilery**  
  
-   Profiler procesora CPU w usłudze Visual Studio i języka XAML pamięci profilera nie wyświetlaj Just My-kodu poprawnie.  
  
-   Profiler pamięci XAML nie wyświetlać dokładnie danych sterty zarządzanej.  
  
-   Profiler procesora CPU nie poprawnie zidentyfikować moduły i wyświetla prefiksem nazwy funkcji.  
  
 **Projektów Biblioteka testów jednostkowych**  
  
 Włączanie [!INCLUDE[net_native](../../../includes/net-native-md.md)] na Biblioteka testów jednostkowych w Sklepie Windows aplikacji projektu nie jest obsługiwane i powoduje, że nie można utworzyć projektu.  
  
## <a name="see-also"></a>Zobacz też  
 [Wprowadzenie](../../../docs/framework/net-native/getting-started-with-net-native.md)  
 [Dokumentacja pliku konfiguracji dyrektyw środowiska uruchomieniowego (rd.xml)](../../../docs/framework/net-native/runtime-directives-rd-xml-configuration-file-reference.md)  
 [Omówienie aplikacji .NET dla Sklepu Windows](http://msdn.microsoft.com/library/windows/apps/br230302.aspx)  
 [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)
