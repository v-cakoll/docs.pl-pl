---
title: ICorDebugThread::GetDebugState — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugThread.GetDebugState
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugThread::GetDebugState
helpviewer_keywords:
- GetDebugState method [.NET Framework debugging]
- ICorDebugThread::GetDebugState method [.NET Framework debugging]
ms.assetid: 9be27b0c-1d99-4722-b0d4-40cf6753ce5c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 68df19120f2e0b45e73f9d5e137afc8a5e7ac513
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61987158"
---
# <a name="icordebugthreadgetdebugstate-method"></a>ICorDebugThread::GetDebugState — Metoda
Pobiera bieżący stan debugowania tego obiektu ICorDebugThread.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDebugState (  
    [out] CorDebugThreadState   *pState  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pState`  
 [out] Wskaźnik do bitowa kombinacja wartości wyliczenia cordebugthreadstate —, który opisuje bieżący stan debugowania tego wątku.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli proces jest obecnie zatrzymana, `pState` reprezentuje stan debugowania, który istniałby dla tego wątku, gdyby proces będzie kontynuowane nie rzeczywiste bieżący stan tego wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
