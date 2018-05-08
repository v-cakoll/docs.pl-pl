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
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 56a24f93e92fbfbd2dbb1156a1c3ef786f59034e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="enabling-network-tracing"></a>Włączanie śledzenia sieci
Śledzenie sieci zapewnia dostęp do informacji na temat wywołań metod i ruch sieciowy generowany przez zarządzanej aplikacji. Należy wykonać następujące zadania, aby włączyć śledzenie sieci w aplikacji:  
  
-   Kompilowanie kodu z włączonym śledzeniem. Zobacz [porady: kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) uzyskać więcej informacji o przełączniki kompilatora, trzeba włączyć śledzenie.  
  
-   Określ lokalizację docelową dla danych wyjściowych śledzenia.  
  
-   Konfigurowanie zachowań Śledzenie sieci. Zobacz [porady: Konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) Aby uzyskać szczegółowe informacje.  
  
 Najbardziej typowe docelowe śledzenia, nazywana także obiekty nasłuchujące śledzenia, są odbiornika domyślne i pliku dziennika.  
  
 Śledzenie używa odbiornika domyślne, jeśli nie określisz nasłuchującego śledzenia. Można wyświetlić komunikaty wysyłane do odbiornika domyślne przez wykonywanie kodu w zarządzanego debugera kodu jest włączone, takich jak debuger CLR wysłane przy użyciu zestawu .NET Framework SDK lub DBwin32.exe wysłane przy użyciu zestawu SDK systemu Windows. Korzystanie z debugera CLR, komunikaty śledzenia są wyświetlane w **dane wyjściowe** okna.  
  
 Jeśli wolisz otrzymywać danych śledzenia przy użyciu pliku można określić plik dziennika przy użyciu ustawień konfiguracji, jak pokazano w poniższym przykładzie. (Ogólne omówienie pliki konfiguracji, zobacz [pliki konfiguracji](../../../docs/framework/configure-apps/index.md).)  
  
 Aby wysłać dane śledzenia w pliku dziennika, należy dodać następujący węzeł do `<system.diagnostics>` węzła pliku konfiguracyjnego odpowiedniego (aplikacji lub komputer). Można zmienić nazwę pliku (trace.log) w zależności od potrzeb.  
  
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
 [Interpretowanie śledzenia sieci](../../../docs/framework/network-programming/interpreting-network-tracing.md)  
 [Śledzenie sieci w programie .NET Framework](../../../docs/framework/network-programming/network-tracing.md)  
 [Wprowadzenie do Instrumentacji i śledzenie](http://msdn.microsoft.com/library/e924e57c-33cf-4b0e-9e7f-a45d13e38f2c)
