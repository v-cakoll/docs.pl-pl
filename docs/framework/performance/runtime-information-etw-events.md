---
title: Informacje o zdarzeniach ETW środowiska uruchomieniowego
description: Zobacz zdarzenia ETW informacji o środowisku uruchomieniowym, które rejestrują jednostkę SKU, numer wersji, sposób aktywowania środowiska uruchomieniowego (w tym parametry wiersza polecenia), identyfikator GUID i inne.
ms.date: 03/30/2017
helpviewer_keywords:
- runtime information events [.NET Framework]
- ETW, runtime information events
ms.assetid: 68b4edbc-7f3b-45f6-ab75-4fd066d6af9a
ms.openlocfilehash: 385519229bdb76841cdf592d95e96d2288ec5e1a
ms.sourcegitcommit: cf5a800a33de64d0aad6d115ffcc935f32375164
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/20/2020
ms.locfileid: "86474231"
---
# <a name="runtime-information-etw-events"></a>Informacje o zdarzeniach ETW środowiska uruchomieniowego
Te zdarzenia ETW rejestrują informacje o środowisku uruchomieniowym, w tym jednostki SKU, numer wersji, sposób aktywowania środowiska uruchomieniowego, parametry wiersza polecenia, z których uruchomiono, identyfikator GUID (jeśli dotyczy) i inne istotne informacje. Jeśli w ramach procesu jest wykonywanych wiele środowisk uruchomieniowych, informacje zawarte w tych zdarzeniach (ClrInstanceID) ułatwiają odróżnienie środowiska uruchomieniowego.  
  
 W poniższej tabeli przedstawiono dwa zdarzenia dotyczące informacji o środowisku uruchomieniowym. Zdarzenia mogą być zgłaszane pod dowolnym słowem kluczowym lub maską. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).  
  
|Zdarzenie|Identyfikator zdarzenia|Dostawca|Opis|  
|-----------|--------------|--------------|-----------------|  
|`RuntimeInformationEvent`|187|CLRRuntime|Uruchamiany po załadowaniu środowiska uruchomieniowego.|  
|`RuntimeInformationDCStart`|187|CLRRundown|Wylicza załadowane środowiska uruchomieniowe.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
|SKU|win: UInt16|1 — środowisko CLR dla komputerów stacjonarnych.<br /><br /> 2 — CoreCLR.|  
|BclVersion — wersja główna|win: UInt16|Wersja główna mscorlib.dll.|  
|BclVersion — wersja pomocnicza|win: UInt16|Numer wersji pomocniczej mscorlib.dll.|  
|BclVersion — numer kompilacji|win: UInt16|Numer kompilacji mscorlib.dll.|  
|BclVersion — QFE|win: UInt16|Numer wersji poprawki mscorlib.dll.|  
|VMVersion — wersja główna|win: UInt16|Wersja clr.dll lub coreclr.dll, w zależności od jednostki SKU.|  
|VMVersion — wersja pomocnicza|win: UInt16|Wersja pomocnicza clr.dll lub coreclr.dll, w zależności od jednostki SKU.|  
|VMVersion — numer kompilacji|win: UInt16|Liczba kompilacji clr.dll lub coreclr.dll.|  
|VMVersion — QFE|win: UInt16|Numer wersji poprawki clr.dll lub coreclr.dll.|  
|StartupFlags|win: UInt32|Flagi uruchamiania zdefiniowane w bibliotece mscoree. h.|  
|Tryb uruchamiania|win: UInt8|plik wykonywalny zarządzany przez 0x01.<br /><br /> 0x02 — hostowane środowisko CLR.<br /><br /> międzyoperacyjna zarządzana 0x04-C++.<br /><br /> 0x08 — aktywowano COM.<br /><br /> 0x10 — inne.|  
|CommandLine|win: UnicodeString|Wartość inna niż null tylko wtedy, gdy Startupmode = 0x01.|  
|ComObjectGUID|win: identyfikator GUID|Wartość inna niż null tylko wtedy, gdy Startupmode = 0x08.|  
|RuntimeDLLPath|win: UnicodeString|Ścieżka do pliku CLR. dll, który został załadowany do procesu.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia ETW CLR](clr-etw-events.md)
