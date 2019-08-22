---
title: Napisz niestandardowego hosta środowiska uruchomieniowego platformy .NET Core
description: Dowiedz się, jak hostować środowisko uruchomieniowe platformy .NET Core z kodu natywnego, aby obsługiwać zaawansowane scenariusze, które wymagają kontrolowania sposobu działania środowiska uruchomieniowego .NET Core.
author: mjrousos
ms.date: 12/21/2018
ms.custom: seodec18
ms.openlocfilehash: 8eebc04390514bca288b67952ec7748366a45d6e
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/21/2019
ms.locfileid: "69660522"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Napisz niestandardowego hosta .NET Core, aby kontrolować środowisko uruchomieniowe platformy .NET z kodu natywnego

Podobnie jak w przypadku wszystkich kodów zarządzanych, aplikacje platformy .NET Core są wykonywane przez hosta. Host jest odpowiedzialny za uruchamianie środowiska uruchomieniowego (w tym składników, takich jak moduł odzyskiwania JIT i elementów bezużytecznych) i wywoływanie zarządzanych punktów wejścia.

Hostowanie środowiska uruchomieniowego .NET Core jest zaawansowanym scenariuszem, a w większości przypadków Deweloperzy platformy .NET Core nie muszą martwić się o hosting, ponieważ procesy kompilacji platformy .NET Core udostępniają domyślny Host do uruchamiania aplikacji platformy .NET Core. W niektórych wyspecjalizowanych sytuacjach może być przydatne jawne hostowanie środowiska uruchomieniowego platformy .NET Core jako metody wywoływania kodu zarządzanego w procesie macierzystym lub w celu uzyskania większej kontroli nad sposobem działania środowiska uruchomieniowego.

Ten artykuł zawiera omówienie kroków niezbędnych do uruchomienia środowiska uruchomieniowego platformy .NET Core z kodu natywnego i wykonywania w nim kodu zarządzanego.

## <a name="prerequisites"></a>Wymagania wstępne

Ponieważ hosty są aplikacjami natywnymi, ten samouczek będzie obejmować konstruowanie C++ aplikacji do hostowania programu .NET Core. Konieczne będzie środowisko C++ programistyczne (takie jak dostarczone przez [program Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Ponadto potrzebna jest prosta aplikacja .NET Core do testowania hosta za pomocą programu, dlatego należy zainstalować [zestaw .NET Core SDK](https://www.microsoft.com/net/core) i [utworzyć małą aplikację .NET Core test](with-visual-studio.md) (na przykład aplikację "Hello World"). Wystarczy aplikacja "Hello world" utworzona przy użyciu nowego szablonu projektu konsoli .NET Core.

## <a name="hosting-apis"></a>Hostowanie interfejsów API
Istnieją trzy różne interfejsy API, których można używać do hostowania programu .NET Core. Ten dokument (wraz ze skojarzonymi z nim [przykłady](https://github.com/dotnet/samples/tree/master/core/hosting)) pokrywa wszystkie opcje.

* Preferowaną metodą hostowania środowiska uruchomieniowego .NET Core w programie .NET Core 3,0 i nowszym jest `nethost` Interfejs `hostfxr` API bibliotek i. Te punkty wejścia obsługują złożoność znajdowania i konfigurowania środowiska uruchomieniowego na potrzeby inicjowania oraz umożliwiają uruchamianie aplikacji zarządzanej i wywoływanie jej w statycznej metodzie zarządzanej.
* Preferowaną metodą hostingu środowiska uruchomieniowego .NET Core przed programem .NET Core 3,0 jest interfejs API [CoreClrHost. h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h) . Ten interfejs API udostępnia funkcje ułatwiające uruchamianie i zatrzymywanie środowiska uruchomieniowego oraz Wywoływanie kodu zarządzanego (przez uruchomienie zarządzanego pliku exe lub poprzez wywoływanie statycznych metod zarządzanych).
* Środowisko .NET Core może być również obsługiwane za `ICLRRuntimeHost4` pomocą interfejsu w [bibliotece mscoree. h](https://github.com/dotnet/coreclr/blob/master/src/pal/prebuilt/inc/mscoree.h). Ten interfejs API był dłuższy niż CoreClrHost. h, dlatego prawdopodobnie widzisz na nich starsze hosty. Nadal działa i zapewnia lepszą kontrolę nad procesem hostingu niż CoreClrHost. W większości scenariuszy, chociaż CoreClrHost. h jest preferowany teraz z powodu łatwiejszych interfejsów API.

## <a name="sample-hosts"></a>Przykładowe hosty
[Przykładowe hosty](https://github.com/dotnet/samples/tree/master/core/hosting) pokazujące kroki opisane w poniższych samouczkach są dostępne w repozytorium GitHub/Samples. Komentarze w przykładach jasno kojarzą numerowane kroki z tych samouczków z miejscem, w którym są wykonywane w próbce. Aby uzyskać instrukcje dotyczące pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Należy pamiętać, że przykładowe hosty są przeznaczone do celów edukacyjnych, dzięki czemu są one jasne przy sprawdzaniu błędów i zostały zaprojektowane w celu wyróżnienia czytelności przez zwiększenie wydajności.

## <a name="create-a-host-using-nethosth-and-hostfxrh"></a>Tworzenie hosta przy użyciu usługi Host. h i HostFxr. h

Poniższe kroki szczegółowo opisują sposób użycia `nethost` bibliotek `hostfxr` i do uruchomienia środowiska uruchomieniowego platformy .NET Core w aplikacji natywnej i wywołania do zarządzanej metody statycznej. [Przykład](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithHostFxr) `nethost` używa nagłówka i biblioteki zainstalowanej z zestawem SDK .NET [`coreclr_delegates.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/coreclr_delegates.h) i kopii plików i [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) w repozytorium [dotnet/Core-Setup](https://github.com/dotnet/core-setup) .

### <a name="step-1---load-hostfxr-and-get-exported-hosting-functions"></a>Krok 1. Załaduj HostFxr i uzyskaj wyeksportowane funkcje hostingu

`nethost` Biblioteka zawiera`hostfxr` funkcję do lokalizowania biblioteki. `get_hostfxr_path` `hostfxr` Biblioteka udostępnia funkcje do hostowania środowiska uruchomieniowego platformy .NET Core. Pełną listę funkcji można znaleźć w [`hostfxr.h`](https://github.com/dotnet/core-setup/blob/master/src/corehost/cli/hostfxr.h) dokumencie, a natywny [dokument projektu hostingu](https://github.com/dotnet/core-setup/blob/master/Documentation/design-docs/native-hosting.md). W przykładzie i w tym samouczku są używane następujące elementy:
* `hostfxr_initialize_for_runtime_config`: Inicjuje kontekst hosta i przygotowuje się do inicjalizacji środowiska uruchomieniowego platformy .NET Core przy użyciu określonej konfiguracji środowiska uruchomieniowego.
* `hostfxr_get_runtime_delegate`: Pobiera delegata dla funkcji środowiska uruchomieniowego.
* `hostfxr_close`: Zamyka kontekst hosta.

Biblioteka zostanie znaleziona przy `get_hostfxr_path`użyciu. `hostfxr` Następnie jest ładowany, a jego eksporty są pobierane.

[!code-cpp[HostFxrHost#LoadHostFxr](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadHostFxr)]

### <a name="step-2---initialize-and-start-the-net-core-runtime"></a>Krok 2 — Inicjowanie i uruchamianie środowiska uruchomieniowego platformy .NET Core

Funkcje `hostfxr_initialize_for_runtime_config` i`hostfxr_get_runtime_delegate` inicjują i uruchamiają środowisko uruchomieniowe platformy .NET Core przy użyciu konfiguracji środowiska uruchomieniowego zarządzanego składnika, który zostanie załadowany. `hostfxr_get_runtime_delegate` Funkcja służy do uzyskania delegata środowiska uruchomieniowego, który umożliwia ładowanie zestawu zarządzanego i uzyskiwanie wskaźnika funkcji do statycznej metody w tym zestawie.

[!code-cpp[HostFxrHost#Initialize](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#Initialize)]

### <a name="step-3---load-managed-assembly-and-get-function-pointer-to-a-managed-method"></a>Krok 3. Załaduj zestaw zarządzany i Pobierz wskaźnik funkcji do metody zarządzanej

Delegat środowiska uruchomieniowego jest wywoływany, aby załadować zestaw zarządzany i uzyskać wskaźnik funkcji do metody zarządzanej. Delegat wymaga ścieżki zestawu, nazwy typu i nazwy metody jako danych wejściowych i zwraca wskaźnik funkcji, którego można użyć do wywołania metody zarządzanej.

[!code-cpp[HostFxrHost#LoadAndGet](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#LoadAndGet)]

Przekazując `nullptr` jako nazwę typu delegata podczas wywoływania delegata środowiska uruchomieniowego, przykład używa sygnatury domyślnej dla metody zarządzanej:

```csharp
public delegate int ComponentEntryPoint(IntPtr args, int sizeBytes);
```

Można użyć innej sygnatury, określając nazwę typu delegata podczas wywoływania delegata środowiska uruchomieniowego.

### <a name="step-4---run-managed-code"></a>Krok 4. uruchamianie kodu zarządzanego!

Host macierzysty może teraz wywołać metodę zarządzaną i przekazać do niej odpowiednie parametry.

[!code-cpp[HostFxrHost#CallManaged](~/samples/core/hosting/HostWithHostFxr/src/NativeHost/nativehost.cpp#CallManaged)]

## <a name="create-a-host-using-coreclrhosth"></a>Tworzenie hosta za pomocą CoreClrHost. h

Poniższe kroki szczegółowo opisują sposób użycia interfejsu API CoreClrHost. h do uruchomienia środowiska uruchomieniowego platformy .NET Core w aplikacji natywnej i wywołania do zarządzanej metody statycznej. Fragmenty kodu w tym dokumencie używają niektórych interfejsów API specyficznych dla systemu Windows, ale [pełny przykładowy Host](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithCoreClrHost) pokazuje ścieżki kodu systemu Windows i Linux.

Host współdziałający w [systemie UNIX](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/unixcorerun) przedstawia bardziej skomplikowany, rzeczywisty przykład hostingu przy użyciu coreclrhost. h.

### <a name="step-1---find-and-load-coreclr"></a>Krok 1 — Znajdowanie i ładowanie CoreCLR

Interfejsy API środowiska uruchomieniowego platformy .NET Core są w *CoreCLR. dll* (w systemie Windows), w *libcoreclr.so* (w systemie Linux) lub w *Libcoreclr. DYLIB* (na macOS). Pierwszym krokiem do hostowania programu .NET Core jest załadowanie biblioteki CoreCLR. Niektóre hosty sonduje różne ścieżki lub używają parametrów wejściowych do znajdowania biblioteki, podczas gdy inni wiedzą, aby załadować ją z określonej ścieżki (obok hosta, na przykład lub z lokalizacji na całym komputerze).

Po znalezieniu biblioteka jest załadowana do `LoadLibraryEx` programu (w systemie Windows `dlopen` ) lub (system Linux/Mac).

[!code-cpp[CoreClrHost#1](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#1)]

### <a name="step-2---get-net-core-hosting-functions"></a>Krok 2. Uzyskiwanie funkcji hostingu platformy .NET Core

CoreClrHost ma kilka ważnych metod, które są przydatne do hostowania programu .NET Core:

* `coreclr_initialize`: Uruchamia środowisko uruchomieniowe programu .NET Core i konfiguruje domyślną (i tylko) domenę aplikacji.
* `coreclr_execute_assembly`: Wykonuje zestaw zarządzany.
* `coreclr_create_delegate`: Tworzy wskaźnik funkcji do metody zarządzanej.
* `coreclr_shutdown`: Zamyka środowisko uruchomieniowe platformy .NET Core.
* `coreclr_shutdown_2`: Jak `coreclr_shutdown`również Pobiera kod zakończenia kodu zarządzanego.

Po załadowaniu biblioteki CoreCLR następnym krokiem jest uzyskanie odwołań do tych funkcji przy użyciu `GetProcAddress` systemu (w systemie Windows) lub `dlsym` (w systemie Linux/Mac).

[!code-cpp[CoreClrHost#2](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#2)]

### <a name="step-3---prepare-runtime-properties"></a>Krok 3 — Przygotowanie właściwości środowiska uruchomieniowego

Przed uruchomieniem środowiska uruchomieniowego należy przygotować pewne właściwości, aby określić zachowanie (zwłaszcza dotyczące modułu ładującego zestawy).

Typowe właściwości obejmują:

* `TRUSTED_PLATFORM_ASSEMBLIES`Jest to lista ścieżek zestawu (rozdzielonych znakami ";" w systemie Windows i ":" w systemie Linux), które środowisko uruchomieniowe będzie w stanie domyślnie rozpoznać. Niektóre hosty mają zakodowane manifesty zawierające listę zestawów, które mogą zostać załadowane. Inne umieściją wszystkie biblioteki w określonych lokalizacjach (obok *CoreCLR. dll*, na przykład) na tej liście.
* `APP_PATHS`Jest to lista ścieżek do sondowania w przypadku zestawu, jeśli nie można go znaleźć na liście zaufanych platform (TPA). Ponieważ Host ma większą kontrolę nad tym, które zestawy są ładowane przy użyciu listy TPA, najlepszym rozwiązaniem dla hostów jest określenie, które zestawy powinny być ładowane i wyświetlać je jawnie. Jeśli jednak jest wymagana sondowanie w czasie wykonywania, ta właściwość może włączyć ten scenariusz.
* `APP_NI_PATHS`Ta lista jest podobna do APP_PATHS, z tą różnicą, że jest to ścieżka, która będzie sondowana w przypadku obrazów natywnych.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Ta właściwość jest listą ścieżek, które moduł ładujący powinien sondować podczas wyszukiwania bibliotek natywnych wywoływanych za pomocą p/Invoke.
* `PLATFORM_RESOURCE_ROOTS`Ta lista zawiera ścieżki do sondowania w przypadku zestawów satelickich zasobów (w podkatalogach specyficznych dla kultury).

Na tym przykładowym hoście lista TPA jest tworzona przez wyświetlenie listy wszystkich bibliotek w bieżącym katalogu:

[!code-cpp[CoreClrHost#7](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#7)]

Ponieważ przykład jest prosty, wymaga `TRUSTED_PLATFORM_ASSEMBLIES` tylko właściwości:

[!code-cpp[CoreClrHost#3](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#3)]

### <a name="step-4---start-the-runtime"></a>Krok 4. Uruchamianie środowiska uruchomieniowego

W przeciwieństwie do interfejsu API hosta mscoree. h (opisanego poniżej), interfejsy API CoreCLRHost. h uruchamiają środowisko uruchomieniowe i tworzą domyślną domenę aplikacji w jednym wywołaniu. Funkcja przyjmuje ścieżkę bazową, nazwę i właściwości opisane wcześniej i zwraca dojście do hosta `hostHandle` za pośrednictwem parametru. `coreclr_initialize`

[!code-cpp[CoreClrHost#4](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#4)]

### <a name="step-5---run-managed-code"></a>Krok 5 — uruchamianie kodu zarządzanego!

Po uruchomieniu środowiska uruchomieniowego host może wywołać kod zarządzany. Można to zrobić na kilka różnych sposobów. Przykładowy kod połączony z tym samouczkiem używa funkcji `coreclr_create_delegate` , aby utworzyć delegata do statycznej metody zarządzanej. Ten interfejs API przyjmuje [nazwę zestawu](../../framework/app-domains/assembly-names.md), nazwę typu kwalifikowanego przestrzeni nazw i nazwę metody jako dane wejściowe i zwraca delegat, którego można użyć do wywołania metody.

[!code-cpp[CoreClrHost#5](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#5)]

W tym przykładzie host może teraz wywołać `managedDelegate` , aby `ManagedWorker.DoWork` uruchomić metodę.

Alternatywnie, `coreclr_execute_assembly` funkcja może służyć do uruchamiania zarządzanego pliku wykonywalnego. Ten interfejs API Pobiera ścieżkę zestawu i tablicę argumentów jako parametry wejściowe. Ładuje zestaw w tej ścieżce i wywołuje jego metodę Main.

```C++
int hr = executeAssembly(
        hostHandle,
        domainId,
        argumentCount,
        arguments,
        "HelloWorld.exe",
        (unsigned int*)&exitCode);
```

### <a name="step-6---shutdown-and-clean-up"></a>Krok 6 — Zamykanie i oczyszczanie

Na koniec, gdy host wykonuje kod zarządzany, środowisko uruchomieniowe programu .NET Core jest zamykane z `coreclr_shutdown` systemem `coreclr_shutdown_2`lub.

[!code-cpp[CoreClrHost#6](~/samples/core/hosting/HostWithCoreClrHost/src/SampleHost.cpp#6)]

CoreCLR nie obsługuje ponownego inicjowania ani zwalniania. Nie wywołuj `coreclr_initialize` ponownie ani nie zwalniaj biblioteki CoreCLR.

## <a name="create-a-host-using-mscoreeh"></a>Tworzenie hosta przy użyciu biblioteki Mscoree. h

Jak wspomniano wcześniej, CoreClrHost. h jest teraz preferowaną metodą hostowania środowiska uruchomieniowego platformy .NET Core. Można nadal używać interfejsu, ale jeśli interfejsy CoreClrHost. h nie są wystarczające (jeśli są potrzebne niestandardowe flagi uruchamiania, na przykład, lub jeśli element AppDomainManager jest wymagany w domenie domyślnej). `ICLRRuntimeHost4` Te instrukcje przeprowadzą Cię przez Hostowanie programu .NET Core przy użyciu biblioteki Mscoree. h.

[Host](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun) współdziałający przedstawia bardziej skomplikowany, rzeczywisty przykład hostingu przy użyciu biblioteki Mscoree. h.

### <a name="a-note-about-mscoreeh"></a>Notatka dotycząca biblioteki Mscoree. h
Interfejs `ICLRRuntimeHost4` hostingu platformy .NET Core jest zdefiniowany w [bibliotece mscoree. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Wersja nagłówka tego pliku (mscoree. h), do którego należy odwołanie, jest tworzona za pośrednictwem MIDL podczas kompilowania [środowiska uruchomieniowego .NET Core](https://github.com/dotnet/coreclr/) . Jeśli nie chcesz kompilować środowiska uruchomieniowego programu .NET Core, biblioteka mscoree. h jest również dostępna jako [wstępnie skompilowany nagłówek](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) w repozytorium dotnet/CoreCLR. [Instrukcje dotyczące tworzenia środowiska uruchomieniowego platformy .NET Core](https://github.com/dotnet/coreclr#building-the-repository) znajdują się w repozytorium GitHub.

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1. identyfikowanie zarządzanego punktu wejścia
Po odwołującym się do niezbędnych nagłówków (na przykład,[mscoree. h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) i stdio. h) jeden z pierwszych rzeczy hosta programu .NET Core musi znajdować się w tym zarządzanym punkcie wejścia, który będzie używany. W naszym przykładowym hoście jest to realizowane przez pobranie pierwszego argumentu wiersza polecenia do hosta jako ścieżki do zarządzanego pliku binarnego, którego `main` Metoda zostanie wykonana.

[!code-cpp[NetCoreHost#1](~/samples/core/hosting/HostWithMscoree/host.cpp#1)]

### <a name="step-2---find-and-load-coreclr"></a>Krok 2 — Znajdowanie i ładowanie CoreCLR
Interfejsy API środowiska uruchomieniowego platformy .NET Core są w *CoreCLR. dll* (w systemie Windows). Aby uzyskać nasz interfejs hostingu (`ICLRRuntimeHost4`), konieczne jest znalezienie i załadowanie *CoreCLR. dll*. W celu zdefiniowania Konwencji na potrzeby lokalizowania *biblioteki CoreCLR. dll*na hoście znajduje się na nim. Niektóre hosty oczekują, że plik jest obecny w dobrze znanej lokalizacji na całym komputerze (na przykład *%ProgramFiles%\dotnet\shared\Microsoft.NETCore.App\2.1.6*). Inne oczekują, że *CoreCLR. dll* zostanie załadowany z lokalizacji znajdującej się obok samego hosta lub aplikacji, która ma być hostowana. Nadal inne osoby mogą zapoznać się ze zmienną środowiskową, aby znaleźć bibliotekę.

W systemie Linux lub Mac podstawowa Biblioteka środowiska uruchomieniowego jest odpowiednio *libcoreclr.so* lub *libcoreclr. DYLIB*.

Nasz przykładowy Host sonduje kilka typowych lokalizacji dla *CoreCLR. dll*. Po znalezieniu należy go załadować za pośrednictwem `LoadLibrary` (lub `dlopen` w systemie Linux/Mac).

[!code-cpp[NetCoreHost#2](~/samples/core/hosting/HostWithMscoree/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost4-instance"></a>Krok 3. Pobieranie wystąpienia ICLRRuntimeHost4
Interfejs hostingu jest pobierany przez wywołanie `GetProcAddress` (lub `dlsym` w systemie Linux/Mac) `GetCLRRuntimeHost`w systemie, a następnie wywołanie tej funkcji. `ICLRRuntimeHost4`

[!code-cpp[NetCoreHost#3](~/samples/core/hosting/HostWithMscoree/host.cpp#3)]

### <a name="step-4---set-startup-flags-and-start-the-runtime"></a>Krok 4 — Ustawianie flag uruchamiania i uruchamianie środowiska uruchomieniowego
Za pomocą dostępnego w tym miejscu możemy teraz określić flagi uruchamiania w poziomie środowiska uruchomieniowego i uruchomić środowisko uruchomieniowe. `ICLRRuntimeHost4` Flagi uruchamiania określają, które moduły odzyskiwania pamięci (GC) mają być używane (współbieżne lub serwerowe), niezależnie od tego, czy będziemy używać jednego elementu AppDomain, czy wielu domen aplikacji oraz jakich zasad optymalizacji modułu ładującego użyć (na potrzeby ładowania zestawów w przypadku neutralnych domen).

[!code-cpp[NetCoreHost#4](~/samples/core/hosting/HostWithMscoree/host.cpp#4)]

Środowisko uruchomieniowe jest uruchomione z wywołaniem `Start` funkcji.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5. Przygotowywanie ustawień elementu AppDomain
Po uruchomieniu środowiska uruchomieniowego będziemy chcieć skonfigurować domenę aplikacji. Istnieje kilka opcji, które muszą zostać określone podczas tworzenia domeny AppDomain platformy .NET, dlatego konieczne jest ich uprzednie przygotowanie.

Flagi AppDomain określają zachowania AppDomain związane z zabezpieczeniami i międzyoperacyjną. Starsze hosty Silverlight używały tych ustawień do kodu użytkownika piaskownicy, ale większość nowoczesnych hostów .NET Core uruchamia kod użytkownika jako pełne zaufanie i umożliwia międzyoperacyjność.

[!code-cpp[NetCoreHost#5](~/samples/core/hosting/HostWithMscoree/host.cpp#5)]

Po podjęciu decyzji o tym, które flagi domen aplikacji należy użyć, muszą być zdefiniowane właściwości elementu AppDomain. Właściwości to pary klucz/wartość ciągów. Wiele właściwości odnosi się do sposobu, w jaki element AppDomain będzie ładować zestawy.

Wspólne właściwości elementu AppDomain obejmują:

* `TRUSTED_PLATFORM_ASSEMBLIES`Jest to lista ścieżek zestawu (ograniczona przez `;` system Windows i `:` w systemie Linux/Mac), dla której domena aplikacji ma określać priorytety ładowania i zapewnić pełne zaufanie (nawet w domenach częściowo zaufanych). Ta lista ma zawierać zestawy "Framework" i inne zaufane moduły, podobnie jak w przypadku scenariuszy .NET Framework GAC. Niektóre hosty umieściją wszystkie biblioteki obok *CoreCLR. dll* na tej liście, inne mają zakodowane manifesty zawierające listę zaufanych zestawów do swoich celów.
* `APP_PATHS`Jest to lista ścieżek do sondowania w przypadku zestawu, jeśli nie można go znaleźć na liście zaufanych platform (TPA). Ponieważ Host ma większą kontrolę nad tym, które zestawy są ładowane przy użyciu listy TPA, najlepszym rozwiązaniem dla hostów jest określenie, które zestawy powinny być ładowane i wyświetlać je jawnie. Jeśli jednak jest wymagana sondowanie w czasie wykonywania, ta właściwość może włączyć ten scenariusz.
* `APP_NI_PATHS`Ta lista jest bardzo podobna do APP_PATHS, z tą różnicą, że jest to ścieżka, która będzie sondowana w przypadku obrazów natywnych.
* `NATIVE_DLL_SEARCH_DIRECTORIES`Ta właściwość jest listą ścieżek, które moduł ładujący powinien sondować podczas wyszukiwania natywnych bibliotek DLL wywoływanych za pośrednictwem p/Invoke.
* `PLATFORM_RESOURCE_ROOTS`Ta lista zawiera ścieżki do sondowania w przypadku zestawów satelickich zasobów (w podkatalogach specyficznych dla kultury).

W naszym [prostym przykładowym hoście](https://github.com/dotnet/samples/tree/master/core/hosting/HostWithMscoree)te właściwości są konfigurowane w następujący sposób:

[!code-cpp[NetCoreHost#6](~/samples/core/hosting/HostWithMscoree/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6. Tworzenie domeny aplikacji
Po przygotowaniu `ICLRRuntimeHost4::CreateAppDomainWithManager` wszystkich flag i właściwości obiektu AppDomain można go użyć do skonfigurowania domeny aplikacji. Ta funkcja opcjonalnie przyjmuje w pełni kwalifikowaną nazwę zestawu i nazwę typu, który ma być używany jako Menedżer domen domeny. Menedżer domeny aplikacji może zezwolić hostowi na kontrolę niektórych aspektów zachowania obiektu AppDomain i może zapewnić punkty wejścia do uruchamiania kodu zarządzanego, Jeśli host nie zamierza bezpośrednio wywołać kodu użytkownika.

[!code-cpp[NetCoreHost#7](~/samples/core/hosting/HostWithMscoree/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7. uruchamianie kodu zarządzanego!
W przypadku wystąpienia elementu AppDomain up i uruchomiona host może teraz rozpocząć wykonywanie kodu zarządzanego. Najprostszym sposobem wykonania tej czynności jest `ICLRRuntimeHost4::ExecuteAssembly` wywołanie metody punktu wejścia zestawu zarządzanego. Należy zauważyć, że ta funkcja działa tylko w scenariuszach z jedną domeną.

[!code-cpp[NetCoreHost#8](~/samples/core/hosting/HostWithMscoree/host.cpp#8)]

Inna opcja, jeśli `ExecuteAssembly` nie spełnia wymagań hosta, `CreateDelegate` służy do tworzenia wskaźnika funkcji do statycznej metody zarządzanej. Wymaga to, aby Host wiedział sygnaturę metody, w której jest wywoływany (w celu utworzenia typu wskaźnika funkcji), ale umożliwia hostom elastyczność wywoływania kodu innego niż punkt wejścia zestawu. Nazwa zestawu podana w drugim parametrze jest [pełną zarządzaną nazwą zestawu](../../framework/app-domains/assembly-names.md) biblioteki do załadowania.

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

### <a name="step-8---clean-up"></a>Krok 8 — czyszczenie
Na koniec host powinien oczyścić się po nim, zwalniając z nich domeny AppDomain, zatrzymując środowisko uruchomieniowe i zwalniając `ICLRRuntimeHost4` odwołanie.

[!code-cpp[NetCoreHost#9](~/samples/core/hosting/HostWithMscoree/host.cpp#9)]

CoreCLR nie obsługuje zwalniania. Nie zwalniaj biblioteki CoreCLR.

## <a name="conclusion"></a>Wniosek
Po skompilowaniu hosta może on być testowany przez uruchomienie go z wiersza polecenia i przekazaniem wszystkich argumentów oczekiwanych przez hosta (takich jak zarządzana aplikacja do uruchomienia dla przykładowego hosta mscoree). Podczas określania aplikacji .NET Core do uruchomienia hosta upewnij się, że korzystasz z biblioteki DLL, która jest generowana przez `dotnet build`. Pliki wykonywalne (. exe) utworzone przez `dotnet publish` dla aplikacji samodzielnych są domyślnym hostem platformy .NET Core (aby można było uruchomić aplikację bezpośrednio z wiersza polecenia w scenariuszach linii głównej); kod użytkownika jest kompilowany do biblioteki DLL o tej samej nazwie.

Jeśli elementy nie działają na początku, należy dokładnie sprawdzić, czy *CoreCLR. dll* jest dostępny w lokalizacji oczekiwanej przez hosta, że wszystkie niezbędne biblioteki struktury znajdują się na liście TPA, a ta coreclr (32-lub 64-bitowa) jest zgodna z sposobem kompilowania hosta.

Hostowanie środowiska uruchomieniowego .NET Core jest zaawansowanym scenariuszem, który nie jest wymagany dla wielu deweloperów, ale dla tych, którzy muszą uruchamiać kod zarządzany z procesu macierzystego lub którzy potrzebują większej kontroli nad zachowaniem środowiska uruchomieniowego programu .NET Core, może być bardzo przydatna.
