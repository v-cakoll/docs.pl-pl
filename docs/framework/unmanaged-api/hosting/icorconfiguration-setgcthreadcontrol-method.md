---
title: ICorConfiguration::SetGCThreadControl — Metoda
ms.date: 03/30/2017
api_name:
- ICorConfiguration.SetGCThreadControl
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- SetGCThreadControl
helpviewer_keywords:
- ICorConfiguration::SetGCThreadControl method [.NET Framework hosting]
- SetGCThreadControl method [.NET Framework hosting]
ms.assetid: 72e38e61-3d56-4ae3-b8f6-0ab7922aaf11
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 9da3c0ee081b81411d13dfcf9c8557c6bd4d3448
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/04/2018
ms.locfileid: "33437310"
---
# <a name="icorconfigurationsetgcthreadcontrol-method"></a>ICorConfiguration::SetGCThreadControl — Metoda
Określa interfejs wywołania zwrotnego dla planowania wątków dla zadań z systemem innym niż środowisko uruchomieniowe, które można zablokować dla wyrzucania elementów bezużytecznych.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT SetGCThreadControl (  
    [in] IGCThreadControl* pGCThreadControl  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pGCThreadControl`  
 [in] Wskaźnik do [IGCThreadControl](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-interface.md) obiekt, który powiadamia hosta o zawieszenie wątków dla zadań innych niż środowiska wykonawczego.  
  
## <a name="remarks"></a>Uwagi  
 Host może wybrać w ramach [IGCThreadControl::ThreadIsBlockingForSuspension](../../../../docs/framework/unmanaged-api/hosting/igcthreadcontrol-threadisblockingforsuspension-method.md) wywołania zwrotnego czy należy zaplanować wątku.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICorConfiguration, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md)
