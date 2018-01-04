---
title: "ICorDebugFunction2::SetJMCStatus — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugFunction2.SetJMCStatus
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugFunction2::SetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugFunction2 interface [.NET Framework debugging]
ms.assetid: 22c27b01-2869-4214-b840-5921f7c874fc
topic_type: apiref
caps.latest.revision: "11"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 315e036481f0454bf68b2da9e496c441ee843ba2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icordebugfunction2setjmcstatus-method"></a>ICorDebugFunction2::SetJMCStatus — Metoda
Funkcja reprezentowany przez ten ICorDebugFunction2 dla tylko mój kod oznacza wykonywanie krok po kroku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 [in] Ustaw `true` do oznaczenia funkcji jako kodu użytkownika; w przeciwnym razie wartość `false`.  
  
## <a name="return-values"></a>Wartości zwrócone  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|Funkcja została pomyślnie oznaczona.|  
|`CORDBG_E_FUNCTION_NOT_DEBUGGABLE`|Funkcja nie można oznaczyć jako kodu użytkownika, ponieważ nie można debugować.|  
  
## <a name="remarks"></a>Uwagi  
 Stepper tylko mój kod pozwoli na pominięcie kodu innych użytkowników. Kod użytkownika muszą być podzbiorem możliwością debugowania kodu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
