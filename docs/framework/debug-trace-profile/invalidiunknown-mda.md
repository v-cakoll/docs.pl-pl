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
ms.openlocfilehash: ea7f48ab61c16cb0430717074f1b1feab4827763
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052595"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
Asystent debugowania `IUnknown` zarządzanego (MDA) jest uaktywniany podczas przekazywania nieprawidłowego wskaźnika do kodu zarządzanego z kodu natywnego. `invalidIUnknown` Nie `IUnknown` można zwrócić sukcesu, gdy zapytanie `IUnknown` dotyczące interfejsu.  
  
## <a name="symptoms"></a>Symptomy  
 Wystąpił nieoczekiwany błąd podczas organizowania wskaźnika interfejsu COM podczas organizowania argumentów.  
  
## <a name="cause"></a>Przyczyna  
 Niepoprawna `QueryInterface` implementacja interfejsu com przeniesiona do środowiska CLR.  
  
## <a name="resolution"></a>Rozwiązanie  
 `QueryInterface` Popraw implementację.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
