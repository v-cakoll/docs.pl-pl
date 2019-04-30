---
title: ICorDebugMDA::GetOSThreadId — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugMDA.GetOSThreadId
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugMDA::GetOSThreadId
helpviewer_keywords:
- ICorDebugMDA::GetOSThreadId method [.NET Framework debugging]
- GetOSThreadId method [.NET Framework debugging]
ms.assetid: 7ca7c364-ade4-4219-b434-9f6ae2359be6
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 51d29fed3d53611daa0042251ce09638399f7ed5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61723150"
---
# <a name="icordebugmdagetosthreadid-method"></a>ICorDebugMDA::GetOSThreadId — Metoda
Pobiera identyfikator wątku systemu operacyjnego (OS), na którym zarządzanego Asystenta debugowania (MDA) jest reprezentowane przez [icordebugmda —](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md) jest wykonywany.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetOSThreadId (  
    [out] DWORD    *pOsTid  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pOsTid`  
 [out] Wskaźnik do identyfikator wątku systemu operacyjnego.  
  
## <a name="remarks"></a>Uwagi  
 Wątek systemu operacyjnego umożliwia zamiast ICorDebugThread w sytuacjach, w których MDA jest uruchamiany na wątku natywnej lub z wątków zarządzanych, które jeszcze nie wprowadzono kodu zarządzanego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugMDA, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugmda-interface.md)
- [Diagnozowanie błędów przy użyciu asystentów zarządzanego debugowania](../../../../docs/framework/debug-trace-profile/diagnosing-errors-with-managed-debugging-assistants.md)
