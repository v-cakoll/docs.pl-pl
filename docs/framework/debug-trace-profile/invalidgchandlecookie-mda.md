---
title: invalidGCHandleCookie MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: c1d8fab863c34313c0cdb778136c6f69a64defeb
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216304"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
Asystent debugowania zarządzanego `invalidGCHandleCookie` (MDA) jest aktywowany, gdy zostanie podjęta próba konwersji z nieprawidłowego <xref:System.IntPtr> pliku cookie na <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="symptoms"></a>Objawy  
 Niezdefiniowane zachowanie, takie jak naruszenia zasad dostępu i uszkodzenie pamięci podczas próby użycia lub pobrania <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr>.  
  
## <a name="cause"></a>Przyczyna  
 Plik cookie prawdopodobnie jest nieprawidłowy, ponieważ nie został pierwotnie utworzony na podstawie <xref:System.Runtime.InteropServices.GCHandle>, reprezentuje <xref:System.Runtime.InteropServices.GCHandle>, który został już zwolniony, jest plikiem cookie w <xref:System.Runtime.InteropServices.GCHandle> w innej domenie aplikacji lub został zorganizowany do kodu natywnego jako <xref:System.Runtime.InteropServices.GCHandle>, ale został przekierowany z powrotem do środowiska CLR jako <xref:System.IntPtr>, gdzie nastąpiło próba rzutowania.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłowy plik cookie <xref:System.IntPtr> dla <xref:System.Runtime.InteropServices.GCHandle>.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Po włączeniu tego MDA debuger nie będzie już mógł śledzić katalogów głównych z powrotem do swoich obiektów, ponieważ wartości plików cookie przenoszone z powrotem różnią się od tych, które są zwracane, gdy MDA nie jest włączone.  
  
## <a name="output"></a>Dane wyjściowe  
 Zgłoszono nieprawidłową wartość pliku cookie <xref:System.IntPtr>.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
