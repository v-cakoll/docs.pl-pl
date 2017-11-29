---
title: invalidGCHandleCookie MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
caps.latest.revision: "8"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: 4757298a382085c1ffebc9a04e41eea81c31941b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
`invalidGCHandleCookie` Zarządzany Asystent debugowania (MDA) jest uaktywniany podczas konwersji z nieprawidłową <xref:System.IntPtr> pliku cookie do <xref:System.Runtime.InteropServices.GCHandle> zostanie podjęta.  
  
## <a name="symptoms"></a>Symptomy  
 Niezdefiniowane zachowanie, takie jak naruszenia zasad dostępu i uszkodzenie pamięci podczas próby użycia lub pobrać <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr>.  
  
## <a name="cause"></a>Przyczyna  
 Plik cookie jest prawdopodobnie nieprawidłowa, ponieważ nie został pierwotnie utworzony z <xref:System.Runtime.InteropServices.GCHandle>, reprezentuje <xref:System.Runtime.InteropServices.GCHandle> który już został zwolniony, plik cookie do <xref:System.Runtime.InteropServices.GCHandle> w domenie innej aplikacji lub został przekazywane do kodu macierzystego jako <xref:System.Runtime.InteropServices.GCHandle>ale przekazany do środowiska CLR jako <xref:System.IntPtr>, gdzie próbowano wykonać rzutowanie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłowe <xref:System.IntPtr> plik cookie <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Po włączeniu to zdarzenie MDA debuger nie jest już możliwość śledzenia certyfikaty główne do nich obiekty, ponieważ inne niż zwracany, gdy nie włączono MDA są przekazywane z powrotem wartości pliku cookie.  
  
## <a name="output"></a>Dane wyjściowe  
 Nieprawidłowa <xref:System.IntPtr> jest zgłaszana wartość pliku cookie.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>  
 <xref:System.Runtime.InteropServices.GCHandle>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
