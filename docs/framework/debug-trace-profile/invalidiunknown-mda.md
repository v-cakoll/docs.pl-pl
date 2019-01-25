---
title: invalidIUnknown MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5fead50c42c0d686492459829f7629654c20a0f3
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54582672"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
`invalidIUnknown` Zarządzanego Asystenta debugowania (MDA) jest uaktywniany podczas nieprawidłową `IUnknown` wskaźnik jest przekazywany do kodu zarządzanego z kodu natywnego. `IUnknown` Nie zwraca Powodzenie po otrzymaniu kwerendy dla `IUnknown` interfejsu.  
  
## <a name="symptoms"></a>Symptomy  
 Wystąpił nieoczekiwany błąd występuje, gdy marshaling wskaźnika interfejsu COM podczas przekazywania międzyprocesowego argumentu.  
  
## <a name="cause"></a>Przyczyna  
 Nieprawidłowe `QueryInterface` implementacji interfejsu COM jest przekazywany do środowiska CLR.  
  
## <a name="resolution"></a>Rozwiązanie  
 Popraw `QueryInterface` implementacji.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Opis błędu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidIUnknown />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
