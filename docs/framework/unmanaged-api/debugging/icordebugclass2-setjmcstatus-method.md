---
title: ICorDebugClass2::SetJMCStatus — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugClass2.SetJMCStatus
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugClass2::SetJMCStatus
helpviewer_keywords:
- ICorDebugClass2::SetJMCStatus method [.NET Framework debugging]
- SetJMCStatus method, ICorDebugClass2 interface [.NET Framework debugging]
ms.assetid: 077e6c7f-f857-480c-bebb-76ee1de4e8fc
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 23f248625753c15a4798ea69a1eb3b377b79f95d
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 07/10/2019
ms.locfileid: "67747754"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus — Metoda
Ustawia wartość wskazującą, czy metoda jest zdefiniowany przez użytkownika kod dla każdej metody klasy.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 [in] Ustaw `true` do wskazania, że metoda jest zdefiniowana przez użytkownika kod; w przeciwnym wypadku ustaw `false`.  
  
## <a name="remarks"></a>Uwagi  
 Stepper (JMC) just my kodu pominie kod zdefiniowane użytkownika. Zdefiniowane przez użytkownika kod musi być podzestawem kod do debugowania.  
  
 `SetJMCStatus` Zwraca wartość HRESULT S_FALSE, jeśli nie można ustawić wartości dla dowolnej metody nawet, jeśli pomyślnie ustawia wartość dla wszystkich innych metod.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
