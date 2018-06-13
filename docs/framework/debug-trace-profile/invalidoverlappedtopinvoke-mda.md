---
title: invalidOverlappedToPinvoke MDA
ms.date: 03/30/2017
helpviewer_keywords:
- overlapped pointers
- managed debugging assistants (MDAs), overlapped pointers
- invalid overlapped pointer to platform invoke
- InvalidOverlappedToPinvoke MDA
- MDAs (managed debugging assistants), overlapped pointers
- pointers, overlapped
ms.assetid: 28876047-58bd-4fed-9452-c7da346d67c0
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 7240692e35c97f3efbc33ca27a0221da1d250149
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33386860"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke MDA
`invalidOverlappedToPinvoke` Zarządzany Asystent debugowania (MDA) jest aktywowany, gdy nachodzący wskaźnik, który nie został utworzony na stercie kolekcji pamięci jest przekazywany do określonych funkcji Win32.  
  
> [!NOTE]
>  Domyślnie to zdarzenie MDA jest aktywna, tylko jeśli wywołanie platformy połączenia jest zdefiniowana w kodzie i debuger informuje o stanie JustMyCode każdej metody. Debuger, który nie rozpoznaje JustMyCode (na przykład MDbg.exe bez rozszerzeń) nie zostanie aktywowany to zdarzenie MDA. MDA ten można włączyć dla tych debugery przy użyciu pliku konfiguracji i jawnie settting `justMyCode="false"` w. plik mda.config `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).  
  
## <a name="symptoms"></a>Symptomy  
 Awarie lub uszkodzenie stosu unexplainable.  
  
## <a name="cause"></a>Przyczyna  
 Nachodzący wskaźnik, który nie został utworzony na stercie kolekcji pamięci są przekazywane do funkcji określonego systemu operacyjnego.  
  
 W poniższej tabeli przedstawiono funkcje, że to zdarzenie MDA śledzi.  
  
|Moduł|Funkcja|  
|------------|--------------|  
|HttpApi.dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|Kernel32.dll|`ReadFile`|  
|Kernel32.dll|`ReadFileEx`|  
|Kernel32.dll|`WriteFile`|  
|Kernel32.dll|`WriteFileEx`|  
|Kernel32.dll|`ReadDirectoryChangesW`|  
|Kernel32.dll|`PostQueuedCompletionStatus`|  
|MSWSock.dll|`ConnectEx`|  
|WS2_32.dll|`WSASend`|  
|WS2_32.dll|`WSASendTo`|  
|WS2_32.dll|`WSARecv`|  
|WS2_32.dll|`WSARecvFrom`|  
|MQRT.dll|`MQReceiveMessage`|  
  
 Jest duże ryzyko uszkodzenia sterty dla tego warunku, ponieważ <xref:System.AppDomain> wywołanie może zwolnić wprowadzania. Jeśli <xref:System.AppDomain> zwalnia, kod aplikacji albo spowoduje zwolnienie pamięci dla wskaźnika, przyczyną uszkodzenia po zakończeniu operacji lub kod będzie wyciek pamięci, co powoduje trudności później.  
  
## <a name="resolution"></a>Rozwiązanie  
 Użyj <xref:System.Threading.Overlapped> obiektów i wywoływania <xref:System.Threading.Overlapped.Pack%2A> metodę, aby pobrać <xref:System.Threading.NativeOverlapped> struktury, które mogą zostać przekazane do funkcji. Jeśli <xref:System.AppDomain> zwalnia, CLR czeka przed zakończeniem operacji asynchronicznych przed zwalnianie wskaźnika.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie miała wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Oto przykład danych wyjściowych z to zdarzenie MDA.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz też  
 <xref:System.Runtime.InteropServices.MarshalAsAttribute>  
 [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)  
 [Marshaling międzyoperacyjny](../../../docs/framework/interop/interop-marshaling.md)
