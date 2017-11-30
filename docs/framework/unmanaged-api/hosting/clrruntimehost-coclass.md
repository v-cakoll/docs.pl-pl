---
title: "CLRRuntimeHost — Klasa coclass"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: CLRRuntimeHost Coclass
api_location: mscoree.dll
api_type: COM
f1_keywords: CLRRuntimeHost
helpviewer_keywords: CLRRuntimeHost coclass [.NET Framework hosting]
ms.assetid: 2ac9cbf5-8a2d-4e4f-8831-0dad8ef0a897
topic_type: apiref
caps.latest.revision: "9"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 372b2466baaa76ba47a6710447d93f9fa6bb967f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="clrruntimehost-coclass"></a>CLRRuntimeHost — Klasa coclass
Zawiera interfejsy zarządzania wykonywanie kodu w czasie wykonywania.  
  
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
|[ICLRRuntimeHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)|Udostępnia metody do kontroli wykonania aplikacji w czasie wykonywania.|  
|[ICLRValidator — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrvalidator-interface.md)|Udostępnia metody weryfikacji przenośnych obrazy wykonywalne oraz szczegółowe raportowanie błędów sprawdzania poprawności.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.idl  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [Współklasy hostingu](../../../../docs/framework/unmanaged-api/hosting/hosting-coclasses.md)
