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
ms.openlocfilehash: 1f557cc370d5c6121b0ad9a4528bd75dcb70a93c
ms.sourcegitcommit: 9c54866bcbdc49dbb981dd55be9bbd0443837aa2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 02/14/2020
ms.locfileid: "77216289"
---
# <a name="invalidoverlappedtopinvoke-mda"></a>invalidOverlappedToPinvoke MDA
Asystent debugowania zarządzanego `invalidOverlappedToPinvoke` (MDA) jest uaktywniany, gdy nakładający się wskaźnik, który nie został utworzony na stercie wyrzucania elementów bezużytecznych, jest przesyłany do określonych funkcji Win32.  
  
> [!NOTE]
> Domyślnie to zdarzenie MDA jest uaktywniane tylko wtedy, gdy wywołanie wywoływana przez platformę jest zdefiniowane w kodzie, a debuger raportuje stan JustMyCode każdej z tych metod. Debuger, który nie rozpoznaje JustMyCode (na przykład MDbg. exe bez rozszerzeń), nie aktywuje tego MDA. To zdarzenie MDA można włączyć dla tych debugerów przy użyciu pliku konfiguracji i jawnie wyraźnych `justMyCode="false"` w pliku MDA. config `(<invalidOverlappedToPinvoke enable="true" justMyCode="false"/>`).  
  
## <a name="symptoms"></a>Objawy  
 Awarie stosu lub niewyjaśnione uszkodzenia sterty.  
  
## <a name="cause"></a>Przyczyna  
 Nakładający się wskaźnik, który nie został utworzony na stercie wyrzucania elementów bezużytecznych, jest przesyłany do określonych funkcji systemu operacyjnego.  
  
 W poniższej tabeli przedstawiono funkcje, które są śledzone przez to zdarzenie MDA.  
  
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
  
 Prawdopodobieństwo uszkodzenia sterty jest wysokie dla tego warunku, ponieważ <xref:System.AppDomain> wywoływanie może zwolnić. Jeśli <xref:System.AppDomain> zwalnia, kod aplikacji zwolni pamięć dla nakładającego się wskaźnika, powodując uszkodzenie po zakończeniu operacji lub kod przecieka pamięć, co spowoduje problemy później.  
  
## <a name="resolution"></a>Rozwiązanie  
 Użyj obiektu <xref:System.Threading.Overlapped>, wywołując metodę <xref:System.Threading.Overlapped.Pack%2A>, aby uzyskać <xref:System.Threading.NativeOverlapped> strukturę, która może zostać przeniesiona do funkcji. Jeśli <xref:System.AppDomain> zwalnia, środowisko CLR czeka na zakończenie operacji asynchronicznej przed zwolnieniem wskaźnika.  
  
## <a name="effect-on-the-runtime"></a>Wpływ na środowisko uruchomieniowe  
 To zdarzenie MDA nie ma wpływu na środowisko CLR.  
  
## <a name="output"></a>Dane wyjściowe  
 Poniżej znajduje się przykład danych wyjściowych z tego MDA.  
  
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

- <xref:System.Runtime.InteropServices.MarshalAsAttribute>
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](diagnosing-errors-with-managed-debugging-assistants.md)
- [Marshaling międzyoperacyjny](../interop/interop-marshaling.md)
