---
title: CLRRuntimeHost — Klasa coclass
ms.date: 03/30/2017
api_name:
- CLRRuntimeHost Coclass
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- CLRRuntimeHost
helpviewer_keywords:
- CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 8bae2d134c412023d0f126453b5285662d994c78
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59207763"
---
# <a name="clrruntimehost-coclass"></a>CLRRuntimeHost — Klasa coclass
Zawiera interfejsy zarządzania wykonywania kodu w czasie wykonywania.  
  
## <a name="syntax"></a>Składnia  
  
```  
coclass CLRRuntimeHost {  
    [default] interface  ICLRRuntimeHost;  
    interface            ICLRValidator;  
};  
```  
  
## <a name="interfaces"></a>Interfejsy  
  
|Interface|Opis|  
|---------------|-----------------|  
|[ICLRRuntimeHost — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|Udostępnia metody do kontroli wykonania aplikacji w czasie wykonywania.|  
|[ICLRValidator — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|Udostępnia metody sprawdzania poprawności przenośnego pliku wykonywalnego obrazów oraz szczegółowe raporty błędów sprawdzania poprawności.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Współklasy hostingu](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
