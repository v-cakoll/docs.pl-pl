---
title: invalidMemberDeclaration MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
caps.latest.revision: "9"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d4f625cbc7d7c46eee5b2eb8d7e47d4a5754fc26
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
`invalidMemberDeclaration` Zarządzany Asystent debugowania (MDA) jest aktywowana Aby zgłosić błąd występujący podczas ustalania sposobu zorganizowania parametrów członka do wywoływania z modelu COM.  
  
## <a name="symptoms"></a>Symptomy  
 Błąd HRESULT jest zwracana do modelu COM bez zarządzanego o została wywołana metoda.  
  
## <a name="cause"></a>Przyczyna  
 Jest to najprawdopodobniej spowodowane niezgodną <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutu na jeden z parametrów.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłową <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybutów dla parametrów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informacyjny zawierającego nazwę elementu członkowskiego, wpisz nazwę i komunikat o błędzie.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidMemberDeclaration/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
