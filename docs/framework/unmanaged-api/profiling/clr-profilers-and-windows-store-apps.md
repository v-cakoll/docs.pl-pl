---
title: Profilery CLR i aplikacje Windows Store
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: f1747d99fbfbc31fb592aee570d10d574b8480b0
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/13/2018
ms.locfileid: "45558226"
---
# <a name="clr-profilers-and-windows-store-apps"></a>Profilery CLR i aplikacje Windows Store

W tym temacie opisano, co należy wziąć pod uwagę podczas pisania narzędzia diagnostyczne, które analizują zarządzany kod uruchomiony w aplikacji Windows Store.  Zawiera także wskazówki do modyfikowania istniejących narzędzi do programowania, więc one nadal działały po uruchomieniu testów za aplikacje Windows Store.  Aby zrozumieć te informacje, najlepiej, jeśli znasz wspólnego języka środowiska uruchomieniowego profilowania interfejsu API został już użyty ten interfejs API w narzędziem diagnostycznym, że działa prawidłowo dla aplikacji klasycznych Windows, a teraz interesują modyfikowanie narzędzie jest poprawnie uruchamiać aplikacje Windows Store.  
  
## <a name="introduction"></a>Wprowadzenie

 Jeśli utworzono ostatnie akapit wprowadzający jesteś zaznajomiony z interfejsem CLR profilowania API.  Narzędzie diagnostyczne, które działa dobrze w odniesieniu do zarządzanych aplikacji pulpitu już zostały zapisane.  Teraz możesz wiedzieć co zrobić, aby narzędzie współpracuje z zarządzanej aplikacji Windows Store.  Być może już sprawdzone działało i zostały wykryte, że nie jest prostym zadaniem.  W rzeczywistości istnieje wiele czynników, które mogą nie być oczywista dla wszystkich deweloperów narzędzia.  Na przykład:  
  
-   Aplikacje Windows Store działają w kontekście z poważnie ograniczonymi uprawnieniami.  
  
-   Pliki metadanych Windows mają unikatowych cechach systemu operacyjnego w porównaniu do tradycyjnych modułów zarządzanych.  
  
-   Aplikacje Windows Store mają rodzaj zawieszanie się interakcyjność systemowi.  
  
-   Twoje mechanizmy komunikacji międzyprocesowej mogą przestać działać z różnych powodów.  
  
 Ten temat zawiera listę czynności, które należy mieć świadomość i radzenia sobie z ich poprawnie.  
  
 Jeśli dopiero zaczynasz pracę z interfejsem CLR profilowania API, przejdź do zasobów na końcu tego tematu, aby znaleźć lepsze informacje wprowadzające.  
  
 Podanie szczegółów dotyczących poszczególnych Windows interfejsów API i jak powinna być używana jest również poza zakres tego tematu.  Należy wziąć pod uwagę w tym temacie punkt początkowy i odwołać się do MSDN, aby dowiedzieć się więcej na temat dowolnych interfejsów API Windows, do których odwołuje się tutaj.  
  
## <a name="architecture-and-terminology"></a>Architektura i terminologia

 Zazwyczaj narzędzia diagnostycznego ma architekturę, tak jak pokazano na poniższej ilustracji. Używa ona termin "profilera", ale wiele takich narzędzi go poza typowe wydajności lub profilowanie pamięci w obszarach, takich jak pokrycie kodu, testowanie struktury obiektów, podróży czasu, debugowanie, aplikacji, monitorowania i tak dalej.  Dla uproszczenia w tym temacie, będą nadal odwoływać się do tych narzędzi jako profilowania.  
  
 Następującą terminologią jest używany w tym temacie:  
  
**Aplikacja**

Jest to aplikacja, która analizuje profilera.  Zwykle Deweloper aplikacji używa teraz program profilujący ułatwia diagnozowanie problemów z aplikacją.  Tradycyjnie ta aplikacja będzie Windows aplikacji pulpitu, ale w tym temacie spoglądamy na aplikacje Windows Store.  
  
**Profiler DLL**

Jest to składnik, który ładuje do obszaru procesu aplikacji, analizowane.  Implementuje ten składnik, znany także jako program profilujący "wyrazem agent" [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[icorprofilercallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2,3, itp.) i interfejsy zużywa [ ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2,3, itp.) interfejsy, aby zbierać dane dotyczące analizy aplikacji i potencjalnie modyfikować aspekty zachowania aplikacji.  
  
**Profiler interfejsu użytkownika**

Jest to aplikacja komputerowa, która profiler użytkownik wchodzi w interakcję z.  Odpowiada za wyświetlanie stanu aplikacji dla użytkownika i dając użytkownikowi oznacza, że do sterowania zachowaniem aplikacji przeanalizowany.  Ten składnik jest zawsze uruchamiany w jego własnej przestrzeni procesu, niezależnie od obszaru procesu aplikacji, poddawanego profilowaniu.  Profiler interfejsu użytkownika mogą również działać jako "Dołączanie wyzwalacza" czyli procesu, który wywołuje [iclrprofiling::attachprofiler —](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metody, aby spowodować, że aplikacja przeanalizowany, można załadować biblioteki DLL Profiler w przypadkach, w którym program profilujący biblioteki DLL nie Załaduj przy uruchamianiu.  
  
> [!IMPORTANT]
> Interfejs użytkownika Profiler powinien pozostać w przypadku aplikacji komputerowych Windows, nawet wtedy, gdy jest używana do kontroli i raportów w aplikacji Windows Store.  Nie będziesz mieć możliwość pakietu i dostarczaj swoje narzędzia do diagnostyki w Windows Store.  Narzędzie musi wykonać czynności, których nie aplikacje Windows Store i wiele z tych czynności znajdują się wewnątrz Profiler interfejs użytkownika.  
  
 W tym dokumencie w przykładowym kodzie założono, że:  
  
- Profiler DLL został napisany w języku C++, ponieważ musi on być natywnej biblioteki DLL, zgodnie z wymaganiami środowiska CLR profilowania API.  
  
- Interfejs użytkownika Profiler został napisany w języku C#.  Nie jest to konieczne, ale ponieważ nie ma żadnych wymagań, od języka Interfejsu użytkownika Profiler procesu, dlaczego nie wybierz język, który jest zwięzłości i czytelności?  
  
### <a name="windows-rt-devices"></a>Urządzenia z systemem Windows RT

Urządzenia z systemem Windows RT są dość zablokowany.  Po prostu profilery innych firm nie można załadować tych urządzeń.  Ten dokument koncentruje się na komputerach z systemem Windows 8.  
  
## <a name="consuming-windows-runtime-apis"></a>Korzystanie z interfejsów API środowiska wykonawczego Windows

 W wielu scenariuszach opisanych w poniższych sekcjach Profiler w interfejsie użytkownika aplikacji klasycznych musi korzystać z nowych interfejsów API środowiska wykonawczego Windows.  Należy zapoznać się z dokumentacją, aby zrozumieć, które interfejsów API środowiska wykonawczego Windows można używać na aplikacje pulpitu i czy ich zachowanie różni się kiedy wywoływana z aplikacje klasyczne i Windows Store apps.  
  
 Jeśli Twój interfejs użytkownika Profiler jest zapisywana w kodzie zarządzanym, nastąpi kilka kroków, które należy zrobić, aby korzystanie z tych Windows Runtime interfejsów API łatwe.  Zobacz [zarządzane aplikacje pulpitu i środowisko uruchomieniowe Windows](https://go.microsoft.com/fwlink/?LinkID=271858) artykuł, aby uzyskać więcej informacji.  
  
## <a name="loading-the-profiler-dll"></a>Trwa ładowanie Profiler DLL

 W tej sekcji opisano, jak Profiler interfejs użytkownika powoduje, że aplikacji Windows Store, aby załadować bibliotekę DLL Profiler.  Kod omówione w tej sekcji należy w aplikacji komputerowej Profiler interfejsu użytkownika, a zatem polega na użyciu interfejsów API Windows, które są bezpieczne dla aplikacji klasycznych, ale nie zawsze bezpieczny dla aplikacji Windows Store.  
  
 Interfejs użytkownika Profiler może spowodować Profiler DLL ma być załadowany do obszaru procesu aplikacji na dwa sposoby:  
  
-   Przy uruchamianiu aplikacji, ponieważ kontrolowane przez zmienne środowiskowe.  
  
-   Dołączając do aplikacji po zakończeniu uruchamiania, wywołując [iclrprofiling::attachprofiler —](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metody.  
  
 Jednym z Twojego pierwszego problemów współczesnej będą się pojawiać startup-load — i dołączyć obciążenia Profiler DLL do poprawnego działania przy użyciu aplikacji Windows Store.  Obie formy ładowania udostępniać pewne specjalne zagadnienia dotyczące wspólnych, więc Rozpocznijmy od nich.  
  
### <a name="common-considerations-for-startup-and-attach-loads"></a>Typowe zagadnienia dotyczące uruchamiania i dołączyć obciążeń

 **Podpisywanie swoje Profiler DLL**  
 Windows próbuje załadować biblioteki DLL Profiler, sprawdza, czy Profiler DLL jest poprawnie podpisana.  W przeciwnym razie obciążenia nie powiedzie się domyślnie. Istnieją dwa sposoby wykonania tej czynności:  
  
-   Upewnij się, że Profiler DLL jest podpisany.  
  
-   Poinformuj użytkowników, na swoim komputerze z systemem Windows 8 należy ich zainstalować licencję deweloperską przed rozpoczęciem korzystania z narzędziem.  Można to zrobić automatycznie w programie Visual Studio, lub ręcznie z poziomu wiersza polecenia.  Aby uzyskać więcej informacji, zobacz [Uzyskaj licencję dewelopera](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx).  
  
 **Uprawnienia systemu plików**  
 W aplikacji Windows Store musi mieć uprawnienie do ładowania i wykonywania Profiler DLL z lokalizacji w systemie plików, w której znajduje się.  Domyślnie aplikacji Windows Store nie ma takiego zezwolenia na większości katalogów, a wszelkie nie powiodła się próba załadowania biblioteki DLL Profiler dadzą wpis w dzienniku zdarzeń aplikacji Windows, która wygląda mniej więcej tak:  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 Ogólnie rzecz biorąc aplikacje Windows Store tylko mogą korzystać z ograniczonego zestawu lokalizacji na dysku.  Każdej aplikacji Windows Store można uzyskać dostęp do własnej folderów danych aplikacji, a także kilka innych obszarach w systemie plików, dla którego przyznano dostęp wszystkie aplikacje Windows Store.  Zaleca się zainstalować Profiler DLL wraz z jego zależnościami gdzieś w ramach Program Files lub Program Files (x86), ponieważ wszystkie aplikacje Windows Store ma uprawnienia odczytu i wykonania ma domyślnie.  
  
### <a name="startup-load"></a>Uruchamianie obciążenia

 Zazwyczaj w przypadku aplikacji klasycznej Profiler interfejs użytkownika wyświetli obciążenia uruchamiania biblioteki DLL Profiler przez inicjowanie blok środowiska, który zawiera wymagane zmienne środowiska CLR profilowania API (czyli `COR_PROFILER`, `COR_ENABLE_PROFILING`, i `COR_PROFILER_PATH`), a następnie utworzenie nowego procesu z tego bloku środowiska.  To samo dotyczy aplikacji Windows Store, ale różnią się mechanizmy.  
  
 **Nie uruchamiaj z podwyższonym poziomem uprawnień**  
 Jeśli przetwarzanie próby zduplikować aplikacji Windows Store B procesu, proces A ma być uruchamiana w średnich integralności poziomu, nie na poziomie wysokiej integralności, (który nie jest podniesione uprawnienia).  Oznacza to, że Profiler interfejs użytkownika powinna być uruchomiona na średnim poziomie integralności, lub musi ona zduplikować inny proces pulpitu na średnim poziomie integralności Aby zadbać o uruchomienie aplikacji Windows Store.  
  
 **Wybieranie Windows App Store, do profilu**  
 Po pierwsze należy poprosić użytkownika profilera aplikacji Windows Store, które były uruchamiane.  Dla aplikacji komputerowych prawdopodobnie możesz pokazać dialogowego przeglądania plików, a użytkownik będzie Znajdź i zaznacz plik .exe.  Jednak aplikacje Windows Store są różne, i za pomocą okna dialogowego przeglądania nie ma sensu.  Zamiast tego zaleca się wyświetlanie listy zainstalowanych dla danego użytkownika dokonać wyboru spośród aplikacji Windows Store użytkownika.  
  
 Możesz użyć [klasy PackageManager](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx) do generowania tej listy.  `PackageManager` jest klasą Windows Runtime, która jest dostępna dla aplikacji klasycznych, a w rzeczywistości jest *tylko* dostępne dla aplikacji klasycznych.  
  
 Poniższy przykład kodu z hipotetyczny interfejsu użytkownika Profiler zapisywane jako aplikacji klasycznej w języku C# yses `PackageManager` do generowania listy aplikacji Windows:  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **Określanie blok środowiska niestandardowego**  
 Nowy interfejs COM, [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx), można go dostosować zachowanie wykonywania aplikacji Windows Store, aby ułatwić niektóre rodzaje diagnostyki.  Jeden z jego metod [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx), pozwala przekazać blok środowiska do aplikacji Windows Store, po uruchomieniu, oraz inne przydatne efekty, takie jak zawieszenie procesu automatycznego wyłączania.  Blok środowiska to ważne, ponieważ jest to, gdzie trzeba określić zmienne środowiskowe (`COR_PROFILER`, `COR_ENABLE_PROFILING`, i `COR_PROFILER_PATH)`) używana przez środowisko CLR w celu załadowania biblioteki DLL Profiler.  
  
 Rozważmy następujący fragment kodu:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 Istnieje kilka elementów, które będą potrzebne, aby uzyskać odpowiednie:  
  
-   `packageFullName` można określić jednocześnie Iterowanie pakietów i przechwytywanie `package.Id.FullName`.  
  
-   `debuggerCommandLine` jest to nieco bardziej interesująca.  Aby można było przekazać blok środowiska niestandardowego w aplikacji Windows Store, należy napisać własny, uproszczony fikcyjnego debugera.  Generowanie udoskonaleń Windows aplikacji Windows Store zawieszone, a następnie dołącza debuger, uruchamiając debuger przy użyciu wiersza polecenia takich jak w tym przykładzie:  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     gdzie `-p 1336` oznacza aplikacji Windows Store ma 1336 identyfikator procesu, a `-tid 1424` oznacza 1424 identyfikator wątku jest wątek, który jest wstrzymana.  Fikcyjny debuger może przeanalizować ThreadID z wiersza polecenia, Wznów wątek, a następnie zamknij.  
  
     Poniżej przedstawiono przykładowe kodu C++, w tym celu (Upewnij się dodać sprawdzanie błędów!):  
  
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
  
     Należy wdrożyć ten zastępczy debuger jako część instalacji narzędzia do diagnostyki, a następnie określ ścieżkę do tego debugera w `debuggerCommandLine` parametru.  
  
 **Uruchomienie aplikacji Windows Store**  
 Na koniec dotarła moment, aby uruchomić aplikację Windows Store. Jeśli już już Próbowałeś wykonać to samodzielnie, być może zauważono, że [CreateProcess](/windows/desktop/api/processthreadsapi/nf-processthreadsapi-createprocessa) nie sposób tworzą proces aplikacji Windows Store.  Zamiast tego należy użyć [IApplicationActivationManager::ActivateApplication](/windows/desktop/api/shobjidl_core/nf-shobjidl_core-iapplicationactivationmanager-activateapplication) metody.  Aby to zrobić, należy pobrać identyfikator modelu użytkownika aplikacji z aplikacji Windows Store, który uruchamiany jest.  A to oznacza, że musisz wykonać nieco możesz za pośrednictwem manifestu.  
  
 Podczas Iterowanie pakietów (zobacz sekcję "Wybieranie Windows Store do profilu aplikacji" w [uruchamiania obciążenia](#Startup) wcześniejszej sekcji), będziesz chciał Pobierz zbiór aplikacje zawarte w manifeście bieżącego pakietu:  
  
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
  
 Tak, jeden pakiet może mieć wiele aplikacji, a każda aplikacja ma swój własny identyfikator modelu użytkownika aplikacji.  Dlatego warto zadać użytkownikowi aplikację do profilu i Pobierz identyfikator modelu użytkownika aplikacji z określonej aplikacji:  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
    //...
}
```  
  
 Na koniec masz teraz co jest potrzebne do uruchomienia aplikacji Windows Store:  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **Pamiętaj, aby wywołać DisableDebugging**  
 Gdy wywoływana [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx), wprowadzone promise, który będzie czyszczenie po sobie przez wywołanie metody [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) metody, dlatego należy zrobić które po zakończeniu sesji profilowania.  
  
### <a name="attach-load"></a>Dołącz obciążenia

 Gdy interfejs użytkownika Profiler chce dołączyć jej Profiler DLL do aplikacji, która została już uruchomiona, uruchamianie, używa [iclrprofiling::attachprofiler —](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md).  To samo dotyczy przy użyciu aplikacji Windows Store.  Ale oprócz typowe kwestie dotyczące, wymienionych wcześniej, upewnij się, że aplikacji Windows Store docelowej nie jest wstrzymany.  
  
 **EnableDebugging**  
 Podobnie jak w przypadku uruchamiania obciążenia, należy wywołać [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx) metody.  Nie będzie potrzebny do przekazywania blok środowiska, ale musisz mieć jeden z jego innych funkcji: wyłączanie procesu automatycznego zawieszenia.  W przeciwnym razie, gdy interfejs użytkownika Profiler wywołuje [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md), może spowodować zawieszenie aplikacji Windows Store docelowej.  W rzeczywistości jest to prawdopodobnie Jeśli użytkownik jest teraz interakcji z Profiler interfejs użytkownika i aplikacji Windows Store nie jest aktywny na wszystkich ekranach użytkownika.  A jeśli Store Windows, aplikacja jest wstrzymana, go nie będzie mógł odpowiadać na dowolną sygnał środowiska CLR i wysyła do niej dołączyć Profiler DLL.  
  
 Dlatego należy wykonaj podobny do poniższego:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 To samo wywołanie, które czyniłyby w przypadku uruchamiania obciążenia, z wyjątkiem nie zostanie określony, debuger wiersza polecenia lub blok środowiska.  
  
 **DisableDebugging**  
 Jak zawsze, nie zapomnij wywołać [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) po zakończeniu sesji profilowania.  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>Uruchamianie aplikacji Windows Store  
 Dlatego w aplikacji Windows Store na koniec został załadowany Profiler DLL.  Teraz Profiler DLL musi prowadzone jak grać przez różne reguły wymaganych przez aplikacje Windows Store, które interfejsy API są dopuszczalne i z uruchamianiem przy użyciu mniejsze uprawnienia.  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Trzymaj się do interfejsów API aplikacji Windows Store  
 Podczas przeglądania interfejsu API Windows, można zauważyć, że każdy interfejs API jest udokumentowany jako mające zastosowanie do aplikacji klasycznych i/lub aplikacji Windows Store.  Na przykład **wymagania** sekcji dokumentacji poświęconej [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) funkcji wskazuje, że funkcja dotyczy tylko aplikacji klasycznych. Z kolei [InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex) funkcja jest dostępna zarówno dla aplikacji klasycznych i aplikacji Windows Store.  
  
 Podczas tworzenia biblioteki DLL Profiler, Traktuj je, tak jak w przypadku aplikacji Windows Store i tylko przy użyciu interfejsów API, które zostały opisane jako dostępne dla aplikacji Windows Store.  Analizowanie zależności (na przykład, można uruchomić `link /dump /imports` względem Profiler DLL do inspekcji), a następnie wyszukaj dokumentację, aby zobaczyć, które zależności są ok, a które nie są.  W większości przypadków naruszeń zasad można naprawić, po prostu zastąpienia ich nowsze formie interfejsu API, który jest przedstawiany jako bezpieczne (na przykład, zastępując [InitializeCriticalSectionAndSpinCount](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionandspincount) z [ InitializeCriticalSectionEx](/windows/desktop/api/synchapi/nf-synchapi-initializecriticalsectionex)).  
  
 Można zauważyć, że Profiler DLL wywołuje niektóre interfejsy API, które dotyczą tylko aplikacji klasycznych, a jeszcze wydają się do pracy, nawet gdy Profiler DLL jest ładowany w aplikacji Windows Store.  Należy pamiętać, że ryzykowne, aby użyć dowolnego interfejsu API nie jest udokumentowany do użytku z aplikacjami Windows Store w Profiler DLL po załadowaniu do procesu aplikacji Windows Store:  
  
-   Takie interfejsy API nie musi działać, gdy zostanie wywołana w kontekście unikatowy, uruchamianą w aplikacji Windows Store w.  
  
-   Takie interfejsy API mogą nie działać spójnie, gdy wywoływana z w ramach różnych procesów aplikacji Windows Store.  
  
-   Takie interfejsy API mogą wydawać się działać prawidłowo z aplikacji Windows Store w bieżącej wersji systemu Windows, ale może spowodować przerwanie lub wyłączone w przyszłych wydaniach systemu Windows.  
  
 Najważniejsze porady jest naprawić wszystkie naruszenia zasad i uniknąć ryzyka.  
  
 Może się okazać absolutnie nie może wykonywać bez konkretnego interfejsu API i nie można odnaleźć, zastępuje odpowiednie dla aplikacji Windows Store.  W takim przypadku co najmniej:  
  
-   Test, test, test daylights życia poza wykorzystanie tego interfejsu API.  
  
-   Omówienie interfejsu API może nagle podział i znikają, gdy wywołuje się, z wewnątrz Windows Store apps w przyszłych wersjach systemu Windows.  To nie były uznawane za problem ze zgodnością przez firmę Microsoft i użycia jego obsługa nie będzie priorytet.  
  
### <a name="reduced-permissions"></a>Ograniczonymi uprawnieniami

 Jest poza zakresem tego tematu, aby wyświetlić listę wszystkich metod, które uprawnienia aplikacji Windows Store różnią się od aplikacji klasycznych.  Jednak bez obaw zachowanie będzie się różnił za każdym razem, gdy Profiler DLL (gdy są ładowane do aplikacji Windows Store w porównaniu do aplikacji klasycznej) próbuje uzyskać dostępu do żadnych zasobów.  System plików jest najbardziej typowym przykładem.  Istnieją, ale kilka miejsca na dysku, który może być dostęp do danej aplikacji Windows Store (zobacz [pliku dostępu i uprawnień (aplikacji środowiska wykonawczego Windows](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)), i Profiler DLL będzie znajdować się w takim samym ograniczeniom.  Dokładnie przetestuj swój kod.  
  
### <a name="inter-process-communication"></a>Komunikacji międzyprocesowej

 Jak pokazano na diagramie na początku tego dokumentu, Profiler DLL (załadowane do obszaru procesu aplikacji Windows Store) prawdopodobnie wystąpi konieczność komunikować się z Profiler interfejs użytkownika (uruchomionego w przestrzeni procesu osobnych aplikacji klasycznej) za pomocą własnego niestandardowego procesu między kanał komunikacyjny (IPC).  Interfejs użytkownika Profiler wysyła sygnałów do DLL Profiler, aby zmodyfikować jego zachowanie i Profiler DLL wysyła dane z analizy aplikacji Windows Store z powrotem do interfejsu użytkownika Profiler dla przetwarzania końcowego i wyświetlanie użytkownikowi profilera.  
  
 Większość profilery muszą działać w ten sposób, ale mechanizmów IPC wybrane opcje są bardziej ograniczone, gdy Profiler DLL jest ładowany w aplikacji Windows Store.  Na przykład nazwane potoki nie są częścią aplikacji Windows Store zestawu SDK, więc nie można ich używać.  
  
 Ale oczywiście pliki są nadal w aczkolwiek w sposób bardziej ograniczone.  Dostępne są zdarzenia.  
  
 **Komunikacja za pośrednictwem plików**  
 Większość danych będzie prawdopodobnie przekazywania między Profiler DLL i Profiler interfejsu użytkownika za pośrednictwem plików.  Należy wybrać lokalizację pliku, który zarówno Profiler DLL (w kontekście aplikacji Windows Store), jak i Profiler interfejsu użytkownika po ich przeczytaniu i do zapisu.  Na przykład ścieżka folderu tymczasowego prowadzi do lokalizacji, dostępnej dla obu Profiler DLL i Profiler interfejsu użytkownika, ale nie inne pakiet aplikacji Windows Store mogą uzyskiwać dostęp do (chroniąc wszelkie informacje, który ma zostać zalogowany z innych pakietów aplikacji Windows Store).  
  
 Zarówno Profiler interfejsu użytkownika, jak i Profiler DLL można określić tę ścieżkę niezależnie.  Interfejs użytkownika Profiler, gdy go wykonuje iterację przez wszystkie pakiety zainstalowane dla bieżącego użytkownika (patrz wcześniej w przykładowym kodzie) uzyskuje dostęp do `PackageId` klasy, z którego ścieżka folderu tymczasowego mogą pochodzić z kodem podobny do tego fragmentu kodu.  (Tak jak zawsze, sprawdzanie błędów została pominięta w celu skrócenia programu.)  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 W międzyczasie Biblioteka DLL Profiler można po prostu te same czynności wykonasz, chociaż jest to możliwe tylko w łatwy sposób pobrać do [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx) przy użyciu [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx) właściwości.  
  
 **Komunikacja za pośrednictwem zdarzeń**  
 Chcąc proste semantyki sygnalizowanie między Profiler interfejsu użytkownika i Profiler DLL, można użyć zdarzenia w aplikacji Windows Store, jak również aplikacje klasycznych.  
  
 Z biblioteki DLL Profiler można po prostu Wywołaj [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa) funkcji, aby utworzyć zdarzenia nazwanego z dowolną nazwę.  Na przykład:  
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 Interfejs użytkownika Profiler musi znaleźć tego zdarzenia o nazwie w przestrzeni nazw aplikacji Windows Store.  Na przykład można wywołać interfejs użytkownika Profiler [CreateEventEx](/windows/desktop/api/synchapi/nf-synchapi-createeventexa), określając nazwę zdarzenia jako  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>` jest identyfikator SID AppContainer aplikacji Windows Store.  Wcześniejszej sekcji tego tematu pokazano, jak przejść przez pakiety instalowane dla bieżącego użytkownika.  Z tego przykładowego kodu można uzyskać packageId.  I z pakietu, można uzyskać `<acSid>` kodem podobny do następującego:  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
### <a name="no-shutdown-notifications"></a>Brak powiadomień zamknięcia

 Podczas uruchamiania w aplikacji Windows Store, Profiler DLL, nie należy polegać na albo [icorprofilercallback::Shutdown —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md) lub nawet [DllMain](/windows/desktop/Dlls/dllmain) (przy użyciu `DLL_PROCESS_DETACH`) wywoływana w celu powiadomienia Biblioteka DLL Profiler czy jest kończone w aplikacji Windows Store.  W rzeczywistości należy się spodziewać, że nigdy nie zostaną wywołane.  W przeszłości wielu Profiler dll ma te powiadomienia o użytym jako wygodnym miejscem opróżnić pamięć podręczną na dysku, zamykanie plików, wysyłanie powiadomień do interfejsu użytkownika Profiler itp.  Ale teraz Profiler DLL musi być uporządkowane w sposób nieco różniący się.  
  
 Profiler DLL powinien być informacje rejestrowania, ponieważ przechodzi ona.  Ze względu na wydajność można partii danych w pamięci i opróżnij go na dysku, gdy zadanie wsadowe powiększania się ostatnie niektóre wartości progowej.  Ale przyjęto założenie, że wszystkie informacje, które nie zostały jeszcze opróżniany do dysku mogą zostać utracone.  Oznacza to, należy wybrać uważnie próg oraz że Twój interfejs użytkownika Profiler musi być ze wzmocnionymi zabezpieczeniami, aby poradzić sobie z niepełne informacje zapisane przez Profiler DLL.  
  
## <a name="windows-runtime-metadata-files"></a>Pliki metadanych Windows Runtime

 Jest poza zakres tego dokumentu, aby przejść do szczegółów na jakie metadanych środowiska wykonawczego Windows (WinMD) są pliki.    W tej sekcji jest ograniczona do zachowaniem interfejsu środowiska CLR profilowania API plików WinMD są ładowane za pomocą aplikacji Windows Store, który analizuje Profiler DLL.  
  
### <a name="managed-and-non-managed-winmds"></a>Winmd zarządzanych i niezarządzanych

 Jeśli Deweloper za pomocą programu Visual Studio Utwórz nowy projekt składnika środowiska wykonawczego Windows, kompilacja tego projektu tworzy plik WinMD, który opisuje metadane (opisy typów klasy, interfejsy, itp.) utworzone przez dewelopera.  Jeśli ten projekt jest projektem języków zarządzanych, napisany w języku C# lub VB, tego samego pliku WinMD zawiera również implementację tych typów (co oznacza, że zawiera on wszystkie IL, które są kompilowane z kodu źródłowego dla deweloperów).  Takie pliki są określane jako zarządzanych plików WinMD.  Są one interesujące, że zawierają one zarówno metadane środowiska wykonawczego Windows, jak i podstawowej implementacji.  
  
 Z kolei jeśli deweloper tworzy projekt składnika środowiska wykonawczego Windows w języku C++, kompilacja tego projektu tworzy plik WinMD, który zawiera tylko metadane, a implementacja jest skompilowany w oddzielnych natywnej biblioteki DLL.  Podobnie plików WinMD, które są dostarczane w zestawie Windows SDK zawiera tylko metadane z implementacją kompilowane do oddzielnych natywnych bibliotek DLL, które są dostarczane jako część systemu Windows.  
  
 Poniższe informacje. dotyczy to zarówno zarządzanych Winmd, które zawierają metadane i implementację, oraz niezarządzanych Winmd, które zawierają tylko metadane.  
  
### <a name="winmd-files-look-like-clr-modules"></a>Pliki WinMD wyglądać moduły środowiska CLR

 Jeśli chodzi o środowisko CLR, wszystkie pliki WinMD to moduły.  API profilowania CLR informuje w związku z tym Profiler DLL podczas ładowania plików WinMD i jakie ich ModuleIDs, w taki sam sposób jak w przypadku innych modułów zarządzanych.  
  
 Profiler DLL można odróżnić plików WinMD od innych modułów, wywołując [icorprofilerinfo3::getmoduleinfo2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) metody i zapoznanie się `pdwModuleFlags` parametr dla danych wyjściowych [COR_PRF_MODULE_WINDOWS_ Środowisko URUCHOMIENIOWE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) flagi.  (Zostanie to ustawione tylko wtedy, gdy ModuleID reprezentuje WinMD.)  
  
### <a name="reading-metadata-from-winmds"></a>Podczas odczytywania metadanych z plików Winmd

 Pliki WinMD, takich jak moduły regularnych zawierają metadanych, który może zostać odczytany za pośrednictwem [interfejsów API metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md).  Jednak CLR mapuje typów środowiska wykonawczego Windows do typów programu .NET Framework podczas odczytuje pliki WinMD, dzięki czemu deweloperzy, którzy program w kodzie zarządzanym i korzystać z pliku WinMD mają bardziej naturalny sposób programowania.  Niektóre przykłady te mapowania, zobacz [pomocy technicznej dla Windows Store aplikacji programu .NET Framework i środowiska wykonawczego Windows](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).  
  
 Dlatego widok swojego programu profilującego otrzyma wykorzystuje metadanych interfejsów API: nieprzetworzony widok Windows Runtime lub zamapowanego widoku .NET Framework?  Odpowiedź: to dla Ciebie.  
  
 Gdy wywołujesz [icorprofilerinfo::getmodulemetadata —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) metody WinMD można uzyskać interfejsu metadane, takie jak [imetadataimport —](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), użytkownik może ustawić [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)w `dwOpenFlags` parametru, aby wyłączyć to mapowanie.  W przeciwnym razie domyślnie mapowania zostaną włączone.  Zazwyczaj program profilujący zostanie zachowana mapowanie włączone, tak, aby ciągów, które uzyskuje dostęp do biblioteki DLL Profiler z metadanych WinMD (na przykład nazwy typów) będzie wyglądać dobrze znanych i fizyczne użytkownikowi profilera.  
  
### <a name="modifying-metadata-from-winmds"></a>Modyfikowanie metadanych z plików Winmd

 Modyfikowanie metadanych w Winmd nie jest obsługiwane.  Jeśli wywołasz [icorprofilerinfo::getmodulemetadata —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) metodę WinMD pliku i określić [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) w `dwOpenFlags` parametru lub zadawać interfejsu zapisywalny metadane, takie jak [ IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [getmodulemetadata —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) zakończy się niepowodzeniem.  Jest to szczególnie ważne, aby ponowne zapisywanie IL profilerów, których potrzeba zmodyfikowania metadanych w celu obsługi swoich Instrumentacji (na przykład aby dodać AssemblyRefs lub nowe metody).  Dlatego należy sprawdzić, [COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) najpierw (zgodnie z opisem w poprzedniej sekcji) i powstrzymanie się z prośbą o interfejsy zapisywalny metadanych dla tych modułów.  
  
### <a name="resolving-assembly-references-with-winmds"></a>Rozpoznawanie odwołania do zestawów za pomocą plików Winmd

 Wiele profilery muszą rozwiązać odwołania do metadanych ręcznie, aby pomóc w Instrumentacji lub typ inspekcji.  Takie profilery muszą wiedzieć, jak środowisko CLR jest rozpoznawana jako odwołania do zestawów, które wskazują na Winmd, ponieważ te odwołania są rozpoznawane w zupełnie inny sposób niż odwołania do standardowego zestawu.  
  
## <a name="memory-profilers"></a>Profilowania pamięci

 Moduł wyrzucania elementów bezużytecznych oraz sterta zarządzana nie są różni się w aplikacji Windows Store i aplikacji klasycznych.  Jednak istnieją pewne niewielkie różnice, które autorzy profilera należy pamiętać o.  
  
### <a name="forcegc-creates-a-managed-thread"></a>Forcegc — tworzy wątek

 W trakcie profilowania pamięci, Profiler DLL tworzonych zwykle przez oddzielnego wątku, z którego można wywołać [forcegc — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) metody.  Jest to nic nowego.  Ale co może być Zaskakujące czynność podczas wyrzucania elementów bezużytecznych w aplikacji Windows Store może przekształcić wątek do wątków zarządzanych (na przykład profilowanie API ThreadID zostaną utworzone dla tego wątku).  
  
 Konsekwencje tego, jest zrozumieć różnice między wywołania synchroniczne i asynchroniczne, zgodnie z definicją funkcji CLR profilowania API. Należy pamiętać, że jest to bardzo różnią się od koncepcji wywołania asynchroniczne w aplikacjach Windows Store.  Zobacz wpis w blogu [Dlaczego mamy CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) Aby uzyskać więcej informacji.  
  
 Istotne jest, wywołania w wątkach, utworzonych przez Twój program profilujący są zawsze traktowane synchroniczne, nawet w przypadku tych wywołań z poza implementacją jednego z biblioteki DLL Profiler [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody.  Co najmniej, które używane w przypadku.  Teraz, gdy środowisko CLR wyłączył wątku Twój program profilujący do wątków zarządzanych ze względu na wywołania do [forcegc — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md), że wątek przestaje być uważany za swój profiler wątku.  Jako takie, środowisko CLR wymusza bardziej rygorystyczne definicji co kwalifikuje się jako synchroniczne dla tego wątku — to znaczy, wywołanie muszą pochodzić od jednego z biblioteki DLL Profiler [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody służące do kwalifikowania jako synchroniczna.  
  
 Co to znaczy w praktyce?  Większość [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) metody są tylko bezpieczne być wywoływana synchronicznie i natychmiast nie powiedzie się inaczej.  Jeśli biblioteka DLL Profiler używa usługi [forcegc — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) wątku dla innych wywołań dokonanych w zazwyczaj na utworzone przez profiler wątków (na przykład, aby [requestprofilerdetach —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md), [requestrejit —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md), lub [requestrevert —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)), możesz zacząć występują problemy.  Nawet funkcji asynchronicznej bezpiecznego takich jak [dostacksnapshot —](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) ma specjalne reguły, jeśli są wywoływane z wątków zarządzanych. (Wpis w blogu [przechodzenie po stosie Profiler: podstawy i nowszych](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) Aby uzyskać więcej informacji.)  
  
 Dlatego zaleca się, który wątek Profiler DLL tworzy wywołanie [forcegc — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) powinny być używane *tylko* na potrzeby wyzwalania wykazów globalnych i następnie odpowiadanie na wywołania zwrotne GC.  Nie należy wywołać profilowania interfejsu API do wykonania innych zadań, takich jak stos próbkowania lub odłączanie.  
  
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences

 Począwszy od programu .NET Framework 4.5 jest nowe wywołanie zwrotne GC [conditionalweaktableelementreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md), które zapewnia program profilujący ukończenia więcej informacji o *zależne uchwyty*. Uchwyty te skutecznie Dodaj odwołanie z obiektu źródłowego do obiektu docelowego na potrzeby Zarządzanie okresem istnienia GC.  Uchwyty zależne to nic nowego i deweloperom programującym w kodzie zarządzanym są w stanie utworzyć własne zależne dojść przy użyciu <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> klasy, nawet przed systemu Windows 8 i .NET Framework 4.5.  
  
 Jednak zarządzanych aplikacji XAML Windows Store teraz intensywnie korzystają z uchwytów zależnych.  W szczególności środowiska CLR są one używane do pomocy w zarządzaniu cykle odwołań między obiektami zarządzanej i niezarządzanej środowiska wykonawczego Windows.  To oznacza, że jest ważniejsze teraz niż kiedykolwiek dla profilowania pamięci do uzyskania informacji o tych zależnych uchwytów, dzięki czemu mogą być wizualizowane i resztę krawędzie na wykresie sterty.  Skorzystaj z biblioteki DLL Profiler [rootreferences2 —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [objectreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), i [conditionalweaktableelementreferences —](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) ze sobą w celu utworzenia pełen wgląd na wykresie sterty .  
  
## <a name="conclusion"></a>Wniosek

 Istnieje możliwość analizowania zarządzanym kodzie działającym wewnątrz aplikacji Windows Store za pomocą interfejsu CLR profilowania API.  W rzeczywistości można wykonać istniejące programem profilującym, które tworzysz i wprowadzić pewne zmiany określonych, dzięki czemu można wskazać, aplikacje Windows Store.   Interfejs użytkownika Profiler należy używać nowych interfejsów API do aktywowania aplikacji Windows Store w trybie debugowania.  Upewnij się, że Profiler DLL wykorzystuje tylko tych interfejsów API odpowiednie dla aplikacji Windows Store.  Mechanizm komunikacji między Profiler DLL i interfejsu użytkownika Profiler powinien być zapisywany z ograniczenia interfejsu API aplikacji Windows Store na uwadze i rozpoznawanie ograniczone uprawnienia w miejscu dla aplikacji Windows Store.  Profiler DLL powinien wiedzieć o jak CLR traktuje Winmd, i jak moduł Garbage Collector zachowanie różni się w odniesieniu do zarządzanych wątków.  
  
## <a name="resources"></a>Resources

 **Środowisko uruchomieniowe języka wspólnego**  
 -   [Dokumentacja interfejsu API profilowania CLR](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [Dokumentacja interfejsu API metadanych CLR](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **CLR interakcji ze środowiskiem uruchomieniowym Windows**  
 [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Aplikacje Windows Store**  
 -   [Dostęp do plików i uprawnienia (aplikacje Windows Runtime](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [Uzyskaj licencję dewelopera](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [Interfejs IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>Zobacz też

[Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)  
