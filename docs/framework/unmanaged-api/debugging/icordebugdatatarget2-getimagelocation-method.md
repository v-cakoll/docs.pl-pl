---
title: Metoda ICorDebugDataTarget2::GetImageLocation
ms.date: 03/30/2017
ms.assetid: 696afe71-5852-478d-a33f-b2d2dbc4b91f
ms.openlocfilehash: ba1cc8c91c53547c6ed4025ee67a69e253f3596d
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76783582"
---
# <a name="icordebugdatatarget2getimagelocation-method"></a>Metoda ICorDebugDataTarget2::GetImageLocation
Zwraca ścieżkę modułu z adresu podstawowego modułu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetImageLocation(    [in] CORDB_ADDRESS baseAddress,  
    [in] ULONG32 cchName,  
    [out] ULONG32 *pcchName,  
    [out, size_is(cchName), length_is(*pcchName)] WCHAR szName[]  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `baseAddress`  
 podczas Wartość [CORDB_ADDRESS](../../../../docs/framework/unmanaged-api/common-data-types-unmanaged-api-reference.md) , która reprezentuje adres podstawowy modułu.  
  
 `cchName`  
 podczas Liczba znaków w buforze, która ma otrzymać ścieżkę modułu.  
  
 `pcchName`  
 określoną Wskaźnik do liczby znaków zapisanych w buforze `szName`.  
  
 `szName`  
 określoną Ścieżka modułu.  
  
## <a name="remarks"></a>Uwagi  
  
> [!NOTE]
> Ta metoda jest dostępna tylko z .NET Native.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** CorDebug. idl, CorDebug. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_46_native](../../../../includes/net-46-native-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICorDebugDataTarget2, interfejs](icordebugdatatarget2-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
