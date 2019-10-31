---
title: Profilery CLR i aplikacje sklepu Windows Store
ms.date: 03/30/2017
dev_langs:
- csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
ms.openlocfilehash: da5942f9a2138a536d158f75a6977d20bf31b41c
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73140388"
---
# <a name="clr-profilers-and-windows-store-apps"></a>Profilery CLR i aplikacje sklepu Windows Store

W tym temacie omówiono, co należy wziąć pod uwagę podczas pisania narzędzi diagnostycznych, które analizują kod zarządzany działający w aplikacji ze sklepu Windows. Zawiera również wskazówki pozwalające modyfikować istniejące narzędzia programistyczne, aby nadal działały po uruchomieniu ich w aplikacjach ze sklepu Windows. Aby zrozumieć te informacje, najlepszym rozwiązaniem jest zapoznanie się z interfejsem API profilowania środowiska uruchomieniowego języka wspólnego. ten interfejs API jest już używany w narzędziu diagnostycznym, które działa prawidłowo w przypadku aplikacji klasycznych systemu Windows. użytkownik chce teraz modyfikować narzędzie Aby działać poprawnie z aplikacjami ze sklepu Windows.

## <a name="introduction"></a>Wprowadzenie

Jeśli zostało to wykonane po akapicie wprowadzającym, zapoznaj się z interfejsem API profilowania środowiska CLR. Zapisałeś już narzędzie diagnostyczne, które dobrze działa w odniesieniu do zarządzanych aplikacji klasycznych. Teraz chcesz wiedzieć się, co należy zrobić, aby narzędzie działało z zarządzaną aplikacją ze sklepu Windows. Być może podjęto już próbę wykonania tej pracy i wykryto, że nie jest to proste zadanie. W rzeczywistości istnieje kilka kwestii, które mogą nie być oczywiste dla wszystkich deweloperów narzędzi. Na przykład:

- Aplikacje ze sklepu Windows działają w kontekście z poważnie ograniczonymi uprawnieniami.

- Pliki metadanych systemu Windows mają unikatowe cechy w porównaniu z tradycyjnymi modułami zarządzanymi.

- Aplikacje ze sklepu Windows mają wykonywać zawieszanie się, gdy działa interaktywny.

- Mechanizmy komunikacji między procesami mogą przestać działać z różnych powodów.

W tym temacie wymieniono zagadnienia, z którymi należy się zapoznać, oraz sposób ich poprawnego działania.

Jeśli jesteś nowym interfejsem API profilowania CLR, przejdź do zasobów na końcu tego tematu, aby znaleźć lepsze informacje wprowadzające.

Szczegółowe informacje na temat konkretnych interfejsów API systemu Windows i sposobu ich użycia również znajdują się poza zakresem tego tematu. Zapoznaj się z tym tematem i przejdź do witryny MSDN, aby dowiedzieć się więcej o dowolnych interfejsach API systemu Windows.

## <a name="architecture-and-terminology"></a>Architektura i terminologia

Zazwyczaj narzędzie diagnostyczne ma architekturę podobną do pokazanej na poniższej ilustracji. Używa ona terminu "Profiler", ale wiele takich narzędzi najlepiej sprawdza się poza typowym profilem wydajności lub pamięci w takich obszarach jak pokrycie kodu, struktury obiektów makiety, debugowanie czasu podróży, monitorowanie aplikacji i tak dalej. Dla uproszczenia ten temat będzie nadal odwoływał się do wszystkich tych narzędzi jako profilowanych.

W tym temacie jest używana następująca terminologia:

**Aplikacja**

Jest to aplikacja, która analizuje Profiler. Zazwyczaj deweloper tej aplikacji korzysta teraz z profilera, aby pomóc w diagnozowaniu problemów z aplikacją. Tradycyjnie ta aplikacja będzie aplikacją klasyczną systemu Windows, ale w tym temacie przeglądamy aplikacje ze sklepu Windows.

**Biblioteka DLL profilera**

Jest to składnik, który ładuje do przestrzeni procesu analizowanej aplikacji. Ten składnik, znany również jako Profiler "Agent", implementuje interfejs [ICorProfilerCallback](icorprofilercallback-interface.md)[ICorProfilerCallback Interface](icorprofilercallback-interface.md)(2, 3 itp.) i używa interfejsów [ICorProfilerInfo](icorprofilerinfo-interface.md)(2, 3 itp.) do zbierania danych dotyczących przeanalizowane aplikacje i potencjalnie modyfikują aspekty zachowania aplikacji.

**Interfejs użytkownika profilera**

Jest to aplikacja klasyczna, z którą korzysta użytkownik profilera. Jest on odpowiedzialny za wyświetlanie stanu aplikacji dla użytkownika i umożliwienie użytkownikowi kontroli zachowania przeanalizowanej aplikacji. Ten składnik jest zawsze uruchamiany we własnej przestrzeni procesu, oddzielony od przestrzeni procesowej profilowanej aplikacji. Interfejs użytkownika profilera może również działać jako "Dołączanie wyzwalacza", który jest procesem wywołującym metodę [ICLRProfiling:: AttachProfiler —](iclrprofiling-attachprofiler-method.md) , aby spowodować, że analizowana aplikacja załadowała plik DLL profilera w tych przypadkach, w których nie załadowano pliku DLL profilera podczas uruchamiania.

> [!IMPORTANT]
> Interfejs użytkownika profilera powinien pozostać w aplikacji klasycznej systemu Windows, nawet jeśli służy do kontrolowania i raportowania w aplikacji ze sklepu Windows. Nie powinno być możliwe spakowanie i dostarczenie narzędzia diagnostycznego w Sklepie Windows. Narzędzie musi wykonać czynności, które nie mogą wykonać aplikacje ze sklepu Windows, a wiele z nich znajduje się w interfejsie użytkownika profilera.

W tym dokumencie przykładowy kod założono, że:

- Plik DLL profilera jest zapisywana C++w, ponieważ musi być NATYWNą biblioteką DLL, zgodnie z wymaganiami interfejsu API profilowania środowiska CLR.

- Interfejs użytkownika profilera jest zapisany C#. Nie jest to konieczne, ale ponieważ nie ma wymagań dotyczących języka dla procesu interfejsu użytkownika profilera, dlaczego nie należy wybierać języka, który jest zwięzły i prosty?

### <a name="windows-rt-devices"></a>Urządzenia z systemem Windows RT

Urządzenia z systemem Windows RT są całkowicie zablokowane. Do takich urządzeń nie można ładować plików innych firm. Ten dokument koncentruje się na komputerach z systemem Windows 8.

## <a name="consuming-windows-runtime-apis"></a>Używanie środowisko wykonawcze systemu Windows interfejsów API

W kilku scenariuszach omówionych w poniższych sekcjach aplikacja klasyczna interfejsu użytkownika profilera musi korzystać z nowych interfejsów API środowisko wykonawcze systemu Windows. Zapoznaj się z dokumentacją, aby dowiedzieć się, które środowisko wykonawcze systemu Windows interfejsy API mogą być używane z aplikacji klasycznych, oraz czy ich zachowanie jest różne w przypadku wywołania z aplikacji klasycznych i aplikacji ze sklepu Windows.

Jeśli interfejs użytkownika profilera jest zapisywana w kodzie zarządzanym, należy wykonać kilka kroków, aby ułatwić korzystanie z tych środowisko wykonawcze systemu Windows interfejsów API. Aby uzyskać więcej informacji, zobacz artykuł dotyczący [zarządzanych aplikacji klasycznych i środowisko wykonawcze systemu Windows](https://go.microsoft.com/fwlink/?LinkID=271858) .

## <a name="loading-the-profiler-dll"></a>Ładowanie pliku DLL profilera

W tej sekcji opisano sposób, w jaki interfejs użytkownika profilera powoduje załadowanie biblioteki DLL profilera przez aplikację ze sklepu Windows. Kod omówiony w tej sekcji należy do aplikacji klasycznej interfejsu użytkownika profilera i w związku z tym obejmuje korzystanie z interfejsów API systemu Windows, które są bezpieczne dla aplikacji klasycznych, ale niekoniecznie są bezpieczne dla aplikacji ze sklepu Windows.

Interfejs użytkownika profilera może spowodować załadowanie biblioteki DLL profilera do obszaru procesu aplikacji na dwa sposoby:

- Przy uruchamianiu aplikacji, zgodnie z ustawieniami zmiennych środowiskowych.

- Po dołączeniu do aplikacji po zakończeniu uruchamiania, wywołując metodę [ICLRProfiling:: AttachProfiler —](iclrprofiling-attachprofiler-method.md) .

Jednym z pierwszych przeszkodyu będzie pobranie i załadowanie pliku DLL profilera w celu poprawnego działania z aplikacjami ze sklepu Windows. Obie formy ładowania dzielą kilka specjalnych zagadnień wspólnych, więc zacznijmy od nich.

### <a name="common-considerations-for-startup-and-attach-loads"></a>Typowe zagadnienia dotyczące uruchamiania i dołączania ładunków

**Podpisywanie biblioteki DLL profilera**

Gdy system Windows podejmie próbę załadowania biblioteki DLL profilera, sprawdza, czy biblioteka DLL profilera jest prawidłowo podpisana. W przeciwnym razie ładowanie nie powiedzie się domyślnie. Istnieją dwa sposoby wykonania tej czynności:

- Upewnij się, że Twój plik DLL profilera jest podpisany.

- Poinformuj użytkownika, że muszą zainstalować licencję dewelopera na swoim komputerze z systemem Windows 8 przed skorzystaniem z narzędzia. Można to zrobić automatycznie z poziomu programu Visual Studio lub ręcznie z poziomu wiersza polecenia. Aby uzyskać więcej informacji, zobacz [Uzyskiwanie licencji dewelopera](https://docs.microsoft.com/previous-versions/windows/apps/hh974578(v=win.10)).

**Uprawnienia systemu plików**

Aplikacja ze sklepu Windows musi mieć uprawnienia do ładowania i uruchamiania pliku DLL profilera z lokalizacji w systemie plików, w którym residesBy domyślnie, aplikacja ze sklepu Windows nie ma takich uprawnień w przypadku większości katalogów i wszelkie nieudane próby załadowania biblioteki DLL profilera w dzienniku zdarzeń aplikacji systemu Windows zostanie wytworzony wpis podobny do przedstawionego poniżej:

```output
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].
```

Ogólnie rzecz biorąc, aplikacje ze sklepu Windows mogą uzyskiwać dostęp do ograniczonego zestawu lokalizacji na dysku. Każda aplikacja ze sklepu Windows może uzyskać dostęp do swoich własnych folderów danych aplikacji, a także kilku innych obszarów w systemie plików, dla których przyznano dostęp do wszystkich aplikacji ze sklepu Windows. Najlepszym rozwiązaniem jest zainstalowanie biblioteki DLL profilera i jej zależności w obszarze pliki programu lub Program Files (x86), ponieważ wszystkie aplikacje ze sklepu Windows domyślnie mają uprawnienia do odczytu i wykonywania.

### <a name="startup-load"></a>Ładowanie uruchamiania

Zazwyczaj w aplikacji klasycznej interfejs użytkownika profilera jest monitowany o ponowne uruchomienie narzędzia Profiler DLL przez zainicjowanie bloku środowiska zawierającego wymagane zmienne środowiskowe interfejsu API profilowania CLR (tj. `COR_PROFILER`, `COR_ENABLE_PROFILING`i `COR_PROFILER_PATH`), a następnie tworząc nowe Przetwarzaj przy użyciu tego bloku środowiska. Te same wartości mają wartość prawda w przypadku aplikacji ze sklepu Windows, ale te mechanizmy są różne.

**Nie uruchamiaj z podwyższonym poziomem uprawnień**

Jeśli proces próbuje zduplikować proces aplikacji ze sklepu Windows w trybie B, proces A powinien być uruchamiany na poziomie integralności średniej, A nie na poziomie wysokiej integralności (czyli nie z podwyższonym poziomem uprawnień). Oznacza to, że interfejs użytkownika profilera powinien działać na poziomie średniej integralności lub trzeba utworzyć inny proces stacjonarny na średnim poziomie integralności, aby zachować ostrożność podczas uruchamiania aplikacji ze sklepu Windows.

**Wybieranie aplikacji ze sklepu Windows do profilowania**

Najpierw należy polecić użytkownikowi profilera, który ma zostać uruchomiony aplikacja ze sklepu Windows. W przypadku aplikacji klasycznych może być widoczne okno dialogowe przeglądania plików, a użytkownik powinien znaleźć i wybrać plik. exe. Jednak aplikacje ze sklepu Windows różnią się, a korzystanie z okna dialogowego przeglądania nie ma sensu. Zamiast tego lepiej jest pokazać użytkownikowi listę aplikacji ze sklepu Windows zainstalowanych dla danego użytkownika.

Aby wygenerować tę listę, można użyć klasy <xref:Windows.Management.Deployment.PackageManager>. `PackageManager` jest klasą środowisko wykonawcze systemu Windows, która jest dostępna dla aplikacji klasycznych i w rzeczywistości jest dostępna *tylko* dla aplikacji klasycznych.

Poniższy przykład kodu z hipotetycznego interfejsu użytkownika profilera zapisaną jako aplikacja klasyczna C# w programie używa `PackageManager` do wygenerowania listy aplikacji systemu Windows:

```csharp
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();
PackageManager packageManager = new PackageManager();
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);
```

**Określanie niestandardowego bloku środowiska**

Nowy interfejs COM [IPackageDebugSettings](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings), pozwala dostosować zachowanie aplikacji ze sklepu Windows, aby ułatwić korzystanie z niektórych form diagnostyki. Jedna z jej metod, [EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), umożliwia przekazanie bloku środowiska do aplikacji ze sklepu Windows, gdy zostanie ona uruchomiona, oraz innych użytecznych efektów, takich jak wyłączenie automatycznego zawieszenia procesów. Blok środowiska jest istotny, ponieważ jest to miejsce, w którym należy określić zmienne środowiskowe (`COR_PROFILER`, `COR_ENABLE_PROFILING`i `COR_PROFILER_PATH)`) używane przez środowisko CLR do załadowania pliku DLL profilera.

Rozważmy następujący fragment kodu:

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, debuggerCommandLine,
                                                                 (IntPtr)fixedEnvironmentPzz);
```

Istnieje kilka elementów, które trzeba uzyskać po prawej stronie:

- `packageFullName` można określić podczas iteracji pakietów i `package.Id.FullName`.

- `debuggerCommandLine` jest nieco bardziej interesujący. Aby przekazać blok środowiska niestandardowego do aplikacji ze sklepu Windows, należy napisać własny debuger fikcyjny uproszczony. System Windows duplikuje aplikację ze sklepu Windows, a następnie dołącza debuger, uruchamiając debuger przy użyciu wiersza polecenia, takiego jak w poniższym przykładzie:

    ```console
    MyDummyDebugger.exe -p 1336 -tid 1424
    ```

     gdzie `-p 1336` oznacza, że aplikacja ze sklepu Windows ma proces o IDENTYFIKATORze 1336, a `-tid 1424` 1424 oznacza wątek, który jest zawieszony. Debuger fikcyjny analizuje ThreadID z wiersza polecenia, wznawia ten wątek, a następnie kończy działanie.

     Oto przykładowy C++ kod, aby to zrobić (należy dodać sprawdzanie błędów):

    ```cpp
    int wmain(int argc, wchar_t* argv[])
    {
        // …
        // Parse command line here
        // …

        HANDLE hThread = OpenThread(THREAD_SUSPEND_RESUME,
                                                                  FALSE /* bInheritHandle */, nThreadID);
        ResumeThread(hThread);
        CloseHandle(hThread);
        return 0;
    }
    ```

     Należy wdrożyć ten debuger fikcyjny jako część instalacji narzędzia diagnostycznego, a następnie określić ścieżkę do tego debugera w parametrze `debuggerCommandLine`.

**Uruchamianie aplikacji ze sklepu Windows**

Na koniec zostanie uruchomiona aplikacja ze sklepu Windows. Jeśli jeszcze tego nie zrobiono, można zauważyć, że proces [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) nie polega na tym, że proces tworzenia aplikacji ze sklepu Windows. Zamiast tego należy użyć metody [IApplicationActivationManager:: ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) . Aby to zrobić, należy uzyskać identyfikator modelu użytkownika aplikacji dla aplikacji ze sklepu Windows, która jest uruchamiana. Oznacza to, że należy wykonać nieco przeszukiwanie stosów za pośrednictwem manifestu.

Podczas iteracji pakietów (zobacz "Wybieranie aplikacji ze sklepu Windows do profilowania" w sekcji [ładowania początkowego](#startup-load) wcześniej) chcesz pobrać zestaw aplikacji zawartych w manifeście bieżącego pakietu:

```csharp
string manifestPath = package.InstalledLocation.Path + "\\AppxManifest.xml";

AppxPackaging.IStream manifestStream;
SHCreateStreamOnFileEx(
                    manifestPath,
                    0x00000040,     // STGM_READ | STGM_SHARE_DENY_NONE
                    0,              // file creation attributes
                    false,          // fCreate
                    null,           // reserved
                    out manifestStream);

IAppxManifestReader manifestReader = appxFactory.CreateManifestReader(manifestStream);

IAppxManifestApplicationsEnumerator appsEnum = manifestReader.GetApplications();
```

Tak, jeden pakiet może mieć wiele aplikacji, a każda aplikacja ma własny identyfikator modelu użytkownika aplikacji. Należy więc polecić użytkownikowi, który aplikacja ma profil, i uzyskać identyfikator modelu użytkownika aplikacji z tej konkretnej aplikacji:

```csharp
while (appsEnum.GetHasCurrent() != 0)
{
    IAppxManifestApplication app = appsEnum.GetCurrent();
    string appUserModelId = app.GetAppUserModelId();
    //...
}
```

Na koniec masz teraz, co musisz zrobić, aby uruchomić aplikację ze sklepu Windows:

```csharp
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);
```

**Pamiętaj, aby wywołać DisableDebugging**

Po wywołaniu [IPackageDebugSettings:: EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging), należy oczyścić, aby wyczyścić się po sobie przez wywołanie metody [IPackageDebugSettings::D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) , dlatego należy się upewnić, że w przypadku przekroczenia sesji profilowania.

### <a name="attach-load"></a>Dołącz obciążenie

Gdy interfejs użytkownika profilera chce dołączyć swój plik DLL profilera do aplikacji, która została już uruchomiona, używa [ICLRProfiling:: AttachProfiler —](iclrprofiling-attachprofiler-method.md). Te same wartości mają wartość prawda w przypadku aplikacji ze sklepu Windows. Oprócz często wymienionych wcześniej zagadnień upewnij się, że docelowa aplikacja ze sklepu Windows nie jest wstrzymana.

**EnableDebugging**

Tak jak w przypadku ładowania uruchomienia, wywołaj metodę [IPackageDebugSettings:: EnableDebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-enabledebugging) . Nie jest on potrzebny do przekazywania bloku środowiska, ale jest wymagana jedna z jego innych funkcji: wyłączanie automatycznego zawieszania procesów. W przeciwnym razie, gdy interfejs użytkownika profilera wywoła [AttachProfiler —](iclrprofiling-attachprofiler-method.md), może zostać zawieszona docelowa aplikacja ze sklepu Windows. W rzeczywistości jest to możliwe, jeśli użytkownik będzie teraz korzystać z interfejsu użytkownika profilera, a aplikacja ze sklepu Windows nie jest aktywna na żadnym ekranie użytkownika. A jeśli aplikacja ze sklepu Windows jest zawieszona, nie będzie w stanie odpowiedzieć na sygnał, który jest wysyłany przez środowisko CLR w celu dołączenia biblioteki DLL profilera.

Możesz to zrobić w następujący sposób:

```csharp
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();
pkgDebugSettings.EnableDebugging(packageFullName, null /* debuggerCommandLine */,
                                                                 IntPtr.Zero /* environment */);
```

Jest to to samo wywołanie dla przypadku ładowania początkowego, z wyjątkiem tego, że nie określono wiersza polecenia debugera ani bloku środowiska.

**DisableDebugging**

Jak zawsze, nie zapomnij wywołać [IPackageDebugSettings::D isabledebugging](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-ipackagedebugsettings-disabledebugging) po zakończeniu sesji profilowania.

## <a name="running-inside-the-windows-store-app"></a>Uruchamianie w aplikacji ze sklepu Windows

Dzięki temu aplikacja ze sklepu Windows ostatecznie załadowała Twój plik DLL profilera. Teraz Biblioteka DLL profilera musi być w sposób odtwarzany przy użyciu różnych reguł wymaganych przez aplikacje ze sklepu Windows, w tym interfejsów API, które są dozwolone, i sposobu uruchamiania z ograniczonymi uprawnieniami.

### <a name="stick-to-the-windows-store-app-apis"></a>Doklej do interfejsów API aplikacji ze sklepu Windows

Podczas przeglądania interfejsu API systemu Windows należy zauważyć, że każdy interfejs API jest udokumentowany jako mający zastosowanie do aplikacji klasycznych, aplikacji ze sklepu Windows lub obu tych funkcji. Na przykład sekcja **wymagania** dokumentacji dla funkcji [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) wskazuje, że funkcja ma zastosowanie tylko do aplikacji klasycznych. Z kolei funkcja [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) jest dostępna dla aplikacji klasycznych i aplikacji ze sklepu Windows.

Podczas tworzenia biblioteki DLL profilera należy traktować ją jako aplikację ze sklepu Windows i używać tylko interfejsów API, które są udokumentowane jako dostępne dla aplikacji ze sklepu Windows. Analizuj zależności (na przykład można uruchomić `link /dump /imports` względem biblioteki DLL profilera w celu przeprowadzenia inspekcji), a następnie przeszukać w dokumencie dokumenty, które z zależności są prawidłowe i które nie są. W większości przypadków naruszenia można naprawić, po prostu zastępując je nowszą formą interfejsu API, który jest udokumentowany jako bezpieczny (na przykład zastępując [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) with [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).

Można zauważyć, że biblioteka DLL profilera wywołuje niektóre interfejsy API, które są stosowane tylko do aplikacji klasycznych, a mimo to działa nawet wtedy, gdy biblioteka DLL profilera jest załadowana w aplikacji ze sklepu Windows. Należy pamiętać, że jest ryzykowne używanie dowolnego interfejsu API, który nie jest udokumentowany do użycia z aplikacjami ze sklepu Windows w bibliotece DLL profilera, gdy jest ładowany do procesu aplikacji ze sklepu Windows:

- Takie interfejsy API nie są gwarantowane, gdy są wywoływane w unikatowym kontekście, w którym działają aplikacje ze sklepu Windows.

- Takie interfejsy API mogą nie funkcjonować spójnie w przypadku wywołania z różnych procesów aplikacji ze sklepu Windows.

- Takie interfejsy API mogą pozornie działać w aplikacjach ze sklepu Windows w bieżącej wersji systemu Windows, ale mogą one zostać zerwane lub wyłączone w przyszłych wersjach systemu Windows.

Najlepszym rozwiązaniem jest rozwiązanie wszystkich naruszeń i uniknięcie ryzyka.

Może się okazać, że absolutnie nie można wykonać bez określonego interfejsu API i nie można znaleźć zastąpienia odpowiedniego dla aplikacji ze sklepu Windows. W takim przypadku co najmniej:

- Przetestuj, przetestuj i przetestuj żywe światło dzienne z użycia tego interfejsu API.

- Informacje o tym, że interfejs API może nagle przerwać lub zniknąć, jeśli jest wywoływany z aplikacji ze sklepu Windows w przyszłych wersjach systemu Windows. Nie będzie to uznawane za problemy ze zgodnością przez firmę Microsoft, a korzystanie z nich nie jest priorytetem.

### <a name="reduced-permissions"></a>Ograniczone uprawnienia

Jest to poza zakresem tego tematu, aby wyświetlić listę wszystkich sposobów, w których uprawnienia aplikacji ze sklepu Windows różnią się od aplikacji klasycznych. Chociaż zachowanie będzie się różnić za każdym razem, gdy biblioteka DLL profilera (w przypadku załadowania do aplikacji ze sklepu Windows w porównaniu z aplikacją klasyczną) próbuje uzyskać dostęp do wszystkich zasobów. System plików jest najbardziej typowym przykładem. Istnieje jednak kilka miejsc na dysku, do których dostęp ma dana aplikacja ze sklepu Windows (zobacz dostęp do [pliku i uprawnienia (środowisko wykonawcze systemu Windows aplikacje](https://docs.microsoft.com/previous-versions/windows/apps/hh967755(v=win.10))), a Twój plik DLL profilera będzie objęty tymi samymi ograniczeniami. Dokładnie Przetestuj swój kod.

### <a name="inter-process-communication"></a>Komunikacja między procesami

Jak pokazano na diagramie na początku tego dokumentu, biblioteka DLL profilera (załadowana do obszaru procesu aplikacji ze sklepu Windows) prawdopodobnie będzie musiała komunikować się z interfejsem użytkownika profilera (uruchomionym w oddzielnym obszarze procesu aplikacji klasycznych) za pomocą własnego niestandardowego procesu kanał komunikacji (IPC). Interfejs użytkownika profilera wysyła sygnały do pliku DLL profilera, aby zmodyfikować jego zachowanie, a plik DLL profilera wysyła dane z przeanalizowanej aplikacji ze sklepu Windows z powrotem do interfejsu użytkownika profilera na potrzeby przetwarzania końcowego i wyświetlania użytkownikowi profilera.

Większość plików musi współpracować w ten sposób, ale wybór mechanizmów IPC jest bardziej ograniczony, gdy plik DLL profilera jest ładowany do aplikacji ze sklepu Windows. Na przykład nazwane potoki nie są częścią zestawu SDK aplikacji ze sklepu Windows, więc nie można ich używać.

Jednak oczywiście pliki nadal znajdują się w, chociaż w bardziej ograniczony sposób. Dostępne są również zdarzenia.

**Komunikacja za pośrednictwem plików**

Większość danych będzie prawdopodobnie przebiegać między biblioteką DLL profilera a interfejsem użytkownika profilera za pośrednictwem plików. Klucz polega na wybraniu lokalizacji plików, którą Biblioteka DLL profilera (w kontekście aplikacji ze sklepu Windows) i interfejsem użytkownika profilera mają dostęp do odczytu i zapisu. Na przykład ścieżka folderu tymczasowego to lokalizacja, do której można uzyskać dostęp zarówno do biblioteki DLL profilera, jak i interfejsu użytkownika profilera, ale żaden inny pakiet aplikacji do sklepu Windows nie może uzyskać dostępu (w ten sposób osłona zawiera informacje z innych pakietów aplikacji ze sklepu Windows).

Zarówno interfejs użytkownika profilera, jak i plik DLL profilera mogą określać tę ścieżkę niezależnie. Interfejs użytkownika profilera, gdy wykonuje iterację we wszystkich pakietach zainstalowanych dla bieżącego użytkownika (Zobacz przykładowy kod wcześniej), uzyskuje dostęp do klasy `PackageId`, z której można pobrać kod podobny do tego fragmentu kodu. (Zawsze sprawdzanie błędów jest pomijane dla zwięzłości).

```csharp
// C# code for the Profiler UI.
ApplicationData appData =
    ApplicationDataManager.CreateForPackageFamily(
        packageId.FamilyName);

tempDir = appData.TemporaryFolder.Path;
```

W tym czasie Biblioteka DLL profilera może być zasadniczo taka sama, chociaż może łatwiej uzyskać dostęp do klasy <xref:Windows.Storage.ApplicationData> przy użyciu właściwości [ApplicationData. Current](xref:Windows.Storage.ApplicationData.Current%2A) .

**Komunikacja za pośrednictwem zdarzeń**

Jeśli chcesz utworzyć prostą semantykę sygnalizowania między interfejsem użytkownika profilera i biblioteką DLL profilera, możesz użyć zdarzeń w aplikacjach ze sklepu Windows, a także aplikacji klasycznych.

Z poziomu biblioteki DLL profilera możesz po prostu wywołać funkcję [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) , aby utworzyć nazwane zdarzenie z dowolną nazwą, którą lubisz. Na przykład:

```cpp
// Profiler DLL in Windows Store app (C++).
CreateEventEx(
    NULL,  // Not inherited
    "MyNamedEvent"
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */
    EVENT_ALL_ACCESS);
```

Interfejs użytkownika profilera musi znaleźć to nazwane zdarzenie w przestrzeni nazw aplikacji ze sklepu Windows. Na przykład interfejs użytkownika profilera może wywoływać [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa), określając nazwę zdarzenia jako

`AppContainerNamedObjects\<acSid>\MyNamedEvent`

`<acSid>` to identyfikator SID aplikacji do sklepu Windows. W poprzedniej sekcji tego tematu pokazano, jak wykonać iterację pakietów zainstalowanych dla bieżącego użytkownika. Z tego przykładowego kodu można uzyskać packageId. I z packageId można uzyskać `<acSid>` z kodem podobnym do poniższego:

```csharp
IntPtr acPSID;
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);

string acSid;
ConvertSidToStringSid(acPSID, out acSid);

string acDir;
GetAppContainerFolderPath(acSid, out acDir);
```

### <a name="no-shutdown-notifications"></a>Brak powiadomień o zamknięciu

Podczas pracy w aplikacji ze sklepu Windows Profiler DLL nie powinien polegać na [ICorProfilerCallback:: Shutdown](icorprofilercallback-shutdown-method.md) lub nawet [DllMain](/windows/desktop/Dlls/dllmain) (z `DLL_PROCESS_DETACH`) wywoływanym w celu powiadomienia biblioteki DLL profilera, że aplikacja ze sklepu Windows zostanie zamknięta. W rzeczywistości należy się spodziewać, że nigdy nie będą wywoływane. W przeszłości wiele bibliotek DLL profilera użyła tych powiadomień jako wygodnych miejsc do opróżniania pamięci podręcznych na dysk, zamykania plików, wysyłania powiadomień z powrotem do interfejsu użytkownika profilera itp. Jednak teraz Twój plik DLL profilera musi być zorganizowany nieco inaczej.

Biblioteka DLL profilera powinna rejestrować informacje w miarę ich tworzenia. Ze względu na wydajność można utworzyć wsadowe informacje w pamięci i opróżnić je na dysk, gdy partia rośnie w rozmiarze poprzedzającym pewien próg. Należy jednak założyć, że wszelkie informacje, które nie zostały jeszcze opróżnione na dysk, mogą zostać utracone. Oznacza to, że warto wybrać próg progu, a interfejs użytkownika profilera musi być zaostrzony, aby można było zająć się niekompletnymi informacjami zapisanymi przez profiler DLL.

## <a name="windows-runtime-metadata-files"></a>Pliki metadanych środowisko wykonawcze systemu Windows

Ten dokument znajduje się poza zakresem tego dokumentu, aby szczegółowo zapoznać się z plikami metadanych środowisko wykonawcze systemu Windows (WinMD). Ta sekcja jest ograniczona do sposobu, w jaki interfejs API profilowania CLR reaguje, gdy pliki WinMD są ładowane przez aplikację ze sklepu Windows, która jest analizowany przez profiler DLL.

### <a name="managed-and-non-managed-winmds"></a>Zarządzane i niezarządzane WinMD

Jeśli deweloper używa programu Visual Studio do utworzenia nowego projektu składnika środowisko wykonawcze systemu Windows, kompilacja tego projektu tworzy plik WinMD, który opisuje metadane (typy opisów klas, interfejsów itp.) utworzonych przez dewelopera. Jeśli ten projekt jest projektem języka zarządzanego, który jest C# pisany w języku lub VB, ten sam plik WinMD również zawiera implementację tych typów (oznacza to, że zawiera wszystkie Il skompilowane z kodu źródłowego dewelopera). Takie pliki są znane jako zarządzane pliki WinMD. Są one interesujące w tym, że zawierają zarówno metadane środowisko wykonawcze systemu Windows, jak i podstawową implementację.

W przeciwieństwie do tego, czy deweloper tworzy projekt składnika środowisko wykonawcze systemu Windows C++dla programu, kompilacja tego projektu tworzy plik winmd, który zawiera tylko metadane, a implementacja zostanie skompilowana do oddzielnej NATYWNEJ biblioteki DLL. Podobnie pliki WinMD dostarczane w Windows SDK zawierają tylko metadane, a implementacja została skompilowana do oddzielnych natywnych bibliotek DLL, które są dostarczane jako część systemu Windows.

Poniższe informacje dotyczą zarówno zarządzanych WinMD, które zawierają metadane i implementacje, jak i do niezarządzanych WinMD, które zawierają tylko metadane.

### <a name="winmd-files-look-like-clr-modules"></a>Pliki WinMD wyglądają jak moduły CLR

W miarę jak środowisko CLR, wszystkie pliki WinMD są modułami. W związku z tym interfejs API profilowania środowiska CLR nakazuje usłudze Profiler DLL, gdy pliki WinMD i ich ModuleIDs są w taki sam sposób jak w przypadku innych modułów zarządzanych.

Biblioteka DLL profilera może rozróżnić pliki WinMD z innych modułów, wywołując metodę [ICorProfilerInfo3:: GetModuleInfo2 —](icorprofilerinfo3-getmoduleinfo2-method.md) i sprawdzając parametr wyjściowy `pdwModuleFlags` dla flagi [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) . (Ustawienie to i tylko wtedy, gdy ModuleID reprezentuje WinMD).

### <a name="reading-metadata-from-winmds"></a>Odczytywanie metadanych z WinMD

Pliki WinMD, takie jak regularne moduły, zawierają metadane, które można odczytać za pośrednictwem [interfejsów API metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md). Jednak środowisko CLR mapuje typy środowisko wykonawcze systemu Windows na typy .NET Framework podczas odczytywania plików WinMD, dzięki czemu deweloperzy, którzy programu w kodzie zarządzanym i zużywają plik WinMD, mogą mieć bardziej naturalne środowisko programistyczne. Przykłady tych mapowań można znaleźć w temacie [.NET Framework support for Windows Store Apps i środowisko wykonawcze systemu Windows](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).

Który widok zostanie pobrany przez profiler, gdy używa interfejsów API metadanych: widoku RAW środowisko wykonawcze systemu Windows lub zamapowanego widoku .NET Framework?  Odpowiedź: to wszystko.

Po wywołaniu metody [ICorProfilerInfo:: GetModuleMetaData —](icorprofilerinfo-getmodulemetadata-method.md) w WinMD w celu uzyskania interfejsu metadanych, takiego jak [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), można ustawić [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) w parametrze `dwOpenFlags`, aby wyłączyć to mapowanie. W przeciwnym razie mapowanie zostanie włączone. Zwykle program profilujący zachowa mapowanie, dzięki czemu ciągi, które będą pobierane przez program Profiler DLL z metadanych WinMD (na przykład nazwy typów) będą wyglądały znajomo i naturalny dla użytkownika profilera.

### <a name="modifying-metadata-from-winmds"></a>Modyfikowanie metadanych z WinMD

Modyfikowanie metadanych w WinMD nie jest obsługiwane. Jeśli wywołasz metodę [ICorProfilerInfo:: GetModuleMetaData —](icorprofilerinfo-getmodulemetadata-method.md) dla pliku winmd i określisz [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) w parametrze `dwOpenFlags` lub poproszą o zapisywalny interfejs metadanych, taki jak [IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData —](icorprofilerinfo-getmodulemetadata-method.md) zakończy się niepowodzeniem. Jest to szczególnie ważne w przypadku, gdy pliki są zapisywane w języku IL, co wymaga modyfikacji metadanych do obsługi Instrumentacji (na przykład w celu dodania siebie lub nowych metod). Dlatego należy najpierw wyszukać [COR_PRF_MODULE_WINDOWS_RUNTIME](cor-prf-module-flags-enumeration.md) (zgodnie z opisem w poprzedniej sekcji) i zrezygnować z monitowania o zapisywalne interfejsy metadanych na takich modułach.

### <a name="resolving-assembly-references-with-winmds"></a>Rozpoznawanie odwołań do zestawów za pomocą WinMD

Wiele profilowań musi ręcznie rozpoznać odwołania do metadanych, aby pomóc w instrumentacji lub inspekcji typów. Takie składowe muszą mieć świadomość, jak środowisko CLR rozpoznaje odwołania do zestawów wskazujące WinMD, ponieważ te odwołania są rozwiązane w zupełnie inny sposób niż standardowe odwołania do zestawu.

## <a name="memory-profilers"></a>Prepliker pamięci

Moduł wyrzucania elementów bezużytecznych i zarządzanej sterty różni się zasadniczo w aplikacji ze sklepu Windows i aplikacji klasycznej. Jednak istnieją pewne delikatne różnice, które muszą być świadome dla autorów profilera.

### <a name="forcegc-creates-a-managed-thread"></a>ForceGC — tworzy wątek zarządzany

Podczas profilowania pamięci Biblioteka DLL programu Profiler zazwyczaj tworzy oddzielny wątek, z którego można wywołać metodę [metody ForceGC —](icorprofilerinfo-forcegc-method.md) . Nic nie dotyczy. Jednak może być zaskakujące, że wykonywanie operacji wyrzucania elementów bezużytecznych w aplikacji ze sklepu Windows może przetworzyć wątek w zarządzanym wątku (na przykład dla tego wątku zostanie utworzony ThreadID API profilowania).

Aby zrozumieć konsekwencje tego działania, ważne jest zrozumienie różnic między wywołań synchronicznych i asynchronicznych zgodnie z definicją w interfejsie API profilowania CLR. Należy zauważyć, że jest to bardzo różne od koncepcji wywołań asynchronicznych w aplikacjach ze sklepu Windows. Zapoznaj się z wpisem w blogu [dlaczego CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) , aby uzyskać więcej informacji.

Odpowiednim punktem jest to, że wywołania wykonane w wątkach utworzonych przez profiler są zawsze uznawane za synchroniczne, nawet jeśli te wywołania pochodzą z zewnątrz implementacji jednej z metod [ICORPROFILERCALLBACK](icorprofilercallback-interface.md) biblioteki profilera. Co najmniej, które były używane w przypadku. Teraz, gdy środowisko CLR przełączyło wątek profilera do zarządzanego wątku ze względu na wywołanie [metody ForceGC —](icorprofilerinfo-forcegc-method.md), ten wątek nie jest już traktowany jako wątek profilera. W związku z tym środowisko CLR wymusza bardziej rygorystyczną definicję, która jest zgodna z elementem synchronicznym dla tego wątku — w związku z tym, że wywołanie musi pochodzić od jednej z metod [ICorProfilerCallback](icorprofilercallback-interface.md) biblioteki DLL profilera, aby kwalifikować się jako synchroniczne.

Co to znaczy? Większość metod [ICorProfilerInfo](icorprofilerinfo-interface.md) jest bezpieczna wyłącznie do wywołania synchronicznego i natychmiast się nie powiedzie. Dlatego jeśli biblioteka DLL programu Profiler ponownie używa wątku [metody ForceGC —](icorprofilerinfo-forcegc-method.md) dla innych wywołań zwykle wykonywanych na wątkach utworzonych przez profiler (na przykład do [RequestProfilerDetach](icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT —](icorprofilerinfo4-requestrejit-method.md)lub [RequestRevert —](icorprofilerinfo4-requestrevert-method.md)), wystąpi problem . Nawet bezpieczna asynchronicznie funkcja, taka jak [DoStackSnapshot —](icorprofilerinfo2-dostacksnapshot-method.md) , ma specjalne reguły w przypadku wywołania z zarządzanych wątków. (Zobacz wpis w blogu szczegółowe informacje o [stosie: podstawowe i poza nim,](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) Aby uzyskać więcej informacji).

W związku z tym zaleca się, aby każdy wątek utworzony przez program Profiler DLL do wywoływania [metody ForceGC —](icorprofilerinfo-forcegc-method.md) powinien być używany *tylko* na potrzeby wyzwalania operacje odzyskiwania pamięci, a następnie odpowiadania na wywołania zwrotne GC. Nie należy wywoływać interfejsu API profilowania, aby wykonywać inne zadania, takie jak próbkowanie stosu lub odłączanie.

### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

Począwszy od .NET Framework 4,5, istnieje nowe wywołanie zwrotne GC, [ConditionalWeakTableElementReferences —](icorprofilercallback5-conditionalweaktableelementreferences-method.md), które zapewnia profilerowi pełniejsze informacje o *dojściach zależnych*. Te uchwyty efektywnie dodają odwołanie z obiektu źródłowego do obiektu docelowego na potrzeby zarządzania okresem istnienia systemu GC. Dojścia zależne nie są nowe i deweloperzy, którzy program w kodzie zarządzanym, mogą tworzyć własne dojścia zależne przy użyciu klasy <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType>, nawet przed systemem Windows 8 i .NET Framework 4,5.

Jednak zarządzane aplikacje ze sklepu Windows XAML teraz intensywnie wykorzystują uchwyty zależne. W szczególności środowisko CLR używa ich do ułatwienia zarządzania cyklami odwołań między obiektami zarządzanymi i niezarządzanymi obiektami środowisko wykonawcze systemu Windows. Oznacza to, że jest to ważniejsze niż kiedykolwiek dotąd, aby uzyskać informacje o tych uchwytach zależnych, dzięki czemu można je wizualizować wraz z resztą krawędzi na grafie sterty. Biblioteka DLL profilera powinna używać [RootReferences2 —](icorprofilercallback2-rootreferences2-method.md), [ObjectReferences —](icorprofilercallback-objectreferences-method.md)i [ConditionalWeakTableElementReferences —](icorprofilercallback5-conditionalweaktableelementreferences-method.md) razem do tworzenia pełnego widoku grafu sterty.

## <a name="conclusion"></a>Wniosek

Można użyć interfejsu API profilowania środowiska CLR do analizy kodu zarządzanego działającego wewnątrz aplikacji ze sklepu Windows. W rzeczywistości można utworzyć istniejący Profiler, który jest opracowywany, i wprowadzić konkretne zmiany, aby można było kierować aplikacje do sklepu Windows. Interfejs użytkownika profilera powinien korzystać z nowych interfejsów API w celu aktywowania aplikacji ze sklepu Windows w trybie debugowania. Upewnij się, że biblioteka DLL profilera wykorzystuje tylko te interfejsy API, które są odpowiednie dla aplikacji ze sklepu Windows. Mechanizm komunikacji między biblioteką DLL i interfejsem użytkownika profilera powinien być zapisany przy użyciu ograniczeń interfejsu API aplikacji ze sklepu Windows i ma świadomość ograniczonych uprawnień dla aplikacji ze sklepu Windows. Biblioteka DLL profilera powinna mieć świadomość, jak środowisko CLR traktuje WinMD i jak zachowanie modułu wyrzucania elementów bezużytecznych jest różne w odniesieniu do zarządzanych wątków.

## <a name="resources"></a>Resources

**Środowisko uruchomieniowe języka wspólnego**

- [Profilowanie (niezarządzana dokumentacja interfejsu API)](index.md)

- [Metadane (niezarządzana dokumentacja interfejsu API)](../metadata/index.md)

**Interakcja środowiska CLR z środowisko wykonawcze systemu Windows**

- [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)

**Aplikacje ze sklepu Windows**

- [Dostęp do plików i uprawnienia (środowisko wykonawcze systemu Windows aplikacje](https://docs.microsoft.com/previous-versions/windows/apps/hh967755%28v=win.10%29)

- [Uzyskaj licencję dewelopera](https://docs.microsoft.com/previous-versions/windows/apps/hh974578%28v=win.10%29)

- [IPackageDebugSettings, interfejs](/windows/desktop/api/shobjidl_core/nn-shobjidl_core-ipackagedebugsettings)
