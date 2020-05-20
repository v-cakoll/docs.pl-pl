---
title: ICLRRuntimeHost::ExecuteInAppDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICLRRuntimeHost.ExecuteInAppDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type:
- apiref
ms.openlocfilehash: 505c16cb7ead7950b6d2d6d401730cc3368fb6aa
ms.sourcegitcommit: 0926684d8d34f4c6b5acce58d2193db093cb9cf2
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 05/20/2020
ms.locfileid: "83703294"
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a>ICLRRuntimeHost::ExecuteInAppDomain — Metoda
Określa, <xref:System.AppDomain> w którym ma zostać wykonany określony kod zarządzany.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,
    [in] FExecuteInDomainCallback pCallback,
    [in] void* cookie  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `AppDomainId`  
 podczas Identyfikator liczbowy, <xref:System.AppDomain> w którym ma zostać wykonana określona metoda.  
  
 `pCallback`  
 podczas Wskaźnik do funkcji, która ma zostać wykonana w obrębie określonego <xref:System.AppDomain> .  
  
 `cookie`  
 podczas Wskaźnik do nieprzezroczystej pamięci przydzielonyj przez proces wywołujący. Ten parametr jest przesyłany przez środowisko uruchomieniowe języka wspólnego (CLR) do wywołania zwrotnego domeny. Nie jest to pamięć sterty zarządzana przez środowisko uruchomieniowe; Alokacja i okres istnienia tej pamięci są kontrolowane przez obiekt wywołujący.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ExecuteInAppDomain`pomyślnie zwrócono.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, środowisko CLR nie będzie już można używać w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `ExecuteInAppDomain`umożliwia hostowi wykonywanie kontroli nad tym, która zarządza <xref:System.AppDomain> określoną metodą zarządzaną w programie. Można uzyskać wartość identyfikatora domeny aplikacji, która odpowiada wartości <xref:System.AppDomain.Id%2A> właściwości, przez wywołanie [metody GetCurrentAppDomainId —](iclrruntimehost-getcurrentappdomainid-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **.NET Framework wersje:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [ICLRRuntimeHost, interfejs](iclrruntimehost-interface.md)
