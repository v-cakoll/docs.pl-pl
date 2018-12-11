---
title: Napisać niestandardowego hosta środowiska uruchomieniowego .NET Core
description: Dowiedz się, obsługa środowiska uruchomieniowego .NET Core z kodu natywnego, aby wspierać zaawansowane scenariusze, które wymagają kontroli, jak działa środowisko uruchomieniowe platformy .NET Core.
author: mjrousos
ms.date: 02/03/2017
ms.custom: seodec18
ms.openlocfilehash: 861a02d2e409637d11c874f16ecd56a1a0fcd92a
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/10/2018
ms.locfileid: "53169641"
---
# <a name="write-a-custom-net-core-host-to-control-the-net-runtime-from-your-native-code"></a>Napisać niestandardowego hosta platformy .NET Core do kontrolowania środowiska uruchomieniowego .NET z kodu natywnego

Podobnie jak wszystkie kodu zarządzanego aplikacje platformy .NET Core są wykonywane przez hosta. Host jest odpowiedzialny za uruchamianie w czasie wykonywania (w tym składników, takich jak JIT i moduł wyrzucania elementów bezużytecznych), tworzenia domen aplikacji i wywoływania zarządzanego punkty wejścia.

Hostowanie środowiska uruchomieniowego .NET Core to zaawansowany scenariusz, i w większości przypadków platformy .NET Core, deweloperzy nie muszą się martwić o hostingu, ponieważ procesy kompilacji platformy .NET Core zapewniają domyślnego hosta do uruchamiania aplikacji .NET Core. W niektórych sytuacjach specjalistyczne jednak może być przydatne do jawnie hosta środowiska uruchomieniowego .NET Core, jako środek wywołanie kodu zarządzanego, natywnego procesu lub Aby uzyskać większą kontrolę nad jak działa środowisko uruchomieniowe.

Ten artykuł zawiera omówienie kroków niezbędnych do uruchamiania środowiska uruchomieniowego .NET Core z kodu natywnego, Utwórz domenę aplikacji początkowej (<xref:System.AppDomain>) i wykonywanie kodu zarządzanego w nim.

## <a name="prerequisites"></a>Wymagania wstępne

Ponieważ hosty znajdują się aplikacje natywne, w tym samouczku opisano tworzenie hosta platformy .NET Core w języku C++ aplikacji. Konieczne będzie środowisko programistyczne języka C++ (takim jak udostępniany przez [programu Visual Studio](https://aka.ms/vsdownload?utm_source=mscom&utm_campaign=msdocs)).

Możesz też prostą aplikację platformy .NET Core, aby przetestować hosta, więc należy zainstalować [zestawu .NET Core SDK](https://www.microsoft.com/net/core) i [tworzenie małych testowanie aplikacji platformy .NET Core](../../core/tutorials/with-visual-studio.md) (np. aplikacji "Hello World"). Aplikacja "Hello World" utworzony przez nowy szablon Projekt konsoli .NET Core jest wystarczająca.

W tym samouczku i jego skojarzone przykładowe kompilacji hosta Windows; Zobacz uwagi na końcu tego artykułu o hostingu w systemach Unix.

## <a name="creating-the-host"></a>Tworzenie hosta

A [hosta przykładowe](https://github.com/dotnet/samples/tree/master/core/hosting) ukazujące kroki opisane w tym artykule jest dostępny w repozytorium dotnet/samples w witrynie GitHub. Komentarze do próby *host.cpp* pliku wyraźnie kojarzenie ponumerowanych kroków z tego samouczka, z której jest przeprowadzane w próbce. Aby uzyskać instrukcje pobierania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Należy pamiętać, że host przykładowy jest przeznaczony do używana do celów, więc światło na sprawdzanie błędów i jest przeznaczony do wyróżnienia czytelności za pośrednictwem wydajności. Więcej przykładów rzeczywistych hosta są dostępne w [dotnet/coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) repozytorium. [Hosta CoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), w szczególności, to dobry host ogólnego przeznaczenia do badania po przeczytaniu za pomocą przykładowych prostsze.

### <a name="a-note-about-mscoreeh"></a>Uwaga dotycząca mscoree.h
Podstawowy interfejs hosta platformy .NET Core (`ICLRRuntimeHost2`) jest zdefiniowany w [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Nagłówek wersję tego pliku (mscoree.h), hosta należy do odwołania, jest generowany za pośrednictwem MIDL podczas [środowisko uruchomieniowe programu .NET Core](https://github.com/dotnet/coreclr/) jest wbudowana. Jeśli nie chcesz tworzyć środowiska uruchomieniowego .NET Core, mscoree.h jest również dostępny jako [wstępnie skompilowany nagłówek](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) w repozytorium dotnet/coreclr. [Instrukcje dotyczące tworzenia środowiska uruchomieniowego .NET Core](https://github.com/dotnet/coreclr#building-the-repository) znajdują się w repozytorium GitHub. 

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1 — ustalenie zarządzany punkt wejścia
Po odwołujące się do niezbędne nagłówki ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) i stdio.h, na przykład), jest jednym z pierwszych czynności należy wykonać na hoście platformy .NET Core, zlokalizuj zarządzany punkt wejścia będzie używana. W naszych przykładowych hosta, to wykonując tylko pierwszy argument wiersza polecenia do naszych hosta jako ścieżkę do zarządzanych danych binarnych którego `main` będzie można wykonać metody.

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>Krok 2 — Znajdź i załaduj CoreCLR.dll
Środowisko uruchomieniowe platformy .NET Core interfejsów API znajdują się w *CoreCLR.dll* (na Windows). Można pobrać interfejsu hostingu (`ICLRRuntimeHost2`), należy znaleźć i załadować *CoreCLR.dll*. Zależy od hosta, aby zdefiniować Konwencję dotyczącą sposobu zlokalizuje *CoreCLR.dll*. Niektóre hosty oczekiwać, że plik do dobrze znanego lokalizacji komputera (na przykład % programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0). Inne oczekuje, że *CoreCLR.dll* zostaną załadowane z miejsca obok hosta autonomiczną usługą Intune a aplikacja będzie hostowana. Nadal inne osoby mogą można znaleźć w zmiennej środowiskowej, aby znaleźć biblioteki.

W systemie Linux lub Mac jest podstawowej biblioteki środowiska uruchomieniowego *libcoreclr.so* lub *libcoreclr.dylib*, odpowiednio.

Nasze przykładowe hosta sondy kilka typowe lokalizacje dla *CoreCLR.dll*. Gdy zostanie znaleziony, zostać załadowany za pośrednictwem `LoadLibrary` (lub `dlopen` na system Linux lub Mac).

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>Krok 3 — Pobierz wystąpienie ICLRRuntimeHost2
`ICLRRuntimeHost2` Interfejs hosta jest pobierany przez wywołanie metody `GetProcAddress` (lub `dlsym` na system Linux lub Mac) na `GetCLRRuntimeHost`, a następnie wywoływania tej funkcji. 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>Krok 4 — ustawienie flagi uruchamiania i uruchamianie środowiska uruchomieniowego
Za pomocą `ICLRRuntimeHost2` dostępnych, możemy teraz określić flagi uruchamianie całego środowiska uruchomieniowego i uruchomić środowiska uruchomieniowego. Flagi uruchamiania określi, które moduł wyrzucania elementów bezużytecznych (GC) do użycia (współbieżnych lub serwera), czy użyto pojedynczego elementu AppDomain lub wielu domen aplikacji oraz jakie zasady optymalizacji modułu ładującego do użytku (niezależne od domeny ładowania zestawów).

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

Środowisko uruchomieniowe zostanie uruchomiony przy użyciu wywołania `Start` funkcji.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5 — ustawienia przygotowywanie elementu AppDomain
Po uruchomieniu środowiska uruchomieniowego, chcemy do skonfigurowania elementu AppDomain. Istnieje kilka opcji, które należy określić podczas tworzenia .NET elementu AppDomain, jednak tak jest przygotować je w pierwszej kolejności.

Flagi AppDomain Określ AppDomain zachowania związane z zabezpieczeniami i współdziałania. Starsze hosty programu Silverlight używany te ustawienia mają być piaskownicy kod użytkownika, ale większości współczesnych hostów platformy .NET Core uruchamiają kod użytkownika jako pełne zaufanie i włączyć współdziałanie.

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

Po podjęciu decyzji, które AppDomain flagi do użycia, należy zdefiniować właściwości elementu AppDomain. Właściwości to pary klucz/wartość ciągów. Wiele właściwości odnoszą się do jak element AppDomain zostanie załadowany zestawów.

Wspólne właściwości elementu AppDomain obejmują:

* `TRUSTED_PLATFORM_ASSEMBLIES` Jest to lista zestawu ścieżek (rozdzielonych przez ';' na Windows i ":" w systemach Unix) który element AppDomain nadać priorytet ładowanie i przyznać pełne zaufanie (nawet w częściowo zaufanych domen). Ta lista jest przeznaczona do zawierają zestawy "Framework" i innych zaufanych modułów, podobne do globalnej pamięci podręcznej zestawów w scenariuszach .NET Framework. Niektóre hosty będą obok Umieść każdą bibliotekę *coreclr.dll* na tej liście inne ma ustaloną manifesty listę zaufanych zestawów dla swoich potrzeb.
* `APP_PATHS` To jest lista ścieżek do sondowania w dla zestawu, jeśli nie można znaleźć na liście zestawów (TPA) TPM. Te ścieżki są przeznaczone do lokalizacji, gdzie można znaleźć zestawów użytkowników. W trybie piaskownicy elemencie AppDomain zestawy, ładowane z tych ścieżek zostanie udzielony tylko w częściowej relacji zaufania. Typowe ścieżki APP_PATH obejmują ścieżka aplikacji docelowej został załadowany z lub w innych lokalizacjach, w którym wiadomo, zasoby użytkownika na żywo.
*  `APP_NI_PATHS` Ta lista jest bardzo podobne do APP_PATHS, chyba że ma ją traktować jako ścieżek, które będzie sondowany dla obrazów natywnych.
*  `NATIVE_DLL_SEARCH_DIRECTORIES` Ta właściwość jest lista ścieżek, które moduł ładujący powinien sondowania, gdy szukasz natywnych bibliotek DLL wywoływanym za pośrednictwem p/invoke.
*  `PLATFORM_RESOURCE_ROOTS` Ta lista zawiera ścieżki do sondowania w dla zestawów satelickich zasobów (w podfolderach specyficzne dla kultury).

W naszym [hosta prostych przykładowych](https://github.com/dotnet/samples/tree/master/core/hosting), te właściwości są skonfigurowane w następujący sposób:

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6 — Tworzenie domeny aplikacji
Po przygotowaniu wszystkie flagi domeny aplikacji i właściwości `ICLRRuntimeHost2::CreateAppDomainWithManager` może służyć do konfigurowania elementu AppDomain. Ta funkcja przyjmuje opcjonalnie, w pełni kwalifikowanej nazwy zestawu i nazwa typu do użycia jako Menedżer ds. domeny AppDomain. Menedżer domeny aplikacji umożliwia hosta kontrolować niektóre aspekty zachowanie domeny aplikacji i może zapewnić punkty wejścia uruchamiania kodu zarządzanego, jeśli host nie zamierzasz bezpośrednio Wywołaj kod użytkownika.   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7 — wykonywania kodu zarządzanego!
Za pomocą elementu AppDomain skonfigurowaniu i uruchomieniu hosta można teraz rozpocząć wykonywanie kodu zarządzanego. W tym celu najłatwiej używać `ICLRRuntimeHost2::ExecuteAssembly` do wywołania metody punktu wejścia zestaw zarządzany. Należy pamiętać, że ta funkcja działa tylko w scenariuszach jednej domeny.

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

Innej opcji, jeśli `ExecuteAssembly` nie odpowiada potrzebom użytkownika hosta, jest użycie `CreateDelegate` utworzyć wskaźnik funkcji na statyczną zarządzane metody. Wymaga to hosta wiedzieć sygnatura metody jest wywoływanie (Aby utworzyć typ wskaźnika funkcji), ale pozwala hostom elastyczność wywołać kod inny niż wpisu zestawu punktu.

```C++
void *pfnDelegate = NULL;
hr = runtimeHost->CreateDelegate(
  domainId,
  L"HW, Version=1.0.0.0, Culture=neutral",  // Target managed assembly
  L"ConsoleApplication.Program",            // Target managed type
  L"Main",                                  // Target entry point (static method)
  (INT_PTR*)&pfnDelegate);

((MainMethodFp*)pfnDelegate)(NULL);
```

### <a name="step-8---clean-up"></a>Krok 8 — czyszczenia
Na koniec hosta powinno wyczyścić zasoby po sam zwalnianie domen aplikacji, zatrzymywanie środowiska uruchomieniowego i zwalniania `ICLRRuntimeHost2` odwołania.

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>Hostowanie platformy .NET Core w systemach Unix
.NET core to produkt dla wielu platform, działających w systemach operacyjnych Windows, Linux i Mac. Jednak jako aplikacje natywne, hosty, na różnych platformach będzie miał pewne różnice między nimi. Proces opisany powyżej użycia `ICLRRuntimeHost2` do uruchamiania środowiska uruchomieniowego, utworzyć elementu AppDomain i wykonywanie kodu zarządzanego, powinny działać na dowolnym obsługiwanym systemie operacyjnym. Jednak interfejsów zdefiniowane w mscoree.h może być kłopotliwe pracować na platformach Unix, ponieważ mscoree sprawia, że wiele założeń Win32.

Aby hostingu na platformach Unix łatwiejsze, zbiór więcej otoki neutralnymi hostingu interfejsu API są dostępne w [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).

Przykład użycia coreclrhost.h (zamiast bezpośrednio mscoree.h) są widoczne w [hosta UnixCoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). Kroki prowadzące do środowiska uruchomieniowego przy użyciu interfejsów API z coreclrhost.h są podobne do czynności, używając mscoree.h:

1. Identyfikowanie kodu zarządzanego do wykonania (polecenia wiersza parametrów, na przykład). 
2. Ładowanie biblioteki CoreCLR.
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. Uzyskiwanie wskaźników do funkcji do programu CoreCLR firmy `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly`, i `coreclr_shutdown` funkcji przy użyciu `dlsym`
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. Skonfiguruj właściwości domeny aplikacji (na przykład lista TPA). Jest to taki sam jak krok 5 z mscoree przepływu pracy, powyżej.
5. Użyj `coreclr_initialize` do uruchamiania środowiska uruchomieniowego i utworzyć elementu AppDomain. Spowoduje to również utworzenie `hostHandle` wskaźnika, który będzie używany w przyszłości hostingu wywołania.
    1. Należy pamiętać, że ta funkcja wykonuje role oba kroki od 4 do 6 z poprzedniej przepływu pracy. 
6. Użyj jednej `coreclr_execute_assembly` lub `coreclr_create_delegate` wykonywanie kodu zarządzanego. Te funkcje są analogiczne do firmy mscoree `ExecuteAssembly` i `CreateDelegate` funkcji z kroku 7 poprzedniej przepływu pracy.
7. Użyj `coreclr_shutdown` zwolnienie domeny aplikacji i zamknąć środowisko wykonawcze. 

## <a name="conclusion"></a>Wniosek
Po skompilowaniu hosta może zostać przetestowany, uruchamiając go z poziomu wiersza polecenia i przekazując argumenty (np. aplikacji zarządzanej, aby uruchomić) oczekuje hosta. Podczas określania aplikacji .NET Core dla hosta do uruchamiania, należy użyć pliku .dll, który jest wytwarzany przez `dotnet build`. Pliki wykonywalne produkowane przez `dotnet publish` aplikacje samodzielne są faktycznie domyślne platformy .NET Core hosta (tak, aby aplikację można uruchomić bezpośrednio z wiersza polecenia w scenariuszach linii głównej); użytkownika kod jest kompilowany do biblioteki dll o takiej samej nazwie. 

Jeśli elementy nie działa początkowo, dokładnie sprawdzić, które *coreclr.dll* jest dostępny w lokalizacji, oczekiwanego przez hosta, wszystkie wymagane biblioteki Framework znajdują się na liście elementu TPA, która pasuje do tego CoreCLR bitowych (32 - lub 64-bitowy) jak Host został skompilowany.

Hostowanie środowiska uruchomieniowego .NET Core to zaawansowany scenariusz nie będzie wymagać wielu programistów, że dla tych, którzy muszą do uruchomienia kodu zarządzanego z macierzysty proces lub potrzebują większą kontrolę nad zachowanie środowiska uruchomieniowego .NET Core, może być bardzo przydatne. Ponieważ platformy .NET Core jest w stanie uruchomić side-by-side z samym sobą, istnieje nawet możliwość tworzenie hostów, które zainicjować i wiele wersji środowiska uruchomieniowego .NET Core, a wykonanie aplikacji na wszystkich z nich w tym samym procesie. 
