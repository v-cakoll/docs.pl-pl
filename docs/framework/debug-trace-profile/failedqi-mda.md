---
title: failedQI MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- failed QueryInterface
- FailedQI MDA
- QueryInterface call failures
- MDAs (managed debugging assistants), failed QueryInterface
- managed debugging assistants (MDAs), failed QueryInterface
ms.assetid: 902dc863-34b3-477c-b433-b8a6bb6133c6
caps.latest.revision: "15"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: bc717f1500d202ae2590adb61b0376e93eba0944
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="failedqi-mda"></a>failedQI MDA
`failedQI` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy środowisko urchomieniowe wywołuje `QueryInterface` w imieniu wywoływana otoka środowiska uruchomieniowego (otoki RCW), wskaźnika interfejsu COM i `QueryInterface` wywołania kończy się niepowodzeniem.  
  
## <a name="symptoms"></a>Symptomy  
 Rzutowanie na otoki RCW nie powiedzie się lub wywołania modelu COM z otoki RCW nieoczekiwanie nie powiodło się.  
  
## <a name="cause"></a>Przyczyna  
  
-   Połączenie jest nawiązywane z nieprawidłowego kontekstu.  
  
-   Kończy się niepowodzeniem zarejestrowanego serwera proxy `QueryInterface` wywołać, ponieważ podjęto próbę wywołania w nieprawidłowego kontekstu.  
  
-   Serwer proxy należące do OLE zwróciła błąd HRESULT.  
  
## <a name="resolution"></a>Rozwiązanie  
 W regułach COM można znaleźć w dokumentacji MSDN.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 Jeśli `QueryInterface` przełączono wywołanie się nie powiedzie, kontekst oraz `QueryInterface` wywołanie jest ponownie umieszczanie, aby zobaczyć, czy Nieprawidłowy kontekst został na pozycji błędu.  
  
## <a name="output"></a>Dane wyjściowe  
 Nazwa zarządzanego interfejsu, identyfikatora GUID interfejsu i HRESULT błędu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <failedQI/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
