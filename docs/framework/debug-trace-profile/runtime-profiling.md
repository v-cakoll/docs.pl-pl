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
ms.openlocfilehash: fec1fb5a2dc3d6589f49d4a5864dabfb03a5477c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33393058"
---
# <a name="runtime-profiling"></a>Profilowanie środowiska uruchomieniowego
Profilowanie jest metoda zbierania danych wydajności w jakimkolwiek scenariuszu rozwoju lub wdrożenia. Ta sekcja dotyczy deweloperów i administratorów, którzy chcą zebrać informacje dotyczące wydajności aplikacji.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Śledzenie wydajności w Monitorze wydajności (Perfmon.exe)  
 Monitor wydajności jest najprostszym narzędzie służące do profilu użytkownika [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikacji. Monitor wydajności graficznie reprezentuje dane liczników wydajności .NET Framework, które są instalowane z środowisko uruchomieniowe języka wspólnego i [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Te liczniki może służyć do monitorowania wszystkich elementów zarządzania pamięcią just in time (JIT) kompilatora wydajność. One informujące o zasobach używany przez aplikację, czyli pośrednich miar wydajności aplikacji. Zrozumieć sposób działania aplikacji wewnętrznie przy użyciu tych liczników.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Aby uruchomić Perfmon.exe w systemie Windows Vista i nowszych wersjach  
  
1.  W wierszu polecenia wpisz **perfmon**. **Monitora wydajności** zostanie wyświetlony w konsoli.  
  
2.  W **narzędzia do monitorowania** folderu, kliknij przycisk **monitora wydajności**.  
  
3.  Na pasku narzędzi Monitora wydajności, kliknij przycisk **Dodaj** ikona (znak plus), jeśli jest obecna. Jeśli nie jest obecny, kliknij prawym przyciskiem myszy w oknie monitora i wybierz **Dodaj liczniki** opcji.  
  
     Spowoduje to otwarcie **Dodaj liczniki** okno dialogowe. **Dostępne liczniki** pole listy wyświetla obiekty dostępne wydajności. Istnieje wiele wstępnie zdefiniowanych obiektów dla aplikacji .NET Framework, w tym w zakresie zarządzania pamięcią (**pamięci platformy .NET CLR**), współdziałanie (**.NET CLR Interop**), obsługa wyjątków (**.NET CLR wyjątki**), a wielowątkowości (**.NET CLR LocksAndThreads**). Każdy obiekt wydajności zawiera wiele liczników wydajności indywidualnych. Aby uzyskać listę dostępnych w Monitorze wydajności liczników wydajności, zobacz [liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
4.  Zaznacz pole wyboru obok nazwy obiektu wydajności, aby wyświetlić listę liczników wydajności poszczególnych, które obsługuje.  
  
5.  Kliknij przycisk licznika wydajności, które chcesz wyświetlić.  
  
6.  W **wystąpienia wybranego obiektu** pola listy, kliknij przycisk  **\<wszystkie wystąpienia >** Aby określić globalnie monitorowanie licznika wydajności dla środowisko uruchomieniowe języka wspólnego (to znaczy na zasady systemowe).  
  
     —lub—  
  
     W **wystąpienia wybranego obiektu** pola listy, kliknij nazwę aplikacji do monitorowania licznika wydajności dla tej aplikacji.  
  
     Możesz rozróżnić wiele wersji środowiska uruchomieniowego lub do odróżniania wiele aplikacji o takiej samej nazwie, należy zmodyfikować klucz rejestru. Aby uzyskać więcej informacji, zobacz [liczniki wydajności i wewnątrzprocesowe Side-By-Side aplikacji](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
>  Po zainstalowaniu nowe liczniki wydajności konsoli wydajności jest uruchomiona, Zatrzymaj i ponownie uruchomić konsolę wydajności, aby wyświetlić nowe liczniki.  
  
 Jeśli chcesz profilu zestawu, który istnieje w strefie lub w udziale zdalnym, upewnij się, że zestaw zdalnego ma pełne zaufanie na komputerze, na którym działają liczników wydajności. Jeśli zestaw nie ma wystarczających zaufania, liczniki wydajności nie będą działać. Aby uzyskać informacje o udzielanie zaufania do różnych stref, zobacz [Caspol.exe (narzędzie zasad zabezpieczenia dostępu kodu)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
>  W systemach, w którym [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] jest zainstalowany, Monitor wydajności mogą nie wyświetlać się danych liczników wydajności w niektórych kategorii, takich jak **.NET CLR danych** i **.NET CLR sieci**, dla aplikacje, które zostały opracowane za pomocą [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]. Jeśli jest to możliwe, można skonfigurować Monitor wydajności, aby wyświetlić te dane, dodając [ \<forceperformancecounteruniquesharedmemoryreads — >](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) elementu do pliku konfiguracji aplikacji.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Odczytywanie i programowe tworzenie liczniki wydajności  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Udostępnia klasy służy do uzyskania programowego dostępu do tych samych informacji wydajności, które są dostępne w konsoli wydajności. Aby utworzyć niestandardowe liczniki wydajności umożliwia także tych klas. W poniższej tabeli opisano niektóre działania monitorowania klasy, które zostały opublikowane w [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Oznacza składnik licznika wydajności systemu Windows NT. Klasa używana do odczytu istniejących, wstępnie zdefiniowanych lub niestandardowych liczników i publikowania danych wydajności (Zapisz), w licznikach niestandardowych.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Zapewnia kilka metod do interakcji z liczników i kategorii liczników na komputerze.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|Określa Instalatora dla `PerformanceCounter` składnika.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Określa formułę do obliczania `NextValue` metodę `PerformanceCounter`.|  
  
## <a name="see-also"></a>Zobacz też  
 [Liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md)
