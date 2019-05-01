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
ms.openlocfilehash: d23a0a489cfe13201b7798920feb3528db3b0709
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61988666"
---
# <a name="icordebugfunction2getjmcstatus-method"></a>ICorDebugFunction2::GetJMCStatus — Metoda
Pobiera wartość wskazującą, czy funkcja, która jest reprezentowany przez ten obiekt icordebugfunction2 — jest oznaczony jako kod użytkownika.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetJMCStatus (  
    [out] BOOL   *pbIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pbIsJustMyCode`  
 [out] Wskaźnik na wartość logiczną, która jest `true`, jeśli ta funkcja jest oznaczona jako kod użytkownika; w przeciwnym razie wartość to `false`.  
  
## <a name="remarks"></a>Uwagi  
 Jeśli funkcja reprezentowany przez ten `ICorDebugFunction2` nie można debugować, `pbIsJustMyCode` zawsze będzie `false`.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
