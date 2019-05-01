---
title: Informacje o zdarzeniach ETW środowiska uruchomieniowego
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
author: mairaw
ms.author: mairaw
ms.openlocfilehash: af27ddaa69d34976929f40055bc2cc668f877e87
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949217"
---
# <a name="runtime-information-etw-events"></a>Informacje o zdarzeniach ETW środowiska uruchomieniowego
Te zdarzenia ETW rejestrować informacje o środowisku uruchomieniowym jednostki SKU i numer wersji, w taki sposób, w którym został aktywowany środowiska uruchomieniowego, w tym parametry wiersza polecenia, który został uruchomiony przy użyciu identyfikatora GUID (jeśli dotyczy) oraz inne istotne informacje. Jeśli wielu modułów wykonawczych są wykonywane w ramach procesu, informacji dostarczonych przez te zdarzenia (ClrInstanceID) pomaga odróżnić środowiska uruchomieniowego.  
  
 W poniższej tabeli przedstawiono dwa środowiska uruchomieniowego informacje o zdarzeniach. Zdarzenia można wygenerowane w ramach żadnego — słowo kluczowe lub maski. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Zdarzenie|Identyfikator zdarzenia|Dostawca|Opis|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Wywoływane, gdy jest ładowany przez środowisko uruchomieniowe.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Wylicza środowisk wykonawczych, które są ładowane.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
|Jednostka SKU|win: UInt16.|1 — desktop CLR.<br /><br /> 2 – CoreCLR.|  
|BclVersion — wersja główna|win: UInt16.|Wersja główna mscorlib.dll.|  
|BclVersion — wersja pomocnicza|win: UInt16.|Pomocniczy numer wersji biblioteki mscorlib.dll.|  
|BclVersion — numer kompilacji|win: UInt16.|Numer mscorlib.dll kompilacji.|  
|BclVersion — QFE|win: UInt16.|Numer wersji poprawki zestawu.|  
|VMVersion — wersja główna|win: UInt16.|Wersja clr.dll lub coreclr.dll, w zależności od jednostki SKU.|  
|VMVersion — wersja pomocnicza|win: UInt16.|Wersja pomocnicza clr.dll lub coreclr.dll, w zależności od jednostki SKU.|  
|VMVersion — numer kompilacji|win: UInt16.|Numer clr.dll lub coreclr.dll kompilacji.|  
|VMVersion — QFE|win: UInt16.|Numer wersji poprawki clr.dll lub coreclr.dll.|  
|StartupFlags|win: UInt32.|Zdefiniowane w mscoree.h flagi uruchamiania.|  
|StartupMode|win:UInt8|0x01 - zarządzanego pliku wykonywalnego.<br /><br /> 0x02 — hostowanego środowiska CLR.<br /><br /> 0x04 - C++ zarządzane międzyoperacyjności.<br /><br /> 0x08 - aktywowane COM.<br /><br /> 0x10 - innych.|  
|Wiersz polecenia|win:UnicodeString|Inną niż null tylko wtedy, gdy StartupMode = 0x01.|  
|ComObjectGUID|win: identyfikator GUID|Inną niż null tylko wtedy, gdy StartupMode = 0x08.|  
|RuntimeDLLPath|win:UnicodeString|Ścieżka do pliku .dll CLR, który został załadowany do procesu.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
