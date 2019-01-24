---
title: Silverlight — debugowanie
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 414526d498b39e894c6bd3530a446f8c06f46378
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54572750"
---
# <a name="silverlight-debugging"></a>Silverlight — debugowanie
Tematy w tej sekcji opisano środowisko i interfejsów udostępnianych przez środowisko uruchomieniowe języka wspólnego (CLR) do obsługi debugowania aplikacji opartych na technologii Silverlight, uruchomionych w systemie operacyjnym Windows lub na platformie dla komputerów Macintosh.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [EnumerateCLRs, funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Udostępnia mechanizm wyliczania CLRs w procesie.  
  
 [CloseCLREnumeration, funkcja](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Zamyka wszystkie prawidłowe zdarzenia uruchamiania nadal CLR, znajduje się w tablicy, uchwyt zwracany przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic ścieżka dojścia i parametry.  
  
 [CreateCoreClrDebugTarget, funkcja](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Tworzy połączenie do zdalnego obiektu docelowego dla wyliczenia procesu i środowiska uruchomieniowego.  
  
 [CreateCordbObject, funkcja](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Tworzy interfejs debugera, który oferuje funkcję podczas tworzenia wystąpienia zarządzanego sesji debugowania zdalnego procesu.  
  
 [CreateVersionStringFromModule, funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Tworzy ciąg wersji ze ścieżki CLR w procesie docelowym.  
  
 [CreateDebuggingInterfaceFromVersion, funkcja](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Akceptuje ciąg wersji środowiska CLR zwróciło [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)funkcji i zwraca odpowiedniego interfejsu debugera.  
  
 [CoreClrDebugProcInfo, struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.  
  
 [CoreClrDebugRuntimeInfo, struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Reprezentuje wystąpienie CLR, który jest załadowany do procesu na komputerze zdalnym.  
  
 [GetStartupNotificationEvent, funkcja](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Tworzy lub zostanie otwarte dojście zdarzenia, które są sygnalizowane po przez dowolnego środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w procesie docelowym określonym.  
  
 [ICoreClrDebugTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Tworzy połączenie do zdalnego obiektu docelowego dla wyliczenia procesu i środowiska uruchomieniowego.  
  
 [InitDbgTransportManager, funkcja](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicjuje menedżera transportu nawiązać zdalnego obiektu docelowego dla wyliczenia procesu i środowiska uruchomieniowego.  
  
 [ShutdownDbgTransportManager, funkcja](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Zamknie menedżera transportu dla połączenia do maszyny zdalnej docelowego.  
  
## <a name="see-also"></a>Zobacz także
- [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
- [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)
- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
- [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
