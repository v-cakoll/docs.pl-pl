---
title: pInvokeLog MDA
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0883849eee12922601e50c2337bb0048d77cab68
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052376"
---
# <a name="pinvokelog-mda"></a>pInvokeLog MDA
Asystent `pInvokeLog` debugowania zarządzanego (MDA) jest uaktywniany dla każdego unikatowego podpisu wywołania platformy używanego podczas wykonywania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat wskazujący podpis wywołania platformy używany podczas wykonywania.  
  
## <a name="configuration"></a>Konfiguracja  
 Każdy element dopasowania filtruje pliki. dll, do których są tworzone wywołania wywołania platformy.  
  
```xml  
<mdaConfig>  
  <assistants>  
    <pInvokeLog>  
      <filter>  
        <match dllName="user32.dll"/>  
        <match dllName="kernel32.dll"/>  
      </filter>  
    </pInvokeLog>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Wykorzystywanie niezarządzanych funkcji DLL](../interop/consuming-unmanaged-dll-functions.md)
