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
ms.openlocfilehash: 4bdb2035906b9383342201017b58d1d0050113b5
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59084560"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke MDA
`invalidOverlappedToPinvoke` Zarządzanego Asystenta debugowania (MDA) jest uaktywniany podczas nakładającego się wskaźnika, który nie został utworzony na stercie wyrzucania elementów bezużytecznych jest przekazywana do określonych funkcji systemu Win32.  
  
> [!NOTE]
>  Domyślnie to zdarzenie MDA jest aktywowane tylko wtedy, gdy wywołanie platformy jest zdefiniowane w kodzie i usuwania błędów raportuje stan JustMyCode każdej metody. Debuger, który nie rozpoznaje JustMyCode (np. MDbg.exe bez rozszerzeń) nie aktywuje to zdarzenie MDA. Ten MDA może być włączony dla tych debugerów przy użyciu pliku konfiguracji i wyraźnych ustawień `justMyCode="false"` w. plik mda.config `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).  
  
## <a name="symptoms"></a>Symptomy  
 Awarie lub niewytłumaczalne uszkodzenia sterty.  
  
## <a name="cause"></a>Przyczyna  
 Niewłaściwy nachodzący wskaźnik, który nie został utworzony na stercie wyrzucania elementów bezużytecznych jest przekazywany do określonych funkcji systemu operacyjnego.  
  
 W poniższej tabeli przedstawiono funkcje, że te zdarzenia mda.  
  
|Moduł|Funkcja|  
|------------|--------------|  
|HttpApi.dll|`HttpReceiveHttpRequest`|  
|IpHlpApi.dll|`NotifyAddrChange`|  
|kernel32.dll|`ReadFile`|  
|kernel32.dll|`ReadFileEx`|  
|kernel32.dll|`WriteFile`|  
|kernel32.dll|`WriteFileEx`|  
|kernel32.dll|`ReadDirectoryChangesW`|  
|kernel32.dll|`PostQueuedCompletionStatus`|  
|MSWSock.dll|`ConnectEx`|  
|WS2_32.dll|`WSASend`|  
|WS2_32.dll|`WSASendTo`|  
|WS2_32.dll|`WSARecv`|  
|WS2_32.dll|`WSARecvFrom`|  
|MQRT.dll|`MQReceiveMessage`|  
  
 Potencjał uszkodzenie sterty jest wysoki jak na ten stan, ponieważ <xref:System.AppDomain> podejmowanie wywołania może zwolnić. Jeśli <xref:System.AppDomain> zwalnia, kod aplikacji spowoduje zwolnienie pamięci dla nakładającego się wskaźnika, powodując uszkodzenie po zakończeniu operacji lub kod wycieku pamięci, powodując trudności później.  
  
## <a name="resolution"></a>Rozwiązanie  
 Użyj <xref:System.Threading.Overlapped> obiektu, wywołanie <xref:System.Threading.Overlapped.Pack%2A> metodę, aby uzyskać <xref:System.Threading.NativeOverlapped> struktury, który może być przekazywany do funkcji. Jeśli <xref:System.AppDomain> zwalnia, CLR czeka, aż zakończeniu operacji asynchronicznej przed zwolnieniem wskaźnika.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie miało wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Oto przykład danych wyjściowych z tego MDA.  
  
 `An overlapped pointer (0x00ea3430) that was not allocated on the GC heap was passed via Pinvoke to the Win32 function 'WriteFile' in module 'KERNEL32.DLL'. If the AppDomain is shut down, this can cause heap corruption when the async I/O completes. The best solution is to pass a NativeOverlapped structure retrieved from a call to System.Threading.Overlapped.Pack(). If the AppDomain exits, the CLR will keep this structure alive and pinned until the I/O completes.`  
  
## <a name="configuration"></a>Konfiguracja  
  
```xml  
<mdaConfig>  
  <assistants>  
    <invalidOverlappedToPinvoke/>  
  </assistants>  
</mdaConfig>  
```  
  
## <a name="see-also"></a>Zobacz także

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
- [Organizowanie międzyoperacyjne](../../../docs/framework/interop/interop-marshaling.md)
