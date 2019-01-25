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
ms.openlocfilehash: c70c70f251fca9312019d4c63304e8354bf87fd1
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54729161"
---
# <a name="reportavoncomrelease-mda"></a>reportAvOnComRelease MDA
`reportAvOnComRelease` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy wyjątki zostaną zgłoszone ze względu na użytkownika zliczanie błędów podczas wykonywania COM międzyoperacyjności i korzystać z funkcji <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody w połączeniu z pierwotnych wywołania COM.  
  
## <a name="symptoms"></a>Symptomy  
 Naruszenia zasad dostępu i uszkodzenie pamięci.  
  
## <a name="cause"></a>Przyczyna  
 Czasami wyjątek jest zgłaszany z powodu użytkownika zliczanie błędów podczas wykonywania COM międzyoperacyjności i korzystać z funkcji <xref:System.Runtime.InteropServices.Marshal.Release%2A> lub <xref:System.Runtime.InteropServices.Marshal.ReleaseComObject%2A> metody w połączeniu z pierwotnych wywołania COM. Zazwyczaj ten wyjątek jest pomijany, ponieważ w przeciwnym razie mogłoby spowodować naruszenie zasad dostępu w środowisku CLR, wyłączania go. Po włączeniu tego Asystenta wyjątków można wykryte i zgłaszane zamiast po prostu zostanie odrzucony.  
  
## <a name="resolution"></a>Rozwiązanie  
 Sprawdź, której można się odwołać zliczanie kodu i poszukaj błędów, a także sprawdzając klientów natywnych obiektów dla zliczanie błędów odwołań.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Dostępne są dwa tryby. Jeśli `allowAv` atrybut jest `true`, Asystenta zapobiega środowiska uruchomieniowego odrzucanie naruszenie zasad dostępu. Jeśli `allowAv` jest `false`, co jest ustawieniem domyślnym, środowisko uruchomieniowe odrzuca naruszenie zasad dostępu, ale komunikat ostrzegawczy jest zgłaszany użytkownikowi, aby wskazać, czy wyjątek został zgłoszony i odrzucone.  
  
## <a name="output"></a>Dane wyjściowe  
 Jeśli to możliwe dane wyjściowe zawierają wskaźnika interfejsu COM vtable oryginalnej. W przeciwnym razie zostanie wyświetlony komunikat informacyjny.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
