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
ms.openlocfilehash: fca6b209e6432678a264f10762adb3871e3596ce
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217222"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
Asystent debugowania zarządzanego `reportAvOnComRelease` (MDA) jest uaktywniany, gdy wyjątki są zgłaszane z powodu błędów w odniesieniu do odwołań użytkownika podczas wykonywania międzyoperacyjności modelu COM i używania metody <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> połączonej z nieprzetworzonymi wywołaniami COM.  
  
## <a name="symptoms"></a>Objawy  
 Naruszenia dostępu i uszkodzenie pamięci.  
  
## <a name="cause"></a>Przyczyna  
 Czasami wyjątek jest zgłaszany z powodu błędów zliczania odwołań użytkownika podczas wykonywania międzyoperacyjności modelu COM i używania metody <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> połączonej z nieprzetworzonymi wywołaniami COM. Zwykle ten wyjątek jest odrzucany, ponieważ nie spowoduje to naruszenia zasad dostępu w środowisku CLR. Po włączeniu tego asystenta takie wyjątki mogą być wykrywane i raportowane zamiast po prostu odrzucone.  
  
## <a name="resolution"></a>Rozwiązanie  
 Zbadaj kod zliczania odwołań i Wyszukaj błędy, a także Zbadaj natywnych klientów obiektu, aby uzyskać odwołania do błędów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Dostępne są dwa tryby. Jeśli atrybut `allowAv` jest `true`, asystent uniemożliwia odrzucanie naruszenia zasad dostępu przez środowisko uruchomieniowe. Jeśli `allowAv` jest `false`, co jest ustawieniem domyślnym, środowisko uruchomieniowe odrzuca naruszenie zasad dostępu, ale użytkownik zgłasza komunikat ostrzegawczy informujący o tym, że wyjątek został zgłoszony i odrzucony.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
