---
title: failedQI MDA
ms.date: 03/30/2017
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
author: mairaw
ms.author: mairaw
ms.openlocfilehash: fec1bfb402f3b394ceb36590c3a880f82c5cb101
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 09/17/2019
ms.locfileid: "71052797"
---
# <a name="failedqi-mda"></a>failedQI MDA
Asystent debugowania `QueryInterface` `QueryInterface` zarządzanego (MDA) jest uaktywniany, gdy środowisko uruchomieniowe wywołuje wskaźnik interfejsu com w imieniu otoki (RCW) środowiska uruchomieniowego, a wywołanie kończy się niepowodzeniem. `failedQI`  
  
## <a name="symptoms"></a>Symptomy  
 Rzutowanie otoki RCW kończy się niepowodzeniem lub wywołanie modelu COM z otoki RCW nieoczekiwanie zakończyło się niepowodzeniem.  
  
## <a name="cause"></a>Przyczyna  
  
- Wywołanie zostało wykonane z niewłaściwego kontekstu.  
  
- Zarejestrowanego serwera proxy nie powiodło się, `QueryInterface` ponieważ wywołanie było podejmowane w nieprawidłowym kontekście.  
  
- Serwer proxy należący do OLE zwrócił błąd HRESULT.  
  
## <a name="resolution"></a>Rozwiązanie  
 Zapoznaj się z dokumentacją MSDN dotyczącą reguł COM.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Jeśli wywołanie zakończy się niepowodzeniem, kontekst jest przełączany, `QueryInterface` a wywołanie zostanie ponowione, aby sprawdzić, czy wystąpił błąd w nieprawidłowym kontekście. `QueryInterface`  
  
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
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
