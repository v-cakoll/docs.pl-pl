---
title: invalidFunctionPointerInDelegate MDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cbb33d2cddab22ad2072354ba543d2cd6a60a668
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59218280"
---
# <a name="invalidfunctionpointerindelegate-mda"></a>invalidFunctionPointerInDelegate MDA
`invalidFunctionPointerInDelegate` Zarządzanego Asystenta debugowania (MDA) jest uaktywniany podczas nieprawidłowy wskaźnik funkcji jest przekazywany do utworzenia delegata przez wskaźnik natywnej funkcji.  
  
## <a name="symptoms"></a>Symptomy  
 Naruszenia zasad dostępu ani uszkodzeń pamięci nieoczekiwany, używając delegata za pośrednictwem wskaźnika funkcji.  
  
## <a name="cause"></a>Przyczyna  
 Określono nieprawidłowy wskaźnik funkcji.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłową funkcją wskaźnik  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Nieprawidłowy wskaźnik funkcji.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidFunctionPointerInDelegate />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
