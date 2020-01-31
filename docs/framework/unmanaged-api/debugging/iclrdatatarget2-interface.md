---
title: ICLRDataTarget2 — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRDataTarget2
api_location:
- mscordbi.dll
api_type:
- COM
f1_keywords:
- ICLRDataTarget2
helpviewer_keywords:
- ICLRDataTarget2 interface [.NET Framework debugging]
ms.assetid: 94249397-861b-4294-a538-cf01466a66d3
topic_type:
- apiref
ms.openlocfilehash: bdc8378a129dd5bb1d9fdcb080c7b5cd53d34091
ms.sourcegitcommit: 13e79efdbd589cad6b1de634f5d6b1262b12ab01
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 01/28/2020
ms.locfileid: "76789074"
---
# <a name="iclrdatatarget2-interface"></a>ICLRDataTarget2 — Interfejs
Podklasa elementu [ICLRDataTarget](iclrdatatarget-interface.md) , która jest używana przez warstwę usług dostępu do danych do manipulowania regionami pamięci wirtualnej w procesie docelowym.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[AllocVirtual, metoda](iclrdatatarget2-allocvirtual-method.md)|Przydziela pamięć w przestrzeni adresowej procesu docelowego.|  
|[FreeVirtual, metoda](iclrdatatarget2-freevirtual-method.md)|Zwalnia pamięć, która została wcześniej przypisana w przestrzeni adresowej procesu docelowego.|  
  
## <a name="remarks"></a>Uwagi  
 Klient API (tzn. debuger) musi implementować ten interfejs stosownie do określonego procesu docelowego. Na przykład żywy proces miałby inną implementację od tej ze zrzutu pamięci. Cel może nie obsługiwać modyfikacji regionów pamięci.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** ClrData. idl, ClrData. h  
  
 **Biblioteka:** CorGuids. lib  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRDataTarget, interfejs](iclrdatatarget-interface.md)
- [Debugowanie, interfejsy](debugging-interfaces.md)
