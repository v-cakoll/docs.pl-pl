---
title: notMarshalable MDA
ms.date: 03/30/2017
helpviewer_keywords:
- managed debugging assistants (MDAs), interface pointer not marshalable
- interface pointer not marshalable MDA
- MDAs (managed debugging assistants), interface pointer not marshalable
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- marshalable interface pointers
- MDAs (managed debugging assistants), marshaling
- notMarshalable MDA
ms.assetid: 96e7b2c1-843f-4d64-b519-740c3a18b50a
ms.openlocfilehash: 45db0e70b2446fa6e3175409bcc3844042f0acc0
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217282"
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
Asystent debugowania zarządzanego `notMarshalable` (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka wskaźnik interfejsu COM bez prawidłowego zarejestrowanego serwera proxy/zastępczego lub nieprawidłowej implementacji interfejsu `IMarshal` podczas próby zorganizowania interfejsu w wielu kontekstach.  
  
## <a name="symptoms"></a>Objawy  
 Wywołania nie są obsługiwane lub wywołania występują w nieprawidłowym kontekście wskaźników interfejsu COM.  
  
## <a name="cause"></a>Przyczyna  
 Brak prawidłowego zarejestrowanego serwera proxy/zastępczego lub nieprawidłowej `IMarshal` podczas próby zorganizowania interfejsu w wielu kontekstach.  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, że zarejestrowano procedurę pośredniczącą serwera proxy i że implementacja `IMarshal` jest prawidłowa.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat z opisem problemu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
