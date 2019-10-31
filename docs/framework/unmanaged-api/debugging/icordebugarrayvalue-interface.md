---
title: ICorDebugArrayValue — Interfejs
ms.date: 03/30/2017
api_name:
- ICorDebugArrayValue
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugArrayValue interface
helpviewer_keywords:
- ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type:
- apiref
ms.openlocfilehash: e41bb5ca0fdd999692395239304f50a6f745a4f3
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73088271"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue — Interfejs

Podklasa elementu ICorDebugHeapValue, która reprezentuje tablicę jednowymiarową lub wielowymiarową.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBaseIndicies, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Pobiera podstawowy indeks każdego wymiaru w tablicy.|  
|[GetCount, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Pobiera łączną liczbę elementów w tablicy.|  
|[GetDimensions, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Pobiera Wymiary tablicy.|  
|[GetElement, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Pobiera wartość reprezentującą dany element w tablicy.|  
|[GetElementAtPosition, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Pobiera element w podanym miejscu, traktując tablicę jako tablicę jednowymiarową o wartości zero.|  
|[GetElementType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Pobiera prosty typ elementów w tablicy.|  
|[GetRank, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Pobiera liczbę wymiarów w tablicy.|  
|[HasBaseIndicies, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Określa, czy tablica ma indeksy podstawowe.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugArrayValue` obsługuje tablice jednowymiarowe i wielowymiarowe.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
