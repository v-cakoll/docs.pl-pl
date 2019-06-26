---
title: Napisać niestandardowego hosta środowiska uruchomieniowego .NET Core
description: Dowiedz się, obsługa środowiska uruchomieniowego .NET Core z kodu natywnego, aby wspierać zaawansowane scenariusze, które wymagają kontroli, jak działa środowisko uruchomieniowe platformy .NET Core.
author: mjrousos
ms.date: 12/21/2018
ms.custom: seodec18
ms.openlocfilehash: d3bdaacd4be776e0e9fff01698cca360ea4c9c6d
ms.sourcegitcommit: bab17fd81bab7886449217356084bf4881d6e7c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2019
ms.locfileid: "67402021"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Napisać niestandardowego hosta platformy .NET Core do kontrolowania środowiska uruchomieniowego .NET z kodu natywnego

Podobnie jak wszystkie kodu zarządzanego aplikacje platformy .NET Core są wykonywane przez hosta. Host jest odpowiedzialny za uruchamianie środowiska uruchomieniowego (takie jak składników, takich jak JIT i moduł wyrzucania elementów bezużytecznych) i wywołując punkty wejścia zarządzanych.

Hostowanie środowiska uruchomieniowego .NET Core to zaawansowany scenariusz, i w większości przypadków platformy .NET Core, deweloperzy nie muszą się martwić o hostingu, ponieważ procesy kompilacji platformy .NET Core zapewniają domyślnego hosta do uruchamiania aplikacji .NET Core. W niektórych sytuacjach specjalistyczne jednak może być przydatne do jawnie hosta środowiska uruchomieniowego .NET Core, jako środek wywołanie kodu zarządzanego, natywnego procesu lub Aby uzyskać większą kontrolę nad jak działa środowisko uruchomieniowe.

Ten artykuł zawiera omówienie kroków niezbędnych do środowiska uruchomieniowego .NET Core z kodu natywnego, a wykonanie kodu zarządzanego w nim.

## <a name="prerequisites"></a>Wymagania wstępne

Ponieważ hosty znajdują się aplikacje natywne, w tym samouczku opisano tworzenie hosta platformy .NET Core w języku C++ aplikacji. Konieczne będzie środowisko programistyczne języka C++ (takim jak udostępniany przez [programu Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Możesz też prostą aplikację platformy .NET Core, aby przetestować hosta, więc należy zainstalować [zestawu .NET Core SDK](https://www.microsoft.com/net/core) i [tworzenie małych testowanie aplikacji platformy .NET Core](../../core/tutorials/with-visual-studio.md) (np. aplikacji "Hello World"). Aplikacja "Hello World" utworzony przez nowy szablon Projekt konsoli .NET Core jest wystarczająca.

## <a name="hosting-apis"></a>Interfejsy API hostingu
Istnieją trzy różne interfejsy API, które mogą służyć do hosta platformy .NET Core. Ten dokument (i skojarzone [przykłady](https://github.com/dotnet/samples/tree/master/core/hosting)) obejmuje wszystkie opcje.

* Hostowanie środowiska uruchomieniowego .NET Core w środowisku .NET Core 3.0 i nowszych preferowaną metodą jest `nethost` i `hostfxr` bibliotek interfejsów API. Te punkty wejścia złożoności znajdowania i konfigurowanie środowiska uruchomieniowego do inicjowania obsługi i zezwolić na uruchamianie aplikacji zarządzanych i wywoływanie statycznej metody zarządzanych.
* Hostowanie środowiska uruchomieniowego .NET Core, .NET Core 3.0 — przed preferowaną metodą jest [CoreClrHost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) interfejsu API. Ten interfejs API udostępnia funkcje łatwe uruchamianie i zatrzymywanie środowiska uruchomieniowego i wywoływania zarządzanego kodu, (albo poprzez uruchomienie zarządzanego pliku exe albo przez wywołanie metody statyczne zarządzanych).
* .NET core może też być hostowana przy użyciu `ICLRRuntimeHost4` interfejsu w [mscoree.h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h). Ten interfejs API został wokół dłużej niż CoreClrHost.h, więc widoczne starsze hosty korzystania z niego. Nadal działa i umożliwia nieco większą kontrolę nad procesu hostingu niż CoreClrHost. W przypadku większości scenariuszy jednak CoreClrHost.h jest preferowana, teraz ze względu na jej prostsza interfejsów API.

## <a name="sample-hosts"></a>Przykładowy Hosts
[Przykładowy hosts](https://github.com/dotnet/samples/tree/master/core/hosting) ukazujące czynności opisanych w samouczkach poniżej są dostępne w repozytorium dotnet/samples w witrynie GitHub. Komentarze w przykładach wyraźnie skojarzyć ponumerowanych kroków z tych samouczków, z której jest przeprowadzane w próbce. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Należy pamiętać, że hosty próbki są przeznaczone do służyć do celów, szkoleniowych, dzięki czemu są światło na sprawdzanie błędów i są przeznaczone do wyróżnienia czytelności za pośrednictwem wydajność.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>Tworzenie hosta przy użyciu NetHost.h i HostFxr.h

Poniższe kroki zawierają szczegółowe instrukcje dotyczące `nethost` i `hostfxr` biblioteki, aby uruchomić środowisko uruchomieniowe platformy .NET Core w aplikacji natywnej i wywołania do zarządzanej metody statycznej. [Przykładowe](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) używa `nethost` nagłówków i bibliotek, instalowane przy użyciu zestawu SDK platformy .NET i kopie [ `coreclr_delegates.h` ](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) i [ `hostfxr.h` ](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) pliki z [core-dotnet-setup](https://github.com/dotnet/core-setup) repozytorium.

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>Krok 1 — ładowanie HostFxr i eksportowane funkcje hostingu

`nethost` Biblioteka zapewnia `get_hostfxr_path` funkcji do lokalizowania `hostfxr` biblioteki. `hostfxr` Biblioteki udostępnia funkcje hostingu środowiska uruchomieniowego .NET Core. Pełną listę funkcji można znaleźć w [ `hostfxr.h` ](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) i [dokumentu macierzystego projektowania hostingu](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md). Próbki i w tym samouczku należy użyć następującego polecenia:
* `hostfxr_initialize_for_runtime_config`: Inicjalizuje kontekst hosta i przygotowanie do inicjowania środowiska uruchomieniowego .NET Core za pomocą konfiguracji określonego środowiska uruchomieniowego.
* `hostfxr_get_runtime_delegate`: Pobiera obiekt delegowany funkcjonalność aparatu plików wykonywalnych.
* `hostfxr_close`: Zamyka kontekstu hosta.

`hostfxr` Biblioteki znajduje się za pomocą `get_hostfxr_path`. Następnie załadowaniu i wywozu są pobierane.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>Krok 2 — inicjowanie i uruchom środowisko uruchomieniowe platformy .NET Core

`hostfxr_initialize_for_runtime_config` i `hostfxr_get_runtime_delegate` funkcje inicjuje i uruchamia środowisko uruchomieniowe platformy .NET Core za pomocą konfiguracji czasu wykonywania zarządzanego składnika, który zostanie załadowany. `hostfxr_get_runtime_delegate` Funkcja jest używana do pobierania delegata obsługi, który umożliwia ładowanie zestawu zarządzanego i wprowadzenie wskaźnik funkcji na metodę statyczną, w tym zestawie.

[!code-cpp[HostFxrHost#Initialize](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>Krok 3 — ładowanie zestawu zarządzanego i wskaźnik funkcji zarządzanej metody get

Delegata środowiska uruchomieniowego jest wywoływana, aby załadować zestaw zarządzany i Uzyskaj wskaźnik funkcji zarządzanej metody. Delegat wymaga ścieżka zestawu, wpisz nazwę i nazwę metody jako dane wejściowe i zwraca wskaźnik funkcji, który może służyć do wywołania metody zarządzanych.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

Przekazując `nullptr` jako nazwy typu delegata podczas wywoływania delegata środowiska uruchomieniowego, w przykładzie użyto domyślny podpis zarządzanej metody:

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Inny podpis mogą służyć podczas wywoływania delegata środowiska uruchomieniowego, określając nazwę typu delegata.

### <a name="step-4---run-managed-code"></a>Krok 4 — przebieg zarządzanego kodu!

Natywne hosta teraz można wywołać metodę zarządzanych i przekaż go w odpowiednie parametry.

[!code-cpp[HostFxrHost#CallManaged](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>Tworzenie hosta przy użyciu CoreClrHost.h

Poniższe kroki zawierają szczegółowe instrukcje dotyczące interfejsu API CoreClrHost.h można uruchomić środowiska uruchomieniowego .NET Core w aplikacji natywnej i wywołania do zarządzanej metody statycznej. Fragmenty kodu, w tym dokumencie przy użyciu niektórych interfejsów API specyficznych dla Windows, ale [hosta pełny przykład](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) zawiera ścieżki kodu systemów Windows i Linux.

[Hosta Unix CoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun) przedstawiono przykład bardziej złożone, rzeczywistych hostingu za pomocą coreclrhost.h.

### <a name="step-1---find-and-load-coreclr"></a>Krok 1 — Znajdź i załaduj CoreCLR

Środowisko uruchomieniowe platformy .NET Core interfejsów API znajdują się w *coreclr.dll* (na Windows) w polu *libcoreclr.so* (w systemie Linux) lub *libcoreclr.dylib* (w systemie macOS). Pierwszym krokiem do hostowanie platformy .NET Core jest można załadować biblioteki CoreCLR. Niektóre hosty sondowania różnych ścieżek, lub użyj parametrów wejściowych, aby znaleźć biblioteki, podczas gdy inne osoby, aby go załadować z określoną ścieżką (obok hosta, na przykład, lub z lokalizacji komputera).

Gdy zostanie znaleziony, biblioteki jest ładowany z `LoadLibraryEx` (na Windows) lub `dlopen` (w systemie Linux lub Mac).

[!code-cpp[CoreClrHost#1](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Krok 2 — Get platformy .NET Core funkcje hostingu

CoreClrHost ma kilka ważnych metod przydatne hostowanie platformy .NET Core:

* `coreclr_initialize`: Uruchamia środowisko uruchomieniowe platformy .NET Core i ustawia domyślne (i tylko) obiektu AppDomain.
* `coreclr_execute_assembly`: Wykonuje zestaw zarządzany.
* `coreclr_create_delegate`: Tworzy wskaźnik funkcji do zarządzanej metody.
* `coreclr_shutdown`: Zamyka środowisko uruchomieniowe platformy .NET Core.
* `coreclr_shutdown_2`: Podobnie jak `coreclr_shutdown`, ale również pobiera kod zarządzany kod zakończenia.

Po załadowaniu biblioteki CoreCLR, następnym krokiem jest pobieranie odwołań do tych funkcji przy użyciu `GetProcAddress` (na Windows) lub `dlsym` (w systemie Linux lub Mac).

[!code-cpp[CoreClrHost#2](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Krok 3 — Przygotowanie właściwości środowiska uruchomieniowego

Przed rozpoczęciem środowisko uruchomieniowe, jest wymagane do przygotowania niektóre właściwości, aby określić zachowanie (szczególnie dotyczące moduł ładujący zestaw).

Wspólne właściwości obejmują:

* `TRUSTED_PLATFORM_ASSEMBLIES` Jest to lista zestawu ścieżek (rozdzielonych przez ';' na Windows i ":" w systemie Linux), której środowisko uruchomieniowe będzie mieć możliwość rozpoznania domyślnie. Niektóre hosty ma ustaloną manifesty listę zestawów, które mogą oni ładować. Inne umieści wszystkie biblioteki w określonych lokalizacjach (obok *coreclr.dll*, na przykład) na tej liście.
* `APP_PATHS` To jest lista ścieżek do sondowania w dla zestawu, jeśli nie można znaleźć na liście zestawów (TPA) TPM. Ponieważ host nie ma większą kontrolę nad tym, którzy zestawy są ładowane przy użyciu listy elementu TPA, jest najlepszym rozwiązaniem dla hostów, aby określić zestawy, które spełniają oczekiwane obciążenia i wyświetlać je w sposób jawny. Jeśli potrzebne jest badania w czasie wykonywania, jednak tej właściwości można włączyć tego scenariusza.
* `APP_NI_PATHS` Ta lista jest podobne do APP_PATHS, z tą różnicą, że oznaczało ma być ścieżek, które będzie sondowany dla obrazów natywnych.
* `NATIVE_DLL_SEARCH_DIRECTORIES` Ta właściwość jest lista ścieżek, które moduł ładujący powinien sondowania podczas wyszukiwania dla bibliotek natywnych wywoływanym za pośrednictwem p/invoke.
* `PLATFORM_RESOURCE_ROOTS` Ta lista zawiera ścieżki do sondowania w dla zestawów satelickich zasobów (w podfolderach specyficzne dla kultury).

Na tym hoście próbki na liście elementu TPA jest tworzony po prostu wyświetlając wszystkie biblioteki w bieżącym katalogu:

[!code-cpp[CoreClrHost#7](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Ponieważ plik jest proste, wymaga tylko `TRUSTED_PLATFORM_ASSEMBLIES` właściwości:

[!code-cpp[CoreClrHost#3](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Krok 4 — uruchamianie runtime

W odróżnieniu od mscoree.h interfejsu API (opisanych poniżej), interfejsy API CoreCLRHost.h Uruchom środowisko uruchomieniowe i Utwórz domyślnej domeny aplikacji wszystko z jednego wywołania. `coreclr_initialize` Funkcja przyjmuje ścieżki podstawowej, nazwę i właściwości opisanych wcześniej, i zwraca uchwyt z powrotem do hosta za pośrednictwem `hostHandle` parametru.

[!code-cpp[CoreClrHost#4](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Krok 5 — wykonywania kodu zarządzanego!

W środowisku uruchomieniowym do hosta może wywoływać kod zarządzany. Można to zrobić na kilka różnych sposobów. Przykładowy kod powiązany ten samouczek używa `coreclr_create_delegate` funkcji, aby utworzyć obiekt delegowany do statycznej metody zarządzanych. Ten interfejs API [nazwy zestawu](../../framework/app-domains/assembly-names.md), nazwę typu kwalifikowanego na przestrzeń nazw i nazwę metody, jako danych wejściowych i zwraca obiekt delegowany, który może służyć do wywołania metody.

[!code-cpp[CoreClrHost#5](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#5)]

W tym przykładzie hosta teraz można wywołać `managedDelegate` do uruchomienia `ManagedWorker.DoWork` metody.

Alternatywnie `coreclr_execute_assembly` funkcja może służyć do uruchamiania zarządzanego pliku wykonywalnego. Ten interfejs API ma ścieżkę zestawu i tablicę argumentów jako parametry wejściowe. Ładuje zestaw w tej ścieżce i wywołuje jego głównej metody.

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Krok 6 — zamykanie i oczyścić

Na koniec, po zakończeniu uruchamiania kodu zarządzanego hosta środowiska uruchomieniowego .NET Core zostanie zamknięta za pomocą `coreclr_shutdown` lub `coreclr_shutdown_2`.

[!code-cpp[CoreClrHost#6](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR nepodporuje ponowne inicjowanie lub zwalnianie. Nie wywołuj `coreclr_initialize` ponownie lub zwalnianie biblioteki CoreCLR.

## <a name="create-a-host-using-mscoreeh"></a>Tworzenie hosta przy użyciu Mscoree.h

Jak wspomniano wcześniej, CoreClrHost.h jest teraz preferowana metoda hostowanie środowiska uruchomieniowego .NET Core. `ICLRRuntimeHost4` Interfejsu nadal można używać, jednak jeśli interfejsy CoreClrHost.h nie są wystarczające (w razie uruchamiania niestandardowej flagi są na przykład lub AppDomainManager jest wymagana w domyślnej domeny). Te instrukcje poprowadzi Cię hostowanie platformy .NET Core przy użyciu mscoree.h.

[Hosta CoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) przedstawiono przykład bardziej złożone, rzeczywistych hostingu za pomocą mscoree.h.

### <a name="a-note-about-mscoreeh"></a>Uwaga dotycząca mscoree.h
`ICLRRuntimeHost4` Platformy .NET Core hostingu interfejsu jest zdefiniowany w [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Nagłówek wersję tego pliku (mscoree.h), hosta należy do odwołania, jest generowany za pośrednictwem MIDL podczas [środowisko uruchomieniowe programu .NET Core](https://github.com/dotnet/coreclr/) jest wbudowana. Jeśli nie chcesz tworzyć środowiska uruchomieniowego .NET Core, mscoree.h jest również dostępny jako [wstępnie skompilowany nagłówek](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) w repozytorium dotnet/coreclr. [Instrukcje dotyczące tworzenia środowiska uruchomieniowego .NET Core](https://github.com/dotnet/coreclr#building-the-repository) znajdują się w repozytorium GitHub.

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1 — ustalenie zarządzany punkt wejścia
Po odwołujące się do niezbędne nagłówki ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) i stdio.h, na przykład), jest jednym z pierwszych czynności należy wykonać na hoście platformy .NET Core, zlokalizuj zarządzany punkt wejścia będzie używana. W naszych przykładowych hosta, to wykonując tylko pierwszy argument wiersza polecenia do naszych hosta jako ścieżkę do zarządzanych danych binarnych którego `main` będzie można wykonać metody.

[!code-cpp[NetCoreHost#1](~/samples/core/hosting/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>Krok 2 — Znajdź i załaduj CoreCLR
Środowisko uruchomieniowe platformy .NET Core interfejsów API znajdują się w *CoreCLR.dll* (na Windows). Można pobrać interfejsu hostingu (`ICLRRuntimeHost4`), należy znaleźć i załadować *CoreCLR.dll*. Zależy od hosta, aby zdefiniować Konwencję dotyczącą sposobu zlokalizuje *CoreCLR.dll*. Niektóre hosty oczekiwać pliku do dobrze znanej lokalizacji komputera (takich jak *%programfiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*). Inne oczekuje, że *CoreCLR.dll* zostaną załadowane z miejsca obok hosta autonomiczną usługą Intune a aplikacja będzie hostowana. Nadal inne osoby mogą można znaleźć w zmiennej środowiskowej, aby znaleźć biblioteki.

W systemie Linux lub Mac jest podstawowej biblioteki środowiska uruchomieniowego *libcoreclr.so* lub *libcoreclr.dylib*, odpowiednio.

Nasze przykładowe hosta sondy kilka typowe lokalizacje dla *CoreCLR.dll*. Gdy zostanie znaleziony, zostać załadowany za pośrednictwem `LoadLibrary` (lub `dlopen` na system Linux lub Mac).

[!code-cpp[NetCoreHost#2](~/samples/core/hosting/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>Krok 3 — Pobierz wystąpienie ICLRRuntimeHost4
`ICLRRuntimeHost4` Interfejs hosta jest pobierany przez wywołanie metody `GetProcAddress` (lub `dlsym` na system Linux lub Mac) na `GetCLRRuntimeHost`, a następnie wywoływania tej funkcji.

[!code-cpp[NetCoreHost#3](~/samples/core/hosting/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>Krok 4 — Ustaw flagi uruchamiania i uruchomić środowiska uruchomieniowego
Za pomocą `ICLRRuntimeHost4` dostępnych, możemy teraz określić flagi uruchamianie całego środowiska uruchomieniowego i uruchomić środowiska uruchomieniowego. Flagi uruchamiania określają, które moduł wyrzucania elementów bezużytecznych (GC) do użycia (współbieżnych lub serwera), czy użyto pojedynczego elementu AppDomain lub wielu domen aplikacji i jakie zasady optymalizacji modułu ładującego do użytku (niezależne od domeny ładowania zestawów).

[!code-cpp[NetCoreHost#4](~/samples/core/hosting/HostWithMscoree/host.cpp#4)]

Środowisko uruchomieniowe zostanie uruchomiony przy użyciu wywołania `Start` funkcji.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5 — ustawienia przygotowywanie elementu AppDomain
Po uruchomieniu środowiska uruchomieniowego, chcemy do skonfigurowania elementu AppDomain. Istnieje kilka opcji, które należy określić podczas tworzenia .NET elementu AppDomain, jednak tak jest przygotować je w pierwszej kolejności.

Flagi AppDomain Określ AppDomain zachowania związane z zabezpieczeniami i współdziałania. Starsze hosty programu Silverlight używany te ustawienia mają być piaskownicy kod użytkownika, ale większości współczesnych hostów platformy .NET Core uruchamiają kod użytkownika jako pełne zaufanie i włączyć współdziałanie.

[!code-cpp[NetCoreHost#5](~/samples/core/hosting/HostWithMscoree/host.cpp#5)]

Po podjęciu decyzji, które AppDomain flagi do użycia, należy zdefiniować właściwości elementu AppDomain. Właściwości to pary klucz/wartość ciągów. Wiele właściwości odnoszą się do jak element AppDomain zostanie załadowany zestawów.

Wspólne właściwości elementu AppDomain obejmują:

* `TRUSTED_PLATFORM_ASSEMBLIES` Jest to lista zestawu ścieżek (rozdzielone `;` na Windows i `:` na system Linux lub Mac) który element AppDomain nadać priorytet ładowanie i przyznać pełne zaufanie (nawet w częściowo zaufanych domen). Ta lista jest przeznaczona do zawierają zestawy "Framework" i innych zaufanych modułów, podobne do globalnej pamięci podręcznej zestawów w scenariuszach .NET Framework. Niektóre hosty będą obok Umieść każdą bibliotekę *coreclr.dll* na tej liście inne ma ustaloną manifesty listę zaufanych zestawów dla swoich potrzeb.
* `APP_PATHS` To jest lista ścieżek do sondowania w dla zestawu, jeśli nie można znaleźć na liście zestawów (TPA) TPM. Ponieważ host nie ma większą kontrolę nad tym, którzy zestawy są ładowane przy użyciu listy elementu TPA, jest najlepszym rozwiązaniem dla hostów, aby określić zestawy, które spełniają oczekiwane obciążenia i wyświetlać je w sposób jawny. Jeśli potrzebne jest badania w czasie wykonywania, jednak tej właściwości można włączyć tego scenariusza.
* `APP_NI_PATHS` Ta lista jest bardzo podobne do APP_PATHS, chyba że ma ją traktować jako ścieżek, które będzie sondowany dla obrazów natywnych.
* `NATIVE_DLL_SEARCH_DIRECTORIES` Ta właściwość jest lista ścieżek, które moduł ładujący powinien sondowania, gdy szukasz natywnych bibliotek DLL wywoływanym za pośrednictwem p/invoke.
* `PLATFORM_RESOURCE_ROOTS` Ta lista zawiera ścieżki do sondowania w dla zestawów satelickich zasobów (w podfolderach specyficzne dla kultury).

W naszym [hosta prostych przykładowych](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree), te właściwości są skonfigurowane w następujący sposób:

[!code-cpp[NetCoreHost#6](~/samples/core/hosting/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6 — Tworzenie domeny aplikacji
Po przygotowaniu wszystkie flagi domeny aplikacji i właściwości `ICLRRuntimeHost4::CreateAppDomainWithManager` może służyć do konfigurowania elementu AppDomain. Ta funkcja przyjmuje opcjonalnie, w pełni kwalifikowanej nazwy zestawu i nazwa typu do użycia jako Menedżer ds. domeny AppDomain. Menedżer domeny aplikacji umożliwia hosta kontrolować niektóre aspekty zachowanie domeny aplikacji i może zapewnić punkty wejścia uruchamiania kodu zarządzanego, jeśli host nie zamierzasz bezpośrednio Wywołaj kod użytkownika.

[!code-cpp[NetCoreHost#7](~/samples/core/hosting/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7 — wykonywania kodu zarządzanego!
Za pomocą elementu AppDomain skonfigurowaniu i uruchomieniu hosta można teraz rozpocząć wykonywanie kodu zarządzanego. W tym celu najłatwiej używać `ICLRRuntimeHost4::ExecuteAssembly` do wywołania metody punktu wejścia zestaw zarządzany. Należy pamiętać, że ta funkcja działa tylko w scenariuszach jednej domeny.

[!code-cpp[NetCoreHost#8](~/samples/core/hosting/HostWithMscoree/host.cpp#8)]

Innej opcji, jeśli `ExecuteAssembly` nie odpowiada potrzebom użytkownika hosta, jest użycie `CreateDelegate` utworzyć wskaźnik funkcji na statyczną zarządzane metody. Wymaga to hosta wiedzieć sygnatura metody jest wywoływanie (Aby utworzyć typ wskaźnika funkcji), ale pozwala hostom elastyczność wywołać kod inny niż wpisu zestawu punktu. Nazwa zestawu, pod warunkiem w drugi parametr jest [nazwy pełnego zestawu zarządzanego](../../framework/app-domains/assembly-names.md) biblioteki do załadowania.

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

### <a name="step-8---clean-up"></a>Krok 8 — czyszczenia
Na koniec hosta powinno wyczyścić zasoby po sam zwalnianie domen aplikacji, zatrzymywanie środowiska uruchomieniowego i zwalniania `ICLRRuntimeHost4` odwołania.

[!code-cpp[NetCoreHost#9](~/samples/core/hosting/HostWithMscoree/host.cpp#9)]

CoreCLR nepodporuje zwolnienie. Nie zwolnienia biblioteki CoreCLR.

## <a name="conclusion"></a>Wniosek
Po skompilowaniu hosta może zostać przetestowany, uruchamiając go z poziomu wiersza polecenia, a następnie przekazując argumenty hosta oczekuje (np. aplikacji zarządzanej można uruchomić hosta przykład mscoree). Podczas określania aplikacji .NET Core dla hosta do uruchamiania, należy użyć pliku .dll, który jest wytwarzany przez `dotnet build`. Pliki wykonywalne (pliki .exe) generowany przez `dotnet publish` aplikacje samodzielne są faktycznie domyślne platformy .NET Core hosta (tak, aby aplikację można uruchomić bezpośrednio z wiersza polecenia w scenariuszach linii głównej); użytkownika kod jest kompilowany do biblioteki dll o takiej samej nazwie.

Jeśli elementy nie działa początkowo, dokładnie sprawdzić, które *coreclr.dll* jest dostępny w lokalizacji, oczekiwanego przez hosta, wszystkie wymagane biblioteki Framework znajdują się na liście elementu TPA, która pasuje do tego CoreCLR bitowych (32 - lub 64-bitowy) jak Host został skompilowany.

Hostowanie środowiska uruchomieniowego .NET Core to zaawansowany scenariusz nie będzie wymagać wielu programistów, że dla tych, którzy muszą do uruchomienia kodu zarządzanego z macierzysty proces lub potrzebują większą kontrolę nad zachowanie środowiska uruchomieniowego .NET Core, może być bardzo przydatne.
