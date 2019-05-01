---
title: ICorDebugProcess::IsOSSuspended — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugProcess.IsOSSuspended
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugProcess::IsOSSuspended
helpviewer_keywords:
- IsOSSuspended method [.NET Framework debugging]
- ICorDebugProcess::IsOSSuspended method [.NET Framework debugging]
ms.assetid: 83406cb2-5797-4402-872d-89c9516aefec
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 039dc0d9befb038e643abc4e2524c133234f460b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61775573"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended — Metoda
Pobiera wartość wskazującą, czy określony wątek została zawieszona wyniku debugera zatrzymywania tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
## <a name="parameters"></a>Parametry  
 `threadID`  
 [in] Identyfikator wątku jest zagrożona.  
  
 `pbSuspended`  
 [out] Wskaźnik na wartość logiczną, która jest `true` , jeśli określony wątek został wstrzymany; w przeciwnym razie *`pbSuspended` jest `false`.  
  
## <a name="remarks"></a>Uwagi  
 Podczas określonego wątku została zawieszona wyniku debugera, ten proces trwa zatrzymywanie, określony wątek Win32 zawiesić licznik jest zwiększany o jeden. Debuger interfejsu użytkownika (UI) mogą chcieć wykonać te informacje pod uwagę wyświetlaniem systemu operacyjnego (OS) wstrzymywanie łącznej liczby wątków do użytkownika.  
  
 `IsOSSuspended` Metoda ma sens tylko w kontekście debugowanie niezarządzane. Podczas debugowania zarządzanego wątki są wspólne wstrzymane, a nie zawieszony przez system operacyjny.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
