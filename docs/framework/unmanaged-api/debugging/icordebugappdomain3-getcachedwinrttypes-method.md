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
ms.openlocfilehash: e5fd1730bbe5b6f2905691dce41a7f503227534a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/12/2020
ms.locfileid: "79179071"
---
# <a name="icordebugappdomain3getcachedwinrttypes-method"></a>ICorDebugAppDomain3::GetCachedWinRTTypes — Metoda
Pobiera wyliczenia dla wszystkich typów środowiska wykonawczego systemu Windows w pamięci podręcznej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetCachedWinRTTypes (
    [out] ICorDebugGuidToTypeEnum **ppGuidToTypeEnum)  
;  
```  
  
## <a name="parameters"></a>Parametry  
 `ppGuidToTypeEnum`  
 [na zewnątrz] Wskaźnik do obiektu interfejsu [ICorDebugGuidToTypeEnum,](icordebugguidtotypeenum-interface.md) który może wyliczyć zarządzane reprezentacje typów środowiska wykonawczego systemu Windows aktualnie ładowanych w domenie aplikacji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Środowisko wykonawcze systemu Windows  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET Framework:**[!INCLUDE[net_current_v45plus](../../../../includes/net-current-v45plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [ICorDebugAppDomain3, interfejs](icordebugappdomain3-interface.md)
