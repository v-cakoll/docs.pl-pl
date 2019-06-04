---
title: GetCLRIdentityManager — Funkcja
ms.date: 03/30/2017
api_name:
- GetCLRIdentityManager
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- GetCLRIdentityManager
helpviewer_keywords:
- GetCLRIdentityManager function [.NET Framework hosting]
ms.assetid: 66eeca30-adb4-45f4-aff5-347564c95724
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: e18172ecf2d4300ae42cc42ecdb1783744cac105
ms.sourcegitcommit: 155012a8a826ee8ab6aa49b1b3a3b532e7b7d9bd
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/04/2019
ms.locfileid: "66490420"
---
# <a name="getclridentitymanager-function"></a>GetCLRIdentityManager — Funkcja
Pobiera wskaźnik do interfejsu, który umożliwia środowisko uruchomieniowe języka wspólnego (CLR) do zarządzania tożsamościami.  
  
 Ta funkcja jest przestarzała w programie .NET Framework 4.  
  
## <a name="syntax"></a>Składnia  
  
```  
STDAPI GetCLRIdentityManager(  
    [in]  REFIID      riid,  
    [out] IUnknown  **ppManager  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `riid`  
 [in] Element `REFIID` (identyfikator interfejsu), który określa interfejs, które można pobrać. Ta wartość musi być IID_ICLRAssemblyIdentityManager lub IID_ICLRHostBindingPolicyManager.  
  
 `ppManager`  
 [out] Wskaźnik na adres albo [iclrassemblyidentitymanager —](../../../../docs/framework/unmanaged-api/hosting/iclrassemblyidentitymanager-interface.md) lub [iclrhostbindingpolicymanager —](../../../../docs/framework/unmanaged-api/hosting/iclrhostbindingpolicymanager-interface.md) obiektu.  
  
## <a name="remarks"></a>Uwagi  
 Wywołaj [getrealprocaddress —](../../../../docs/framework/unmanaged-api/hosting/getrealprocaddress-function.md) funkcję, aby uzyskać wskaźnik do `GetCLRIdentityManager` funkcji.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** MSCorWks.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [Przestarzałe funkcje hostingu środowiska CLR](../../../../docs/framework/unmanaged-api/hosting/deprecated-clr-hosting-functions.md)
