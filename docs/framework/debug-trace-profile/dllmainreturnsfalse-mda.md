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
ms.openlocfilehash: c513ba06ac79eb3da229605120c4f59ab8d32665
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54554546"
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA
`dllMainReturnsFalse` Zarządzanego Asystenta debugowania (MDA) jest włączone, jeśli zarządzanej `DllMain` funkcja zestawu użytkownika o nazwie z powodu DLL_PROCESS_ATTACH, zwraca wartość FALSE.  
  
## <a name="symptoms"></a>Symptomy  
 `DllMain` Funkcja zwróciła wartość FALSE, wskazujący, że jej nie zostało wykonane prawidłowo. Może to spowodować problemy z nieokreślonej, ponieważ `DllMain` funkcje zwykle zawierają kod inicjujący ważne.  
  
## <a name="cause"></a>Przyczyna  
 `DllMain` Funkcja jest wywoływana z przyczyną DLL_PROCESS_ATTACH Inicjowanie biblioteki DLL, podczas ładowania. Jeśli zostanie zwrócona wartość FALSE, oznacza to, że inicjowanie biblioteki DLL nie powiodło się.  
  
## <a name="resolution"></a>Rozwiązanie  
 Analizowanie kodu `DllMain` funkcji DLL nie powiodło się i zidentyfikować przyczynę niepowodzenia inicjowania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Informuje jedynie dane o wartości zwracanej przez `DllMain`.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat wskazujący, że `DllMain` funkcja, o nazwie powodu DLL_PROCESS_ATTACH, zwróciła wartość FALSE. Należy pamiętać, że to zdarzenie MDA jest aktywowane tylko wtedy, gdy `DllMain` zaimplementowano w kodzie zarządzanym.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
