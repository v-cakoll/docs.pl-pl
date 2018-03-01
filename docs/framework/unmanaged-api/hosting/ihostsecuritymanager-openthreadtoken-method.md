---
title: "IHostSecurityManager::OpenThreadToken — Metoda"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name:
- IHostSecurityManager.OpenThreadToken
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- IHostSecurityManager::OpenThreadToken
helpviewer_keywords:
- IHostSecurityManager::OpenThreadToken method [.NET Framework hosting]
- OpenThreadToken method [.NET Framework hosting]
ms.assetid: d5999052-8bf0-4a9e-8621-da6284406b18
topic_type:
- apiref
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 9b5c39632d7628d30149a0a0278f9bf6c865bc29
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 12/22/2017
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken — Metoda
Otwiera token dostępu skojarzony z wątkiem aktualnie wykonywane.  
  
## <a name="syntax"></a>Składnia  
  
```  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
#### <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 [in] Maska wartości dostępu, które określają żądanych typów dostęp do tokenu wątku. Te wartości są definiowane w Win32 `OpenThreadToken` funkcji. Typy żądany dostęp są uzgadniane przed tokenu poufnej listy kontroli dostępu (DACL), aby określić, jakie typy dostępu do Udziel lub Odmów.  
  
 `bOpenAsSelf`  
 [in] `true` do określenia, czy należy dokonać kontroli dostępu w kontekście zabezpieczeń procesu, wątku wywołującym; `false` do określenia, czy należy wykonać sprawdzanie dostępu przy użyciu kontekstu zabezpieczeń dla sam wątek wywołujący. Jeśli wątek personifikuje klienta, kontekstu zabezpieczeń może być procesu klienta.  
  
 `phThreadToken`  
 [out] Wskaźnik do tokena dostępu w nowo otwartym.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken`zwrócona pomyślnie.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie został załadowany do procesu lub CLR jest w stanie, w którym nie można uruchamiać kodu zarządzanego lub pomyślnie przetworzyć wywołania.|  
|HOST_E_TIMEOUT|Upłynął limit czasu wywołania.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właścicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas zablokowanych wątku lub włókna oczekiwał na nim.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwróci wartość E_FAIL, CLR nie jest już możliwe w ramach procesu. Kolejne wywołania metody hosting zwracać HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostSecurityManager::OpenThreadToken`działa podobnie do funkcji Win32 odpowiedniego o takiej samej nazwie, z tą różnicą, że funkcja Win32 umożliwia obiekt wywołujący, aby przekazać w dojścia do dowolnego wątku, podczas `IHostSecurityManager::OpenThreadToken` otwiera tylko token skojarzony z wątkiem wywołującym.  
  
 `HANDLE` Typ nie jest zgodny z interfejsem COM, oznacza to, jego rozmiar jest specyficzna dla systemu operacyjnego i wymaga przekazywanie niestandardowych. W związku z tym token ten jest przeznaczona do użytku tylko w ramach procesu między środowiska CLR i hostem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE.h  
  
 **Biblioteka:** uwzględnione jako zasób w MSCorEE.dll  
  
 **Wersje programu .NET framework:**[!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz też  
 [IHostSecurityContext, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)  
 [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
