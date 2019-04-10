---
title: ICLRRuntimeHost::UnloadAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.UnloadAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::UnloadAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::UnloadAppDomain method [.NET Framework hosting]
- UnloadAppDomain method [.NET Framework hosting]
ms.assetid: 571912bc-3429-4ff8-8eb2-ea993ffbd901
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 490af9ca67b538e0093115a6b371b65d9788772f
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59222968"
---
# <a name="iclrruntimehostunloadappdomain-method"></a>ICLRRuntimeHost::UnloadAppDomain — Metoda
Zwalnia zarządzanej <xref:System.AppDomain> , który odpowiada określony identyfikator liczbowy.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT UnloadAppDomain(  
    [in] DWORD dwAppDomainId  
    [in] BOOL  fWaitUntilDone  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwAppDomainId`  
 [in] Identyfikator liczbowy domeny aplikacji, aby zwolnić.  
  
 `fWaitUntilDone`  
 [in] `true` do wskazania, że środowisko uruchomieniowe języka wspólnego (CLR) muszą czekać, aż zakończy się wykonywanie bieżącego wątku aplikacji przed podjęciem próby zwolnienie domeny aplikacji.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`UnloadAppDomain` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Możesz uzyskać identyfikator liczbowy domeny aplikacji, w którym bieżącego wątku jest wykonywana przez wywołanie metody [getcurrentappdomainid —](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md). Ten identyfikator odnosi się do <xref:System.AppDomain.Id%2A> właściwość zarządzaną <xref:System.AppDomain> typu.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeHost — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
