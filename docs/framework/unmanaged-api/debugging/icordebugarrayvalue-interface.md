---
title: ICorDebugArrayValue, interfejs1
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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 7b8e9e9c9f43b45bf4f5d65bf80394c0fcd71325
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559283"
---
# <a name="icordebugarrayvalue-interface1"></a>ICorDebugArrayValue, interfejs1
Podklasa klasy ICorDebugHeapValue, który reprezentuje tablicę jednowymiarową lub wielowymiarową.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBaseIndicies, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Pobiera podstawowy indeks każdego wymiaru tablicy.|  
|[GetCount, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Pobiera całkowitą liczbę elementów w tablicy.|  
|[GetDimensions, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Pobiera wymiary tablicy.|  
|[GetElement, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Pobiera wartość reprezentującą danego elementu w tablicy.|  
|[GetElementAtPosition, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Pobiera element wskazywany danej pozycji, traktując tablicy jako tablicę indeksowaną od zera, jednowymiarową.|  
|[GetElementType, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Pobiera prosty typ elementów w tablicy.|  
|[GetRank, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Pobiera liczbę wymiarów w tablicy.|  
|[HasBaseIndicies, metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Określa, czy tablica zawiera indeksy podstawowej.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugArrayValue` obsługuje tablice jednowymiarowe i wielowymiarowe.  
  
> [!NOTE]
>  Ten interfejs może być wywoływany zdalnie, między komputerami ani między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
