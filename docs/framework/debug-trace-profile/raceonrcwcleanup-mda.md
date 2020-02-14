---
title: raceOnRCWCleanup MDA
ms.date: 03/30/2017
helpviewer_keywords:
- RCW
- managed debugging assistants (MDAs), RCWs
- race on RCW cleanup
- MDAs (managed debugging assistants), RCWs
- RaceOnRCWCleanup MDA
- runtime callable wrappers
ms.assetid: bee1e9b1-50a8-4c89-9cd9-7dd6b2458187
ms.openlocfilehash: edf1fe3ee5be631f7f3c42f4a6cdb17f1be722cf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216193"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA
Asystent debugowania zarządzanego programu `raceOnRCWCleanup` (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) wykryje, że w [czasie wykonywania wywołania](../../standard/native-interop/runtime-callable-wrapper.md) do wydawania jest używane polecenie, takie jak <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType> metody.  
  
## <a name="symptoms"></a>Objawy  
 Naruszenia zasad dostępu lub uszkodzenia pamięci w trakcie lub po zwolnieniu otoki RCW przy użyciu <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> lub podobnej metody.  
  
## <a name="cause"></a>Przyczyna  
 Otoka RCW jest używana w innym wątku lub na stosie wolnego wątku.  Nie można zwolnić otoki RCW, która jest używana.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie zwalniaj otoki RCW, która może być używana w bieżącym lub w innych wątkach.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat z opisem błędu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <raceOnRCWCleanup/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
