---
title: invalidVariant MDA
ms.date: 03/30/2017
helpviewer_keywords:
- MDAs (managed debugging assistants), invalid variant
- VARIANT type errors
- InvalidVariant MDA
- invalid VARIANT types
- managed debugging assistants (MDAs), invalid variant
ms.assetid: d273e070-d1b1-4a53-a9c7-7af837b04a3d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 426b9df449b12d2f34fa70fc721cc050fa3e4ddd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386722"
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
`invalidVariant` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy nieprawidłową `VARIANT` struktury napotkano podczas wywoływania z kodu natywnego lub niezarządzane do zarządzanego kodu.  
  
## <a name="symptoms"></a>Symptomy  
 Nieoczekiwane zachowanie podczas przejścia między kodu natywnego i zarządzanego, obejmujące kierowanie `VARIANT` do obiektu.  
  
## <a name="cause"></a>Przyczyna  
 Kod natywny jest przekazanie źle sformułowane `VARIANT` struktury do kodu zarządzanego.  Środowisko wykonawcze próbuje kierować to `VARIANT` do obiektu i aktywuje MDA, jeśli `VARIANT` jest nieprawidłowy. Przykłady nieprawidłowy `VARIANT`obejmują S `VARIANT` z `VARTYPE` VT_EMPTY &#124; VT_BYREF lub `VARIANT` z `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Rozwiązanie  
 Kod natywny lub niezarządzane przekazywanie `VARIANT` upewnij się, że `VARIANT` jest poprawnie sformułowany i zainicjować.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 MDA nie ma wpływu na zachowanie środowiska uruchomieniowego.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat MDA wskazujący, że środowisko wykonawcze wykryto nieprawidłową `VARIANT` przekazany do kodu zarządzanego przez moduł niezarządzane.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
