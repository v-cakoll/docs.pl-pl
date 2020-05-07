---
title: ICorDebugArrayValue, interfejs
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
ms.openlocfilehash: bd1e86b83c43af20604416f158ab9e74f399821b
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/07/2020
ms.locfileid: "82894970"
---
# <a name="icordebugarrayvalue-interface"></a>ICorDebugArrayValue, interfejs

Podklasa elementu ICorDebugHeapValue, która reprezentuje tablicę jednowymiarową lub wielowymiarową.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBaseIndicies, metoda](icordebugarrayvalue-getbaseindicies-method.md)|Pobiera podstawowy indeks każdego wymiaru w tablicy.|  
|[GetCount — Metoda](icordebugarrayvalue-getcount-method.md)|Pobiera łączną liczbę elementów w tablicy.|  
|[GetDimensions, metoda](icordebugarrayvalue-getdimensions-method.md)|Pobiera Wymiary tablicy.|  
|[GetElement, metoda](icordebugarrayvalue-getelement-method.md)|Pobiera wartość reprezentującą dany element w tablicy.|  
|[GetElementAtPosition, metoda](icordebugarrayvalue-getelementatposition-method.md)|Pobiera element w podanym miejscu, traktując tablicę jako tablicę jednowymiarową o wartości zero.|  
|[GetElementType, metoda](icordebugarrayvalue-getelementtype-method.md)|Pobiera prosty typ elementów w tablicy.|  
|[GetRank — Metoda](icordebugarrayvalue-getrank-method.md)|Pobiera liczbę wymiarów w tablicy.|  
|[HasBaseIndicies, metoda](icordebugarrayvalue-hasbaseindicies-method.md)|Określa, czy tablica ma indeksy podstawowe.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugArrayValue`obsługuje tablice jednowymiarowe i wielowymiarowe.  
  
> [!NOTE]
> Ten interfejs nie obsługuje wywoływania zdalnego na wielu maszynach ani wielu procesów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [Debugowanie — Interfejsy](debugging-interfaces.md)
