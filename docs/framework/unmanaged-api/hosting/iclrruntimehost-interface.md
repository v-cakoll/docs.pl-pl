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
ms.openlocfilehash: 72caac0aafe7f9c5919057a6ad2565258aec6a50
ms.sourcegitcommit: da21fc5a8cce1e028575acf31974681a1bc5aeed
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/08/2020
ms.locfileid: "84504085"
---
# <a name="iclrruntimehost-interface"></a>ICLRRuntimeHost — Interfejs
Zapewnia funkcjonalność podobną do interfejsu [ICorRuntimeHost](icorruntimehost-interface.md) dostępnego w .NET Framework wersja 1 z następującymi zmianami:  
  
- Dodanie metody [SetHostControl —](iclrruntimehost-sethostcontrol-method.md) w celu ustawienia interfejsu sterowania hosta.  
  
- Pominięcie niektórych metod dostarczonych przez `ICorRuntimeHost` .  
  
## <a name="methods"></a>Metody  
  
|Metoda|Opis|  
|------------|-----------------|  
|[ExecuteApplication, metoda](iclrruntimehost-executeapplication-method.md)|Używany w scenariuszach wdrażania ClickOnce opartych na manifestach, aby określić aplikację, która ma zostać aktywowana w nowej domenie.|  
|[ExecuteInAppDomain, metoda](iclrruntimehost-executeinappdomain-method.md)|Określa, <xref:System.AppDomain> w którym ma zostać wykonany określony kod zarządzany.|  
|[ExecuteInDefaultAppDomain, metoda](iclrruntimehost-executeindefaultappdomain-method.md)|Wywołuje określoną metodę określonego typu w określonym zestawie.|  
|[GetCLRControl, metoda](iclrruntimehost-getclrcontrol-method.md)|Pobiera wskaźnik interfejsu typu [ICLRControl](iclrcontrol-interface.md) , którego mogą używać hosty do dostosowywania aspektów środowiska uruchomieniowego języka wspólnego (CLR).|  
|[GetCurrentAppDomainId, metoda](iclrruntimehost-getcurrentappdomainid-method.md)|Pobiera liczbowy identyfikator <xref:System.AppDomain> , który jest aktualnie wykonywany.|  
|[SetHostControl, metoda](iclrruntimehost-sethostcontrol-method.md)|Ustawia interfejs sterowania hosta. `SetHostControl`Przed wywołaniem należy wywołać metodę `Start` .|  
|[Start — Metoda](iclrruntimehost-start-method.md)|Inicjuje środowisko CLR w procesie.|  
|[Stop, metoda](iclrruntimehost-stop-method.md)|Kończy wykonywanie kodu przez środowisko uruchomieniowe.|  
|[UnloadAppDomain, metoda](iclrruntimehost-unloadappdomain-method.md)|Zwalnia dane <xref:System.AppDomain> odnoszące się do określonego identyfikatora liczbowego.|  
  
## <a name="remarks"></a>Uwagi  
 Rozpoczynając od .NET Framework 4, użyj interfejsu [ICLRMetaHost](iclrmetahost-interface.md) , aby uzyskać wskaźnik do interfejsu [ICLRRuntimeInfo](iclrruntimeinfo-interface.md) , a następnie Wywołaj metodę [ICLRRuntimeInfo:: GetInterface](iclrruntimeinfo-getinterface-method.md) , aby uzyskać wskaźnik do `ICLRRuntimeHost` . We wcześniejszych wersjach .NET Framework Host Pobiera wskaźnik do `ICLRRuntimeHost` wystąpienia przez wywołanie [CorBindToRuntimeEx](corbindtoruntimeex-function.md) lub [CorBindToCurrentRuntime](corbindtocurrentruntime-function.md). Aby zapewnić implementację dowolnej z technologii zapewnianych w .NET Framework w wersji 2,0, należy użyć `ICLRRuntimeHost` zamiast `ICorRuntimeHost` .  
  
> [!IMPORTANT]
> Nie wywołuj metody [startowej](iclrruntimehost-start-method.md) przed wywołaniem metody [ExecuteApplication —](iclrruntimehost-executeapplication-method.md) w celu aktywowania aplikacji opartej na manifeście. Jeśli `Start` Metoda jest wywoływana jako pierwsza, `ExecuteApplication` wywołanie metody zakończy się niepowodzeniem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [CorBindToCurrentRuntime, funkcja](corbindtocurrentruntime-function.md)
- [CorBindToRuntimeEx, funkcja](corbindtoruntimeex-function.md)
- [ICLRControl — Interfejs](iclrcontrol-interface.md)
- [ICorRuntimeHost, interfejs](icorruntimehost-interface.md)
- [Hosting, interfejsy](hosting-interfaces.md)
- [CLRRuntimeHost, klasa coclass](clrruntimehost-coclass.md)
