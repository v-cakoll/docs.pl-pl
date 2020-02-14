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
ms.openlocfilehash: 4ccb03c9a8a473c10f15b00e64810b04f21504c9
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77217525"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom MDA
Asystent debugowania zarządzanego `exceptionSwallowedOnCallFromCOM` (MDA) jest uaktywniany, gdy wyjątek jest zgłaszany z kodu środowiska uruchomieniowego języka wspólnego (CLR) wywoływanego z modelu COM za pomocą metody, która nie ma niezarządzanego typu zwracanego HRESULT.  
  
## <a name="symptoms"></a>Objawy  
 Wywołanie zarządzanego składnika z modelu COM zwraca wartość FALSE lub 0. Alternatywnie, jeśli metoda ma typ zwracany void, może nie być wskazywać, że wyjątek został zgłoszony podczas wykonywania metody. W takim przypadku wyjątek zostanie przechwycony w trybie dyskretnym, a wykonywanie zwróci do obiektu wywołującego COM.  
  
## <a name="cause"></a>Przyczyna  
 Zgłoszono wyjątek, ale nie ma prawidłowego sposobu na jego raportowanie.  
  
## <a name="resolution"></a>Rozwiązanie  
 Tylko informacyjne, niekoniecznie wskazujące usterkę.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Raport dotyczy tylko danych o przechwyconych dyskretnie wyjątkach.  
  
## <a name="output"></a>Dane wyjściowe  
 Komunikat informacyjny zawierający nazwę metody, nazwę typu i komunikat o wyjątku.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <exceptionSwallowedOnCallFromCom />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
