---
title: ICorDebugProcess::IsTransitionStub — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsTransitionStub
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsTransitionStub
helpviewer_keywords:
- ICorDebugProcess::IsTransitionStub method [.NET Framework debugging]
- IsTransitionStub method [.NET Framework debugging]
ms.assetid: f7653317-7e48-4163-be03-f50f1a4b0f70
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 18084cb69d2c620fc892cc05e5a561e8fda3bc1c
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57488191"
---
# <a name="icordebugprocessistransitionstub-method"></a>ICorDebugProcess::IsTransitionStub — Metoda
Pobiera wartość wskazującą, czy adres znajduje się wewnątrz odcinek, który spowoduje przejście do kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsTransitionStub(  
    [in]  CORDB_ADDRESS address,  
    [out] BOOL *pbTransitionStub);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 [in] A `CORDB_ADDRESS` wartość, która określa danego adresu.  
  
 `pbTransitionStub`  
 [out] Wskaźnik na wartość logiczną, która jest `true` Jeśli określony adres znajduje się wewnątrz odcinek, który spowoduje przejście do zarządzanego kodu; w przeciwnym razie *`pbTransitionStub` jest `false`.  
  
## <a name="remarks"></a>Uwagi  
 `IsTransitionStub` Metoda może służyć przez kod niezarządzany przechodzenia krok po kroku w podjęciu decyzji, przywrócenie kontroli przechodzenia krok po kroku do stepper zarządzanych.  
  
 Można również wycinków przejścia tożsamości, analizując informacje zawarte w przenośny plik wykonywalny (PE).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
