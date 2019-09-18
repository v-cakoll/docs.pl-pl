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
ms.openlocfilehash: c34f160b643a0431168097d3832357b4ac6e4557
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052572"
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
Asystent debugowania `VARIANT` zarządzanego (MDA) jest uaktywniany po napotkaniu nieprawidłowej struktury podczas wywołania z kodu natywnego lub niezarządzanego do kodu zarządzanego. `invalidVariant`  
  
## <a name="symptoms"></a>Symptomy  
 Nieoczekiwane zachowanie podczas przejścia między kodem natywnym i zarządzanym obejmującym kierowanie `VARIANT` do obiektu.  
  
## <a name="cause"></a>Przyczyna  
 Kod natywny przekazuje nieprawidłowo sformułowaną `VARIANT` strukturę do kodu zarządzanego.  Środowisko uruchomieniowe próbuje zorganizować `VARIANT` ten obiekt w celu aktywowania go, `VARIANT` Jeśli element jest nieprawidłowy. `VARIANT`Przykłady nieprawidłowych wartości S `VARIANT` obejmują `VARTYPE` element &#124; `VARIANT` with VT_EMPTY VT_BYREF lub `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Rozwiązanie  
 Kod natywny lub niezarządzany `VARIANT` przekazujący musi mieć `VARIANT` pewność, że jest poprawnie sformułowany i zainicjowany.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Zdarzenie MDA nie ma wpływu na zachowanie środowiska uruchomieniowego.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat MDA wskazujący, że środowisko uruchomieniowe wykryło nieprawidłowe `VARIANT` przekazanie do zarządzanego kodu przez moduł niezarządzany.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidVariant />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
