---
title: Profilery CLR i aplikacji ze Sklepu Windows
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: csharp
applies_to:
- Windows 10
- Windows 8
helpviewer_keywords:
- profiling API
- profiling API [.NET Framework]
- profiling managed code
- profiling managed code [Windows Store Apps]
ms.assetid: 1c8eb2e7-f20a-42f9-a795-71503486a0f5
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d884b80ba8ccc42d1b6acc671db408305a095a7d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="clr-profilers-and-windows-store-apps"></a>Profilery CLR i aplikacji ze Sklepu Windows
W tym temacie omówiono, jakie trzeba myśleć o podczas pisania narzędzia diagnostyczne analizy zarządzanego kodu uruchamianego w aplikacji ze Sklepu Windows.  Udostępnia również wytyczne do modyfikowania istniejących narzędzi rozwoju, aby nadal działa podczas wykonywania dla aplikacji ze Sklepu Windows.  Aby zrozumieć te informacje, najlepiej, jeśli znasz wspólnego języka środowiska uruchomieniowego profilowania API, już używane tego interfejsu API w narzędzia diagnostycznego, że działa prawidłowo, przed aplikacji klasycznych systemu Windows, a teraz jest zainteresowani modyfikowanie narzędzie jest do poprawnego działania względem aplikacji ze Sklepu Windows.  
  
 Ten temat składa się z następujących sekcji:  
  
 [Wprowadzenie](#Intro)  
 [Architektura i terminologia](#Arch)  
 [Urządzenia z systemem Windows RT](#RT)  
[Korzystanie z interfejsów API środowiska wykonawczego systemu Windows](#Consuming)  
[Podczas ładowania biblioteki DLL profilera](#Loading)  
 [Typowe kwestie dotyczące do uruchamiania i Dołącz obciążenia](#Common)  
 [Uruchamianie obciążenia](#Startup)  
 [Dołącz obciążenia](#Attach)  
[Używany w aplikacji ze Sklepu Windows](#Running)  
 [Trzymaj do interfejsów API aplikacji Sklepu Windows](#APIs)  
 [Ograniczonymi uprawnieniami](#Permissions)  
 [Komunikacja między procesami](#Interprocess)  
 [Brak powiadomień zamknięcia](#Shutdown)  
[Pliki metadanych środowiska wykonawczego systemu Windows](#Metadata)  
 [Metadanych Winmd zarządzanych i niezarządzanych](#WMDs)  
 [Plików WinMD wyglądać modułów środowiska CLR](#CLRModules)  
 [Odczytywanie metadanych z metadanych Winmd](#Reading)  
 [Modyfikowanie metadanych z metadanych Winmd](#Modifying)  
 [Rozpoznawanie odwołania do zestawów z metadanych Winmd](#Resolving)  
[Profilowania pamięci](#Profilers)  
 [ForceGC tworzy zarządzanych wątków](#ForceGC)  
 [ConditionalWeakTableReferences](#WeakTable)  
[Zawierania](#Conclusion)  
[Zasoby](#Resources)  
  
<a name="Intro"></a>   
## <a name="introduction"></a>Wprowadzenie  
 Jeśli wprowadzono poza wprowadzające akapitu następnie możesz zapoznać się z interfejsu API profilowania CLR.  Narzędzie diagnostyczne, które działa dobrze w odniesieniu do zarządzanych aplikacji klasycznych już zostały zapisane.  Teraz możesz zastanawiasz się, co należy zrobić, aby narzędzie współpracuje z zarządzanych aplikacji ze Sklepu Windows.  Być może już próbowano działało i mieć wykryte, że nie jest proste zadania.  W rzeczywistości istnieje wiele czynników, które mogą nie być widoczne dla wszystkich deweloperów narzędzia.  Na przykład:  
  
-   Aplikacje ze Sklepu Windows, uruchom w kontekście z poważnie z ograniczonymi uprawnieniami.  
  
-   Pliki metadanych systemu Windows mają unikatowych parametrów w porównaniu do tradycyjnego modułów zarządzanych.  
  
-   Aplikacje ze Sklepu Windows mają nawyk zawieszenia się interakcyjności systemowi.  
  
-   Twoje mechanizmy komunikacji międzyprocesowej może działać z różnych przyczyn.  
  
 Ten temat zawiera listę czynności, które trzeba znać i sposób postępowania z nimi poprawnie.  
  
 Jeśli zaczynasz API profilowania CLR, przejdź do zasobów na końcu tego tematu można znaleźć lepsze informacje wprowadzające.  
  
 Udostępnia szczegółowe informacje o określonych interfejsów API systemu Windows i jak powinny być używane jest również poza zakres tego tematu.  Należy wziąć pod uwagę w tym temacie punkt początkowy i zapoznaj się MSDN, aby dowiedzieć się więcej na temat dowolnego odwołujesz interfejsów API systemu Windows.  
  
<a name="Arch"></a>   
## <a name="architecture-and-terminology"></a>Architektura i terminologia  
 Zwykle narzędzie diagnostyczne ma architekturę, tak jak pokazano na poniższej ilustracji. Używa termin "profilera", ale wiele takich narzędzi Przejdź przekroczeniem typowe wydajności lub profilowania pamięci w obszarach, takich jak pokrycie kodu mock struktury obiektów, podróży czasu, debugowanie, aplikacji, monitorowania i tak dalej.  Dla uproszczenia w tym temacie będą nadal odwoływać się do tych narzędzi jako profilowania.  
  
 Następującą terminologią używany w tym temacie:  
  
 Aplikacja  
 To jest aplikacja, która analizuje profilera.  Zazwyczaj developer tej aplikacji jest teraz, używając profilera do zdiagnozowania problemów z aplikacją.  Tradycyjnie ta aplikacja będzie aplikacji pulpitu systemu Windows, ale w tym temacie wiązała się ze Sklepu Windows.  
  
 Biblioteki DLL profilera  
 Jest to składnik, który ładuje do obszaru procesu aplikacji analizowany.  Ten składnik, znanej także jako profilera "wyrazem agent" implementuje [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)[ICorProfilerCallback — interfejs](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md)(2,3, itp.) i wykorzystuje interfejsy [ ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md)(2,3, itp.) interfejsów w celu zbierania danych o analizy aplikacji i potencjalnie zmodyfikować aspekty zachowania aplikacji.  
  
 Profiler interfejsu użytkownika  
 Jest to aplikacja komputerowa, która nastąpi interakcja z użytkownikiem profilera.  Odpowiada za wyświetlanie stanu aplikacji dla użytkownika i nadanie sposób kontrolowania zachowania przeanalizowane aplikacji użytkownika.  Ten składnik jest zawsze uruchamiany w jego własnej przestrzeni procesu, niezależnie od miejsca procesu poddawanego profilowaniu aplikacji.  Profiler interfejsu użytkownika mogą również działać jako "Dołącz wyzwalacza", które jest procesem, który wywołuje [ICLRProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metoda powoduje ładowanie biblioteki DLL profilera w przypadkach, gdy biblioteki DLL profilera nie przeanalizowane aplikacji załadować podczas uruchamiania.  
  
> [!IMPORTANT]
>  Profiler interfejsu użytkownika może pozostawać aplikacji pulpitu systemu Windows, nawet wtedy, gdy jest używana do sterowania i tworzenia raportów dotyczących aplikacji ze Sklepu Windows.  Nie powinien mieć możliwość pakietu i dostarczać własnych narzędzi diagnostycznych w Sklepie Windows.  Narzędzie musi wykonać czynności, które aplikacje ze Sklepu Windows nie może wykonać i wiele z tych problemów znajdują się w Interfejsie użytkownika profilera.  
  
 W tym dokumencie przykładowy kod zakłada się, że:  
  
-   Biblioteki DLL profilera napisano w języku C++, ponieważ musi on być natywnej biblioteki DLL, zgodnie z wymaganiami interfejsu API profilowania środowiska CLR.  
  
-   Profiler interfejsu użytkownika są zapisywane w języku C#.  Nie jest to konieczne, ale ponieważ nie ma żadnych wymagań na język dla procesu Interfejsu użytkownika profilera, dlaczego nie wybierz języku, który jest krótkie i proste?  
  
<a name="RT"></a>   
### <a name="windows-rt-devices"></a>Urządzenia z systemem Windows RT  
 Urządzenia z systemem Windows RT są dość zablokowany.  Po prostu profilery innej firmy nie może być załadowany do tych urządzeń.  Ten dokument koncentruje się na komputerach z systemem Windows 8.  
  
<a name="Consuming"></a>   
## <a name="consuming-windows-runtime-apis"></a>Korzystanie z interfejsów API środowiska wykonawczego systemu Windows  
 W wielu scenariuszach opisanych w poniższych sekcjach aplikacji pulpitu profilera interfejsu użytkownika musi korzystać z nowych interfejsów API środowiska wykonawczego systemu Windows.  Należy zajrzyj do dokumentacji, aby zrozumieć, które interfejsów API środowiska wykonawczego systemu Windows mogą być używane aplikacje, i czy ich zachowanie różni się podczas wywoływana z aplikacji klasycznych i Sklepu Windows apps.  
  
 Jeśli w Interfejsie użytkownika Profiler jest zapisywane w kodzie zarządzanym, będzie wykonanie kilku kroków, które należy zrobić, aby korzystanie z tych łatwe API środowiska uruchomieniowego systemu Windows.  Zobacz [zarządzanych aplikacji klasycznych i środowiska wykonawczego systemu Windows](http://go.microsoft.com/fwlink/?LinkID=271858) artykułu, aby uzyskać więcej informacji.  
  
<a name="Loading"></a>   
## <a name="loading-the-profiler-dll"></a>Podczas ładowania biblioteki DLL profilera  
 W tej sekcji opisano, jak profilera interfejsu użytkownika powoduje, że można załadować biblioteki DLL profilera aplikacji ze Sklepu Windows.  Kod omówione w tej sekcji należy w Twojej aplikacji komputerowej profilera interfejsu użytkownika i dlatego polega na użyciu interfejsów API systemu Windows, które są bezpieczne dla aplikacji klasycznych, ale nie zawsze bezpieczny dla aplikacji ze Sklepu Windows.  
  
 Interfejs użytkownika programu Profiler może spowodować biblioteki DLL profilera być załadowane do obszaru procesu aplikacji na dwa sposoby:  
  
-   Podczas uruchamiania aplikacji, jak kontrolowane przez zmiennych środowiskowych.  
  
-   Przez dołączanie do aplikacji po zakończeniu uruchamiania przez wywołanie metody [ICLRProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md) metody.  
  
 Będzie jeden z Twojego pierwszego roadblocks pobieranie obciążenia uruchamiania i dołączyć ładowania biblioteki DLL profilera, aby działać poprawnie ze Sklepu Windows.  Oba rodzaje ładowania wspólnych udostępnianie pewne specjalne kwestie, więc Zacznijmy z nimi.  
  
<a name="Common"></a>   
### <a name="common-considerations-for-startup-and-attach-loads"></a>Typowe kwestie dotyczące do uruchamiania i Dołącz obciążenia  
 **Podpisywanie biblioteki DLL profilera**  
 System Windows podejmuje próbę załadowania biblioteki DLL profilera, sprawdza, czy biblioteki DLL profilera jest poprawnie podpisany.  Jeśli tak nie jest, obciążenie nie powiedzie się domyślnie. Istnieją dwa sposoby wykonania tej czynności:  
  
-   Upewnij się, że biblioteki DLL profilera jest podpisana.  
  
-   Poinformuj użytkowników o licencji dewelopera konieczności zainstalowania na komputerze z systemem Windows 8 przed użyciem własnych narzędzi.  Można to zrobić automatycznie w programie Visual Studio, lub ręcznie z wiersza polecenia.  Aby uzyskać więcej informacji, zobacz [uzyskać licencji dewelopera](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx).  
  
 **Uprawnienia systemu plików**  
 W Sklepie Windows musi mieć uprawnienie do ładowania i wykonywania biblioteki DLL profilera z lokalizacji w systemie plików, w której znajduje się.  Domyślnie aplikacji ze Sklepu Windows nie ma takich uprawnień na większości katalogów, a wszelkie nieudanej próby załadowania biblioteki DLL profilera utworzy wpis w dzienniku zdarzeń aplikacji systemu Windows, który wygląda następująco:  
  
```Output  
NET Runtime version 4.0.30319.17929 - Loading profiler failed during CoCreateInstance.  Profiler CLSID: '{xxxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx}'.  HRESULT: 0x80070005.  Process ID (decimal): 4688.  Message ID: [0x2504].  
```  
  
 Ogólnie rzecz biorąc aplikacje ze Sklepu Windows mogą tylko dostęp ograniczony zestaw lokalizacji na dysku.  Każda aplikacja ze Sklepu Windows mają dostęp do własnych folderów danych aplikacji, a także kilka innych obszarach, w systemie plików, dla którego wszystkie aplikacje ze Sklepu Windows mają prawo dostępu.  Najlepiej zainstalować biblioteki DLL profilera i jego zależności gdzieś w ramach Program Files lub Program Files (x86), ponieważ wszystkie aplikacje ze Sklepu Windows mają uprawnienia Odczyt i wykonywanie istnieje domyślnie.  
  
<a name="Startup"></a>   
### <a name="startup-load"></a>Uruchamianie obciążenia  
 Zazwyczaj w aplikacji klasycznej profilera interfejsu użytkownika wyświetla monit o obciążenie uruchamiania biblioteki DLL profilera przez inicjowanie blok środowiska wymagane zmiennymi środowiska CLR profilowania API (np. `COR_PROFILER`, `COR_ENABLE_PROFILING`, i `COR_PROFILER_PATH`), a następnie utworzenie nowego procesu z tego bloku środowiska.  To samo dotyczy aplikacji do Sklepu Windows, ale mechanizmy są różne.  
  
 **Nie należy uruchamiać z podwyższonym poziomem uprawnień**  
 Jeśli proces próbuje zduplikować aplikacji ze Sklepu Windows B proces, proces A powinna być uruchomiona w integralności średnia poziomu, nie na poziomie integralności wysoka, (tj. nie z podwyższonym poziomem uprawnień).  Oznacza to, że Profiler interfejsu użytkownika powinna być uruchomiona na poziomie integralności średnia lub musi zduplikować inny proces pulpitu na poziomie integralności średnia automatyzującą uruchamianie aplikacji ze Sklepu Windows.  
  
 **Wybieranie do profilu aplikacji ze Sklepu Windows**  
 Najpierw należy poprosić użytkownika programu profiler do uruchomienia aplikacji Sklepu Windows.  Dla aplikacji klasycznych prawdopodobnie będzie wyświetlić okna dialogowego przeglądania plików, a użytkownik może znaleźć i wybrać plik .exe.  Jednak aplikacje ze Sklepu Windows są różne, a za pomocą okna dialogowego przeglądania nie ma sensu.  Zamiast tego lepiej jest wyświetlane użytkownikowi listę zainstalowane dla danego użytkownika można wybierać aplikacje ze Sklepu Windows.  
  
 Można użyć [klasy PackageManager](https://msdn.microsoft.com/library/windows/apps/windows.management.deployment.packagemanager.aspx) do generowania tej listy.  `PackageManager`jest klasą środowiska wykonawczego systemu Windows, która jest dostępna dla aplikacji klasycznych, a w rzeczywistości jest *tylko* dostępne dla aplikacji klasycznych.  
  
 W poniższym przykładzie kod produktu z hipotetyczny interfejsu użytkownika programu profilującego zapisywane jako aplikacji klasycznej w języku C# yses `PackageManager` aby wygenerować listę aplikacji systemu Windows:  
  
```csharp  
string currentUserSID = WindowsIdentity.GetCurrent().User.ToString();  
IAppxFactory appxFactory = (IAppxFactory) new AppxFactory();  
PackageManager packageManager = new PackageManager();  
IEnumerable<Package> packages = packageManager.FindPackagesForUser(currentUserSID);  
```  
  
 **Określanie blok środowiska niestandardowych**  
 Nowy interfejs COM [IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx), można go dostosować sposób wykonywania aplikacji Sklepu Windows, aby ułatwić niektórych formularzy diagnostyki.  Jeden z jego metody [EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=vs.85\).aspx), można przekazać blok środowiska aplikacji ze Sklepu Windows, po uruchomieniu, oraz inne przydatne efektów, jak wyłączenie zawieszenia proces automatycznego.  Blok środowiska to ważne, ponieważ jest to, gdzie należy określić zmienne środowiskowe (`COR_PROFILER`, `COR_ENABLE_PROFILING`, i `COR_PROFILER_PATH)`) używana przez środowisko CLR w celu załadowania biblioteki DLL profilera.  
  
 Rozważmy poniższy fragment kodu:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, debuggerCommandLine,   
                                                                 (IntPtr)fixedEnvironmentPzz);  
```  
  
 Istnieje kilka elementów, które będą potrzebne, aby uzyskać prawo:  
  
-   `packageFullName`można określić podczas Iterowanie za pośrednictwem pakietów i przechwytywanie `package.Id.FullName`.  
  
-   `debuggerCommandLine`jest bardziej interesujące.  Aby przekazać blok środowiska niestandardowych do aplikacji ze Sklepu Windows, należy napisać własny, simplistic fikcyjny debugera.  Tarła Windows aplikacji ze Sklepu Windows zawieszone, a następnie dołącza debuger przez uruchamianie debugera przy użyciu wiersza polecenia takich jak w tym przykładzie:  
  
    ```Output  
    MyDummyDebugger.exe -p 1336 -tid 1424  
    ```  
  
     gdzie `-p 1336` oznacza aplikacji ze Sklepu Windows ma 1336 identyfikator procesu, a `-tid 1424` oznacza 1424 identyfikator wątku jest wstrzymanym wątku.  Fikcyjny debuger może przeanalizować identyfikator wątku, w wierszu polecenia, Wznów wątek, a następnie zamknij.  
  
     Oto niektóre kod w języku C++ w tym przykładzie (należy pamiętać o dodaniu sprawdzanie błędów!):  
  
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
  
     Należy wdrożyć ten debuger fikcyjny jako część instalacji narzędzia diagnostyczne, a następnie określ ścieżkę do tego debugera w `debuggerCommandLine` parametru.  
  
 **Uruchamianie aplikacji ze Sklepu Windows**  
 Na koniec dotarła chwilę, aby uruchomić aplikację w Sklepie Windows. Jeśli już już próbowałeś czynności samodzielnie, można zauważyć, że [CreateProcess](https://msdn.microsoft.com/library/windows/desktop/ms682425\(v=vs.85\).aspx) nie sposób tworzą procesu aplikacji Sklepu Windows.  Zamiast tego należy użyć [IApplicationActivationManager::ActivateApplication](https://msdn.microsoft.com/library/windows/desktop/Hh706903\(v=vs.85\).aspx) metody.  Aby to zrobić, należy uzyskać identyfikator modelu użytkownika aplikacji do Sklepu Windows, który uruchamiany jest aplikacji.  I oznacza to, że musisz wykonać nieco tu przeszukuje przez manifest.  
  
 Podczas Iterowanie za pośrednictwem pakietów (zobacz "Wybieranie magazynu aplikacji do profilu Windows" w [obciążenia uruchamiania](#Startup) wcześniejszej sekcji), należy do pobrania zestaw aplikacji zawarte w manifeście bieżący pakiet:  
  
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
  
 Tak, jeden pakiet może mieć wielu aplikacji, a każda aplikacja ma własny identyfikator modelu użytkownika aplikacji.  Dlatego należy poprosić użytkownika do profilu aplikację i wystarczy pobrać identyfikator modelu użytkownika aplikacji z tej konkretnej aplikacji:  
  
```csharp  
while (appsEnum.GetHasCurrent() != 0)  
{  
    IAppxManifestApplication app = appsEnum.GetCurrent();  
    string appUserModelId = app.GetAppUserModelId();  
…  
```  
  
 Na koniec masz teraz co jest potrzebne do uruchomienia aplikacji ze Sklepu Windows:  
  
```csharp  
IApplicationActivationManager appActivationMgr = new ApplicationActivationManager();  
appActivationMgr.ActivateApplication(appUserModelId, appArgs, ACTIVATEOPTIONS.AO_NONE, out pid);  
```  
  
 **Pamiętaj, aby wywołać DisableDebugging**  
 Gdy wywoływana [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx), wprowadzone promise, który będzie oczyszczanie po sobie przez wywołanie metody [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) metody, dlatego należy wykonać które po zakończeniu sesji profilowania.  
  
<a name="Attach"></a>   
### <a name="attach-load"></a>Dołącz obciążenia  
 Po Interfejsie profilera chce dołączyć jego biblioteki DLL profilera do aplikacji, która została już rozpoczęta uruchomiona, za pomocą [ICLRProfiling::AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md).  To samo z aplikacji ze Sklepu Windows.  Ale oprócz typowe kwestie wymagające rozważenia podanych wcześniej, upewnij się, że docelowy aplikacji ze Sklepu Windows nie jest wstrzymana.  
  
 **EnableDebugging**  
 Podobnie jak w przypadku uruchamiania obciążenia, należy wywołać [IPackageDebugSettings::EnableDebugging](https://msdn.microsoft.com/library/hh438395\(v=VS.85\).aspx) metody.  Nie będzie potrzebny do przekazywania blok środowiska, ale należy jej innych funkcji: wyłączanie procesu automatycznego zawieszenia.  W przeciwnym razie po Interfejsie profilera [AttachProfiler](../../../../docs/framework/unmanaged-api/profiling/iclrprofiling-attachprofiler-method.md), może zostać zawieszone docelowej aplikacji ze Sklepu Windows.  W rzeczywistości to prawdopodobnie, jeśli użytkownik jest teraz interakcji z profilera interfejsu użytkownika i aplikacji ze Sklepu Windows nie jest aktywny na wszystkich ekranach użytkownika.  I jeśli Sklepu Windows, aplikacja jest wstrzymana, nie będzie mogą odpowiadać dowolnej sygnał środowiska CLR i wysyła do niego dołączyć biblioteki DLL profilera.  
  
 Dlatego należy wykonać podobny do następującego:  
  
```csharp  
IPackageDebugSettings pkgDebugSettings = new PackageDebugSettings();  
pkgDebugSettings.EnableDebugging(packgeFullName, null /* debuggerCommandLine */,   
                                                                 IntPtr.Zero /* environment */);  
```  
  
 To samo wywołanie, które spowodowałoby w przypadku obciążenia uruchamiania, ale nie zostanie określona, wiersz polecenia debugera lub blok środowiska.  
  
 **DisableDebugging**  
 Zawsze, nie zapomnij wywołać [IPackageDebugSettings::DisableDebugging](https://msdn.microsoft.com/library/hh438394\(v=vs.85\).aspx) zakończenia sesji profilowania.  
  
<a name="Running"></a>   
## <a name="running-inside-the-windows-store-app"></a>Używany w aplikacji ze Sklepu Windows  
 Dlatego aplikacji ze Sklepu Windows na koniec załadował biblioteki DLL profilera.  Teraz biblioteki DLL profilera musi organizowane jednocześnie odtwarzanie przez różne reguły wymagane przez aplikacje ze Sklepu Windows, w tym które interfejsy API są dopuszczalne i sposób uruchamiania z zmniejszona uprawnienia.  
  
<a name="APIs"></a>   
### <a name="stick-to-the-windows-store-app-apis"></a>Trzymaj do interfejsów API aplikacji Sklepu Windows  
 Podczas przeglądania interfejsu API systemu Windows, można zauważyć, że każdy interfejs API jest udokumentowany jako mające zastosowanie do aplikacji klasycznych i aplikacji ze Sklepu Windows.  Na przykład **wymagania** części dokumentacji dla [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) funkcji wskazuje, że funkcja dotyczy tylko aplikacji klasycznych. Z kolei [InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx) funkcja jest dostępna dla aplikacji klasycznych i aplikacji ze Sklepu Windows.  
  
 Podczas tworzenia biblioteki DLL profilera, je traktować jak w przypadku aplikacji ze Sklepu Windows i używać tylko interfejsów API, które są udokumentowane jako dostępne dla aplikacji ze Sklepu Windows.  Analizowanie zależności (na przykład można uruchomić `link /dump /imports` względem biblioteki DLL profilera inspekcja), a następnie Wyszukaj dokumenty, które zależności są ok, a które nie są.  W większości przypadków naruszeń zasad można naprawić, zastępując po prostu nowszej formularza interfejsu API, które są udokumentowane jako bezpieczny (na przykład, zastępując [InitializeCriticalSectionAndSpinCount](https://msdn.microsoft.com/library/windows/desktop/ms683476\(v=vs.85\).aspx) z [ InitializeCriticalSectionEx](https://msdn.microsoft.com/library/windows/desktop/ms683477\(v=vs.85\).aspx)).  
  
 Można zauważyć, że biblioteki DLL profilera wywołuje niektórych interfejsów API, które dotyczą tylko aplikacji klasycznych, a jeszcze wydają się do pracy, nawet gdy załadować biblioteki DLL profilera wewnątrz aplikacji ze Sklepu Windows.  Należy pamiętać, że ryzykowne za pomocą dowolnego interfejsu API nie jest udokumentowany do użycia z aplikacji ze Sklepu Windows w bibliotece DLL profilera, gdy ładowany do procesu aplikacji Sklepu Windows:  
  
-   Takie interfejsów API nie ma gwarancji działa, gdy wywoływany w kontekście unikatowy uruchomionymi w aplikacji ze Sklepu Windows.  
  
-   Takie interfejsy API mogą nie działać spójnie, po wywołany z poziomu różnych procesów aplikacji Sklepu Windows.  
  
-   Tych interfejsów API wydaje działały prawidłowo w aplikacji ze Sklepu Windows w bieżącej wersji systemu Windows, ale mogą być dzielone lub można wyłączyć w przyszłych wersjach systemu Windows.  
  
 Najważniejsze wskazówki jest Usuń wszystkie naruszenia zasad i uniknąć ryzyka.  
  
 Może się okazać absolutnie nie można wykonywać bez określonego interfejsu API i nie można odnaleźć zastępczy odpowiedni dla aplikacji ze Sklepu Windows.  W takim przypadku co najmniej:  
  
-   Testowanie, testowanie i przetestować daylights życia poza użycie tego interfejsu API.  
  
-   Zrozumienie interfejsu API może nagle Podziel lub znikają, gdy jest wywoływana z wewnątrz Sklepu Windows apps w przyszłych wersjach systemu Windows.  To nie należy rozważyć zastosowanie problem ze zgodnością przez firmę Microsoft, a obsługa użycie jej nie będzie priorytet.  
  
<a name="Permissions"></a>   
### <a name="reduced-permissions"></a>Ograniczonymi uprawnieniami  
 Jest poza zakresem tego tematu, aby wyświetlić listę wszystkich metod, które uprawnienia aplikacji Sklepu Windows różnią się od aplikacji klasycznych.  Ale pewnością zachowanie różnych za każdym razem, gdy próbuje dostępu do żadnych zasobów biblioteki DLL profilera (jeśli jest ładowany w porównaniu do aplikacji klasycznej aplikacji ze Sklepu Windows).  System plików jest najbardziej typowym przykładem.  Istnieją, ale niektóre miejsca na dysku, który może uzyskać dostępu do danej aplikacji ze Sklepu Windows (zobacz [plików dostępu i uprawnienia (środowiska wykonawczego systemu Windows](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)), a biblioteki DLL profilera będą takie same ograniczenia.  Dokładnie przetestuj kodu.  
  
<a name="Interprocess"></a>   
### <a name="inter-process-communication"></a>Komunikacja między procesami  
 Jak pokazano na diagramie na początku tego dokumentu, biblioteki DLL profilera (załadowane do obszaru procesu aplikacji Sklepu Windows) będzie prawdopodobnie muszą komunikować się z profilera interfejsu użytkownika (uruchomionego w obszarze procesu oddzielne aplikacji komputerowej) za pomocą własnego niestandardowego procesu między kanał komunikacyjny (IPC).  Interfejs użytkownika profilera wysyła sygnały do biblioteki DLL profilera, aby zmodyfikować zachowanie, a biblioteki DLL profilera wysyła dane z analizy aplikacji ze Sklepu Windows z powrotem do interfejsu użytkownika programu profilującego do przetwarzania końcowego i wyświetlania użytkownikowi profilera.  
  
 Większość profilery muszą działać w ten sposób, ale opcje dla mechanizmów IPC są bardziej ograniczone, podczas ładowania biblioteki DLL profilera do aplikacji ze Sklepu Windows.  Na przykład nazwane potoki nie są częścią aplikacji ze Sklepu Windows SDK, więc nie można ich używać.  
  
 Ale oczywiście plików są nadal w, choć w sposób bardziej ograniczone.  Dostępne są zdarzenia.  
  
 **Komunikację za pomocą plików**  
 Większość danych prawdopodobnie przechodzą między DLL profilera i Profiler interfejsu użytkownika za pomocą plików.  Klucz jest pobranie lokalizacji pliku zarówno biblioteki DLL profilera (w kontekście aplikacji ze Sklepu Windows), jak i interfejs użytkownika profilera mają odczytu i zapisu do.  Na przykład ścieżka folderu tymczasowego to lokalizacji, która jest dostępna zarówno biblioteki DLL profilera, jak i interfejs użytkownika profilera, ale nie inne pakiet aplikacji Sklepu Windows mogą uzyskiwać dostęp do (chroniąc informacje logowania z innymi pakietami aplikacji Sklepu Windows).  
  
 Zarówno profilera interfejsu użytkownika, jak i biblioteki DLL profilera można określić tę ścieżkę niezależnie.  UI profilera, gdy jego iterację wszystkie pakiety zainstalowane dla bieżącego użytkownika (patrz przykładowy kod wcześniej), uzyskuje dostęp do `PackageId` klasy, z którego ścieżkę do folderu tymczasowego mogą pochodzić z kodem, podobnie jak ta Wstawka kodu.  (Jak zawsze sprawdzanie błędów został pominięty w celu jego skrócenia.)  
  
```csharp  
// C# code for the Profiler UI.  
ApplicationData appData =  
    ApplicationDataManager.CreateForPackageFamily(  
        packageId.FamilyName);  
  
tempDir = appData.TemporaryFolder.Path;  
```  
  
 W tym samym czasie biblioteki DLL profilera można zasadniczo tak samo postąpić, chociaż może więcej łatwo uzyskać dostęp do [ApplicationData](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.aspx) przy użyciu [ApplicationData.Current](https://msdn.microsoft.com/library/windows/apps/windows.storage.applicationdata.current.aspx) właściwości.  
  
 **Komunikację za pomocą zdarzeń**  
 Chcąc proste semantyki sygnalizowania między profilera interfejsu użytkownika a biblioteki DLL profilera, można użyć w aplikacji ze Sklepu Windows, a także aplikacji klasycznych zdarzenia.  
  
 Z biblioteki DLL profilera, możesz po prostu wywołać [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx) funkcji do utworzenia nazwanego zdarzenia z dowolną nazwę.  Na przykład:  
  
```cpp  
// Profiler DLL in Windows Store app (C++).  
CreateEventEx(   
    NULL,  // Not inherited  
    "MyNamedEvent"  
    CREATE_EVENT_MANUAL_RESET, /* explicit ResetEvent() required; leave initial state unsignaled */  
    EVENT_ALL_ACCESS);  
```  
  
 Następnie Interfejsie profilera musi znaleźć nazwanego zdarzenia w przestrzeni nazw aplikacji do Sklepu Windows.  Na przykład można wywołać interfejsu użytkownika programu profilującego [CreateEventEx](https://msdn.microsoft.com/library/windows/desktop/ms682400\(v=vs.85\).aspx), określając nazwę zdarzenia jako  
  
 `AppContainerNamedObjects\<acSid>\MyNamedEvent`  
  
 `<acSid>`jest identyfikator SID AppContainer aplikacji do Sklepu Windows.  Wcześniejszej sekcji tego tematu pokazano, jak przejść przez pakiety zainstalowane dla bieżącego użytkownika.  W tym przykładowym kodzie mogą uzyskać packageId.  I z pakietu, można uzyskać `<acSid>` z kodem podobny do następującego:  
  
```csharp  
IntPtr acPSID;  
DeriveAppContainerSidFromAppContainerName(packageId.FamilyName, out acPSID);  
  
string acSid;  
ConvertSidToStringSid(acPSID, out acSid);  
  
string acDir;  
GetAppContainerFolderPath(acSid, out acDir);  
```  
  
<a name="Shutdown"></a>   
### <a name="no-shutdown-notifications"></a>Brak powiadomień zamknięcia  
 Gdy jest używany w aplikacji ze Sklepu Windows, biblioteki DLL profilera nie będą miały albo [ICorProfilerCallback::Shutdown](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-shutdown-method.md) lub nawet [DllMain](https://msdn.microsoft.com/library/windows/desktop/ms682583\(v=vs.85\).aspx) (z `DLL_PROCESS_DETACH`) wywoływana w celu powiadomienia biblioteki DLL profilera czy zamykanie aplikacji ze Sklepu Windows.  W rzeczywistości należy oczekiwać, że nigdy nie zostanie wywołana.  W przeszłości wielu biblioteki DLL profilera użyto te powiadomienia jako wygodny miejsca aby opróżnić pamięć podręczną na dysku, zamykanie plików, wysyłania powiadomień do interfejsu użytkownika programu profilującego itp.  Ale teraz biblioteki DLL profilera musi być nieco inaczej zorganizowany.  
  
 Biblioteki DLL profilera powinny być rejestrowane informacje, ponieważ przechodzi ona.  Ze względu na wydajność warto partii informacje w pamięci i opróżnić go na dysku wraz z rozwojem partii rozmiar poza niektóre wartości progowej.  Ale zakłada, że wszystkie informacje, które nie zostały jeszcze opróżniane mogą zostać utracone.  Oznacza to należy do pobrania z próg rozsądny sposób i Interfejsie użytkownika profilera musi zaostrzonego radzenia sobie z pełnych informacji o napisane przez biblioteki DLL profilera.  
  
<a name="Metadata"></a>   
## <a name="windows-runtime-metadata-files"></a>Pliki metadanych środowiska wykonawczego systemu Windows  
 Jest ona poza zakres tego dokumentu, aby przejść do szczegółów na jakie metadane środowiska wykonawczego systemu Windows (WinMD) plików.    W tej sekcji jest ograniczona do zachowaniem API profilowania CLR plików WinMD są ładowane przez aplikacji do Sklepu Windows, które analizuje biblioteki DLL profilera.  
  
<a name="WMDs"></a>   
### <a name="managed-and-non-managed-winmds"></a>Metadanych Winmd zarządzanych i niezarządzanych  
 Jeśli dewelopera za pomocą programu Visual Studio Utwórz nowy projekt składnika środowiska wykonawczego systemu Windows, kompilacja projektu tworzy plik WinMD, który opisuje metadane (nazwy typu klasy, interfejsy, itp.) utworzone przez dewelopera.  Jeśli ten projekt jest projektem zarządzanego języka napisany w językach C# i VB, ten sam plik WinMD zawiera również stosowania tych typów (co oznacza, że zawiera on wszystkie IL skompilowanych z dewelopera kodu źródłowego).  Takie pliki są określane jako zarządzanych plików WinMD.  Są one interesujące, że zawierają one metadane środowiska wykonawczego systemu Windows i ta implementacja.  
  
 Z kolei jeśli dewelopera tworzy projekt składnika środowiska wykonawczego systemu Windows dla języka C++, kompilacja projektu tworzy plik WinMD, który zawiera tylko metadane i implementacja jest kompilowany do oddzielnych natywnej biblioteki DLL.  Podobnie plików WinMD, które są dostarczane w zestawie SDK systemu Windows zawierają tylko metadane z implementacją skompilowany w oddzielnych natywnych bibliotek DLL, które są dostarczane jako część systemu Windows.  
  
 Poniższe informacje dotyczy to zarówno zarządzanych metadanych Winmd, zawierających metadanych i implementacji, oraz metadanych niezarządzanych Winmd, który zawiera tylko metadane.  
  
<a name="CLRModules"></a>   
### <a name="winmd-files-look-like-clr-modules"></a>Plików WinMD wyglądać modułów środowiska CLR  
 Jeśli chodzi o CLR, wszystkie pliki WinMD to moduły.  API — profilowanie CLR w związku z tym informuje biblioteki DLL profilera, gdy ładowanie plików WinMD i jakie ich ModuleIDs, w taki sam sposób jak w przypadku innych modułów zarządzanych.  
  
 Biblioteki DLL profilera można rozróżnić plików WinMD z innymi modułami wywołując [ICorProfilerInfo3::GetModuleInfo2](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-getmoduleinfo2-method.md) — metoda i zapoznanie się `pdwModuleFlags` output parametr [COR_PRF_MODULE_WINDOWS_ Środowisko URUCHOMIENIOWE](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) flagi.  (Jest ustawiona tylko wtedy, gdy ModuleID reprezentuje WinMD.)  
  
<a name="Reading"></a>   
### <a name="reading-metadata-from-winmds"></a>Odczytywanie metadanych z metadanych Winmd  
 Plików WinMD, takich jak moduły regularne zawierać metadane, który może zostać odczytany przez [interfejsy API metadanych](../../../../docs/framework/unmanaged-api/metadata/index.md).  Jednak CLR mapowania typów środowiska wykonawczego systemu Windows do typów .NET Framework, podczas wczytywania WinMD plików, dzięki czemu deweloperzy, którzy programów w kodzie zarządzanym i korzystanie z pliku WinMD może mieć bardziej naturalne środowisko programowania.  Niektóre przykłady te mapowania można znaleźć [.NET Framework pomocy technicznej dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md).  
  
 Dlatego widok profilera otrzyma podczas używania interfejsów API metadanych: pierwotny widok środowiska wykonawczego systemu Windows lub zamapowanego widoku .NET Framework?  Odpowiedź: jest użytkownik.  
  
 Podczas wywoływania [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) metoda WinMD można uzyskać interfejsu metadane, takie jak [IMetaDataImport](../../../../docs/framework/unmanaged-api/metadata/imetadataimport-interface.md), możesz ustawić [ofNoTransform](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md)w `dwOpenFlags` parametr, aby wyłączyć to mapowanie.  W przeciwnym razie domyślnie mapowanie zostaną włączone.  Zazwyczaj profiler zachowa mapowania włączone, tak, aby ciągów, które uzyskuje dostęp do biblioteki DLL profilera z metadanych WinMD (na przykład nazwy typów) będzie wyglądać znanego i fizyczne użytkownikowi profilera.  
  
<a name="Modifying"></a>   
### <a name="modifying-metadata-from-winmds"></a>Modyfikowanie metadanych z metadanych Winmd  
 Modyfikowanie metadanych w metadanych Winmd nie jest obsługiwane.  Jeśli należy wywołać [ICorProfilerInfo::GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) metoda to WinMD pliku i określ [ofWrite](../../../../docs/framework/unmanaged-api/metadata/coropenflags-enumeration.md) w `dwOpenFlags` parametru lub poproś o interfejsu zapisywalny metadanych, takich jak [ IMetaDataEmit](../../../../docs/framework/unmanaged-api/metadata/imetadataemit-interface.md), [GetModuleMetaData](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-getmodulemetadata-method.md) zakończy się niepowodzeniem.  Jest to szczególnie ważne, aby ponowne zapisywanie IL profilowania, które należy zmodyfikować metadanych do obsługi ich Instrumentacji (na przykład, aby dodać AssemblyRefs lub nowych metod).  Dlatego należy sprawdzić, czy [COR_PRF_MODULE_WINDOWS_RUNTIME](../../../../docs/framework/unmanaged-api/profiling/cor-prf-module-flags-enumeration.md) najpierw (zgodnie z opisem w poprzedniej sekcji) i powstrzymania z prośbą o interfejsy metadanych zapisywalny dla tych modułów.  
  
<a name="Resolving"></a>   
### <a name="resolving-assembly-references-with-winmds"></a>Rozpoznawanie odwołania do zestawów z metadanych Winmd  
 Profilery wiele należy rozpoznać odwołania do metadanych ręcznie, aby pomóc w Instrumentacji lub typu inspekcji.  Takie profilowania trzeba znać sposób CLR usuwa odwołania do zestawów, które wskazują metadanych Winmd, ponieważ te odwołania są rozpoznawane w sposób całkowicie innego niż odwołania do zestawów standardowa.  
  
<a name="Profilers"></a>   
## <a name="memory-profilers"></a>Profilowania pamięci  
 Moduł zbierający elementy bezużyteczne i sterty zarządzanej nie są różni się w aplikacji ze Sklepu Windows i aplikacji komputerowej.  Istnieją pewne niewielkie różnice profilera wymagane przez autorów pod uwagę.  
  
<a name="ForceGC"></a>   
### <a name="forcegc-creates-a-managed-thread"></a>ForceGC tworzy zarządzanych wątków  
 Podczas profilowania pamięci, biblioteki DLL profilera tworzonych zwykle oddzielnym wątku, z którego można wywołać [ForceGC — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) metody.  Jest to żadne nowe.  Ale, które mogą być zaskakująco jest czynnością czynności wyrzucania elementów bezużytecznych wewnątrz aplikacji ze Sklepu Windows mogą przekształcenie z wątku do zarządzanego wątku (na przykład identyfikator interfejsu API wątku profilowania zostaną utworzone dla tego wątku).  
  
 Do zrozumienia konsekwencji tego, należy poznać różnice między wywołania synchroniczne i asynchroniczne, zgodnie z definicją w interfejsie API profilowania środowiska CLR. Należy pamiętać, że jest to bardzo różnią się od pojęcia wywołania asynchroniczne w aplikacji ze Sklepu Windows.  Zobacz wpis w blogu [Dlaczego mamy CORPROF_E_UNSUPPORTED_CALL_SEQUENCE](https://blogs.msdn.microsoft.com/davbr/2008/12/23/why-we-have-corprof_e_unsupported_call_sequence/) Aby uzyskać więcej informacji.  
  
 Właściwego punktu jest, że wywołania utworzone przez profilera wątki są zawsze traktowane jako synchroniczne, nawet w przypadku tych wywołań z poza wykonanie jednej z biblioteki DLL profilera [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody.  Co najmniej, które używane w przypadku.  Teraz, gdy środowisko CLR wyłączył wątek programu profiler do zarządzanego wątku z powodu wywołania do [ForceGC — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md), że wątek nie jest już jest uważany za wątek programu profiler.  W efekcie CLR wymusza bardziej rygorystyczne definicji kwalifikuje się jako synchroniczne dla tego wątku, co — mianowicie który wywołanie muszą pochodzić od wewnątrz jednej biblioteki DLL profilera [ICorProfilerCallback](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-interface.md) metody służące do kwalifikowania jako synchroniczne.  
  
 Co to znaczy w praktyce  Większość [ICorProfilerInfo](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-interface.md) metody tylko są bezpieczne ma być wywoływana synchronicznie i natychmiast nie powiedzie się inaczej.  Dlatego w przypadku ponownie używa biblioteki DLL profilera z [ForceGC — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) wątku dla innych wywołań zwykle w wątkach utworzone profilera (na przykład, aby [RequestProfilerDetach](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo3-requestprofilerdetach-method.md), [RequestReJIT](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrejit-method.md), lub [RequestRevert](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo4-requestrevert-method.md)), możesz zacząć problemów.  Nawet funkcji asynchronicznych bezpieczne takich jak [DoStackSnapshot](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo2-dostacksnapshot-method.md) ma reguły specjalne przy wywołaniach z wątków zarządzanych. (Zobacz wpis w blogu [stosie profilera: podstawy i](https://blogs.msdn.microsoft.com/davbr/2005/10/06/profiler-stack-walking-basics-and-beyond/) Aby uzyskać więcej informacji.)  
  
 Dlatego zaleca się którymkolwiek wątku tworzy bibliotekę DLL profilera do wywołania [ForceGC — metoda](../../../../docs/framework/unmanaged-api/profiling/icorprofilerinfo-forcegc-method.md) powinna być używana *tylko* wyłącznie w celu wyzwalania wykazów globalnych, a następnie odpowiada na żądania wywołania zwrotne GC.  Nie należy wywoływać w interfejsie API profilowania wykonywanie innych zadań, takich jak stosu próbki lub odłączanie.  
  
<a name="WeakTable"></a>   
### <a name="conditionalweaktablereferences"></a>ConditionalWeakTableReferences  
 Począwszy od programu .NET Framework 4.5 jest nowe wywołanie zwrotne GC, [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md), które powoduje profilera ukończyć więcej informacji o *zależnych uchwytów*. Uchwyty skutecznie Dodaj odwołanie z obiektem źródłowym do obiektu docelowego na potrzeby Zarządzanie okresem istnienia GC.  Uchwyty zależne są żadne nowe i deweloperów, którzy programów w kodzie zarządzanym mógł utworzyć własne zależnych dojść przy użyciu <xref:System.Runtime.CompilerServices.ConditionalWeakTable%602?displayProperty=nameWithType> klasy nawet przed systemu Windows 8 i .NET Framework 4.5.  
  
 Zarządzane aplikacje Sklepu Windows w języku XAML należy teraz obciążona dojść zależnych.  W szczególności CLR używa ich, aby pomóc w zarządzaniu cykle odwołania między obiektami zarządzanych i niezarządzanych środowiska wykonawczego systemu Windows.  Oznacza to, że jest ważniejsza teraz kiedykolwiek do profilowania pamięci mieć świadomość uchwyty zależnych, dzięki czemu można można zwizualizować wraz z resztą krawędzi na wykresie sterty.  Należy używać biblioteki DLL profilera [RootReferences2](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback2-rootreferences2-method.md), [ObjectReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback-objectreferences-method.md), i [ConditionalWeakTableElementReferences](../../../../docs/framework/unmanaged-api/profiling/icorprofilercallback5-conditionalweaktableelementreferences-method.md) ze sobą w celu ukończenia widoku wykresu sterty formularz .  
  
<a name="Conclusion"></a>   
## <a name="conclusion"></a>Wniosek  
 Istnieje możliwość analizy kodu zarządzanego działającego w aplikacji ze Sklepu Windows za pomocą interfejsu API profilowania środowiska CLR.  W rzeczywistości można podjąć istniejących profilera, który projektujesz i wprowadzić kilka zmian określonych, dzięki czemu można kierować aplikacji ze Sklepu Windows.   Profiler interfejsu użytkownika należy używać nowych interfejsów API do aktywacji w trybie debugowania aplikacji ze Sklepu Windows.  Upewnij się, że biblioteki DLL profilera wykorzystuje tylko API odpowiednich dla aplikacji ze Sklepu Windows.  Mechanizm komunikacji między profilera interfejsu użytkownika i biblioteki DLL profilera, na których mają być zapisywane z ograniczenia interfejsu API aplikacji Sklepu Windows na uwadze i świadomości ograniczone uprawnienia w przypadku aplikacji ze Sklepu Windows.  Biblioteki DLL profilera należy zwrócić uwagę sposób CLR traktuje metadanych Winmd, i jak moduł Garbage Collector jest różny w odniesieniu do zarządzanych wątków.  
  
<a name="Resources"></a>   
## <a name="resources"></a>Resources  
 **Środowisko uruchomieniowe języka wspólnego**  
 -   [Dokumentacja interfejsu API profilowania CLR](../../../../docs/framework/unmanaged-api/profiling/index.md)  
  
-   [Dokumentacja interfejsu API metadanych CLR](../../../../docs/framework/unmanaged-api/metadata/index.md)  
  
 **CLR interakcji z środowiska uruchomieniowego systemu Windows**  
 [Obsługa programu .NET Framework dla aplikacji ze Sklepu Windows i środowiska wykonawczego systemu Windows](../../../../docs/standard/cross-platform/support-for-windows-store-apps-and-windows-runtime.md)  
  
 **Aplikacje ze Sklepu Windows**  
 -   [Dostęp do plików i uprawnienia (aplikacje ze środowiska wykonawczego systemu Windows](https://msdn.microsoft.com/library/windows/apps/hh967755.aspx)  
  
-   [Uzyskać licencji dewelopera](https://msdn.microsoft.com/library/windows/apps/Hh974578.aspx)  
  
-   [Interfejs IPackageDebugSettings](https://msdn.microsoft.com/library/hh438393\(v=vs.85\).aspx)  
  
## <a name="see-also"></a>Zobacz też  
 [Profilowanie](../../../../docs/framework/unmanaged-api/profiling/index.md)
