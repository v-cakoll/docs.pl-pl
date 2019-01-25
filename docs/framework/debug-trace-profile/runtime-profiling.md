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
ms.openlocfilehash: 17530537e6d74b247aaf8708efed28ef169f9d57
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54491249"
---
# <a name="runtime-profiling"></a>Profilowanie środowiska uruchomieniowego
Profilowanie jest metoda zbierania danych wydajności w każdym scenariuszu rozwoju lub wdrożenia. Ta sekcja dotyczy dla deweloperów i administratorów, którzy chcą zebrać informacje dotyczące wydajności aplikacji.  
  
## <a name="tracking-performance-using-the-performance-monitor-perfmonexe"></a>Śledzenie wydajności przy użyciu Monitora wydajności (Perfmon.exe)  
 Monitor wydajności jest najprostszym narzędzie służące do profilu usługi [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] aplikacji. Monitor wydajności graficznie reprezentuje dane liczników wydajności .NET Framework, które są instalowane z środowiska uruchomieniowego języka wspólnego i [!INCLUDE[winsdklong](../../../includes/winsdklong-md.md)]. Te liczniki można monitorować wszystko — od zarządzania pamięcią just-in-time (JIT) kompilatora wydajności. Ich poinformować użytkownika o zasoby używane przez aplikację, czyli pośrednich miary wydajności Twojej aplikacji. Zrozumienie sposobu działania aplikacji wewnętrznie, korzystać z tych liczników.  
  
#### <a name="to-run-perfmonexe-on-windows-vista-and-later-versions"></a>Aby uruchomić Perfmon.exe w systemach Windows Vista i nowsze wersje  
  
1.  W wierszu polecenia wpisz **monitora wydajności**. **Monitora wydajności** pojawi się konsola.  
  
2.  W **narzędzia do monitorowania** folderu, kliknij przycisk **monitora wydajności**.  
  
3.  Na pasku narzędzi Monitora wydajności kliknij **Dodaj** ikonę (znak plus), jeśli jest obecna. Jeśli nie jest obecny, kliknij prawym przyciskiem myszy w oknie monitora i wybierz **Dodaj liczniki** opcji.  
  
     Spowoduje to otwarcie **Dodaj liczniki** okno dialogowe. **Dostępne liczniki** polu listy są wyświetlane obiekty dostępne wydajności. Istnieje kilka wstępnie zdefiniowanych obiektów dla aplikacji programu .NET Framework, w tym w zakresie zarządzania pamięcią (**pamięć .NET CLR**), interoperacyjności (**.NET CLR Interop**), obsługa wyjątków (**Wyjątki .NET CLR**), a wielowątkowości (**.NET CLR LocksAndThreads**). Każdy obiekt wydajności zawiera wiele liczników wydajności poszczególnych. Aby uzyskać listę dostępnych w Monitorze wydajności liczników wydajności, zobacz [liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md).  
  
4.  Zaznacz pole wyboru obok nazwy obiekt wydajności, aby wyświetlić listę liczników wydajności poszczególnych, które obsługuje.  
  
5.  Kliknij licznik wydajności, który chcesz wyświetlić.  
  
6.  W **wystąpienia wybranego obiektu** pola listy, kliknij przycisk  **\<wszystkie wystąpienia >** umożliwia określenie, że monitorowanie licznika wydajności dla środowiska uruchomieniowego języka wspólnego globalnie (to znaczy na Podstawa całego systemu).  
  
     —lub—  
  
     W **wystąpienia wybranego obiektu** pola listy, kliknij nazwę aplikacji w taki sposób, aby monitorować licznik wydajności dla tej aplikacji.  
  
     W celu rozróżnienia wielu wersji środowiska uruchomieniowego lub odróżnić wiele aplikacji o takiej samej nazwie, należy zmodyfikować klucz rejestru. Aby uzyskać więcej informacji, zobacz [liczniki wydajności i wewnątrzprocesowe Side-By-Side aplikacje](../../../docs/framework/debug-trace-profile/performance-counters-and-in-process-side-by-side-applications.md).  
  
> [!NOTE]
>  Nowe liczniki wydajności są instalowane, gdy uruchomiona jest Konsola wydajności, Zatrzymaj i ponownie uruchomić konsolę programu wydajności w taki sposób, aby uwidocznić nowe liczniki.  
  
 Jeśli chcesz przeprowadzić profilowanie zestawu, który istnieje w strefie lub w udziale zdalnym, upewnij się, że zdalnego zestawu ma pełnego zaufania, na komputerze z uruchomionym liczników wydajności. Jeśli zestaw nie ma wystarczających zaufania, liczniki wydajności nie będzie działać. Aby dowiedzieć się, jak udzielanie zaufania do różnych stref, zobacz [Caspol.exe (narzędzie zasad zabezpieczeń dostępu kodu)](../../../docs/framework/tools/caspol-exe-code-access-security-policy-tool.md).  
  
> [!NOTE]
>  W systemach, na którym [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] jest zainstalowany, Monitor wydajności mogą nie wyświetlać dane liczników wydajności w pewnych kategoriach, takich jak **.NET CLR Data** i **.NET CLR sieci**, dla aplikacje, które zostały opracowane przy użyciu [!INCLUDE[net_v11_short](../../../includes/net-v11-short-md.md)]. Jeśli jest to możliwe, można skonfigurować Monitor wydajności, aby wyświetlić te dane, dodając [ \<forceperformancecounteruniquesharedmemoryreads — >](../../../docs/framework/configure-apps/file-schema/runtime/forceperformancecounteruniquesharedmemoryreads-element.md) elementu do pliku konfiguracji aplikacji.  
  
## <a name="reading-and-creating-performance-counters-programmatically"></a>Odczytywanie i programowe tworzenie liczników wydajności  
 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] Udostępnia klasy, można użyć do programowego dostępu do tych samych informacji wydajności, który jest dostępny w konsoli Wydajność. Te klasy można również użyć do tworzenia niestandardowych liczników wydajności. W poniższej tabeli opisano niektóre z klas, które są dostarczane w monitorowania wydajności [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)].  
  
|Class|Opis|  
|-----------|-----------------|  
|<xref:System.Diagnostics.PerformanceCounter?displayProperty=nameWithType>|Reprezentuje składnik licznika wydajności systemu Windows NT. Klasa używana do odczytu istniejące liczniki wstępnie zdefiniowaną lub niestandardową i publikowania danych wydajności (Zapisz), aby liczników niestandardowych.|  
|<xref:System.Diagnostics.PerformanceCounterCategory?displayProperty=nameWithType>|Zapewnia kilka metod do interakcji z liczników i kategorie liczników na komputerze.|  
|<xref:System.Diagnostics.PerformanceCounterInstaller?displayProperty=nameWithType>|Określa Instalator dla `PerformanceCounter` składnika.|  
|<xref:System.Diagnostics.PerformanceCounterType?displayProperty=nameWithType>|Określa formułę, aby obliczyć `NextValue` metodę `PerformanceCounter`.|  
  
## <a name="see-also"></a>Zobacz także
- [Liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md)
