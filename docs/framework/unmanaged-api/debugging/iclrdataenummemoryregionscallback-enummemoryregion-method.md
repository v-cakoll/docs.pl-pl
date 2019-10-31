---
title: ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback.EnumMemoryRegion
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion
helpviewer_keywords:
- EnumMemoryRegion method [.NET Framework debugging]
- ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion method [.NET Framework debugging]
ms.assetid: 9bb93fab-57e8-4f9a-9ef3-1794504fa896
topic_type:
- apiref
ms.openlocfilehash: 2ebe7ef37fb072e3688cc4dcfa5ed89832e886e9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73122936"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a>ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda
Wywoływane przez [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) , aby zgłosić do debugera, wynik próby wyliczenia określonego regionu pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `address`  
 podczas Adres początkowy regionu pamięci, który miał zostać wyliczony.  
  
 `size`  
 podczas Rozmiar (w bajtach) obszaru pamięci.  
  
## <a name="remarks"></a>Uwagi  
 Metoda `ICLRDataEnumMemoryRegions::EnumMemoryRegions` wywoła tę metodę wywołania zwrotnego po każdej próbie wyliczyć regionu pamięci. Wyliczenie będzie kontynuowane, nawet jeśli ta metoda zwróci błąd wskazujący, że wynik HRESULT.  
  
 Regiony zgłaszane przez to wywołanie zwrotne mogą być duplikatami lub nakładanymi regionami.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataEnumMemoryRegionsCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
