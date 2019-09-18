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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7452ae28d63c89845b45bf500c02e771f0b8f4df
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052611"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
Asystent `invalidGCHandleCookie` debugowania zarządzanego (MDA) jest aktywowany, gdy <xref:System.Runtime.InteropServices.GCHandle> zostanie podjęta próba konwersji <xref:System.IntPtr> z nieprawidłowego pliku cookie na plik.  
  
## <a name="symptoms"></a>Symptomy  
 Niezdefiniowane zachowanie, takie jak naruszenia zasad dostępu i uszkodzenie pamięci podczas próby użycia lub pobrania <xref:System.Runtime.InteropServices.GCHandle> <xref:System.IntPtr>z.  
  
## <a name="cause"></a>Przyczyna  
 Plik cookie prawdopodobnie jest nieprawidłowy, ponieważ nie został pierwotnie utworzony z <xref:System.Runtime.InteropServices.GCHandle>, <xref:System.Runtime.InteropServices.GCHandle> oznacza, że został już zwolniony, <xref:System.Runtime.InteropServices.GCHandle> jest plikiem cookie w innej domenie aplikacji lub został zorganizowany do kodu natywnego jako <xref:System.Runtime.InteropServices.GCHandle>ale przeszedł z powrotem do środowiska CLR <xref:System.IntPtr>jako, gdzie podjęto próbę rzutowania.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłowy <xref:System.IntPtr> plik cookie <xref:System.Runtime.InteropServices.GCHandle>dla.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Po włączeniu tego MDA debuger nie będzie już mógł śledzić katalogów głównych z powrotem do swoich obiektów, ponieważ wartości plików cookie przenoszone z powrotem różnią się od tych, które są zwracane, gdy MDA nie jest włączone.  
  
## <a name="output"></a>Dane wyjściowe  
 Zgłoszono <xref:System.IntPtr> nieprawidłową wartość pliku cookie.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidGCHandleCookie />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.GCHandle.FromIntPtr%2A>
- <xref:System.Runtime.InteropServices.GCHandle>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
