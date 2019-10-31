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
ms.openlocfilehash: ed841d1b2ff346ebef668cbd96a58ddfe466b3b8
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120446"
---
# <a name="iclrruntimehostexecuteindefaultappdomain-method"></a>ICLRRuntimeHost::ExecuteInDefaultAppDomain — Metoda
Wywołuje określoną metodę określonego typu w określonym zarządzanym zestawie.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
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
 podczas Ścieżka do <xref:System.Reflection.Assembly>, która definiuje <xref:System.Type>, których metoda ma zostać wywołana.  
  
 `pwzTypeName`  
 podczas Nazwa <xref:System.Type>, która definiuje metodę do wywołania.  
  
 `pwzMethodName`  
 podczas Nazwa metody do wywołania.  
  
 `pwzArgument`  
 podczas Parametr ciągu, który ma zostać przekazany do metody.  
  
 `pReturnValue`  
 określoną Wartość całkowita zwrócona przez wywołaną metodę.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ExecuteInDefaultAppDomain` pomyślnie zwrócone.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca wartość E_FAIL, lista CRL nie będzie już można używać w ramach procesu. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 Wywołana metoda musi mieć następujący podpis:  
  
```cpp  
static int pwzMethodName (String pwzArgument)  
```  
  
 gdzie `pwzMethodName` reprezentuje nazwę wywołanej metody, a `pwzArgument` reprezentuje wartość ciągu przekazaną jako parametr do tej metody. Jeśli wartość HRESULT jest ustawiona na S_OK, `pReturnValue` jest ustawiona na wartość całkowitą zwracaną przez wywołaną metodę. W przeciwnym razie `pReturnValue` nie jest ustawiona.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
