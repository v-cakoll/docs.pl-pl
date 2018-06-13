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
ms.openlocfilehash: 7d3b8f1e869e90fd3388cc0844e608b7ff40fc89
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33407095"
---
# <a name="cordebugplatform-enumeration"></a>Wyliczenie CorDebugPlatform
Udostępnia wartości platform docelowych, które są używane przez [ICorDebugDataTarget::GetPlatform](../../../../docs/framework/unmanaged-api/debugging/icordebugdatatarget-getplatform-method.md) metody.  
  
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
|CORDB_PLATFORM_WINDOWS_X86|Platforma docelowa jest sprzęt Intel x86 z systemem Windows.|  
|CORDB_PLATFORM_WINDOWS_AMD64|Platforma docelowa jest sprzęt AMD64 lub Intel EM64T z systemem Windows 64-bitowym.|  
|CORDB_PLATFORM_WINDOWS_IA64|Platforma docelowa jest sprzęt Intel IA-64 z systemem Windows 32-bitowych.|  
|CORDB_PLATFORM_MAC_PPC|Platforma docelowa jest systemu operacyjnego dla komputerów Macintosh PowerPC sprzętu.|  
|CORDB_PLATFORM_MAC_X86|Platforma docelowa jest Macintosh systemu operacyjnego na Intel x86 sprzętu.|  
|CORDB_PLATFORM_WINDOWS_ARM|Platforma docelowa jest Macintosh systemu operacyjnego na sprzęcie ARM systemu Windows.|  
|CORDB_PLATFORM_MAC_AMD64|Platforma docelowa jest Macintosh systemu operacyjnego na sprzęcie AMD64.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
 `CORDB_PLATFORM_WINDOWS_ARM` i `CORDB_PLATFORM_MAC_AMD64` elementy są dostępne w programie .NET Framework 4.5.2 i nowszych wersjach.  
  
## <a name="see-also"></a>Zobacz też  
 [Debugowanie, wyliczenia](../../../../docs/framework/unmanaged-api/debugging/debugging-enumerations.md)
