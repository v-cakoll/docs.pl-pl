---
title: pInvokeLog MDA
description: Informacje o programie pInvokeLog Managed Debug Assistant (MDA), który jest uaktywniany dla każdego unikatowego podpisu wywołania platformy używanego podczas wykonywania w programie .NET.
ms.date: 03/30/2017
helpviewer_keywords:
- signatures, platform invoke
- MDAs (managed debugging assistants), platform invoke
- platform invoke, run-time errors
- platform invoke log
- PInvokeLog MDA
- managed debugging assistants (MDAs), platform invoke
ms.assetid: b830444a-5003-49fe-b89b-b8bee22f7b1a
ms.openlocfilehash: 05af4e17a91f7c0d8f3576a86d3d784ef6666aed
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803693"
---
# <a name="pinvokelog-mda"></a>pInvokeLog MDA
`pInvokeLog`Asystent debugowania zarządzanego (MDA) jest uaktywniany dla każdego unikatowego podpisu wywołania platformy używanego podczas wykonywania.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat wskazujący podpis wywołania platformy używany podczas wykonywania.  
  
## <a name="configuration"></a>Konfigurowanie  
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
