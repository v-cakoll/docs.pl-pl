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
ms.openlocfilehash: 568c63681b84d0ab3642d84e4a6715ad230582db
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120394"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost — Interfejs
Zapewnia funkcjonalność podobną do interfejsu [ICorRuntimeHost](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md) dostępnego w .NET Framework wersja 1 z następującymi zmianami:  
  
- Dodanie metody [SetHostControl —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md) w celu ustawienia interfejsu sterowania hosta.  
  
- Pominięcie niektórych metod dostarczonych przez `ICorRuntimeHost`.  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ExecuteApplication, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md)|Używany w scenariuszach wdrażania ClickOnce opartych na manifestach, aby określić aplikację, która ma zostać aktywowana w nowej domenie.|  
|[ExecuteInAppDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeinappdomain-method.md)|Określa <xref:System.AppDomain>, w którym ma zostać wykonany określony kod zarządzany.|  
|[ExecuteInDefaultAppDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeindefaultappdomain-method.md)|Wywołuje określoną metodę określonego typu w określonym zestawie.|  
|[GetCLRControl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getclrcontrol-method.md)|Pobiera wskaźnik interfejsu typu [ICLRControl](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md) , którego mogą używać hosty do dostosowywania aspektów środowiska uruchomieniowego języka wspólnego (CLR).|  
|[GetCurrentAppDomainId, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md)|Pobiera liczbowy identyfikator <xref:System.AppDomain>, który jest aktualnie wykonywany.|  
|[SetHostControl, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-sethostcontrol-method.md)|Ustawia interfejs sterowania hosta. Przed wywołaniem `Start`należy wywołać `SetHostControl`.|  
|[Start, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md)|Inicjuje środowisko CLR w procesie.|  
|[Stop, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-stop-method.md)|Kończy wykonywanie kodu przez środowisko uruchomieniowe.|  
|[UnloadAppDomain, metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-unloadappdomain-method.md)|Zwalnia <xref:System.AppDomain> odpowiadające określonemu identyfikatorowi liczbowemu.|  
  
## <a name="remarks"></a>Uwagi  
 Rozpoczynając od .NET Framework 4, użyj interfejsu [ICLRMetaHost](../../../../docs/framework/unmanaged-api/hosting/iclrmetahost-interface.md) , aby uzyskać wskaźnik do interfejsu [ICLRRuntimeInfo](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-interface.md) , a następnie Wywołaj metodę [ICLRRuntimeInfo:: GetInterface](../../../../docs/framework/unmanaged-api/hosting/iclrruntimeinfo-getinterface-method.md) , aby uzyskać wskaźnik do `ICLRRuntimeHost`. We wcześniejszych wersjach .NET Framework Host Pobiera wskaźnik do wystąpienia `ICLRRuntimeHost` przez wywołanie [CorBindToRuntimeEx](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md). Aby zapewnić implementację dowolnej z technologii zapewnianych w .NET Framework w wersji 2,0, należy użyć `ICLRRuntimeHost` zamiast `ICorRuntimeHost`.  
  
> [!IMPORTANT]
> Nie wywołuj metody [startowej](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-start-method.md) przed wywołaniem metody [ExecuteApplication —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-executeapplication-method.md) w celu aktywowania aplikacji opartej na manifeście. Jeśli metoda `Start` jest wywoływana jako pierwsza, wywołanie metody `ExecuteApplication` zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorBindToCurrentRuntime, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx, funkcja](../../../../docs/framework/unmanaged-api/hosting/corbindtoruntimeex-function.md)
- [ICLRControl, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrcontrol-interface.md)
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
- [Hosting, interfejsy](../../../../docs/framework/unmanaged-api/hosting/hosting-interfaces.md)
- [CLRRuntimeHost, klasa coclass](../../../../docs/framework/unmanaged-api/hosting/clrruntimehost-coclass.md)
