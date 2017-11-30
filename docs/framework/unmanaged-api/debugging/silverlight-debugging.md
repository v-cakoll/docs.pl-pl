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
ms.openlocfilehash: bf39d2dd12207d594c7bf5bd5b249d82c3f15d3c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/21/2017
---
# <a name="silverlight-debugging"></a>Silverlight — debugowanie
W tematach w tej sekcji opisano środowisko i interfejsów, które udostępnia środowisko uruchomieniowe języka wspólnego (CLR) do obsługi debugowania aplikacji Silverlight, uruchomionych w systemie operacyjnym Windows lub na platformie Macintosh.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [Enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)  
 Udostępnia mechanizm dla wyliczania CLRs w procesie.  
  
 [Closeclrenumeration — funkcja](../../../../docs/framework/unmanaged-api/debugging/closeclrenumeration-function.md)  
 Zamyka prawidłowy zdarzeń kontynuować uruchamianie CLR znajduje się w tablicy dojść zwrócony przez [enumerateclrs — funkcja](../../../../docs/framework/unmanaged-api/debugging/enumerateclrs-function.md)i zwalnia pamięć dla tablic dojście i ciągu ścieżki.  
  
 [Createcoreclrdebugtarget — funkcja](../../../../docs/framework/unmanaged-api/debugging/createcoreclrdebugtarget-function.md)  
 Tworzy połączenie dla zdalnego miejsca docelowego, proces i środowiska uruchomieniowego wyliczenia.  
  
 [Createcordbobject — funkcja](../../../../docs/framework/unmanaged-api/debugging/createcordbobject-function.md)  
 Tworzy interfejs debugera dostarczająca funkcje dla sesji debugowania zarządzanego dla procesu zdalnego wystąpienia.  
  
 [Createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)  
 Tworzy ciąg wersji ze ścieżki CLR w procesie docelowym.  
  
 [Createdebugginginterfacefromversion — funkcja](../../../../docs/framework/unmanaged-api/debugging/createdebugginginterfacefromversion-function-for-silverlight.md)  
 Akceptuje zwrócony ciąg wersji aparatu CLR z [createversionstringfrommodule — funkcja](../../../../docs/framework/unmanaged-api/debugging/createversionstringfrommodule-function.md)funkcji i zwraca odpowiedniego interfejsu debugera.  
  
 [Coreclrdebugprocinfo — struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugprocinfo-structure.md)  
 Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.  
  
 [Coreclrdebugruntimeinfo — struktura](../../../../docs/framework/unmanaged-api/debugging/coreclrdebugruntimeinfo-structure.md)  
 Reprezentuje wystąpienie środowiska CLR, który jest ładowany w ramach procesu na komputerze zdalnym.  
  
 [Getstartupnotificationevent — funkcja](../../../../docs/framework/unmanaged-api/debugging/getstartupnotificationevent-function.md)  
 Tworzy lub otwiera obsługi zdarzenia, które są sygnalizowane po przez dowolnego środowisko uruchomieniowe języka wspólnego (CLR), który jest ładowany w procesie określonego obiektu docelowego.  
  
 [Icoreclrdebugtarget — interfejs](../../../../docs/framework/unmanaged-api/debugging/icoreclrdebugtarget-interface.md)  
 Tworzy połączenie dla zdalnego miejsca docelowego, proces i środowiska uruchomieniowego wyliczenia.  
  
 [Initdbgtransportmanager — funkcja](../../../../docs/framework/unmanaged-api/debugging/initdbgtransportmanager-function.md)  
 Inicjuje menedżera transportu do nawiązania połączenia zdalnego celu wyliczenie procesu i środowiska uruchomieniowego.  
  
 [Shutdowndbgtransportmanager — funkcja](../../../../docs/framework/unmanaged-api/debugging/shutdowndbgtransportmanager-function.md)  
 Zamknięcie menedżera transportu na połączenie komputera zdalnego docelowej.  
  
## <a name="see-also"></a>Zobacz też  
 [Klasy coclass debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-coclasses.md)  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)  
 [Statyczne funkcje globalne debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-global-static-functions.md)  
 [Debugowanie — wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)  
 [Struktury debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-structures.md)
