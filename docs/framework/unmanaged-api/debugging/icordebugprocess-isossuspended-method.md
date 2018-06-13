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
ms.openlocfilehash: 2b65a621541f2b4a800f6b3708a6b257374c5866
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33419822"
---
# <a name="icordebugprocessisossuspended-method"></a>ICorDebugProcess::IsOSSuspended — Metoda
Pobiera wartość wskazującą, czy określony wątek został wstrzymany wyniku debugera zatrzymywanie tego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsOSSuspended(  
    [in]  DWORD threadID,  
    [out] BOOL  *pbSuspended);  
```  
  
#### <a name="parameters"></a>Parametry  
 `threadID`  
 [in] Identyfikator wątku jest zagrożona.  
  
 `pbSuspended`  
 [out] Wskaźnik do wartość logiczna, która jest `true` Jeśli określony wątek został zawieszony; w przeciwnym razie *`pbSuspended` jest `false`.  
  
## <a name="remarks"></a>Uwagi  
 Gdy określony wątek zostało zawieszone wyniku debugera zatrzymywanie tego procesu, określony wątek Win32 zawiesić liczba jest zwiększany o jeden. Debuger interfejsu użytkownika (UI) może być konieczne pobierać te informacje pod uwagę, jeśli zawiera system operacyjny (OS) zawiesić liczba wątków dla użytkownika.  
  
 `IsOSSuspended` Metoda ma sens tylko w kontekście debugowanie niezarządzane. Podczas debugowania zarządzanego wątki są wspólnie wstrzymaną zamiast zawieszone systemu operacyjnego.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
