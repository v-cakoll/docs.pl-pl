---
title: ICLRRuntimeHost — Interfejs
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost
helpviewer_keywords:
- ICLRRuntimeHost interface [.NET Framework hosting]
ms.assetid: cb0c5f65-3791-47bc-b833-2f84f4101ba5
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ed32fe643a7722eaf1af38e6079096194690e950
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/23/2019
ms.locfileid: "61771896"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost — Interfejs
Oferuje funkcje podobne do tego elementu [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) interfejsu podany w .NET Framework w wersji 1, z następującymi zmianami:  
  
- Dodanie [sethostcontrol —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) metodę, aby ustawić interfejs kontrolki hosta.  
  
- Pominięcie niektórych metod dostarczonych przez `ICorRuntimeHost`.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ExecuteApplication, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|Używane w oparte na manifeście scenariusze wdrażania technologii ClickOnce do określenia aplikacji zostanie uaktywniony w nowej domenie.|  
|[ExecuteInAppDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Określa <xref:System.AppDomain> w którym można wykonać określonego kodu zarządzanego.|  
|[ExecuteInDefaultAppDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Wywołuje określoną metodę określonego typu w określonym zestawie.|  
|[GetCLRControl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Pobiera wskaźnik interfejsu typu [iclrcontrol —](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) czy hostów można użyć do dostosowania aspektów środowisko uruchomieniowe języka wspólnego (CLR).|  
|[GetCurrentAppDomainId, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Pobiera identyfikator liczbowy z <xref:System.AppDomain> obecnie jest wykonywana.|  
|[SetHostControl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Ustawia interfejs kontrolki hosta. Należy wywołać `SetHostControl` przed wywołaniem `Start`.|  
|[Start, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|Inicjuje środowisko CLR do procesu.|  
|[Stop, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Zatrzymuje wykonywanie kodu w czasie wykonywania.|  
|[UnloadAppDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Zwalnia <xref:System.AppDomain> , który odpowiada określony identyfikator liczbowy.|  
  
## <a name="remarks"></a>Uwagi  
 Począwszy od [!INCLUDE[net_v40_long](../../../../includes/net-v40-long-md.md)], użyj [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) interfejsu, aby uzyskać wskaźnik do [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) interfejsu, a następnie wywołaj [iclrruntimeinfo::getinterface —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) metodę, aby uzyskać wskaźnik do `ICLRRuntimeHost`. We wcześniejszych wersjach programu .NET Framework, host pobiera wskaźnik do `ICLRRuntimeHost` wystąpienia, wywołując [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Aby zapewnić implementacje technologii dostarczanych w .NET Framework w wersji 2.0, należy użyć `ICLRRuntimeHost` zamiast `ICorRuntimeHost`.  
  
> [!IMPORTANT]
>  Nie wywołuj [Start](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) metoda przed wywołaniem [executeapplication —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) metodę, aby aktywować manifestu aplikacji. Jeśli `Start` najpierw jest wywoływana metoda `ExecuteApplication` wywołania metody zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost, klasa coclass](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
