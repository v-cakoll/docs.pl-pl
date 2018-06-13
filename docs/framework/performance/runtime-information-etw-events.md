---
title: Informacje o zdarzeniach ETW środowiska uruchomieniowego
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 4244196a957c67a807cdb705f6d74ee2b41869d7
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33391605"
---
# <a name="runtime-information-etw-events"></a>Informacje o zdarzeniach ETW środowiska uruchomieniowego
Te zdarzenia ETW dziennika informacji na temat środowiska uruchomieniowego, jednostka SKU, numer wersji, sposób, w którym środowiska wykonawczego został aktywowany, w tym parametry wiersza polecenia, który został uruchomiony z identyfikatorem GUID (jeśli dotyczy) oraz inne istotne informacje. Jeśli wiele środowisk uruchomieniowych są wykonywane w ramach procesu, informacji dostarczonych przez te zdarzenia (ClrInstanceID) pomaga odróżnić środowisk uruchomieniowych.  
  
 W poniższej tabeli przedstawiono dwie informacje o zdarzeniach środowiska uruchomieniowego. Zdarzenia można uruchamiany w ramach żadnych — słowo kluczowe ani maski. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Zdarzenie|Identyfikator zdarzenia|Dostawcy|Opis|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Wywoływane, gdy jest ładowany w środowisku uruchomieniowym.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Wylicza środowiska uruchomieniowe, które zostały załadowane.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Windows: UInt16|Unikatowy identyfikator wystąpienia CLR lub środowisko CoreCLR.|  
|Jednostka SKU|Windows: UInt16|1 – desktop CLR.<br /><br /> 2 — środowisko CoreCLR.|  
|BclVersion — wersja główna|Windows: UInt16|Wersja główna mscorlib.dll.|  
|BclVersion — wersja pomocnicza|Windows: UInt16|Podrzędny numer wersji biblioteki mscorlib.dll.|  
|BclVersion — numer kompilacji|Windows: UInt16|Numer mscorlib.dll kompilacji.|  
|BclVersion — QFE|Windows: UInt16|Poprawka numer wersji biblioteki mscorlib.dll.|  
|VMVersion — wersja główna|Windows: UInt16|Wersja clr.dll lub coreclr.dll, w zależności od wersji.|  
|VMVersion — wersja pomocnicza|Windows: UInt16|Wersja pomocnicza clr.dll lub coreclr.dll, w zależności od wersji.|  
|VMVersion — numer kompilacji|Windows: UInt16|Numer clr.dll lub coreclr.dll kompilacji.|  
|VMVersion — QFE|Windows: UInt16|Numer wersji poprawki clr.dll lub coreclr.dll.|  
|StartupFlags|Windows: UInt32.|Zdefiniowany w mscoree.h flagi uruchamiania.|  
|StartupMode|Windows: UInt8|0x01 - zarządzanego pliku wykonywalnego.<br /><br /> 0x02 - hostowanej CLR.<br /><br /> 0x04 - C++ zarządzane interop.<br /><br /> 0x08 - COM została aktywowana.<br /><br /> 0x10 - innych.|  
|Wiersz polecenia|Windows: UnicodeString|Inne niż null tylko wtedy, gdy StartupMode = 0x01.|  
|ComObjectGUID|Windows: identyfikator GUID|Inne niż null tylko wtedy, gdy StartupMode = 0x08.|  
|RuntimeDLLPath|Windows: UnicodeString|Ścieżka do pliku dll CLR, który został załadowany do procesu.|  
  
## <a name="see-also"></a>Zobacz też  
 [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
