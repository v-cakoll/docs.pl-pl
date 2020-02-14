---
title: dllMainReturnsFalse MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
ms.openlocfilehash: 0b413521e0a2dc06c2ff0be642f080eaf541202f
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216443"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA
Asystent debugowania zarządzanego `dllMainReturnsFalse` (MDA) jest aktywowany, jeśli funkcja zarządzane `DllMain` zestawu użytkownika wywołana z przyczyną DLL_PROCESS_ATTACH zwraca wartość FALSE.  
  
## <a name="symptoms"></a>Objawy  
 Funkcja `DllMain` zwróciła wartość FALSE, co oznacza, że nie została wykonana prawidłowo. Może to spowodować nieokreślone problemy, ponieważ funkcje `DllMain` zwykle zawierają ważny kod inicjujący.  
  
## <a name="cause"></a>Przyczyna  
 Funkcja `DllMain` jest wywoływana z powodu DLL_PROCESS_ATTACH do inicjowania biblioteki DLL po załadowaniu. Jeśli zwraca wartość FALSE, oznacza to, że inicjowanie biblioteki DLL nie powiodło się.  
  
## <a name="resolution"></a>Rozwiązanie  
 Analizuj kod funkcji `DllMain` nieudanej biblioteki DLL i zidentyfikuj przyczynę niepowodzenia inicjacji.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Raportuje tylko dane dotyczące wartości zwracanej dla `DllMain`.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat wskazujący, że funkcja `DllMain` wywołana dla przyczyny DLL_PROCESS_ATTACH, zwróciła wartość FALSE. Należy pamiętać, że to MDA jest uaktywniane tylko wtedy, gdy `DllMain` jest zaimplementowana w kodzie zarządzanym.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
