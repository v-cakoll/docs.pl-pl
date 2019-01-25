---
title: invalidMemberDeclaration MDA
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
author: mairaw
ms.author: mairaw
ms.openlocfilehash: c276df65497a0d8cafea80959b8193790c19ebba
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54667352"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
`invalidMemberDeclaration` Zarządzanego Asystenta debugowania (MDA) jest aktywowana Aby zgłosić błąd występujący podczas określania sposobu organizowania parametrów elementu członkowskiego, wywoływana z modelu COM.  
  
## <a name="symptoms"></a>Symptomy  
 Błąd HRESULT jest zwracana do COM bez zarządzanej metody o została wywołana.  
  
## <a name="cause"></a>Przyczyna  
 Jest to najprawdopodobniej z powodu niezgodnej <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu na jeden z parametrów.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłowy <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybuty w parametrach.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informacyjny zawierające nazwy elementu członkowskiego, wpisz nazwę i komunikat o błędzie.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także
- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
