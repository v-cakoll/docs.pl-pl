---
title: gcManagedToUnmanaged MDA
description: Zapoznaj się z asystentem debugowania zarządzanego przez gcManagedToUnmanaged. To zdarzenie MDA może zostać aktywowane z powodu przedwcześnie wyrzucania elementów bezużytecznych podczas przejścia do kodu niezarządzanego.
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
ms.openlocfilehash: 76c621a1f2bb780d38228f2a84d4c77441774770
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415917"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
`gcManagedToUnmanaged`Asystent debugowania zarządzanego (MDA) powoduje wyrzucanie elementów bezużytecznych za każdym razem, gdy wątek przechodzi z zarządzanego do niezarządzanego kodu.  
  
## <a name="symptoms"></a>Objawy  
 Niezarządzany składnik użytkownika zgłasza naruszenie zasad dostępu podczas próby użycia zarządzanego obiektu, który został ujawniony w modelu COM. Obiekt COM wydaje się być wystawiony. Naruszenie zasad dostępu jest niejednoznaczne.  
  
## <a name="cause"></a>Przyczyna  
 Jeśli składnik niezarządzany nie odwołuje się prawidłowo do prawidłowego zliczania zarządzanego obiektu COM, środowisko uruchomieniowe może zebrać obiekt zarządzany uwidoczniony do modelu COM, gdy składnik niezarządzany nadal utrzymuje odwołanie do obiektu. Środowisko uruchomieniowe wywołuje <xref:System.Runtime.InteropServices.Marshal.Release%2A> podczas odzyskiwania pamięci, więc jeśli składnik użytkownika używa obiektu przed wystąpieniem bezużyteczności, wówczas nie został jeszcze zebrany. To jest źródło nieustalenia.  
  
## <a name="resolution"></a>Rozwiązanie  
 Włączenie tego asystenta skraca czas od momentu, gdy obiekt kwalifikuje się do kolekcji i <xref:System.Runtime.InteropServices.Marshal.Release%2A> jest wywoływany, ułatwiając śledzenie, który składnik niezarządzany najpierw próbuje uzyskać dostęp do zebranego obiektu.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Powoduje wyrzucanie elementów bezużytecznych po każdym przejścia wątku z zarządzanego do niezarządzanego kodu.  
  
## <a name="output"></a>Dane wyjściowe  
 To zdarzenie MDA nie generuje danych wyjściowych.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcManagedToUnmanaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
