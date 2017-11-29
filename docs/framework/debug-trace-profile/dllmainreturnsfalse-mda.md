---
title: dllMainReturnsFalse MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- managed debugging assistants (MDAs), DllMain returns false
- DllMainReturnsFalse MDA
- DllMain function
- MDAs (managed debugging assistants), DllMain returns false
ms.assetid: e2abdd04-f571-4b97-8c16-2221b8588429
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 91d2dfefc8de49770ec5c0b0083767bbb4b76c0b
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
