---
title: IHostSecurityManager::OpenThreadToken — Metoda
ms.date: 03/30/2017
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
ms.openlocfilehash: 2ced153798355aff882f0244f3dd946c39dea2bd
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 10/30/2019
ms.locfileid: "73121468"
---
# <a name="ihostsecuritymanageropenthreadtoken-method"></a>IHostSecurityManager::OpenThreadToken — Metoda
Otwiera token dostępu swobodnego skojarzony z aktualnie wykonywanym wątkiem.  
  
## <a name="syntax"></a>Składnia  
  
```cpp  
HRESULT OpenThreadToken (  
    [in]  DWORD    dwDesiredAccess,   
    [in]  BOOL     bOpenAsSelf,   
    [out] HANDLE   *phThreadToken  
);  
```  
  
## <a name="parameters"></a>Parametry  
 `dwDesiredAccess`  
 podczas Maska wartości dostępu określająca żądane typy dostępu do tokenu wątku. Te wartości są zdefiniowane w funkcji `OpenThreadToken` Win32. Żądane typy dostępu są uzgadniane z poufną listą kontroli dostępu (DACL) tokenu, aby określić, które typy dostępu mają być udzielone lub odrzucane.  
  
 `bOpenAsSelf`  
 [in] `true`, aby określić, że sprawdzanie dostępu należy przeprowadzić przy użyciu kontekstu zabezpieczeń procesu dla wątku wywołującego; `false`, aby określić, że sprawdzanie dostępu ma być wykonywane przy użyciu kontekstu zabezpieczeń dla samego wątku wywołującego. Jeśli wątek personifikuje klienta, kontekst zabezpieczeń może być procesem klienta.  
  
 `phThreadToken`  
 określoną Wskaźnik do nowo otwartego tokenu dostępu.  
  
## <a name="return-value"></a>Wartość zwracana  
  
|HRESULT|Opis|  
|-------------|-----------------|  
|S_OK|`OpenThreadToken` pomyślnie zwrócone.|  
|HOST_E_CLRNOTAVAILABLE|Środowisko uruchomieniowe języka wspólnego (CLR) nie zostało załadowane do procesu lub środowisko CLR znajduje się w stanie, w którym nie można uruchomić kodu zarządzanego lub przetworzyć wywołania pomyślnie.|  
|HOST_E_TIMEOUT|Upłynął limit czasu połączenia.|  
|HOST_E_NOT_OWNER|Obiekt wywołujący nie jest właocicielem blokady.|  
|HOST_E_ABANDONED|Zdarzenie zostało anulowane podczas oczekiwania na niego zablokowanego wątku lub włókna.|  
|E_FAIL|Wystąpił nieznany błąd krytyczny. Gdy metoda zwraca wartość E_FAIL, środowisko CLR nie jest już możliwe do użycia w procesie. Kolejne wywołania metod hostingu zwracają HOST_E_CLRNOTAVAILABLE.|  
  
## <a name="remarks"></a>Uwagi  
 `IHostSecurityManager::OpenThreadToken` zachowuje się podobnie do odpowiedniej funkcji Win32 o tej samej nazwie, z tą różnicą, że funkcja Win32 zezwala obiektowi wywołującemu na przekazywanie dojścia do dowolnego wątku, podczas gdy `IHostSecurityManager::OpenThreadToken` otwiera tylko token skojarzony z wątkiem wywołującym.  
  
 Typ `HANDLE` nie jest zgodny z modelem COM, oznacza to, że jego rozmiar jest specyficzny dla systemu operacyjnego i wymaga kierowania niestandardowego. W ten sposób token jest używany tylko w ramach procesu, między środowiskiem CLR a hostem.  
  
## <a name="requirements"></a>Wymagania  
 **Platformy:** Zobacz [wymagania systemowe](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Nagłówek:** MSCorEE. h  
  
 **Biblioteka:** Uwzględnione jako zasób w bibliotece MSCorEE. dll  
  
 **Wersje .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]  
  
## <a name="see-also"></a>Zobacz także

- [IHostSecurityContext, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritycontext-interface.md)
- [IHostSecurityManager, interfejs](../../../../docs/framework/unmanaged-api/hosting/ihostsecuritymanager-interface.md)
