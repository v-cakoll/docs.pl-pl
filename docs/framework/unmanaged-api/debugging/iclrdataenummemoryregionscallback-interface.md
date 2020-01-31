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
ms.openlocfilehash: 4e3891996af5945ed95c8c37dddfee5c446db248
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789106"
---
# <a name="iclrdataenummemoryregionscallback-interface"></a>ICLRDataEnumMemoryRegionsCallback — Interfejs
Zapewnia metodę wywołania zwrotnego dla [ICLRDataEnumMemoryRegions:: EnumMemoryRegions —](iclrdataenummemoryregions-enummemoryregions-method.md) , aby zgłosić do debugera wynik próby wyliczenia określonego regionu pamięci.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[EnumMemoryRegion, metoda](iclrdataenummemoryregionscallback-enummemoryregion-method.md)|Wywołane przez `ICLRDataEnumMemoryRegions::EnumMemoryRegions`, aby zgłosić debugerowi wynik próby wyliczenia określonego regionu pamięci.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Debugowanie, interfejsy](debugging-interfaces.md)
