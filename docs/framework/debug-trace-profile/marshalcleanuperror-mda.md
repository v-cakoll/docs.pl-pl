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
ms.openlocfilehash: ab3690cac28ef572b19cadb632662590d1ea04c7
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052479"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA
Asystent `marshalCleanupError` debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka błąd podczas próby oczyszczenia tymczasowych struktur i pamięci używanej do organizowania typów danych między natywnymi i zarządzanymi granicami kodu.  
  
## <a name="symptoms"></a>Symptomy  
 Przeciek pamięci występuje podczas wykonywania natywnych i zarządzanych przejść do kodu, stan środowiska uruchomieniowego, taki jak kultura wątku nie jest przywracany <xref:System.Runtime.InteropServices.SafeHandle> lub błędy pojawiają się w wyniku czyszczenia.  
  
## <a name="cause"></a>Przyczyna  
 Wystąpił nieoczekiwany błąd podczas czyszczenia struktur tymczasowych.  
  
## <a name="resolution"></a>Rozwiązanie  
 Przejrzyj wszystkie <xref:System.Runtime.InteropServices.SafeHandle> implementacje destruktora, finalizatora i niestandardowego organizatora pod kątem błędów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat zgłaszający operację, która nie powiodła się podczas czyszczenia.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
