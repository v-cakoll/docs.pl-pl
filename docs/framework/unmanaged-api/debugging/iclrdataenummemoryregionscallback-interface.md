---
title: ICLRDataEnumMemoryRegionsCallback — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDataEnumMemoryRegionsCallback
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataEnumMemoryRegionsCallback
helpviewer_keywords:
- ICLRDataEnumMemoryRegionsCallback interface [.NET Framework debugging]
ms.assetid: 3f1af8b0-8478-48e0-a7ec-3e90e0b97649
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b0e7ce243658a8c8a8404ff9079ed1395e56486f
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/23/2019
ms.locfileid: "54604163"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a>ICLRDataEnumMemoryRegionsCallback — Interfejs
Zapewnia metodę wywołania zwrotnego dla [ICLRDataEnumMemoryRegions::EnumMemoryRegions](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregions-enummemoryregions-method.md) do zgłaszania do debugera wyniku próby wyliczenia określonego regionu pamięci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumMemoryRegion, metoda](../../../../docs/framework/unmanaged-api/debugging/iclrdataenummemoryregionscallback-enummemoryregion-method.md)|Wywoływane przez `ICLRDataEnumMemoryRegions::EnumMemoryRegions` do zgłaszania do debugera wyniku próby wyliczenia określonego regionu pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData.idl, ClrData.h  
  
 **Biblioteka:** CorGuids.lib  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także
- [Debugowanie, interfejsy](../../../../docs/framework/unmanaged-api/debugging/debugging-interfaces.md)
