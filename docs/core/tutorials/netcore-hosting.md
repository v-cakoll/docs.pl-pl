---
title: Pisanie niestandardowego hosta programu .NET Core
description: Dowiedz się, jak hostować program .NET Core runtime z kodu macierzystego do obsługi zaawansowanych scenariuszy, które wymagają kontrolowania, jak działa program runtime .NET Core.
author: mjrousos
ms.date: 12/21/2018
ms.openlocfilehash: 46c7873a1865db04cf1c2b1bb2ded2b5dacbcc8d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/14/2020
ms.locfileid: "78239901"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Napisz niestandardowy host .NET Core, aby sterować czasem uruchomieniowym .NET z kodu macierzystego

Podobnie jak wszystkie kodu zarządzanego, aplikacje .NET Core są wykonywane przez hosta. Host jest odpowiedzialny za uruchamianie czasu wykonywania (w tym składników, takich jak JIT i moduł zbierający elementy bezużyteczne) i wywoływanie zarządzanych punktów wejścia.

Hostowanie programu runtime .NET Core jest scenariuszem zaawansowanym i w większości przypadków deweloperzy .NET Core nie muszą się martwić o hosting, ponieważ procesy kompilacji .NET Core zapewniają domyślny host do uruchamiania aplikacji .NET Core. W pewnych specjalistycznych okolicznościach, choć może być przydatne jawnie hostować .NET Core runtime, albo jako środek wywoływania kodu zarządzanego w procesie macierzystym lub w celu uzyskania większej kontroli nad jak działa czas wykonywania.

Ten artykuł zawiera omówienie kroków niezbędnych do uruchomienia programu runtime .NET Core z kodu macierzystego i wykonania kodu zarządzanego w nim.

## <a name="prerequisites"></a>Wymagania wstępne

Ponieważ hosty są aplikacjami macierzystymi, ten samouczek obejmuje tworzenie aplikacji C++ do hostowania .NET Core. Będziesz potrzebować środowiska programistycznego Języka C++ (na przykład środowiska dostarczonego przez [program Visual Studio).](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)

Należy również utworzyć prostą aplikację .NET Core do testowania hosta, więc należy zainstalować [.NET Core SDK](https://dotnet.microsoft.com/download) i [utworzyć małą aplikację testową .NET Core](with-visual-studio.md) (na przykład aplikację "Hello World"). Wystarczy aplikacja "Hello World" utworzona przez nowy szablon projektu konsoli .NET Core.

## <a name="hosting-apis"></a>Hosting interfejsów API
Istnieją trzy różne interfejsy API, które mogą służyć do hosta .NET Core. Ten artykuł (i powiązane z nim [przykłady)](https://github.com/dotnet/samples/tree/master/core/hosting)obejmuje wszystkie opcje.

* Preferowaną metodą hostowania programu .NET Core w .NET Core 3.0 i powyżej jest interfejsy API `nethost` i `hostfxr` bibliotek. Te punkty wejścia obsługi złożoności znajdowania i konfigurowania czasu wykonywania do inicjowania i umożliwiają zarówno uruchomienie aplikacji zarządzanej i wywołanie w statycznej metody zarządzanej.
* Preferowaną metodą hostowania programu .NET Core przed .NET Core 3.0 jest interfejs API [CoreClrHost.h.](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/hosts/inc/coreclrhost.h) Ten interfejs API udostępnia funkcje łatwego uruchamiania i zatrzymywania czasu wykonywania i wywoływania kodu zarządzanego (przez uruchomienie zarządzanego exe lub wywołanie statycznych metod zarządzanych).
* .NET Core może być również `ICLRRuntimeHost4` hostowany z interfejsem w [mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h). Ten interfejs API jest już dłuższy niż CoreClrHost.h, więc być może widzieliście starsze hosty używające go. Nadal działa i pozwala nieco większą kontrolę nad procesem hostingu niż CoreClrHost. W przypadku większości scenariuszy coreclrHost.h jest teraz preferowany ze względu na prostsze interfejsy API.

## <a name="sample-hosts"></a>Przykładowe hosty

[Przykładowe hosty](https://github.com/dotnet/samples/tree/master/core/hosting) demonstrujące kroki opisane w poniższych samouczkach są dostępne w repozytorium github dotnet/samples. Komentarze w przykładach wyraźnie kojarzą ponumerowane kroki z tych samouczków z miejscem, w którym są wykonywane w przykładzie. Aby uzyskać instrukcje dotyczące pobierania, zobacz [Przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Należy pamiętać, że przykładowe hosty są przeznaczone do użycia w celach edukacyjnych, więc są lekkie podczas sprawdzania błędów i mają na celu podkreślenie czytelności nad wydajnością.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>Tworzenie hosta przy użyciu sieci NetHost.h i HostFxr.h

W poniższych krokach `nethost` opisano sposób uruchamiania `hostfxr` programu .NET Core w czasie wykonywania w aplikacji macierzystej i wywołania w zarządzanej metodzie statycznej. [W przykładzie](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) `nethost` użyto nagłówka i biblioteki zainstalowanej z [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) zestawem SDK .NET oraz kopii plików i [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) plików z repozytorium [dotnet/core-setup.](https://github.com/dotnet/core-setup)

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>Krok 1 - Załaduj HostFxr i uzyskaj eksportowane funkcje hostingu

Biblioteka `nethost` udostępnia `get_hostfxr_path` funkcję lokalizowania `hostfxr` biblioteki. Biblioteka `hostfxr` udostępnia funkcje do obsługi programu .NET Core. Pełną listę funkcji można [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) znaleźć w dokumencie [projektowym hostingu macierzystego](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md). W przykładzie i w tym samouczku są używane następujące elementy:

* `hostfxr_initialize_for_runtime_config`: Inicjuje kontekst hosta i przygotowuje się do inicjowania czasu uruchomieniowego .NET Core przy użyciu określonej konfiguracji czasu wykonywania.
* `hostfxr_get_runtime_delegate`: Pobiera pełnomocnika dla funkcji wykonywania.
* `hostfxr_close`: Zamyka kontekst hosta.

Biblioteka `hostfxr` zostanie znaleziona za pomocą programu `get_hostfxr_path`. Następnie jest ładowany i jego eksportuje są pobierane.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>Krok 2 — Inicjowanie i uruchamianie czasu uruchomieniowego programu .NET Core

I `hostfxr_initialize_for_runtime_config` `hostfxr_get_runtime_delegate` funkcje zainicjować i uruchomić program .NET Core runtime przy użyciu konfiguracji czasu wykonywania dla składnika zarządzanego, który zostanie załadowany. Funkcja `hostfxr_get_runtime_delegate` jest używana do uzyskania delegata czasu wykonywania, który umożliwia ładowanie zestawu zarządzanego i uzyskanie wskaźnika funkcji do metody statycznej w tym zestawie.

[!code-cpp[HostFxrHost#Initialize](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>Krok 3 — załaduj zarządzany zestaw i pobierz wskaźnik funkcji do metody zarządzanej

Pełnomocnik czasu wykonywania jest wywoływana, aby załadować zarządzany zestaw i uzyskać wskaźnik funkcji do metody zarządzanej. Pełnomocnik wymaga ścieżki zestawu, nazwy typu i nazwy metody jako dane wejściowe i zwraca wskaźnik funkcji, który może służyć do wywoływania metody zarządzanej.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

Przekazując `nullptr` jako nazwę typu delegata podczas wywoływania delegata czasu wykonywania, przykład używa podpisu domyślnego dla metody zarządzanej:

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Inny podpis może służyć przez określenie nazwy typu delegata podczas wywoływania delegata w czasie wykonywania.

### <a name="step-4---run-managed-code"></a>Krok 4 - Uruchom kod zarządzany!

Host macierzysty może teraz wywołać metodę zarządzaną i przekazać ją żądane parametry.

[!code-cpp[HostFxrHost#CallManaged](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>Tworzenie hosta przy użyciu coreclrHost.h

W poniższych krokach szczegółowo opisano sposób używania interfejsu API CoreClrHost.h do uruchamiania programu runtime .NET Core w aplikacji natywnej i wywołania w zarządzanej metodzie statycznej. Fragmenty kodu w tym dokumencie używają niektórych interfejsów API specyficznych dla systemu Windows, ale [pełny przykładowy host](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) pokazuje ścieżki kodu systemu Windows i Linux.

[Host Unix CoreRun](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/unixcorerun) pokazuje bardziej złożony, rzeczywisty przykład hostingu przy użyciu coreclrhost.h.

### <a name="step-1---find-and-load-coreclr"></a>Krok 1 - Znajdź i załaduj CoreCLR

Interfejsy API środowiska uruchomieniowego .NET Core znajdują się w *pliku coreclr.dll* (w systemie Windows), w *libcoreclr.so* (w systemie Linux) lub w *systemie libcoreclr.dylib* (w systemie macOS). Pierwszym krokiem do hostowania .NET Core jest załadowanie biblioteki CoreCLR. Niektóre hosty sondują różne ścieżki lub używają parametrów wejściowych, aby znaleźć bibliotekę, podczas gdy inni wiedzą, aby załadować ją z określonej ścieżki (na przykład obok hosta lub z lokalizacji dla całego komputera).

Po znalezieniu biblioteka jest `LoadLibraryEx` ładowana (w systemie Windows) lub `dlopen` (w systemie Linux/macOS).

[!code-cpp[CoreClrHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Krok 2 - Pobierz funkcje hostingu .NET Core

CoreClrHost ma kilka ważnych metod przydatnych do hostowania .NET Core:

* `coreclr_initialize`: Uruchamia program .NET Core i konfiguruje domyślną (i jedyną) domenę aplikacji.
* `coreclr_execute_assembly`: Wykonuje zarządzany zestaw.
* `coreclr_create_delegate`: Tworzy wskaźnik funkcji do metody zarządzanej.
* `coreclr_shutdown`: Zamyka program runtime .NET Core.
* `coreclr_shutdown_2`: `coreclr_shutdown`Like , ale także pobiera kod zakończenia kodu zarządzanego.

Po załadowaniu biblioteki CoreCLR następnym krokiem jest `GetProcAddress` uzyskanie odwołań `dlsym` do tych funkcji przy użyciu (w systemie Windows) lub (w systemie Linux/macOS).

[!code-cpp[CoreClrHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Krok 3 - Przygotowanie właściwości czasu wykonywania

Przed uruchomieniem czasu wykonywania, należy przygotować niektóre właściwości, aby określić zachowanie (szczególnie dotyczące modułu ładującego zestawu).

Typowe właściwości obejmują:

* `TRUSTED_PLATFORM_ASSEMBLIES`Jest to lista ścieżek zestawu (rozdzielonych przez ';' w systemie Windows i ':' w systemie Linux), które środowisko uruchomieniowe będzie można rozwiązać domyślnie. Niektóre hosty mają zakodowane manifesty z listą zestawów, które mogą załadować. Inni umieści ą dowolną bibliotekę w niektórych lokalizacjach (na przykład obok *pliku coreclr.dll)* na tej liście.
* `APP_PATHS`Jest to lista ścieżek do sondowania dla zestawu, jeśli nie można go znaleźć na liście zestawów zaufanych platform (TPA). Ponieważ host ma większą kontrolę nad tym, które zestawy są ładowane przy użyciu listy TPA, jest najlepszym rozwiązaniem dla hostów, aby określić, które zestawy oczekują załadować i wyświetlić je jawnie. Jeśli sondowanie w czasie wykonywania jest potrzebne, jednak ta właściwość może włączyć ten scenariusz.
* `APP_NI_PATHS`Ta lista jest podobna do APP_PATHS z tą różnicą, że ma to być ścieżki, które będą badane dla obrazów macierzystych.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Ta właściwość jest lista ścieżek moduł uładujący powinien sondować podczas poszukiwania natywnych bibliotek wywoływanych za pośrednictwem p/invoke.
* `PLATFORM_RESOURCE_ROOTS`Ta lista zawiera ścieżki do sondowania dla zestawów satelickich zasobów (w podkatalogach specyficznych dla kultury).

W tym przykładowym hoście lista TPA jest konstruowana przez po prostu listę wszystkich bibliotek w bieżącym katalogu:

[!code-cpp[CoreClrHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Ponieważ przykład jest prosty, wymaga `TRUSTED_PLATFORM_ASSEMBLIES` tylko właściwości:

[!code-cpp[CoreClrHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Krok 4 - Rozpoczynanie pracy runtime

W przeciwieństwie do interfejsu API hostingu mscoree.h (opisaneponiżej), interfejsy API CoreCLRHost.h uruchamiają czas wykonywania i tworzą domyślną domenę AppDomain za pomocą jednego wywołania. Funkcja `coreclr_initialize` przyjmuje ścieżkę podstawową, nazwę i właściwości opisane wcześniej i zwraca dojście do hosta za pośrednictwem parametru. `hostHandle`

[!code-cpp[CoreClrHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Krok 5 - Uruchom kod zarządzany!

Po uruchomieniu uruchomiono hosta można wywołać kod zarządzany. Można to zrobić na kilka różnych sposobów. Przykładowy kod połączony z `coreclr_create_delegate` tym samouczkiem używa funkcji do utworzenia delegata do statycznej metody zarządzanej. Ten interfejs API przyjmuje [nazwę zestawu,](../../standard/assembly/names.md)nazwę typu kwalifikowanego obszaru nazw i nazwę metody jako dane wejściowe i zwraca pełnomocnika, który może służyć do wywoływania metody.

[!code-cpp[CoreClrHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#5)]

W tym przykładzie host może `managedDelegate` teraz `ManagedWorker.DoWork` wywołać, aby uruchomić metodę.

Alternatywnie `coreclr_execute_assembly` funkcja może służyć do uruchamiania zarządzanego pliku wykonywalnego. Ten interfejs API przyjmuje ścieżkę zestawu i tablicę argumentów jako parametry wejściowe. Ładuje zestawu na tej ścieżce i wywołuje jego główną metodę.

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Krok 6 - Zamknięcie i czyszczenie

Na koniec po zakończeniu uruchamiania kodu zarządzanego, program runtime `coreclr_shutdown` `coreclr_shutdown_2`.NET Core jest zamykany z lub .

[!code-cpp[CoreClrHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithCoreClrHost/src/SampleHost.cpp#6)]

Program CoreCLR nie obsługuje ponownej inicjalizacji ani rozładunku. Nie należy `coreclr_initialize` dzwonić ponownie ani nie zwalniać biblioteki CoreCLR.

## <a name="create-a-host-using-mscoreeh"></a>Tworzenie hosta przy użyciu mscoree.h

Jak wspomniano wcześniej, CoreClrHost.h jest teraz preferowaną metodą hostowania programu .NET Core. Interfejs `ICLRRuntimeHost4` nadal może być używany, jeśli interfejsy CoreClrHost.h nie są wystarczające (jeśli potrzebne są niestandardowe flagi uruchamiania, na przykład lub jeśli appdomainmanager jest potrzebny w domenie domyślnej). Te instrukcje poprowadzą Cię przez hosting .NET Core za pomocą mscoree.h.

[Host CoreRun](https://github.com/dotnet/runtime/tree/master/src/coreclr/src/hosts/corerun) pokazuje bardziej złożony, rzeczywisty przykład hostingu przy użyciu mscoree.h.

### <a name="a-note-about-mscoreeh"></a>Uwaga o mscoree.h
Interfejs `ICLRRuntimeHost4` hostingu .NET Core jest zdefiniowany w [MSCOREE. IDL](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/inc/MSCOREE.IDL). Wersja nagłówkowa tego pliku (mscoree.h), do której host będzie musiał się odwoływać, jest tworzona za pośrednictwem midl po skonstruowaniu [czasu uruchomieniowego .NET Core.](https://github.com/dotnet/runtime/) Jeśli nie chcesz tworzyć .NET Core runtime, mscoree.h jest również dostępny jako [wstępnie utworzony nagłówek](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/) w repozytorium dotnet/runtime.

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1 - Identyfikacja zarządzanego punktu wejścia
Po odróżnieniu się od niezbędnych nagłówków[(mscoree.h](https://github.com/dotnet/runtime/blob/master/src/coreclr/src/pal/prebuilt/inc/mscoree.h) i stdio.h, na przykład), jedną z pierwszych rzeczy, które musi zrobić host .NET Core, jest zlokalizowanie zarządzanego punktu wejścia, z którym będzie korzystał. W naszym przykładowym hoście odbywa się to po prostu biorąc pierwszy argument wiersza `main` polecenia do naszego hosta jako ścieżka do pliku binarnego zarządzanego, którego metoda zostanie wykonana.

[!code-cpp[NetCoreHost#1](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>Krok 2 - Znajdź i załaduj CoreCLR
Interfejsy API środowiska uruchomieniowego .NET Core są w *pliku CoreCLR.dll* (w systemie Windows). Aby uzyskać nasz`ICLRRuntimeHost4`interfejs hostingowy ( ), konieczne jest znalezienie i załadowanie *pliku CoreCLR.dll*. To do hosta, aby zdefiniować konwencję, w jaki sposób będzie zlokalizować *CoreCLR.dll*. Niektóre hosty oczekują, że plik będzie obecny w znanej lokalizacji dla całego komputera (takiej jak *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*). Inni oczekują, że *plik CoreCLR.dll* zostanie załadowany z lokalizacji obok samego hosta lub aplikacji, która ma być hostowana. Jeszcze inni mogą zapoznać się ze zmienną środowiskową, aby znaleźć bibliotekę.

W systemie Linux lub macOS podstawowa biblioteka runtime jest odpowiednio *libcoreclr.so* lub *libcoreclr.dylib.*

Nasz przykładowy host sonduje kilka typowych lokalizacji dla *pliku CoreCLR.dll*. Po znalezieniu, musi `LoadLibrary` być `dlopen` załadowany przez (lub na Linux / macOS).

[!code-cpp[NetCoreHost#2](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>Krok 3 — pobierz wystąpienie ICLRRuntimeHost4
Interfejs `ICLRRuntimeHost4` hostingu jest pobierany przez wywołanie `GetProcAddress` (lub `dlsym` `GetCLRRuntimeHost`na Linux / macOS) na , a następnie wywołanie tej funkcji.

[!code-cpp[NetCoreHost#3](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>Krok 4 - Ustawianie flag startowych i uruchamianie czasu wykonywania
Z `ICLRRuntimeHost4` w-hand, możemy teraz określić flagi uruchamiania całego programu runtime i uruchomić czas wykonywania. Flagi uruchamiania określają, które moduły zbierające elementy bezużyteczne (GC) mają być używane (równoczesne lub serwer), czy użyjemy jednej domeny Aplikacji lub wielu domen aplikacji oraz jakie zasady optymalizacji modułu ładującego mają być używane (do ładowania zestawów neutralne dla domeny).

[!code-cpp[NetCoreHost#4](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#4)]

Czas wykonywania jest uruchamiany `Start` z wywołaniem funkcji.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5 — przygotowywanie ustawień domeny aplikacji
Po uruchomieniu czasu uruchomieniowego będziemy chcieli skonfigurować AppDomain. Istnieje wiele opcji, które muszą być określone podczas tworzenia domeny aplikacji .NET, jednak, więc konieczne jest, aby przygotować te najpierw.

Flagi AppDomain określają zachowania domeny aplikacji związane z zabezpieczeniami i współżycia. Starsze hosty programu Silverlight używały tych ustawień do izolowania kodu użytkownika, ale większość nowoczesnych hostów .NET Core uruchamia kod użytkownika jako pełne zaufanie i włącza współżycie.

[!code-cpp[NetCoreHost#5](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#5)]

Po podjęciu decyzji, które flagi AppDomain do użycia, AppDomain właściwości muszą być zdefiniowane. Właściwości są pary klucz/wartość ciągów. Wiele właściwości odnoszą się do jak AppDomain będzie ładować zestawy.

Typowe właściwości AppDomain obejmują:

* `TRUSTED_PLATFORM_ASSEMBLIES`Jest to lista ścieżek zestawu `;` (rozdzielonych przez system Windows i `:` Linux/macOS), które AppDomain powinny priorytetładowania ładowania i dać pełne zaufanie do (nawet w domenach częściowo zaufanych). Ta lista ma zawierać zestawy "Framework" i inne zaufane moduły, podobne do gac w scenariuszach .NET Framework. Niektóre hosty umieści dowolną bibliotekę obok *pliku coreclr.dll* na tej liście, inne mają zakodowane manifesty z listą zaufanych zestawów do swoich celów.
* `APP_PATHS`Jest to lista ścieżek do sondowania dla zestawu, jeśli nie można go znaleźć na liście zestawów zaufanych platform (TPA). Ponieważ host ma większą kontrolę nad tym, które zestawy są ładowane przy użyciu listy TPA, jest najlepszym rozwiązaniem dla hostów, aby określić, które zestawy oczekują załadować i wyświetlić je jawnie. Jeśli sondowanie w czasie wykonywania jest potrzebne, jednak ta właściwość może włączyć ten scenariusz.
* `APP_NI_PATHS`Ta lista jest bardzo podobna do APP_PATHS z tą różnicą, że ma to być ścieżki, które będą badane dla obrazów natywnych.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Ta właściwość jest lista ścieżek moduł uładujący powinien sondować podczas poszukiwania natywnych bibliotek DLL wywołanych przez p/invoke.
* `PLATFORM_RESOURCE_ROOTS`Ta lista zawiera ścieżki do sondowania dla zestawów satelickich zasobów (w podkatalogach specyficznych dla kultury).

W naszym [prostym przykładowym hoście](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)te właściwości są konfigurowane w następujący sposób:

[!code-cpp[NetCoreHost#6](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6 - Tworzenie appdomain
Po przygotowaniu wszystkich flag i `ICLRRuntimeHost4::CreateAppDomainWithManager` właściwości AppDomain, można skonfigurować AppDomain. Ta funkcja opcjonalnie przyjmuje w pełni kwalifikowaną nazwę zestawu i nazwę typu do użycia jako menedżera domeny AppDomain. Menedżer AppDomain może zezwolić hostowi na kontrolowanie niektórych aspektów zachowania domeny aplikacji i może zapewnić punkty wejścia do uruchomienia kodu zarządzanego, jeśli host nie zamierza bezpośrednio wywoływać kodu użytkownika.

[!code-cpp[NetCoreHost#7](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7 - Uruchom kod zarządzany!
Z AppDomain i działa, host może teraz rozpocząć wykonywanie kodu zarządzanego. Najprostszym sposobem, aby `ICLRRuntimeHost4::ExecuteAssembly` to zrobić jest użycie do wywołania metody punktu wejścia zestawu zarządzanego. Należy zauważyć, że ta funkcja działa tylko w scenariuszach pojedynczej domeny.

[!code-cpp[NetCoreHost#8](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#8)]

Inną opcją, jeśli `ExecuteAssembly` nie spełnia potrzeb hosta, `CreateDelegate` jest użycie wskaźnika funkcji do statycznej metody zarządzanej. Wymaga to, aby host znał podpis metody, do których jest wywoływany (w celu utworzenia typu wskaźnika funkcji), ale umożliwia hostom elastyczność wywoływania kodu innego niż punkt wejścia zestawu. Nazwa zestawu podana w drugim parametrze jest [pełną zarządzaną nazwą zestawu](../../standard/assembly/names.md) biblioteki do załadowania.

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
    domainId,
    L"HW, Version=1.0.0.0, Culture=neutral", // Target managed assembly
    L"ConsoleApplication.Program",           // Target managed type
    L"Main",                                 // Target entry point (static method)
    (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>Krok 8 - Oczyszczanie
Na koniec host powinien oczyścić się po sobie, zwalniając AppDomains, `ICLRRuntimeHost4` zatrzymując środowiska uruchomieniowego i zwalniając odwołanie.

[!code-cpp[NetCoreHost#9](~/samples/snippets/core/tutorials/netcore-hosting/csharp/HostWithMscoree/host.cpp#9)]

CoreCLR nie obsługuje rozładunku. Nie należy zwalniać biblioteki CoreCLR.

## <a name="conclusion"></a>Podsumowanie
Po zbudowaniu hosta można go przetestować, uruchamiając go z wiersza polecenia i przekazując wszelkie argumenty, które oczekuje host (takie jak zarządzana aplikacja do uruchomienia dla przykładowego hosta mscoree). Określając aplikację .NET Core do uruchomienia hosta, należy użyć pliku dll, `dotnet build`który jest tworzony przez . Pliki wykonywalne (.exe plików) produkowane przez `dotnet publish` dla aplikacji samodzielnych są w rzeczywistości domyślnym hostem .NET Core (dzięki czemu aplikacja może być uruchamiana bezpośrednio z wiersza polecenia w scenariuszach mainline); kod użytkownika jest kompilowany do dll o tej samej nazwie.

Jeśli rzeczy nie działają początkowo, dokładnie sprawdź, czy *plik coreclr.dll* jest dostępny w lokalizacji oczekiwanej przez hosta, że wszystkie niezbędne biblioteki framework znajdują się na liście TPA i że bitness CoreCLR (32-bit lub 64-bit) pasuje do sposobu hosta został zbudowany.

Hostowanie programu uruchomieniowego .NET Core jest zaawansowanym scenariuszem, którego wielu deweloperów nie będzie wymagać, ale dla tych, którzy muszą uruchomić kod zarządzany z procesu macierzystego lub którzy potrzebują większej kontroli nad zachowaniem programu .NET Core, może to być bardzo przydatne.
