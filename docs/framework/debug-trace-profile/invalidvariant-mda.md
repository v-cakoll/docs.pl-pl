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
ms.openlocfilehash: 8d686621ae4aa087e1b4f4bea9df7fc3de758d40
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216276"
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
Asystent debugowania zarządzanego `invalidVariant` (MDA) jest uaktywniany po napotkaniu nieprawidłowej struktury `VARIANT` podczas wywołania z kodu natywnego lub niezarządzanego do kodu zarządzanego.  
  
## <a name="symptoms"></a>Objawy  
 Nieoczekiwane zachowanie podczas przejścia między kodem natywnym i zarządzanym obejmującym kierowanie `VARIANT` do obiektu.  
  
## <a name="cause"></a>Przyczyna  
 Kod natywny przekazuje nieprawidłowo sformułowaną strukturę `VARIANT` do kodu zarządzanego.  Środowisko uruchomieniowe próbuje zorganizować ten `VARIANT` do obiektu i aktywuje zdarzenie MDA, jeśli `VARIANT` jest nieprawidłowy. Przykłady nieprawidłowych `VARIANT`S obejmują `VARIANT` z `VARTYPE` VT_EMPTY &#124; VT_BYREF lub `VARIANT` z `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Rozwiązanie  
 Kod natywny lub niezarządzany przekazanie `VARIANT` musi mieć pewność, że `VARIANT` jest poprawnie sformułowany i zainicjowany.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Zdarzenie MDA nie ma wpływu na zachowanie środowiska uruchomieniowego.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat MDA wskazujący, że środowisko uruchomieniowe wykryło nieprawidłową `VARIANT` przekazaną do kodu zarządzanego przez moduł niezarządzany.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
