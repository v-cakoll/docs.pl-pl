---
title: ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 886f78a0561ebbd5470b7932123f67975d650693
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61698268"
---
# <a name="iclrdataenummemoryregionsenummemoryregions-method"></a>ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda
Wylicza określone obszary pamięci.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT EnumMemoryRegions (  
    [in] ICLRDataEnumMemoryRegionsCallback  *callback,  
    [in] ULONG32                            miniDumpFlags,  
    [in] CLRDataEnumMemoryFlags             clrFlags  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `callback`  
 [in] Wskaźnik do [iclrdataenummemoryregionscallback —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienia, która jest wywoływana przez tę metodę dla każdego regionu pamięci filtrująca wyliczany do debugera wyniku powiadomienia.  
  
 Wyliczenie obszarów pamięci będzie kontynuowane, nawet jeśli wywołanie zwrotne oznacza błąd.  
  
 `miniDumpFlags`  
 [in] Nie jest używany.  
  
 `clrFlags`  
 [in] Wartość [clrdataenummemoryflags —](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) wyliczenie, które określa regiony pamięci do wyliczenia.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda używa określonego [iclrdataenummemoryregionscallback —](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienia powiadomiono wywołującego wyników.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataEnumMemoryRegions, interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
