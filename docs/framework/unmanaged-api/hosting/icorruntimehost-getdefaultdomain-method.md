---
title: ICorRuntimeHost::GetDefaultDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.GetDefaultDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::GetDefaultDomain
helpviewer_keywords:
- ICorRuntimeHost::GetDefaultDomain method [.NET Framework hosting]
- GetDefaultDomain method [.NET Framework hosting]
ms.assetid: 5e17a6fc-f335-4aae-9bb0-c3e1271a9426
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b3880c1bf9cb1417953818551f802fb78773952d
ms.sourcegitcommit: 5137208fa414d9ca3c58cdfd2155ac81bc89e917
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 03/06/2019
ms.locfileid: "57485567"
---
# <a name="icorruntimehostgetdefaultdomain-method"></a>ICorRuntimeHost::GetDefaultDomain — Metoda
Pobiera wskaźnik interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType> reprezentujący domyślnej domeny dla bieżącego procesu.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT GetDefaultDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [out] Wskaźnik interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType> do <xref:System.AppDomain> wystąpienia, która reprezentuje domyślnej domeny aplikacji dla procesu.  
  
 This, wskaźnik jest wpisane `IUnknown`, więc obiekty wywołujące zwykle powinny wywoływać `QueryInterface` uzyskać wskaźnika interfejsu typu <xref:System._AppDomain?displayProperty=nameWithType>.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|Operacja zakończyła się pomyślnie.|  
|S_FALSE|Nie można ukończyć operacji.|  
|E_FAIL|Wystąpił błąd nieznanego, krytycznego. Jeśli metoda zwraca E_FAIL, środowisko uruchomieniowe języka wspólnego (CLR) nie jest już możliwe w procesie. Kolejne wywołania do dowolnych hostowania interfejsów API zwraca HOST_E_CLRNOTAVAILABLE.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko CLR nie został załadowany do procesu lub środowisko CLR jest w stanie, w której nie można uruchomić kod zarządzany lub przetworzyć wywołania.|  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** Dołączony jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:** 1.0, 1.1  
  
## <a name="see-also"></a>Zobacz także
- <xref:System._AppDomain>
- <xref:System.AppDomain>
- [ICorRuntimeHost, interfejs](../../../../docs/framework/unmanaged-api/hosting/icorruntimehost-interface.md)
