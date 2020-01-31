---
title: Silverlight — debugowanie
ms.date: 03/30/2017
helpviewer_keywords:
- debugging API [Silverlight]
- Silverlight, debugging
ms.assetid: 5e903e04-17d0-4014-ac9a-a43330ec8b1c
ms.openlocfilehash: 91f311818b615ea8f166bb3362ec52d39fcd0297
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790324"
---
# <a name="silverlight-debugging"></a>Silverlight — debugowanie
Tematy w tej sekcji opisują środowisko i interfejsy, które zapewnia środowisko uruchomieniowe języka wspólnego (CLR) do obsługi debugowania aplikacji opartych na technologii Silverlight, które są uruchomione w systemie operacyjnym Windows lub na platformie Macintosh.  
  
## <a name="in-this-section"></a>W tej sekcji  
 [EnumerateCLRs, funkcja](enumerateclrs-function.md)  
 Zapewnia mechanizm wyliczania CLRs w procesie.  
  
 [CloseCLREnumeration, funkcja](closeclrenumeration-function.md)  
 Zamyka wszystkie prawidłowe zdarzenia Kontynuuj środowiska CLR znajdujące się w tablicy dojść zwracanych przez [funkcję EnumerateCLRs —](enumerateclrs-function.md)i zwalnia pamięć dla tablic uchwytów i ścieżek ciągów.  
  
 [CreateCoreClrDebugTarget, funkcja](createcoreclrdebugtarget-function.md)  
 Tworzy połączenie ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.  
  
 [CreateCordbObject, funkcja](createcordbobject-function.md)  
 Tworzy interfejs debugera, który zapewnia funkcję tworzenia wystąpienia zarządzanej sesji debugowania w procesie zdalnym.  
  
 [CreateVersionStringFromModule, funkcja](createversionstringfrommodule-function.md)  
 Tworzy ciąg wersji ze ścieżki CLR w procesie docelowym.  
  
 [CreateDebuggingInterfaceFromVersion, funkcja](createdebugginginterfacefromversion-function-for-silverlight.md)  
 Akceptuje ciąg wersji środowiska CLR zwrócony z funkcji [funkcji CreateVersionStringFromModule —](createversionstringfrommodule-function.md)i zwraca odpowiedni interfejs debugera.  
  
 [CoreClrDebugProcInfo, struktura](coreclrdebugprocinfo-structure.md)  
 Reprezentuje proces, który jest uruchomiony na komputerze zdalnym.  
  
 [CoreClrDebugRuntimeInfo, struktura](coreclrdebugruntimeinfo-structure.md)  
 Reprezentuje wystąpienie CLR, które jest ładowane w procesie na maszynie zdalnej.  
  
 [GetStartupNotificationEvent, funkcja](getstartupnotificationevent-function.md)  
 Tworzy lub otwiera dojście zdarzenia, które będzie sygnalizowane przez środowisko uruchomieniowe języka wspólnego (CLR) ładowane w określonym procesie docelowym.  
  
 [ICoreClrDebugTarget, interfejs](icoreclrdebugtarget-interface.md)  
 Tworzy połączenie ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.  
  
 [InitDbgTransportManager, funkcja](initdbgtransportmanager-function.md)  
 Inicjuje menedżera transportu, aby połączyć się ze zdalnym elementem docelowym na potrzeby wyliczenia procesu i środowiska uruchomieniowego.  
  
 [ShutdownDbgTransportManager, funkcja](shutdowndbgtransportmanager-function.md)  
 Zamyka menedżera transportu dla połączenia ze zdalnym komputerem docelowym.  
  
## <a name="see-also"></a>Zobacz także

- [Klasy coclass debugowania](debugging-coclasses.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
- [Debugowanie statycznych funkcji globalnych](debugging-global-static-functions.md)
- [Debugowanie, wyliczenia](debugging-enumerations.md)
- [Struktury debugowania](debugging-structures.md)
