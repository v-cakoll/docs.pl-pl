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
ms.openlocfilehash: d234e01e3d47a64b9a001591ee2b61074eea8afb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403397"
---
# <a name="icordebugclass2setjmcstatus-method"></a>ICorDebugClass2::SetJMCStatus — Metoda
Ustawia wartość wskazującą, czy metoda jest zdefiniowane przez użytkownika kod dla każdej metody klasy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetJMCStatus (  
    [in] BOOL   bIsJustMyCode  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `bIsJustMyCode`  
 [in] Ustaw `true` aby wskazać, że metoda jest zdefiniowane przez użytkownika kod; w przeciwnym razie wartość `false`.  
  
## <a name="remarks"></a>Uwagi  
 Stepper (JMC) just my kodu pominie zdefiniowane użytkownika kodu. Kod użytkownika muszą być podzbiorem możliwością debugowania kodu.  
  
 `SetJMCStatus` Zwraca wartość HRESULT S_FALSE, jeśli nie można ustawić wartości dla dowolnej metody, nawet jeśli pomyślnie ustawia wartość dla wszystkich innych metod.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]
