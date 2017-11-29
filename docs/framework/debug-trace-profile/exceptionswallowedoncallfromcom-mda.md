---
title: exceptionSwallowedOnCallFromCom MDA
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
caps.latest.revision: "13"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: d68e3f8659b0d5fe212c58443fe9a8b42f9cef89
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom MDA
`exceptionSwallowedOnCallFromCOM` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy wyjątek z wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) kodu wywoływana z modelu COM za pomocą metody, która nie ma typu zwracanego HRESULT niezarządzane.  
  
## <a name="symptoms"></a>Symptomy  
 Zwraca wywołania do zarządzanego składnika modelu COM o wartości FALSE lub 0. Alternatywnie Jeśli metoda ma zwrócony typ void, może istnieć żadnego wskazania, że wystąpił wyjątek podczas wykonywania metody. W takim przypadku wyjątek zostanie przechwycony dyskretnej i wykonywania nastąpi powrót do metody wywołującej COM.  
  
## <a name="cause"></a>Przyczyna  
 Wystąpił wyjątek, ale nie istnieje prawidłowy sposób do raportu.  
  
## <a name="resolution"></a>Rozwiązanie  
 Komunikat informacyjny tylko, nie zawsze świadczy o usterki.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Zwraca tylko dane dotyczące wyjątków w trybie dyskretnym zgłoszony.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informacyjny zawierający nazwę metody, wpisz nazwę i komunikat o wyjątku.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu Asystenci zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Przekazywanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
