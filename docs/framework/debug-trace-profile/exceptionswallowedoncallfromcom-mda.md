---
title: exceptionSwallowedOnCallFromCom MDA
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4f076cbc556c7d9feff8a226f050743cd7728622
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59148151"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom MDA
`exceptionSwallowedOnCallFromCOM` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy wyjątek jest generowany z wspólnego języka środowiska uruchomieniowego (języka wspólnego CLR) kodu wywoływane z modelu COM za pomocą metody, która nie ma wartość HRESULT niezarządzany typ zwracany.  
  
## <a name="symptoms"></a>Symptomy  
 Wywołanie zarządzanego składnika z modelu COM zwraca wartość FALSE lub 0. Alternatywnie Jeśli metoda ma zwracać typ void, może istnieć żadnego wskazania, że wystąpił wyjątek podczas wykonywania metody. W tym przypadku wyjątek zostanie zgłoszony dyskretnie i wykonanie nastąpi powrót do obiektu wywołującego COM.  
  
## <a name="cause"></a>Przyczyna  
 Wystąpił wyjątek, ale nie istnieje prawidłowy sposób Zgłoś ją.  
  
## <a name="resolution"></a>Rozwiązanie  
 Komunikat o charakterze informacyjnym tylko, nie zawsze wskazuje usterkę.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Informuje jedynie dane o dyskretnie przechwycone wyjątki.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informacyjny, zawierające nazwę metody, wpisz nazwę i komunikat o wyjątku.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
