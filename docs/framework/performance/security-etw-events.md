---
title: Zabezpieczenia zdarzeń ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 11a19dce496423883e5fed62375c6db8ed5efdb1
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61949204"
---
# <a name="security-etw-events"></a>Zabezpieczenia zdarzeń ETW
<a name="top"></a> Zdarzenia zabezpieczeń są wywoływane podczas Weryfikacja silnej nazwy i weryfikacji Authenticode.  
  
 Ta kategoria obejmuje następujące zdarzenia:  
  
- [StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia](#strongnameverificationstart_v1_and_strongnameverificationstop_v1_events)  
  
- [AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia](#authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events)  
  
<a name="strongnameverificationstart_v1_and_strongnameverificationstop_v1_events"></a>   
## <a name="strongnameverificationstartv1-and-strongnameverificationstopv1-events"></a>StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1 zdarzenia  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe CLR ETW i poziomy](../../../docs/framework/performance/clr-etw-keywords-and-levels.md).)  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Początek Weryfikacja silnej nazwy.|  
|`StrongNameVerificationStop_V1`|182|Koniec Weryfikacja silnej nazwy.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|VerificationFlags|win: UInt32.|Flagi weryfikacji.|  
|ErrorCode|win: UInt32.|Kod błędu HResult.|  
|FullyQualifiedAssemblyName|win:UnicodeString|W pełni kwalifikowanej nazwy zestawu.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
 [Powrót do początku](#top)  
  
<a name="authenticodeverificationstart_v1_and_authenticodeverificationstop_v1_events"></a>   
## <a name="authenticodeverificationstartv1-and-authenticodeverificationstopv1-events"></a>AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1 zdarzenia  
 W poniższej tabeli przedstawiono — słowo kluczowe i poziomu.  
  
|Słowo kluczowe dla podnoszonego zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informational(4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywołane, gdy|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Uruchomienie weryfikacji Authenticode.|  
|`AuthenticodeVerificationStop_V1`|184|Koniec weryfikacji Authenticode.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|VerificationFlags|win: UInt32.|Flagi weryfikacji.|  
|ErrorCode|win: UInt32.|Kod błędu HResult.|  
|ModulePath|win:UnicodeString|Ścieżka modułu.|  
|ClrInstanceID|win: UInt16.|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](../../../docs/framework/performance/clr-etw-events.md)
