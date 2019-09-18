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
ms.openlocfilehash: 62a24e45339b93af2c62db440f0611f16705116d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71048537"
---
# <a name="enabling-network-tracing"></a>Włączanie śledzenia sieci
Śledzenie sieci zapewnia dostęp do informacji o wywołaniach metod i ruchu sieciowym generowanym przez zarządzaną aplikację. Aby włączyć śledzenie sieci w aplikacji, należy wykonać następujące zadania:  
  
- Kompiluj swój kod z włączonym śledzeniem. Zobacz [How to: Kompiluj warunkowo, śledząc i Debuguj](../debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) , aby uzyskać więcej informacji na temat przełączników kompilatora wymaganych do włączenia śledzenia.  
  
- Określ miejsce docelowe śledzenia danych wyjściowych.  
  
- Skonfiguruj zachowanie funkcji Śledzenie sieci. Zobacz [How to: Skonfiguruj śledzenie](how-to-configure-network-tracing.md) sieci, aby uzyskać szczegółowe informacje.  
  
 Najpopularniejsze miejsca docelowe śledzenia, nazywane również odbiornikami śledzenia, to domyślny odbiornik i plik dziennika.  
  
 Śledzenie używa domyślnego odbiornika, jeśli nie zostanie określony odbiornik śledzenia. Możesz wyświetlić komunikaty wysyłane do domyślnego odbiornika, wykonując kod w debugerze obsługującym kod zarządzany, taki jak debuger CLR dostarczany z zestawem SDK .NET Framework, lub DBwin32. exe dostarczony z Windows SDK. Przy użyciu debugera CLR komunikaty śledzenia pojawiają się w oknie **danych wyjściowych** .  
  
 Jeśli wolisz używać pliku do odbierania śladów, możesz określić plik dziennika za pomocą ustawień konfiguracji, jak pokazano w poniższym przykładzie. (Ogólne omówienie plików konfiguracji można znaleźć w temacie [pliki konfiguracyjne](../configure-apps/index.md)).  
  
 Aby wysłać ślady do pliku dziennika, Dodaj następujący węzeł do `<system.diagnostics>` węzła odpowiedniego pliku konfiguracji (aplikacji lub komputera). Możesz zmienić nazwę pliku (Trace. log) zgodnie z potrzebami.  
  
```xml  
<system.diagnostics>  
  <trace autoflush="true" indentsize="4">  
    <listeners>  
      <add name="file" type="System.Diagnostics.TextWriterTraceListener" initializeData="trace.log"/>  
    </listeners>   
  </trace>  
</system.diagnostics>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Interpretowanie śledzenia sieci](interpreting-network-tracing.md)
- [Śledzenie sieci w programie .NET Framework](network-tracing.md)
- [Śledzenie i instrumentacja aplikacji](../debug-trace-profile/tracing-and-instrumenting-applications.md)
