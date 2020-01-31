---
title: Wyliczenie CorDebugPlatform
ms.date: 03/30/2017
api_name:
- CorDebugPlatformEnum
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- CorDebugPlatformEnum
helpviewer_keywords:
- CorDebugPlatformEnum enumeration [.NET Framework debugging]
ms.assetid: c5444816-7378-4521-afd3-bf5e4b5303d5
topic_type:
- apiref
ms.openlocfilehash: 2ed32449c4a133e6e72ec44f9cb57f49de22164a
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76778241"
---
# <a name="cordebugplatform-enumeration"></a>Wyliczenie CorDebugPlatform
Zapewnia wartości platformy docelowej, które są używane przez metodę [ICorDebugDataTarget:: GetPlatform](icordebugdatatarget-getplatform-method.md) .  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
typedef enum CorDebugPlatform  
{  
    CORDB_PLATFORM_WINDOWS_X86,    // Windows on Intel x86  
    CORDB_PLATFORM_WINDOWS_AMD64,  // Windows x64 (AMD64, Intel EM64T)  
    CORDB_PLATFORM_WINDOWS_IA64,   // Windows on Intel IA-64  
    CORDB_PLATFORM_MAC_PPC,        // Macintosh OS on PowerPC  
    CORDB_PLATFORM_MAC_X86,        // Macintosh OS on Intel x86  
    CORDB_PLATFORM_WINDOWS_ARM,    // Windows on ARM  
    CORDB_PLATFORM_MAC_AMD64       // MacOS on Intel x64  
} CorDebugPlatform;  
```  
  
## <a name="members"></a>Elementy członkowskie  
  
|Element członkowski|Opis|  
|------------|-----------------|  
|CORDB_PLATFORM_WINDOWS_X86|Platforma docelowa to system Windows działający na sprzęcie Intel x86.|  
|CORDB_PLATFORM_WINDOWS_AMD64|Platforma docelowa to 64 bitowego systemu Windows działającego na sprzęcie AMD64 lub Intel EM64T.|  
|CORDB_PLATFORM_WINDOWS_IA64|Platforma docelowa to 32 bitowego systemu Windows działającego na sprzęcie Intel IA-64.|  
|CORDB_PLATFORM_MAC_PPC|Platforma docelowa to system operacyjny Macintosh działający na sprzęcie PowerPC.|  
|CORDB_PLATFORM_MAC_X86|Platforma docelowa to system operacyjny Macintosh działający na sprzęcie Intel x86.|  
|CORDB_PLATFORM_WINDOWS_ARM|Platforma docelowa to system operacyjny Macintosh działający na sprzęcie ARM systemu Windows.|  
|CORDB_PLATFORM_MAC_AMD64|Platforma docelowa to system operacyjny Macintosh działający na sprzęcie AMD64.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 `CORDB_PLATFORM_WINDOWS_ARM` i `CORDB_PLATFORM_MAC_AMD64` elementy członkowskie są dostępne w .NET Framework 4.5.2 i nowszych wersjach.  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](debugging-enumerations.md)
