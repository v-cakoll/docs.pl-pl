---
title: gcManagedToUnmanaged MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), garbage collection
- GcManagedToUnmanaged MDA
- GC managed to unmanaged
- transitioning threads managed to unmanaged code
- threading [.NET Framework], garbage collection
- managed to unmanaged garbage collection
- managed debugging assistants (MDAs), garbage collection
- threading [.NET Framework], managed debugging assistants
- garbage collection, run-time errors
ms.assetid: 7417f837-805e-4fed-a430-ca919c8421dc
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 9be8165af499729c7b3a95c480cb64d0200e23fd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386616"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
`gcManagedToUnmanaged` Zarządzany Asystent debugowania (MDA) powoduje wyrzucania elementów bezużytecznych zawsze, gdy wątek przejścia z kodu zarządzanego do kodu niezarządzanego.  
  
## <a name="symptoms"></a>Symptomy  
 Składnik niezarządzane użytkownika zgłasza naruszenia zasad dostępu podczas próby użycia zarządzanego obiektu, który ma zostać udostępnione modelowi COM. Obiekt COM może zostały zwolnione. Naruszenia zasad dostępu jest niejednoznaczny.  
  
## <a name="cause"></a>Przyczyna  
 Jeśli niezarządzane składnik nie jest zliczanie zarządzanego obiektu COM poprawnie, środowisko uruchomieniowe można zebrać ujawniony dla modelu COM, gdy składnik niezarządzane nadal będzie zawierać odwołania do obiektu zarządzanego obiektu. Wywołania środowiska uruchomieniowego <xref:System.Runtime.InteropServices.Marshal.Release%2A> podczas wyrzucania, więc jeśli składnik użytkownika używa obiektu przed wyrzucania, następnie go zostanie nie jeszcze zostać zebrane. Jest to źródłem nondeterminism.  
  
## <a name="resolution"></a>Rozwiązanie  
 Włączenie tego Asystenta skraca czas między gdy obiekt jest uprawniona do kolekcji i <xref:System.Runtime.InteropServices.Marshal.Release%2A> jest wywoływana, co pomaga śledzić, który składnik niezarządzane najpierw próbuje uzyskać dostęp do połączonego obiektu.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Wyrzucanie elementów bezużytecznych zawsze, gdy wątek przejść z kodu zarządzanego do kodu niezarządzanego przyczyny.  
  
## <a name="output"></a>Dane wyjściowe  
 To zdarzenie MDA tworzy żadnych danych wyjściowych.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)  
 [gcUnmanagedToManaged](../../../docs/framework/debug-trace-profile/gcunmanagedtomanaged-mda.md)
