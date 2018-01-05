---
title: invalidIUnknown MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid IUnknown pointer
- InvalidIUnknown MDA
- invalid IUnknown pointers
- IUnknown pointers
- managed debugging assistants (MDAs), invalid IUnknown pointer
ms.assetid: c7924771-a16b-40fe-b337-ce51dcdf6a12
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: ff88f8bc544c95a4fe5149cd517d9157d5ac23c7
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
`invalidIUnknown` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy nieprawidłową `IUnknown` wskaźnika są przekazywane do kodu zarządzanego z kodu macierzystego. `IUnknown` Zakończy się niepowodzeniem, zwraca sukces, gdy zapytanie dotyczące `IUnknown` interfejsu.  
  
## <a name="symptoms"></a>Symptomy  
 Wystąpił nieoczekiwany błąd występuje, gdy organizowanie wskaźnika interfejsu COM podczas przekazywania międzyprocesowego argumentu.  
  
## <a name="cause"></a>Przyczyna  
 Niepoprawna `QueryInterface` implementacji interfejsu COM przekazany do środowiska CLR.  
  
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
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
