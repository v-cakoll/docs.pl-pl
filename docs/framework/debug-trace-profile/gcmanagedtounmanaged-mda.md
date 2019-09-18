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
ms.openlocfilehash: afc0fd47e51723a7b3ba1b07dffc49260f88917d
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052784"
---
# <a name="gcmanagedtounmanaged-mda"></a>gcManagedToUnmanaged MDA
Asystent `gcManagedToUnmanaged` debugowania zarządzanego (MDA) powoduje wyrzucanie elementów bezużytecznych za każdym razem, gdy wątek przechodzi z zarządzanego do niezarządzanego kodu.  
  
## <a name="symptoms"></a>Symptomy  
 Niezarządzany składnik użytkownika zgłasza naruszenie zasad dostępu podczas próby użycia zarządzanego obiektu, który został ujawniony w modelu COM. Obiekt COM wydaje się być wystawiony. Naruszenie zasad dostępu jest niejednoznaczne.  
  
## <a name="cause"></a>Przyczyna  
 Jeśli składnik niezarządzany nie odwołuje się prawidłowo do prawidłowego zliczania zarządzanego obiektu COM, środowisko uruchomieniowe może zebrać obiekt zarządzany uwidoczniony do modelu COM, gdy składnik niezarządzany nadal utrzymuje odwołanie do obiektu. Środowisko uruchomieniowe <xref:System.Runtime.InteropServices.Marshal.Release%2A> wywołuje podczas odzyskiwania pamięci, więc jeśli składnik użytkownika używa obiektu przed wystąpieniem bezużyteczności, wówczas nie został jeszcze zebrany. To jest źródło nieustalenia.  
  
## <a name="resolution"></a>Rozwiązanie  
 Włączenie tego asystenta skraca czas od momentu, gdy obiekt kwalifikuje się <xref:System.Runtime.InteropServices.Marshal.Release%2A> do kolekcji i jest wywoływany, ułatwiając śledzenie, który składnik niezarządzany najpierw próbuje uzyskać dostęp do zebranego obiektu.  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
- [gcUnmanagedToManaged](gcunmanagedtomanaged-mda.md)
