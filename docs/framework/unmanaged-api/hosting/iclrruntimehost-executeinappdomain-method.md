---
title: "ICLRRuntimeHost::ExecuteInAppDomain — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: ICLRRuntimeHost.ExecuteInAppDomain
api_location: mscoree.dll
api_type: COM
f1_keywords: ICLRRuntimeHost::ExecuteInAppDomain
helpviewer_keywords:
- ICLRRuntimeHost::ExecuteInAppDomain method [.NET Framework hosting]
- ExecuteInAppDomain method [.NET Framework hosting]
ms.assetid: e2b0e2db-3fae-4b56-844e-d30a125a660c
topic_type: apiref
caps.latest.revision: "16"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: da6e9b52c0ea6f2935aad70779e159db91a4f501
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/18/2017
---
# <a name="iclrruntimehostexecuteinappdomain-method"></a>ICLRRuntimeHost::ExecuteInAppDomain — Metoda
Określa <xref:System.AppDomain> polegający na wykonanie określonego kodu zarządzanego.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT ExecuteInAppDomain(  
    [in] DWORD AppDomainId,   
    [in] FExecuteInDomainCallback pCallback,   
    [in] void* cookie  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `AppDomainId`  
 [in] Numeryczny identyfikator <xref:System.AppDomain> w którym można wykonać określonej metody.  
  
 `pCallback`  
 [in] Wskaźnik do funkcji, które można wykonać w ramach określonego <xref:System.AppDomain>.  
  
 `cookie`  
 [in] Wskaźnik do nieprzezroczyste pamięci przydzielone przez obiekt wywołujący. Ten parametr jest przekazywany przez środowisko uruchomieniowe języka wspólnego (CLR) do domeny wywołania zwrotnego. Nie jest pamięci sterty zarządzanego środowiska wykonawczego. alokacji i okres istnienia tej pamięci są kontrolowane przez obiekt wywołujący.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`ExecuteInAppDomain`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Jeśli metoda zwraca E_FAIL, CLR nie będzie już można używać w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `ExecuteInAppDomain`Umożliwia hosta sprawowanie kontroli over zarządzanych <xref:System.AppDomain> określonej metody zarządzane mają zostać wykonane w. Można pobrać wartości identyfikatora domeny aplikacji, co odpowiada wartości <xref:System.AppDomain.Id%2A> właściwości, wywołując [GetCurrentAppDomainId — metoda](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-getcurrentappdomainid-method.md).  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [ICLRRuntimeHost — interfejs](../../../../docs/framework/unmanaged-api/hosting/iclrruntimehost-interface.md)
