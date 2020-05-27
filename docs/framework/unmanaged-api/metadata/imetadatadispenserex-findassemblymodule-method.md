---
title: IMetaDataDispenserEx::FindAssemblyModule — Metoda
ms.date: 03/30/2017
api_name:
- IMetaDataDispenserEx.FindAssemblyModule
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IMetaDataDispenserEx::FindAssemblyModule
helpviewer_keywords:
- FindAssemblyModule method [.NET Framework metadata]
- IMetaDataDispenserEx::FindAssemblyModule method [.NET Framework metadata]
ms.assetid: d1fb65e1-7e19-4513-85b1-44f87c294d3e
topic_type:
- apiref
ms.openlocfilehash: 64f1e2a8f05616c7ca84bc130428629b1176e985
ms.sourcegitcommit: 03fec33630b46e78d5e81e91b40518f32c4bd7b5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/27/2020
ms.locfileid: "84006184"
---
# <a name="imetadatadispenserexfindassemblymodule-method"></a>IMetaDataDispenserEx::FindAssemblyModule — Metoda
Ta metoda nie jest zaimplementowana. Jeśli zostanie wywołana, zwraca E_NOTIMPL.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT FindAssemblyModule(  
    [in]  LPCWSTR  szAppBase,  
    [in]  LPCWSTR  szPrivateBin,  
    [in]  LPCWSTR  szGlobalBin,  
    [in]  LPCWSTR  szAssemblyName,  
    [in]  LPCWSTR  szModuleName,  
    [out] LPCWSTR  szName,  
    [in]  ULONG    cchName,  
    [out] ULONG    *pcName  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `szAppBase`  
 podczas Nieużywane.  
  
 `szPrivateBin`  
 podczas Nieużywane.  
  
 `szGlobalBin`  
 podczas Nieużywane.  
  
 `szAssemblyName`  
 podczas Nazwa modułu.  
  
 `szModuleName`  
 podczas Zestaw, który ma zostać znaleziony.  
  
 `szName`  
 określoną Prosta nazwa zestawu.  
  
 `cchName`  
 podczas Rozmiar, w bajtach, z `szName` .  
  
 `pcName`  
 określoną Liczba znaków, które faktycznie zostały zwrócone `szName` .  
  
## <a name="requirements"></a>Wymagania  
 **Platforma:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** Cor. h  
  
 **Biblioteka:** Używany jako zasób w bibliotece MsCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też

- [IMetaDataDispenserEx, interfejs](imetadatadispenserex-interface.md)
- [IMetaDataDispenser — Interfejs](imetadatadispenser-interface.md)
