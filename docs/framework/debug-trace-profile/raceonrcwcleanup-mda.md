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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b2fe4a5a2886fdbbd36ee491ea66dbce353fb034
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717249"
---
# <a name="raceonrcwcleanup-mda"></a>raceOnRCWCleanup MDA
`raceOnRCWCleanup` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) wykryje, że [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) jest używany, gdy wykonywane jest wywołanie, aby zwolnić go przy użyciu polecenia takiego jak <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A?displayProperty=nameWithType>metody.  
  
## <a name="symptoms"></a>Symptomy  
 Naruszenia zasad dostępu ani uszkodzeń pamięci podczas lub po uwolnieniu RCW przy użyciu <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> lub podobnej metody.  
  
## <a name="cause"></a>Przyczyna  
 RCW jest używana w innym wątku lub zwalnianie stosu wątku.  Nie można zwolnić RCW, który jest używany.  
  
## <a name="resolution"></a>Rozwiązanie  
 Nie zwolnienia RCW, która może być używany w bieżącym lub w innych wątków.  
  
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
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
