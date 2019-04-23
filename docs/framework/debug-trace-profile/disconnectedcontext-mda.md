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
author: mairaw
ms.author: mairaw
ms.openlocfilehash: cb42c04df6e02ff43421b7af6bf2d51b53aa3e69
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181983"
---
# <a name="disconnectedcontext-mda"></a>disconnectedContext MDA
`disconnectedContext` Zarządzanego Asystenta debugowania (MDA) jest aktywowany, gdy środowisko CLR podejmuje próbę przejścia do odłączonego apartamentu lub kontekstu podczas obsługi żądanie dotyczące obiektu COM.  
  
## <a name="symptoms"></a>Symptomy  
 Wywołania na [wywoływana otoka środowiska uruchomieniowego](../../../docs/framework/interop/runtime-callable-wrapper.md) (RCW) są dostarczane do podstawowego składnika modelu COM w bieżącym apartamentu lub kontekstu, zamiast jednego, w którym istnieją. Może to spowodować uszkodzenie i lub utraty danych, jeśli składnik COM nie jest wielowątkowych, tak jak w przypadku składniki apartamentem jednowątkowym (przedziale STA). Alternatywnie, jeśli RCW jest serwer proxy, wywołanie może spowodować zgłaszanie z <xref:System.Runtime.InteropServices.COMException> z HRESULT RPC_E_WRONG_THREAD.  
  
## <a name="cause"></a>Przyczyna  
 OLE apartamentu lub kontekstu została zamknięta podczas prób środowiska CLR, do którego nastąpi przejście do niej. Jest to najczęściej spowodowane apartamentach STA, który jest zamykana przed udostępnieniem wszystkich składników COM należące do typu apartment zostały całkowicie, to może wystąpić w wyniku jawnym wywołaniem z kodu użytkownika na RCW lub w przypadku, gdy środowisko CLR, sama jest manipulowanie składnika COM , na przykład po środowisko CLR udostępnia składnika COM po skojarzone RCW bezużyteczne.  
  
## <a name="resolution"></a>Rozwiązanie  
 Aby uniknąć tego problemu, sprawdź, czy wątek, który jest właścicielem STA skończył się, zanim wszystkie obiekty, które znajdują się w apartamentu aplikacji zostało zakończone. To samo dotyczy kontekstów; Upewnij się, że kontekstach nie są zamykane, zanim aplikacja jest całkowicie zakończyło się z składników modelu COM, znajdujące się w ramach kontekstu.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR. Informuje jedynie dane o odłączony kontekst.  
  
## <a name="output"></a>Dane wyjściowe  
 Raporty kontekstu plik cookie odłączonego apartamentu lub kontekstu.  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <disconnectedContext />  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
