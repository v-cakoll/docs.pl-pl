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
ms.openlocfilehash: 4c36ec514645a38ef1228e76bdf6dbd06e886bae
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217505"
---
# <a name="failedqi-mda"></a>failedQI MDA
Asystent debugowania zarządzanego `failedQI` (MDA) jest uaktywniany, gdy wywołania środowiska uruchomieniowego `QueryInterface` na wskaźniku interfejsu COM w imieniu otoki (RCW) środowiska uruchomieniowego, a wywołanie `QueryInterface` kończy się niepowodzeniem.  
  
## <a name="symptoms"></a>Objawy  
 Rzutowanie otoki RCW kończy się niepowodzeniem lub wywołanie modelu COM z otoki RCW nieoczekiwanie zakończyło się niepowodzeniem.  
  
## <a name="cause"></a>Przyczyna  
  
- Wywołanie zostało wykonane z niewłaściwego kontekstu.  
  
- Zarejestrowany serwer proxy kończy się niepowodzeniem wywołania `QueryInterface`, ponieważ próba wywołania była w nieprawidłowym kontekście.  
  
- Serwer proxy należący do OLE zwrócił błąd HRESULT.  
  
## <a name="resolution"></a>Rozwiązanie  
 Zapoznaj się z dokumentacją MSDN dotyczącą reguł COM.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Jeśli wywołanie `QueryInterface` nie powiedzie się, kontekst jest przełączany i próba wywołania `QueryInterface` zostanie ponowiona, aby sprawdzić, czy wystąpił błąd w nieprawidłowym kontekście.  
  
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
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
