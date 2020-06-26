---
title: gcUnmanagedToManaged MDA
description: Zapoznaj się z asystentem debugowania zarządzanego przez gcManagedToUnmanaged w programie .NET. To zdarzenie MDA może zostać aktywowane ze względu na uszkodzenie sterty pamięci podczas przejścia do kodu zarządzanego.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GC unmanaged to managed
- transitioning threads unmanaged to managed code
- GcUnmanagedToManaged MDA
- threading [.NET Framework], garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
- unmanaged to managed garbage collection
ms.assetid: 103eb3a3-1cf0-4406-8a9a-a7798fdc22d1
ms.openlocfilehash: 320d55224e6a204d330447d6c68eabe0fa6cf892
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415904"
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged MDA
`gcUnmanagedToManaged`Asystent debugowania zarządzanego (MDA) powoduje wyrzucanie elementów bezużytecznych za każdym razem, gdy wątek przechodzi z niezarządzanych do kodu zarządzanego.  
  
## <a name="symptoms"></a>Objawy  
 Aplikacja, która uruchamia niezarządzane składniki użytkownika przy użyciu modelu COM i wywołania platformy, powoduje niedeterministyczne naruszenie dostępu w środowisku CLR.  
  
## <a name="cause"></a>Przyczyna  
 Jeśli aplikacja działa w niezarządzanych składnikach użytkownika, wówczas te składniki mogły spowodować uszkodzenie sterty zebranej przez elementy bezużyteczne. Powoduje to naruszenie zasad dostępu w środowisku CLR, gdy moduł zbierający elementy bezużyteczne podejmie próbę wykonania grafu obiektów.  
  
## <a name="resolution"></a>Rozwiązanie  
 Włączenie tego asystenta skraca czas od momentu, gdy składnik niezarządzany uszkadza stertę zebraną przez elementy bezużyteczne i gdy występuje naruszenie zasad dostępu, wymuszając wyrzucanie elementów bezużytecznych przed każdym zarządzanym przejściem.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Powoduje wyrzucanie elementów bezużytecznych przy każdym przejścia wątku z niezarządzanego do kodu zarządzanego.  
  
## <a name="output"></a>Dane wyjściowe  
 To zdarzenie MDA nie generuje danych wyjściowych.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
