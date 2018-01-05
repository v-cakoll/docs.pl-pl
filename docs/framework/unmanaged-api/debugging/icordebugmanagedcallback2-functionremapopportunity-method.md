---
title: "ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugManagedCallback2.FunctionRemapOpportunity
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugManagedCallback2::FunctionRemapOpportunity
helpviewer_keywords:
- FunctionRemapOpportunity method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapOpportunity method [.NET Framework debugging]
ms.assetid: 0d6471bc-ad9b-4b1d-a307-c10443918863
topic_type: apiref
caps.latest.revision: "14"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 208803acea65b24429938dc646e7abe70949b237
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugmanagedcallback2functionremapopportunity-method"></a>ICorDebugManagedCallback2::FunctionRemapOpportunity — Metoda
Powiadamia debuger osiągnięcie w wykonanie kodu punktu sekwencji w starszej wersji funkcji edytowany.  
  
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
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domeny aplikacji zawierający funkcję edytowany.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątku podczas ponownego mapowania punktu przerwania.  
  
 `pOldFunction`  
 [in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje wersji funkcji, która jest obecnie uruchomiony w wątku.  
  
 `pNewFunction`  
 [in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje najnowszą wersję funkcji.  
  
 `oldILOffset`  
 [in] Język pośredni (MSIL) firmy Microsoft przesunięcie wskaźnika instrukcji w starej wersji funkcji.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne daje debuger możliwość ponownie zamapować wskaźnik instrukcji, aby jego właściwe miejsce w nowej wersji określona funkcja wywołując [ICorDebugILFrame2::RemapFunction](../../../../docs/framework/unmanaged-api/debugging/icordebugilframe2-remapfunction-method.md) metody. Jeśli debuger nie wywołuje `RemapFunction` przed wywołaniem [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) metody środowiska uruchomieniowego będzie kontynuować jego wykonywanie poprzedni kod i uruchomią innego `FunctionRemapOpportunity` wywołanie zwrotne z następnego punktu sekwencji.  
  
 To wywołanie zwrotne zostanie wywołany dla każdej ramki, w której jest wykonywany starszą wersję danej funkcji, dopóki debuger zwraca wartość S_OK.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugManagedCallback2, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)  
 [ICorDebugManagedCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
