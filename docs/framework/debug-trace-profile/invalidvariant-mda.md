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
ms.openlocfilehash: 64f5a4425d70974bae8c4f7bec28041e687fe95f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59228487"
---
# <a name="invalidvariant-mda"></a>invalidVariant MDA
`invalidVariant` Zarządzanego Asystenta debugowania (MDA) jest uaktywniany podczas nieprawidłową `VARIANT` struktury napotkano podczas wywoływania z kodu natywnego lub niezarządzanego kodu zarządzanego.  
  
## <a name="symptoms"></a>Symptomy  
 Nieoczekiwane zachowanie podczas przejścia między kodu natywnego i zarządzanego obejmujące kierowania `VARIANT` do obiektu.  
  
## <a name="cause"></a>Przyczyna  
 Kod natywny jest przekazanie źle sformułowane `VARIANT` strukturę do kodu zarządzanego.  Środowisko uruchomieniowe próbuje kierować to `VARIANT` do obiektu i aktywuje MDA, jeśli `VARIANT` jest nieprawidłowy. Przykłady nieprawidłowy `VARIANT`obejmują S `VARIANT` z `VARTYPE` VT_EMPTY &#124; VT_BYREF lub `VARIANT` z `VARTYPE` VT_VARIANT.  
  
## <a name="resolution"></a>Rozwiązanie  
 Natywny lub kodowi niezarządzanemu przekazywanie `VARIANT` musi zapewnić, że `VARIANT` jest poprawnie sformułowana i zainicjowany.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 MDA nie ma wpływu na działanie w środowisku uruchomieniowym.  
  
## <a name="output"></a>Dane wyjściowe  
 MDA komunikat wskazujący, że środowisko wykonawcze nie wykryto nieprawidłową `VARIANT` przekazany do kodu zarządzanego przez moduł niezarządzanych.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
