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
ms.openlocfilehash: 6033cd4178b2bc493794b5dcc527bc543ba24284
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216294"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
Asystent debugowania zarządzanego `invalidMemberDeclaration` (MDA) został aktywowany, aby zgłosić błąd, który występuje podczas określania sposobu organizowania parametrów elementu członkowskiego, który ma być wywoływany z modelu COM.  
  
## <a name="symptoms"></a>Objawy  
 Błąd HRESULT jest zwracany do modelu COM bez wywołania metody zarządzanej.  
  
## <a name="cause"></a>Przyczyna  
 Najprawdopodobniej jest to spowodowane niezgodnym atrybutem <xref:System.Runtime.InteropServices.MarshalAsAttribute> na jednym z parametrów.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłowe atrybuty <xref:System.Runtime.InteropServices.MarshalAsAttribute> w parametrach.  
  
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
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
