---
title: Debugowanie, śledzenie i profilowanie
ms.date: 03/30/2017
helpviewer_keywords:
- debugging [.NET Framework]
- .NET Framework application configuration, debugging
- debugging [.NET Framework], .NET Framework application debugging
- troubleshooting applications [.NET Framework], profiling
- application development [.NET Framework], debugging
- .NET Framework application configuration, profiling
- profiling applications
- troubleshooting applications [.NET Framework], debugging
- troubleshooting applications [.NET Framework]
- application development [.NET Framework], profiling
ms.assetid: 4a04863e-2475-46f4-bc3f-3c11510c2a4b
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 855a1329c9804e4b40d796c639bbe8768156dcc2
ms.sourcegitcommit: d2ccb199ae6bc5787b4762e9ea6d3f6fe88677af
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/12/2019
ms.locfileid: "56092504"
---
# <a name="debugging-tracing-and-profiling"></a>Debugowanie, śledzenie i profilowanie
Do debugowania aplikacji .NET Framework, kompilatora i środowiska uruchomieniowego musi być skonfigurowana do włączenia debuger, który chcesz dołączyć do aplikacji i aby wygenerować symbole i linii mapy, jeśli to możliwe, dla aplikacji i jej odpowiednie Microsoft intermediate Language (MSIL). Po zarządzanych aplikacji został debugowany, mogą być profilowane do poprawienia wydajności. Profilowanie oblicza i opisuje linie kodu źródłowego, które generują kod najczęściej wykonywaną i ile czas potrzebny do ich wykonania.  
  
 Aplikacje programu .NET framework są łatwo debugować za pomocą programu Visual Studio, która obsługuje wiele szczegółów konfiguracji. Jeśli nie zainstalowano programu Visual Studio, możesz sprawdzić i zwiększyć wydajność aplikacji .NET Framework przy użyciu klas debugowania w programie .NET Framework <xref:System.Diagnostics> przestrzeni nazw. Ta przestrzeń nazw zawiera <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, i <xref:System.Diagnostics.TraceSource> klasy w celu śledzenia wykonywania przepływu, a <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, i <xref:System.Diagnostics.PerformanceCounter> klas na potrzeby profilowania kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Włączanie debugowania dołączania JIT](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 Pokazuje, jak skonfigurować rejestr w celu dołączania JIT aparatu debugowania aplikacji .NET Framework.  
  
 [Ułatwianie debugowania obrazu](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 Pokazuje, jak wyłączyć śledzenia JIT na i optymalizacji ułatwiają zestaw do debugowania.  
  
 [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 W tym artykule opisano, jak monitorować wykonywanie aplikacji, gdy jest uruchomiona i w jaki sposób do Instrumentacji go, aby wyświetlić jak dobrze działa, czy Niestety, wystąpił problem.  
  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 W tym artykule opisano asystentów zarządzanego debugowania (mda), które są Debugowanie — pomoce, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR) zawiera informacje na temat stanu środowiska uruchomieniowego.  
  
 [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 W tym artykule opisano, jak Deweloper typ można określić, co typ będzie wyglądać po wyświetleniu go w debugerze.  
  
 [Liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 W tym artykule opisano liczniki, które służą do śledzenia wydajności aplikacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Debugowanie aplikacji ASP.NET lub ASP.NET Core w programie Visual Studio](/visualstudio/debugger/debugging-aspnet-and-ajax-applications)  
 Zawiera wymagania wstępne i instrukcje dotyczące sposobu debugowania aplikacji ASP.NET, podczas tworzenia lub po wdrożeniu.  
  
 [Podręcznik programowania](../../../docs/framework/development-guide.md)  
 Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.
