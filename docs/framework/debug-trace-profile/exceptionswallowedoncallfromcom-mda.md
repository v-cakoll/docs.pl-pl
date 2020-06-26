---
title: exceptionSwallowedOnCallFromCom MDA
description: Zapoznaj się z asystentem debugowania zarządzanego przez exceptionSwallowedOnCallFromCOM w programie .NET. To zdarzenie MDA występuje, jeśli wystąpił wyjątek, ale nie istnieje dobry sposób na zgłoszenie go.
ms.date: 03/30/2017
helpviewer_keywords:
- messages, informational
- informational messages
- managed debugging assistants (MDAs), exceptions
- exception handling, managed debugging assistants
- MDAs (managed debugging assistants), exceptions
- ExceptionSwallowedOnCallFromCOM MDA
ms.assetid: 55d6ab12-f251-4aab-aa64-aacbe9d9f974
ms.openlocfilehash: 434f06cf953147d5c245e625db997bed6dbef700
ms.sourcegitcommit: a2c8b19e813a52b91facbb5d7e3c062c7188b457
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/26/2020
ms.locfileid: "85415956"
---
# <a name="exceptionswallowedoncallfromcom-mda"></a>exceptionSwallowedOnCallFromCom MDA
`exceptionSwallowedOnCallFromCOM`Asystent debugowania zarządzanego (MDA) jest uaktywniany, gdy wyjątek jest zgłaszany z kodu środowiska uruchomieniowego języka wspólnego (CLR) wywoływanego z modelu COM za pomocą metody, która nie ma niezarządzanego zwracanego typu HRESULT.  
  
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
- [Organizowanie międzyoperacyjne](../interop/interop-marshaling.md)
