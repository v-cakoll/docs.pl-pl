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
ms.openlocfilehash: 5df9a3f506d8c2de6f1a3125459adc2d59d510bf
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217366"
---
# <a name="invalidiunknown-mda"></a>invalidIUnknown MDA
Asystent debugowania zarządzanego `invalidIUnknown` (MDA) jest uaktywniany po przekazaniu nieprawidłowego wskaźnika `IUnknown` do kodu zarządzanego z kodu natywnego. `IUnknown` nie może zwrócić sukcesu w przypadku zapytania o interfejs `IUnknown`.  
  
## <a name="symptoms"></a>Objawy  
 Wystąpił nieoczekiwany błąd podczas organizowania wskaźnika interfejsu COM podczas organizowania argumentów.  
  
## <a name="cause"></a>Przyczyna  
 Niepoprawna implementacja `QueryInterface` w interfejsie COM przeniesiona do środowiska CLR.  
  
## <a name="resolution"></a>Rozwiązanie  
 Popraw implementację `QueryInterface`.  
  
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

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
