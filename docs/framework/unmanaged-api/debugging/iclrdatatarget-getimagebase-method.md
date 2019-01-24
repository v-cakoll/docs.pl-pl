---
title: ICLRDataTarget::GetImageBase — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataTarget.GetImageBase
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget::GetImageBase
helpviewer_keywords:
- ICLRDataTarget::GetImageBase method [.NET Framework debugging]
- GetImageBase method [.NET Framework debugging]
ms.assetid: 091c5f32-c160-49e3-a75f-4692e084c8e4
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 2ef46c066512caac93f5f0cb189152d2cac6dada
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54633872"
---
# <a name="iclrdatatargetgetimagebase-method"></a>ICLRDataTarget::GetImageBase — Metoda
Pobiera adres podstawowy pamięci określonego obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `imagePath`  
 [in] Nazwa pliku obrazu, wraz ze ścieżką.  
  
 `baseAddress`  
 [out] Wskaźnik do CLRDATA_ADDRESS, która przechowuje adres podstawowy obrazu.  
  
## <a name="remarks"></a>Uwagi  
 Nazwa pliku obrazu może lub nie może być ścieżką. Jeśli ścieżka jest określona, dopasowanie jest wykonywane na całej ścieżce; w przeciwnym razie dopasowanie jest wykonywane tylko na nazwę pliku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [ICLRDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
