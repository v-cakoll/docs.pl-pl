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
ms.openlocfilehash: 1a14c548ce960d53f47934595171189db28edfbb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216153"
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA
Asystent debugowania zarządzanego `marshalCleanupError` (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka błąd podczas próby oczyszczenia tymczasowych struktur i pamięci używanej do organizowania typów danych między natywną i zarządzaną granicami kodu.  
  
## <a name="symptoms"></a>Objawy  
 Przeciek pamięci występuje podczas wykonywania natywnych i zarządzanych przejść do kodu, stan środowiska uruchomieniowego, taki jak kultura wątku nie jest przywracany lub błędy występujące w <xref:System.Runtime.InteropServices.SafeHandle> oczyszczanie.  
  
## <a name="cause"></a>Przyczyna  
 Wystąpił nieoczekiwany błąd podczas czyszczenia struktur tymczasowych.  
  
## <a name="resolution"></a>Rozwiązanie  
 Przejrzyj wszystkie za<xref:System.Runtime.InteropServices.SafeHandle> destruktory, finalizatory i niestandardowe implementacje organizatora pod kątem błędów.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
