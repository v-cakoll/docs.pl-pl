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
ms.openlocfilehash: fed643ae52f50b1b8cd134880c644c8941da6f56
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122875"
---
# <a name="iclrdatatargetgetimagebase-method"></a>ICLRDataTarget::GetImageBase — Metoda
Pobiera adres pamięci podstawowej określonego obrazu.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT GetImageBase (  
    [in, string] LPCWSTR    imagePath,  
    [out] CLRDATA_ADDRESS   *baseAddress  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `imagePath`  
 podczas Nazwa pliku obrazu, łącznie z jego ścieżką.  
  
 `baseAddress`  
 określoną Wskaźnik do elementu CLRDATA_ADDRESS, który przechowuje podstawowy adres obrazu.  
  
## <a name="remarks"></a>Uwagi  
 Nazwa pliku obrazu może być nieścieżką lub nie może mieć ścieżki. Jeśli ścieżka jest określona, dopasowywanie jest wykonywane na całej ścieżce; w przeciwnym razie dopasowanie jest wykonywane tylko na nazwie pliku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdatatarget-interface.md)
