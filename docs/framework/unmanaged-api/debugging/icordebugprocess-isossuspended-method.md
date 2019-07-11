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
ms.openlocfilehash: 275f62c8211f71f067d310dd4b3af2ddb11e93d7
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67755461"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended — Metoda
Pobiera wartość wskazującą, czy określony wątek została zawieszona wyniku debugera zatrzymywania tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
