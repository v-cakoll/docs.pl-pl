---
title: Zabezpieczenia zdarzeń ETW
ms.date: 03/30/2017
helpviewer_keywords:
- security events [.NET Framework]
- ETW, security events (CLR)
ms.assetid: 0ed69f73-5c01-4514-bd63-979c6e38d41d
author: mairaw
ms.author: mairaw
ms.openlocfilehash: b1dad042595608a805f978673858acaa5c01130f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 11/12/2019
ms.locfileid: "73974880"
---
# <a name="security-etw-events"></a>Zabezpieczenia zdarzeń ETW

Zdarzenia zabezpieczeń są wywoływane podczas weryfikacji silnej nazwy i weryfikacji kodu Authenticode.  

## <a name="strongnameverificationstart_v1-and-strongnameverificationstop_v1-events"></a>Zdarzenia StrongNameVerificationStart_V1 i StrongNameVerificationStop_V1  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom. (Aby uzyskać więcej informacji, zobacz [słowa kluczowe i poziomy ETW CLR](clr-etw-keywords-and-levels.md)).  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`StrongNameVerificationStart_V1`|181|Rozpoczęcie weryfikacji silnej nazwy.|  
|`StrongNameVerificationStop_V1`|182|Koniec weryfikacji silnej nazwy.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|VerificationFlags|win: UInt32|Flagi weryfikacji.|  
|ErrorCode|win: UInt32|Kod błędu HResult.|  
|FullyQualifiedAssemblyName|win: UnicodeString|W pełni kwalifikowana nazwa zestawu.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  

## <a name="authenticodeverificationstart_v1-and-authenticodeverificationstop_v1-events"></a>Zdarzenia AuthenticodeVerificationStart_V1 i AuthenticodeVerificationStop_V1  
 W poniższej tabeli przedstawiono słowo kluczowe i poziom.  
  
|Słowo kluczowe do podniesienia zdarzenia|Poziom|  
|-----------------------------------|-----------|  
|`SecurityKeyword` (0x400)|Informacyjny (4)|  
  
 W poniższej tabeli przedstawiono informacje o zdarzeniu.  
  
|Zdarzenie|Identyfikator zdarzenia|Wywoływane, gdy|  
|-----------|--------------|-----------------|  
|`AuthenticodeVerificationStart_V1`|183|Rozpoczęcie weryfikacji Authenticode.|  
|`AuthenticodeVerificationStop_V1`|184|Koniec weryfikacji Authenticode.|  
  
 W poniższej tabeli przedstawiono dane zdarzenia.  
  
|Nazwa pola|Typ danych|Opis|  
|----------------|---------------|-----------------|  
|VerificationFlags|win: UInt32|Flagi weryfikacji.|  
|ErrorCode|win: UInt32|Kod błędu HResult.|  
|ModulePath|win: UnicodeString|Ścieżka modułu.|  
|ClrInstanceID|win: UInt16|Unikatowy identyfikator wystąpienia CLR lub CoreCLR.|  
  
## <a name="see-also"></a>Zobacz także

- [Zdarzenia CLR ETW](clr-etw-events.md)
