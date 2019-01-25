---
title: ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 86736f885e40e553195cf2a5f84575a5384e6b60
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54564711"
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda
Powiadamia debugera, że wykonywanie kodu osiągnęła punktu sekwencji w starszej wersji przeprowadzono edycję funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FunctionRemapOpportunity (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pOldFunction,  
    [in] ICorDebugFunction    *pNewFunction,  
    [in] ULONG32              oldILOffset  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą przeprowadzono edycję funkcji.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek napotkano punkt przerwania ponowne mapowanie.  
  
 `pOldFunction`  
 [in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje wersji funkcji, która jest aktualnie uruchomiona w wątku.  
  
 `pNewFunction`  
 [in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje najnowszą wersję funkcji.  
  
 `oldILOffset`  
 [in] Przesunięcie Microsoft intermediate language (MSIL) wskaźnik instrukcji w starej wersji funkcji.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne zapewnia debugera można ponownie zamapować wskaźnik instrukcji do jego właściwe miejsce w nowej wersji określonej funkcji przez wywołanie metody [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metody. Jeśli debuger nie mogą wywoływać `RemapFunction` przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody, środowisko uruchomieniowe będzie w dalszym ciągu wykonują poprzedni kod i zostanie uruchomiony inny `FunctionRemapOpportunity` wywołania zwrotnego w następnym punkcie sekwencji.  
  
 To wywołanie zwrotne zostanie wywołany dla każdej ramki, który jest wykonywany na starszą wersję danej funkcji, dopóki debuger nie zwróci S_OK.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
