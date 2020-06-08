---
title: IHostAssemblyManager — Interfejs
ms.date: 03/30/2017
api_name:
- IHostAssemblyManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostAssemblyManager
helpviewer_keywords:
- IHostAssemblyManager interface [.NET Framework hosting]
ms.assetid: dfec05bb-3cd7-4bd5-b396-a4f097c3a636
topic_type:
- apiref
ms.openlocfilehash: 4e32a36a4cf751bf7c5a2c918fde0122f21b7878
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84501598"
---
# <a name="ihostassemblymanager-interface"></a>IHostAssemblyManager — Interfejs
Dostarcza metody, które umożliwiają hostowi określenie zestawów zestawów, które powinny być ładowane przez środowisko uruchomieniowe języka wspólnego (CLR) lub hosta.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[GetAssemblyStore, metoda](ihostassemblymanager-getassemblystore-method.md)|Pobiera wskaźnik interfejsu do [IHostAssemblyStore](ihostassemblystore-interface.md) , który reprezentuje listę zestawów załadowanych przez hosta.|  
|[GetNonHostStoreAssemblies, metoda](ihostassemblymanager-getnonhoststoreassemblies-method.md)|Pobiera wskaźnik interfejsu do [ICLRAssemblyReferenceList](iclrassemblyreferencelist-interface.md) , który reprezentuje listę zestawów, które host oczekuje na załadowanie środowiska CLR.|  
  
## <a name="remarks"></a>Uwagi  
 Host nie jest wymagany do implementowania `IHostAssemblyManager` ani `IHostAssemblyStore` . Jeśli host jest zaimplementowany `IHostAssemblyManager` , musi również implementować `IHostAssemblyStore` .  
  
 Zapytania środowiska uruchomieniowego dla obiektu `IHostAssemblyManager` przez wywołanie [IHostControl:: GetHostManager](ihostcontrol-gethostmanager-method.md) po zainicjowaniu z `IID` IID_IHostAssemblyManager.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRAssemblyReferenceList — Interfejs](iclrassemblyreferencelist-interface.md)
- [IHostAssemblyStore, interfejs](ihostassemblystore-interface.md)
- [IHostControl, interfejs](ihostcontrol-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
