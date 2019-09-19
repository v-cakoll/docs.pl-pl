---
title: dllMainReturnsFalse MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
author: mairaw
ms.author: mairaw
ms.openlocfilehash: adc05ae9bd357c142ff09de069aff446b5ea60e8
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052855"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA
Asystent debugowania `DllMain` zarządzanego (MDA) jest aktywowany, jeśli zarządzana funkcja zestawu użytkownika wywołana z przyczyną DLL_PROCESS_ATTACH zwraca wartość false. `dllMainReturnsFalse`  
  
## <a name="symptoms"></a>Symptomy  
 `DllMain` Funkcja zwróciła wartość false, co oznacza, że nie została wykonana prawidłowo. Może to spowodować nieokreślone problemy, ponieważ `DllMain` funkcje zwykle zawierają ważny kod inicjujący.  
  
## <a name="cause"></a>Przyczyna  
 `DllMain` Funkcja jest wywoływana z przyczyną DLL_PROCESS_ATTACH dla inicjalizacji biblioteki DLL po załadowaniu. Jeśli zwraca wartość FALSE, oznacza to, że inicjowanie biblioteki DLL nie powiodło się.  
  
## <a name="resolution"></a>Rozwiązanie  
 Analizuj kod `DllMain` funkcji nieudanej biblioteki DLL i zidentyfikuj przyczynę niepowodzenia inicjacji.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Raportuje tylko dane dotyczące wartości zwracanej dla `DllMain`.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informujący o tym `DllMain` , że funkcja wywołana dla przyczyny DLL_PROCESS_ATTACH zwraca wartość false. Należy zauważyć, że to MDA jest uaktywniane tylko wtedy, gdy `DllMain` jest zaimplementowany w kodzie zarządzanym.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
