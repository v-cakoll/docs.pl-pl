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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 03b6f1b29157889d0e84e5dddc94d5e3ae27efce
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61989641"
---
# <a name="cordebugplatform-enumeration"></a>Wyliczenie CorDebugPlatform
Udostępnia wartości platformy docelowe, które są używane przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.  
  
## <a name="syntax"></a>Składnia  
  
```  
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
|CORDB_PLATFORM_WINDOWS_X86|Platforma docelowa jest sprzęt firmy Intel x86 z systemem Windows.|  
|CORDB_PLATFORM_WINDOWS_AMD64|Platforma docelowa jest Windows 64-bitowym systemem AMD64 lub obsługą technologii Intel EM64T sprzętu.|  
|CORDB_PLATFORM_WINDOWS_IA64|Platforma docelowa jest 32-bitowa Windows uruchomionej na sprzęcie Intel IA-64.|  
|CORDB_PLATFORM_MAC_PPC|Platforma docelowa jest uruchomionej na sprzęcie PowerPC systemu operacyjnego dla komputerów Macintosh.|  
|CORDB_PLATFORM_MAC_X86|Platforma docelowa jest uruchomionego na sprzęt firmy Intel x86 systemu operacyjnego dla komputerów Macintosh.|  
|CORDB_PLATFORM_WINDOWS_ARM|Platforma docelowa jest uruchomionego na ARM Windows sprzętu systemu operacyjnego dla komputerów Macintosh.|  
|CORDB_PLATFORM_MAC_AMD64|Platformą docelową jest system operacyjny dla komputerów Macintosh uruchomionej na sprzęcie AMD64.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 `CORDB_PLATFORM_WINDOWS_ARM` i `CORDB_PLATFORM_MAC_AMD64` składowe są dostępne w programie .NET Framework 4.5.2 i nowszych wersjach.  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
