---
title: Liczniki wydajności i wewnątrzprocesowe, równoczesne aplikacje
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
ms.openlocfilehash: a50b0f92837c3a962fa21d5c1342492d7fa397dd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121570"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Liczniki wydajności i wewnątrzprocesowe, równoczesne aplikacje
Korzystając z monitora wydajności (Perfmon. exe), można odróżnić liczniki wydajności na podstawie czasu wykonywania. W tym temacie opisano zmianę rejestru wymaganą do włączenia tej funkcji.  
  
## <a name="the-default-behavior"></a>Zachowanie domyślne  
 Domyślnie Monitor wydajności Wyświetla liczniki wydajności dla poszczególnych aplikacji. Jednak istnieją dwa scenariusze, w których jest to problematyczne:  
  
- W przypadku monitorowania dwóch aplikacji o tej samej nazwie. Na przykład, jeśli obie aplikacje mają nazwę MojaApl. exe, zostanie ona wyświetlona jako **MojaApl** , a druga jako **MojaApl # 1** w kolumnie **wystąpienie** . W takim przypadku trudno jest dopasować licznik wydajności do określonej aplikacji. Nie jest jasne, czy dane zbierane dla programu **MojaApl # 1** odnoszą się do pierwszego pliku Mojaapl. exe lub drugiego pliku Mojaapl. exe.  
  
- Gdy aplikacja używa wielu wystąpień środowiska uruchomieniowego języka wspólnego. .NET Framework 4 obsługuje międzyprocesowe scenariusze hostingu równoczesnego; oznacza to, że pojedynczy proces lub aplikacja może ładować wiele wystąpień środowiska uruchomieniowego języka wspólnego. Jeśli jedna aplikacja o nazwie MojaAplikacja. exe ładuje dwa wystąpienia środowiska uruchomieniowego, domyślnie zostanie wyznaczony w kolumnie **wystąpienie** jako **MojaApl** i **MojaApl # 1**. W takim przypadku nie jest jasne, czy **MojaApl** i **MojaApl # 1** odnoszą się do dwóch aplikacji o tej samej nazwie lub w tej samej aplikacji z dwoma środowiskami uruchomieniowymi. Jeśli wiele aplikacji o tej samej nazwie ładuje wiele środowisk uruchomieniowych, niejednoznaczność jest jeszcze większa.  
  
 Aby wyeliminować tę niejednoznaczność, można ustawić klucz rejestru. W przypadku aplikacji utworzonych przy użyciu .NET Framework 4, ta zmiana w rejestrze dodaje identyfikator procesu, a następnie identyfikator wystąpienia środowiska uruchomieniowego do nazwy aplikacji w kolumnie **wystąpienie** . Zamiast *aplikacji* lub *aplikacji*#1 aplikacja jest teraz identyfikowana jako *aplikacja*_`p`*Identyfikator procesu*\_`r`*runtimeID* w kolumnie **instance** . Jeśli aplikacja została opracowana przy użyciu poprzedniej wersji środowiska uruchomieniowego języka wspólnego, to wystąpienie jest reprezentowane jako *aplikacja\_* `p`*Identyfikator procesu* , pod warunkiem, że zainstalowano .NET Framework 4.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Liczniki wydajności dla przetwarzanych aplikacji równoległych  
 Aby obsługiwać liczniki wydajności dla wielu wersji środowiska uruchomieniowego języka wspólnego, które są hostowane w pojedynczej aplikacji, należy zmienić jedno ustawienie klucza rejestru, jak pokazano w poniższej tabeli.  
  
|||  
|-|-|  
|Nazwa klucza|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\. NETFramework\Performance|  
|Nazwa wartości|ProcessNameFormat|  
|Typ wartości|REG_DWORD|  
|Wartość|1 (0x00000001)|  
  
 Wartość 0 dla `ProcessNameFormat` wskazuje, że zachowanie domyślne jest włączone; oznacza to, że perfmon. exe Wyświetla liczniki wydajności dla poszczególnych aplikacji. Po ustawieniu tej wartości na 1, perfmon. exe rozróżnia wiele wersji aplikacji i oferuje liczniki wydajności na podstawie środowiska uruchomieniowego. Wszystkie inne wartości ustawień klucza rejestru `ProcessNameFormat` są nieobsługiwane i zarezerwowane do użytku w przyszłości.  
  
 Po zaktualizowaniu ustawienia klucza rejestru `ProcessNameFormat` należy ponownie uruchomić Perfmon. exe lub innych użytkowników liczników wydajności, aby nowa funkcja nazewnictwa wystąpień była poprawnie działać.  
  
 Poniższy przykład pokazuje, jak zmienić wartość `ProcessNameFormat` programowo.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Po wprowadzeniu tej zmiany rejestru perfmon. exe wyświetla nazwy aplikacji przeznaczonych dla .NET Framework 4 jako *aplikacja*_`p`*identyfikator procesu*\_`r`*runtimeID*, gdzie *aplikacja* jest nazwą Application, *ProcessId* jest identyfikatorem procesu aplikacji, a *runtimeID* jest identyfikatorem środowiska uruchomieniowego języka wspólnego. Na przykład jeśli aplikacja o nazwie MojaAplikacja. exe ładuje dwa wystąpienia środowiska uruchomieniowego języka wspólnego, perfmon. exe może zidentyfikować jedno wystąpienie jako myapp_p1416_r10, a drugie jako myapp_p3160_r10. Identyfikator środowiska uruchomieniowego rozróżnia tylko środowiska uruchomieniowe w ramach procesu; nie zawiera żadnych innych informacji o środowisku uruchomieniowym. (Na przykład identyfikator środowiska uruchomieniowego nie ma relacji do wersji lub jednostki SKU środowiska uruchomieniowego).  
  
 Jeśli zainstalowano .NET Framework 4, zmiana rejestru wpłynie również na aplikacje, które zostały opracowane przy użyciu wcześniejszych wersji .NET Framework. Są one wyświetlane w pliku perfmon. exe jako *application_* `p`*ProcessId*, gdzie *aplikacja* jest nazwą aplikacji *i identyfikatorem procesu.* Jeśli na przykład liczniki wydajności dwóch aplikacji o nazwie MojaAplikacja. exe są monitorowane, jeden z nich może być wyświetlany jako myapp_p23900, a drugi jako myapp_p24908.  
  
> [!NOTE]
> Identyfikator procesu eliminuje niejednoznaczność rozpoznawania dwóch aplikacji o tej samej nazwie, która korzysta ze starszych wersji środowiska uruchomieniowego. Identyfikator środowiska uruchomieniowego nie jest wymagany w przypadku poprzednich wersji, ponieważ poprzednie wersje środowiska uruchomieniowego języka wspólnego nie obsługują scenariuszy równoległych.  
  
 Jeśli .NET Framework 4 nie istnieje lub została odinstalowana, ustawienie klucza rejestru nie ma żadnego wpływu. Oznacza to, że dwie aplikacje o tej samej nazwie będą nadal wyświetlane w pliku perfmon. exe jako *aplikacja* i *aplikacja # 1* (na przykład jako **MojaApl** i **MojaApl # 1**).
