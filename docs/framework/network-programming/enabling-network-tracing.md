---
title: Włączanie śledzenia sieci
ms.date: 03/30/2017
helpviewer_keywords:
- trace destinations
- sending traces to log file
- trace listeners, network tracing
- network tracing, enabling
- CLR Debugger
- default listeners
- logs, trace
- destination for tracing output
ms.assetid: 5fff458c-51a6-4134-ba47-8a6137ddc41e
ms.openlocfilehash: 61ffd422463ca70cc34c39dd216ce8e660809dcb
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/15/2020
ms.locfileid: "79180880"
---
# <a name="enabling-network-tracing"></a>Włączanie śledzenia sieci
Śledzenie sieci zapewnia dostęp do informacji o wywołaniach metod i ruchu sieciowym generowanych przez aplikację zarządzaną. Aby włączyć śledzenie sieci w aplikacji, należy wykonać następujące zadania:  
  
- Skompiluj kod z włączoną funkcją śledzenia. Zobacz [Jak: Kompilowanie warunkowo z śledzenia i debugowania, aby](../debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) uzyskać więcej informacji na temat przełączników kompilatora wymagane do włączenia śledzenia.  
  
- Określ miejsce docelowe dla śledzenia danych wyjściowych.  
  
- Skonfiguruj zachowanie śledzenia sieci. Zobacz [Jak: Konfigurowanie śledzenia sieci, aby](how-to-configure-network-tracing.md) uzyskać szczegółowe informacje.  
  
 Najczęstsze miejsca docelowe śledzenia, określane również jako detektory śledzenia, są domyślnym odbiornikiem i plikiem dziennika.  
  
 Śledzenie używa odbiornika domyślnego, jeśli nie określisz odbiornika śledzenia. Wiadomości wysyłane do odbiornika domyślnego można wyświetlać, wykonując kod w debugerze z włączoną kodem zarządzanym, takim jak debuger ŚRODOWISKA CLR dostarczany z modułem SDK programu .NET Framework lub program DBwin32.exe dostarczany z modułem Windows SDK. Za pomocą debugera CLR komunikaty śledzenia są wyświetlane w oknie **Dane wyjściowe.**  
  
 Jeśli wolisz używać pliku do odbierania śladów, możesz określić plik dziennika przy użyciu ustawień konfiguracji, jak pokazano w poniższym przykładzie. (Aby zapoznać się z ogólną omówień plików konfiguracyjnych, zobacz [Pliki konfiguracyjne](../configure-apps/index.md).)  
  
 Aby wysłać ślady do pliku dziennika, `<system.diagnostics>` dodaj następujący węzeł do węzła odpowiedniego pliku konfiguracyjnego (aplikacji lub komputera). Nazwę pliku (trace.log) można zmienić zgodnie z potrzebami.  
  
```xml  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>
  </trace>  
</system.diagnostics>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Interpretowanie śledzenia sieci](interpreting-network-tracing.md)
- [Śledzenie sieci w .NET Framework](network-tracing.md)
- [Śledzenie i instrumentacja aplikacji](../debug-trace-profile/tracing-and-instrumenting-applications.md)
