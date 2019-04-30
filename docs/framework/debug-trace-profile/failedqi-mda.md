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
ms.openlocfilehash: 0ac478644561d2aab13d10811987d8d02c8d7608
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61754729"
---
# <a name="failedqi-mda"></a>failedQI MDA
`failedQI` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko wykonawcze wywołuje `QueryInterface` na wskaźnik interfejsu COM w imieniu wywoływana otoka środowiska uruchomieniowego (RCW), a `QueryInterface` wywołanie zakończy się niepowodzeniem.  
  
## <a name="symptoms"></a>Symptomy  
 Rzutowanie na RCW zakończy się niepowodzeniem lub wywołania dla modelu COM z RCW nieoczekiwanie zakończy się niepowodzeniem.  
  
## <a name="cause"></a>Przyczyna  
  
- Wykonano wywołanie z nieprawidłowym kontekście.  
  
- Zarejestrowany serwer proxy, kończy się niepowodzeniem `QueryInterface` wywołania, ponieważ podjęto próbę wywołania w nieprawidłowym kontekście.  
  
- Serwer proxy należące do OLE zwróciła błąd HRESULT.  
  
## <a name="resolution"></a>Rozwiązanie  
 Na karcie reguły COM można znaleźć w dokumentacji MSDN.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Jeśli `QueryInterface` wywołanie zakończy się niepowodzeniem, kontekst jest włączane i `QueryInterface` wywołanie podejmowana jest próba ponownie zobaczyć był nieprawidłowy kontekst na pozycji błędu.  
  
## <a name="output"></a>Dane wyjściowe  
 Zarządzane nazwy interfejsu, identyfikator GUID interfejsu i HRESULT błędu.  
  
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
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
