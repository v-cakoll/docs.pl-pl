---
title: marshalCleanupError MDA
ms.date: 03/30/2017
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 2399f72b6efcdf69d8ff4bb3bce541073063c750
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61753936"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA
`marshalCleanupError` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka błąd podczas próby czyszczenie tymczasowej struktur i pamięci używanej dla marshaling typów danych między granicami kodu natywnego i zarządzanego.  
  
## <a name="symptoms"></a>Symptomy  
 Podczas wprowadzania kodu natywnego i zarządzanego przejścia występuje przeciek pamięci, środowisko uruchomieniowe stan, takich jak kultury wątku nie jest przywracane lub błędy występują w <xref:System.Runtime.InteropServices.SafeHandle> oczyszczania.  
  
## <a name="cause"></a>Przyczyna  
 Wystąpił nieoczekiwany błąd podczas usuwania tymczasowego struktury.  
  
## <a name="resolution"></a>Rozwiązanie  
 Przejrzyj wszystkie <xref:System.Runtime.InteropServices.SafeHandle> destruktora, finalizator i implementacje organizatora niestandardowego dla błędów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat operacji, który uległ awarii podczas oczyszczania funkcji raportowania.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
