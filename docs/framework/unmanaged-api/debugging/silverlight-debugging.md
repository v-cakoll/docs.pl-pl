---
title: "Silverlight — debugowanie"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
caps.latest.revision: "4"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f6869e58ca47b7b55a5b988e0f6ae4a224f0f35a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="silverlight-debugging"></a>Silverlight — debugowanie
W tematach w tej sekcji opisano środowisko i interfejsów, które udostępnia środowisko uruchomieniowe języka wspólnego (CLR) do obsługi debugowania aplikacji Silverlight, uruchomionych w systemie operacyjnym Windows lub na platformie Macintosh.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [EnumerateCLRs, funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Udostępnia mechanizm dla wyliczania CLRs w procesie.  
  
 [CloseCLREnumeration, funkcja](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Zamyka prawidłowy zdarzeń kontynuować uruchamianie CLR znajduje się w tablicy dojść zwrócony przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic dojście i ciągu ścieżki.  
  
 [CreateCoreClrDebugTarget, funkcja](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Tworzy połączenie dla zdalnego miejsca docelowego, proces i środowiska uruchomieniowego wyliczenia.  
  
 [CreateCordbObject, funkcja](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Tworzy interfejs debugera dostarczająca funkcje dla sesji debugowania zarządzanego dla procesu zdalnego wystąpienia.  
  
 [CreateVersionStringFromModule, funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Tworzy ciąg wersji ze ścieżki CLR w procesie docelowym.  
  
 [CreateDebuggingInterfaceFromVersion, funkcja](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Akceptuje zwrócony ciąg wersji aparatu CLR z [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)funkcji i zwraca odpowiedniego interfejsu debugera.  
  
 [CoreClrDebugProcInfo, struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.  
  
 [CoreClrDebugRuntimeInfo, struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Reprezentuje wystąpienie środowiska CLR, który jest ładowany w ramach procesu na komputerze zdalnym.  
  
 [GetStartupNotificationEvent, funkcja](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Tworzy lub otwiera obsługi zdarzenia, które są sygnalizowane po przez dowolnego środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w procesie określonego obiektu docelowego.  
  
 [ICoreClrDebugTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Tworzy połączenie dla zdalnego miejsca docelowego, proces i środowiska uruchomieniowego wyliczenia.  
  
 [InitDbgTransportManager, funkcja](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicjuje menedżera transportu do nawiązania połączenia zdalnego celu wyliczenie procesu i środowiska uruchomieniowego.  
  
 [ShutdownDbgTransportManager, funkcja](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Zamknięcie menedżera transportu na połączenie komputera zdalnego docelowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Debugowanie statycznych funkcji globalnych](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
