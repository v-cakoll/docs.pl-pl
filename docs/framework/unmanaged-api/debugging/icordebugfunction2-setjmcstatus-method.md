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
ms.openlocfilehash: 7da12554ba1db9a467aa03c01bfb3b584125b129
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/12/2020
ms.locfileid: "83213195"
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus — Metoda
Oznacza funkcję reprezentowaną przez ten ICorDebugFunction2 do Tylko mój kod wykonywania kroków.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 podczas Ustaw `true` , aby oznaczyć funkcję jako kod użytkownika; w przeciwnym razie ustaw wartość `false` .  
  
## <a name="return-values"></a>Wartości zwrócone  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|Funkcja została pomyślnie oznaczona.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|Nie można oznaczyć funkcji jako kodu użytkownika, ponieważ nie można jej debugować.|  
  
## <a name="remarks"></a>Uwagi  
 Tylko mój kod stepper pominie kod niebędący użytkownikiem. Kod użytkownika musi być podzbiorem kodu możliwością debugowania.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
