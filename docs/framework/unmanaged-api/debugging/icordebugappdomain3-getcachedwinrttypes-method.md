---
title: ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugAppDomain3.GetCachedWinRTTypes
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes
helpviewer_keywords:
- ICorDebugAppDomain3::GetCachedWinRTTypes method [.NET Framework debugging]
- GetCachedWinRTTypes method, ICorDebugAppDomain3 interface [.NET Framework debugging]
ms.assetid: 9afd0e04-a403-41e2-9528-a6dcbcdcbd4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: c7e2685d17f3dd32db295f926fc19121d29e1752
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/12/2019
ms.locfileid: "67025911"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda
Pobiera moduł wyliczający dla wszystkich typów środowiska wykonawczego Windows pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetCachedWinRTTypes (   
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a>Parametry  
 `ppGuidToTypeEnum`  
 [out] Wskaźnik do [icordebugguidtotypeenum —](../../../../docs/framework/unmanaged-api/debugging/icordebugguidtotypeenum-interface.md) obiektu interfejsu, który można wyliczyć zarządzanych reprezentacja typów środowiska wykonawczego Windows obecnie załadowane w domenie aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Środowisko wykonawcze systemu Windows  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugAppDomain3, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugappdomain3-interface.md)
