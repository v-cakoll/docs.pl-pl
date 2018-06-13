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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: d0ed92cbf5a859b9d5b7b8eddefda3ad34a98f27
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33404053"
---
# <a name="iclrdataenummemoryregionscallbackenummemoryregion-method"></a>ICLRDataEnumMemoryRegionsCallback::EnumMemoryRegion — Metoda
Wywoływane przez [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) zgłoszenia do debugera wynik próby wyliczenia określonego regionu pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumMemoryRegion (  
    [in] CLRDATA_ADDRESS  address,  
    [in] ULONG32          size  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `address`  
 [in] Adres początkowy obszaru pamięci, który miał zostać wyliczone.  
  
 `size`  
 [in] Rozmiar w bajtach obszaru pamięci.  
  
## <a name="remarks"></a>Uwagi  
 `ICLRDataEnumMemoryRegions::EnumMemoryRegions` — Metoda będzie wywoływać tej metody wywołania zwrotnego po każdej próbie wyliczyć regionu pamięci. Wyliczenie będzie kontynuowane, nawet wtedy, gdy ta metoda zwraca wartość HRESULT informujący o niepowodzeniu.  
  
 Regiony zgłoszone przez tego wywołania zwrotnego może być duplikatów lub nakładające się regionów.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRDataEnumMemoryRegionsCallback, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md)
