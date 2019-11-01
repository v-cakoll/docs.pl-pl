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
ms.openlocfilehash: 43e9438ed2c1cd82bb4d89ff082545021b2d543e
ms.sourcegitcommit: 5a28f8eb071fcc09b045b0c4ae4b96898673192e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/31/2019
ms.locfileid: "73195343"
---
# <a name="debugging-tracing-and-profiling"></a>Debugowanie, śledzenie i profilowanie
Aby debugować aplikację .NET Framework, środowisko kompilatora i środowiska uruchomieniowego musi być skonfigurowane tak, aby umożliwić debugerowi dołączenie do aplikacji i tworzenie zarówno symboli, jak i map wierszy, jeśli jest to możliwe, dla aplikacji i jej odpowiadającego pośredniego firmy Microsoft język (MSIL). Po debugowaniu aplikacji zarządzanej można ją profilować w celu zwiększenia wydajności. Profilowanie szacuje i opisuje wiersze kodu źródłowego, które generują najczęściej wykonywany kod, oraz czas ich wykonania.  
  
 Aplikacje .NET Framework są łatwo debugowane przy użyciu programu Visual Studio, który obsługuje wiele szczegółów konfiguracji. Jeśli program Visual Studio nie jest zainstalowany, można przeanalizować i poprawić wydajność aplikacji .NET Framework przy użyciu klas debugowania w przestrzeni nazw .NET Framework <xref:System.Diagnostics>. Ta przestrzeń nazw zawiera klasy <xref:System.Diagnostics.Trace>, <xref:System.Diagnostics.Debug>i <xref:System.Diagnostics.TraceSource> dla przepływu wykonywania śledzenia, a także klasy <xref:System.Diagnostics.Process>, <xref:System.Diagnostics.EventLog>i <xref:System.Diagnostics.PerformanceCounter> na potrzeby profilowania kodu.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Włączanie debugowania dołączania JIT](enabling-jit-attach-debugging.md)  
 Pokazuje, jak skonfigurować rejestr do JIT — Dołącz aparat debugowania do aplikacji .NET Framework.  
  
 [Ułatwianie debugowania obrazu](making-an-image-easier-to-debug.md)  
 Pokazuje, jak włączyć i zoptymalizować śledzenie JIT, aby ułatwić debugowanie zestawu.  
  
 [Śledzenie i instrumentacja aplikacji](tracing-and-instrumenting-applications.md)  
 Opisuje, jak monitorować wykonywanie aplikacji w trakcie jej działania oraz jak można przyłączyć ją do wyświetlania, jak to działa, lub czy problem został usunięty.  
  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)  
 Opisuje zarządzane asystentów debugowania (MDA), które są ułatwieniami debugowania, które działają w połączeniu z środowiskiem uruchomieniowym języka wspólnego (CLR) w celu zapewnienia informacji o stanie środowiska uruchomieniowego.  
  
 [Udoskonalanie debugowania za pomocą atrybutów wyświetlania debugera](enhancing-debugging-with-the-debugger-display-attributes.md)  
 Opisuje, w jaki sposób deweloper typu może określić, jaki typ ma wyglądać, gdy zostanie wyświetlony w debugerze.  
  
 [Liczniki wydajności](performance-counters.md)  
 Opisuje liczniki, których można użyć do śledzenia wydajności aplikacji.  
  
## <a name="related-sections"></a>Sekcje pokrewne  
 [Debuguj ASP.NET lub ASP.NET Core aplikacje w programie Visual Studio](/visualstudio/debugger/how-to-enable-debugging-for-aspnet-applications)  
 Zawiera wymagania wstępne i instrukcje dotyczące debugowania aplikacji ASP.NET podczas tworzenia lub po wdrożeniu.  
  
 [Podręcznik programowania](../development-guide.md)  
 Przewodnik po wszystkich obszarach kluczowych technologii i zadaniach związanych z rozwojem aplikacji, takich jak tworzenie, konfigurowanie, debugowanie, zabezpieczanie i wdrażanie aplikacji, oraz informacje na temat programowania dynamicznego, interoperacyjności, rozszerzalności, zarządzania pamięcią i wątków.
