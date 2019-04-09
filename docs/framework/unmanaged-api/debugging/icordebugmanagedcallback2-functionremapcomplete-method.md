---
title: ICorDebugManagedCallback2::FunctionRemapComplete — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugManagedCallback2.FunctionRemapComplete
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugManagedCallback2::FunctionRemapComplete
helpviewer_keywords:
- FunctionRemapComplete method [.NET Framework debugging]
- ICorDebugManagedCallback2::FunctionRemapComplete method [.NET Framework debugging]
ms.assetid: 5396c4c3-4ec3-4e3a-a38d-d65b21f0a2fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 515d434e8d8f1c99cf5052ef9a2f1e098f6021b2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59140559"
---
# <a name="icordebugmanagedcallback2functionremapcomplete-method"></a>ICorDebugManagedCallback2::FunctionRemapComplete — Metoda
Powiadamia debugera, że wykonywanie kodu zostało przełączone do nowej wersji przeprowadzono edycję funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT FunctionRemapComplete (  
    [in] ICorDebugAppDomain   *pAppDomain,  
    [in] ICorDebugThread      *pThread,  
    [in] ICorDebugFunction    *pFunction  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [in] Wskaźnik do obiektu ICorDebugAppDomain, który reprezentuje domenę aplikacji, zawierającą przeprowadzono edycję funkcji.  
  
 `pThread`  
 [in] Wskaźnik do obiektu ICorDebugThread, który reprezentuje wątek napotkano punkt przerwania ponowne mapowanie.  
  
 `pFunction`  
 [in] Wskaźnik do obiektu ICorDebugFunction, który reprezentuje wersja funkcji aktualnie uruchomiona w wątku.  
  
## <a name="remarks"></a>Uwagi  
 To wywołanie zwrotne umożliwia debugera do odtworzenia steppery, wszelkie istniejące wcześniej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugManagedCallback2 — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback2-interface.md)
- [ICorDebugManagedCallback — Interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmanagedcallback-interface.md)
