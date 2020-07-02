---
title: notMarshalable MDA
description: Zapoznaj się z asystentem debugowania zarządzanego notMarshalable, który może uaktywnić, jeśli wywołania nie są obsługiwane lub występują w nieprawidłowym kontekście wskaźników interfejsu COM.
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
ms.openlocfilehash: b464d914a8d83504daaf4cb276914da7798262dc
ms.sourcegitcommit: c23d9666ec75b91741da43ee3d91c317d68c7327
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/01/2020
ms.locfileid: "85803797"
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
`notMarshalable`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka wskaźnik interfejsu COM bez prawidłowego zarejestrowanego serwera proxy/zastępczego lub nieprawidłowej `IMarshal` implementacji interfejsu podczas próby zorganizowania interfejsu w wielu kontekstach.  
  
## <a name="symptoms"></a>Objawy  
 Wywołania nie są obsługiwane lub wywołania występują w nieprawidłowym kontekście wskaźników interfejsu COM.  
  
## <a name="cause"></a>Przyczyna  
 Brak prawidłowego zarejestrowanego serwera proxy/zastępczego lub nieprawidłowej `IMarshal` próby zorganizowania interfejsu w wielu kontekstach.  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, że zarejestrowano procedurę pośredniczącą serwera proxy i że `IMarshal` implementacja jest prawidłowa.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat z opisem problemu.  
  
## <a name="configuration"></a>Konfigurowanie  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
