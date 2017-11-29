---
title: marshalCleanupError MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- cleanup operations
- marshaling, run-time errors
- managed debugging assistants (MDAs), marshaling
- MDAs (managed debugging assistants), marshaling
- marshaling cleanup error
- MarshalCleanupError MDA
- memory, cleanup errors
ms.assetid: 2f5d9e7c-ae51-4155-a435-54347aa1f091
caps.latest.revision: "12"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: c78fedaab26ff7f1da7bccd98c83a90e550d9014
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="marshalcleanuperror-mda"></a>marshalCleanupError MDA
`marshalCleanupError` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy środowisko uruchomieniowe języka wspólnego (CLR) napotka błąd podczas próby wyczyścić tymczasowego struktury i pamięć używana na potrzeby organizowanie typów danych między granicami kodu natywnego i zarządzanego.  
  
## <a name="symptoms"></a>Symptomy  
 Podczas wprowadzania kodu natywnego i zarządzanego przejścia występuje przeciek pamięci, środowiska uruchomieniowego stanu, takich jak kultury wątku nie jest przywracana lub w występują błędy <xref:System.Runtime.InteropServices.SafeHandle> oczyszczania.  
  
## <a name="cause"></a>Przyczyna  
 Wystąpił nieoczekiwany błąd podczas usuwania tymczasowego struktury.  
  
## <a name="resolution"></a>Rozwiązanie  
 Przejrzyj wszystkie <xref:System.Runtime.InteropServices.SafeHandle> destruktor, finalizatora i implementacje organizatora niestandardowego błędów.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat operacji, które zakończyły się niepowodzeniem podczas oczyszczania funkcji raportowania.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <marshalCleanupError />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Przekazywanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
