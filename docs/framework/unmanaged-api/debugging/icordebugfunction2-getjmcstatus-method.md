---
title: ICorDebugFunction2::GetJMCStatus — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugFunction2.GetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugFunction2::GetJMCStatus
helpviewer_keywords:
- ICorDebugFunction2::GetJMCStatus method [.NET Framework debugging]
- GetJMCStatus method [.NET Framework debugging]
ms.assetid: 840a71ed-bf5a-4f5e-8ed6-762222b34493
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: acf0ba3938568524479e12b93ae8cebbcf52f909
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33411732"
---
# <a name="icordebugfunction2getjmcstatus-method"></a>ICorDebugFunction2::GetJMCStatus — Metoda
Pobiera wartość wskazującą, czy funkcja reprezentowanego przez ten obiekt ICorDebugFunction2 jest oznaczony jako kodu użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbIsJustMyCode`  
 [out] Wskaźnik do wartość logiczna, która jest `true`, jeśli ta funkcja jest oznaczony jako kod użytkownika; w przeciwnym razie wartość jest `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja reprezentowany przez to `ICorDebugFunction2` nie można debugować `pbIsJustMyCode` zawsze będzie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
