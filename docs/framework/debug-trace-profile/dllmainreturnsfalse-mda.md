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
ms.openlocfilehash: 4987b025450f2207a01a472a0c39fc6da2de0782
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
---
# <a name="dllmainreturnsfalse-mda"></a>dllMainReturnsFalse MDA
`dllMainReturnsFalse` Zarządzany Asystent debugowania (MDA) jest włączone, jeśli zarządzanej `DllMain` funkcja zestawu użytkownika, wywołana z przyczyny DLL_PROCESS_ATTACH, zwraca wartość FALSE.  
  
## <a name="symptoms"></a>Symptomy  
 `DllMain` Funkcja zwróciła wartość FALSE, wskazujący, że jej nie zostało wykonane prawidłowo. Ponieważ mogą powodować problemy nieokreślonej `DllMain` funkcje zwykle zawierają kod inicjujący ważne.  
  
## <a name="cause"></a>Przyczyna  
 `DllMain` Eval jest wywołana z przyczyny DLL_PROCESS_ATTACH inicjowania biblioteki DLL od obciążenia. Jeśli zwraca wartość FALSE, oznacza to, że nie można zainicjować biblioteki DLL.  
  
## <a name="resolution"></a>Rozwiązanie  
 Analizowanie kodu `DllMain` funkcji DLL nie powiodło się i zidentyfikować przyczynę niepowodzenia inicjowania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Tylko raporty danych o wartości zwracanej przez `DllMain`.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat wskazujący, że `DllMain` funkcji o nazwie przyczyny DLL_PROCESS_ATTACH, zwróciła wartość FALSE. Należy pamiętać, że to zdarzenie MDA jest włączona tylko wtedy, gdy `DllMain` zaimplementowano w kodzie zarządzanym.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <dllMainReturnsFalse />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
