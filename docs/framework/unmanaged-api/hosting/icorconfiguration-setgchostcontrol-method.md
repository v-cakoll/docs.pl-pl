---
title: "ICorConfiguration::SetGCHostControl — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorConfiguration.SetGCHostControl
api_location: mscoree.dll
api_type: COM
f1_keywords: SetGCHostControl
helpviewer_keywords:
- ICorConfiguration::SetGCHostControl method [.NET Framework hosting]
- SetGCHostControl method [.NET Framework hosting]
ms.assetid: bca6bd79-e288-475a-aa46-6bf81541d966
topic_type: apiref
caps.latest.revision: "7"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 33d01ff208e9814e73c7a658e41819348da6831a
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="icorconfigurationsetgchostcontrol-method"></a>ICorConfiguration::SetGCHostControl — Metoda
Ustawia wywołanie zwrotne interfejsu używanego przez moduł garbage collector na żądanie hosta, aby zmienić limit pamięci wirtualnej.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetGCHostControl (  
    [in] IGCHostControl* pGCHostControl  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pGCHostControl`  
 [in] Wskaźnik do [IGCHostControl](../../../../docs/framework/unmanaged-api/hosting/igchostcontrol-interface.md) obiekt, który umożliwia modułu zbierającego elementy bezużyteczne na żądanie hosta, aby zmienić limit pamięci wirtualnej.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorConfiguration — interfejs](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
