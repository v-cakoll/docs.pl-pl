---
title: reportAvOnComRelease MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), reference counting errors
- exceptions, reference counting errors
- ReportAvOnComRelease MDA
- COM release access violations
- user reference counting errors
- managed debugging assistants (MDAs), reference counting errors
- report access violation on Com release
- reference counting errors
ms.assetid: a2b86b63-08b2-4943-b344-3c2cf46ccd31
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 0bea73a30cb103f0e72caf73a633229a0719dc6c
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052324"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
Asystent `reportAvOnComRelease` debugowania zarządzanego (MDA) jest uaktywniany, gdy wyjątki są zgłaszane z powodu błędów zliczania odwołań do użytkownika podczas wykonywania międzyoperacyjności <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> modelu COM i <xref:System.Runtime.InteropServices.Marshal.Release%2A> używania metody lub w połączeniu z nieprzetworzonymi wywołaniami com.  
  
## <a name="symptoms"></a>Symptomy  
 Naruszenia dostępu i uszkodzenie pamięci.  
  
## <a name="cause"></a>Przyczyna  
 Czasami wyjątek jest zgłaszany z powodu błędów zliczania odwołań użytkownika podczas wykonywania międzyoperacyjności modelu COM <xref:System.Runtime.InteropServices.Marshal.Release%2A> i <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> używania metody lub w połączeniu z nieprzetworzonymi wywołaniami com. Zwykle ten wyjątek jest odrzucany, ponieważ nie spowoduje to naruszenia zasad dostępu w środowisku CLR. Po włączeniu tego asystenta takie wyjątki mogą być wykrywane i raportowane zamiast po prostu odrzucone.  
  
## <a name="resolution"></a>Rozwiązanie  
 Zbadaj kod zliczania odwołań i Wyszukaj błędy, a także Zbadaj natywnych klientów obiektu, aby uzyskać odwołania do błędów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Dostępne są dwa tryby. Jeśli atrybut ma `true`wartość, asystent uniemożliwia odrzucanie naruszenia zasad dostępu przez środowisko uruchomieniowe. `allowAv` Jeśli `allowAv` jest`false`to ustawienie domyślne, środowisko uruchomieniowe odrzuca naruszenie zasad dostępu, ale komunikat ostrzegawczy jest raportowany użytkownikowi, aby wskazać, że wyjątek został zgłoszony i odrzucony.  
  
## <a name="output"></a>Dane wyjściowe  
 Jeśli to możliwe, dane wyjściowe zawierają oryginalną tablicę sieciową wskaźnika interfejsu COM. W przeciwnym razie zostanie wyświetlony komunikat informacyjny.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <reportAvOnComRelease />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
