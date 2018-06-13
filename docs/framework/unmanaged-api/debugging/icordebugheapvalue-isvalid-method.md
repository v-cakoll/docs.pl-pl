---
title: ICorDebugHeapValue::IsValid — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugHeapValue.IsValid
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugHeapValue::IsValid
helpviewer_keywords:
- IsValid method [.NET Framework debugging]
- ICorDebugHeapValue::IsValid method [.NET Framework debugging]
ms.assetid: 68e20e62-203d-46d8-bb91-8d3c61cfacc3
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 95532d6721467b482b1d79d611f8055b606bb4a5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33413511"
---
# <a name="icordebugheapvalueisvalid-method"></a>ICorDebugHeapValue::IsValid — Metoda
Pobiera wartość wskazującą, czy obiekt reprezentowany przez ten ICorDebugHeapValue jest nieprawidłowy.  
  
 Ta metoda jest przestarzała w programie .NET Framework w wersji 2.0.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT IsValid (  
    [out] BOOL    *pbValid  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pbValid`  
 [out] Wskaźnik na wartość logiczną, wskazującą, czy ta wartość na stercie jest prawidłowa.  
  
## <a name="remarks"></a>Uwagi  
 Wartość jest nieprawidłowa, jeśli ma zostać odzyskana przez moduł garbage collector.  
  
 Ta metoda jest przestarzała. W .NET Framework 2.0, wszystkie wartości są prawidłowe do [ICorDebugController::Continue](../../../../docs/framework/unmanaged-api/debugging/icordebugcontroller-continue-method.md) jest wywołana, w których wartości są nieważne.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]
