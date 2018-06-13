---
title: ICorDebugVariableHomeEnum::Next — metoda
ms.date: 03/30/2017
api_name:
- ICorDebugVariableHomeEnum.Next
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICorDebugVariableHomeEnum::Next
helpviewer_keywords:
- ICorDebugVariableHomeEnum::Next method [.NET Framework debugging]
- Next method, ICorDebugVariableHomeEnum interface [.NET Framework debugging]
ms.assetid: eb9ea96c-5b58-4655-8104-094fc8b393b8
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d5ab18d6c2ae8bbf47a3bcd7cb892530be4f8f4e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33421587"
---
# <a name="icordebugvariablehomeenumnext-method"></a>ICorDebugVariableHomeEnum::Next — metoda
Pobiera określoną liczbę [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) wystąpień, które zawierają informacje o zmiennych lokalnych i argumenty w funkcji.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT Next(  
    [in] ULONG celt,  
    [out, size_is(celt), length_is(*pceltFetched)] ICorDebugVariableHome *homes[],  
    [out] ULONG *pceltFetched  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `celt`  
 [in] Liczba obiektów, które mają zostać pobrane.  
  
 `homes`  
 Tablicy wskaźników, z których każdy wskazuje [ICorDebugVariableHome](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md) obiektu, który zawiera informacje o lokalnej zmiennej lub argumentu funkcji.  
  
 `pceltFetched`  
 [out] Liczba wystąpień zwrócona faktycznie w obiektach.  
  
## <a name="return-value"></a>Wartość zwracana  
 Metoda zwraca następujące wartości.  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|`S_OK`|Metoda została ukończona pomyślnie.|  
|`S_FALSE`|Rzeczywista liczba wystąpień pobrać, zgodnie z opisem w `pceltFetched`, jest mniejsza niż liczba wystąpień żądanie.|  
  
## <a name="remarks"></a>Uwagi  
 [ICorDebugVariableHomeEnum::Next](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-next-method.md) metoda pobiera maksymalnie `celt` obiektów, zaczynając od bieżąca pozycja modułu wyliczającego. Gdy metoda zwróci wartość, `pceltFetched` zawiera rzeczywistą liczbę obiektów pobrane.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug.idl, CorDebug.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v462plus](../../../../includes/net-current-v462plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorDebugVariableHomeEnum, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehomeenum-interface.md)  
 [ICorDebugVariableHome, interfejs](../../../../docs/framework/unmanaged-api/debugging/icordebugvariablehome-interface.md)
