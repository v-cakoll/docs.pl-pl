---
title: Informacje o zdarzeniach ETW środowiska uruchomieniowego
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
ms.openlocfilehash: 2927ed088ba6c9e46b9676d55d0046575e23cfb1
ms.sourcegitcommit: 5f236cd78cf09593c8945a7d753e0850e96a0b80
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/07/2020
ms.locfileid: "75715956"
---
# <a name="runtime-information-etw-events"></a>Informacje o zdarzeniach ETW środowiska uruchomieniowego
Te zdarzenia ETW rejestrują informacje o środowisku uruchomieniowym, w tym jednostki SKU, numer wersji, sposób aktywowania środowiska uruchomieniowego, parametry wiersza polecenia, z których uruchomiono, identyfikator GUID (jeśli dotyczy) i inne istotne informacje. Jeśli w ramach procesu jest wykonywanych wiele środowisk uruchomieniowych, informacje zawarte w tych zdarzeniach (ClrInstanceID) ułatwiają odróżnienie środowiska uruchomieniowego.  
  
 W poniższej tabeli przedstawiono dwa zdarzenia dotyczące informacji o środowisku uruchomieniowym. Zdarzenia mogą być zgłaszane pod dowolnym słowem kluczowym lub maską. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).  
  
|Zdarzenie|Identyfikator zdarzenia|Provider|Opis|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Uruchamiany po załadowaniu środowiska uruchomieniowego.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Wylicza załadowane środowiska uruchomieniowe.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|Win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
|Jednostka SKU|Win: UInt16|1 — środowisko CLR dla komputerów stacjonarnych.<br /><br /> 2 — CoreCLR.|  
|BclVersion — wersja główna|Win: UInt16|Główna wersja biblioteki mscorlib. dll.|  
|BclVersion — wersja pomocnicza|Win: UInt16|Numer wersji pomocniczej biblioteki mscorlib. dll.|  
|BclVersion — numer kompilacji|Win: UInt16|Numer kompilacji biblioteki mscorlib. dll.|  
|BclVersion — QFE|Win: UInt16|Numer wersji poprawki biblioteki mscorlib. dll.|  
|VMVersion — wersja główna|Win: UInt16|Wersja środowiska CLR. dll lub CoreCLR. dll, w zależności od jednostki SKU.|  
|VMVersion — wersja pomocnicza|Win: UInt16|Wersja pomocnicza środowiska CLR. dll lub CoreCLR. dll, w zależności od jednostki SKU.|  
|VMVersion — numer kompilacji|Win: UInt16|Liczba kompilacji dla środowiska CLR. dll lub CoreCLR. dll.|  
|VMVersion — QFE|Win: UInt16|Numer wersji poprawki środowiska CLR. dll lub CoreCLR. dll.|  
|StartupFlags|win: UInt32|Flagi uruchamiania zdefiniowane w bibliotece mscoree. h.|  
|Tryb uruchamiania|win: UInt8|plik wykonywalny zarządzany przez 0x01.<br /><br /> 0x02 — hostowane środowisko CLR.<br /><br /> międzyoperacyjność zarządzana przez C++ 0x04.<br /><br /> 0x08 — aktywowano COM.<br /><br /> 0x10 — inne.|  
|Wiersza polecenia|win: UnicodeString|Wartość inna niż null tylko wtedy, gdy Startupmode = 0x01.|  
|ComObjectGUID|win: identyfikator GUID|Wartość inna niż null tylko wtedy, gdy Startupmode = 0x08.|  
|RuntimeDLLPath|win: UnicodeString|Ścieżka do pliku CLR. dll, który został załadowany do procesu.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
