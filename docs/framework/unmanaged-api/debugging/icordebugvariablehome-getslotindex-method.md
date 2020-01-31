---
title: 'ICorDebugVariableHome:: GetSlotIndex, Metoda'
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHome.GetSlotIndex
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHome::GetSlotIndex
helpviewer_keywords:
- ICorDebugVariableHome::GetSlotIndex method [.NET Framework debugging]
- GetSlotIndex method, ICorDebugVariableHome interface [.NET Framework debugging]
ms.assetid: 966da50d-5665-4fff-bf7b-1c72bbadd9a4
topic_type:
- apiref
ms.openlocfilehash: 542bfa05c55ef224d1b9111f9af6c069e9e23542
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76790971"
---
# <a name="icordebugvariablehomegetslotindex-method"></a>ICorDebugVariableHome:: GetSlotIndex, Metoda
Pobiera zarządzany indeks szczeliny zmiennej lokalnej.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetSlotIndex(  
    [out] ULONG32 *pSlotIndex  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pSlotIndex`  
 określoną Wskaźnik do indeksu szczeliny zmiennej lokalnej.  
  
## <a name="return-value"></a>Wartość zwrócona  
 Metoda zwraca następujące wartości.  
  
|Wartość|Opis|  
|-----------|-----------------|  
|`S_OK`|Wywołanie metody zwróciło wartość indeksu szczeliny w `pSlotIndex`.|  
|`E_FAIL`|Bieżące wystąpienie [ICorDebugVariableHome](icordebugvariablehome-interface.md) reprezentuje argument funkcji.|  
  
## <a name="remarks"></a>Uwagi  
 Za pomocą indeksu miejsca można pobrać metadane dla tej zmiennej lokalnej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugVariableHome, interfejs](icordebugvariablehome-interface.md)
