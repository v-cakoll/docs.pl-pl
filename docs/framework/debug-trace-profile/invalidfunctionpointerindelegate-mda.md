---
title: invalidFunctionPointerInDelegate MDA
description: Przejrzyj invalidFunctionPointerInDelegate Managed Debug Assistant (MDA), który jest wywoływany w przypadku przekazania nieprawidłowego wskaźnika funkcji do obiektu delegowanego.
ms.date: 03/30/2017
helpviewer_keywords:
- invalidFunctionPointerInDelegate MDA
- managed debugging assistants (MDAs), invalid function pointer to delegates
- MDAs (managed debugging assistants), invalid function pointer to delegates
- function pointers, invalid
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- invalid function pointers
ms.assetid: 99ae44f1-783e-49a9-9009-24f54bbd0f09
ms.openlocfilehash: a17427d117c62ba782af3c9549c84623a3013b06
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051743"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate MDA
`invalidFunctionPointerInDelegate`Asystent debugowania zarządzanego (MDA) jest uaktywniany po przekazaniu nieprawidłowego wskaźnika funkcji do konstruowania delegata przez wskaźnik funkcji natywnej.  
  
## <a name="symptoms"></a>Objawy  
 Naruszenia zasad dostępu lub nieoczekiwane uszkodzenie pamięci podczas używania delegata na wskaźniku funkcji.  
  
## <a name="cause"></a>Przyczyna  
 Określono nieprawidłowy wskaźnik funkcji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłowy wskaźnik funkcji  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Nieprawidłowy wskaźnik funkcji.  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
