---
title: Profilowanie środowiska uruchomieniowego
ms.date: 03/30/2017
helpviewer_keywords:
- performance counters
- common language runtime, profiling
- Perfmon.exe
- System Monitor
- profiling
- runtime, profiling
- profiling applications
- Performance Console
ms.assetid: ccd68284-f3a8-47b8-bc3f-92e5fe3a1640
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2486316cf582da09eaa8998d06efb8a4e4ea3a88
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 08/22/2019
ms.locfileid: "69967211"
---
# <a name="runtime-profiling"></a>Profilowanie środowiska uruchomieniowego
Profilowanie to metoda zbierania danych wydajności w dowolnym scenariuszu opracowywania i wdrażania. Ta sekcja jest przeznaczony dla deweloperów i administratorów systemu, którzy chcą zbierać informacje o wydajności aplikacji.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Śledzenie wydajności przy użyciu Monitora wydajności (Perfmon. exe)  
 Monitor wydajności jest najłatwiejszym narzędziem służącym do profilowania aplikacji .NET Framework. Monitor wydajności graficzny przedstawia dane znajdujące się w .NET Framework licznikach wydajności, które są instalowane przy użyciu środowiska uruchomieniowego języka wspólnego i Windows SDK. Te liczniki mogą służyć do monitorowania wszystkiego od zarządzania pamięcią do wydajności kompilatora just-in-Time (JIT). Poinformują o zasobach używanych przez aplikację, które są pośrednią miarą wydajności aplikacji. Użyj tych liczników, aby zrozumieć, w jaki sposób aplikacja działa wewnętrznie.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Aby uruchomić Perfmon. exe w systemie Windows Vista i nowszych wersjach  
  
1. W wierszu polecenia wpisz polecenie **perfmon**. Zostanie wyświetlona konsola **monitora wydajności** .  
  
2. W folderze **narzędzia monitorowania** kliknij przycisk **Monitor wydajności**.  
  
3. Na pasku narzędzi monitora wydajności kliknij ikonę **Dodaj** (znak plus), jeśli jest obecny. Jeśli go nie ma, kliknij prawym przyciskiem myszy w oknie monitorowanie i wybierz opcję **Dodaj liczniki** .  
  
     Spowoduje to otwarcie okna dialogowego **Dodawanie liczników** . W polu listy **dostępne liczniki** są wyświetlane dostępne obiekty wydajności. Istnieje wiele wstępnie zdefiniowanych obiektów dla .NET Framework aplikacji, w tym tych dla zarządzania pamięcią (**pamięć programu .NET CLR**), współdziałanie (**Architektura .NET CLR Interop**), obsługa wyjątków (**wyjątki środowiska .NET CLR**) i wielowątkowość ( **.NET CLR LocksAndThreads**). Każdy obiekt wydajności zawiera szereg poszczególnych liczników wydajności. Listę liczników wydajności dostępnych w Monitorze wydajności można znaleźć w temacie [liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
4. Zaznacz pole wyboru obok nazwy obiektu wydajności, aby wyświetlić listę poszczególnych obsługiwanych liczników wydajności.  
  
5. Kliknij licznik wydajności, który chcesz wyświetlić.  
  
6. W polu listy **wystąpienia wybranego obiektu** kliknij pozycję  **\<wszystkie wystąpienia >** , aby określić, że chcesz monitorować licznik wydajności dla środowiska uruchomieniowego CLR globalnie (to znaczy na poziomie całego systemu).  
  
     —lub—  
  
     W polu listy **wystąpienia wybranego obiektu** kliknij nazwę aplikacji, aby monitorować licznik wydajności dla tej aplikacji.  
  
     Aby rozróżnić wiele wersji środowiska uruchomieniowego lub aby odróżnić wiele aplikacji o tej samej nazwie, należy również zmodyfikować klucz rejestru. Aby uzyskać więcej informacji, zobacz [liczniki wydajności i wewnątrzprocesowe aplikacje](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md)równoległe.  
  
> [!NOTE]
> Gdy podczas działania konsoli wydajności są instalowane nowe liczniki wydajności, Zatrzymaj i ponownie uruchom konsolę wydajności, aby wyświetlić nowe liczniki.  
  
 Jeśli chcesz utworzyć profil zestawu, który istnieje w strefie lub w udziale zdalnym, upewnij się, że zestaw zdalny ma pełne zaufanie na komputerze, na którym są uruchomione liczniki wydajności. Jeśli zestaw nie ma wystarczających relacji zaufania, liczniki wydajności nie będą działały. Informacje o przyznawaniu zaufania do różnych stref można znaleźć w temacie [Caspol. exe (Narzędzie zasad zabezpieczeń dostępu kodu)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
> W systemach, w których zainstalowano .NET Framework 4, Monitor wydajności może nie wyświetlać danych dla liczników wydajności w niektórych kategoriach, takich jak **dane środowiska .NET CLR** i **sieci CLR platformy .NET**, dla aplikacji, które zostały opracowane przy użyciu platformy .NET. Framework 1,1. W takim przypadku można skonfigurować Monitor wydajności do wyświetlania tych danych przez dodanie [ \<elementu forcePerformanceCounterUniqueSharedMemoryReads >](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) do pliku konfiguracji aplikacji.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Programowe odczytywanie i tworzenie liczników wydajności  
 .NET Framework zawiera klasy, których można użyć, aby programowo uzyskać dostęp do tych samych informacji o wydajności, które są dostępne w konsoli wydajności. Można również użyć tych klas do tworzenia niestandardowych liczników wydajności. W poniższej tabeli opisano niektóre klasy monitorowania wydajności, które są dostępne w .NET Framework.  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Reprezentuje składnik licznika wydajności systemu Windows NT. Ta klasa umożliwia odczytywanie istniejących wstępnie zdefiniowanych lub niestandardowych liczników oraz publikowanie (zapisywanie) danych wydajności do liczników niestandardowych.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Program udostępnia kilka metod współpracy z licznikami i kategoriami liczników na komputerze.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|Określa Instalatora `PerformanceCounter` składnika.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Określa formułę, w której `NextValue` ma zostać obliczona Metoda. `PerformanceCounter`|  
  
## <a name="see-also"></a>Zobacz także

- [Liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md)
