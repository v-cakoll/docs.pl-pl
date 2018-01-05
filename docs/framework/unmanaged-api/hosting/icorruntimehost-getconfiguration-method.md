---
title: "ICorRuntimeHost::GetConfiguration — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICorRuntimeHost.GetConfiguration
api_location: mscoree.dll
api_type: COM
f1_keywords: ICorRuntimeHost::GetConfiguration
helpviewer_keywords:
- ICorRuntimeHost::GetConfiguration method [.NET Framework hosting]
- GetConfiguration method [.NET Framework hosting]
ms.assetid: c431617a-b055-44a0-8730-48b7a86d9610
topic_type: apiref
caps.latest.revision: "10"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 446142d8bd61d384c3b8a58d5469e27a7a512c60
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="icorruntimehostgetconfiguration-method"></a>ICorRuntimeHost::GetConfiguration — Metoda
Pobiera obiekt, który umożliwia hosta określić konfigurację wywołania zwrotnego środowisko uruchomieniowe języka wspólnego (CLR).  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetConfiguration(  
    [out] ICorConfiguration** pConfiguration  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `pConfiguration`  
 [out] Wskaźnik do adresu [ICorConfiguration](../../../../docs/framework/unmanaged-api/hosting/icorconfiguration-interface.md) obiektu, który może służyć do konfigurowania środowiska CLR.  
  
## <a name="remarks"></a>Uwagi  
 Przed jego inicjowania; należy skonfigurować środowisko CLR w przeciwnym razie `GetConfiguration` metoda zwróci wartość HRESULT wskazujący błąd.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Zobacz też  
 [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
