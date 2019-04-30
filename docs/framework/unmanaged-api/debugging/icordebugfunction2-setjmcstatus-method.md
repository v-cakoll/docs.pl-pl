---
title: ICorDebugFunction2::SetJMCStatus — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 49ced1b4be888c7550c3927d1b319ab2f0bef086
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61763779"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus — Metoda
Funkcja reprezentowany przez ten icordebugfunction2 — tylko mój kod oznacza przechodzenie krok po kroku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 [in] Ustaw `true` aby oznaczyć tę funkcję, co kod użytkownika; w przeciwnym wypadku ustaw `false`.  
  
## <a name="return-values"></a>Wartości zwrócone  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|Funkcja został pomyślnie oznaczony.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|Funkcja nie można oznaczyć jako kod użytkownika, ponieważ nie można debugować.|  
  
## <a name="remarks"></a>Uwagi  
 Stepper tylko mój kod pozwoli na pominięcie kodu innych użytkowników. Kod użytkownika musi być podzestawem kod do debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
