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
ms.openlocfilehash: 481360f731297e1c287c969e6524c68e0c9c0b7e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386473"
---
# <a name="debugging-tracing-and-profiling"></a>Debugowanie, śledzenie i profilowanie
Do debugowania aplikacji .NET Framework, kompilatora i środowiska uruchomieniowego musi być skonfigurowane do włączenia debugera dołączyć do aplikacji i zarówno symbole i linii mapy, jeśli to możliwe, aplikacji i jej odpowiednie Microsoft pośredni język (MSIL). Po zarządzanej aplikacji został debugowania, mogą być profilowane zwiększania wydajności. Profilowanie ocenia i opisuje wierszy kodu źródłowego z generowaniem kodu najczęściej wykonywane, i ile czasu potrzebnego na ich wykonanie.  
  
 Aplikacji programu .NET framework są łatwo debugować przy użyciu programu Visual Studio, która obsługuje wiele informacji konfiguracji. Jeśli nie zainstalowano programu Visual Studio, możesz sprawdzić i zwiększanie wydajności aplikacji .NET Framework za pomocą klasy debugowania w programie .NET Framework <xref:System.Diagnostics> przestrzeni nazw. Ta przestrzeń nazw zawiera <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>, i <xref:System.Diagnostics.TraceSource> klasy śledzenia przepływu wykonywania i <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>, i <xref:System.Diagnostics.PerformanceCounter> klasy dla profilowania kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Włączanie debugowania dołączania JIT](../../../docs/framework/debug-trace-profile/enabling-jit-attach-debugging.md)  
 Pokazuje, jak skonfigurować rejestr w celu dołączania JIT to aparat debugowania aplikacji .NET Framework.  
  
 [Ułatwianie debugowania obrazu](../../../docs/framework/debug-trace-profile/making-an-image-easier-to-debug.md)  
 Pokazuje, jak wyłączyć śledzenia JIT na i optymalizacji ułatwiające debugowania zestawu.  
  
 [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)  
 Opisuje sposób monitorowania wykonywanie aplikacji, gdy jest on uruchomiony i jak możliwość agregowania go, aby wyświetlić jak wykonuje czy też coś niepowodzenia.  
  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 W tym artykule opisano Asystenci zarządzanego debugowania (mda), które pomocy, które działają w połączeniu z środowisko uruchomieniowe języka wspólnego (CLR), aby podać informacje dotyczące stanu środowiska uruchomieniowego debugowania.  
  
 [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](../../../docs/framework/debug-trace-profile/enhancing-debugging-with-the-debugger-display-attributes.md)  
 W tym artykule opisano, jak developer typu można określić co typu będą wyglądać po wyświetleniu go w debugerze.  
  
 [Liczniki wydajności](../../../docs/framework/debug-trace-profile/performance-counters.md)  
 W tym artykule opisano liczniki, które można śledzić wydajność aplikacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Debugowanie aplikacji ASP.NET i AJAX](http://msdn.microsoft.com/library/9d531913-541b-47b8-864d-138021fca0c6)  
 Zawiera wymagania wstępne i instrukcje dotyczące debugowania aplikacji ASP.NET, podczas tworzenia lub po wdrożeniu.  
  
 [Podręcznik programowania](../../../docs/framework/development-guide.md)  
 Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.
