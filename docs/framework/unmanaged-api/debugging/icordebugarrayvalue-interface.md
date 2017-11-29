---
title: ICorDebugArrayValue Interface1
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorDebugArrayValue
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICorDebugArrayValue interface
helpviewer_keywords: ICorDebugArrayValue interface [.NET Framework debugging]
ms.assetid: dc437751-7093-44e2-bfdc-191d9ce3c192
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 13e226ccdcd6becc98d524c429b5cadae8d19c3e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icordebugarrayvalue-interface1"></a>ICorDebugArrayValue Interface1
Podklasa ICorDebugHeapValue reprezentujący tablicy jednowymiarowej lub wielowymiarowych.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetBaseIndicies — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getbaseindicies-method.md)|Pobiera podstawowy indeks każdego wymiaru tablicy.|  
|[GetCount — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getcount-method.md)|Pobiera całkowitą liczbę elementów w tablicy.|  
|[GetDimensions — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getdimensions-method.md)|Pobiera wymiarów tablicy.|  
|[GetElement — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelement-method.md)|Pobiera wartość reprezentującą danego elementu w tablicy.|  
|[GetElementAtPosition — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementatposition-method.md)|Pobiera element na pozycji, traktując jako tablica liczony od zera, jednowymiarowej tablicy.|  
|[GetElementType — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getelementtype-method.md)|Pobiera prosty typ elementów w tablicy.|  
|[GetRank — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-getrank-method.md)|Pobiera liczbę wymiarów tablicy.|  
|[HasBaseIndicies — metoda](../../../../docs/framework/unmanaged-api/debugging/icordebugarrayvalue-hasbaseindicies-method.md)|Określa, czy tablica zawiera podstawowe indeksy.|  
  
## <a name="remarks"></a>Uwagi  
 `ICorDebugArrayValue`obsługuje zarówno jednowymiarowe i wielowymiarowych tablic.  
  
> [!NOTE]
>  Ten interfejs nie obsługuje wywoływany zdalnie, między komputerami lub między procesami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Interfejsy debugowania](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
