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
ms.openlocfilehash: 5145b013db1a86ef1b3128ab1c4495dddaaaf987
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/28/2019
ms.locfileid: "64624643"
---
# <a name="enabling-network-tracing"></a>Włączanie śledzenia sieci
Śledzenie sieci zapewnia dostęp do informacji o wywołaniach metod i ruchu sieciowym generowanym przez zarządzaną aplikację. Należy wykonać następujące zadania w celu włączenia funkcji śledzenia sieci w Twojej aplikacji:  
  
- Kompiluj swój kod z włączonym śledzeniem. Zobacz [jak: Kompilowanie warunkowe ze śledzeniem i debugowaniem](../../../docs/framework/debug-trace-profile/how-to-compile-conditionally-with-trace-and-debug.md) Aby uzyskać więcej informacji na temat przełączniki kompilatora, wymagane, aby włączyć śledzenie.  
  
- Określ miejsce docelowe danych wyjściowych śledzenia.  
  
- Skonfiguruj zachowanie funkcji śledzenia sieci. Zobacz [jak: Konfigurowanie śledzenia sieci](../../../docs/framework/network-programming/how-to-configure-network-tracing.md) Aby uzyskać szczegółowe informacje.  
  
 Najpopularniejsze miejsca docelowe śledzenia, nazywane również detektorów śledzenia są odbiornika domyślne, a plik dziennika.  
  
 Śledzenie używa odbiornika domyślne, jeśli nie określisz odbiornik śledzenia. Można wyświetlić komunikaty wysyłane do odbiornika domyślne przez wykonywanie kodu zarządzanego debugera kodu włączone, takich jak debuger CLR są dostarczane z zestawu SDK programu .NET Framework lub DBwin32.exe są dostarczane z zestawu Windows SDK. Korzystanie z debugera CLR, komunikaty śledzenia są wyświetlane w **dane wyjściowe** okna.  
  
 Jeśli chcesz otrzymywać danych śledzenia przy użyciu pliku można określić plik dziennika przy użyciu ustawień konfiguracji, jak pokazano w poniższym przykładzie. (Ogólne omówienie plików konfiguracyjnych, zobacz [pliki konfiguracyjne](../../../docs/framework/configure-apps/index.md).)  
  
 Aby wysłać dane śledzenia w pliku dziennika, należy dodać następujący węzeł do `<system.diagnostics>` węzeł odpowiedniego pliku konfiguracyjnego (aplikacji lub komputera). Można zmienić nazwę pliku (trace.log) do własnych potrzeb.  
  
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

- [Interpretowanie śledzenia sieci](../../../docs/framework/network-programming/interpreting-network-tracing.md)
- [Śledzenie sieci w programie .NET Framework](../../../docs/framework/network-programming/network-tracing.md)
- [Śledzenie i instrumentacja aplikacji](../../../docs/framework/debug-trace-profile/tracing-and-instrumenting-applications.md)
