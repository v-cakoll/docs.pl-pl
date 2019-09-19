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
ms.openlocfilehash: fe15d718a9c5f91bfae4f37c04e726990e2fbd45
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052585"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
Asystent `invalidMemberDeclaration` debugowania zarządzanego (MDA) został aktywowany, aby zgłosić błąd, który występuje podczas określania sposobu organizowania parametrów elementu członkowskiego, który ma być wywoływany z modelu com.  
  
## <a name="symptoms"></a>Symptomy  
 Błąd HRESULT jest zwracany do modelu COM bez wywołania metody zarządzanej.  
  
## <a name="cause"></a>Przyczyna  
 Najprawdopodobniej ze względu na niezgodny <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut na jednym z parametrów.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłowe <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybuty dla parametrów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informacyjny zawierający nazwę elementu członkowskiego, nazwę typu i komunikat o błędzie.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
