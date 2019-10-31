---
title: Silverlight — debugowanie
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: b7af03197a43976c47b7ddc30346d622e6b97207
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73139135"
---
# <a name="silverlight-debugging"></a>Silverlight — debugowanie
Tematy w tej sekcji opisują środowisko i interfejsy, które zapewnia środowisko uruchomieniowe języka wspólnego (CLR) do obsługi debugowania aplikacji opartych na technologii Silverlight, które są uruchomione w systemie operacyjnym Windows lub na platformie Macintosh.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [EnumerateCLRs, funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Zapewnia mechanizm wyliczania CLRs w procesie.  
  
 [CloseCLREnumeration, funkcja](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Zamyka wszystkie prawidłowe zdarzenia Kontynuuj środowiska CLR znajdujące się w tablicy dojść zwracanych przez [funkcję EnumerateCLRs —](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic uchwytów i ścieżek ciągów.  
  
 [CreateCoreClrDebugTarget, funkcja](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Tworzy połączenie ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.  
  
 [CreateCordbObject, funkcja](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Tworzy interfejs debugera, który zapewnia funkcję tworzenia wystąpienia zarządzanej sesji debugowania w procesie zdalnym.  
  
 [CreateVersionStringFromModule, funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Tworzy ciąg wersji ze ścieżki CLR w procesie docelowym.  
  
 [CreateDebuggingInterfaceFromVersion, funkcja](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Akceptuje ciąg wersji środowiska CLR zwrócony z funkcji [funkcji CreateVersionStringFromModule —](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)i zwraca odpowiedni interfejs debugera.  
  
 [CoreClrDebugProcInfo, struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.  
  
 [CoreClrDebugRuntimeInfo, struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Reprezentuje wystąpienie CLR, które jest ładowane w procesie na maszynie zdalnej.  
  
 [GetStartupNotificationEvent, funkcja](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Tworzy lub otwiera dojście zdarzenia, które będzie sygnalizowane przez środowisko uruchomieniowe języka wspólnego (CLR) ładowane w określonym procesie docelowym.  
  
 [ICoreClrDebugTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Tworzy połączenie ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.  
  
 [InitDbgTransportManager, funkcja](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicjuje menedżera transportu, aby połączyć się ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.  
  
 [ShutdownDbgTransportManager, funkcja](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Zamyka menedżera transportu dla połączenia ze zdalnym komputerem docelowym.  
  
## <a name="see-also"></a>Zobacz także

- [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
