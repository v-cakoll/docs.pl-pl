---
title: "Liczniki wydajności i wewnątrzprocesowe, równoczesne aplikacje"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- performance counters
- performance counters,and in-process side-by-side applications
- performance,.NET Framework applications
- performance monitoring,counters
ms.assetid: 6888f9be-c65b-4b03-a07b-df7ebdee2436
caps.latest.revision: "26"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: acbdf1ff1f2827bf607c2f838685d5161af61fd0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="performance-counters-and-in-process-side-by-side-applications"></a>Liczniki wydajności i wewnątrzprocesowe, równoczesne aplikacje
Korzystanie z Monitora wydajności (Perfmon.exe), jest możliwe do odróżnienia liczników wydajności na podstawie na środowiska wykonawczego. W tym temacie opisano zmiany rejestru wymagane do włączenia tej funkcji.  
  
## <a name="the-default-behavior"></a>Domyślne zachowanie  
 Domyślnie Monitor wydajności Wyświetla liczniki wydajności na podstawie określonych aplikacji. Istnieją dwa scenariusze, w których jest to powodować problemy:  
  
-   Podczas monitorowania dwóch aplikacji, które mają taką samą nazwę. Na przykład, jeśli obie aplikacje są nazywane myapp.exe, zostanie wyświetlony jeden jako **moja_aplikacja** i inne, **moja_aplikacja #1** w **wystąpienia** kolumny. W tym przypadku jest trudne do dopasowania licznik wydajności do określonej aplikacji. Nie jest jasne, czy dane są zbierane dla **moja_aplikacja #1** odwołuje się do myapp.exe pierwszy lub drugi myapp.exe.  
  
-   Jeśli aplikacja używa wielu wystąpień środowiska CLR. [!INCLUDE[net_v40_long](../../../includes/net-v40-long-md.md)] Obsługuje scenariusze hostingu side-by-side wewnątrzprocesowe; oznacza to, jednego procesu lub aplikacji można załadować wiele wystąpień środowiska CLR. Jeśli pojedynczej aplikacji o nazwie obciążeń myapp.exe dwa wystąpienia środowiska wykonawczego, domyślnie zostanie one określony w **wystąpienia** jako kolumny **moja_aplikacja** i **moja_aplikacja #1**. W takim przypadku nie jest jasne, czy **moja_aplikacja** i **moja_aplikacja #1** odnosić się do dwóch aplikacji o takiej samej nazwie lub do tej samej aplikacji z dwóch środowisk uruchomieniowych. Jeśli wiele aplikacji o takiej samej nazwie załadować wiele środowisk uruchomieniowych, niejednoznaczności jest jeszcze bardziej znaczące.  
  
 Można ustawić klucz rejestru, aby usunąć tę niejednoznaczność. W przypadku aplikacji utworzony przy użyciu [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)], tej zmiany rejestru dodaje identyfikator procesu, następuje identyfikator wystąpienia środowiska uruchomieniowego na nazwę aplikacji w **wystąpienia** kolumny. Zamiast *aplikacji* lub *aplikacji*#1 aplikacja jest teraz identyfikowane jako *aplikacji*_`p`*processID* \_ `r` *runtimeID* w **wystąpienia** kolumny. Jeśli aplikacja została opracowana za pomocą poprzedniej wersji środowiska CLR, to wystąpienie jest reprezentowany jako *aplikacji\_*`p`*processID* pod warunkiem, że [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] jest zainstalowany.  
  
## <a name="performance-counters-for-in-process-side-by-side-applications"></a>Liczniki wydajności dla aplikacji Side-by-Side w procesie  
 Do obsługi liczniki wydajności dla wielu wspólnego języka środowiska uruchomieniowego wersji, które znajdują się w jednej aplikacji, należy zmienić klucz rejestru pojedynczego ustawienie, jak pokazano w poniższej tabeli.  
  
|||  
|-|-|  
|Nazwa klucza|HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\\. NETFramework\Performance|  
|Nazwa wartości|ProcessNameFormat|  
|Typ wartości|REG_DWORD|  
|Wartość|1 (0x00000001)|  
  
 Wartość 0 dla `ProcessNameFormat` wskazuje, że jest włączona domyślnie; będący Perfmon.exe wyświetla liczniki wydajności na podstawie określonych aplikacji. Gdy ta wartość jest ustawiona na 1, Perfmon.exe pozwala odróżnić od siebie wiele wersji aplikacji i zawiera liczników wydajności na podstawie na środowiska wykonawczego. Wszystkie inne wartości `ProcessNameFormat` ustawienie klucza rejestru jest nieobsługiwane i zarezerwowane do użytku w przyszłości.  
  
 Po zaktualizowaniu `ProcessNameFormat` klucza rejestru ustawienie, musisz ponownie uruchomić Perfmon.exe lub innym klientom liczników wydajności, aby nowa funkcja nazewnictwa wystąpienia działa prawidłowo.  
  
 Poniższy przykład przedstawia sposób zmiany `ProcessNameFormat` wartość programowo.  
  
 [!code-csharp[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/csharp/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/cs/regsetting1.cs#1)]
 [!code-vb[Conceptual.PerfCounters.InProSxS#1](../../../samples/snippets/visualbasic/VS_Snippets_CLR/conceptual.perfcounters.inprosxs/vb/regsetting1.vb#1)]  
  
 Po wprowadzeniu tej zmiany w rejestrze Perfmon.exe wyświetla nazwy aplikacji przeznaczonych [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] jako *aplikacji*_`p`*processID* \_ `r` *runtimeID*, gdzie *aplikacji* jest nazwa aplikacji, *processID* jest identyfikatora procesu aplikacji, a  *runtimeID* jest identyfikatorem środowiska uruchomieniowego języka wspólnego. Na przykład jeśli aplikacja o nazwie obciążeń myapp.exe dwa wystąpienia środowisko uruchomieniowe języka wspólnego, Perfmon.exe może zidentyfikować jedno wystąpienie jako myapp_p1416_r10, a drugi jako myapp_p3160_r10. Identyfikator środowiska uruchomieniowego tylko pozwala odróżnić od siebie środowisk uruchomieniowych w ramach procesu; nie ma innych informacji dotyczących środowiska uruchomieniowego. (Na przykład identyfikator działania ma relacja wersji lub wersji środowiska uruchomieniowego).  
  
 Jeśli [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] jest zainstalowany, zmiany w rejestrze również wpływa na aplikacje, które zostały opracowane za pomocą wcześniejszych wersji programu .NET Framework. Są one wyświetlane w Perfmon.exe jako *application_*`p`*processID*, gdzie *aplikacji* to nazwa aplikacji i *processID* jest identyfikatorem procesu. Na przykład jeśli liczniki wydajności z dwóch aplikacji o nazwie myapp.exe są monitorowane, co może być wyświetlany jako myapp_p23900, a drugi jako myapp_p24908.  
  
> [!NOTE]
>  Identyfikator procesu eliminuje niejednoznaczności rozpoznawania dwóch aplikacji o takiej samej nazwie, korzystających z wcześniejszych wersji środowiska uruchomieniowego. Identyfikator środowiska uruchomieniowego nie jest wymagana w poprzednich wersjach, ponieważ poprzednie wersje środowiska CLR nie obsługują side-by-side scenariuszy.  
  
 Jeśli [!INCLUDE[net_v40_short](../../../includes/net-v40-short-md.md)] nie istnieje lub została odinstalowana, ustawienie klucza rejestru nie ma wpływu. Oznacza to, że dwie aplikacje o tej samej nazwie będą nadal wyświetlane w Perfmon.exe jako *aplikacji* i *aplikacji #1* (na przykład jako **moja_aplikacja** i **moja_aplikacja #1**).
