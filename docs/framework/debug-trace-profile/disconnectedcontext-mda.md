---
title: disconnectedContext MDA
ms.date: 03/30/2017
helpviewer_keywords:
- DisconnectedContext MDA
- MDAs (managed debugging assistants), disconnected context
- dead context
- transitioning disconnected apartment or context
- context disconnections
- managed debugging assistants (MDAs), disconnected context
ms.assetid: 1887d31d-7006-4491-93b3-68fd5b05f71d
ms.openlocfilehash: 3d04e304a6b30fe6fd4deeda5a97007f11ee7b13
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216549"
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext MDA
Asystent debugowania zarządzanego `disconnectedContext` (MDA) jest uaktywniany, gdy środowisko CLR próbuje przejść do odłączonego apartamentu lub kontekstu podczas obsługi żądania dotyczącego obiektu COM.  
  
## <a name="symptoms"></a>Objawy  
 Wywołania wywoływanej [otoki środowiska uruchomieniowego](../../standard/native-interop/runtime-callable-wrapper.md) (RCW) są dostarczane do źródłowego składnika COM w bieżącym elemencie Apartment lub Context, a nie na tym, w którym istnieją. Może to spowodować uszkodzenie lub utratę danych, jeśli składnik COM nie jest wielowątkowy, tak jak w przypadku składników jednowątkowego apartamentu (STA). Alternatywnie, jeśli OTOKa jest sama serwerem proxy, wywołanie może spowodować wygenerowanie <xref:System.Runtime.InteropServices.COMException> z wartością HRESULT RPC_E_WRONG_THREAD.  
  
## <a name="cause"></a>Przyczyna  
 Obiekt OLE Apartment lub kontekst został zamknięty, gdy środowisko CLR podejmie próbę przejścia do niego. Jest to najczęściej spowodowane tym, że STA apartamentach jest zamykany zanim wszystkie składniki COM będące własnością elementu Apartment zostały całkowicie wydane, może się to zdarzyć w wyniku jawnego wywołania kodu użytkownika na otoki RCW lub gdy samo środowisko CLR operuje na składniku COM. na przykład gdy środowisko CLR zwalnia składnik COM, gdy skojarzona Otoka RCW została odtworzona.  
  
## <a name="resolution"></a>Rozwiązanie  
 Aby uniknąć tego problemu, upewnij się, że wątek, który jest właścicielem STA, nie zakończy się przed zakończeniem działania aplikacji ze wszystkimi obiektami, które znajdują się w apartamentu. To samo dotyczy kontekstów; Upewnij się, że konteksty nie są zamykane, zanim aplikacja zostanie całkowicie zakończona wszystkimi składnikami COM znajdującymi się wewnątrz tego kontekstu.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Raport dotyczy tylko danych o rozłączonym kontekście.  
  
## <a name="output"></a>Dane wyjściowe  
 Raportuje plik cookie kontekstu odłączonego apartamentu lub kontekstu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
