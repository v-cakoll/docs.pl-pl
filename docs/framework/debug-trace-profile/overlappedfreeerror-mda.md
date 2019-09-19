---
title: overlappedFreeError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- OverlappedFreeError MDA
- overlapped free method call error
- managed debugging assistants (MDAs), overlapped structures
- overlapped structures
- MDAs (managed debugging assistants), overlapped structures
- freeing overlapped structures
ms.assetid: b6ab2d48-6eee-4bab-97a3-046b3b0a5470
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 70d31bc187cabe49351e86a20023e2ec65e87b94
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052401"
---
# <a name="overlappedfreeerror-mda"></a>overlappedFreeError MDA
Asystent `overlappedFreeError` debugowania zarządzanego (MDA) jest uaktywniany, <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29?displayProperty=nameWithType> gdy metoda jest wywoływana przed ukończeniem operacji nakładania się.  
  
## <a name="symptoms"></a>Symptomy  
 Naruszenia dostępu lub uszkodzenie sterty zebranych przez elementy bezużyteczne.  
  
## <a name="cause"></a>Przyczyna  
 Nakładająca się struktura została zwolniona przed ukończeniem operacji. Funkcja, która używa nakładającego się wskaźnika, może później pisać do struktury, po jej zwolnieniu. Może to spowodować uszkodzenie sterty, ponieważ inny obiekt może teraz zajmować ten region.  
  
 To zdarzenie MDA może nie reprezentować błędu, jeśli nakładająca się operacja nie została pomyślnie uruchomiona.  
  
## <a name="resolution"></a>Rozwiązanie  
 Przed wywołaniem <xref:System.Threading.Overlapped.Free%28System.Threading.NativeOverlapped%2A%29> metody upewnij się, że operacja we/wy z nakładającą się strukturą została ukończona.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej przedstawiono przykładowe dane wyjściowe dla tego MDA.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlappedStructure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <overlappedFreeError/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
