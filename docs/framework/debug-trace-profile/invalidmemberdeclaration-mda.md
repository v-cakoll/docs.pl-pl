---
title: invalidMemberDeclaration MDA
description: Zapoznaj się z asystentem debugowania zarządzanego przez invalidMemberDeclaration, który jest wywoływany w przypadku zwrócenia błędu HRESULT do modelu COM bez wywoływania metody zarządzanej.
ms.date: 03/30/2017
helpviewer_keywords:
- invalid member declaration
- InvalidMemberDeclaration MDA
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
ms.assetid: a84dd9a3-d6cf-4824-989a-ecbbf443eeb4
ms.openlocfilehash: 5dbfba2baec3263d91746c06379438e97a81f005
ms.sourcegitcommit: 0edbeb66d71b8df10fcb374cfca4d731b58ccdb2
ms.contentlocale: pl-PL
ms.lasthandoff: 07/07/2020
ms.locfileid: "86051717"
---
# <a name="invalidmemberdeclaration-mda"></a>invalidMemberDeclaration MDA
`invalidMemberDeclaration`Asystent debugowania zarządzanego (MDA) został aktywowany, aby zgłosić błąd, który występuje podczas określania sposobu organizowania parametrów elementu członkowskiego, który ma być wywoływany z modelu com.  
  
## <a name="symptoms"></a>Objawy  
 Błąd HRESULT jest zwracany do modelu COM bez wywołania metody zarządzanej.  
  
## <a name="cause"></a>Przyczyna  
 Najprawdopodobniej ze względu na niezgodny <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybut na jednym z parametrów.  
  
## <a name="resolution"></a>Rozwiązanie  
 Określ prawidłowe <xref:System.Runtime.InteropServices.MarshalAsAttribute> atrybuty dla parametrów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informacyjny zawierający nazwę elementu członkowskiego, nazwę typu i komunikat o błędzie.  
  
## <a name="configuration"></a>Konfigurowanie  
  
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
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
