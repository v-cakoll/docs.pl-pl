---
title: gcUnmanagedToManaged MDA
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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 1679f87276262a08f5717ea81d263f4600542971
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052762"
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged MDA
Asystent `gcUnmanagedToManaged` debugowania zarządzanego (MDA) powoduje wyrzucanie elementów bezużytecznych za każdym razem, gdy wątek przechodzi z niezarządzanych do kodu zarządzanego.  
  
## <a name="symptoms"></a>Symptomy  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [gcManagedToUnmanaged](gcmanagedtounmanaged-mda.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
