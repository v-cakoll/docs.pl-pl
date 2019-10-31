---
title: ICorDebugObjectValue::GetClass — Metoda
ms.date: 03/30/2017
api_name:
- ICorDebugObjectValue.GetClass
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugObjectValue::GetClass
helpviewer_keywords:
- ICorDebugObjectValue::GetClass method [.NET Framework debugging]
- GetClass method, ICorDebugObjectValue interface [.NET Framework debugging]
ms.assetid: 5be25292-8357-445f-a09b-f997c0de761c
topic_type:
- apiref
ms.openlocfilehash: 4719f155957f04471d4ad2b8d71bec9c0f0d30c0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73096091"
---
# <a name="icordebugobjectvaluegetclass-method"></a>ICorDebugObjectValue::GetClass — Metoda
Pobiera klasę tej wartości obiektu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetClass (  
    [out] ICorDebugClass     **ppClass  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `ppClass`  
 określoną Wskaźnik do adresu obiektu "ICorDebugClass", który reprezentuje klasę wartości obiektu reprezentowanej przez ten obiekt "ICorDebugObjectValue".  
  
## <a name="remarks"></a>Uwagi  
 Metody `GetClass` i [ICorDebugValue:: GetType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue-gettype-method.md) każda zwracają informacje o typie wartości; są one zastępowane przez ogólne [ICorDebugValue2:: GetExactType](../../../../docs/framework/unmanaged-api/debugging/icordebugvalue2-getexacttype-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
