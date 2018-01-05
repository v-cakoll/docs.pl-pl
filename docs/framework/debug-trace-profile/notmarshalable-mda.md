---
title: notMarshalable MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: "11"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 489f0e2ff4dc1eeaa9721ec6cf59faad0bee2ca8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="notmarshalable-mda"></a>notMarshalable MDA
`notMarshalable` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka wskaźnika interfejsu COM bez prawidłowy zarejestrowanego serwera proxy/stub lub niepoprawne `IMarshal` implementacja podczas próby interfejsu kierowanie interfejs między kontekstami.  
  
## <a name="symptoms"></a>Symptomy  
 Wywołania nie są obsługiwane lub występować w nieprawidłowego kontekstu do wskaźników interfejsów COM. wywołań.  
  
## <a name="cause"></a>Przyczyna  
 Nie prawidłowy zarejestrowanego serwera proxy/stub lub niepoprawne `IMarshal` podczas próby kierować interfejs między kontekstami.  
  
## <a name="resolution"></a>Rozwiązanie  
 Upewnij się, że masz pełnomocnika namiastki zarejestrowany oraz czy `IMarshal` implementacja jest nieprawidłowy.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko uruchomieniowe.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat opisujący problem.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <notMarshalable/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
