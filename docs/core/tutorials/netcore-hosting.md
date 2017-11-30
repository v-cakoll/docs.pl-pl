---
title: Hosting .NET Core
description: "Hostowanie środowiska uruchomieniowego .NET Core z kodu natywnego"
keywords: .NET, .NET core hostingu, Hosting .NET Core
author: mjrousos
ms.author: mikerou
ms.date: 2/3/2017
ms.topic: article
ms.prod: .net-core
ms.devlang: dotnet
ms.assetid: 13edec8b-614d-47ed-9e95-ed6d3b94ec0c
ms.openlocfilehash: 1f0983b909244dda7270d3eff01dc302383639a5
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="hosting-net-core"></a>Hosting .NET Core

Podobnie jak wszystkie kodu zarządzanego aplikacje .NET Core są wykonywane przez hosta. Host jest odpowiedzialna za uruchamianie środowiska uruchomieniowego (w tym składników, takich jak JIT i moduł zbierający elementy bezużyteczne), tworzenie aplikacji i wywoływanie zarządzać punktów wejścia.

Hostowanie środowiska uruchomieniowego .NET Core zaawansowanego scenariusza i, w większości przypadków .NET Core deweloperzy nie musisz martwić się o hosting ponieważ procesy kompilacji platformy .NET Core zapewnia domyślnego hosta do uruchamiania aplikacji .NET Core. W niektórych sytuacjach specjalne jednak może być przydatne do jawnie hosta środowiska uruchomieniowego .NET Core, albo jako sposób wywoływania z kodu zarządzanego w procesie native lub w celu uzyskania większą kontrolę nad sposób działania środowiska uruchomieniowego.

Ten artykuł zawiera omówienie kroki niezbędne do uruchomienia środowiska uruchomieniowego .NET Core z kodu macierzystego, Tworzenie domeny aplikacji początkowej (<xref:System.AppDomain>) i wykonywanie kodu zarządzanego w nim.

## <a name="prerequisites"></a>Wymagania wstępne

Natywnych aplikacji nie są hosty, w tym samouczku opisano konstruowanie aplikacji C++, na hoście platformy .NET Core. Konieczne będzie środowiska programowania C++ (takim jak udostępniany przez [programu Visual Studio](https://www.visualstudio.com/downloads/)).

Trzeba będzie także prostą aplikację .NET Core, aby przetestować hosta, dlatego należy zainstalować [.NET Core SDK](https://www.microsoft.com/net/core) i [kompilacji małych przetestuj aplikację .NET Core](../../core/tutorials/with-visual-studio.md) (na przykład aplikacja "Hello World"). Aplikacja "Hello World" utworzone przez nowy szablon projektu konsoli .NET Core jest wystarczająca.

W tym samouczku i jego skojarzony przykładowa kompilacji hosta systemu Windows; Zobacz uwagi na końcu tego artykułu o hostingu w systemie Unix.

## <a name="creating-the-host"></a>Tworzenie hosta

A [hosta próbki](https://github.com/dotnet/docs/tree/master/samples/core/hosting) Demonstrowanie procedury opisane w tym artykule jest dostępny w repozytorium GitHub dotnet/docs. Komentarze w przykładowym *host.cpp* pliku wyraźnie Skojarz ponumerowane kroki z tego samouczka, z którym jest przeprowadzana w próbce. Instrukcje pobrania, zobacz [przykłady i samouczki](../../samples-and-tutorials/index.md#viewing-and-downloading-samples).

Należy pamiętać, że host próbki jest przeznaczona do zastosowania w przypadku uczenia celów, więc jest lekki na sprawdzanie błędów ani zaprojektowano w celu wyróżnienia czytelności za pośrednictwem wydajności. Więcej przykładów w rzeczywistych hosta są dostępne w [dotnet/środowisko coreclr](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts) repozytorium. [Hosta CoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts/corerun), w szczególności jest dobrym hosta ogólnego przeznaczenia badanie po odczytaniu za pośrednictwem próbki prostsze.

### <a name="a-note-about-mscoreeh"></a>Uwagi dotyczące mscoree.h
Podstawowy .NET Core interfejs hosta (`ICLRRuntimeHost2`) jest zdefiniowany w [MSCOREE. IDL](https://github.com/dotnet/coreclr/blob/master/src/inc/MSCOREE.IDL). Nagłówkiem w wersji tego pliku (mscoree.h), hosta należy do odwołania, jest generowany przez MIDL podczas [podstawowego środowiska wykonawczego .NET](https://github.com/dotnet/coreclr/) jest wbudowana. Jeśli nie chcesz utworzyć środowiska uruchomieniowego .NET Core, mscoree.h jest również dostępny jako [wstępnie skompilowanego nagłówka](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc) w repozytorium dotnet/środowisko coreclr. [Instrukcje dotyczące tworzenia środowiska uruchomieniowego .NET Core](https://github.com/dotnet/coreclr#building-the-repository) znajdują się w repozytorium GitHub. 

### <a name="step-1---identify-the-managed-entry-point"></a>Krok 1 — ustalenie zarządzany punkt wejścia
Po odwołujące się do niezbędne nagłówki ([mscoree.h](https://github.com/dotnet/coreclr/tree/master/src/pal/prebuilt/inc/mscoree.h) i stdio.h, na przykład), przede wszystkim hosta .NET Core trzeba wykonać jest zlokalizować punktu wejścia zarządzanych, będzie używana. W naszym hosta próbki odbywa się wykonując tylko pierwszy argument wiersza polecenia do naszej hosta jako ścieżka do pliku binarnego, zarządzane którego `main` będzie można wykonać metody.

[!code-cpp[NetCoreHost#1](../../../samples/core/hosting/host.cpp#1)]

### <a name="step-2---find-and-load-coreclrdll"></a>Krok 2 — Znajdź i obciążenia CoreCLR.dll
Środowisko uruchomieniowe .NET Core API znajdują się w *CoreCLR.dll* (w systemie Windows). Uzyskać naszych hostingu interfejsu (`ICLRRuntimeHost2`), należy odnaleźć i załadować *CoreCLR.dll*. Do hosta, aby zdefiniować sposób zlokalizuje Konwencja *CoreCLR.dll*. Niektóre hosty oczekiwać, że plik, który będzie znajdować się w dobrze znanej lokalizacji komputera (na przykład % programfiles%\dotnet\shared\Microsoft.NETCore.App\1.1.0). Inne oczekuje, że *CoreCLR.dll* zostanie pobrany z lokalizacji obok wybranego hosta siebie lub aplikacji ma być obsługiwana. Inne nadal może można znaleźć zmiennej środowiskowej można znaleźć biblioteki.

W systemie Linux lub Mac jest podstawowa Biblioteka środowiska uruchomieniowego *libcoreclr.so* lub *libcoreclr.dylib*odpowiednio.

Nasze przykładowe hosta sondy kilka wspólnej lokalizacji dla *CoreCLR.dll*. Znaleziono jeden raz, zostać załadowany za pośrednictwem `LoadLibrary` (lub `dlopen` na Linux/Mac).

[!code-cpp[NetCoreHost#2](../../../samples/core/hosting/host.cpp#2)]

### <a name="step-3---get-an-iclrruntimehost2-instance"></a>Krok 3 — Pobierz wystąpienia ICLRRuntimeHost2
`ICLRRuntimeHost2` Interfejs hosta jest pobierana przez wywołanie metody `GetProcAddress` (lub `dlsym` na systemie Linux/Mac) na `GetCLRRuntimeHost`, a następnie wywoływania tej funkcji. 

[!code-cpp[NetCoreHost#3](../../../samples/core/hosting/host.cpp#3)]

### <a name="step-4---setting-startup-flags-and-starting-the-runtime"></a>Krok 4 — ustawienie flagi uruchamiania i uruchamianie środowiska uruchomieniowego
Z `ICLRRuntimeHost2` dostępnych, możemy teraz określić flagi uruchamiania całego środowiska uruchomieniowego i uruchomić środowiska uruchomieniowego. Flagi uruchamiania określi, które moduł zbierający elementy bezużyteczne (GC) Aby użyć (równoczesnych lub serwera), czy używamy AppDomain jednego lub wielu obiektów AppDomain i jakie zasady optymalizacji modułu ładującego (dla neutralne dla domen ładowania zestawów).

[!code-cpp[NetCoreHost#4](../../../samples/core/hosting/host.cpp#4)]

Środowisko uruchomieniowe zostanie uruchomiony przy użyciu wywołania `Start` funkcji.

```C++
hr = runtimeHost->Start();
```

### <a name="step-5---preparing-appdomain-settings"></a>Krok 5 — ustawienia przygotowanie domeny aplikacji
Po uruchomieniu środowiska uruchomieniowego, chcemy do konfigurowania elementu AppDomain. Istnieje wiele opcji, które należy określić podczas tworzenia AppDomain .NET, więc przygotowanie tych pierwszej.

Flagi AppDomain określić zachowania elementu AppDomain związanych z bezpieczeństwem i interop. Starsze hostów Silverlight używane te ustawienia do kodu użytkownika piaskownicy, ale większość nowoczesnych hosty .NET Core uruchamiane przy pełnym zaufaniu kod użytkownika i włączyć interop.

[!code-cpp[NetCoreHost#5](../../../samples/core/hosting/host.cpp#5)]

Po podjęciu decyzji, które AppDomain flagi do użycia, właściwości elementu AppDomain muszą być zdefiniowane. Właściwości są pary klucz wartość ciągów. Wiele właściwości odnoszą się do elementu AppDomain zostanie jak ładowanie zestawów.

Wspólne właściwości domeny aplikacji obejmują:

* `TRUSTED_PLATFORM_ASSEMBLIES`Jest to lista ścieżek zestawu (rozdzielonych przez ';' w systemie Windows i ":" w systemie Unix) który elementu AppDomain powinien ustalić ich priorytety ładowania i zapewnia pełne zaufanie (nawet w częściowo zaufane domeny). Ta lista jest przeznaczona do zawierają zestawy 'Struktury' i innych zaufanych modułów, podobny do pamięci podręcznej GAC w scenariuszach .NET Framework. Niektóre hosty wprowadzi żadnej biblioteki obok *coreclr.dll* na tej liście ustalony manifestów listę zaufanych zestawów ich w celach innych osób.
* `APP_PATHS`Jest to lista ścieżek do sondowania w dla zestawu, jeśli nie można znaleźć na liście zestawów (TPA) TPM. Te ścieżki mają być lokalizacji, gdzie można znaleźć zestawów użytkowników. W trybie piaskownicy AppDomain zestawów załadowanych z tych ścieżek będzie można udzielać tylko częściowej relacji zaufania. Wspólne ścieżki APP_PATH obejmują ścieżka aplikacji docelowej został załadowany z ani innych lokalizacji, w którym zasoby użytkownika wiadomo, że na żywo.
*  `APP_NI_PATHS`Ta lista jest bardzo podobny do APP_PATHS z tą różnicą, że ma ma być ścieżek, które będzie sondowany dla obrazów natywnych.
*  `NATIVE_DLL_SEARCH_DIRECTORIES`Ta właściwość jest lista ścieżek, które moduł ładujący powinien sondowania wywołanego wyszukiwanie natywnych bibliotek DLL za pośrednictwem p/invoke.
*  `PLATFORM_RESOURCE_ROOTS`Ta lista zawiera ścieżki do sondowania w zestawów satelickich zasobów (w podfolderach specyficzne dla kultury).
*  `AppDomainCompatSwitch`Ten ciąg Określa, które Osobliwości zgodności ma być używany dla zestawów bez jawnego Moniker platformy docelowej (atrybut poziomu zestawu wskazującą Framework, które zestawu jest przeznaczona do uruchomienia). Zazwyczaj powinien to być ustawiony na `"UseLatestBehaviorWhenTFMNotSpecified"` , ale niektóre hosty mogą wolą starsze Silverlight lub Windows Phone zgodności Osobliwości, zamiast tego.

W naszym [hosta prosty przykład](https://github.com/dotnet/docs/tree/master/samples/core/hosting), te właściwości są skonfigurowane w następujący sposób:

[!code-cpp[NetCoreHost#6](../../../samples/core/hosting/host.cpp#6)]

### <a name="step-6---create-the-appdomain"></a>Krok 6 — utworzenie domeny aplikacji
Gdy wszystkie flagi AppDomain i właściwości są przygotowywane `ICLRRuntimeHost2::CreateAppDomainWithManager` może służyć do konfigurowania elementu AppDomain. Ta funkcja przyjmuje opcjonalnie pełni kwalifikowanej nazwy zestawu i nazwa typu do użycia jako Menedżer AppDomain domeny. Menedżer AppDomain można zezwolić na hosta kontrolować niektóre aspekty zachowanie domeny aplikacji i może udostępniać punktów wejścia do uruchamiania kodu zarządzanego, jeśli host nie ma zostać bezpośrednio wywoływać kod użytkownika.   

[!code-cpp[NetCoreHost#7](../../../samples/core/hosting/host.cpp#7)]

### <a name="step-7---run-managed-code"></a>Krok 7 — Uruchom kod zarządzany!
Z elementu AppDomain skonfigurowaniu i uruchomieniu hosta można teraz rozpocząć wykonywania kodu zarządzanego. Najprostszym sposobem, w tym celu jest użycie `ICLRRuntimeHost2::ExecuteAssembly` do wywołania metody punktu wejścia zarządzanego zestawu. Należy pamiętać, że ta funkcja działa tylko w jednej domenie scenariuszach.

[!code-cpp[NetCoreHost#8](../../../samples/core/hosting/host.cpp#8)]

Inną opcję, jeśli `ExecuteAssembly` nie odpowiada potrzebom na hoście, jest użycie `CreateDelegate` Aby utworzyć wskaźnik funkcji do statycznego zarządzane metody. Wymaga to hosta wiedzieć podpis metody jest wywoływanie (Aby utworzyć typ wskaźnika funkcji), ale pozwala hostom elastyczność do wywołania kodu innego niż wpisu zestawu punktu.

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

### <a name="step-8---clean-up"></a>Krok 8 - Oczyszczanie
Na koniec hosta powinien oczyszczanie po sam zwalnianie domen aplikacji, zatrzymując środowiska uruchomieniowego i zwalniania `ICLRRuntimeHost2` odwołania.

[!code-cpp[NetCoreHost#9](../../../samples/core/hosting/host.cpp#9)]

## <a name="about-hosting-net-core-on-unix"></a>O hostingu .NET Core w systemie Unix
Oprogramowanie .NET core to produkt i platform, działających w systemach operacyjnych Windows, Linux lub Mac. Jednak jako natywnych aplikacji hosty dla różnych platform ma pewne różnice między nimi. Proces opisany powyżej użycia `ICLRRuntimeHost2` do uruchamiania środowiska uruchomieniowego, utworzyć elementu AppDomain i wykonać kod zarządzany, powinny działać na dowolnym obsługiwanym systemie operacyjnym. Jednak interfejsów zdefiniowanych w mscoree.h może być skomplikowane do pracy z na platformach systemu Unix, ponieważ biblioteka mscoree sprawia, że wiele założenia Win32.

Aby hostingu na platformach systemu Unix jest łatwiejsze, zbiór więcej otoki niezależny od platformy obsługi interfejsu API są dostępne w [coreclrhost.h](https://github.com/dotnet/coreclr/blob/master/src/coreclr/hosts/inc/coreclrhost.h).

Przykład użycia coreclrhost.h (zamiast bezpośrednio mscoree.h) są widoczne w [hosta UnixCoreRun](https://github.com/dotnet/coreclr/tree/master/src/coreclr/hosts). Kroki umożliwiające korzystanie z interfejsów API z coreclrhost.h do obsługi środowiska uruchomieniowego są podobne do czynności, korzystając z mscoree.h:

1. Określenie kodu zarządzanego do wykonania (polecenia wiersz parametrów, na przykład). 
2. Ładowanie biblioteki środowisko CoreCLR.
    1. `dlopen("./libcoreclr.so", RTLD_NOW | RTLD_LOCAL);` 
3. Pobierz wskaźników funkcji do przez środowisko CoreCLR `coreclr_initialize`, `coreclr_create_delegate`, `coreclr_execute_assembly`, i `coreclr_shutdown` funkcji przy użyciu`dlsym`
    1. `coreclr_initialize_ptr coreclr_initialize = (coreclr_initialize_ptr)dlsym(coreclrLib, "coreclr_initialize");`
4. Ustawianie właściwości domeny aplikacji (na przykład lista TPA). To jest taka sama jak krok 5 z przepływu mscoree powyżej.
5. Użyj `coreclr_initialize` Aby uruchomić środowisko uruchomieniowe i utworzyć elementu AppDomain. Spowoduje to również utworzenie `hostHandle` wskaźnika, który będzie używany w przyszłości hosting wywołania.
    1. Należy pamiętać, że ta funkcja wykonuje role oba kroki 4 i 6 z poprzednich przepływu pracy. 
6. Użyj jednej `coreclr_execute_assembly` lub `coreclr_create_delegate` do wykonania kodu zarządzanego. Te funkcje są odpowiednikiem w bibliotece mscoree `ExecuteAssembly` i `CreateDelegate` funkcji z kroku 7 poprzedniej przepływu pracy.
7. Użyj `coreclr_shutdown` aby zwolnić elementu AppDomain i zamknąć środowiska uruchomieniowego. 

## <a name="conclusion"></a>Wniosek
Po utworzeniu hosta może być testowana uruchamiając go z poziomu wiersza polecenia, a następnie przekazywanie argumentów (na przykład zarządzaną aplikację do uruchamiania) oczekuje hosta. Podczas określania aplikacji .NET Core dla hosta do uruchomienia, należy użyć pliku .dll, który jest generowany przez `dotnet build`. Pliki wykonywalne utworzonego przez `dotnet publish` niezależne aplikacje są faktycznie domyślne .NET Core hosta (tak, aby aplikację można uruchomić bezpośrednio z poziomu wiersza polecenia w połączeniach scenariuszach); kod użytkownika jest kompilowany do biblioteki dll o takiej samej nazwie. 

Jeśli początkowo działają rzeczy, dokładnie sprawdzić, które *coreclr.dll* jest dostępny w lokalizacji oczekiwany przez hosta, wszystkie wymagane biblioteki Framework znajdują się na liście TPA, która odpowiada tym środowisko CoreCLR bitowości (32 - lub 64-bitowy) jak Host został skompilowany.

Hostowanie środowiska uruchomieniowego .NET Core jest zaawansowanym scenariuszu nie wymagają wielu deweloperów, że dla tych, którzy muszą uruchomić kodu zarządzanego z natywnego procesu lub którzy muszą mieć większą kontrolę nad zachowanie środowiska uruchomieniowego .NET Core, może być bardzo przydatne. Ponieważ .NET Core jest w stanie uruchomić side-by-side ze sobą, jest nawet możliwe utworzenie hosta, na którym zainicjować i rozpocząć wielu wersji środowiska uruchomieniowego .NET Core i wykonaj aplikacje na wszystkich z nich w tym samym procesie. 
