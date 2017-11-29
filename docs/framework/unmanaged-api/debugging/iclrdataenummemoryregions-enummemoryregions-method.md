---
title: "ICLRDataEnumMemoryRegions::EnumMemoryRegions — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRDataEnumMemoryRegions.EnumMemoryRegions
api_location: mscordbi.dll
api_type: COM
f1_keywords: ICLRDataEnumMemoryRegions::EnumMemoryRegions
helpviewer_keywords:
- ICLRDataEnumMemoryRegions::EnumMemoryRegions method [.NET Framework debugging]
- EnumMemoryRegions method [.NET Framework debugging]
ms.assetid: 22d2e339-f174-40b5-a478-0b744501566f
topic_type: apiref
caps.latest.revision: "12"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 1393c5c803020339ef998a57b87ad495220c1046
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
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
  
#### <a name="parameters"></a>Parametry  
 `callback`  
 [in] Wskaźnik do [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienie, które jest wywoływana przez tę metodę w poszczególnych regionach pamięci wyliczany do debugera w wyniku powiadomienia.  
  
 Wyliczanie regiony pamięci będzie kontynuowane, nawet wtedy, gdy wywołanie zwrotne oznacza błąd.  
  
 `miniDumpFlags`  
 [in] Nie jest używany.  
  
 `clrFlags`  
 [in] Wartość [CLRDataEnumMemoryFlags](../../../../docs/framework/unmanaged-api/debugging/clrdataenummemoryflags-enumeration.md) wyliczenia, który określa regiony pamięci, które mają zostać wyliczone.  
  
## <a name="remarks"></a>Uwagi  
 Ta metoda używa określonego [ICLRDataEnumMemoryRegionsCallback](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-interface.md) wystąpienia, aby powiadomić wywołującego wyników.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRDataEnumMemoryRegions — interfejs](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-interface.md)
