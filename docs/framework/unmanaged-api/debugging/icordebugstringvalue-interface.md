---
title: ICorDebugStringValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugStringValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugStringValue
helpviewer_keywords:
- ICorDebugStringValue interface [.NET Framework debugging]
ms.assetid: bf84d0af-53e1-4c04-bc5b-7e5f81ba2cc2
topic_type:
- apiref
ms.openlocfilehash: d1d3a5eb6e0b24b40a35c13a99465dd3c7032a91
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73138944"
---
# <a name="icordebugstringvalue-interface"></a>ICorDebugStringValue — Interfejs
Podklasa elementu ICorDebugHeapValue, która ma zastosowanie do wartości ciągu.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetLength, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getlength-method.md)|Pobiera liczbę znaków w ciągu, do których odwołuje się ten `ICorDebugStringValue`.|  
|[GetString, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugstringvalue-getstring-method.md)|Pobiera ciąg, do którego odwołuje się ten `ICorDebugStringValue`.|  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
