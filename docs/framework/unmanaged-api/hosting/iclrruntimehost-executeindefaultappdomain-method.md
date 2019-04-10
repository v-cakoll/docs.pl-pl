---
title: ICLRRuntimeHost::ExecuteInDefaultAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInDefaultAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInDefaultAppDomain method [.NET Framework hosting]
- ExecuteInDefaultAppDomain method [.NET Framework hosting]
ms.assetid: 30b5cf9a-a762-4bd4-be12-d6c1442b78b1
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1e6805dc67f7ec5ceb8c67d77462a0200b6c0317
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/08/2019
ms.locfileid: "59205912"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain — Metoda
Wywołuje określoną metodę określonego typu w określonym zestawie zarządzanym.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExecuteInDefaultAppDomain (  
    [in] LPCWSTR pwzAssemblyPath,  
    [in] LPCWSTR pwzTypeName,   
    [in] LPCWSTR pwzMethodName,  
    [in] LPCWSTR pwzArgument,  
    [out] DWORD *pReturnValue  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pwzAssemblyPath`  
 [in] Ścieżka do <xref:System.Reflection.Assembly> definiujący <xref:System.Type> metodę, której ma zostać wywołana.  
  
 `pwzTypeName`  
 [in] Nazwa <xref:System.Type> definiuje metody do wywołania.  
  
 `pwzMethodName`  
 [in] Nazwa metody do wywołania.  
  
 `pwzArgument`  
 [in] Parametr typu ciąg do przekazania do metody.  
  
 `pReturnValue`  
 [out] Wartość liczby całkowitej, zwrócona przez wywoływanej metody.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain` pomyślnie zwrócił.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie posiada blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowane wątki lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, listy CRL nie będzie już można używać w ramach procesu. Kolejne wywołania do hostowania metody zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołana metoda musi mieć następujący podpis:  
  
```  
static int pwzMethodName (String pwzArgument)  
```  
  
 gdzie `pwzMethodName` reprezentuje nazwę wywoływanej metody i `pwzArgument` reprezentuje wartość ciągu jest przekazywany jako parametr do tej metody. Jeśli ustawiono wartość HRESULT S_OK, `pReturnValue` jest ustawiona na wartość całkowitą, zwracany przez wywoływanej metody. W przeciwnym razie `pReturnValue` nie jest ustawiona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeHost — Interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
