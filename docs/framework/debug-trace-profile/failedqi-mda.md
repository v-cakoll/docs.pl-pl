---
title: failedQI MDA
description: Zapoznaj się z asystentem debugowania zarządzanego w programie failedQI (MDA) w programie .NET, który może zostać aktywowany w przypadku niepowodzenia rzutowania lub wywołania modelu COM z otoki wywołującej (RCW) środowiska uruchomieniowego.
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
ms.openlocfilehash: 2d7f14c67d47e58bcb88eab4621df63d7c598a7a
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415943"
---
# <a name="failedqi-mda"></a>failedQI MDA
`failedQI`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe wywołuje `QueryInterface` wskaźnik interfejsu com w imieniu otoki (RCW) środowiska uruchomieniowego, a `QueryInterface` wywołanie kończy się niepowodzeniem.  
  
## <a name="symptoms"></a>Objawy  
 Rzutowanie otoki RCW kończy się niepowodzeniem lub wywołanie modelu COM z otoki RCW nieoczekiwanie zakończyło się niepowodzeniem.  
  
## <a name="cause"></a>Przyczyna  
  
- Wywołanie zostało wykonane z niewłaściwego kontekstu.  
  
- Zarejestrowanego serwera proxy nie powiodło się, `QueryInterface` ponieważ wywołanie było podejmowane w nieprawidłowym kontekście.  
  
- Serwer proxy należący do OLE zwrócił błąd HRESULT.  
  
## <a name="resolution"></a>Rozwiązanie  
 Zapoznaj się z dokumentacją MSDN dotyczącą reguł COM.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Jeśli `QueryInterface` wywołanie zakończy się niepowodzeniem, kontekst jest przełączany, a `QueryInterface` wywołanie zostanie ponowione, aby sprawdzić, czy wystąpił błąd w nieprawidłowym kontekście.  
  
## <a name="output"></a>Dane wyjściowe  
 Zarządzana nazwa interfejsu, identyfikator GUID interfejsu i HRESULT błędu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
