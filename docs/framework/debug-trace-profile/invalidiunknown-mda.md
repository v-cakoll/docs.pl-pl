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
ms.openlocfilehash: db360a3b7c5f70596d5d5855b8e38dae5d484c42
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33390178"
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
