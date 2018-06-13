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
ms.openlocfilehash: dfaa77adef7cdc21b1ad8abaca1439361a33d4b8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386629"
---
# <a name="gcunmanagedtomanaged-mda"></a>gcUnmanagedToManaged MDA
`gcUnmanagedToManaged` Zarządzany Asystent debugowania (MDA) powoduje wyrzucania elementów bezużytecznych zawsze, gdy wątek przejścia z niezarządzanych do kodu zarządzanego.  
  
## <a name="symptoms"></a>Symptomy  
 Aplikacji uruchomionej składniki niezarządzane użytkownika przy użyciu platformy i modelu COM. wywołania powoduje naruszenie dostępu niedeterministyczne w środowisku CLR.  
  
## <a name="cause"></a>Przyczyna  
 Jeśli aplikacja działa składniki niezarządzane użytkownika, następnie te składniki mógł uszkodzony stosu zebranego przez pamięci. Powoduje to naruszenie zasad dostępu w środowisku CLR, gdy moduł garbage collector spróbuje przeprowadzić wykres obiektu.  
  
## <a name="resolution"></a>Rozwiązanie  
 Włączenie tego Asystenta skraca czas między gdy niezarządzany składnika uszkodzi stosu zebranego przez pamięci i gdy naruszenia zasad dostępu się stanie, wymuszając wyrzucania elementów bezużytecznych występuje przed każdym Zarządzanie zmianami.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Powoduje, że wyrzucania elementów bezużytecznych zawsze, gdy wątek przejścia z niezarządzanych w kodzie zarządzanym.  
  
## <a name="output"></a>Dane wyjściowe  
 To zdarzenie MDA tworzy żadnych danych wyjściowych.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <gcUnmanagedToManaged/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [gcManagedToUnmanaged](../../../docs/framework/debug-trace-profile/gcmanagedtounmanaged-mda.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
