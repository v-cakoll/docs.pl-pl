---
title: ICorRuntimeHost::CurrentDomain — Metoda
ms.date: 03/30/2017
api_name:
- ICorRuntimeHost.CurrentDomain
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- ICorRuntimeHost::CurrentDomain
helpviewer_keywords:
- ICorRuntimeHost::CreateDomain method [.NET Framework hosting]
- CurrentDomain method [.NET Framework hosting]
ms.assetid: dd2afb38-675b-4c3c-a9f3-8ab3b133eb02
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 1cb5ff5300a7fd2577e602b3077dd816cf7dfbe2
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 04/18/2019
ms.locfileid: "59181391"
---
# <a name="icorruntimehostcurrentdomain-method"></a>ICorRuntimeHost::CurrentDomain — Metoda
Pobiera wskaźnik interfejsu typu <xref:System.AppDomain?displayProperty=nameWithType> reprezentujący domeny załadowany w bieżącym wątku.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT CurrentDomain (  
    [out] IUnknown** pAppDomain  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `pAppDomain`  
 [out] Wskaźnik typu <xref:System.AppDomain?displayProperty=nameWithType> reprezentujący wątku bieżącej domeny aplikacji. This, wskaźnik jest wpisane `IUnknown`, więc obiekty wywołujące zwykle powinny wywoływać `QueryInterface` uzyskać wskaźnika typu <xref:System._AppDomain>.  
  
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
