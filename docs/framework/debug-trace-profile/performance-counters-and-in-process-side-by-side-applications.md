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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: dd3501bc74da2c9a812f9c4816b5a081b3780cd0
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490030"
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Liczniki wydajności i wewnątrzprocesowe, równoczesne aplikacje
Korzystanie z Monitora wydajności (Perfmon.exe), istnieje możliwość rozróżnienia liczników wydajności na podstawie poszczególnych środowiska uruchomieniowego. W tym temacie opisano zmiany rejestru wymagane do włączenia tej funkcji.  
  
## <a name="the-default-behavior"></a>Zachowanie domyślne  
 Domyślnie Monitor wydajności Wyświetla liczniki wydajności na podstawie poszczególnych aplikacji. Istnieją dwa scenariusze, w których stanowi to:  
  
- Gdy monitorujesz dwie aplikacje, które mają taką samą nazwę. Na przykład, jeśli obie aplikacje są nazywane myapp.exe, zostanie wyświetlony jeden jako **myapp** i innych **myapp nr 1** w **wystąpienia** kolumny. W tym przypadku jest trudne dopasować, licznik wydajności do określonej aplikacji. Nie jest jasne, czy dane są zbierane dla **myapp nr 1** odwołuje się do myapp.exe pierwszej lub drugiej myapp.exe.  
  
- Jeśli aplikacja korzysta z wielu wystąpień środowiska uruchomieniowego języka wspólnego. .NET Framework 4 obsługuje scenariusze hostingu side-by-side w trakcie; oznacza to pojedynczego procesu lub aplikacji można załadować wiele wystąpień środowiska uruchomieniowego języka wspólnego. Jeśli pojedynczej aplikacji o nazwie obciążeń myapp.exe dwóch wystąpień środowiska uruchomieniowego, domyślnie, zostaną one oznaczone w **wystąpienia** jako kolumny **myapp** i **myapp nr 1**. W tym przypadku nie jest jasne czy **myapp** i **myapp nr 1** odnosić się do dwóch aplikacji o takiej samej nazwie lub tej samej aplikacji za pomocą dwóch środowisk uruchomieniowych. Jeśli wiele aplikacji o takiej samej nazwie można załadować wielu modułów wykonawczych niejednoznaczności jest jeszcze bardziej.  
  
 Można ustawić klucz rejestru, aby wyeliminować tę niejednoznaczność. Dla aplikacji utworzonych za pomocą programu .NET Framework 4, zmiany w rejestrze dodaje identyfikator procesu, następuje identyfikator wystąpienia środowiska uruchomieniowego do nazwy aplikacji w **wystąpienia** kolumny. Zamiast *aplikacji* lub *aplikacji*#1 aplikację teraz jest identyfikowany jako *aplikacji*_`p`*processID* \_ `r` *runtimeID* w **wystąpienia** kolumny. Jeśli aplikacja została opracowana przy użyciu poprzedniej wersji środowiska uruchomieniowego języka wspólnego, tego wystąpienia jest reprezentowany jako *aplikacji\_* `p`*processID* pod warunkiem, że. .NET Framework 4 jest zainstalowana.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Liczniki wydajności dla-Process Side-by-Side aplikacji  
 Aby obsłużyć liczniki wydajności dla wielu typowych języka wersje środowiska uruchomieniowego, które znajdują się w jednej aplikacji, możesz zmienić klucz rejestru jednego ustawienia, jak pokazano w poniższej tabeli.  
  
|||  
|-|-|  
|Nazwa klucza|HKEY_LOCAL_MACHINE\System\CurrentControlSet\Services\\.NETFramework\Performance|  
|Nazwa wartości|ProcessNameFormat|  
|Typ wartości|REG_DWORD|  
|Wartość|1 (0x00000001)|  
  
 Wartość 0 dla `ProcessNameFormat` wskazuje, że zachowanie domyślne jest włączone; będącego, Perfmon.exe wyświetla liczniki wydajności na podstawie poszczególnych aplikacji. Gdy ta wartość jest ustawiona na 1, Perfmon.exe pozwala odróżnić od siebie wiele wersji aplikacji i oferuje liczniki wydajności na podstawie poszczególnych środowiska uruchomieniowego. Dowolna inna wartość, aby uzyskać `ProcessNameFormat` ustawienie klucza rejestru nie jest wspierana i zarezerwowane dla przyszłego użytku.  
  
 Po zaktualizowaniu `ProcessNameFormat` klucza rejestru ustawienia, należy ponownie uruchomić Perfmon.exe lub innych klientów, liczników wydajności, aby nowa funkcja nazewnictwa wystąpienia działa prawidłowo.  
  
 Poniższy przykład pokazuje, jak zmienić `ProcessNameFormat` wartość programowo.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Po wprowadzeniu tej zmiany w rejestrze, Perfmon.exe wyświetla nazwy aplikacji przeznaczonych dla środowiska .NET Framework 4, jako *aplikacji*_`p`*processID* \_ `r` *runtimeID*, gdzie *aplikacji* to nazwa aplikacji, *processID* jest identyfikator procesu aplikacji, a  *runtimeID* jest identyfikatorem środowiska uruchomieniowego języka wspólnego. Na przykład jeśli aplikacja o nazwie obciążeń myapp.exe dwa wystąpienia środowiska uruchomieniowego języka wspólnego, Perfmon.exe może zidentyfikować jednego wystąpienia jako myapp_p1416_r10, a drugi jako myapp_p3160_r10. Identyfikator środowiska uruchomieniowego tylko pozwala odróżnić od siebie środowiska uruchomieniowe w ramach procesu; nie obejmuje wszystkie inne informacje dotyczące środowiska uruchomieniowego. (Na przykład identyfikator środowiska uruchomieniowego ma nie relacji do wersji lub wersji środowiska uruchomieniowego).  
  
 Jeśli zainstalowano program .NET Framework 4, zmiany w rejestrze wpływa również na aplikacje, które zostały opracowane we wcześniejszych wersjach programu .NET Framework. Będą one widoczne w Perfmon.exe jako *application_* `p`*processID*, gdzie *aplikacji* to nazwa aplikacji i *processID* to identyfikator procesu. Na przykład jeśli dwie aplikacje o nazwie myapp.exe liczniki wydajności są monitorowane, jeden może być widoczne jako myapp_p23900, a drugi jako myapp_p24908.  
  
> [!NOTE]
>  Identyfikator procesu, który eliminuje niejednoznaczności rozpoznawania dwie aplikacje o takiej samej nazwie, które używają starszych wersji środowiska uruchomieniowego. Identyfikator środowiska uruchomieniowego nie jest wymagany dla poprzednich wersji, ponieważ poprzednie wersje środowiska uruchomieniowego języka wspólnego nie obsługują scenariusze side-by-side.  
  
 Jeśli program .NET Framework 4 nie istnieje lub została odinstalowana, ustawienie klucza rejestru nie ma znaczenia. Oznacza to, że dwie aplikacje o takiej samej nazwie będą w dalszym ciągu są wyświetlane w Perfmon.exe jako *aplikacji* i *aplikacji nr 1* (na przykład, jako **myapp** i **myapp nr 1**).
