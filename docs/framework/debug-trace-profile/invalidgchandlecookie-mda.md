---
title: invalidGCHandleCookie MDA
description: Przejrzyj invalidGCHandleCookie Managed Debug Assistant (MDA), który jest uaktywniany w przypadku próby konwersji z nieprawidłowego pliku cookie IntPtr na GCHandle.
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid cookies
- cookies, invalid
- managed debugging assistants (MDAs), invalid cookies
- InvalidGCHandleCookie MDA
- invalid cookies
ms.assetid: 613ad742-3c11-401d-a6b3-893ceb8de4f8
ms.openlocfilehash: 1063b7be902d3063717b6639564d819ef3292c0e
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051301"
---
# <a name="invalidgchandlecookie-mda"></a>invalidGCHandleCookie MDA
`invalidGCHandleCookie`Asystent debugowania zarządzanego (MDA) jest aktywowany, gdy <xref:System.IntPtr> <xref:System.Runtime.InteropServices.GCHandle> zostanie podjęta próba konwersji z nieprawidłowego pliku cookie na plik.  
  
## <a name="symptoms"></a>Objawy  
 Niezdefiniowane zachowanie, takie jak naruszenia zasad dostępu i uszkodzenie pamięci podczas próby użycia lub pobrania <xref:System.Runtime.InteropServices.GCHandle> z <xref:System.IntPtr> .  
  
## <a name="cause"></a>Przyczyna  
 Plik cookie prawdopodobnie jest nieprawidłowy, ponieważ nie został pierwotnie utworzony z programu <xref:System.Runtime.InteropServices.GCHandle> , oznacza, <xref:System.Runtime.InteropServices.GCHandle> że został już zwolniony, jest plikiem cookie <xref:System.Runtime.InteropServices.GCHandle> w innej domenie aplikacji lub został zorganizowany do kodu natywnego jako a, ale został przekierowany z <xref:System.Runtime.InteropServices.GCHandle> powrotem do środowiska CLR jako <xref:System.IntPtr> , gdzie podjęto próbę wykonania rzutowania.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłowy <xref:System.IntPtr> plik cookie dla <xref:System.Runtime.InteropServices.GCHandle> .  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Po włączeniu tego MDA debuger nie będzie już mógł śledzić katalogów głównych z powrotem do swoich obiektów, ponieważ wartości plików cookie przenoszone z powrotem różnią się od tych, które są zwracane, gdy MDA nie jest włączone.  
  
## <a name="output"></a>Dane wyjściowe  
 <xref:System.IntPtr>Zgłoszono nieprawidłową wartość pliku cookie.  
  
## <a name="configuration"></a>Konfigurowanie  
  
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
